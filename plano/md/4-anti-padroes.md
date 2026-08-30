# Anti-padrões

| Anti-padrão | Por que não fazer |
|---|---|
| `<style>` e `<script>` dentro do template | vira monolito de centenas de linhas por template, e desmontar depois custa um plano inteiro |
| Senha em texto claro em arquivo versionado | fica no histórico do git pra sempre, e repo público a expõe na hora |
| Login sem freio | força bruta livre contra senha curta |
| Contar tentativa pelo primeiro IP da lista de encaminhamento | limite burlável mandando o cabeçalho na mão |
| Mapa de contagem que nunca é limpo | cresce até estourar a memória |
| Validar upload pelo tipo declarado pelo cliente | tipo forjável. A validação real é a assinatura do arquivo |
| Converter texto em número sem tratar erro | um valor inválido na requisição vira 500 e página de erro do framework |
| Dois endpoints iguais separados só por um detalhe do cabeçalho da requisição | funciona, mas some se alguém mexer no cliente. E ninguém enxerga lendo |
| Enviar formulário por código sem disparar o evento de envio | intercepção nenhuma funciona, e o comportamento novo não pega |
| Clonar o CRUD a cada entidade | cada mudança comum passa a exigir lembrar de todos os arquivos clonados |
| Enum novo no código sem migration ampliando o CHECK | a funcionalidade responde 500 em produção |
| Chave gerada de texto livre numa coluna curta | salvar derruba com erro de banco em vez de mensagem no formulário |
| Componente que compara URL por nome de arquivo | rota sem extensão nunca casa, e o item ativo do menu não acende |
| Recurso consumido por máquina trancado por engano | o crawler recebe o HTML do login no lugar do robots.txt, e a rota de erro trancada vira destino salvo pós-login devolvendo JSON cru |
| Esconder feature com `display:none` no HTML | nem quem está construindo a feature enxerga a seção. Feature não pronta é estado no banco, com interruptor |
| Placeholder com cara de real na carga | ID de exemplo repetido abre conteúdo real aleatório na página, puxando rastreadores |
| Arraste como única forma de reordenar | arraste HTML5 não dispara no toque, e a lista fica inutilizável no celular |
| Teto fixo de itens numa galeria | conteúdo novo publicado pelo admin some em silêncio |
| Estado "apagado" por opacidade | fundo e texto desbotam juntos. Não existe opacidade que ainda pareça apagada e passe em contraste AA |
| Imagem de conteúdo com megabytes | cartão de link em aplicativo de mensagem sai sem miniatura |
| Buscar a classe no HTML pra saber se o CSS morreu | seletor criado em tempo de execução pelo JS parece morto na busca e está vivo |
| Estilo injetado por JS como `<style>` | morre quando o CSP liga, e morre em silêncio |
| Interação principal só no clique | teclado não alcança, e é a falha de acessibilidade mais cara de consertar depois |
| Deixar hospedagem pro fim | as pegadinhas de infraestrutura aparecem com o produto pronto e usuário esperando |
| Montar o arnês de teste só quando o primeiro CRUD nasce | deploy, autenticação e casca ficam validados só por clique, e a regressão deles aparece meses depois, longe da mudança que causou |
| Etapa fechada só com validação manual | vira fila invisível: ninguém repete aquele clique na mudança seguinte |
| Deixar a régua de legibilidade pra uma varredura final | retrofitar nome e tamanho de função em código pronto é um plano inteiro, e meses depois ninguém lembra por que o código é daquele jeito |
| Perseguir percentual de cobertura | percentual alto convive com caminho crítico descoberto, e o número vira teste que percorre linha sem afirmar nada |
| Erro da fila fechado sem teste que reproduz | o mesmo erro volta na mudança seguinte, e a fila vira roda-viva |
| Limpar "sobra de teste" sem conferir a origem | apaga upload de verdade do usuário achando que era resíduo do próprio teste |
