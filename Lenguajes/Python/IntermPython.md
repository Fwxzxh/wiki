---
title: Python Intermedio
description: Apuntes sobre el curso de Python Intermedio
published: true
date: 2022-12-24T18:40:11.215Z
tags: cursos, python
editor: markdown
dateCreated: 2022-12-24T18:40:04.618Z
---

# Programación funcional

- Es un estilo de programación.
- Esta basado fuertemente en funciones.
- Una parte clave de la programación funcional son las *funciones de
  orden superior* (Higher-order function).
  - Estas funciones toman como argumentos otras funciones.

``` python
def applyTwice(func, arg):
    return func(func(arg))

def addFive(x):
    return x + 5

return applyTwice(addFive, 10)
```

> El código de arriba retorna 20.

## Funciones puras

- La programación funcional busca funciones puras.
  - No tienen efectos secundarios (side effects).
  - Retornan un valor que depende **solo** de sus argumentos.
  - Emula como las funciones en matemáticas funcionan.
- Tienen ventajas y desventajas:
  - Son más fáciles de debuggear y de testear.
  - Son más eficientes, el resultado de una función puede guardarse y
    darse a la siguiente función reduciendo el numero de veces que esta
    es llamada.
  - Mejores para correr en paralelo.
  - Pueden ser más difíciles de escribir en ciertas situaciones.

``` python
def pureFunct(x, y): # todo ocurre dentro de la función.
    temp = x + 2*y
    return temp/(2*x + y)



someList = [] # tiene efectos secundarios ya que modificamos cosas afuera de esas funciones.
def impureFunct(args):
    someList.append(args)
```

## Lambdas

- Usualmente creamos funciones con `def`.
- Podemos crear funciones sobre la marcha con `lambda`.
- Estas son funciones anónimas.
- Esto normalmente se usa para funciones simples.

``` python
def myFunc(f, arg):
    return f(arg)

myFunc(lambda x: 2*x*x, 5)
```

> Solo pueden hacer operaciones que requieren de una sola expresión.

``` python
# named function
def polynomial(x):
    return x**2 + 5*x + 4
print(polynomial(-4))

# lambda
print((lambda x: x**2 + 5*x + 4) (-4))
```

## List comprehensions

- Nos permite crear listas con una sintaxis más corta.

La sintaxis es:

> \[expression for element in iteratable if condition\]

Ejemplo:

``` python
squares = [ i for i in range(1, 101) if i % 36 == 0]
```

- La `expression` representa cada uno de los elementos a poner en la
  nueva lista.
- `for element in iterabale` es el ciclo en el cual extraeremos los
  elementos de otra lista o cualquier `iteratable`.
- `if condition` La condición opcional para filtrar los elementos del
  ciclo.
- Al final la expresión nos regresa una lista que cumple los parametros
  dados.

## Dict comprehencions

- Podemos usar las comprehencions en diccionarios.
- La sintaxis es la misma pero debemos de especificar al principio en la
  `expression` la llave y el valor.

``` python
my_dict = {i: i**3 for i in range(1,101) if 1 % 3 1= 0}
```

## Map

- Son útiles cuando trabajamos con listas o objetos iteratables.
- Toma una función y un iteratable como argumento y retorna un nuevo
  iteratable con la función aplicada a cada argumento.

``` python
def addFive(x):
    return x + 5

nums = [11, 22, 33, 44, 55]
result = list(map(addFive, nums))

# o usando una lambda
nums = [11, 22, 33, 44, 55]
result = list(map(lambda x: x + 5, nums))
```

## Filter

- `filter` Toma un iteratable y filtra los elementos que cumplen con una
  condición.

``` python
nums = [11, 22, 33, 44, 55]
res = list(filter(lambda x: x % 2==0, nums))
return res
```

<table>
<tbody>
<tr class="odd">
<td>22</td>
<td>44</td>
</tr>
</tbody>
</table>

## Reduce

