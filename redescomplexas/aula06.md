## Aula 06 - Redes Complexas

## Medidas de Centralidade

Centralidade é uma medida que indica a importância de um vértice para a **propragação de informação**. Ou seja, pontos de propagação das redes.

Mas como quantificar essa centralidade?

### Medidas de Centralidade

* Degree
* k-core
* Betweenes Centrality
* Eigenvector Centrality
* Closeness Centrality
* Page-Rank
* Accessibility


### Degree Centrality

Grau do vértice, ou seja, o número de conexões que um vértice tem. É um dos mais clássicos.

Exemplo: Numa rede social, uma entidade (pessoa), com muitas conexões (seguidores), então essa entidaed (pessoa) tem um nível de relevância alto.

O problema de usar grau, é que podem ser hubs periféricos, onde não estão no eixo central da rede, de modo que a propagação da informação não seria rápida.

![Exemplo de Hubs Periféricos](/imgs/hubsdegree.png)

### k-core

O subgrafo maximal conexo onde todos os vértices tenham pelo menos k grau.

Você vai removendo os que tenham menos que K, até que o que sobrar será o hub central mais importante.

![Exemplo de k-core](/imgs/kcore.png)

### Closeness Centrality

Define a centralidade em termos da distância entre vértices.