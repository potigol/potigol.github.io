> # Potigol é ...
> Uma linguagem moderna (funcional) para aprender a programar.

---

### *[Download](https://github.com/potigol/Potigol/releases)*

Conheça também a biblioteca de jogos 2D [Jerimum](https://potigol.github.io/Jerimum/) :video_game:

## Características
 * Projetada para ser usada por alunos iniciantes
 * Tipagem estática com inferência de tipos
 * Palavras-chave em português 
 * Multiparadigma
 * Estímulo ao paradigma funcional: valores imutáveis, casamento de padrões, funções como valores

## Como usar
  - Baixe a versão mais recente do Potigol https://github.com/potigol/Potigol/releases/latest
  - Descompacte o arquivo
  - Para executar o Editor de Código digite no prompt do terminal
  
  ````java -jar epotigol.jar````
  
   ![Editor Potigol](https://cloud.githubusercontent.com/assets/303460/8604675/7180d638-2656-11e5-9239-90d29628d9d0.png)

  - No windows basta executar `epotigol.bat`.

  - Para executar um programa em Potigol digite no prompt do terminal

  ````java -jar potigol.jar arquivo.poti````

  - No Windows basta usar `potigol arquivo.poti`.
  
Exemplos: https://github.com/potigol/Potigol/wiki/jogos

## A Linguagem

### Variáveis
````scala
x = 10                 # Declaração de um valor fixo (não pode ser alterado)
y, z = 20              # Mais de uma variável recebe o mesmo valor y = 20 e z = 20
a, b, c = 1, 2, 3      # Declaração paralela: a = 1, b = 2 e c = 3

var y := 10            # Declaração de uma variável alterável
y := y + 2             # Atribuição de um valor a uma variável
var a, b, c := 1, 2, 3 # Declaração paralela: var a := 1, var b := 2 e var c := 3
a, b, c := b, a, 4     # Atribuição paralela: a := 2, b := 1 e c := 4
````

### Operações Aritméticas
````scala
5 + 3         # 8
5 - 3         # 2
5 * 3         # 15
5 / 3         # 2.33333
5 div 3       # 1
5 mod 3       # 2
````

### Entrada
````scala
a = leia_inteiro
b = leia_real
c = leia_texto
x, y, z = leia_inteiro
números = leia_inteiros(5)      # lê um lista de 5 inteiros, um por linha
números = leia_inteiros(",")    # lê uma lista de números separados por vírgula
````

### Saída
````ruby
escreva "Olá Mundo"   # Escreve e passa para a próxima linha
imprima "Olá "        # Escreve e continua na mesma linha
escreva "Mundo"

nome = "Mundo"
escreva "Olá {nome}"
````

### Se
````python
se x > 5 então
    escreva "Maior do que cinco."
fim

###
se x > 5 então
    escreva "Maior do que cinco."
senão
    escreva "Menor ou igual a cinco."
fim

###
se x > 8 então
    escreva "Maior do que oito."
senãose x > 6 então
    escreva "Maior do que seis."
senãose x > 4 então
    escreva "Maior do que quatro."
senãose x > 2 então
    escreva "Maior do que dois."
senão
    escreva "Menor ou igual a dois."
fim
````

### Escolha
````scala
escolha x
    caso 1 => escreva "Um"
    caso 2 => escreva "Dois"
    caso 3 => escreva "Três"
    caso _ => escreva "Outro valor"
fim
````

### Para
````scala
para i de 1 até 10 faça
    escreva i
fim
````

### Enquanto
````scala
var i := 0
enquanto i<=10 faça
    escreva i
    i := i + 1
fim
````

### Funções
````scala
soma(x, y: Inteiro) = x + y
    
a, b = leia_inteiro
c = soma(a, b)
escreva "{a} + {b} = {c}"

fatorial(n: Inteiro)
    var f := 1
    para i de 2 até n faça
        f := f * i
    fim
    retorne f
fim

a = leia_inteiro
escreva "Fatorial de {a} é {fatorial(a)}"
````

## Tipos

### Número (Inteiro e Real)
````scala
12345.678.inteiro                 # 12345
12345.678.arredonde               # 12346
12345.678.arredonde(2)            # 12345.68
12345.texto                       # "12345"
12345 formato "%8d"               # "   12345"
123.45 formato "%.1f"             # "123.4"
````

### Texto
````scala
"123".inteiro                     # 123
"12abc3".inteiro                  # 12
"abc".inteiro                     # 0

"12.3".real                       # 12.3
"12a.3".real                      # 12.0
"abc".real                        # 0.0

"abc".tamanho                     # 3
"abc".posição('b')                # 2
"abc".posição('d')                # 0
"abc".contém('a')                 # verdadeiro
"abc".contém('d')                 # falso

"Abc".maiúsculo                   # "ABC"
"Abc".minúsculo                   # "abc"
"Abc".inverta                     # "cbA"

"Isto é um texto".divida          # ["Isto", "é", "um", "texto"]
"Isto é um texto".divida("t")     # ["Is", "o é um ", "ex", "o"]
"Isto é um texto".lista           # ["I", "s", "t", "o", " ", "é", " ", "u", "m", " ", "t", "e", "x", "t", "o"]

"abc".cabeça                      # 'a'
"abc".cauda                       # "bc"
"abc".último                      # 'c'
"abcde".pegue(3)                  # "abc"
"abcde".descarte(3)               # "de"

"abcb".selecione(letra => letra<>'c')          # "abb"
"abcb".descarte_enquanto(letra => letra<>'c')  # "cb"
"abcb".pegue_enquanto(letra => letra<'c')      # "ab"
````

### Lista
````scala
[2, 4, 6, 8, 10]                         # lista literal
2 :: [4, 6, 8, 10]                       # [2, 4, 6, 8, 10]
[2, 4, 6, 8, 10].tamanho                 # 5
[2, 4, 6, 8, 10].cabeça                  # 2
[2, 4, 6, 8, 10].cauda                   # [4, 6, 8, 10]
[2, 4, 6, 8, 10].último                  # 10
[2, 4, 6, 8, 10].pegue(2)                # [2, 4]
[2, 4, 6, 8, 10].descarte(2)                # [6, 8, 10]


[2, 4, 6, 8, 10].inverta                 # [10, 8, 6, 4, 2]
[2, 6, 8, 10, 4].ordene                  # [2, 4, 6, 8, 10]
[2, 4, 6] + [8, 10]                      # [2, 4, 6, 8, 10]
[2, 4, 6].junte                          # "246"
[2, 4, 6].junte(", ")                    # "2, 4, 6"
[2, 4, 6].junte("[", ", ", "]")          # "[2, 4, 6]"

a = [2, 4, 6, 8, 10]
a[3]                                     # 6
a.posição(6)                             # 3
a.posição(12)                            # 0
a.contém(6)                              # verdadeiro
a.contém(12)                             # falso
a.remova(4)                              # [2, 4, 6, 10]
a.insira(3,5)                            # [2, 4, 5, 6, 8, 10]

Lista.imutável(5, 0)                     # [0, 0, 0, 0, 0]
Lista.vazia[Inteiro]                     # []   - Lista vazia de inteiros

# Matrizes e Cubos
a = [[1, 2], [3, 4]]                     # Matriz 2x2
a[2]                                     # [3, 4]
a[2][1]                                  # 3
b = Matriz.imutável(2, 2, 0)             # b == [[0, 0], [0, 0]]
c = Cubo.imutável(2, 2, 2, "-")          # c == [[["-", "-"],["-", "-"]],[["-", "-"],["-", "-"]]] 
c[1][2][1]                               # "-"

# Listas mutáveis
a = Lista.mutável(5, 0)                      # [0, 0, 0, 0, 0].mutável
a[3] := 5                                    # a == [0, 0, 5, 0, 0].mutável
        
# Funções de alta-ordem
[2, 4, 6, 8, 10].selecione(n => n mod 4 == 0)  # [4, 8]
[2, 4, 6, 8, 10].mapeie(n => n div 2)          # [1, 2, 3, 4, 5]
[2, 4, 6]. injete(0)((a,b) => a + b)           # 0 + 2 + 4 + 6 == 12
[2, 4, 6]. injete((a,b) => a + b)              # 2 + 4 + 6 == 12
[2, 4, 6, 2, 4].pegue_enquanto(n => n < 6)     # [2, 4]
[2, 4, 6, 2, 4].descarte_enquanto(n => n < 6)     # [6, 2, 4]
````

### Tupla
````ruby
t = (2015, "potigol", 1.0)                     # Tupla do tipo (Inteiro, Texto, Real)
t.primeiro                                     # 2015
t.segundo                                      # "potigol"
t.terceiro                                     # 1.0
````

## Funções Matemáticas
````ruby
PI
sen(3.14)
cos(3.14)
tg(1)
arcsen(1)
arccos(1)
arctg(1)

abs(-2.4)                              # 2.4
raiz(9)                                # 3.0
log(2)
log10(2)

aleatório()                            # número aleatório entre 0 e 1
aleatório(10)                          # número aleatório entre 1 e 10
aleatório(1, 6)                        # número aleatório entre 1 e 6
aleatório([2, 4, 6, 8, 10])            # número aleatório pertencente à lista [2, 4, 6, 8, 10]
````

## Programação Orientada a Objetos

Classes são definidas através de tipos. Os tipos são compostos por atributos e métodos (funções). Todos elementos de um tipo são públicos, mas não é possível alterar diretamente um atributo.

### Declaração de um Tipo (Classe)
````scala
tipo «Tipo»
  «[var]» «lista de atributos do construtor» : «tipo»
  «[var]» «atributos» = «valor»
  «métodos»
fim

«obj» = «Tipo»(«lista de valores do construtor»)
«obj».«atributo»
«obj».«método»
````

#### Exemplo

````ruby
tipo Quadrado
  lado: Real
  area() = lado * lado
  perimetro() = 4 * lado
fim

q1 = Quadrado(10)
escreva q1.area
escreva q1.perimetro
````

## Programação Funcional

### Valores (constantes)
````ruby
nome = "potigol"
````

### Listas
````ruby
lista1 = [1,2,3,4]
lista2 = 0::lista1
````

### Operações com listas (filter, fold, map)
````ruby
numeros = [1, 2, 3, 4, 5, 6, 7, 8]
pares = numeros.selecione(n => n mod 2 == 0)    # filtro
soma = numeros.injete(0)((a,b) => a + b)        # fold
dobro = numeros.mapeie(n => n * 2)              # map
````

### Expressões lambda
````ruby
x = (a: Inteiro) => a * 2
escreva x(4)
````

### "list comprehension"
````ruby
y = para i de 1 até 10,
         j de i + 1 até 10 gere
           i+j
    fim
escreva y
````

### Funções de Alta ordem
````scala
f(g: Inteiro => Inteiro, a: Inteiro) =  g(a)
sucessor(n: Inteiro) = n + 1
escreva f(sucessor, 5)
````

### Currying
````scala
soma(a: Inteiro) = ((b: Inteiro) => a + b)
escreva soma(2)(3)
suc = soma(1)
escreva suc(4)
````

### Recursão em cauda otimizada
````scala
h(a, cont: Inteiro): Inteiro = escolha a
  caso 0 => cont
  caso n => h(a-1, cont+1)
fim
escreva h(1000,0)
````

### Casamento de Padrões
````scala
# QuickSort
quicksort(num: Lista[Inteiro]): Lista[Inteiro] = 
    escolha num
        caso []  => []
        caso pivo::resto => 
            menores = resto.selecione( _ <= pivo )
            maiores = resto.selecione( _ >  pivo )
            quicksort(menores) + pivo::quicksort(maiores)
    fim

escreva "Digite alguns números separados por espaços"
numeros = leia_inteiros(" ")
escreva "Os números ordenados:"
escreva quicksort(numeros)
````