Para usar esta función debemos de importar el modulo de `functools`.

``` python
from functools import reduce

my_list = [2, 2, 2, 2, 2]

all_multiplied = reduce(lambda a, b: a * b, my_list)
print(all_multiplied)
```

En este caso no nos retornaria una lista si no la suma del producto de
todos los elementos de la lista.

## Generators

- Son un tipo de iteratable, como las listas o las tuplas.
- No permiten indexar con índices arbitrarios.
- Pueden ser creados usando funciones y el operador `yield`.

``` python
def countDown():
    i = 5
    while i > 0:
        yield i
        i -= 1

for i in countDown():
    return i
```

> `yield` es usado para definir un generador, remplazando el `return` de
> una función; esto para retornar un resultado sin destruir las
> variables locales de la función.

- Debido al hecho de que solo retornan un elemento a la vez, no tienen
  restricciones de memoria y pueden ser infinitos.

``` python
def infiniteSevens():
    while True:
        yield 7

for i in infiniteSevens():
    print(i)
```

> Básicamente, los generadores nos permiten declarar funciones que se
> comportan como objetos iteratables.

- Generadores finitos pueden ser convertidos en listas.

``` python
def numbers(x):
    for i in range(x):
        if i % 2 == 0:
            yield i

print(list(numbers(11)))
```

> Usar generadores da mejor rendimiento el cual es resultado de la
> evaluación perezosa (lazy evaluation).

## Decorators

- Proveen una manera de modificar funciones usando otras funciones.
- Se usan para extender la funcionalidad de una función que no quieres
  modificar.

``` python
def decor(func):
    def wrap():
        print("=========")
        func()
        print("=========")
    return wrap

def printText():
    print("Hello world!")

decorated = decor(printText())
decorated()
```

``` example
============
Hello world!
============
```

Definimos una función `decor`, que recibe un parámetro `func`. Dentro de
`decor`, definimos una función anidada llamada `wrap`. Esta función
imprime un string, entonces llama a `func()` e imprime otro string. La
función `decor` retorna a `wrap`.

Podríamos decir que la variable `decorated`. es una versión decorada de
`printText`, es `printText` más algo más.

Si quisiéramos escribir una función decorada útil, probablemente
reemplazaríamos `printText` con la función decorada, de esa manera
siempre tendríamos `printText` "más algo", reasignando la variable que
tiene la función.

``` python
printText = decor(printText)
printText()
```

> Ahora `printText` corresponde a nuestra versión decorada.

Python provee soporte para hacer wrap de cualquier función precediendo
la declaración de esta con el nombre del decorador y el símbolo `@`.

``` python
def decor(func):
    def wrap():
        print("============")
        func()
        print("============")
    return wrap

@decor
def printText():
    print("Hello world!")

printText()
```

``` example
============
Hello world!
============
```

> Una sola función puede tener más de un decorador.

## Recursión.

- Se basa en la auto-referencia se una función
- Se usa cuando los problemas pueden resolverse partiéndonos en
  sub-problemas del mismo tipo.

> Un buen ejemplo de recursión es el factorial.

``` python
def factorial(x):
    if x == 1:
        return 1
    else:
        return x + factorial(x + 1)

factorial(5)
```

> 1! = 1 es conocido como el **caso base**, este actúa como la salida de
> la recursión, y evita que la recursión se haga infinitamente.

- También podemos tener recursión indirecta, con una función que llama a
  una segunda y esta segunda a la primera.

``` python
def isEven(x):
    if x == 0:
        return True
    else:
        return isOdd(x)

def isOdd(x):
    return not isEven(x)
```

## \*args

- Usando `*args` podemos pasarle un numero arbitrario de argumentos a
  una función.
- Los argumentos son accesibles en una tupla.

``` python
def function(named_arg, *args):
    print(named_arg)
    print(*args)

function(1, 2, 3, 4, 5)
```

``` example
1
(2, 3, 4, 5)
```

