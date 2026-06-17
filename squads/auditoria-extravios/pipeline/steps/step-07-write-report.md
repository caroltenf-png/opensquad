---
step: "07"
name: "Geração do Relatório de Auditoria"
type: agent
agent: report-writer
description: O Rafael Relato consolida todos os artefatos no relatório de auditoria executivo.
---

# 📝 Step 07 — Geração do Relatório de Auditoria

## Para o Pipeline Runner

Acionar o **Rafael Relato** (`report-writer`) com a task `write-report`.

## Entrada
- `output/audit-scope.md`, `output/loss-findings.yaml`, `output/financial-impact.yaml`,
  `output/root-cause-analysis.md`, `output/data-quality-report.md`

## Saída esperada
- `output/audit-report.md`

## Ação
1. Consolidar sem introduzir números novos.
2. Sumário executivo de uma página + lacunas destacadas.
3. Avançar para o Step 08 (checkpoint de aprovação do relatório).
