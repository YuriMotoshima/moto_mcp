---
name: workflow
description: Como conduzir desenvolvimento — ciclo incremental, reviews, testes, deploy
metadata:
  type: feedback
---

## Ciclo de desenvolvimento

**Entender → mínimo → testar → validar → avançar.**

Nunca pular etapas. Nunca propor solução grande antes de validar o menor pedaço.

1. **Entender**: ler o código existente antes de propor qualquer mudança. Nunca assumir.
2. **Mínimo**: implementar o menor pedaço que resolve o problema concreto.
3. **Testar**: rodar localmente antes de commitar.
4. **Validar**: aguardar confirmação do usuário antes de avançar.
5. **Avançar**: só então passar para o próximo item.

## Durante baterias de teste

- Quando o usuário disser "estou passando testes, anote mas não altere": registrar
  apenas, não tocar em código.
- Alterar código no meio do ciclo de teste contamina os resultados.
- Só fazer correções quando ele disser explicitamente "faz os fixes".

## Code review e testes de segurança

- Reviews são feitos por arquivo/módulo, não por feature inteira de uma vez.
- Achados de teste vão para um registro com status (resolvido / risco aceito).
- Nenhum achado crítico vai para produção sem resolução.

## Padrões de código

- **Sem comentários óbvios**: comentar apenas o WHY não-óbvio — restrição oculta,
  invariante sutil, workaround de bug específico.
- **Sem abstrações prematuras**: três linhas similares são melhores que abstração
  prematura.
- **Sem error handling para cenários impossíveis**: confiar nas garantias do framework.
- **Sem backwards-compatibility hacks**: se algo não é usado, deletar.
- **Qualidade acima de tudo**: corrigir direito, sem gambiarra, sem jeitinho.
- **Nunca reutilizar campo que claramente significa outra coisa.**

## Rigor de entrega

Declarar algo "pronto/aprovado/estável" antes da evidência sustentar isso é uma causa
comum de retrabalho. Regra: só usar "aprovado"/"validado"/"estável" quando a alegação
específica foi medida de fato (teste rodou, output real observado); caso contrário,
"parcial"/"pendente"/"smoke". Antes de entregar, caçar ativamente race
condition/concorrência/edge case no que mudou — não assumir ausência. Se a mesma área
está sendo redesenhada pela 2ª vez, parar e escrever por que a tentativa anterior falhou
antes de codar de novo.

## Subagentes

Um subagente não herda automaticamente esta memória nem nenhuma persona — só sabe o que
estiver escrito no prompt dele. Ao delegar trabalho que toca código/docs/decisão, incluir
no prompt o essencial deste arquivo (rigor de entrega, "entender→mínimo→testar→validar",
sem gambiarra) — não só caminhos de arquivo e a tarefa mecânica.

## Infraestrutura e deploy

- Testar localmente antes de qualquer deploy.
- Deploy incremental, com validação em cada etapa.
- Nunca subir sem validação local primeiro.
- Segredos de produção nunca commitados — fora do repositório.

## Commits

- Mensagens descritivas, com contexto do "por quê".
- Prefixos sugeridos: `feat:`, `fix:`, `security:`, `chore:`, `docs:`.
- Política de atribuição de autoria é definida em `global/commit_policy.md` — não
  presumir aqui.
- Quando o usuário confirma que quer commitar uma mudança já testada, isso pode valer
  como instrução permanente pra esse tipo de situação — perguntar se é esse o caso, não
  assumir por padrão.

## Comunicação com o agente

- Respostas curtas — uma coisa por vez.
- Perguntas diretas esperam respostas diretas — sem opções demais.
- Quando o usuário confirma ("sim", "ok"), executar — não pedir mais confirmação para a
  mesma coisa.
- Quando discordar, apontar com evidência — não suavizar.

**Why:** um método de colaboração explícito evita reexplicar do zero a cada sessão.