- El parámetro `*args` debe venir al final de los argumentos con nombre.
- El nombre `args` es una convención, puede ser cualquier otro.

## \*\*kwargs

- *Keyword arguments*.
- Te permite manipular argumentos con nombre que no han sido definidos
  antes.
- Estos argumentos son retornados en un diccionario.

``` python
def myFunc(x, y=7, *args, **kwargs):
    print(kwargs)

myFunc(2, 3, 4, 5, 6, a=7, b=8)
```

``` example
{'a': 7, 'b': 8}
```

> Los argumentos dados en `kwargs`, no son los mismos que se incluyen en
> `args`.

# OOP

## Clases

- El foco de la *programación orientada a objetos* (POO) son los
  **objetos**.
- Estos objetos son creados usando **clases**.
- Una clase describe como el objeto va a ser, podemos definirlo como el
  molde del objeto a crear.
- Son creadas con la palabra clave `class`.
  - Contienen métodos de clase (funciones).

``` python
class cat:
    def __init__(self, color, legs):
        self.color = color
        self.legs = legs

felix = cat("ginger", 4)
rover = car("blue", 4)
stumpy = cat("brown", 4)
```

> Aquí tenemos una clase `cat`, que tiene dos atributos: color y legs.
>
> Usamos esta clase para crear tres objetos tipo `cat` con diferentes
> atributos.

## `__init___`

- El método más importante de una clase.
- Es llamado cuando se crea una instancia (objeto) de la clase, usando
  el nombre de la clase como método.
- Deben tener `self` como primer parámetro.
  - Pero no es necesario pasarlo como argumento cuando llamas a un
    método.
  - `self` se refiere a la instancia llamando al método.
- En un método `__init__`, `self.atributo` puede ser usado para definir
  los valores iniciales en una nueva instancia.

``` python
class cat:
    def __init__(self, color, legs):
        self.color = color
        self.legs = legs

felix = cat("ginger", 4)
print(felix.color)
# Nos imprimiría, ginger
```

> En el ejemplo de arriba, el método `__init__` toma dos argumentos los
> cuales son asignados a los atributos del objeto creado.

> El método `__init__` es llamado también constructor.

## Métodos

- Las clases pueden tener otros métodos para añadir funcionalidad a esa
  clase.
- Todos los métodos deben tener `self` como primer parámetro.

``` python
class dog:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def bark(self):
        print("Woof!")

    def barkColor(self):
        print("Wooof!" + self.color) # podemos acceder a los argumentos del constructor con self

fido = dog("fido", "brown")
print(fido.name)
fido.bark()
```

> Los atributos de una clase son compartidos por todas las instancias de
> esta clase.

## Herencia

- Provee una manera de compartir funcionalidad entre clases.
- Podemos tener una clase base con ciertos métodos/atributos y
  extenderla con otras clases hijas que toman esos métodos/atributos y
  los extienden.
- Para heredar una clase a otra ponemos el nombre de la **super-clase**
  (la clase de la que queremos la funcionalidad) entre los paréntesis.

``` python
class animal:
    def __init__(self, name, color):
        self.name = name
        self.color = color

class cat(animal):
    def purr(self):
        print("Purr...")

class dog(animal):
    def bark(self):
        print("Woof!")

fido = dog("Fido", "brown")
print(fido.color)
fido.bark()
```

- Cuando una clase toma herencia de otra se le llama **sub-clase**.
- Si una clase hereda de otra y tiene los mismos atributos y/o métodos,
  estos son anulados.

``` python
class wolf:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def bark(self):
        print("Grr!")

class dog(wolf):
    def bark(self):
        print("Woof!")

husky = dog("Max", "grey")
husky.bark()
# retornaria: Woof!
```

> Podemos referirnos a la clase padre de una instancia con la función
> `super()`.

``` python
class a:
    def spam(self):
        print(1)

class b(a):
    def spam(self):
        print(2)
        super().spam()

b().spam()
```

``` example
2
1
```

