## Views

Cada view é uma função Python que irá entregar as páginas do site. 

A view vai ser mapeada para um URL, ou seja, teremos um mapeamento URL -> função python. 

### Passagem de Argumento

Só colocar os argumentos na função.

~~~python
def detail(request, question_id):
    return HttpResponse("You're looking at question %s." % question_id)

def results(request, question_id):
    response = "You're looking at the results of question %s."
    return HttpResponse(response % question_id)
~~~

A URL ele vai ficar justamente com o mesmo nome. Ou seja, a URL que vai ser mapeada para essas views com esse argumento ficará da seguinte forma:

~~~python
urlpatterns = [
    # ex: /polls/
    path('', views.index, name='index'),
    # ex: /polls/5/
    path('<int:question_id>/', views.detail, name='detail'),
    # ex: /polls/5/results/
    path('<int:question_id>/results/', views.results, name='results'),
    # ex: /polls/5/vote/
]
~~~

### Funcionamento

Todas as views tem apenas duas funções: Ou retornam um HttpResponse com o objeto da resposta ou retornam um erro Http404. 

Como ele vai fazer isso é o programador que decide. É aqui que você vai realizar operações CRUD no banco e etc. 

Não importa o que você faça, como você faça, com qual biblioteca. Você apenas deve retornar um HttpResponse e tudo certo. 

## Templates

É a forma com que você vai renderizar a resposta que vem da View. A View vai retornar "hard-coded", diretamente lá a resposta. O template deixa com que você crie algo que a view vai utilizar para demonstrar a resposta da forma desejada.

É necessário ter um **diretório chamado templates**.

O Django busca para cada INSTALLED_APPS uma pasta de template. Então você tem que ter uma estrutura ocmo: *app/templates/apps/index.html*

**Arquivos HTML**

Funcionarão como o blade, uma mistura de Python com HTML.  

## Unindo as views com os templates. 

Você precisa de um loader e de um dicionário de contexto.

* Loader
    * Irá carregar os templates
* Contexto
    * Um dicionário que irá relacionar o nome das variáveis no código HTML com o nome das variáveis na View. 

~~~python
from django.http import HttpResponse
from django.template import loader

from .models import Question


def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    template = loader.get_template('polls/index.html')
    context = {
        'latest_question_list': latest_question_list,
    }
    return HttpResponse(template.render(context, request))
~~~

Outra forma é utilizando a função render() que vai retornar um HttpResponse e vai funcionar da mesma forma. 
~~~python
from django.shortcuts import render

from .models import Question


def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    context = {'latest_question_list': latest_question_list}
    return render(request, 'polls/index.html', context)
~~~

## Erros

Você pode fazer o uso de um try-except normal e só dar o raise ou você pode utilizar o *get_object_or_404()* que vai encurtar o processo.


~~~python
from django.http import Http404
from django.shortcuts import render

from .models import Question
# ...
def detail(request, question_id):
    try:
        question = Question.objects.get(pk=question_id)
    except Question.DoesNotExist:
        raise Http404("Question does not exist")
    return render(request, 'polls/detail.html', {'question': question})
~~~

~~~python
rom django.shortcuts import get_object_or_404, render

from .models import Question
# ...
def detail(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, 'polls/detail.html', {'question': question})
~~~

## URL-Template Naming

Como você pode nomear rotas, você pode utilizar essa nomenclatura para encurtar rotas no Template. 

Ficaria assim com o seguinte path.name:

*path('<int:question_id>/', views.detail, name='detail'),*

~~~html
<li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
~~~

~~~html
<li><a href="{% url 'detail' question.id %}">{{ question.question_text }}</a></li>
~~~

Logo, se você precisar mudar o URL, basta mudar no path() e não em todos os templates.