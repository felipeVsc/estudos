# Aula 2 06/04

## Herança

Herdar informações e comportamentos **(atributos e métodos)** de classes pai

Funciona da mesma forma que a herança biológica, o que o "pai" tiver, o filho também terá e pode implementar mais funcionalidades. De geral para específico.

É possível armazenar objetos de tipo subclasse em um tipo de superclasse. O contrário não é possível. Isso ajuda para a generalização, de modo que você pode passar um TipoClassePai classeFilho e utilizar em métodos de ClassePai que recebam o tipo TipoClassePai

Também pode fazer essa mesma ideia para ArrayList, onde você poderia colocar mais de um tipo especifico

~~~java

TipoClassePai classeFilho = new ClasseFilho();

// metodo imaginario de ClassePai

public void printarInfo(TipoClassePai classe){
    // code
}

printarInfo(classeFilho)
~~~


*Utilização* 

Só colocar um "extends ClassePai" na subclasse

~~~java

public class ClassePai{
    // code
}

// Arquivo 2
public class ClasseFilho extends ClassePai{
    // code
}

~~~

**Super/Construtor**

Usar para pegar coisas, como o construtor da superclasse.

~~~java
public ClasseFilho(Args da ClassePai){
    super(args) // Já realiza as operações para os atributos da classe pai

}
~~~

## Modificadores de Acesso

Fora o public e private, sendo o public o mais abrangente (qualquer um) e o private sendo o mais restritivo (apenas a classe).

Existem outros dois:

* **protected** &rarr; Quaisquer classes que herdam a classe pai, outras classes que estejam no mesmo package, ou seja, alguma relação.
* **package** &rarr; dentro do mesmo package, independente de herança e etc.

#### **Diagramação**

"+" = public.

"#" = protected.

nada = package.

"-" = private.

## Method Overriding

Toda classe herda de Object. 

#### Override

Método com mesmo nome dentro de uma hierarquia, você vai reescrever aquela função. Adiciona o @Override acima da função que vai sobrescrever a função original.

~~~java
@Override
public void FuncaoOriginal(){
    // funcao nova que vai sobrescrever a original

    return super.toString()+novasCoisas
}
~~~

Da para você herdar do original e adicionar novas coisas (usar no projeto, na parte de privacidade é interessante) "#anot"

#### **toString()**

Fazer override no toString, que é de object, torna possível você dar só System.out.println(objeto) e ele vai chamar o toString(), que se você customizar, pode fazer com que o retorno seja tipo o retriveAll lá, personalizado.

#### Array com varios tipos filhos

Como é possivel associar o tipo do pai aos filhos, como Pai obj1 = new Filho(), logo você pode criar sempre como Pai, incluindo uma ArrayList, de modo que você não precise fazer o cast das coisas, nem um ArrayList<>

~~~java
ArrayList<Pai> lista = new ArrayList<>();
lista.add(new Filho())

for (Pai item: lista){
    // code
}
~~~

# Aula 03 - 13/04

## Polimorfismo

Só funciona em métodos que sofreram @Override.

**Cast**

Transformar tipos, incluindo tipos de objetos

TipoNovo nome = (TipoNovo) tipoAntigo

&rarr; Só funciona de pai para filho, não funciona entre filhos (entre subclasses)

## Classes Abstratas

O esqueleto das classes, com o mínimo de métodos que são obrigatórios. Não serão implementados na abstração, apenas diz que aquele método é **OBRIGATÓRIO** ser implementado.

Basicamente é uma "regra de negócio", de modo que você cria classes que não podem ser instanciadas.

Garante a existência do método nas subclasses.

Em classes você pode implementar campos, ao contrário de Interfaces.    

~~~java

public abstract class ClasseAbstrata{
    public abstract String metodoAbstrato();
    // só a assinatura mesmo
}
~~~

Você pode usar em outro método da classe pai o resultado de um método abstrato, baseado na fé de que vai ser implementado pela subclasse e no momento que você for utilizar eses método da classe Pai, então a filha já vai ter implementado a abstração

~~~java
public abstract string metodoAbs();

public void teste(){
    metodoAbs(); 
    // quando o filho chamar super().teste() ele já vai na fé de que foi implementado
}
~~~

## Interfaces

Uma interface só tem métodos abstratos, nenhum é implementado.

A interface não tem a ideia de herdar, mas sim de "implementar" aquela interface, já que vai ser puramente o esqueleto, sem nenhum tipo de implementação.

**Boa prática** &rarr; implementar baseado em interfaces e não em classes abstratas.

No Java não existe herança múltipla, de modo que você só pode herdar de uma classe abstrata, porém, existe interface múltipla, de modo que você pode implementar mais de uma interface.

A Interface vai garantir por meio de um "contrato" que aqueles métodos serão aplicados. 

*Exemplo*: A classe Retangulo herda de Poligono, que vai implementar coisas como quantidade de lados, retornar os lados, coisas normais de um poligono. A classe Retangulo também vai implementar as interfaces: "OperacoesBasicas", que é uma interface que vai implementar obrigatóriamente métodos como área do polígono e perímetro.

Métodos obrigatórios dentro de um contexto, de modo que são métodos comuns para classes de diferentes contextos.

~~~java
public inteface InterfaceClasse{
    double amount(); // é assim que declara um método abstrato numa interface. 

}
~~~

Para utilizar nas outras classes, tem que fazer:

~~~java
public class Classe implements InterfaceClasse{
    
    @Override
    public double amount(){
        // code
    }
}
~~~

## Collections 

* List &rarr; Ordenado, pode conter duplicadas.
    - ArrayList, LinkedList, Vector
    - Pode acessar posições.
* Set &rarr; Não ordenado, não pode conter duplicados
    - Não da acessar posições, dado que pode mudar
    - TreeSet pode ter ordenação, mas baseada no valor (Red-Black Tree)
    - LinkedHashSet é uma implementação de set que só vai se importar com ordem de add das coisas.
* Map &rarr; Key-Value, não pode ter keys duplicadas, mas valores sim.
     - Abstração de uma função matemática
    - Put, não add.








