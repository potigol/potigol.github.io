# Compilando Potigol

Uma forma de tornar mais rápida a execução de programas em Potigol é transcrever
os programas para a lingaugem Scala e em seguida realizar a compilação.

### Download do Potigol

Faça o download da linguagem Potigol (https://github.com/potigol/Potigol/releases/download/0.9.13/potigol.zip) e descompacte.

### Download de Scala versão 2.11.8

Faça o download da linguagem Scala (http://scala-lang.org/download/2.11.8.html) e descompacte dentro da pasta do Potigol.

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

### Linux (compilar.sh)
````
#!/bin/bash

arq=$1
nome=${arq%.*}

if [ "$1.scala" -ot "$arq" ]; then
    java -jar ./potigol/potigol.jar -d $arq > $nome.scala
fi
./scala-2.11.8/bin/scala -save -cp potigol/potigol.jar $nome.scala 2> /dev/null
````

Para testar digite:

> ./compilar.sh soma.poti

### Windows (compilar.bat)
````
@ECHO off
CHCP 65001 > NUL
SET scala_file=%~n1.scala
SET t1=%~t1
FOR %%A IN (%scala_file%) DO (SET t2=%%~tA)
IF "%t1%" GTR "%t2%" (
    java -jar %~dp0potigol.jar -d %1 > %scala_file%
    potigol %1
) ELSE (
    %~dp0scala-2.11.8\bin\scala -save -cp %~dp0potigol.jar %scala_file% 2> NUL
````

Para testar digite:

> compilar.bat soma.poti

Veja também: https://git.io/vdXlu
