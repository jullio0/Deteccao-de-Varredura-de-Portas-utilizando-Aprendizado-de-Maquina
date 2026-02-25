# 🛡️ **Detecção de Varredura de Portas (PortScan) com Machine Learning**

Este repositório contém o pipeline completo de aprendizado de máquina desenvolvido para a detecção de ataques de PortScan utilizando telemetria de rede baseada em fluxos. O projeto faz parte do Trabalho de Conclusão de Curso (TCC) em Redes de Computadores no IFPB.




## 📋 Resumo do Projeto

O objetivo principal é identificar precocemente atividades de reconhecimento (varreduras de portas) em redes corporativas, utilizando uma abordagem reprodutível que lida com o alto desbalanceamento de dados típico deste cenário.

* **Dataset**: CICIDS2017 (versão pré-processada).
* **Modelo de Melhor Desempenho**: Random Forest + SMOTE.
* **Resultados Finais**: 99,49% de Recall e apenas 0,05% de taxa de falsos positivos (FPR).




## 🚀 Estrutura do Pipeline

O pipeline foi desenvolvido de forma modular para garantir transparência e reprodutibilidade:

**1 - Preparação do Ambiente**: Instalação e importação das bibliotecas (Pandas, Scikit-learn, Imbalanced-learn, XGBoost, LightGBM).

**2 - Pré-processamento**: Tratamento de valores ausentes (imputação pela mediana) e padronização de escalas.

**3 - Seleção de Atributos**: Uso do teste estatístico F para selecionar as 30 características mais relevantes.

**4 - Balanceamento**: Aplicação da técnica SMOTE para equilibrar a classe minoritária (ataques) no conjunto de treino.

**5 - Treinamento e Validação**: Comparação entre Regressão Logística (Baseline), Random Forest, XGBoost e LightGBM via Validação Cruzada Estratificada (5-fold).




## 📊 Principais Resultados

Os modelos foram avaliados em um conjunto de dados "não visto" (held-out) para simular o comportamento em um ambiente real:
| Modelo | Precision | Recall | F1-score | ROC-AUC | FPR |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Random Forest + SMOTE** | **0,8801** | **0,9949** | **0,9340** | **0,9987** | **0,05%** |
| LightGBM + SMOTE | 0,8647 | 0,9974 | 0,9264 | 0,9980 | 0,05% |
| XGBoost + SMOTE | 0,8442 | 0,9974 | 0,9144 | 0,9992 | 0,06% |
| Logistic Regression (baseline) | 0,1992 | 0,9693 | 0,3304 | 0,9967 | 1,32% |




## 🛠️ Como Reproduzir

**1 -** Acesse o notebook através do arquivo .ipynb neste repositório.

**2 -** Carregue o dataset CICIDS2017 conforme as instruções contidas no notebook.

**3 -** Execute as células sequencialmente para observar a geração do ranking de features e o treinamento dos modelos.




## 🎓 Autor

### Júlio Cézar Netto de Araújo 

**Orientador**: Prof. Diego Ernesto Rosa Pessoa.

**Instituição**: Instituto Federal da Paraíba (IFPB) - Unidade Acadêmica de Informação e Comunicação.
