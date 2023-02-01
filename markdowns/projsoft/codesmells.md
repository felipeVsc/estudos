# Code Smells

Problemas de qualidade de softwares que podem ser melhorados.

Tipos: 

* Bloaters &rarr; Coisas com proporções gigantes
* OO Abusers &rarr; Aplicações incorretas de Orientação a Objetos
* Change Preventers &rarr; Uma mudança leva a muitas outras mudanças
* Dispensible &rarr; Algo que não deveria existir
* Couplers &rarr; Coisas muito correlacionadas

## Bloaters

### Long Parameter List

Ter muitos paramêtros, não no sentido de quantidade, mas de não haver a **necessidade** de ter todos esses paramêtros.

Pensar em formas de juntar paramêtros para diminuir a quantidade deles.

Exemplo: Em vez de passar varias informações de um objeto, passar o próprio objeto.

~~~java
int low = range.getLow();
int high = range.getHigh();

plan=withinRange(low,high); // ERRADO
plan = withinRange(range); // CORRETO, passando o objeto
~~~

### Data Clumps

Repetir um conjunto de atributos em várias partes do código.

Deve-se tentar juntar esses atributos em um só objeto e passar esse objeto. (Aqui pode ser utilizado no projeto)

~~~java
amount1(start,end);
amount2(start,end);
~~~

### Long Method
// Pode ter no projeto

Métodos que fazem além do que deveriam. Tentar sempre dividir bem os métodos em suas funcionalidade.

O que vai determinar se um método é longo ou não é se ele tem muita funcionalidade, muito relacionamento com outras classes. 

Outra causa é uma grande quantidade de IF's aninhados/switchs aninhados, seja para um menu, seja um instanceof, qualquer coisa que seja de condicional aninhado. 

Um exemplo de método além de suas funcionalidades é você fazer validação dentro de um toString(), sendo que o toString() é feito apenas para apresentação, logo, deveria ser criada outro método que irá realizar as validações.


### Large Class

// Pode ter no projeto

Analoga ao Long Method, mas no contexto de classe. A classe vai lidar com muitos objetos.

Uma classe que tem MUITOs objetos que poderiam ser diminuídos.


### Primitive Obsession

* Quando você sempre tenta usar tipos primitivos; quando uma array tem elementos que sempre significam coisas diferentes, que poderiam ser substituídos por um objeto com significado. Basicamente, utilizar vetores no lugar de utilizar objetos.

* Utilizar valores primitivos para controle lógico de transição, por exemplo, se o usuário está ativo com um "usuarioAtividade = "ATIVO"". Utilização de constantes para controle lógico de transição.

Evitar os tipos primitivos, tentar sempre encaixar um objeto.

Um exemplo é o numero de telefone, que você pode usar uma string com "(DDD) numero", mas o ideal seria um objeto telefone com os atributos DDD e numero. 


## OO Abusers

### Refused Bequest

Quando você utiliza muita coisa que não precisa realmente, ou deveria, da superclasse.

### Indecent Exposure

Exposição da privacidade de classes/metodos. Quando subclasses são acessadas diretamente, expostas, sem passar pela superclasse, o que gera problema de encapsulamentos.


## Change Preventers


### Divergent Change

É um trecho de código que há de ser sempre mudado se ocorrer alguma alteração. Tal fato quando se ocorre em muitas funções, é um problema.

Você ter que mudar muitos métodos só porque fez uma mudança numa classe. Por exemplo, ter que mudar os métodos para busca e print de um objeto.

### Shotgun Surgery

Toda vez que você muda uma classe, serão necessárias pequenas mudanças em outras classes. Logo, na classe que você muda, ela terá um **Shotgun Surgery**, dado que você vai precisar fazer pequenas mudanças em várias outras partes do código.

## Dispensibles


### Códigos duplicados

Ter a mesma estrutura de código em mais de um lugar.

Pode ocorrer tanto em subclasses de uma mesma classe, quanto em classes que não se relacionam, além de construtores duplicados.

Também pode ocorrer com estruturas lógicas duplicadas, como checar se um objeto é nulo.

### Lazy Class/Speculative Generality

Classes com, por exemplo, apenas uma subclasse. Logo, não fará muito uso da orientação a objetos. Idealmente, no mínimo duas subclasses para utilizar os objetos.

Pode levar a uma generalização indesejada.

Se for no contexto de classes **abstratas**, então é chamado Speculative Generality.

Outros pontos:
    * Métodos que não são utilizados
    * Métodos com nomes confusos

### Data class

Classes apenas com atributos e os getters and setters, não fazem mais nenhuma outra operação. Pode ser necessário, mas se possível, tentar evitar. 


### Comments

Muitos comentários, porque é esperado que o método seja legível, sem precisar de muito comentário.



## Couplers

### Feature Envy

Quando um método está mais interessado em funcionalidades de outra classe do que da sua classe-pai.

Quando um método usa mais atributos de uma outra classe do que a mesma que ele está, logo o método deveria estar na classe que ele utiliza mais atributos.

~~~java
public int mediaDescription(){
    return description+gender+contact.getEmail()+contact.prefix()+contact.getArea()+contact.number();

    // Logo, esse media description deveria pertencer a "contact", dado que utiliza mais coisas de contact do que da sua classe-pai.
}
~~~


### Message Chains

Quando um objeto invoca MUITOS outros objetos para chegar num valor. 
Cadeia de troca de mensagens.

~~~java
object.getE().getD().getC().getB().getA().getValue();
~~~

### Middle Man

Métodos que não fazem muita coisa, como por exemplo, um método com poucas linhas que fazem pouca coisa, como apenas checar uma condicional.





