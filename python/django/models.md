# Models

Representação da tabela no código. Mesmo esquema que o Laravel.

Aqui cada tabela é representada por uma classe que irá herdar de *models.Model*.

Cada atributoda classe irá consistir em um campo da tabela.

## Exemplo

~~~python
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
~~~

* A tabela será criado com a seguinte estrutura de nome: *myapp_person*.
    * Você pode definir o nome usando: *db_table = 'nome'*
* Um campo id é adicionado automaticamente como PK, mas isso pode ser mudado.

## Uso de Models

Necessário editar o arquivo *settings.py* e adicionar na lista de INSTALLED_APPS o seu app.

Depois de adicionar você vai precisar rodar os migrates.

## Fields

Os campos da tabela e seus tipos. O nome da variável será o nome do campo, logo, tem que tomar cuidado com palavras reservadas.

É possível atribuir um nome específico se você quiser.

Você pode criar tipos de campo próprios ou usar os que ja vem com o Django.

**Tipos padrão**

* IntegerField
* BooelanField
* CharField
    * Necessário especificar o max_lenght
* TextField
    * Para textos grandes.
* DateField
    * Usa uma instância de datetime.date do Python.
    * Args opcionais como auto_now para last-modified.
* DecimalField
    * Necessario dizer o max_digits e o decimal_places
* DurationField
    * Equivalente ao interval do PostgreSQL.
* EmailField
    * CharField com validações de email.
* File, Img, JsonField e etc.

Existem alguns argumentos comuns que podem ser utilizados por todos os tipos:

* null
    * Especificar que podem ser guardados valores como NULL
* blank
    * Parecido com o null, mas voltado para validação.
* choice
    * Tuplas para serem usadas como choice para um campo.
    * Vai substituir os valores.
* default
    * Definir um valor padrão
* primary_key
    * Definir como PK
* unique
    * Definir como unique

**Exemplo de choice**

~~~python
from django.db import models

class Person(models.Model):
    SHIRT_SIZES = (
        ('S', 'Small'),
        ('M', 'Medium'),
        ('L', 'Large'),
    )
    name = models.CharField(max_length=60)
    shirt_size = models.CharField(max_length=1, choices=SHIRT_SIZES)
~~~

**Primary Key**

Por padrão, o Django vai querer criar um campo chamado "id" como BigAutoField, sendo ele a Primary Key.

Mas se você quiser mudar, basta adicionar o argumento *primary_key=True* em algum dos campos do Model. Todo Model é obrigado a ter uma PK, se ele não tiver, o Django vai adicionar o id.

**Nomenado os campos**

Se você quiser nomear o campo com um nome que não seja o da variável, é só colocar como primeiro argumento o nome desejado. O Django vai trasnfromar os espaços em underline.

Se for objeto de alguma relação, então tem que usar o campo "verbose_name".

*first_name = models.CharField("person's first name", max_length=30)*

## Relacionamentos

Django oferece as três mais comuns: Many-to-One; Many-to-Many; One-to-One.

**Many-To-One**

Vai ser usado um campo normal so que do tipo ForeignKey. Sendo necessário especificar para qual model ele está se referindo.

**Exemplo**:

Um carro tem um Manufacturer mas Manufacturer tem vários carros:

~~~python
from django.db import models

class Manufacturer(models.Model):
    # ...
    pass

class Car(models.Model):
    manufacturer = models.ForeignKey(Manufacturer, on_delete=models.CASCADE)
    # ...
~~~

**Many-to-Many**

Só adicionar um campo do tipo ManyToMany.

Uma pizza tem múltiplas coberturas e uma cobertura pode ser de várias pizzas. 

~~~python
from django.db import models

class Topping(models.Model):
    # ...
    pass

class Pizza(models.Model):
    # ...
    toppings = models.ManyToManyField(Topping)
~~~

Idealmente, o objeto a ser editado é quem vai ter esse campo. Nesse caso, o "editado" seria toppings. Então pizza tem o campo toppings em vez de Toppings ter o campo pizza.

## Meta Class

Classe para os metadados do Model. Tudo que não é relacionado aos campos: ordenação, nome da tabela e etc.

~~~python
from django.db import models

class Ox(models.Model):
    horn_length = models.IntegerField()

    class Meta:
        ordering = ["horn_length"]
        verbose_name_plural = "oxen"
~~~

## Custom Methods

Você pode adicionar métodos a classe do Model para realizar qualquer coisa. Você também pode fazer o override dos métodos padrão como o save.

Você pode criar as "property"

~~~python
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    birth_date = models.DateField()

    def baby_boomer_status(self):
        "Returns the person's baby-boomer status."
        import datetime
        if self.birth_date < datetime.date(1945, 8, 1):
            return "Pre-boomer"
        elif self.birth_date < datetime.date(1965, 1, 1):
            return "Baby boomer"
        else:
            return "Post-boomer"

    @property
    def full_name(self):
        "Returns the person's full name."
        return '%s %s' % (self.first_name, self.last_name)
~~~