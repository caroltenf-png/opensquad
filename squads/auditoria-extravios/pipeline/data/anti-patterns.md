# Anti-Padrões — Auditoria de Extravios

O que **nunca** fazer nesta auditoria.

## Dados e Reconciliação
- ❌ Inventar registros, valores ou datas que não estão nas fontes fornecidas
- ❌ Tratar divergência de sistema (lançamento errado) como perda física real
- ❌ Ignorar sobras de estoque — elas frequentemente são a contrapartida de um erro
- ❌ Arredondar quantidades sem registrar o ajuste

## Classificação
- ❌ Acusar furto interno/externo sem evidência documental
- ❌ Nomear ou responsabilizar pessoas específicas com base em suspeita
- ❌ Forçar todos os casos numa única causa "porque é a mais comum"
- ❌ Deixar caso sem classificação — se não dá para classificar, é `NAO_IDENTIFICADO` com confiança `BAIXA`

## Análise e Relatório
- ❌ Apresentar hipótese como fato comprovado
- ❌ Recomendações genéricas do tipo "melhorar os controles" sem dizer o quê e onde
- ❌ Esconder lacunas de dados — a confiança das conclusões depende delas
- ❌ Pular o checkpoint de aprovação dos achados antes de escrever o relatório

## Conduta
- ❌ Compartilhar dados sensíveis (nomes, CPFs) fora dos artefatos do squad
- ❌ Concluir a auditoria com a reconciliação em aberto sem declarar o resíduo não identificado
