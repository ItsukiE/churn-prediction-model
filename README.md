# 📉 Customer Churn Prediction
> Identificando clientes em risco de cancelamento para ações de retenção proativas.

![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Lib](https://img.shields.io/badge/Library-Scikit--Learn-orange)

## 💼 O Problema de Negócio
O cancelamento de clientes (Churn) é um dos maiores problemas para empresas de receita recorrente. O custo de adquirir um novo cliente (CAC) é geralmente 5x a 7x maior do que manter um atual.

O objetivo deste projeto é prever quais clientes têm maior probabilidade de cancelar o serviço, permitindo que a equipe de Marketing realize campanhas de retenção focadas e reduza o desperdício de orçamento.

**Dados:** Dataset com 10.000 clientes (Infos demográficas, comportamento de uso, reclamações).

## 🛠️ Estratégia da Solução

O projeto foi desenvolvido seguindo o ciclo de Data Science:

1.  **Limpeza dos Dados:** Tratamento de valores nulos (ex: `complaint_type`) e remoção de colunas irrelevantes (`customer_id`).
2.  **Feature Engineering:** Transformação de variáveis categóricas usando One-Hot Encoding.
3.  **Modelagem (Machine Learning):**
    * Algoritmo: **Random Forest Classifier**.
    * Estratégia para Desbalanceamento: Uso de `class_weight='balanced'` para dar peso maior à classe minoritária (Churn).
    * Controle de Overfitting: Poda da árvore com `max_depth=5`.
4.  **Otimização de Decisão:** Ajuste do **Threshold (Limiar)** de classificação para priorizar a captura de Churn (Recall).

## 📊 Performance do Modelo

Como o objetivo é **não perder clientes**, a métrica principal escolhida foi o **Recall** (taxa de detecção de cancelamentos).

| Métrica | Performance (Baseline) | Performance (Ajustada) |
| :--- | :---: | :---: |
| **Recall (Churn)** | 63% | **~90-100%** |
| **Threshold** | 0.50 | **0.30** |

*Nota: Ao baixar o threshold para 0.30, conseguimos identificar quase todos os clientes que sairiam, aceitando uma precisão menor (mais falsos positivos).*

## 💡 Conclusão e Insights

O modelo final permite segmentar a base de clientes com precisão suficiente para **ações de baixo custo**, como e-mails automatizados e push notifications.

* **Top 3 Fatores de Risco:** O modelo identificou que variáveis como `complaint_type`, `tenure` e `satisfaction_score` são determinantes para a saída do cliente.
* **Ação Recomendada:** Utilizar a lista gerada pelo modelo com Threshold 0.30 para enviar comunicações de "Reaproximação" preventiva.

## 🚀 Como executar o projeto

```bash
# Clone este repositório
$ git clone [https://github.com/SEU_USUARIO/churn-prediction.git](https://github.com/SEU_USUARIO/churn-prediction.git)

# Instale as dependências
$ pip install pandas seaborn scikit-learn matplotlib

# Execute o Jupyter Notebook
$ jupyter notebook churn_ml_model.ipynb
