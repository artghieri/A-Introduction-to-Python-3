## Introduction












--- 

<!-- 

Função Matemáticas
Em python há função matemáticas nativas para o auxílio de seu programa como a função abs() e a função round()

print(round(3.4)) 

print(abs(-20)) ##Módulo

print(len(var))

max()

min()
Mas além disso, podemos importar o módulo math e utilizar inúmeras funções pertencentes a esse módulo.

import math

math.sqrt(4)

math.pow(2,2)

math.cos(30)

math.ceil(3.4)

#

Expressions x Statements
Statements são declarações de variáveis feitas durante o código.

valor = 1000
Expression são operações matemáticas realizadas com as variáveis ou uma linha inteira de código que realiza uma ação.

idade = (valor / 250) * 8

#

Função Nativas
hello = "hello world"

print(len(hello))

print(hello.upper())

print(hello.lower())

print(hello.capitalize())
  
print(nome.isspace())

print(nome.replace("hello", "ola"))

nome = nome.replace("hello", "ola")

print(nome) 
Acesse w3school e docs python https://docs.python.org/3/library/functions.html

**Lembre `string` são imutáveis**

#

List Unpacking
a,b,c *other, d = [1,2,3,4,5,6,7,8,9]

#

Truthy e Falsy
Quando precisarmos apenas chegar se uma variável não está vazia ou com um valor padrão designada para vazio, como é o casos dos tipos de dados numéricos (0, 0.0), podemos simplesmente verificar se o valor é True ou False.

idade = 22

if idade:
	print(f"Sua idade e: {îdade}")
else:
	print("Digite sua idade")
Casos Falsy
None
False

Numbers that are numerically equal to zero, including:
	0
	0.0
	0j
	decimal.Decimal(0)
	fraction.Fraction(0, 1)
	
Empty sequences and collections, including:
	[] - an empty list
	{} - an empty dict
	() - an empty tuple
	set() - an empty set
	'' - an empty str
	b'' - an empty bytes
	bytearray(b'') - an empty bytearray
	memoryview(b'') - an empty memoryview
	an empty range, like range(0)
	
objects for which
	obj.__bool__() returns False
	obj.__len__() returns 0, given that obj.__bool__ is undefined

 #

Short Circuiting
Em condicionais, nos casos que utilizamos os operadores lógicos and e or poderemos ter casos específicos de execucação de acordo com a seguinte condição.

if True and False:
Quando utilizamos and é checado a condição dos 2 parâmetros para o direcionamento do programa.
if True or False:
Quando utilizamos or se apenas uma das condicionais for válido (True) não é chegado a outra condicional, causando um short circuiting.
Dessa maneira conseguimos economizar tempo de processamento.

Ternários ou Expressões Condicionais
É uma operação que atribui um valor avaliado em uma condição baseada em True ou Falso.

idade = 22

status = "Maior de Idade" if idade > 18 else "Menor de Idade" 

username = ""

retorno = username if username else "Digite o username"

#

Iterables
Iterables são objetos ou coleções que podem ser verificados um por um.

Iterabale -> list, dictionary, tuple, set, string
Iterate -> verificação um por um de cada item de uma coleção
Para dicionários eu preciso informar quais itens serão percorridos: keys, values ou items

for key in dictionary.keys():
for values in dictionary.values();
for key, values in dictonary.items()
Range
Range é um tipo especial de objeto em python que cria uma objeto com um intervalo.

range(start, end, step)

list(range(start, end, step)) 
Cria uma lista com valores inteiros em um intervalo determinado.
Enumerate
Se precisar o indíce de um iterable object, podemos utilizar a função enumerate.

for index, value in enumerate(iterable_object)
for index, value in enumerate([1,2,3,4,5])

#

Break / Continue / Pass
Break: realiza uma quebra na estrutura de execução de código atual
Continue: realizar uma volta ao topo da condição de loop
Pass: ignora um bloco de execução
while True:
	resp = input("> ")
	if resp in "bye":
		break
while i < 10:
	i += 1
	continue # Nesse exemplo nunca será mostrado o print
	print(i)
for item in lista:
	pass

 #

 Positional Arguments
def pessoa(nome, idade):
	print(f"{nome} {idade}")

Positional Arguments são argumentos que são passados para os parâmetros de uma função em uma determinada ordem, portanto, isso pode afetar a saída de sua função

pessoa("nicholas", 22) 
nicholas 22
		  
pessoa(22, "nicholas")
22 nicholas
Keyword Arguments
def pessoa(nome, idade):
	print(f"{nome} {idade}")

Agora Keyword Arguments são argumentos que direcionamento diretamente os seus valores para a função

pessoa(idade="22", nome="nicholas")
nicholas 22
Default Parameters
def pessoa(nome = "Jojo", idade = 22):  
	print(f"{nome} {idade}")

pessoa()
Jojo 22

pessoa("nicholas", 30)
nicholas 30

#

Argumentos
Para passar um conjunto de elementos em uma função usaremos * ou **
def function(*arg):
	return sum(args)

function(1,2,3,4,5)


def function(arg):  
	total = 0
	for item in args:
	    total += item
	return total

function([1,2,3,4,5])
def function(*arg, **kwargs):
	total = 0
	for item in kwargs.values():
		total += items
	return sum(args) + total

function(1,2,3,4,5, num1=2, num2=1)
Ordem adotada: param, *args, default, **kwargs
**Usar \*args para listas, tuplas, sets, dicionários e conjunto de dados.**

#

Docstrings
Docstrings podem ser utilizadas para comentar uma função.

def teste(a):
	'''
	Info: This function prints a parameter
	'''
	print(a)
Para acessar o docstrings utilizaremos essa linha de comando:
print(test.__doc__)
Operador Walrus
Operador Walrus é outro nome para expressões de atribuição. De acordo com a documentação oficial, é uma forma de atribuir a variáveis dentro de uma expressão usando a notação NOME : = expr.

As expressões de atribuição permitem que um valor seja atribuído a uma variável, mesmo uma variável que ainda não existe, no contexto da expressão em vez de como uma instrução independente.

hello = "Helloooo World"

if ((n := len(hello)) > 5):
	print(f"A escrita tem {n} caracteres")
Lambda
Podemos utilizar lamba quando queremos criar uma definição em loco em função do valor de uma variável em nosso programa.

lamba var_entrada: operacoes_com_a_var_entrada  var_saida
preco = 1000

imposto = lambda preco: preco * 0.3

print(imposto(preco))

##map pega uma lista de valores e aplica uma funcao em cada valor
precos = [1000, 500, 100, 10]
imposto2 = list(map(imposto, precos))
#imposto2 = list(map(lambda preco: preco * 0.3, precos))
print(imposto2)
