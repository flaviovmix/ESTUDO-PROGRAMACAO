## Etapa 1: Java na unha

**Objetivo:** escrever, compilar e rodar Java só com o JDK (`javac` e `java`), sem IDE decidindo nada, sem Maven, sem framework, entendendo cada palavra de cada arquivo.

**Conteúdo de estudo:** o que o `javac` faz com um `.java` (vira `.class`, bytecode), o que a JVM roda, por que o tipo é decidido antes de rodar (tipagem estática) e o que cada palavra de `public static void main(String[] args)` faz. O peso vai no código: cada aula anda o arquivo linha por linha, conceito só o mínimo pra linha fazer sentido.

Trilha aberta em paralelo com as outras duas (D4). Cada aula é uma subetapa com um passo só (D5); as aulas seguintes entram na tabela quando a anterior fechar, nunca de uma vez.

Tarefas:
- Pasta `java/`, uma subpasta por aula no padrão `NN - nome/`, um `.java` por exercício, comando de compilar e rodar escrito num `LEIA-ME.txt` dentro da pasta da aula.
- O dono tecla os 2-3 primeiros movimentos de cada aula; o executor completa o repetitivo com o dono conferindo.
- Enunciado cru, sem pré-digerir. Durante o código, só veredito quando pedido; a explicação vem depois que ele tentou.
- Cada aula fecha com o dono explicando com as próprias palavras o que cada linha faz.

## Subetapas (uma aula = um passo)

| # | Subetapa | Estado |
|---|---|---|
| 1.1 | Olá, JDK: `java -version`, primeiro `Ola.java`, `javac` e `java`, o que é o `.class` | não iniciada |
| 1.2 | Variável e tipo: `int`, `double`, `boolean`, `char`, `String`; o compilador recusando tipo errado | não iniciada |
| 1.3 | Condição: `if`/`else`, operadores de comparação e lógicos, `switch` | não iniciada |
| 1.4 | Laço: `for`, `while`, `do-while`, acumulador | não iniciada |
| 1.5 | Método: assinatura, parâmetro, retorno, `static` | não iniciada |
| 1.6 | Classe e objeto: atributo, construtor, `new`, `this` | não iniciada |
| 1.7 | Coleção: array e `ArrayList` | não iniciada |
| 1.8 | Entrada: `Scanner` e `args`, um programa que conversa | não iniciada |

**Pronto quando:** cada aula da tabela está `✅` com data, o código de cada uma compila e roda pelo terminal com o comando do `LEIA-ME.txt` da pasta, está commitado, e a última aula foi o dono fazendo um exercício sozinho, sem roteiro, e explicando o que escreveu.

**Desvios registrados:**

(nenhum ainda)
