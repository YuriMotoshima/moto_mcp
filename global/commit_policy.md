# Política de commit — TEMPLATE, definir por projeto

Regras genéricas, válidas até o usuário definir a política específica:

- Nenhum commit ou push deve ser feito sem que o fluxo já tenha autorizado localmente, ou
  sem pedido explícito para push.
- Mensagem de commit objetiva, descrevendo o que mudou e por quê.
- Antes de commitar, conferir o working tree para não misturar alterações não
  relacionadas.
- Se houver alterações abertas de outro agente/pessoa no mesmo repo, preservar e separar
  quando possível; se a separação ficar insegura, avisar o usuário antes de commitar.
- Separar commits por tema/alteração lógica quando houver mais de uma frente no mesmo
  turno.

## Atribuição de autoria — decisão do usuário, não uma regra fixa deste template

Times diferentes têm preferências diferentes sobre citar ferramenta de IA em commits
(alguns preferem trailer neutro tipo `Co-Authored-By: <ferramenta>`, outros preferem não
mencionar nenhuma ferramenta, por posicionamento de marca ou política interna). **Este
template não impõe nenhuma das duas** — defina aqui a política real do seu projeto antes
de usar em produção:

```text
[Preencher: trailer de atribuição a usar, ou "nenhum" se a política for não mencionar
ferramenta de IA em nenhum commit]
```

Push continua exigindo pedido explícito do usuário independente da política escolhida
aqui.
