# Handoff - Deploy Checklists

Checklist operacional para VPS, containers, domínio, TLS, healthcheck e logs.

- Identificar projeto do compose.
- Confirmar portas locais e reverse proxy.
- Confirmar secrets/env.
- Subir serviços em ordem segura quando necessário.
- Validar health interno e público.
- Validar workers e cache/fila quando aplicável.
- Validar banco/storage quando aplicável.
- Não usar prune/delete amplo sem confirmação explícita do escopo.
