---
task: "Collect and Normalize Data"
order: 1
input:
  - audit_scope: Escopo da auditoria (lido de output/audit-scope.md)
  - source_files: Arquivos de dados fornecidos pelo usuário (CSV/XLSX/registros em output/sources/ ou caminhos informados)
output:
  - normalized_dataset: Dataset único e auditável (output/normalized-dataset.yaml)
  - data_quality_report: Relatório de qualidade dos dados (output/data-quality-report.md)
---

# Collect and Normalize Data

Lê todas as fontes de dados fornecidas, consolida num dataset único com schema
consistente e produz um relatório de qualidade apontando lacunas e inconsistências.

## Process

1. **Ler o `audit-scope.md`.** Fixar período, unidades, categorias e materialidade mínima.
2. **Inventariar as fontes.** Para cada arquivo/fonte: nome, tipo, nº de linhas, período coberto, colunas presentes.
3. **Mapear o schema.** Reconciliar nomes de coluna divergentes para o schema canônico abaixo. Registrar cada mapeamento aplicado.
4. **Normalizar.** Padronizar datas (YYYY-MM-DD), unidades de medida, e identificadores (SKU, nº de documento). Manter sempre o `source_ref` (arquivo + linha original).
5. **Filtrar pelo escopo.** Descartar registros fora do período/unidade. Contar quantos foram descartados e por quê.
6. **Marcar problemas (não corrigir):** valores ausentes, duplicidades, datas inválidas, quantidades negativas inesperadas, unidades inconsistentes.
7. **Salvar** `normalized-dataset.yaml` e `data-quality-report.md`.

## Schema Canônico (por registro)

```yaml
- source_ref: "expedicao.csv:142"
  doc_id: "NF-00831"
  stage: "EXPEDICAO"          # RECEBIMENTO|ARMAZENAGEM|SEPARACAO|EXPEDICAO|TRANSPORTE|ENTREGA
  sku: "SKU-1042"
  description: "Fone Bluetooth X"
  unit: "UN"
  qty_expected: 50
  qty_actual: 47
  unit_cost: 38.90            # null se não informado
  cost_source: "custo_medio"  # custo_medio|ultima_compra|nf|null
  location: "CD-SP / Rua 12"
  date: "2026-05-04"
  flags: ["qty_divergente"]   # vazio se ok
```

## Output Format (data-quality-report.md)

```markdown
# Relatório de Qualidade dos Dados

**Fontes processadas:** N arquivos / M registros
**Registros no escopo:** X  |  **Descartados (fora do escopo):** Y

## Lacunas Identificadas
- [fonte]: [coluna ausente / impacto na auditoria]

## Inconsistências
- Duplicidades: N (linhas: ...)
- Custo unitário ausente: N registros (X% do total)
- Datas inválidas: N

## Cobertura por Fonte
| Fonte | Linhas | Período | Colunas faltantes |
```

## Quality Criteria

- [ ] Todo registro normalizado tem `source_ref` rastreável
- [ ] Nenhum valor ausente foi preenchido por estimativa
- [ ] Descartes fora do escopo foram contados e justificados
- [ ] Duplicidades marcadas, não removidas
- [ ] Relatório declara o % de registros sem custo unitário

## Veto Conditions

Rejeitar e refazer se:
1. Algum registro perdeu o vínculo com a fonte original
2. Valores faltantes foram preenchidos com estimativa
3. O dataset inclui registros fora do período/escopo
