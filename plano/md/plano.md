# Plano: ESTUDO-PROGRAMACAO

**Tipo:** outro: projeto de estudo. Não é loja: o bloco L1-L4 e a pasta `etapas-loja/` foram apagados.

**Saída:** ../html

O tipo decide se entram decisões e blocos de domínio que as 16 etapas genéricas não cobrem. Quem preenche a linha do tipo é o executor, na primeira sessão, perguntando ao dono; a linha de saída já vem pronta. A saída é a pasta onde o plano em HTML é gerado (Etapa 0, primeira tarefa): esta pasta é o `plano/md/` do projeto, e o gerado cai na irmã `plano/html/` (abre em `plano/html/index.html`).

Índice do projeto. **É o único arquivo lido em toda sessão**, por isso ele é curto: o detalhe mora em `etapas/`, e só a etapa atual é carregada.

As regras estão nos arquivos `1` a `4` ao lado, e vieram junto na cópia. Elas ficam congeladas com este projeto de propósito: o molde vai continuar evoluindo, e projeto que já fechou etapa não pode ter o critério dela reescrito por baixo.

---

## Decisões

Decisões **travadas**. Uma vez escritas, não se repropõe. Se a realidade derrubar uma, a nova entra com data e o motivo da virada, e a antiga fica registrada.

- D1. (30/08/2026) Projeto de estudo: o método é o **modo estudo** do `1-formato-do-plano`, item 8 (o dono no teclado nos 2-3 primeiros movimentos de cada etapa, o executor completa o repetitivo, cada etapa declara o Conteúdo de estudo e fecha com o dono explicando o que mudou). O modo se redeclara no início de cada etapa; "pode executar" vale só pra etapa em que foi dito e vira desvio registrado.
- D2. (30/08/2026) Repo **público** no GitHub (`flaviovmix/ESTUDO-PROGRAMACAO`, já criado). Consequência: nenhum segredo, senha de banco ou dado pessoal entra no repo, nem em arquivo de exemplo; o `.gitignore` fecha antes do primeiro `git add` de código.
- D3. (30/08/2026) Trilhas de estudo, nesta ordem de começo: **Java na unha** (sem framework, sem build tool: `javac`/`java` e JDK puro), **SQL** (PostgreSQL local) e **HTML, CSS e JS na unha** (sem framework, sem bundler). Estrutura por trilha, não por tipo.
- D4. (30/08/2026) Uma etapa por trilha, as três **abertas em paralelo**: a etapa atual é a que o dono escolhe na sessão, e só o arquivo dela é carregado. Pastas na raiz: `java/`, `sql/`, `web/`; dentro, uma subpasta por aula no padrão `NN - nome/` (número com dois dígitos, espaço, hífen, espaço, nome em kebab). Nomes de arquivo, variável e tabela em **português**.
- D5. (30/08/2026) **Uma aula = um passo.** Cada aula é uma subetapa (1.1, 1.2...) com um critério só, que fecha com um artefato que roda, commitado, e com o dono explicando com as próprias palavras. Aulas seguintes entram na tabela quando a anterior fecha. Ritual: enunciado cru, o dono tecla os primeiros movimentos, veredito só quando pedido, explicação linha por linha depois que ele tentou.

## Pendências

Cada uma diz **em que etapa trava**. Pendência sem etapa dona vira esquecimento.

- P1. ... **Trava a Etapa N.**

---

## Status das etapas

Ao fechar uma etapa, marcar `✅ + data` **aqui e no arquivo dela**. Índice desatualizado é pior que índice nenhum.

| # | Etapa | Status | Última mexida |
|---|---|---|---|
| 0 | Decisões travadas e esqueleto do repo | em andamento, decisões D* | 30/08/2026 |
| 1 | Java na unha | não iniciada | |
| 2 | SQL | não iniciada | |
| 3 | HTML, CSS e JS na unha | não iniciada | |

Etapa em andamento se escreve com a posição: `em andamento, 1.3 de 8`. As Etapas 1-15 do molde (app web) foram apagadas em 30/08/2026 e substituídas pelas três trilhas (desvio registrado na Etapa 0).

---

## Ondas de evolução (depois de uma trilha fechar)

Registrar com data e commit, senão daqui a seis meses ninguém sabe por que uma decisão foi tomada.
