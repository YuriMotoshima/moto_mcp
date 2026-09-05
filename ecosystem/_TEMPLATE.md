---
name: ecosystem
description: Visão geral da empresa/produto do usuário e como os projetos se relacionam. TEMPLATE — preencher com o contexto real.
metadata:
  type: project
---

# [Nome da empresa/ecossistema]

Preencher com:

- O que a empresa/produto faz.
- Linhas de negócio, se houver mais de uma.
- Lista de projetos/repositórios que compõem o ecossistema, com uma linha de propósito
  cada (detalhe completo vai em `projects/<nome>.md`).
- Infraestrutura compartilhada (hospedagem, banco, deploy) que vale saber antes de
  trabalhar em qualquer projeto do ecossistema.
- Padrões de segurança/qualidade que todo projeto novo deve seguir desde o dia 1.

## Domínios/URLs de produção

Preencher se aplicável — domínio, o que cada subdomínio serve.

## Paridade de padrões entre projetos

Preencher o que os projetos do ecossistema compartilham por convenção (stack, padrão de
auth, infraestrutura) — isso evita reinventar convenção projeto a projeto.

**Why:** qualquer agente trabalhando em qualquer projeto do ecossistema deve entender o
contexto completo sem reexplicar do zero a cada sessão.
