# Propriedades ACID

* Atomicidade
* Consistência
* Isolamento
* Durabilidade

## Transações

Banco de dados transacionais são bancos onde cada operação é chamada de transação e é tratdo como uma unidade de trabalho.  Cada transação deverá ser totalmente completada ou irá ser cancelada, mantendo sempre o banco em um estado confiável. 

Em um Data Lake, por exemplo, os jobs podem percorrer apenas parte dos dados e você perder o ponto de quebra. Em caso de um banco transacional, se a operação não for totalmente completada, os dados não serão alterados.

## ACID

ACID são os princípios que as transações seguem. Ou seja, para ser algo transacional, precisa atender a essas propriedades. Elas trazem confiabilidade e integridade para o banco.

### Atomicidade

Cada instrução, seja um Create, Read ou outros, é tratado como uma única unidade. Ou todas as instruções daquele bloco são executadas ou nenhuma é executada. Evita a corrupção de dados.

Exemplo: Transferência de Dinheiro. São duas operções: retirada de dinheiro da Conta 1 e envio para a Conta 2. Caso não exista a Atomicidade, pode ocorrer a retirada mas não o envio. Com atomicidade tudo é considerado apenas uma operação.

### Consistência

Garantia de que as transações modifiquem apenas as tabelas de maneiras predefinidas e previsíveis. As transações devem levar o banco de um estado consistente para outro estado consistente. Toda transação deve respeitar a integridade dos dados (constraints, por ex)

Todas as regras de integridade e de negócios devem ser respeitadas. Uma transação não pode quebrar nada.

Se uma regra de negócio é que uma conta bancária não pode ter saldo negativo, então o banco tem que garantir que ao ocorrer uma transação de saque, ela não será realizada se for quebrar a regra de negócio do saldo negativo. 


### Isolamento

Transações diferentes são realizadas independentendemente, mesmo quando feitas simultaneamente. Transações não interferem umas nas outras. Toda a história de concorrência, como lidar para transações não ofertarem valores diferentes. 

Exemplo: Saques de dinheiro que não existem porque duas pessoas sacaram simultaneamente.

### Durabilidade

Garantia de que as alterações feitas por transações bem sucedidas se mantenham gravadas no banco. Se por exemplo, durante uma query SQL cair a energia, se tiver sido completada então tudo deve ter sido armazenado. Caso não, o rollback deve ser feito automaticamente.

