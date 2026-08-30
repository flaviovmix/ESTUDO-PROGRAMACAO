## Etapa 0: Decisões travadas e esqueleto do repo

**Objetivo:** nenhuma linha de feature antes de as decisões estruturais estarem escritas.

As decisões que precisam de resposta **antes** do primeiro commit (viram `D1..Dn` no plano do projeto):

| Decisão | Por que agora |
|---|---|
| Stack: linguagem, framework, banco, migrations, camada de view | trocar depois é reescrever |
| **Onde o repo fica hospedado (GitHub, GitLab, servidor próprio) e se ele é público ou privado** | repo público publica na hora tudo que entrar nele, e o histórico do git não esquece: um segredo commitado por engano só se resolve trocando o segredo. Público também é decisão de licença e de quem pode abrir issue |
| Branch de trabalho e política de merge | evita commit na branch errada no dia 1 |
| Idioma do domínio (tabela e classe em português ou inglês) | misturar é dívida permanente |
| **Onde mora o estático** (dentro do artefato ou fora) | decide o acoplamento de deploy pra sempre |
| **Onde mora o conteúdo que cresce** (upload) | nunca dentro do artefato. Pasta externa ou volume |
| Segredos por variável de ambiente desde o commit 1 | segredo versionado fica no histórico do git pra sempre |
| Papéis de usuário, mesmo que só exista um hoje | enfiar papel depois mexe em toda rota |
| **Domínio e servidor de produção** | é a Etapa 3, não a última |
| **Dado pessoal: o que o projeto guarda, por quanto tempo, tem dado de criança, como se exclui uma conta** | é lei (LGPD) e é remendo caro: exclusão de conta enfiada depois arrasta junto a limpeza de tudo que a conta gerou |
| **Teto de custo mensal da infra** | domínio, servidor, e-mail e backup externo são pagos recorrentes. Domínio expirado por cartão vencido derruba o site e o APK de uma vez |
| **Este plano é de estudo ou só de entrega** (`1-formato-do-plano`, item 8) | muda como cada etapa executa |
| **Que tipo de projeto é este** (loja virtual, sistema interno, site de conteúdo, app de uso próprio, outro) | as 16 etapas são genéricas. O tipo decide se entram decisões e blocos de domínio que elas não cobrem, e é aqui que isso se descobre, não na hora de codar |

Tarefas:
- **Gerar o plano em HTML antes de responder qualquer decisão**: `/gerar-html-do-plano <pasta deste plano>`. Abre `plano/html/index.html` com a tabela das 16 etapas **toda em vermelho**, e é assim que ela deve estar hoje: o plano é lido do `plano.md` e dos `.md` de `etapas/`, sem cópia de status em lugar nenhum. Dali em diante, regerar faz parte de fechar etapa (`1-formato-do-plano`, item 6). Pra bolinha refinar dentro de uma etapa, `✅` no começo da linha da tarefa e coluna `Estado` na tabela de subetapas.
- **Repo, nesta ordem, que importa:** criar o repositório local, **fechar o `.gitignore` antes de qualquer `git add`** (artefatos de build, `.env`, upload local, pasta de trabalho), primeiro commit só com o esqueleto, criar o repositório remoto com a visibilidade decidida acima, e enviar. Arquivo que entrou no primeiro commit fica no histórico pra sempre, então a ordem não é detalhe.
- Criar a **branch de trabalho** já, e deixar a principal no estado publicado desde o começo (regra de git em `1-formato-do-plano`, item 7).
- `README.md` que ensina alguém a subir o projeto do zero: pré-requisitos, comando de build, comando de rodar, credenciais de dev, como recriar o banco.
- **O README documenta o dev-loop**: o que pede restart, o que pede cópia manual pro diretório de build, o que é só F5. "O fix não aparece" quase sempre é o arquivo editado que não chegou onde o app serve.
- **Ligar o alerta automático de vulnerabilidade de dependência no repo** (Dependabot ou equivalente) já, o que só é possível depois de o remoto existir. A vulnerabilidade nasce depois do lançamento; o alerta tem que existir antes.
- Estrutura de pastas **por feature**, não por tipo. Os irmãos ficam juntos: o HTML, o CSS e o JS do mesmo componente perto um do outro. Nada de pasta-balde (`utils/`, `misc/`).
- Escrever, no plano, a regra de nomenclatura do projeto (prefixos, sufixos, kebab ou camel) e não desviar dela depois.

