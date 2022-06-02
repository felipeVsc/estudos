# Laravel

Framework PHP que utiliza da arquitetura MVC (Model View Controller).

## Padrão MVC

### Model

É a camada responsável pela parte lógica da aplicação, coisas como consultas, validações, porém, eles apenas existem ali, não sabem a hora de serem chamados. 

### View

É a camada responsável pela visualização de qualquer que seja a informação, logo, ela só vai cuidar de mostrar para o usuário.

### Controller

É o middleman, camada que vai saber quando chamar algo do Model e enviar para a View.

## Funcionamento:

Controler recebe requisição &rarr; Envia requisição para o Model &rarr; Model retorna a resposta para o Controller &rarr; Controller envia para a View

![alt text](https://blog.pusher.com/wp-content/uploads/2018/04/mvc-diagram-501x300.png)

## Criação de cada parte:

### Model

Vai iterar com funções e bancos de dados.

Para cada tabela do banco de dados, é criado um arquivo, contendo as colunas.

**Migrations**

Migrations são formas de facilitar o gerenciamento de banco de dados, principalmente entre máquinas. Cria-se um *schema* do banco de dados e roda um CLI, que irá refazer aquele BD no SBGD, tipo um dump.

### Controller

Utilizando-se Resource Controllers, é possível criar as rotas de acordo com o Model do banco de dados. Assim, o Controller irá já criar as rotas necessárias para cada tipo de ação.


## Rotas:

Exemplo de rota com passagem de parametros:

Faz o esquema pela rota e passa a variável pela função

~~~php
Route::get("/user/{username}", function($username) {
    return 'texto' . $username;
});
~~~

**Passando para View**

Como array:
~~~php
Route::get("/user/{username}", function($username) {
    return view('users',['username'=> $username]); // Passa dentro da array
});
~~~

Utilizando compact() para deixar mais bonito, mas transforma em um chave valor de mesmo jeito

~~~php
Route::get("/user/{username}", function($username) {
    return view('users',compact('username')); // Passa dentro da array
});
~~~

*FORMA CORRETA:* Se for fazer algo de controle lógico, é necessário passar para o Controller, que ira chamar o Model.

## Utilizando Controllers

Pode-se criar um Controller utilizando o cli:

*php artisan make:controller UsersController*

Nas rotas, você indica qual o Controller e qual a função que aquela rota deverá chamar, e na função você tem que ter como paramêtro os paramêtros da rota.

*Rota*:

~~~php
use pathToController/UsersController;
Route::get("/user/{username}", [UsersController::class, 'funcao']
);
~~~

Pode-se colocar nome nas rotas, logo, se mudar a rota de "user/{username}" para "usuarios/{username}", não é preciso mudar no resto do código.

~~~php
use pathToController/UsersController;
Route::get("/usuarios/{username}", [UsersController::class, 'funcao']
).name("rotanome");
~~~

Na função do controller, só utilizar route("rotanome").

*Controller*:

~~~php

class UsersController extends Controller{
    public function funcao($username){
        return view('users',compact('username'))
    }
}

// Cria o Controller, extende da classe geral, cria a função que vai lidar com o username e passa ela para a view.
~~~