## Métodos mágicos

- Son métodos especiales que tienen dos guiones bajos antes y después de
  su nombre.
  - Como el método `__init__`.
- Son conocidos también como `dunders`.
- Son usados para crear funcionalidades que no pueden hacerse usando
  métodos convencionales.
  - Un uso común de ellos es hacer sobrecarga de operadores (Operator
    overloading).
    - Esto significa definir operadores para clases personalizadas que
      permiten operadores como `*` y `+` ser usados.

``` python
class vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __add__(self, other):
        return vector2D(self.x + other.x, self.y + other.y)

first = vector2D(5, 7)
second = vector2D(3, 9)
result = first + second
print(result.x)
print(result.y)
```

``` example
8
16
```

> El método `__add__` permite un comportamiento custom de el operador
> `+` en nuestra clase.
>
> Añade los atributos correspondientes de los objetos y retorna un nuevo
> objeto con el resultado.
>
> Una vez definido podemos sumar dos objetos tipo vector.

Algunos métodos mágicos son:

`__sub__`  
para `-`.

`__mul__`  
para `*`.

`__truediv__`  
para `/`.

`__floordiv__`  
para `//`.

`__mod__`  
para `%`.

`__pow__`  
para `**`.

`__and__`  
para `&`.

`__xor__`  
para `^`.

`__or__`  
para `|`.

La expresión `x + y` es traducida como `x.__add__(y)`.

Sin embargo si en x no se ha implementado el método `__add__` y x & y
son de tipos diferentes se llama al método `y.__raad__(x)`, hay un
método `r` para cada uno de los operadores.

``` python
class specialString:
    def __init__(self, cont):
        self.cont = cont

    def __truediv__(self, other):
        line = "=" * len(other.cont)
        return "\n".join([self.cont, line, other.cont])

spam = specialString("spam")
hello = specialString("Hello world!")
print (spam / hello)
```

``` example
spam
============
Hello world!
```

> En este ejemplo definimos el operador de división para nuestra clase
> specialString.

Python nos da métodos mágicos para comparaciones.

`__lt__`  
para `<`.

`__le__`  
para `<=`.

`__eq__`  
para `==`.

`__ne__`  
para `!=`.

`__gt__`  
para `>`.

`__ge__`  
para `>=`.

> Si `__ne__` no esta implementado, retorna el opuesto de `__eq__`.

``` python
class specialString:
    def __init__(self, cont):
        self.cont = cont

    def __gt__(self, other):
        for index in range(len(other.cont)+1):
            result = other.cont[:index] + ">" + self.cont
            result += ">" + other.cont[index:]
            print(result)

spam = specialString("spam")
spam = specialString("eggs")
spam > eggs
```

``` example
>spam>eggs
e>spam>ggs
eg>spam>gs
egg>spam>s
eggs>spam>
```

> Podemos definir cualquier operación custom para cada operador.

Hay diferentes métodos para hacer que una clase se comporte como un
contenedor.

`__len__`  
para `len()`.

`__getitem__`  
para indexar.

`__setitem__`  
para asignar a valores indexados.

`__delitem__`  
para borrar valores indexados.

`__iter__`  
para iterar a travez de objetos.

`__contains__`  
para `in`.

Hay muchos más tipos de métodos mágicos como `__call__` para llamar a
objetos como funciones o `__int__`, `__str__` para convertir objetos a
otros tipo de datos.

``` python
import random

class vagueList:
    def __init__(self, cont):
        self.cont = cont

    def __getitem__(self, index):
        return self.cont[index + random.randint(-1, 1)]

    def __len__(self):
        return random.randint(0, len(self.cont)*2)


vague_list = vagueList(["A", "B", "C", "D", "E"])
print(len(vague_list))
print(len(vague_list))
print(vague_list[2])
print(vague_list[2])
```

``` example
0
10
C
B
```

## Data Hiding