---

## Se a resposta foi "loja virtual"

As 16 etapas montam a base (auth, deploy, upload, teste, LGPD, backup), mas **não cobrem o domínio de comércio**. Ao ouvir "loja", acrescentar o seguinte, e não deixar pra descobrir na hora de codar.

**Entram já aqui:** a **política de devolução como `D*`** (é decisão do dono, e o direito de arrependimento de 7 dias é lei), e os **fornecedores como default declarado** (`1-formato-do-plano`, item 3: fornecedor não nasce travado; a etapa que o usa diz em voz alta que é o default do plano e só trava como `D*` depois que o dono confirmar). Os defaults: gateway de pagamento **Mercado Pago com checkout hospedado**, porque assim o cartão nunca toca o servidor e o projeto fica fora do escopo PCI; nota fiscal por API tipo **Focus NFe ou NFe.io**, porque regra tributária muda por estado e por produto; frete por intermediador tipo **Melhor Envio**, em vez de integrar transportadora a transportadora. O endereço e o CPF do cliente entram na decisão de dado pessoal, e as mensalidades desses serviços entram no teto de custo.

**Entra na Etapa 1, e se escreve lá agora:** trava de estoque. Dois clientes comprando a última unidade ao mesmo tempo é concorrência, ou seja, modelagem de banco e transação. Ler, conferir e gravar não resolve, e retrofitar depois reescreve o caminho de compra inteiro. Como cada sessão carrega só a etapa atual, promessa que fica neste parágrafo se perde: ao fechar esta etapa, **acrescentar a tarefa no arquivo `01-banco-e-migrations.md`** (estoque na variação com trava de concorrência, e tabela de reserva), registrando o acréscimo nos Desvios de lá. O ciclo completo da reserva (nasce com o pedido, baixa no pago, volta no expirado ou cancelado antes do pagamento; depois do pago vale a regra de reentrada da L4) está escrito na L2.

**Entram depois da Etapa 11 e antes da 12**, como as quatro etapas de `etapas-loja/`: **L1** catálogo e carrinho, **L2** pagamento e pedido, **L3** frete e fiscal, **L4** pós-venda. Elas vêm por último porque dependem de quase tudo que nasce antes: o molde de CRUD e a rede parametrizada de testes (Etapas 7-8), o upload pra imagem de produto (9), os critérios de área pública que o catálogo herda (10) e o e-mail transacional que pedido, rastreio e devolução disparam (11). Construir carrinho antes disso é construir sem molde e sem teste, que é o que a Etapa 7 existe pra evitar.

Copiar as quatro linhas de status pro `plano.md` (a tabela do bloco de loja já está lá) e **apagar a pasta `etapas-loja/` se o projeto não for loja**, junto com as linhas.

---

**Pronto quando:** alguém que nunca viu o projeto sobe local lendo só o README, as decisões `D*` estão escritas no plano (incluindo as do tipo de projeto, quando houver), e o repositório remoto existe com o primeiro commit, a visibilidade decidida, a branch de trabalho criada e o alerta de dependência ligado.

**Desvios registrados:**

- (30/08/2026) **Projeto de estudo, sem app.** As Etapas 1-15 do molde (app web) foram apagadas, linha e arquivo, e no lugar entraram três trilhas, uma etapa cada, com as aulas como subetapas: 1 Java na unha, 2 SQL, 3 HTML/CSS/JS na unha (D3, D4, D5). Da tabela de decisões acima, estático, upload, papéis de usuário, domínio/servidor, dado pessoal e teto de custo **não se aplicam**: não há app, usuário nem servidor. Repo já existia no GitHub, público (D2). Alerta de dependência fica ligado mesmo sem dependência: custa nada. Executado direto, a pedido do dono ("ok" à proposta do desenho).
- (30/08/2026) A seção "Se a resposta foi loja virtual" não se aplica; ficou no arquivo só como registro do molde.
