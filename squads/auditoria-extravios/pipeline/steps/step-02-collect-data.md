---
step: "02"
name: "Coleta e Normalização de Dados"
type: agent
agent: data-collector
description: A Clara Coleta lê as fontes, normaliza num dataset único e reporta a qualidade dos dados.
---

# 🗂️ Step 02 — Coleta e Normalização de Dados

## Para o Pipeline Runner

Acionar a **Clara Coleta** (`data-collector`) com a task `collect-normalize`.

## Entrada
- `output/audit-scope.md`
- Fontes em `output/sources/` (ou caminhos informados no escopo)

## Saída esperada
- `output/normalized-dataset.yaml`
- `output/data-quality-report.md`

## Ação
1. Executar a task de coleta e normalização.
2. Não interpretar nem classificar nada aqui — apenas organizar e sinalizar problemas.
3. Avançar para o Step 03 (checkpoint de validação).
