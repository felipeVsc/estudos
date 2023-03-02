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