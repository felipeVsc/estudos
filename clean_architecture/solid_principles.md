# Princípios SOLID

Buscam organizar as funções e estruturas de dados em classes e dizer como que essas classes devem ser conectadas.

A ideia é como agrupar funções e dados e fazê-los se comunicar de forma correta.

* Tolerar mudanças
* Fácil entendimento
* Reutilizáveis

## Aplicabilidade

Aqui o foco não é que nem no livro Clean Code, onde o foco é o código, mas sim os módulos "acima" do código, ou seja, realmente a arquitetura de componentes do software.

É interessante distinguir aqui dois conceitos: *funções* e *módulos*.

Funções são o baixo nível, o código que escrevemos diretamente.
Módulos são os conceitos acima das funções, questão arquitetural mesmo.

## SRP (Single Responsability Principle)

**Princípio da Responsabilidade Única**

* Um módulo deve ter uma, e apenas uma, razão para mudar.

A mudança é causada por atores (usuários/grupos de usuários), ou seja, um módulo deve ser responsável por um, e apenas um, ator. Se quando eu fizer alguma mudança no módulo eu afetar algum outro ator que não seja o que pediu a mudança, então está violando o príncipio. 

Todos os códigos responsáveis por um único ator no sistema devem estar "amarrados" coesamente.

### Exemplo

Temos uma classe Employee com três funções: - CalculatePay(); - ReportHours(); - save().

Cada função dessa é utilizada por um departamento da empresa. Logo, se um departamento requerer uma modificação, eu vou ter que mexer no código de outros departamentos para realizar a função. Esse módulo deveria ter apenas uma única responsabilidade, um único departamento. 

## OCP (Open-Closed Principle)

**Princípio do Aberto/Fechado**

* Um artefato de software deve ser aberto para extensão, mas fechado para modificação.

Você deve poder extender o artefato sem precisar modificar ele. Se você quiser adicionar novas funcionalidades, você não precisa mudar tudo. 

Se você precisa de uma nova funcionalidade simples e isso leva a um grande refatoramento, então a arquitetura é ruim.

Para que o componente A seja protegido das mudanças no componente B, o componente B deve depender do componente A.

## LSP (Liskov Substitutive Principle)

**Principio de Substituição de Liskov**

Principio de subtipos, onde você pode substituir um pelo outro sem alterar o funcionamento.

Os subtipos podem ser substituídos pelo tipo pai sem problemas, sem ser necessário nenhuma modificação.

Se você precisar ficar checando subtipos, algo de errado tem.

## ISP (?)

**Princípio da Segregação de Interface**

Quebra de Ligação entre responsabilidades. Várias operações diferentes podem estar sob a mesma classe Operações, mas se cada uma das operações forem exclusivas para um ator, então é interessante realizar a segregação dessas operações em interfaces.

Isso porque se um Usuário1 que está usando a Operação1 da Classe Operação que contém Operação1,Operação2,Operação3, realizar alguma alteração na sua funcionalidade, então toda a classe Operação precisará ser recompilada, logo, os usuários de Operação2 e 3 também serão afetados.

### COLOCAR AS FIGS AQUI!

Isso só é necessário se a linguagem for tipada, ou seja, se os imports e etc acontecerem em tempo de compilação e não em tempo de execução. Logo, isso é um problema em Java, mas não é um problema em Python.

A ideia é você não depender de algo que não lhe é necessário. Se algo que você está usando tem mais coisas do que você precisa, e principalmente se essas coisas poderão ser modificadas no futuro, então você tem um problema.

## DIP (?)

**Princípio da Inversão de Dependência**

Principio que as dependências tem que ser interfaces ou coisas abstratas e não algo concretamente aplicado. Temos que evitar tudo que possa ser alterado e quebre nosso código, ou leve o programador a refatorar muita coisa.

A ideia é que uma interface irá ter muito menos alterações do que uma classe concreta, logo, é preferível sempre ser dependente de uma interface e adicionar novas coisas em classes concretas do que depender de uma classe concreta.

* Não devemos se referir a classes concretas e sim as interfaces abstratas.
* Não derive de classes concretas, mas sim herde de interfaces abstratas.

Para implementar esse principio, geralmente se faz necessário usar um Abstract Factory.

A ideia é dividir bem o código em coisas abstratas contendo as regras de negócios de alto nível, que pouco mudarão, e as implementações concretas.