# Aula 02 - Análise de Dados - LNCC

## Visualização de Dados

### Scatter plot

Utilizado para mostrar valores para relações entre variáveis dependentes e independentes.

Geralmente associam-se cores aos componentes.

add imagem!

### Bar Plot

Utilizado para apresentar dados categóricos, onde você indica por barras os valores.

Existe a versão horizontal dele, chamado de "lollipop", é interessante para se ter a mesma coisa que o de barras mas mudando a visualização, de modo que não vai estar se repetindo o padrão de gráficos.

* Error Bars
    * Adicionar uma error bar em cima da barra normal, mostrando a dispersão, mostrando quanto ela oscila dentro daquilo
* Grouped bar
    * Mais de uma barra agrupada, diversos grupos para uma mesma categoria.
    * Pode ser lado a lado ou em cima

### Pie Chart

Gráfico estatistíco clássico, de modo que você utiliza proporções da informação. 

## Análise de Distribuição de Dados

### Correlação

* Gráfico de Correlação entre os atributos numéricos de um dataset
* Quanto mais perto de um, geralmente um vai aumentar e o outro também. Se for -1, então um cresce e o outro diminui. Se for 0, não tem correlação

### Histograma

* Visualiza a distribuição de uma única variável, dividindo o eixo x em "bins", contando a quantidade de coisas em cada bin.
* Density plot é uma versão mais suavizada, não são bem quadrados, mas fica meio que um gráfico mesmo de curva.

### Box plot

* Divide os grupos de dados em seus quartis. Para cada atributo quanto você tem de oscilação dos valores. 
* Linhas indicam também a variação, de minimo e maximo que **não são outliers**
* Existem dots também que **são os outliers.**

## Análise Exploratória de Dados (EDA)

### Características Importantes de Dados Estruturados

* Dimensionalidade
    * Quantidade de atributos que existem, pode ser um problema ou não
    * Muitas dimensões e poucos dados é algo ruim, podendo causar overfitting
    * Idealmente se faz uma seleção dos atributos, de modo que você pode utilizar técnicas para escolher os atributos
* Esparcidade
    * Se os dados forem esparsos, apenas a quantidade.
    * Muitos campos vazios, datasets grandes mas com dados esparsos, campos nulos e vazios que acabam atrapalhando o sistema.
* Resolução
    * Escala dos dados, sendo possível você agregar dados para diminuir a resolução deles
    * Um exemplo é justamente você ter um dataset de ruas e reunir eles em bairros apenas, diminuindo a resolução.
    * Pode ajudar a resolver problemas como a esparcidade? - PERGUNTAR -
* Distribuição
    * Centralidade e dispersão

### Atributos

Qualquer coisa que categorize os dados, podem ser também dimensões, features, variáveis.

Basicamente é um data field que vai representar algo de um objeto. Podendo ser de tipo binário, numérico, nominal e etc.


