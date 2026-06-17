---
step: "05"
name: "Aprovação dos Extravios Identificados"
type: checkpoint
description: O usuário revisa os extravios classificados e o impacto financeiro antes da análise de causa raiz.
---

# 🛑 Checkpoint: Aprovação dos Extravios Identificados

## Para o Pipeline Runner

Apresentar o resumo de `loss-findings.yaml` + `financial-impact.yaml`.

## Apresentação ao Usuário

🔎 Auditoria concluída. Resumo:

- **Extravios identificados:** [N] casos  |  **Resíduo não identificado:** [U] unidades
- **Perda total:** R$ [X]  (shrinkage [Y]%)
- **Por tipo:** [trânsito R$..., avaria R$..., não identificado R$...]
- **Top caso:** [case_id — valor]

Revise especialmente:
- As classificações de tipo (concorda com a evidência?)
- O resíduo não identificado
- Casos com valor "a confirmar"

Deseja:
- ✅ **Aprovar** e seguir para a análise de causa raiz
- ✏️ **Revisar** classificações/casos específicos (informe os case_id)

## Ação do Pipeline Runner

1. Se "revisar": devolver ao Step 04 com os ajustes pedidos.
2. Se "aprovar": avançar para o Step 06 (Renata Risco).