- Una parte importante de la POO es el concepto de **encapsulación**.
  - Se trata de empacar un grupo de ciertas variables y funciones en un
    objeto.
- Un concepto con relación a esto es el *Data Hiding*, el cual dice que
  los detalles de implementación de una clase deben de estar ocultos, y
  ser presentados al usuario con una **interfaz** estándar y limpia.
  - En otros lenguajes esto se hace haciendo uso de métodos privados que
    bloquean acceso externo a sus variables y métodos.
- En python la filosofía va en el estilo de "we are all consenting
  adults here".
  - Significando que no deberías poner restricciones arbitrarias para
    acceder a ciertas partes de una clase asi que no hay maneras de
    hacerlo.
  - Podemos desanimar a la gente de accessar a partes de una clase
    denotando que son detalles de implementación y deben de usarse bajo
    su propio riesgo.
- Los métodos y atributos privados por convención empiezan con un solo
  guion bajo antes del nombre.
  - Esto es solo una convención porque nada te detiene de acceder a
    ellos.

``` python
class queue:
    def __init__(self, contents):
        self._hiddenList = list(contents)

    def push(self, value):
        self._hiddenList.insert(0, value)

    def pop(self):
        return self._hiddenList.pop(-1)

    def __repr__(self):
        return "Queue({})".format(self._hiddenList)


queue = Queue([1, 2, 3])
print(queue)
queue.push(0)
print(queue)
queue.pop()
print(queue)
print(queue._hiddenlist)
```

``` example
Queue([1, 2, 3])
Queue([0, 1, 2, 3])
Queue([0, 1, 2])
[0, 1, 2]
```

> En el código de arriba, `_hiddenList` esta marcado como privado, pero
> aun asi podemos acceder a el y el método mágico `__repr__` es usado
> como representación de la instancia.

- Los métodos muy privados (Strongly Private) tienen doble guion bajo
  antes del nombre.
  - Esto causa que estos elementos no puedan ser accedidos directamente
    desde afuera de la clase.
  - El propósito de esto no es para mantenerlos privados, si no evitar
    bugs si hay otros métodos o atributos con el mismo nombre.
- Estos métodos siguen siendo accesibles desde afuera de la clase, pero
  de una manera diferente.
  - El método `__privateMethod` de la clase `spam`, puede ser accedido
    escribiendo `_spam__privateMethod`.

``` python
class spam:
    __egg = 7
    def printEgg(self):
        print(self.__egg)

s = spam()
s.printEgg()
print(s._spam__egg)
print(s.__egg)
```

``` example
7
7

Traceback (most recent call last):
  File "file0.py", line 9, in <module>
    print(s.__egg)
AttributeError: 'spam' object has no attribute '__egg'
```

## Métodos de clase

- Son diferentes a los que son llamados de la instancia de un objeto son
  la palabra `self`.
- Los métodos de clase son llamados por una clase, la cual es pasada al
  argumento `cls` del método.
- Son usados como métodos fábrica (factory methods)
  - Son métodos que retornan un objeto clase (Son como un constructor),
    para diferentes usos.
  - Estos métodos son marcados con el decorador `classmethod`.
  - Esto significa que puedes usar la clase y sus propiedades dentro de
    este método sin tener que instanciar la clase.
- Es similar a *function overloading* en c++.

``` python
from datetime import date

# random Person
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def fromBirthYear(cls, name, birthYear):
        return cls(name, date.today().year - birthYear)

    def display(self):
        print(self.name + "'s age is: " + str(self.age))

person = Person('Adam', 19)
person.display()

person1 = Person.fromBirthYear('John',  1985)
person1.display()
```

``` example
Adam's age is: 19
John's age is: 31
```

`newSquare` es un método de clase y es llamado en la clase, en lugar de
ser una instancia de la clase, retorna un objeto tipo cls

> Los nombres `self` y `cls`, son solo convenciones, pueden ser
> cambiados a cualquier cosa, pero es mejor seguir las convenciones.

## Métodos estáticos

