# Análise de Dados - LNCC

## Aula 1

### Data Mining na Perspectiva de um Banco de Dados

- **Etapa de Seleção de Dados / Integração de Fontes**
    
    - Seleciona diversas fontes, de modo a montar um conjunto de dados que seja suficiente para a aplicação. 
    
    - Esse conjunto de dados pode ser hospedado em um data lake ou em um data warehouse por exemplo.
    
    * Materializar os dados propriamente ditos
   
<br>


- **Etapa de Pré-Processamento**
    
    - Etapa onde são preparados os dados, de modo que são “limpos”, retirando valores nulos, recriando valores por meio do cálculo de médias e etc
    
    - Essas duas etapas são as que mais tomam tempo.

    - Nem sempre retirar ruídos, fazer uma limpeza extrema é interessante. Tem processos que podem ocorrer como a **suavização** que podem auxiliar na não retirada dos outliers. Outro ponto também é que pode conter informações nesses outliers, como aquele artigo que foca nos outliers do trânsito.

<br>    

- **Etapa de Data Mining**
    
    - Etapa onde são utilizados os algoritmos que irão extrair algum tipo de conhecimento de dados.
    
    - Até então era apenas a função de Engenheiro de Dados, a partir de agora temos a função de Analista de Dados/Cientista de Dados.
    
    - Essa é a etapa que vai gerar possíveis resultados, que deverão ser avaliados para que o processo seja refinado.
    
    - Esse refinamento pode ser em qualquer uma das etapas, desde apenas o algoritmo da mineração ou podendo até mesmo ocorrerem mudanças nas etapas de limpeza de dados.

<br>

### CRISP-DM 

> Cross-Industry Standard Process for Data Mining

Modelo profissional para o processo de extração de dados, envolvendo etapas desde o entendimento do domínio, modelando os dados e realizar o deploy para produção, de modo que vai realmente apoiar o processo de tomada de decisão.

![Imagem do Crisp](/datascience_lncc/img_ds_lncc/imgcrisp.png)

A principal ideia aqui é você se debruçar nos dados, realmente você entender o contexto, não numa visão apenas de dados normais, mas sim entender o contexto dos dados, tendo um conhecimento prévio do domínio desses dados. 


### Coisas que não são Data Mining

 - Consultas diretas no banco
 - Busca de Informação (Como Google)
 - Produzir data warehouse/data lake e consultar eles
 - Sistemas especialista/dedutivos (a partir de regras)
 - Exploração de Dados (base mais estatística e não automatizada)


### Funções Gerais de Data Mining

* Generalização (Mais Antiga)

    * Integração de informações, construção de um data warehouse contendo todo o processo esperado para um ELT de Data Warehouse
    * Agregar os dados multidimensionais em alguma escala
    * Basicamente, você tenta modelar os dados de alguma forma que eles tenham um correlação, sejam agregados em suas diversas dimensões
    * Utiliza-se de OLAP
    * Você pode pegar e agregar diversas fontes de dados e modelar eles em uma nova dimensão:
        * Você ter dados diários e agrega-los em semanas ou meses, de modo que no Data Warehouse vai estar em semanas/meses, mesmo que na fonte esteja em dias.

* Associação e Análise de Correlação

    * Busca de padrões frequentes ou conjuntos que sejam frequentes
        * Padrões de compra como: quais itens geralmente são comprados juntos?
    * Cuidado com a questão de associação e correlação versus causalidade
        * Correlação não implica causalidade!
    * Minerar e ranquear os padrões encontrados

* Predição
    * Modelos que serão treinados por dados de treinamento que irão conseguir predizer ou classificar algo.
        * Data-driven models
    * Consegue descrever ou distinguir as classes e características para conseguir predizer/classificar algo novo
    * Método padrão, envolve coisas como Árvores de Decisão, Naive Bayes, Classificadores no geral.

* Clusterização
    * Aprendizado não supervisionado
    * Apenas agrupa os dados em possíveis categorias (clusters), maximizando as similaridades intra-classe e minimizando as similaridades inter-classes

