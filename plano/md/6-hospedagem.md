# Hospedagem em servidor, ponta a ponta

Esta parte é a Etapa 3 detalhada, mais o que a Etapa 12 acrescenta depois. Escrita de forma genérica, com VM própria + container + proxy reverso na frente como caminho recomendado.

## 1. Escolher o modelo, com o custo na mesa

| Modelo | Quando serve | Custo real |
|---|---|---|
| VM própria com container | projeto que vai crescer, mais de um serviço no mesmo servidor, controle total | você é o administrador do sistema. Atualização, firewall, certificado, backup |
| Plataforma gerenciada | quer só publicar, aceita o preço e a caixa preta | menos controle sobre disco persistente e sobre custo quando escala |
| Hospedagem estática | site sem servidor de aplicação | não serve pra este plano, que pressupõe banco e login |

Recomendação padrão: **VM com container e proxy reverso**. É o que dá pra explicar inteiro, e o que permite vários projetos convivendo no mesmo servidor.

**Somar o custo recorrente antes de escolher**, e escrever na decisão de custo da Etapa 0: domínio (com renovação automática **ligada**), VM, provedor de e-mail, armazenamento do backup externo. Valor e onde cada um é cobrado. Domínio expirado por cartão vencido derruba o site e o APK de uma vez.

## 2. O desenho mínimo

```
Internet
   |
   v
[proxy reverso]  <- termina o HTTPS, um site por domínio
   |
   +-- app do projeto A (container, porta interna)
   |        |
   |        +-- banco do projeto A (container, volume nomeado)
   |        +-- pasta de conteúdo (volume ou pasta montada do host)
   |
   +-- app do projeto B ...
```

Regras que evitam dor:
- **O banco não expõe porta pra internet.** Só a rede interna dos containers. E isso se **confere com scan de fora** (a mesma conferência de scan da Etapa 3), não olhando a configuração.
- **O conteúdo que cresce mora em volume ou pasta montada**, nunca dentro da imagem. Republicar o app não pode apagar upload de usuário.
- **Um domínio por projeto**, com certificado automático no proxy.
- A configuração do proxy é arquivo, e **arquivo de configuração mora no repositório**. Configuração que só existe no servidor é a que ninguém consegue auditar depois.

## 3. Endurecer a máquina

- Firewall com só **80, 443 e a porta do SSH** abertas. Todo o resto fechado.
- SSH **por chave**, autenticação por senha desligada, login de root bloqueado.
- ⚠️ **Container que publica porta fura o firewall do host**: as regras que o runtime de container cria passam por cima das do firewall comum. Publicar `5432:5432` "só pra testar" expõe o banco pra internet mesmo com o firewall dizendo que não. A prova é sempre um scan de fora da máquina.
- **Patches de segurança automáticos do sistema** ligados (o mecanismo de atualização não assistida da distribuição).
- **As imagens base dos containers também envelhecem**: reconstruir com base atualizada faz parte do ritual recorrente da Etapa 12.

## 4. DNS e HTTPS

1. Apontar o domínio (registro A ou AAAA) pro IP da máquina.
2. Certificado automático pelo proxy. Conferir renovação.
3. Redirecionar HTTP pra HTTPS.
4. Conferir o certificado do jeito que o usuário vê: navegador, e também requisição de linha de comando.

## 5. As pegadinhas de proxy

- **O app precisa saber que está atrás de proxy.** Sem a configuração de cabeçalhos encaminhados, o app monta endereço absoluto em `http://` e o usuário toma redirecionamento quebrado logo depois do login, com a sessão criada. O sintoma engana: parece falha de login, mas o login funcionou.
- **O HSTS é o exemplo acabado do mesmo mecanismo**: o framework só emite esse cabeçalho quando enxerga a requisição como segura. Sem os cabeçalhos encaminhados, ele nunca sai, e ninguém percebe porque nada quebra na cara de ninguém.
- **IP do cliente vem do último salto confiável, não do primeiro.** A lista de encaminhamento pode começar com um valor que o próprio cliente mandou. Quem lê o primeiro valor pra contar tentativa de login tem um limite que nunca fecha.
- **Ler a configuração do proxy antes de afirmar qualquer coisa** sobre esses cabeçalhos: se ele sobrescreve, o problema muda de forma. Suposição aqui vira relatório de segurança errado.
- **Limite por IP em memória precisa de faxina.** Sem ela, o mapa cresce até o app cair.
- **Arquivo servido pelo app e arquivo servido de fora do artefato sobem por canais diferentes.** Se o HTML dentro do pacote passa a apontar pra CSS que mora fora, subir só o pacote deixa a página sem estilo. Decidir isso na Etapa 0 e, se acontecer mesmo assim, escrever a lista fechada do que precisa subir junto.

## 6. Variáveis de ambiente e segredos

- Uma lista no README com **toda** variável que produção precisa, o que ela faz, e o que acontece se faltar.
- Segredo nunca no repositório, nem em migration, nem em arquivo de configuração versionado.
- Faltando a variável, o comportamento padrão é o **mais fechado** (valor aleatório, acesso negado), nunca o mais aberto.
- Segredo já commitado por engano: vale a regra da tabela de git (`1-formato-do-plano`, item 7), **rodar o segredo**. O histórico não esquece.
- **Rotação também é rotina, não só socorro**: cada segredo da lista tem o procedimento de troca escrito e testado (trocar sem procedimento é downtime), e os gatilhos definidos (suspeita, máquina de dev comprometida, chave exposta em log). Detalhe operacional na Etapa 12.

## 7. O procedimento de atualização (escrever, testar, versionar)

O procedimento tem que caber num bloco copiável, com estes passos:

1. **Backup antes** (banco e o artefato atual, com nome datado).
2. Construir o artefato localmente, com os testes verdes.
3. Enviar pro servidor.
4. Aplicar migrations (ou deixar o app aplicar no boot) e **conferir quais são novas em relação ao banco de produção**.
5. Reiniciar o serviço.
6. Conferência pós-deploy pelo **script versionado** (nasce na Etapa 3): as URLs e recursos que precisam responder, os cabeçalhos de segurança nas rotas certas e a **ausência** deles onde não devem estar. Lista pra conferir no olho não sobrevive ao terceiro deploy.
7. Se algo falhar, voltar pro artefato anterior guardado no passo 1.

Escrever também **o que sobe junto**: pacote, arquivos estáticos, arquivos de raiz (`robots.txt`, `sitemap.xml`), e configuração do proxy quando mudou.

## 8. Backup

- Dump do banco agendado, com retenção (diário por N dias, semanal por N semanas).
- Backup **fora da mesma máquina**. Backup no mesmo disco não protege de perda de disco.
- **Vigiado**: idade e tamanho mínimo do último dump conferidos, com alerta quando o job falhar. Backup por agendador quebra em silêncio.
- Restauração testada num banco vazio, com o app subindo em cima, e **retestada com cadência escrita** (a cada N meses e depois de mudança grande de schema).
- O conteúdo enviado por usuário entra no backup também. É a parte que não dá pra recriar.

## 9. Depois que está no ar

- Não testar em produção enquanto houver usuário real. Antes disso, testar direto lá é aceitável e economiza tempo. Escrever no plano em que momento essa liberdade acaba.
- Toda mudança nasce local, sobe **em lote**, quando o dono do projeto mandar. Nada de "já subo esse ajuste".
- Erro reportado por usuário entra na fila, e só fecha quando quem reportou confirmar em produção.
