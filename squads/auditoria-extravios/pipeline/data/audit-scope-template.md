# Template — Escopo da Auditoria

Estrutura que o checkpoint de entrada (step-01) salva em `output/audit-scope.md`.

```markdown
# Escopo da Auditoria de Extravios

**Período auditado:** [data início] a [data fim]
**Unidades/CDs:** [lista de centros de distribuição, lojas ou filiais]
**Categorias de item:** [todas | SKUs específicos | famílias de produto]
**Tipo de extravio sob foco:** [todos | apenas trânsito | apenas inventário | ...]
**Materialidade mínima:** [valor a partir do qual um caso é investigado; ex: R$ 100]

## Fontes de Dados Fornecidas
- [ ] Registro de estoque / inventário (esperado x contado)
- [ ] Notas fiscais / registros de expedição
- [ ] Comprovantes de entrega (canhotos, POD)
- [ ] Registros de ocorrência (B.O., sinistros, reclamações)
- [ ] Logs do WMS/ERP
- [ ] Outros: [descrever]

## Objetivo
[O que a gestão quer responder com esta auditoria]
```

## Notas
- Se uma fonte de dados não for fornecida, o escopo deve registrar a **lacuna**
  e o impacto dela na confiança das conclusões.
- A materialidade mínima evita que ruído de centavos consuma a auditoria.