- Son similares a los métodos de clase, pero estos no reciben ningún
  argumento.
- Son idénticos a funciones normales de una clase.
- Son marcados con el decorador `staticmethod`.

``` python
class pizza:
    def __init__(self, toppings):
        self.toppings = toppings

    @staticmethod
    def validateTopping(topping):
        if topping == "pineapple":
            raise ValueError("No pineapples!")
        else:
            return True

ingredients = ["cheese", "onions", "spam"]
if all(pizza.validateTopping(i) for i in ingredients):
    Pizza = pizza(ingredients)
```

> Los Métodos estáticos se comportan como funciones normales, pero
> puedes llamarlos desde una instancia de una clase.

## Propiedades

- Proveen una manera de personalizar el acceso a atributos de una
  instancia.
- Son creados añadiendo el decorador `@property`.
- Un uso común de es hacer un atributo solo de lectura.

``` python
class pizza:
    def __init__(self, toppings):
        self.toppings = toppings

    @property
    def pineappleAllowed(self):
        return False

Pizza = pizza(["cheese", "tomato"])
print(Pizza.pineappleAllowed)
Pizza.pineappleAllowed = True
```

``` example
False


Traceback (most recent call last):
  File "file0.py", line 11, in <module>
    Pizza.pineapple_allowed = True
AttributeError: can't set attribute
```

- Propiedades pueden definirse como funciones `getter/setter`
  Los `setter`  
  Definen valores en las propiedades.

  Los `getter`  
  Obtienen los valores de las propiedades.
- Para definir un `setter`, ocupamos un decorador del mismo nombre que
  la propiedad seguido con un punto y la palabra `setter`.
  - Lo mismo aplica para los `getter`.

``` python
class pizza:
    def __init__(self, toppings):
        self.toppings = toppings
        self._pineappleAllowed = False

    @property
    def pineappleAllowed(self):
        return self._pineappleAllowed

    @pineappleAllowed.setter
    def pineappleAllowed(self, value):
        if value:
            password = input("Enter the password: ")
            if password == "Sw0rdf1sh!":
                self._pineappleAllowed = value
            else:
                raise ValueError("Alert! Intruder!")

Pizza = pizza(["Cheese", "tomato"])
print(Pizza.pineappleAllowed)
Pizza.pineappleAllowed = True # al cambiar de la propiedad nos pide la contraseña del setter
print(Pizza.pineappleAllowed)
```

``` example
False
Enter the password: Sw0rdf1sh!
True
```

# Excepciones

- Una excepción es un evento, el cual ocurre en la ejecución del
  programa y rompe el flujo de este.
- Ocurren cuando algo sale mal, puede ser por una entrada incorrecta de
  input o de codigo.

``` python
num1 = 7
num2 = 0
print(num1/num2)
```

``` example
Traceback (most recent call last):
  File "file0.py", line 3, in <module>
    print(num1/num2)
ZeroDivisionError: division by zero
```

Diferentes excepciones son levantadas por diferentes razones:

`ImportError`  
Fallo un `import`.

`IndexError`  
Una lista esta indexada con un número fuera de rango.

`NameError`  
Una variable desconocida esta siendo usada.

`SyntaxError`  
El código no puede ser parseado de manera correcta.

`TypeError`  
Una función es llamada con un valor de incorrecto tipo.

## Manejo de excepciones

- Cuando una excepción ocurre, el programa deja de ejecutarse.
- Para manejar excepciones y ejecutar código cuando ocurren se usan los
  bloques `try/except`.
  - El bloque `try` contiene código que puede lanzar una excepción, si
    esta ocurre el bloque `try` deja de ejecutarse y el código en el
    bloque `except` es ejecutado.

``` python
try:
    num1 = 7
    num2 = 0
    print(num1/num2)
    print("Done")
except ZeroDivisionError: # si ocurre la excepción ZeroDivisionError
    print("Un error ha ocurrido")
    print("Debido a division con zero")
```

