# Relatório de Análise de Evasão de Clientes

## 1. Desempenho do Modelo

O modelo utilizado foi **Regressão Logística** com aplicação de **oversampling** para balanceamento da classe minoritária.  
Os resultados obtidos foram:

- **Acurácia:** 0.6484  
- **Precisão:** 0.4158  
- **Recall:** 0.8309  
- **F1-Score:** 0.5543  

### Matriz de Confusão
|                | Predito Não Evasão (0) | Predito Evasão (1) |
|----------------|------------------------|--------------------|
| **Real 0**     | 908                    | 649                |
| **Real 1**     | 94                     | 462                |

### Relatório de Classificação
| Classe | Precisão | Recall | F1-Score | Suporte |
|--------|----------|--------|----------|---------|
| 0      | 0.91     | 0.58   | 0.71     | 1557    |
| 1      | 0.42     | 0.83   | 0.55     | 556     |
| **Média/Total** | **0.78** | **0.65** | **0.67** | 2113 |

---

## 2. Principais Fatores que Influenciam a Evasão

A importância das variáveis foi calculada com base nos coeficientes da regressão logística. Valores positivos indicam aumento na probabilidade de evasão, e valores negativos indicam diminuição.

| Variável                                                   | Coeficiente | Importância Absoluta |
|------------------------------------------------------------|-------------|----------------------|
| `remainder__tenure`                                        | -2.008443   | 2.008443             |
| `remainder__Charges.Monthly`                               | 0.856760    | 0.856760             |
| `onehotencoder__Contract_Dois anos`                        | -0.841776   | 0.841776             |
| `onehotencoder__Contract_Mês a mês`                        | 0.765659    | 0.765659             |
| `onehotencoder__InternetService_Fibra ótica`               | 0.676343    | 0.676343             |
| `onehotencoder__PaymentMethod_Cheque eletrônico`           | 0.458523    | 0.458523             |
| `onehotencoder__OnlineSecurity_Não`                        | 0.338550    | 0.338550             |
| `onehotencoder__TechSupport_Não`                           | 0.338545    | 0.338545             |
| `onehotencoder__OnlineBackup_Não`                          | 0.169142    | 0.169142             |
| `onehotencoder__DeviceProtection_Não`                      | -0.108747   | 0.108747             |
| Demais variáveis                                            | ≈ ±0.021812 | 0.021812             |

---

## 3. Interpretação dos Resultados

- **Tempo de contrato (`tenure`)** foi o fator mais relevante, com coeficiente negativo, indicando que clientes com mais tempo de permanência tendem a **evadir menos**.
- **Cobrança mensal alta (`Charges.Monthly`)** está associada a **maior probabilidade de evasão**.
- Contratos **mensais** aumentam o risco de saída, enquanto contratos de **dois anos** reduzem significativamente esse risco.
- Usuários com **internet de fibra óptica**, **pagamento por cheque eletrônico**, **sem segurança online** ou **sem suporte técnico** apresentam maior tendência à evasão.
- A ausência de **backup online** também está associada à maior evasão, embora com menor peso.

---

## 4. Estratégias de Retenção Sugeridas

Com base nos resultados:
1. **Fidelização por contratos longos:** oferecer benefícios e descontos para migração de contrato mensal para anual ou bienal.
2. **Ajuste de preços para clientes em risco:** reduzir mensalidade para usuários com alto custo mensal e baixa fidelidade.
3. **Aprimorar suporte e segurança online:** oferecer pacotes com suporte técnico e segurança digital gratuitos ou com desconto.
4. **Campanhas para novos clientes:** foco em retenção nos primeiros meses, período mais crítico para evasão.

---
