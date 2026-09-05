# START HERE - Agent Memory

Esta é a fonte central de contexto para Claude, Codex, Gemini, Copilot e qualquer outro
agente de IA usado neste ecossistema. Este repositório é genérico e reutilizável — não
contém identidade de empresa, cliente ou pessoa específica. Preencha `global/user_profile.md`,
`ecosystem/`, `clients/` e `projects/` com o conteúdo real do seu contexto.

## Ordem obrigatória de leitura

1. Leia `global/user_profile.md`.
2. Leia `global/workflow.md`.
3. Leia `global/rules_absolute.md`.
4. Leia `global/commit_policy.md`.
5. Leia `ecosystem/` quando a tarefa envolver a empresa, produto, clientes, infraestrutura
   ou deploy do usuário.
6. Leia o arquivo em `projects/` quando a tarefa envolver um projeto específico.
7. Leia `knowledge/security/security_testing_baseline.md` quando a tarefa envolver
   segurança, testes adversariais, validação, pentest ou deploy seguro.
8. Leia o arquivo em `clients/` quando a tarefa envolver um cliente específico.
9. Leia `agents/<nome>.md` somente quando a tarefa chamar uma especialidade/persona.
10. Leia `knowledge/<tema>/` quando a tarefa exigir base conceitual ou técnica.

## Regra de manutenção: todo projeto/cliente novo ganha um arquivo

Sempre que o usuário introduzir um projeto novo ou um cliente novo:

1. Criar um arquivo próprio em `projects/<nome>.md` ou `clients/<nome>.md`, usando
   `projects/_TEMPLATE.md` ou `clients/_TEMPLATE.md` como ponto de partida.
2. Registrar no índice correspondente (`clients/_index.md` para clientes; para projetos,
   listar em `INDEX.md`).
3. Não misturar contexto de projetos/clientes diferentes no mesmo arquivo.
4. Não presumir ou inventar contexto — se a informação não foi dada, deixar como
   pendência explícita no próprio arquivo.

## Regras absolutas

- Responder curto, direto e com conclusão primeiro.
- Não declarar pronto, seguro, testado ou aprovado sem evidência real.
- Não concordar por reflexo; discordar quando houver risco técnico, segurança, escala,
  rastreabilidade ou qualidade.
- Quando o usuário disser "anote", apenas registrar; não alterar código.
- Antes de alterar repo, ler o código e respeitar padrão local.
- Regra de negócio fica no backend/service, não sob responsabilidade do front.
- Sem gambiarra, sem jeitinho, sem reaproveitar campo com outro significado.
- Commit local somente quando solicitado ou quando o fluxo já autorizou; push somente
  com pedido explícito.
- Política de atribuição em commit é definida pelo usuário em `global/commit_policy.md`
  — não presumir uma regra de marca específica sem o usuário definir.

## Regra de segurança

Não salvar secrets, tokens, chaves, `.env` real, credenciais, senhas ou dados sensíveis
nesta memória.

## Leitura complementar consolidada

- Para colaboração e estilo fino de trabalho, leia `global/user_profile.md` e
  `global/workflow.md`.
- Para política de commit, leia `global/commit_policy.md`.
- Para revisão técnica, leia `agents/mike.md` e `agents/mike_review.md`.
- Para segurança/testes transversais, leia `knowledge/security/security_testing_baseline.md`.
