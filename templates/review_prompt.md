# Template - Review

Use este modelo para pedir uma revisão rigorosa.

## Prompt

Revise a entrega abaixo com postura de segurança, qualidade e produto em produção.

Contexto:
- Projeto:
- Objetivo da mudança:
- Base/hash anterior:
- Hash/branch atual:

Escopo da revisão:
- Conferir se a entrega atende exatamente o pedido.
- Ler o código real, não confiar apenas no resumo.
- Separar achado real de melhoria futura.
- Apontar arquivo/linha quando houver risco.
- Verificar regra de negócio no backend/service.
- Verificar segurança, tenant, auth, logs, dados sensíveis e rastreabilidade quando
  aplicável.

Formato esperado:
- Resultado: aprovado / aprovado com ressalvas / reprovado.
- Findings por severidade.
- Testes conferidos.
- O que não foi testado.
- Próxima ação objetiva.
