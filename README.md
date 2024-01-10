# Titanic---ml
Repositório criado para a competição do Kaggle sobre o desastre do Titanic: Titanic - Machine Learning from Disaster (
https://www.kaggle.com/competitions/titanic)

### [Parte 1](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v1.ipynb)
- Nesse etapa foram realizados os passos iniciais para exploração e tratamento da base de dados. 
- Colunas com alta cardinalidade e elevada quantidade de valores faltantes foram excluídas e aquelas com quantidades menores, tiveram seus valores faltantes substituídos pela média ou mediana da coluna.
- Nesta etapa, todas as variáveis categóricas do dataset foram desconsideradas no treinamento dos modelos.
- Foram criados 3 modelos de previsão: Regressão Logística, Random Forest e SVM (Support Vector Machine).
- Melhor acurácia direta: Regressão Lógistica, com 72.5%.

### [Parte 2](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v2.ipynb)
- Esta etapa é marcada pelo tratamento das variáveis categóricas que restaram (após a exclusão das colunas de alta cardinalidade na etapa anterior) através da codificação com o OneHotEncoder. As colunas codificadas foram "Sex" e "Embarked".
- Após a codificação das variáveis categóricas, foi realizada a padronização/escalonamento dos dados da base, melhorando as previsões dos algoritmos que tem base em cálculos de distância, nesse caso, o SVM. Inicialmente, para a padronização, foi utilizado o StandardScaler.
- Melhor acurácia direta: Regressão Logística, com 81.3%.

### [Parte 3](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v3.ipynb)
- Foram observadas, apenas para fins de visualização, algumas relações entre as variáveis "SibSp" e "Parch".
- Após analisar, desconsiderando a prévia padronização, a escala dos dados da base de treino, foi observada além das diferenças de escala, a presença de outliers na coluna "SibSp". Desta forma, optou-se pela utilização do RobustScaler para a padronização dos dados.
- Foi realizada uma verificação simples de importância dos atributos da base de treino para classificação através do Random Forest.
- Melhor acurácia direta: SVM, com 81.6%.

### [Parte 4](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v4.ipynb)
- Foram realizadas estratégias simples de seleção de atributos, através de análise de correlação e análise de importância de atributos com RandomForestClassifier. O método de VarianceThreshold se mostrou ineficiente diante das variâncias médias elevadas de todas as colunas.
- O MLP (Multilayer Perceptron) foi adicionado como novo modelo de previsão.
- Foi utilizado o GridSearchCV para busca dos melhores hiperparâmetros de todos os modelos de classificação criados.
- Melhor acurácia direta: MLP, com 83%.

### [Parte 5](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v5.ipynb)
- O GradientBoosting e XGBoost foram adicionados como novos modelos de previsão.
- O algoritmo K-Folds Cross Validation foi utilizado com divisão de 10 partes para medir com maior eficiência a acurácia dos modelos.
- Agora, considera-se como acurácia final de cada modelo a média das acurácias obtidas em 30 execuções do K-Folds Cross Validation.
- Melhor acurácia: XGBoost, 83.2%
