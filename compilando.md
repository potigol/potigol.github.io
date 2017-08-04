# Compilando Potigol

Uma forma de tornar mais rápida a execução de programas em Potigol é transcrever
os programas para a lingaugem Scala e em seguida realizar a compilação.

## Preparando o ambiente

Crie uma pasta de trabalho

### Download de Scala versão 2.11.8

Faça o download da linguagem Scala (http://scala-lang.org/download/2.11.8.html) e descompacte na pasta de trabalho.

### Copiando o Potigol

Copie a pasta do potigol para a pasta de trabalho


## Compilando o programa

Crie um programa em Potigol. Por exemplo:

````
escreva "Somar dois números"
a, b = leia_inteiro
soma = a + b
escreva "Soma = {a+b}"
````

Primeiro passo é transformar o código Potigol em código Scala
> potigol -d soma.poti > soma.scala

Execute o programa em Scala usando:

> ./scala-2.11.8/bin/scala -save -cp potigol/potigol.jar soma.scala 2> /dev/null
 
Na primeira execução o programa será compilado e um arquivo chamado `soma.jar` será criado.
A partir da segunda execução não será mais necessário uma nova compilação.

## Criando um script

Criando um script para automatizar o processo de tradução e compilação. Se o arquivo `.scala` não existir ou for mais antigo
do que o `.poti` então o código Potigol é traduzido par Scala. Depois é executado.

````
#!/bin/bash

if [ "$1.scala" -ot "$1.poti" ]; then
    java -jar ./potigol/potigol.jar -d $1.poti > $1.scala
fi
./scala-2.11.8/bin/scala -save -cp potigol/potigol.jar $1.scala 2> /dev/null
````

Para testar digite:

> ./compilar.sh soma
