---
task: "Validate Compliance and Quality"
order: 1
input:
  - audit_report: output/audit-report.md
  - quality_criteria: pipeline/data/quality-criteria.md
  - anti_patterns: pipeline/data/anti-patterns.md
output:
  - compliance_review: Revisão de conformidade com nota e pendências (output/compliance-review.md)
---

# Validate Compliance and Quality

Audita o relatório final contra os critérios de qualidade e os anti-padrões,
atribui uma nota de conformidade e lista pendências.

## Process

1. **Rodar o checklist** do `quality-criteria.md`, item por item (rastreabilidade, reconciliação, classificação, imparcialidade, acionabilidade).
2. **Verificar anti-padrões** do `anti-patterns.md`. Qualquer ocorrência grave é veto.
3. **Amostrar a rastreabilidade:** escolher 3-5 números do relatório e confirmar que existem nos artefatos de origem.
4. **Atribuir nota** de 0 a 100 e classificar: aprovado (≥85), aprovado com ressalvas (70-84), reprovado (<70).
5. **Listar pendências** — cada veto com artefato, item exato e ação para resolver.
6. **Salvar** `compliance-review.md`.

## Output Format

```markdown
# Revisão de Compliance

**Nota:** 88/100 — **Aprovado**

## Checklist
- [x] Rastreabilidade — OK (amostra de 5 números confere)
- [x] Reconciliação fecha / resíduo declarado
- [ ] Imparcialidade — RESSALVA: seção 5 usa "negligência da equipe"

## Vetos (bloqueiam aprovação)
(nenhum)

## Ressalvas (registradas, não bloqueiam)
- Seção 5: substituir linguagem que sugere culpa por descrição factual

## Verificação de Rastreabilidade (amostra)
| Número no relatório | Artefato de origem | Confere? |
```

## Quality Criteria

- [ ] Todos os itens do quality-criteria.md foram verificados explicitamente
- [ ] A amostra de rastreabilidade foi feita e registrada
- [ ] Cada veto aponta artefato + item + ação corretiva
- [ ] A nota é coerente com a quantidade/gravidade das pendências

## Veto Conditions (do próprio relatório auditado)

Reprovar (devolver) se:
1. Há acusação de furto sem evidência
2. Há número sem rastreabilidade até a fonte
3. A reconciliação está aberta sem declarar o resíduo
4. Lacunas de dados materiais não foram declaradas
