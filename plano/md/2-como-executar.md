# Como executar o plano

## Abrindo a sessão

Antes de qualquer coisa, ler o `plano.md` e se situar sozinho:

- **Título ainda em `[NOME DO PROJETO]` e tabela toda "não iniciada"** = pasta recém-copiada. Perguntar **duas coisas**: o nome do projeto e **que tipo de projeto é** (loja virtual, sistema interno, site de conteúdo, app de uso próprio, outro). Escrever as duas no topo do `plano.md` e o nome no `erros.md`, e abrir a Etapa 0. O dono não edita arquivo pra começar; quem preenche sou eu.

  O tipo não é enfeite: ele decide se entram **decisões e blocos de domínio** que as 16 etapas genéricas não cobrem. Hoje o único conjunto mapeado é o de loja virtual, na Etapa 0. Tipo que não tem bloco mapeado segue nas 16 etapas puras, e o que faltar aparece como `P*` no caminho.
- **Já tem nome mas nenhum `✅`** = alguém preencheu por fora, ou a sessão anterior parou antes da Etapa 0. Não re-perguntar o que já está escrito: conferir se o tipo também está preenchido, abrir a Etapa 0 e registrar lá, em Desvios, que o preenchimento veio de fora.
- **Já tem nome e a tabela tem `✅`** = projeto em andamento. Dizer a etapa, a subetapa, a data da última mexida e o próximo "pronto quando", e só então carregar o arquivo daquela etapa.

Em nenhum dos casos abrir etapa que não é a atual.

## Em toda etapa

- **Uma etapa por vez**, com confirmação entre elas; fechamento e validação conforme a `1-formato-do-plano`, item 6.
- **Etapa fecha com o comportamento dela dentro do arnês** (`1-formato-do-plano`, item 9) **e com o código dela passando pela régua de legibilidade** (item 10). O que ficou de fora, nos dois casos, se escreve como `P*`, nunca se cala.
- **Decisão ambígua no meio do caminho pausa a execução.** A decisão vira `D*` escrita, não escolha silenciosa do executor.
- **Mexida grande começa com levantamento registrado** (o mapa do que existe) antes da primeira edição. Achado de levantamento que muda o plano entra no arquivo **antes** de qualquer linha de código.
- **Padrão do projeto ganha do gosto de quem escreve.** Mas padrão ruim repetido não é padrão, é dívida: sinalizar em uma frase antes de replicar, nunca propagar calado nem consertar sozinho.
- **Sinalizar refatoração é sempre bem-vindo. Executar precisa de OK.**
- Git conforme a `1-formato-do-plano`, item 7: não commitar sem pedido; savepoint antes de etapa arriscada é bem-vindo.

## O contrato do modo entrega

Assuma que a maior parte do plano vai rodar em **entrega**, não em estudo (`1-formato-do-plano`, item 8). Das Etapas 7 a 11, e no bloco de domínio quando houver (L1-L4 na loja), o trabalho é produzir funcionalidade em ritmo, e é aí que este contrato vale. As réguas de validação e os itens 9/10 valem pra toda etapa, as L incluídas. Ele existe porque um executor sem a lista do que decide sozinho cai num de dois extremos, e os dois custam caro: ou pergunta o que o plano já decidiu, e a produção vira ping-pong; ou decide calado o que era do dono, e ele descobre três etapas depois.

**Antes de começar cada etapa, reler as decisões `D*`.** É o passo que mais cai em ritmo de produção, e sem ele as decisões viram letra morta lá pela Etapa 9, com o executor reinventando o que já estava travado.

**Segue sozinho, sem perguntar** (tudo isto o plano já decidiu; perguntar é ruído):

| Segue | Onde já foi decidido |
|---|---|
| Nomenclatura, prefixo, sufixo, caixa | Etapa 0 |
| Onde o arquivo novo mora na estrutura por feature | Etapa 0 |
| Validação no servidor com mensagem em português no formulário | Etapa 7 |
| Entrada inválida tratada (texto onde se espera número, campo vazio, id inexistente) | Etapa 7 |
| Estado vazio do componente (lista sem item, carrossel de 1) | Etapa 5 |
| O caso novo entrando como linha na tabela de teste | item 9, Etapa 8 |
| A régua de legibilidade rodando no diff da própria etapa | item 10 |
| Índice quando nasce listagem, `ON DELETE` da relação nova | Etapa 1 |

**Para e pergunta, sempre** (cada um destes é uma decisão do dono disfarçada de detalhe técnico):

| Para | Por quê |
|---|---|
| Terceiro clone de uma peça repetível | extrair base é decisão de arquitetura, não de estilo (Etapa 8) |
| Escolha que não está coberta por nenhum `D*` | vira `D*` escrita, com data, não escolha silenciosa |
| Gambiarra: JS como string, seletor frágil, contorno de limitação do framework | o dono aceita ou recusa a fragilidade sabendo o preço |
| Migration que altera ou apaga dado existente | não tem desfazer, e `drop`/`update` em massa é irreversível |
| Mudança em contrato já publicado (rota, payload, nome de campo consumido de fora) | quebra quem já consome, e isso não aparece no teste do projeto |
| "Pronto quando" que não é alcançável do jeito que foi escrito | o critério muda por decisão registrada, nunca por interpretação de quem executa |

**O que nunca é opcional, mesmo com pressa:** validação no servidor, autorização da rota, tratamento de erro visível, e o registro do que foi feito no plano na mesma sessão (`1-formato-do-plano`, item 6). "Estamos sem tempo" encurta o método de estudo, nunca estes quatro. Etapa entregue sem eles não está entregue, está devendo.
