---
step: "06"
name: "Análise de Causa Raiz e Padrões"
type: agent
agent: risk-analyst
description: A Renata Risco encontra concentrações, infere causas raiz e propõe recomendações priorizadas por risco.
---

# 📊 Step 06 — Análise de Causa Raiz e Padrões

## Para o Pipeline Runner

Acionar a **Renata Risco** (`risk-analyst`) com a task `root-cause-analysis`.

## Entrada
- `output/loss-findings.yaml`
- `output/financial-impact.yaml`

## Saída esperada
- `output/root-cause-analysis.md`

## Ação
1. Pareto + identificação de hot spots por estágio/rota/SKU/turno.
2. Inferir causa raiz (marcar hipótese x comprovada) e priorizar recomendações por risco.
3. Avançar para o Step 07 (Rafael Relato).
