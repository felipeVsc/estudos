# Aula 03 - Redes Complexas

## Como processar e analisar Redes Complexas?

Usa-se um grafo para representar as redes complexas, na estrutura de nós e arestas significando links entre entidades. 

As interações entre entidades e as próprias entidades podem não estar bem claras e definidas, de modo que nem sempre a rede complexa vai representar exatamente o que é real, logo é necessário **modelar** essa rede complexa de alguma forma que seja viável a representação em grafos.

Para analisarmos e processarmos, devemos utilizar técnicas das Teorias dos Grafos.

### Rede vs Grafos

Grafo é a representação matemática de uma rede, a rede é um sistema real que é referente a algo muito mais complexo quando olhado como um tudo.

### Tipos de Redes

**Static Single Layer Network**

* Não Dirigidas

    * Não tem direção, como a amizade no Facebook

* Dirigidas

    * Tem uma direção definida, tipo o Twitter, onde um pode seguir o outro sem o outro seguir você

**Bipartida**

Duas classes de vértices e a conexão só se da entre as classes.
<br>
x -> y sempre.
<br>
Pode-se definir projeções, que seriam as conexões que deveriam existir entre uma mesma classe.

1 -> a<br>
2 -> a<br>
<br>
Então 1 -> 2, dado que ambos estão relacionados em a.

**Multilayer**

Redes multicamadas, que seriam algo como redes conectadas com outras redes. Por exemplo, as redes do Facebook, Instagram e Whatsapp são conectadas sob a rede da Meta.

**Temporais**

Conexões e vértices mudam com o tempo. Tudo vai variar com um paramêtro de tempo.

**Outras**

* Espaciais

    * Vertices apresentam uma posição definida.
        * Redes de cidades, redes de ruas.
        
* Arestas Ponderadas

    * Cada aresta tem um peso. Redes de Roteadores podem ter pesos. Pode indicar um custo para aquela conexão.
    * Por exemplo, o tráfego em uma rua pode ter um peso maior.

Pode ser que seja necessário transformar de um tipo para outro de rede. Podemos utilizar algo como **threshold**, definindo limiares para transformação. Tudo vai depender do tipo de informação que queremos extrair.

### Representação

* Matriz de Adjacência
    * Acesso mais rápido, diretamente pela posição matriz[i][j]
    * Métodos matematicos como a transposta para transformar de um ponderado para um simples
    * Porém ocupa muito espaço de memória

* Edge List
    * Um espaço menor na memória, já que guarda apenas as conexões
    * Porém, o acesso é ruim ja que tem que percorrer a lista para encontrar algo.
    * Não tem muito o que fazer matematicamente

* Adjacency List
    * Lista onde cada vertice vai ter a sua lista de conexoes
        * [1:[2,3], 2:[1,4]]
    * Menos uso de memória, já que não guarda os zeros igual a matriz de adjacência
    * Não tem muito método matematico.