---
name: security-testing-baseline
description: "Security Test Master Checklist — baseline de DESENVOLVIMENTO (não só teste) para qualquer backend/frontend/gateway/worker/integração. Consolida red team local + práticas de appsec, produto, cloud, supply chain e frontend."
metadata:
  type: reference
---

# Security Test Master Checklist

Objetivo: baseline de validação antes de considerar um backend, frontend, gateway,
worker ou integração pronto para uso real. **É base de DESENVOLVIMENTO, não portão de
teste no fim** — entra no dia 1 de cada sistema novo. Toda construção nova **duplica
este checklist** no próprio `docs/` (cópia própria por sistema, não referência a um
único lugar) e nasce sob este padrão.

Escopo seguro: testes autorizados, ambientes locais/test/staging, sem DDoS, sem brute
force destrutivo, sem alvo externo sem autorização explícita.

## Fontes externas consultadas

OWASP WSTG/ASVS/API Security Top 10/Top 10/Cheat Sheets (Authentication, Session
Management, XSS Prevention, SSRF Prevention), MITRE CWE Top 25/ATT&CK/CAPEC, NIST SP
800-115/SSDF SP 800-218/Cybersecurity Framework 2.0, CIS Controls/Benchmarks, PortSwigger
Web Security Academy, MDN Web Security/HTTP Observatory, Microsoft SDL/Threat Modeling
Tool, OpenSSF Scorecard, SLSA, Kubernetes Security Checklist, Cloud Security Alliance
CCM, PCI SSC, OpenID Connect Core, IETF RFC 9700 OAuth 2.0 Security BCP, GraphQL
Security, GitHub Code Security docs, Docker build/security docs.

## Complementos além do red team local básico

- Threat modeling obrigatório por STRIDE/DFD antes de implementar feature sensível.
- Abuso de negócio: fluxos multi-step, desconto, pagamento, convite, reset, aprovação,
  limite, estado e replay fora da ordem feliz.
- Frontend/browser: DOM XSS, Trusted Types, CSP estrita, SRI, source maps, tokens em
  storage, service worker, cache, clickjacking e XS-Leaks.
- OAuth/OIDC: PKCE, nonce/state, redirect URI exata, mix-up, token leakage, confused
  deputy e validação de claims.
- GraphQL, WebSocket, SSE e streaming: authorization por campo/evento, limite de
  profundidade, custo, introspection e desconexão.
- Supply chain: SBOM, provenance, Scorecard, dependency review, pinning, signed builds,
  secret scanning, branch protection e artifact integrity.
- Cloud/container: rootless/non-root, seccomp/AppArmor, capabilities, read-only FS,
  secrets fora da imagem, network policies, egress allowlist, IAM mínimo.
- Cache/proxy: request smuggling, web cache poisoning/deception, host header,
  hop-by-hop headers, cache de resposta autenticada e vary correto.
- Detecção/resposta: alertas para auth abuse, token replay, SSRF blocked, admin actions,
  secrets detected, 5xx spike e egress anômalo.
- Privacy/compliance: minimização, retenção, export/delete, classificação de dados,
  mascaramento e propósito de coleta.

## Lista consolidada por domínio

Prioridade: **P0** bloqueia release se falhar · **P1** corrigir antes de produção ou
documentar risco aceito · **P2** maturidade, pode ser backlog se não houver exposição.

Domínios (ver checklist completo de referência ao adaptar este template): governança e
critério de aceite; threat modeling e superfície de ataque; configuração/secrets/
ambientes; sanidade/build/CI; autenticação/contas/identidade; sessão/cookies/CSRF/
refresh tokens; autorização/RBAC/tenant/IDOR; contratos de API/validação/robustez;
injection/parsing hostil; dados sensíveis/privacidade/criptografia; frontend/browser
security; HTTP/proxy/cache/headers; SSRF/egress/integrações externas; uploads/arquivos/
conteúdo ativo; business logic/estado/concorrência/replay; logs/auditoria/detecção/
resposta; MCP/agents/LLM/ferramentas; DB/cache/fila/resiliência; container/cloud/runtime
hardening; supply chain/dependência; protocolos especiais (GraphQL/WebSocket/SSE/gRPC).

## Bateria mínima por tipo de projeto

**Backend/API mínimo para qualquer release:** sanidade (check/compile/import/test) →
health público/privado e startup sem dependência → auth (sem/inválido/expirado/
revogado/scope) → RBAC/IDOR (A não acessa B em read/list/write/export/log) → validação
(JSON errado/extra/null/unicode/grande) → injection (SQL/NoSQL/command/template/path/
header/log) → sessão/cookies/CSRF/refresh replay se houver browser login → secrets
(response/log/DB/cache/queue/relatório limpos) → SSRF/egress em toda URL externa/
webhook/provider/parser → concorrência/idempotência nos estados críticos → logs/
auditoria/correlation ID → container/supply chain (lock/advisory/image/secrets/
non-root/healthcheck).

**Frontend mínimo para qualquer release:** DOM XSS em toda entrada renderizada (inclui
querystring/hash/localStorage) → bundle/source map sem segredo/token/endpoint/comentário
→ tokens fora de localStorage quando sensíveis, refresh em cookie HttpOnly → CSP/
frame-ancestors/nosniff/referrer/permissions/HTTPS → CORS/CSRF em browser real → rotas
protegidas no front não substituem enforcement no backend → SRI/CDN/dependency audit →
cache/service worker não guarda resposta autenticada → upload/download UI não permite
tipo ativo perigoso sem tratamento → erros de UI sem stacktrace/segredo/payload raw.

**Deep/periódico:** DAST/manual com proxy → OSV/advisories e scan de imagem → threat
modeling atualizado → race em fluxos de dinheiro/permissão/token/convite/job → request
smuggling/cache poisoning quando houver proxy/CDN → GraphQL/WebSocket/SSE quando
existirem → cloud/IAM/K8s/CIS quando houver deploy cloud → incident response tabletop
(secret leak, token replay, provider compromise).

## Como usar em novos projetos

1. **Duplicar** esta matriz no `docs/` do sistema novo (cópia própria — cada sistema tem
   a sua, é base de desenvolvimento desde o dia 1, não referência a um lugar único).
2. Marcar cada item `Aplicável` / `Não aplicável` / `Backlog`.
3. Todo `P0 Aplicável` precisa de teste automatizado, teste manual registrado ou risco
   aceito por escrito.
4. Todo backend novo recebe ao menos a bateria mínima antes de "pronto".
5. Todo frontend novo recebe a bateria mínima de browser security antes de expor login/
   dados sensíveis/operação autenticada.
6. Para cada achado: evidência, impacto, reprodução, fix sugerido e comando de
   revalidação.

## Checklist curta para PR/review

- Auth/scopes/tenant estão no backend e no repositório?
- Algum dado sensível aparece em response/log/cache/DB/bundle?
- Alguma URL externa/webhook/provider/upload/parser abre SSRF/path risk?
- Algum estado crítico pode sofrer replay/race/idempotency bug?
- Alguma dependência/imagem/action/script novo aumenta supply chain risk?
- Frontend introduziu XSS, storage de token, CSP fraca ou source map sensível?
- Proxy/cache/CORS/cookies mudaram?
- Existe teste ou evidência real, não apenas mock feliz?
