---
task: "Write Audit Report"
order: 1
input:
  - audit_scope: output/audit-scope.md
  - loss_findings: output/loss-findings.yaml
  - financial_impact: output/financial-impact.yaml
  - root_cause_analysis: output/root-cause-analysis.md
  - data_quality_report: output/data-quality-report.md
output:
  - audit_report: Relatório de auditoria consolidado (output/audit-report.md)
---

# Write Audit Report

Consolida todos os artefatos num relatório de auditoria executivo e rastreável.

## Process

1. **Reunir os artefatos.** Não introduzir nenhum número novo — tudo vem dos arquivos de entrada.
2. **Escrever o sumário executivo** (1 página): quanto se perdeu, onde, por quê e o que fazer.
3. **Detalhar** escopo/metodologia, achados, impacto financeiro, causa raiz e recomendações.
4. **Destacar lacunas e limitações** a partir do `data-quality-report.md` e do resíduo não identificado.
5. **Montar anexos** com a tabela completa de casos.
6. **Salvar** `audit-report.md`.

## Estrutura do Relatório

```markdown
# Relatório de Auditoria de Extravios — [período]

## 1. Sumário Executivo
- Perda total: R$ X (shrinkage Y%)
- Principal concentração: [hot spot]
- Causa raiz predominante: [...]
- Top 3 recomendações: [...]

## 2. Escopo e Metodologia
[período, unidades, fontes, materialidade, como foi feito]

## 3. Achados
[tabela resumo por tipo/estágio/severidade]

## 4. Impacto Financeiro
[totais, por tipo, top casos, valor a confirmar]

## 5. Análise de Causa Raiz
[hot spots e padrões]

## 6. Recomendações Priorizadas
[tabela acionável]

## 7. Lacunas e Limitações
[dados ausentes, resíduo não identificado, impacto na confiança]

## Anexo A — Tabela Completa de Casos
```

## Quality Criteria

- [ ] Todo número do relatório existe nos artefatos de origem
- [ ] Sumário executivo cabe em uma página e responde quanto/onde/porquê/o quê
- [ ] Lacunas de dados e resíduo não identificado estão destacados
- [ ] Hipóteses não viram afirmações categóricas
- [ ] Toda recomendação está ancorada num achado
- [ ] Nenhuma pessoa é nomeada/responsabilizada

## Veto Conditions

Rejeitar e refazer se:
1. O relatório introduz dados que não estão nos artefatos
2. O impacto financeiro foi suavizado ou inflado
3. O resíduo não identificado foi omitido
