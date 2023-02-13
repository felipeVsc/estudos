# Java - P2

A primeira coisa é que a classe principal tem que ter o mesmo nome do arquivo, se não, não irá compilar.

Comentários são feitos de duas formas:

// e /* */

### Main 
~~~java
~~~
~~~java
public static void main(String[] args){
    // code
}
~~~

### Tipos

Java é tipada, logo, é necessário declarar o tipo da váriavel. 

~~~java
int numero;
char caractere;
String nome;
double quilometragem;
~~~

* Nesse caso, String é uma classe e não um tipo primitivo, dado que String é uma array de chars.

Para trocar de tipo, como por exemplo de double para int, temos que usar o casting

~~~java
double x = 10.5;
int y = (int) x;
~~~

* Nota: o int vira double, mas o double não vira int direto, fazendo x=y.

__Double__

O double é o tipo padrão para ponto flutuante no Java, sendo de melhor uso que o float. 

Para iniciar um float x = 0.0, temos que utilizar float x = 0.0f, para que assim o compilador saiba que estamos querendo trabalhar com o float

### Condicional

~~~java
if (condicao){
    // codigo
} else if(condicao){
    // codigo
} else{
    // codigo
}
~~~

Pode usar !variavel para negação

#### __Operador ternário__

Bom para se quiser atribuir rapidamente a uma variavel

~~~
(expressão) ? true:false
~~~

Exemplo:

~~~java
String dia = (dia<10) ? "Segunda":"Terca"
~~~

Se o dia<10, então defina como Segunda, senão, defina como Terça.

#### __Switch case__

Funciona do mesmo modo que em C, ele "seleciona" uma variável e vai de acordo com cada casos.

* Nota: se não tiver o break, ele vai rodar todos os cases que não tenham break. 

~~~java
switch (variavel){
    case v1:
        //codigo
        break;
    case v2:
        // codigo
        break;
    default:
        // codigo;
}
~~~

### Repetição

* break irá parar, e continue vai pular o resto do código do loop se atingir a condição.

* __Continue__ é equivalente a um pass em python

#### __while__

~~~java
int contador = 0;
while(contador<10){
    // codigo
    contador++;
}
~~~

#### __do while__

Código dentro do "do" será rodado antes do loop.

A grande diferença para while é que o código do "do" será rodado pelo menos uma vez, porque ele primeiro roda o do para depois verificar a condição.

~~~java
int contador = 0;
do{
    // codigo
} while(contador<10){
    // codigo
    contador++;
}
~~~



#### __For__

Roda normal igual a qualquer for

~~~java
for(inicializacao; condicao; incremento){
    // codigo
}
~~~

#### __For each/Enhaced__

Array unpacking normal, onde vai pegando os itens da Array e definindo para a variável. Só pode ser usada para obter as info e não mudar elas.

~~~java
for(int variavel:array){
    // codigo
}
~~~

Vai substituir o uso do for nesse caso:

~~~java
for(int x=0;x<10;x++){
    System.out.println(array[x]);

}
~~~

## Input de Usuário

* Necessário: **import java.util.Scanner**

~~~java
Scanner input = new Scanner(System.in);

int numero = input.nextInt();
~~~

Precisa chamar o scanner e passar o next() de acordo com o tipo

* Não tem como colocar texto dentro do input igual em Python, tem que printar um texto antes do input.

## Strings 

São instâncias da classe String e não propriamente dita apenas uma array de caracteres. 

~~~java
String texto = "Texto";
~~~

Para se ler uma string, usa-se __nextLine()__ no input

__Alguns métodos interessantes:__

* lenght()

* charAt(int i) &rarr; retorna o char na posição i

* contains(String s) &rarr; se contem a sequencia de char

* equals(String s) &rarr; True se forem exatamente iguais, case sensitive

* equalsIgnoreCase(String s) &rarr; True se forem exatamente iguais e ignorando o Case

* indexOf(int ch) &rarr; indice da primeira aparição do char

* lastIndexOf(int ch) &rarr;

* toUpperCase() &rarr; tem lower case também

* replace(char oldChar, char newChar) &rarr; troca as ocorrencias

* substring(int inicio, int fim) &rarr; faz um slice na string

* https://docs.oracle.com/javase/7/docs/api/java/lang/String.html


## Arrays 

Array do mesmo jeito que C basicamente

~~~java
int[] array = new int[size];

// ou

int[] array = {1,2,3,4};

~~~

Alguns métodos interessantes:

* fill() &rarr; Preencher array
* sort() &rarr; Sorting 
* binarySearch() &rarr; Procura se tem e onde está um valor
* equals() &rarr; compara array

## ArrayList

Listas, implementação de Array com métodos mais legais.

* Garante ordenação
* Garante busca
* Não tem tamanho fixo

~~~java
 ArrayList lista = new ArrayList();

 ~~~

 __Alguns métodos:__

 * lista.add("campo");
 * lista.size();
 * lista.get(pos);
 * lista.contains();
 * lista.remove();
 * lista.clear();
 