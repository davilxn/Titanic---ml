# Titanic---ml
Repositório criado para a competição do Kaggle sobre o desastre do Titanic: Titanic - Machine Learning from Disaster (
https://www.kaggle.com/competitions/titanic)

### [Parte 1](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v1.ipynb)
- Nesse etapa foram realizados os passos iniciais para exploração e tratamento da base de dados. 
- Colunas com alta cardinalidade e elevada quantidade de valores faltantes foram excluídas e aquelas com quantidades menores, tiveram seus valores faltantes substituídos pela média ou mediana da coluna.
- Nesta etapa, todas as variáveis categóricas do dataset foram desconsideradas no treinamento dos modelos.
- Foram usados 3 modelos de classificação: Regressão Logística, Random Forest e SVM (Support Vector Machine).
- Melhor acurácia de validação: Regressão Lógistica, com 72.5%.
- Acurácia das previsões de teste submetidas: 67.2%

### [Parte 2](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v2.ipynb)
- Esta etapa é marcada pelo tratamento das variáveis categóricas que restaram (após a exclusão das colunas de alta cardinalidade na etapa anterior) através da codificação com o OneHotEncoder. As colunas codificadas foram "Sex" e "Embarked".
- Após a codificação das variáveis categóricas, foi realizada a padronização/escalonamento dos dados da base, melhorando as previsões dos algoritmos que tem base em cálculos de distância, nesse caso, o SVM. Inicialmente, para a padronização, foi utilizado o StandardScaler.
- Melhor acurácia de validação: Regressão Logística, com 81.3%.
- Acurácia das previsões de teste submetidas: 65.0%

### [Parte 3](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v3.ipynb)
- Foi desconsiderada a exclusão de colunas categóricas anteriormente realizada, em prol da realização uma exploração mais aprofundada das relações entre as variáveis previsoras e a variável alvo (Survived) e das variáveis previsoras entre si, na busca por padrões que tornassem os dados mais discriminatórios.
- Com base na exploração realizada, foram aplicadas técnicas de engenheria de atributos, que resultaram na modificação de algumas colunas (Fare, Age, Sex) e na criação de novas (Family, Titles, AgePclass).
- Foi desconsiderada, nesta etapa, o uso de padronizadores/normalizadores. Além disso, foi utilizado One Hot Enconder para codificação da variável categórica nominal "Embarked".
- Foram realizadas estratégias simples de seleção de atributos, através de análise de correlação e avaliação de importância de atributos com RandomForestClassifier. O método de VarianceThreshold se mostrou ineficiente diante das variâncias médias elevadas de todas as colunas.
- Melhor acurácia de validação: SVM, com 80.6%.
- Acurácia das previsões de teste submetidas: 76.3%

### [Parte 4](https://github.com/davilxn/Titanic---ml/blob/main/titanic_sink_v4.ipynb)
- Foram adicionados como novos modelos de previsão: Gradient Boosting e XGBoost.
- Foi criado e adicionado como modelo extra de previsão uma ANN (torch.nn.Module).
- Foi utilizado o GridSearchCV para busca dos melhores hiperparâmetros de todos os modelos de classificação criados.
- O algoritmo K-Folds Cross Validation foi utilizado com divisão de 10 partes para medir com maior eficiência a acurácia dos modelos.
- Melhor acurácia de validação: ANN, com 82.5%.
- Melhor acurácia por CV: XGBoost (min: 83.2, mean: 84.0, max: 85.1)
- Acurácia das previsões de teste submetidas: 78.0%
