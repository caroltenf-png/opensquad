---
task: "Root Cause and Pattern Analysis"
order: 1
input:
  - loss_findings: Extravios classificados (output/loss-findings.yaml)
  - financial_impact: Impacto financeiro (output/financial-impact.yaml)
output:
  - root_cause_analysis: Análise de causa raiz, padrões e recomendações (output/root-cause-analysis.md)
---

# Root Cause and Pattern Analysis

A partir dos extravios aprovados, encontra concentrações, infere causas raiz e
propõe recomendações de prevenção priorizadas por risco.

## Process

1. **Agrupar e contar** os casos por estágio, tipo, SKU/família, unidade/CD, rota, turno e período.
2. **Pareto.** Identificar os poucos grupos que concentram a maior parte do **valor** perdido.
3. **Para cada hot spot, inferir a causa raiz** (falha de processo/controle), distinguindo causa de sintoma. Marcar o nível: `comprovada` x `hipótese`.
4. **Avaliar risco** de cada padrão: `impacto financeiro × recorrência × facilidade de exploração da falha` → score `BAIXO/MEDIO/ALTO/CRITICO`.
5. **Recomendar.** Para cada padrão relevante, ao menos uma ação específica (o quê, onde, responsável sugerido, esforço, ganho esperado).
6. *(Opcional)* usar `web_search` apenas para benchmark de boas práticas de prevenção de perdas — citar a fonte.
7. **Salvar** `root-cause-analysis.md`.

## Output Format

```markdown
# Análise de Causa Raiz e Padrões

## Concentração (Pareto)
| Hot spot | Casos | Valor | % do total |
|----------|-------|-------|-----------|
| Rota CD-SP→Campinas (TRANSPORTE) | 9 | R$ 9.800 | 53% |

## Padrões e Causa Raiz
### Padrão 1 — Extravio em trânsito na rota X
- **Evidência:** 9 casos, todos sem POD da diferença, turno noturno
- **Causa raiz (hipótese):** ausência de conferência cega na entrega
- **Risco:** ALTO (recorrente + alto valor)
- **Recomendação:** implantar dupla conferência com foto no recebimento da rota X — resp. sugerido: Logística — esforço: baixo

## Recomendações Priorizadas
| # | Recomendação | Risco mitigado | Esforço | Ganho estimado |
```

## Quality Criteria

- [ ] Hot spots baseados em concentração real, não em caso isolado
- [ ] Causa raiz distinguida de sintoma
- [ ] Hipóteses marcadas como hipóteses
- [ ] Toda recomendação é específica (o quê, onde, responsável)
- [ ] Recomendações priorizadas por risco

## Veto Conditions

Rejeitar e refazer se:
1. Recomendação genérica ("melhorar controles") sem especificar o quê/onde
2. Correlação apresentada como causalidade sem ressalva
3. Conclusão de causa ignora lacuna de dados relevante
