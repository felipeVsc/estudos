# SQL

## Criando tabelas

Definir o nome e o tipo, ficando atento ao tipo.

~~~sql
CREATE TABLE nomeTabela 
(
    campo1 varchar(),
    campo2 varchar(),
    campo3 int()
);
~~~

**Valores Pre-definidos**

Só usar enum(valores) ou check in (valores) para só permitir que aquele campo seja populado com alguma dessas coisas

~~~sql
CREATE TABLE pessoa(
    sexo enum('F','M','O')
);
~~~

### Criando e Referenciando Primary Keys

## Inserindo Dados

~~~sql
INSERT INTO tabela(campo1,campo2,campo3) VALUES (valor1,valor2,valor3);
~~~

Não precisa colocar todos os campos, mas tem que respeitar os tipos. Se for tipo DATE, uma String formatada já é convertida automaticamente
