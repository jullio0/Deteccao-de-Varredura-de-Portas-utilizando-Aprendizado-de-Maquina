Detecção de Varredura de Portas (PortScan) com Machine Learning

Este repositório contém o código e os experimentos desenvolvidos no contexto de um Trabalho de Conclusão de Curso (TCC), cujo objetivo é investigar o uso de técnicas de Aprendizado de Máquina para a detecção de varreduras de portas (PortScan) a partir de telemetria de rede baseada em fluxos.

A abordagem utiliza um conjunto de dados público derivado do CICIDS2017, com foco em um cenário binário (Benign vs PortScan), e avalia diferentes modelos de classificação supervisionada, considerando métricas relevantes para ambientes de segurança.

📌 Objetivo do Projeto

Desenvolver e avaliar um pipeline reprodutível de aprendizado de máquina capaz de:

Identificar padrões associados a varreduras de portas em tráfego de rede;

Lidar com forte desbalanceamento entre classes;

Comparar diferentes algoritmos de classificação;

Avaliar o desempenho considerando detecção de ataques e impacto operacional (falsos positivos).

📂 Estrutura do Repositório . ├── notebook.ipynb # Notebook principal com todo o pipeline ├── data/ # Dados de entrada (não incluídos no repositório) ├── results/ # Resultados gerados (CSV e tabelas) ├── figures/ # Figuras exportadas para o TCC └── README.md # Este arquivo

⚠️ Observação: Os arquivos de dados não são incluídos no repositório por tamanho/licença. Veja a seção Dataset.

📊 Dataset

Base: CICIDS2017 (versão pré-processada)

Fonte: Kaggle (D’Hooge, s.d.)

Formato: Parquet (variante no-metadata)

Cenário: Classificação binária (Benign vs PortScan)

Características:

578.353 registros

78 colunas (77 atributos numéricos + 1 variável alvo)

Forte desbalanceamento (≈ 0,34% PortScan)

A variante no-metadata não inclui identificadores diretos como IPs, portas ou timestamps, reduzindo risco de vazamento de informação.

⚙️ Pipeline de Processamento

O pipeline foi implementado utilizando scikit-learn e imbalanced-learn, contendo as seguintes etapas:

Imputação de valores ausentes pela mediana

Seleção de atributos com SelectKBest (f_classif)

Padronização com StandardScaler

Reamostragem com SMOTE (quando aplicável)

Classificador final

Essa estrutura garante reprodutibilidade, evita vazamento de dados e permite comparação justa entre modelos.

🤖 Modelos Avaliados

Regressão Logística (baseline)

Random Forest + SMOTE

XGBoost + SMOTE

LightGBM + SMOTE

📈 Avaliação

Os modelos foram avaliados utilizando:

Validação cruzada estratificada (5-fold) no conjunto de treino

Conjunto de teste final (held-out)

Métricas:

Precision

Recall

F1-score

ROC-AUC

FPR (False Positive Rate)

Curvas ROC para comparação do trade-off entre TPR e FPR

O F1-score foi adotado como principal critério de seleção por refletir melhor o equilíbrio entre detecção de ataques e redução de falsos positivos em bases desbalanceadas.

🔁 Reprodutibilidade

Seed global fixa: random_state = 42

Pipeline único aplicado a treino, validação e teste

Versões das bibliotecas documentadas no notebook

Resultados exportados automaticamente em CSV e tabelas LaTeX

🧪 Como Executar

Faça o download do dataset no Kaggle (CICIDS2017 – no-metadata)

Ajuste o caminho dos arquivos na célula de carregamento dos dados

Execute o notebook sequencialmente no Google Colab ou ambiente local compatível

Os resultados serão salvos automaticamente na pasta results/

📚 Contexto Acadêmico

Este projeto foi desenvolvido como parte de um Trabalho de Conclusão de Curso na área de Redes de Computadores, com foco em segurança de redes e detecção de intrusões baseada em dados.

✍️ Autor

Júlio Cézar Netto de Araújo

Curso Superior de Tecnologia em Redes de Computadores

About
No description, website, or topics provided.
Resources
 Readme
 Activity
Stars
 0 stars
Watchers
 0 watching
Forks
 0 forks
Releases
No releases published
Create a new release
Packages
No packages published
Publish your first package
Footer
© 2026 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Community
Docs
Contact
Manage cookies
Do not share my personal information
