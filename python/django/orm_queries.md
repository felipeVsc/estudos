# Queries

ORM do Django!

## Create

Instanciar a classe do Model passando os atributos e depois dando "save()"

~~~python
>>> from blog.models import Blog
>>> b = Blog(name='Beatles Blog', tagline='All the latest Beatles news.')
>>> b.save()
~~~

## Update

Tenha a instância do objeto e depois é só usar DOT notation no atributo que você quer mudar e dar "save()" que ele irá fazer o update.

~~~python
b5.name = "new name"
b5.save()
~~~

**Atualizando FK**

Basta você passar um objeto do tipo certo.

~~~python
>>> from blog.models import Blog, Entry
>>> entry = Entry.objects.get(pk=1)
>>> cheese_blog = Blog.objects.get(name="Cheddar Talk")
>>> entry.blog = cheese_blog
>>> entry.save()
~~~

**Atualizando ManyToMany**

~~~python
>>> from blog.models import Blog, Entry
>>> entry = Entry.objects.get(pk=1)
>>> cheese_blog = Blog.objects.get(name="Cheddar Talk")
>>> entry.blog = cheese_blog
>>> entry.save()
~~~

## Retrieve

Necessário construir um QuerySet pelo Manager do seu model.

QuerySets são uma coleção de objetos que podem ou não anteder a certos filtros. É o equivalente a um SELECT. 

Todo Model tem um Manager padrão chamado objects. 

**Retrieve All**

Basicamente, você vai acessar pelo manager (objects) tudo relacionado ao model Entry. Você não faz por uma instância do modelo (ou seja, um registro) mas sim pelo Model em si.

~~~python
all_entries = Entry.objects.all()
~~~

**Filter**

Podemos adicionar filtros no select.

Existem duas formas:

* Filter() &rarr; retorna os objetos que dão match.
* exclude() &rarr; retorna os objetos que *não* dão match.

Exemplo de filtro de entradas com pub_date_year igual a 2006:
~~~python
Entry.objects.filter(pub_date__year=2006)
~~~

Você pode fazer encadeamentos de filtros:

~~~python
>>> Entry.objects.filter(
...     headline__startswith='What'
... ).exclude(
...     pub_date__gte=datetime.date.today()
... ).filter(
...     pub_date__gte=datetime.date(2005, 1, 30)
... )
~~~

Existem diversos filtros, só pesquisar aquele que você precisa.

Cada QuerySet, cada "filtro" desse vai gerar um novo, ou seja, não tem correlação com o antigo. São sempre subsets.

* São lazy, ou seja, só serão rodados mesmo as queries quando for acionado.

**Single Object**

Se quer fazer o select em apenas um único dado, então pode usar o get(), que pode ser combinado com outras coisas como o filter.

~~~python
>>> one_entry = Entry.objects.get(pk=1)
~~~

A diferença entre fazer um filtro e pegar a posição 0 e fazer um GET() é que o GET vai gerar um erro *DoesNotExist* se não existir nada e um erro *MultipleObjectsReturned* se tiver mais que um.

**Field lookup**

Para fazer o esquema do "where x <=10" você usa anotações no nome do campo.

Exemplo: 

pub_date <= 2006-01-01

~~~python
Entry.objects.filter(pub_date__lte='2006-01-01')
~~~

Podemos fazer também algo como "exact" que seria equivalente a um WHERE x == "asd"

~~~python
>>> Entry.objects.get(headline__exact="Cat bites dog")
~~~

Contains, que seria o equivalente a um "WHERE x LIKE '%asd%'

~~~python
Entry.objects.get(headline__contains='Lennon')
~~~