---
step: "08"
name: "Aprovação do Relatório"
type: checkpoint
description: O usuário aprova o relatório final ou solicita ajustes antes da revisão de compliance.
---

# 🛑 Checkpoint: Aprovação do Relatório

## Para o Pipeline Runner

Apresentar o `audit-report.md` (com foco no sumário executivo).

## Apresentação ao Usuário

📝 Relatório de auditoria pronto. Veja o sumário executivo:

[colar o sumário executivo do relatório]

Deseja:
- ✅ **Aprovar** — segue para a revisão de compliance (opcional, recomendada)
- ✏️ **Ajustar** — informe seções a revisar
- ⏹️ **Finalizar aqui** — pular a revisão de compliance

## Ação do Pipeline Runner

1. Se "ajustar": devolver ao Step 07 com as observações.
2. Se "aprovar": avançar para o Step 09 (Cida Compliance).
3. Se "finalizar": encerrar o pipeline com o relatório atual como entrega final.
