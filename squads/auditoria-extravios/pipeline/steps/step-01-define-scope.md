---
step: "01"
name: "Definição do Escopo"
type: checkpoint
description: O usuário define período, unidades, categorias, materialidade e quais fontes de dados serão auditadas.
---

# 🛑 Checkpoint: Definição do Escopo

## Para o Pipeline Runner

Checkpoint de entrada. Coletar o escopo da auditoria e localizar as fontes de dados.

## Solicitação ao Usuário

🔎 Vamos auditar extravios.

1. **Período** a auditar? (ex: "maio/2026", "01/04 a 30/06/2026")
2. **Unidades / CDs / lojas** no escopo? (ex: "CD-SP e CD-RJ", "todas")
3. **Categorias de item**? (todas, famílias específicas ou SKUs)
4. **Materialidade mínima** — a partir de que valor um caso deve ser investigado? (ex: R$ 100)
5. **Fontes de dados** disponíveis e onde estão (coloque os arquivos em `output/sources/` ou informe os caminhos):
   - Inventário (esperado x contado), expedição/NF, comprovantes de entrega (POD), registros de ocorrência, logs do WMS/ERP.

## Ação do Pipeline Runner

1. Receber as respostas e conferir se há pelo menos uma fonte de dados utilizável.
2. Salvar em `output/audit-scope.md` no formato do `pipeline/data/audit-scope-template.md`.
3. Registrar lacunas de fonte já conhecidas.
4. Avançar para o Step 02 (Clara Coleta).
