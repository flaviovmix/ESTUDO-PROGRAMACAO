## Etapa 3: HTML, CSS e JS na unha

**Objetivo:** montar uma página com HTML semântico, CSS em arquivo próprio e JS em arquivo próprio, servida por um servidor local simples, sem framework, sem bundler, entendendo cada linha dos três arquivos.

**Por que a trilha começa por aqui (06/09/2026):** o dono escolheu abrir o estudo pela web, e não pelo terminal Java, porque começar por uma parte que não mostra nada na tela desanima. HTML e CSS aparecem no navegador a cada salvamento, e o programa da série JAVA WEB é web: a lista de tarefas que vai nascer em Java já tem cara antes de ter código. É aquecimento, de leve; o peso volta pra trilha 1 quando a página estiver de pé.

**Servidor:** Live Server do VS Code (`http://127.0.0.1:5500/...`), que é o que todo mundo usa e recarrega sozinho ao salvar. O `python -m http.server` fica no `LEIA-ME.txt` como segundo jeito. Os dois servem por `http://`, que é o que importa. Com o Live Server aberto, não renomear nem mover pasta: ele segura o arquivo no Windows.

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
| 3.1 | HTML/CSS: a folha de uma tarefa do Nexus (nome + subtarefas), uma lista de tarefas simples e só essa parte, igual à real no celular e no desktop. As tags principais (`section`, `header`, `footer`, `nav`, `form`, `h1`-`h3`, `textarea`, `button`, `ul`/`li`) aparecem porque a tela precisa delas; o CSS nasce dentro do `<style>` e, no fim da aula, sai pro `estilo.css` por `<link>`. Modelo pronto (feito pelo executor) em `PROJETOS/SEIRES/JAVA WEB/_arquivos/modelo-lista-de-tarefas/`, que é o que o episódio da série mostra | não iniciada (modelo pronto em 06/09/2026, conferido contra a tela real nos dois tamanhos) |
| 3.2 | JS: arquivo próprio, `let`/`const`, tipo no valor, `console.log` | não iniciada |
| 3.3 | DOM: pegar elemento, mudar texto, ouvir clique | não iniciada |
| 3.4 | Estado na mão: contador com variável e tela sincronizadas, a dor | não iniciada |
| 3.5 | Formulário: `input`, evento, validação simples | não iniciada |

**Pronto quando:** cada aula da tabela está `✅` com data, a página de cada uma abre servida sem erro no console, está commitada, e a última aula foi o dono montando uma página sozinho, sem roteiro, e explicando o que cada arquivo faz.

**Desvios registrados:**

- 06/09/2026: a trilha 3 abriu antes da 1, por escolha do dono (ver "Por que a trilha começa por aqui"). A aula 3.1 foi redesenhada no mesmo dia: HTML e CSS juntos, reproduzindo a folha da tarefa do Nexus, só nome + subtarefas (celular e desktop; a tela inteira de /tarefas foi descartada no mesmo dia por ser demais pra um aquecimento), CSS primeiro dentro do arquivo e só depois exportado (antes, HTML e CSS eram aulas separadas e o CSS já nascia em arquivo próprio). Live Server aceito como servidor da aula. A aula em si acontece numa sessão de estudo, com o dono no teclado; o executor monta antes um modelo pronto da tela, que serve de gabarito e de material do episódio da série JAVA WEB que anuncia este módulo ao ouvinte.
