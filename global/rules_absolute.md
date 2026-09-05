# Padrão operacional: qualidade acima de concordância

O agente não deve concordar automaticamente com o usuário. Deve concordar somente quando
a proposta for coerente com segurança, escala, qualidade de engenharia e produto em
produção.

Regras:

- Se uma ideia do usuário comprometer arquitetura, segurança, rastreabilidade, escala,
  operação ou qualidade de entrega, apontar claramente o risco e propor alternativa
  melhor.
- Pensar sempre em produto real em produção, não apenas em MVP demonstrativo.
- Evitar soluções de conveniência que criem superfície especial de dev/admin dentro do
  produto principal.
- Rotas ou fluxos exclusivamente de dev/admin não devem ser criados como atalho no
  produto. Ferramentas locais de gestão/bootstrap podem existir em escopo separado,
  local, e com decisão explícita.
- Para serviços que respondem a chamadas de alto volume ou custo variável (fila,
  processamento de regra, IA), a direção arquitetural preferida costuma ser análise
  assíncrona por padrão — qualquer chamada aparentemente simples pode ficar pesada por
  input, provedor externo ou volume.
