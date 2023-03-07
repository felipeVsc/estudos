    # Django

## Arquitetura

Django é baseado numa arquitetura de MVT, Model View Template, parecido com a MVC (Model, View, Controller).

* Models
    * Representação dos dados
    * ORM vai cuidar disso

* View
    * Recebe o request e devolve a response. 
    * Essa response pode ser a própria página HTML.

* Templates
    * Onde ocorre a renderização dos dados em cima da página estática.

## Arquivos básicos

* Settings.py
    * Arquivo onde ficarão as configurações do Django, coisa como banco de dados, dependências.
* Urls.py
    * Define as URL's do projeto, linkando um endereço a uma view
* Manage.py
    * Wrapper do Django Admin

## Iniciando um projeto

**Criar o projeto**<br>
~~~
django-admin startproject nomeDoProjeto
~~~

**Rodar o webserver**<br>
~~~
python manage.py runserver
~~~

A porta padrão é a 8000, mas você pode deifnir adicionando a porta depois de "runserver".

Se forem feitas alterações no código, o servidor atualiza sozinho. Só é necessário reiniciar o servidor se adicionar arquivos.

**Criar a aplicação**<br>
~~~
python manage.py startapp nomeApp
~~~

* A diferença entre project e app: Project são coleções de diversos apps. Ou seja, project é o site todo, apps são cada "funcionalidade" do site.

## View

Views é a parte que vai lidar com a request do usuário e retornar uma responde.

**Exemplo de uma view:**
~~~python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
~~~

Para chamar a view temos que fazer mapear a view no arquivo **urls.py** do app, depois você precisa mapear o app no arquivo de rotas **urls.py** do projeto.

**Arquivo urls.py do app:**
~~~python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
~~~

*Path()*

Argumentos:
"" &rarr; URL, podendo conter <username> para passar como argumento.
views.index &rarr; "index" é o nome da função, podendo variar.
name &rarr; apenas um nome para aquela rota.



**Arquivo urls.py do projeto:**
~~~python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('app/', include('app.urls')),
    path('admin/', admin.site.urls),
]
~~~

## Conectando com um Banco de Dados

A configuração do driver do banco é feito no arquivo **settings.py**.

Aqui a configuração é padrão, só trocar o nome do driver, colocar infos adicionais de user, password, host e etc.

## colocar aqui as coisas do arquivo!

## Models

Representação do layout do banco de dados. Igual em Laravel!

Contém os campos e o comportamento dos dados. O data model é definido apenas aqui e o resto é derivado desse model.

Os models ficam no arquivo **models.py**.

~~~python
from django.db import models


class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')


class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
~~~

Cada "tabela"/model vai ser representado por uma classe que vai derivar de *models.Model*. As variáveis dessas classes serão os campos da tabela. Essas variáveis serão instâncias de **Field**, que pode ser chamado de várias formas como *CharField* e *DateTimeField*.

O mesmo nome da variável é o nome que irá para a coluna do banco.
Você pode definir o primeiro argumento como um nome normal. Exemplo disso é o models.DateTimeFiled('date published'), onde o 'date published' é o nome "legível".

Os campos podem ter vários argumentos, tanto obrigatórios como opcionais. O CharField tem um argumento obrigatório de max_length.

* Foreign Key:
    * Django suporta as relações padrão de um banco como many-to-one, many-to-many, one-to-one. Só realizar igual na Choice.question

**Rodando os Models**

Precisamos adicionar o app nas settings do Django. Adicionaremos a seguinte linha:<br>
**nomeDaPasta.apps.nomeProjConfig**

Ele vai referenciar a classe Config dentro do arquivo apps do app.

A partir da referência ao app no settings, você roda os migrations por meio do seguinte comando:

<code>
python manage.py makemigrations polls
</code>
