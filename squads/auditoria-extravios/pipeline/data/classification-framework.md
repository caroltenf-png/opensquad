# Framework de Classificação de Extravios

Toda ocorrência de extravio identificada deve ser classificada segundo **tipo**,
**severidade** e **estágio do fluxo** onde ocorreu. Este framework é a referência
canônica usada pelo Auditor e pela Analista de Risco.

## 1. Tipo de Extravio

| Código | Tipo | Descrição |
|--------|------|-----------|
| `FURTO_INTERNO` | Furto/desvio interno | Subtração por colaborador, com indício de acesso autorizado |
| `FURTO_EXTERNO` | Furto/roubo externo | Subtração por terceiros (assalto, arrombamento, roubo de carga) |
| `AVARIA` | Avaria/dano | Item danificado em manuseio, armazenagem ou transporte, sem condição de venda |
| `EXTRAVIO_TRANSITO` | Extravio em trânsito | Item embarcado mas não entregue/recebido, sem evidência de furto |
| `ERRO_SISTEMA` | Erro de sistema/registro | Divergência por lançamento incorreto, duplicidade ou baixa não realizada |
| `ERRO_INVENTARIO` | Erro de contagem | Divergência por contagem física incorreta ou unidade de medida trocada |
| `VENCIMENTO` | Perda por validade | Item descartado por vencimento/obsolescência |
| `NAO_IDENTIFICADO` | Causa não identificada | Divergência real porém sem evidência suficiente para classificar |

> Regra: nunca classificar como `FURTO_INTERNO`/`FURTO_EXTERNO` sem evidência
> documental ou correlação clara. Na dúvida, usar `NAO_IDENTIFICADO`.

## 2. Severidade (impacto financeiro do caso)

| Faixa | Critério (valor do extravio) |
|-------|------------------------------|
| `BAIXA` | até R$ 500 |
| `MEDIA` | R$ 501 a R$ 5.000 |
| `ALTA` | R$ 5.001 a R$ 50.000 |
| `CRITICA` | acima de R$ 50.000 **ou** indício de fraude/recorrência |

## 3. Estágio do Fluxo

`RECEBIMENTO` → `ARMAZENAGEM` → `SEPARACAO` → `EXPEDICAO` → `TRANSPORTE` → `ENTREGA`

Cada extravio deve ser ancorado ao estágio mais provável onde a divergência se
originou, com base nos registros (não no local onde foi *detectado*).

## 4. Confiança da Classificação

- `ALTA` — há evidência documental direta (ex: registro de ocorrência, vídeo, divergência conciliada)
- `MEDIA` — há correlação forte mas indireta (ex: padrão de horário/rota)
- `BAIXA` — divergência confirmada mas sem evidência de causa (vai para `NAO_IDENTIFICADO`)
