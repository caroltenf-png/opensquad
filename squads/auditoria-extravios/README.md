# 🔎 Squad: Auditoria de Extravios

Equipe de auditoria que identifica, classifica e quantifica extravios
(mercadorias, ativos ou valores), investiga a causa raiz e entrega um
relatório de auditoria com recomendações de prevenção.

## Equipe

| Agente | Papel |
|--------|-------|
| 🗂️ Clara Coleta | Coleta e normaliza os registros num dataset auditável |
| 🔎 Aurélio Auditor | Reconcilia esperado x realizado, classifica e quantifica os extravios |
| 📊 Renata Risco | Encontra padrões, causa raiz e recomendações priorizadas por risco |
| 📝 Rafael Relato | Consolida tudo no relatório de auditoria executivo |
| ✅ Cida Compliance | Audita o relatório contra critérios de qualidade (opcional) |

## Pipeline (9 passos, 4 checkpoints)

1. 🛑 **Definição do Escopo** — período, unidades, fontes, materialidade
2. 🗂️ Coleta e Normalização de Dados
3. 🛑 **Validação dos Dados Coletados**
4. 🔎 Reconciliação e Identificação de Extravios
5. 🛑 **Aprovação dos Extravios Identificados**
6. 📊 Análise de Causa Raiz e Padrões
7. 📝 Geração do Relatório de Auditoria
8. 🛑 **Aprovação do Relatório**
9. ✅ Revisão de Compliance *(opcional)*

## Como executar

Na sua IDE (Claude Code), com a pasta do projeto aberta:

```
/opensquad rode o squad auditoria-extravios
```

Antes de rodar, coloque suas fontes de dados (CSV/XLSX exportados do
ERP/WMS — inventário, expedição, POD, ocorrências) em
`squads/auditoria-extravios/output/sources/`, ou informe os caminhos no
checkpoint de escopo.

## Entregas

- `output/audit-report.md` — relatório de auditoria final
- `output/financial-impact.yaml` — impacto financeiro consolidado
- `output/root-cause-analysis.md` — causa raiz e recomendações
- `output/compliance-review.md` — revisão de qualidade (se executada)

> ⚠️ Este squad **não acusa pessoas**. Classificações de furto exigem
> evidência documental; na ausência, o caso é registrado como
> `NAO_IDENTIFICADO`.
