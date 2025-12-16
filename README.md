# 📉 Previsão de Churn de Clientes

Este projeto utiliza Machine Learning para prever quais clientes de uma empresa têm maior chance de cancelar o serviço (Churn). 

## 🛠️ Tecnologias Usadas
* **Python** (Pandas, Numpy, Seaborn)
* **Machine Learning:** Scikit-Learn (Random Forest)

## 🧠 O Modelo
Utilizei um **Random Forest Classifier** ajustado para lidar com o desbalanceamento dos dados (poucos cancelamentos vs. muitos clientes ativos).

* **Tratamento de Dados:** Limpeza de nulos e One-Hot Encoding.
* **Estratégia:** Priorizei o **Recall** (encontrar quem vai sair) em vez da Acurácia pura.
* **Ajuste Fino:** O modelo permite ajustar o "Threshold" (sensibilidade). Se baixarmos a régua de 50% para 40%, conseguimos identificar quase **todos** os cancelamentos.

## 📊 Resultados

| Configuração | Recall (Detectou Churn?) | Precisão (Acertou o Churn?) |
| :--- | :---: | :---: |
| Padrão | 67% | 38% |
| **Ajustado (Threshold 0.4)** | **~95%** | **Baixa** |

**Conclusão:** O modelo é ideal para filtrar a base de clientes e enviar campanhas de baixo custo (e-mails, notificações) para o grupo de risco.

## 🚀 Como rodar

1.  Clone o repositório.
2.  Instale as bibliotecas: `pip install pandas seaborn scikit-learn`
3.  Abra o arquivo `churn_ml_model.ipynb` no Jupyter Notebook ou Google Colab.

---
Autor: [Eduardo Lúcio](https://www.linkedin.com/in/eduluc/)
