# Processamento Paralelo e Distribuído

> Estudos para apresentação de seminário no PIBIC

### __O que é processamento paralelo?__

*Dividir para conquistar*

Uso simultaneo de várias unidades de processamento, de modo que uma tarefa seja destrinchada em pequenas tarefas independentes que irão se utilizar de diferentes unidades de processamento. O software irá manter o controle para saber em qual estado está cada parte.

O objetivo é justamente ofertar uma capacidade de processamento maior, com uma entrega de resultados mais rápida.

Difere de multithreading, dado que multithreading é concorrente e não paralelo.

Temos algumas divisões que podem esclarecer mais para vocês. Os x-cores são um tipo de processamento paralelo, também é possível ter vários processadores físicos sendo controlados por um único SO, ou um sistema distribuído.

A utilização de processamento paralelo entre diversas máquinas conectadas é chamado de **processamento distribuído**.

- exemplo do photoshop
- tentar ver algo com oac

#### Motivação

* Quantidade cada vez maior de dados para serem processados
* Necessidade de um sistema de processamento tolerante a falhas
* Escalabilidade

### **Sistemas Distribuídos**

Uma coleção de computadores interligados via rede, que são controlados por softwares de sistemas distribuído, de modo que todos irão colaborar para alguma função, seja processamento ou armazenamento.

*Definição por Andrew Tanenbaum:*

> "Um Sistema Distribuído é uma coleção de computadores independentes que parecem ao usuário ser um computador único"

Ou seja, diversos hardwares que são controlados por um software para que pareçam uma única máquina.

Algumas coisas que sistemas distribuídos tem que prover são:

* Escalabilidade
* Tolerância a falhas
* Um controlador (middleware)

Exemplos: internet, cripto, p2p files, jogos;

Processamento paralelo ocorre dentro do distribuído. 

### Armazenamento Distribuido

Segue a mesma ideia de um sistema distribuído, mas nesse caso vai servir para armazenamento, com tolerância a falhas, duplicação de dados e etc.

Mesma ideia da escalabilidade, de você distribuir, de modo que se um node cair, ou uma máquina cair, você ainda tem as outras como backup

Também há a necessidade de um controlador para manter a sincroniza e etc

### Hadoop
* YARN
* MapReduce -> Paralelismo já embutido, feito justamente para grandes datasets
* HDFS -> Armazenamento Distribuído

### HDFS

Blocos de dados divididos em 128MB, onde cada bloco é enviado para o HDFS, que irá replicar pelo menos 3x.

O Master (Namenode) irá conter as informações de onde estão cada bloco, como juntar, controlar o acesso.

Os datanodes serão onde os dados irão ficar guardados.

Essa separação por blocos facilita a vida do MapReduce quando ele for ser utilizado, aumentando a performance.

Uma coisa importante no HDFS/Hadoop é o *rack awareness*, de modo que ele sabe que tem que manter réplicas em racks diferentes, de modo que se um cair, o outro continuará disponível.









