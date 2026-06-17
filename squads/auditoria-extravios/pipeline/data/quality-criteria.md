# Critérios de Qualidade — Auditoria de Extravios

Critérios transversais que todos os agentes devem respeitar. O Revisor de
Compliance usa esta lista como checklist final.

## Rastreabilidade
- [ ] Todo extravio identificado aponta para os registros de origem (ID do documento, linha, data)
- [ ] Nenhuma conclusão sem dado de suporte rastreável
- [ ] Valores financeiros têm a fonte do custo unitário declarada (custo médio, última compra, NF)

## Reconciliação
- [ ] O esperado x realizado fecha: `esperado − realizado − extravios_explicados = 0` (ou a diferença é declarada como `NAO_IDENTIFICADO`)
- [ ] Divergências positivas (sobra) também são reportadas, não só faltas
- [ ] Ajustes de erro de sistema não são contados como perda real

## Classificação
- [ ] Todo caso tem tipo, severidade, estágio e confiança preenchidos
- [ ] Classificações de furto têm evidência ou são rebaixadas para `NAO_IDENTIFICADO`
- [ ] A soma das severidades bate com o impacto financeiro total

## Imparcialidade
- [ ] Linguagem factual — descreve o que os dados mostram, não acusa pessoas nomeadas sem evidência
- [ ] Hipóteses são marcadas como hipóteses, não como fato

## Acionabilidade
- [ ] Cada padrão de causa raiz tem ao menos uma recomendação de prevenção
- [ ] Recomendações são específicas (o quê, onde, responsável sugerido), não genéricas
