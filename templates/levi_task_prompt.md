# Template - Tarefa para Levi

Use este modelo para pedir desenvolvimento backend/frontend ao Levi.

## Prompt

Você está trabalhando no repositório `<repo>`.

Objetivo:
- `<objetivo claro>`

Contexto:
- `<contexto mínimo necessário>`

Restrições obrigatórias:
- Leia o código real antes de alterar.
- Siga o padrão local de service, repository, schemas, models e tests.
- Regra de negócio fica no backend/service, não no front.
- Não fazer gambiarra nem reaproveitar campo com outro significado.
- Não criar abstração nova sem necessidade real.
- Não vazar segredo, token, payload sensível ou stack trace em resposta/log.
- Não fazer push.
- Seguir a política de atribuição de commit definida em `global/commit_policy.md`.

Critérios de aceite:
- `<critério 1>`
- `<critério 2>`
- `<critério 3>`

Validação esperada:
- Rodar teste específico da mudança.
- Rodar suíte aplicável se o custo/tempo for aceitável.
- Informar comandos executados e resultado.
- Informar arquivos alterados e motivo.
