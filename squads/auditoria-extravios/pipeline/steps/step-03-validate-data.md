---
step: "03"
name: "Validação dos Dados Coletados"
type: checkpoint
description: O usuário revisa o relatório de qualidade e decide se segue, complementa fontes ou ajusta o escopo.
---

# 🛑 Checkpoint: Validação dos Dados Coletados

## Para o Pipeline Runner

Apresentar ao usuário um resumo do `data-quality-report.md`.

## Apresentação ao Usuário

📋 Dados consolidados. Antes de auditar:

- **Registros no escopo:** [X]  |  **Descartados:** [Y]
- **Lacunas relevantes:** [listar]
- **Custo unitário ausente em:** [Z%] dos registros

Como deseja seguir?
- ✅ **Seguir** com os dados atuais (as lacunas constarão como limitação no relatório)
- 📎 **Complementar** fornecendo as fontes faltantes
- 🎯 **Ajustar o escopo** (período/unidades/materialidade)

## Ação do Pipeline Runner

1. Se "complementar" ou "ajustar": voltar ao Step 02 (ou 01) com os novos insumos.
2. Se "seguir": avançar para o Step 04 (Aurélio Auditor).