``` example
Un error ha ocurrido
Debido a division con zero
```

- Un bloque `try` puede tener diferentes bloques `except` para manejar
  diferentes excepciones.
- Múltiples excepciones pueden ponerse en un bloque `except` usando
  parentesis.

``` python
try:
    variable = 10
    print(variable + "hello")
    print(variable / 2)
except ZeroDivisionError:
    print("Divided by zero")
except (ValueError, TypeError):
    print("Error occurred")
```

> Un bloque `except` sin una excepción especificada se detonara con
> cualquier excepción.

``` python
try:
    word = "spam"
    print(word / 0)
except:
    print("An error occurred")
```

``` example
An error occurred
```

## Finally

- Despues de los bloques `try/except` podemos agregar un bloque
  `finally`.
- Este bloque se ejecutara **siempre** sin importar si la excepción
  ocurrio o no.

``` python
try:
    print("Hello")
    print(1 / 0)
except ZeroDivisionError:
    print("Divided by zero")
finally:
    print("This code will run no matter what")
```

``` example
Hello
Divided by zero
This code will run no matter what
```

> Este bloque es útil, porque por ejemplo cuando trabajamos con archivos
> pueden ocurrir muchas excepciones, pero siempre debemos cerrar el
> archivo al final no importa que.

## Else

- El bloque `else` puede usarse junto con los bloques `try/except`.
- En este caso solo se ejecuta si no hubieron excepciones.

``` python
try:
    print(1)
except ZeroDivisionError:
    print(2)
else:
    print(3)

try:
    print(1/0)
except ZeroDivisionError:
    print(4)
else:
    print(5)
```

``` example
1
3
4
```

## Levantando excepciones

- Puedes lanzar excepciones arbitrariamente en tu programa con `raise`.

``` python
num = 102
if num > 100:
  raise ValueError
```

``` example
Traceback (most recent call last):
  File "file0.py", line 3, in <module>
    raise ValueError
ValueError
```

> Necesitas especificar el tipo de excepción que se va a levantar.

- Excepciones pueden ser levantadas con argumentos para dar más detalles
  sobre ellas.

``` python
name = "123"
raise NameError("Invalid Name")
```

``` example
Traceback (most recent call last):
  File "file0.py", line 2, in <module>
    raise NameError("Invalid name!")
NameError: Invalid name!
```

## Assert

- Nos permite hacer afirmaciones, si esta se cumple podemos lanzar un
  error.

sintaxis:

> `assert condition, mensaje de error`

Ejemplo:

``` python
def palindrome(string):
    assert len(string) > 0, "No se puede ingresar una cadena vacía"
    return string == string[::-1]

print(palindrome(""))
```

En el ejemplo vamos a tener una excepción `AssertionError` y en el
mensaje vendrá el mensaje que le dimos como segundo argumento al
`assert`.

- Las `assertions` son para errores del programador y no deberían ser
  manejadas por el programa, debería de crashear este.
- Para errores de los cuales se pueden recuperar usamos excepciones en
  lugar de detectarlas por `assert`.
- Usamos `assert` para cachar bug inesperados generalmente y para
  asegurarnos de que las cosas funcionan bien en ciertos puntos del
  programa.

# Archivos

## Abriendo archivos

- Es útil poder abrir, leer y escribir archivos.
- En python podemos hacerlo con la función `open`.

``` python
myfile = open("filename.txt")
```

> El argumento de `open` es la ruta al archivo.

- Puedes especificar el *modo* en el que el archivo será abierto, dando
  un segundo argumento a `open`.
  "r"  
  Significa que el archivo esta en modo lectura (default).

  "w"  
  Modo de escritura.

  "a"  
  Modo añadir, para añadir nuevo contenido al final del archivo.

  - Añadir "b" a cualquier modo, habilita el modo binario, el cual es
    usado para archivos que no son de texto.

``` python
open("filename.txt","w")
open("test.bin", "wb")
```

