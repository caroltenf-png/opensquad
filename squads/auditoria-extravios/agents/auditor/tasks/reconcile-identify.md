---
task: "Reconcile and Identify Losses"
order: 1
input:
  - normalized_dataset: Dataset normalizado (output/normalized-dataset.yaml)
  - classification_framework: Framework de classificação (pipeline/data/classification-framework.md)
output:
  - discrepancies: Todas as divergências esperado x realizado (output/discrepancies.yaml)
  - loss_findings: Extravios identificados e classificados (output/loss-findings.yaml)
---

# Reconcile and Identify Losses

Reconcilia o esperado x realizado, identifica cada divergência e classifica os
extravios usando o framework canônico.

## Process

1. **Reconciliar por chave** (SKU + estágio + período). Para cada chave: `divergencia = qty_expected − qty_actual`.
2. **Separar tipos de divergência:** falta (positiva), sobra (negativa), e zero. Sobras entram no relatório — não são descartadas.
3. **Cruzar com evidências.** Para cada falta, procurar nos registros de ocorrência, POD e logs uma explicação (ocorrência registrada, avaria, erro de baixa, etc.).
4. **Classificar** cada caso pelo `classification-framework.md`: `tipo`, `severidade` (preliminar, confirmada na próxima task), `stage`, `confianca`.
5. **Aplicar a regra de evidência.** Furto só com evidência documental; senão, `NAO_IDENTIFICADO` / confiança `BAIXA`.
6. **Fechar a conta.** Calcular o resíduo: divergência total − soma dos extravios explicados. Declarar o resíduo explicitamente.
7. **Salvar** `discrepancies.yaml` e `loss-findings.yaml`.

## Output Format (loss-findings.yaml)

```yaml
period: "2026-05-01 a 2026-05-31"
total_discrepancies: 38
total_losses_identified: 31
residual_unexplained_units: 7

findings:
  - case_id: "EXT-001"
    sku: "SKU-1042"
    description: "Fone Bluetooth X"
    stage: "TRANSPORTE"
    qty_lost: 3
    type: "EXTRAVIO_TRANSITO"
    severity: "MEDIA"
    confidence: "MEDIA"
    evidence:
      - "expedicao.csv:142 (50 embarcados)"
      - "entregas.csv:88 (47 recebidos, sem POD da diferença)"
    notes: "Sem registro de ocorrência; rota CD-SP→Campinas"
```

## Quality Criteria

- [ ] Toda divergência (falta E sobra) está em discrepancies.yaml
- [ ] Todo extravio tem tipo, severidade, estágio, confiança e evidência
- [ ] Classificações de furto têm evidência documental
- [ ] O resíduo não identificado está declarado numericamente
- [ ] Nenhuma pessoa é nomeada/responsabilizada

## Veto Conditions

Rejeitar e refazer se:
1. A reconciliação não fecha e o resíduo não foi declarado
2. Há classificação de furto sem evidência
3. Sobras de estoque foram ignoradas
4. Algum caso ficou sem classificação
