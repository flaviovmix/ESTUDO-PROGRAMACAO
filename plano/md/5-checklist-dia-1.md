# Checklist do dia 1

Marcar tudo isto **antes da primeira feature**. É a lista do que não fica mais barato depois.

- [ ] Decisões `D*` escritas, incluindo onde mora o estático, onde mora o upload, o domínio de produção, o dado pessoal (o que guarda, retenção, exclusão de conta) e o teto de custo mensal
- [ ] **Se o tipo tem bloco de domínio (loja):** fornecedores declarados como default (gateway, nota fiscal, frete), política de devolução como `D*`, endereço e CPF do cliente na decisão de dado pessoal, as mensalidades desses serviços no teto de custo, e as linhas L* na tabela do `plano.md`
- [ ] Modo de execução decidido: estudo ou entrega (`1-formato-do-plano`, item 8)
- [ ] Repo local criado com o `.gitignore` fechado **antes** do primeiro `git add`, remoto criado com a visibilidade decidida (público ou privado), e README que ensina a subir do zero
- [ ] Dev-loop documentado no README (o que pede restart, o que pede cópia, o que é só F5)
- [ ] Branch de trabalho criada e as regras de git escritas no plano (quem manda na principal, quando commitar, savepoint)
- [ ] Alerta automático de vulnerabilidade de dependência ligado no repo
- [ ] Estrutura de pastas por feature, regra de nomenclatura escrita
- [ ] Migrations ligadas antes da primeira tabela, com a regra "aplicada não se edita"
- [ ] Seed sem segredo, senha inicial por variável de ambiente com padrão fechado
- [ ] Perfis de ambiente separados, toda configuração por variável
- [ ] Página de erro própria, sem stack trace, nos dois perfis
- [ ] **Domínio no ar com HTTPS e o esqueleto vazio publicado**
- [ ] Firewall fechado e SSH por chave, conferidos com scan de fora
- [ ] Procedimento de deploy e de rollback escrito e testado
- [ ] Backup do banco agendado, restaurado uma vez e com alerta de falha
- [ ] Freio de força bruta no login, com faxina das janelas
- [ ] Papéis definidos, negar por padrão nas rotas, sessão com as flags certas
- [ ] Layout base único, tokens num arquivo, CSS por componente, JS espelhando o CSS
- [ ] Orçamento de peso da página pública escrito no plano (a régua 6 mede contra ele)
- [ ] **CSP sem `unsafe-inline` ligado**
- [ ] Acessibilidade e SEO no molde da página
- [ ] Casca do admin na régua de 4 tamanhos (se o projeto tem admin)
- [ ] **Arnês de teste montado na Etapa 2**: executor por um comando, perfil de teste, banco de verdade com transação revertida, pasta de trabalho descartável
- [ ] Teste de fumaça do esqueleto passando no caminho real (health, página de erro, a mesma URL em JSON); o dos papéis entra na Etapa 4 e a rede parametrizada de CRUD na Etapa 7
- [ ] Conferência pós-deploy como script versionado, rodando depois de cada subida
- [ ] Fila de erros criada (`erros.md`), mesmo vazia
- [ ] Pasta do plano copiada pra `plano/md/`, e o nome do projeto já preenchido no `plano.md` e no `erros.md` (quem preenche é o executor, na primeira sessão)
- [ ] Plano em HTML gerado (`plano/html/index.html`, com as 16 etapas em vermelho) e regerado a cada etapa fechada
- [ ] Etapa que não se aplica a este projeto apagada: linha da tabela e arquivo em `etapas/`
- [ ] Combinado escrito de que etapa fecha com o comportamento dela no arnês (item 9) e com o código dela na régua de legibilidade (item 10)
