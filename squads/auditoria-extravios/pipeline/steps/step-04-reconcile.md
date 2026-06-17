---
step: "04"
name: "Reconciliação e Identificação de Extravios"
type: agent
agent: auditor
description: O Aurélio Auditor reconcilia esperado x realizado, classifica os extravios e quantifica o impacto financeiro.
---

# 🔎 Step 04 — Reconciliação e Identificação de Extravios

## Para o Pipeline Runner

Acionar o **Aurélio Auditor** (`auditor`) com as tasks, em ordem:
1. `reconcile-identify`
2. `quantify-impact`

## Entrada
- `output/normalized-dataset.yaml`
- `pipeline/data/classification-framework.md`

## Saída esperada
- `output/discrepancies.yaml`
- `output/loss-findings.yaml`
- `output/financial-impact.yaml`

## Ação
1. Reconciliar e classificar (regra de evidência para furto; declarar resíduo).
2. Quantificar o impacto financeiro (sem estimar custo sem fonte).
3. Avançar para o Step 05 (checkpoint de aprovação dos achados).
