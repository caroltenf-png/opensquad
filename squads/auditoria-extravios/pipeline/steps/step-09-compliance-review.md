---
step: "09"
name: "Revisão de Compliance"
type: agent
agent: compliance-reviewer
optional: true
description: A Cida Compliance audita o relatório contra os critérios de qualidade e os anti-padrões, com nota e pendências.
---

# ✅ Step 09 — Revisão de Compliance (opcional)

## Para o Pipeline Runner

Acionar a **Cida Compliance** (`compliance-reviewer`) com a task `validate-compliance`.

## Entrada
- `output/audit-report.md`
- `pipeline/data/quality-criteria.md`
- `pipeline/data/anti-patterns.md`

## Saída esperada
- `output/compliance-review.md` (nota 0-100 + pendências)

## Ação
1. Rodar o checklist e a amostra de rastreabilidade.
2. Se houver **veto** ou nota < 70: devolver ao Step 07 para correção e repetir.
3. Se aprovado (≥85) ou aprovado com ressalvas (70-84): encerrar o pipeline.
   Entregas finais: `audit-report.md` + `compliance-review.md`.
