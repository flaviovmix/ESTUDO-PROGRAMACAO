## Etapa 2: SQL

**Objetivo:** criar e usar um banco PostgreSQL local só com SQL escrito à mão e rodado pelo `psql`, sem ORM, sem ferramenta gráfica decidindo nada, entendendo cada cláusula de cada comando.

**Conteúdo de estudo:** o que é um banco, uma tabela e uma linha; tipo de coluna; chave primária; o que cada cláusula de `SELECT`, `INSERT`, `UPDATE`, `DELETE` faz e por que o `WHERE` esquecido é a dor clássica; chave estrangeira e `JOIN`; agregação. O peso vai no comando: cada aula anda o script linha por linha.

Trilha aberta em paralelo com as outras duas (D4). Cada aula é uma subetapa com um passo só (D5); as aulas seguintes entram na tabela quando a anterior fechar, nunca de uma vez.

Tarefas:
- Banco próprio `estudo_programacao` no PostgreSQL local; nunca usar banco de outro projeto.
- Pasta `sql/`, uma subpasta por aula no padrão `NN - nome/`, scripts `.sql` rodados com `psql -f`, comando escrito num `LEIA-ME.txt` dentro da pasta da aula.
- Senha do banco nunca entra em script nem no README (D2, repo público): o `LEIA-ME.txt` diz "a senha do seu Postgres local", e só.
- O dono tecla os 2-3 primeiros movimentos de cada aula; enunciado cru; veredito só quando pedido; explicação depois que ele tentou.
- Cada aula fecha com o dono explicando com as próprias palavras o que cada cláusula faz.

## Subetapas (uma aula = um passo)

| # | Subetapa | Estado |
|---|---|---|
| 2.1 | Banco e `psql`: criar `estudo_programacao`, conectar, `\l`, `\dt`, `\q` | não iniciada |
| 2.2 | Tabela: `CREATE TABLE` com tipos, `PRIMARY KEY`, `NOT NULL`; `DROP` e recriar | não iniciada |
| 2.3 | `INSERT` e `SELECT`: inserir linhas, `select *`, `WHERE`, `ORDER BY` | não iniciada |
| 2.4 | `UPDATE` e `DELETE`: e o `WHERE` esquecido | não iniciada |
| 2.5 | Duas tabelas: chave estrangeira e `JOIN` | não iniciada |
| 2.6 | Agregação: `COUNT`, `SUM`, `AVG`, `GROUP BY` | não iniciada |

**Pronto quando:** cada aula da tabela está `✅` com data, o script de cada uma roda do zero num banco recém-criado com o comando do `LEIA-ME.txt` da pasta, está commitado, e a última aula foi o dono escrevendo uma consulta sozinho, sem roteiro, e explicando o que ela devolve e por quê.

**Desvios registrados:**

(nenhum ainda)
