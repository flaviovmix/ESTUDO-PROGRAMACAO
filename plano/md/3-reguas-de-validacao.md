# Réguas de validação

Escrever estas sete no plano do projeto, e usar em todo "pronto quando".

**1. Régua de 4 tamanhos.** 3840×2160, 1920×1080, 768×1024, 360×800. Nenhum estouro horizontal em nenhum. Atenção: se o corpo da página esconde estouro por configuração de overflow, a medida da largura de rolagem **não acusa nada**. Medir elemento por elemento.

**2. Régua de sobreposição.** `elementFromPoint` no centro dos alvos principais (logo, botões, primeiro card): o que responde tem que ser o próprio alvo. Elemento fixo ou grudado cobrindo conteúdo é o defeito que nenhuma medida de overflow acusa: o overflow do body esconde o vazamento e ele fica invisível.

**3. Comportamento idêntico, exceto o delta declarado.** Etapa de organização não muda comportamento. Se mudou algo, ou é o delta que a etapa declarou no começo, ou é regressão.

**4. Comparação geométrica antes e depois.** Pra mudança grande de CSS ou de estrutura, medir a caixa e as propriedades computadas de todo elemento nas duas versões, na mesma tela. É prova mais forte que olhar imagem. Os jeitos conhecidos de o próprio teste mentir:
- **Congelar animação por JavaScript, nunca injetando estilo**: com CSP ligado, a injeção é bloqueada de um lado só e o congelamento vale só numa das versões.
- Elemento medido **no meio da animação de entrada** devolve cor misturada com o fundo. Esperar terminar antes de medir.
- Medição em página autenticada **confere a URL final**: sem o cookie, a ferramenta mede a tela de login e devolve a nota de outra página.
- Contagem de inline se faz **no HTML cru, não no DOM**: o que o JS aplica em runtime vira atributo no DOM e dá falso positivo.
- O `Accept` da requisição **muda a resposta do servidor** (JSON no lugar da página de erro), e navegador nenhum pede assim. Testar com o que o navegador manda.
- Ferramenta que conta **linha** não conta **ocorrência**: padrão que casa dentro de outro padrão erra a auditoria.

**5. Três papéis, sempre.** Anônimo, usuário comum, administrador. Muita coisa só quebra num deles.

**6. Peso e performance.** Orçamento de peso da página pública escrito no plano, dimensão declarada em toda imagem, e o score de performance medido junto com o de acessibilidade, na mesma rodada.

**7. Quem fecha é o dono.** Automação adianta, mas etapa fecha com o dono validando no navegador, recebendo o link, cobrindo o que script nenhum mede: arraste com o mouse, upload grande com a barra andando, corte de imagem, modal, gesto no aparelho.
