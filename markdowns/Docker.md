# Tutorial Docker

* Ter o docker instalado é um bom ponto de partida

## Primeiros passos

* Criar diretorio
* Criar arquivo "Dockerfile"
* Ter o arquivo da sua linguagem 

## Como rodar?

1. ___docker build -t nomeImagem .___
    > O ponto serve para indicar onde está o Dockerfile, o -t é para dar uma tag a imagem.
2. ___docker run nomeImagem___
    > Pode ser que tenham argumentos a mais, como portas e etc, mas ai vai depender da aplicação

## Como compartilhar

1. Conta no Docker Hub, é lá que ficam as imagens
2. Criar repositório no Docker Hub
3. Logar na conta via CLI, usando: ___docker login -u "user" -p "pw" docker.io
4. docker push docker/nomeRepo:nomeImagem

## Como rodar a imagem em um novo pc

1. docker pull rep
2. docker run rep

## Como configurar o Dockerfile

~~~FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run"]
~~~

O cmd final serve para dizer quais serão os comandos que irão ser dados. No caso do exemplo, seria como digitar "flask run" no prompt.

Copy e Run requirements.txt é para se usar quando tiver dependencias, tipo o Flask, Django, Pandas, que tenham que ser instaladas via pip.

O resto das configurações vai depender muito de cada aplicação, se vai precisar da questão de portas e etc.
