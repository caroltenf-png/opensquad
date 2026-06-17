---
task: "Quantify Financial Impact"
order: 2
input:
  - loss_findings: Extravios classificados (output/loss-findings.yaml)
  - normalized_dataset: Dataset normalizado (para custo unitário)
output:
  - financial_impact: Impacto financeiro consolidado (output/financial-impact.yaml)
---

# Quantify Financial Impact

Atribui valor financeiro a cada extravio e consolida o impacto por tipo, estágio
e severidade.

## Process

1. **Valorar cada caso:** `valor = qty_lost × unit_cost`. Declarar a `cost_source`.
2. **Casos sem custo:** marcar `valor: a_confirmar` e listá-los à parte — nunca chutar.
3. **Confirmar a severidade** de cada caso conforme as faixas do framework (recalibrar se o valor mudar a faixa).
4. **Consolidar** os totais por: tipo, estágio do fluxo, severidade e unidade/CD.
5. **Calcular o shrinkage:** `valor_total_perdido / valor_total_movimentado` no período (se o movimentado estiver disponível).
6. **Salvar** `financial-impact.yaml`.

## Output Format

```yaml
currency: "BRL"
total_loss_value: 18450.30
value_pending_confirmation: 1200.00   # casos sem custo unitário
shrinkage_rate: 0.014                  # 1,4% do movimentado (null se indisponível)

by_type:
  EXTRAVIO_TRANSITO: 9800.00
  AVARIA: 4100.30
  ERRO_SISTEMA: 0.00        # ajuste, não é perda real
  NAO_IDENTIFICADO: 4550.00

by_stage:
  TRANSPORTE: 9800.00
  ARMAZENAGEM: 4100.30
  ENTREGA: 4550.00

by_severity:
  CRITICA: 0
  ALTA: 1
  MEDIA: 12
  BAIXA: 18

top_cases:
  - case_id: "EXT-014"
    value: 6200.00
    type: "EXTRAVIO_TRANSITO"
```

## Quality Criteria

- [ ] Todo caso tem valor OU está marcado como `a_confirmar` com a razão
- [ ] `cost_source` declarada para cada valor
- [ ] Erro de sistema NÃO entra como perda financeira real
- [ ] A soma por tipo/estágio/severidade bate com o total
- [ ] Shrinkage calculado (ou declarado indisponível)

## Veto Conditions

Rejeitar e refazer se:
1. Algum valor foi estimado sem fonte de custo
2. Os totais consolidados não batem com a soma dos casos
3. Ajuste de sistema foi contado como perda