Después de que un archivo ha sido abierto y usado, debe ser cerrado con
la función `close`.

``` python
file = open("filename.txt", "w")
file.close()
```

## leyendo archivos

- Los contenidos de un archivo abierto pueden leerse con el método
  `read`.

``` python
file = open("filename.txt", "w")
cont = file.read()
print(cont)
file.close()
```

> El código de arriba imprime el contenido del archivo.

- Para leer una cierta cantidad de bytes de un archivo podemos dárselos
  como argumento a `read`.
- Cada carácter ASCII es 1 byte

``` python
file = open("filename.txt", "w")
print(file.read(5)) # imprime los primeros 5 caracteres
print(file.read(7)) # imprime los siguientes 7 caracteres
print(file.read()) # imprime lo restante del archivo
file.close()
```

- Para leer cada linea de un archivo podemos usar el método
  `readlines()`.
  - Esto retornará una lista con cada uno de los renglones del archivo.

``` python
file = open("filename.txt", "w")
for line in file.readlines():
    print(line)
file.close()
```

- También podemos iterar sobre la variable `file`.

``` python
file = open("filename.txt", "w")
for line in file:
    print(line)
file.close()
```

## Escribiendo archivos

- Para escribir usamos el método `write`.

``` python
file = open("filename.txt", "w")
file.write("This has been written")
file.close()
```

- Si el archivo no existe, lo creara.
- Si el archivo existe, borrara el contenido y lo reemplazara con lo que
  escribamos (en modo "w").
- Podemos agregar contenido a un archivo existente con el modo "a".

``` python
file = open("filename.txt", "a")
file.write("\nThis has been added in a new line")
file.close()
```

- El método write retorna la cantidad de bytes escritos, si es que la
  escritura es exitosa.

``` python
msg = "Hello world!"
file = open("newfile.txt", "w")
bytesWritten = file.write(msg)
file.close()
```

> Para escribir algo que no sea un string, debe de convertirse a un
> string primero.

- Es buena practica cerrar los archivos después de escribir o leer en
  ellos.
  - Una buena manera de hacer esto es con `try/finally`.

``` python
try:
    file = open("/file/file.txt")
    conf = file.read()
    print(conf)
finally:
    file.close()
```

- Una forma alternativa de hacer esto es con `with`.
  - Esto crea una variable alternativa (normalmente llamada `f`), que
    solo es accesible dentro del bloque `with`.

``` python
with open("/file/file.txt") as f:
    print(f.read())
```

> El archivo es automáticamente cerrado al final del bloque `with`.

# Extras

## Ambientes virtuales

- Un ambiente virtual es un interprete de python solo para tu proyecto.
  - Haciendo uso de este, podemos instalar dependencias sin que estas
    tengan conflictos con el interprete del sistema.
  - También con estos podemos hacer que el entorno de desarrollo sea
    reproducible para equipos grandes.

### Comandos comunes usando `venv`

- `python -m venv nombre_venv`
  - Utilizamos el modulo `venv` para crear un ambiente virtual en la
    ruta en la que estamos.
  - Dentro de esta tendremos una carpeta con los scripts para
    inicializar un ambiente virtual.
    - `./venv/Scripts/activate` en windows.
    - `venv/bin/activate` en unix.
    - Estos tienen su contraparte `deactivate` para apagar el ambiente
      virtual.

## PIP

- Es el manejador de paquetes de python.
- Nos ayuda a manejar y resolver dependencias.
- Generalmente queremos usarlo dentro de un ambiente virtual para no
  "Ensuciar" el interprete del sistema.

### Comandos comunes

- `pip freeze` : Nos muestra las dependencias instaladas con PIP.
- `pip install` : Nos ayuda a instalar algún paquete.
- `pip freeze > requirements.txt` : podemos utilizarlo para exportar
  nuestras dependencias a un archivo.
  - ahora podemos importar estas dependencias con
    `pip install -r requirements.txt`.
