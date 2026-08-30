## Etapa 3: HTML, CSS e JS na unha

**Objetivo:** montar uma página com HTML semântico, CSS em arquivo próprio e JS em arquivo próprio, servida por um servidor local simples, sem framework, sem bundler, entendendo cada linha dos três arquivos.

**Conteúdo de estudo:** o que o navegador faz com um `.html`; por que servir (`http://`) é diferente de abrir (`file://`); seletor, caixa e cascata no CSS; no JS, `let`/`const`, o tipo que mora no valor e não na variável (contraste com o Java da Etapa 1), template literal, DOM e evento; a dor de manter variável e tela sincronizadas na mão. O peso vai no código: cada aula anda os arquivos linha por linha.

Trilha aberta em paralelo com as outras duas (D4). Cada aula é uma subetapa com um passo só (D5); as aulas seguintes entram na tabela quando a anterior fechar, nunca de uma vez.

Tarefas:
- Pasta `web/`, uma subpasta por aula no padrão `NN - nome/`, com `index.html`, `estilo.css` e `script.js` lado a lado; comando de servir (`python -m http.server`) escrito num `LEIA-ME.txt` dentro da pasta da aula.
- Página sempre vista servida, nunca por `file://`.
- JS explicado ancorado no Java que o dono já tem (contraste, não do zero). As lacunas conhecidas (`let`/`const`, crase, tipagem dinâmica) se observam no código dele sem apontar antes de ele pedir.
- O dono tecla os 2-3 primeiros movimentos de cada aula; enunciado cru; veredito só quando pedido; explicação depois que ele tentou.
- Cada aula fecha com o dono explicando com as próprias palavras o que cada linha faz.

## Subetapas (uma aula = um passo)

| # | Subetapa | Estado |
|---|---|---|
| 3.1 | HTML: uma página semântica (`header`, `main`, `footer`, `h1`, `p`, lista), servida | não iniciada |
| 3.2 | CSS: arquivo próprio, seletor, caixa, cor e fonte, variáveis | não iniciada |
| 3.3 | JS: arquivo próprio, `let`/`const`, tipo no valor, `console.log` | não iniciada |
| 3.4 | DOM: pegar elemento, mudar texto, ouvir clique | não iniciada |
| 3.5 | Estado na mão: contador com variável e tela sincronizadas, a dor | não iniciada |
| 3.6 | Formulário: `input`, evento, validação simples | não iniciada |

**Pronto quando:** cada aula da tabela está `✅` com data, a página de cada uma abre servida sem erro no console, está commitada, e a última aula foi o dono montando uma página sozinho, sem roteiro, e explicando o que cada arquivo faz.

**Desvios registrados:**

(nenhum ainda)
