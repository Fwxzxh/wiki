---
title: Kotlin
description: 
published: true
date: 2022-12-26T01:01:19.452Z
tags: kotlin
editor: markdown
dateCreated: 2022-12-26T01:01:19.452Z
---

# Introducción

## Qué es la JVM

- `Java virtual Machine`.
- La JVM funciona como punto medio entre el código que escribimos y lo
  que entiende el sistema operativo.
- La JVM lee el bytecode que resulta de nuestro código.
- Java también produce bytecode.
  - Podemos utilizar java y kotlin al mismo tiempo porque ambos se
    convierten a bytecode.

# Conceptos Básicos

## Jerarquía de archivos de un proyecto de kotlin

- Carpeta `Gradle`
  - Nos permite gestionar las dependencias de nuestro proyecto y
    compilar nuestro proyecto.
- Carpeta `Build`
  - En la cual se encuentra todo nuestro código compilado previamente
    por gradle
- Carpeta `src`
  - En la que se encuentra nuestro código.
- Carpeta `Test`.
  - Es en la que se encuentran todos los Test de nuestra aplicación.
- Archivo `build.gradle.kts`
  - La configuración de nuestro proyecto.
    - Dependencias.
    - Versión de kotlin.
  - Archivo `gradle.properties`
    - Nos permite declarar propiedades de proyecto
  - Ejecutables `gradlew` y `gradlew.bat`
    - Ejecutables de gradle para diferentes plataformas.
  - Archivo `settings.gradle.kts`
    - Donde especificamos las propiedades del proyecto.
      - Como el nombre.

## Introducción

- Es conciso, seguro y pragmático
- Diseñado para interoperar con código en java.
- Puede ser usado en todos los lugares donde se usa java.
- Google anuncio que el desarrollo de android es "kotlin first".

## Hello World

- La función `main` es el punto de entrada de cada programa de kotlin.

``` kotlin
fun main(args : Array<String>) {
    println("Hello World")
}
```

## Tipos de datos

- Cada valor debe de tener un tipo.
- Algunos de los más usados son:
  - `int` : números enteros.
  - `Double` : números decimales.
  - `Char` : Representan un carácter.
  - `Boolean` : Representan **verdadero** o **falso**
- El tipo de dato `String` es usado para representar texto (cadenas de
  caracteres).
  - Los `String` van delimitados con comillas dobles.
  - Podemos usar `\n` para crear un salto de línea.

``` kotlin
println("A \n B \n C \n")
```

``` example
A
B
C
```

## Variables

- Son usadas para guardar datos.
- Cada variable tiene un tipo, que define el tipo de la variable.
- Se declaran usando la palabra `var`.
- También podemos declarar constantes con la palabra `const val`

``` kotlin
var num : Int = 42
```

Con esto tenemos una variable de llamada `num` de tipo `Int` que vale
42.

Ahora podríamos imprimir el resultado usando `println`.

``` kotlin
num = 8 // Podemos cambiar el valor de num
println(num)
```

También podemos declarar variables usando la palabra `val`.

``` kotlin
val course : String = "Kotlin"
println(course)
```

La diferencia es que las variables declaradas con `val` no se pueden
cambiar, son inmutables.

## Inferencia de tipos

- Kotlin soporta inferencia de tipos.
  - Esto le permite adivinar el tipo de la variable con el valor que se
    le asigna.
  - Esto nos permite saltarnos la definición de tipos.

``` kotlin
val name = "James"
var num = 42
```

## Operadores

- Kotlin soporta todos los operadores aritméticos comunes.

``` kotlin
var num1 = 8
var num2 = 34

println(num1 + num2)
println(num1 - num2)
println(num1 * num2)
println(num1 / num2)
println(num1 % num2)
```

También podemos usar el operador de `+` para concatenar `strings`.

## Operadores de asignación

Podemos combinar el operador de asignación `=` junto con operadores
aritméticos para hacer ambas operaciones.

Por ejemplo `a+=b` es equivalente a `a = a+b`.

``` kotlin
var num = 4
num *= 5

println(num)
```

Kotlin también soporta los operadores de incremento y decremento `++` y
`--`.

``` kotlin
var num = 8
num++
println(num)
```

Los operadores de incremento y decremento tienen dos versiones:

- `prefix`
  - Antes del nombre de la variable
  - Este incrementa la variable y luego usa el número.
- `posfix`
  - Después del nombre de la variable
  - Este usa el valor de la variable primero y luego lo incrementa.

## Operadores de comparación

- Kotlin contiene todos los operadores de comparación comunes.

``` kotlin
var age = 18
println(age >= 16)
```

## Comentarios

Los comentarios son texto explicatorio que usamos para describir nuestro
código.

Un comentario de una sola linea empieza con `//`.

``` kotlin
// my first kotlin program
fun main(args : Array<String>) {
    // declaring a name variable
    var name = "Amy"
    println(name)
}
```

Si necesitamos comentarios más largos podemos usar comentarios
multilinea.

Estos abarcan todo lo que pongamos entre `/*` y `*/`.

``` kotlin
fun main(args : Array<String>) {
    /* this is a multiline comment
     The program declares a string and outputs it */
    var name = "Amy"
    println(name)
}
```

## Entrada

Podemos tomar valores como entrada usando el método `readLine()`.

``` kotlin
var age = readLine()
println("You entered " + age)
```

`readLine()` retorna la entrada como un `string`

Si queremos convertir la entrada a un `Int` debemos usar la función
`toInt()`

``` kotlin
var a = readLine()!!.toInt()
var b = readLine()!!.toInt()
println(a + b)
```

El código de arriba lee dos entradas, las convierte en enteros e imprime
la suma.

El operador `!!` es llamado el `not-null assertion operator`, esto lo
que hace es que asume que la operación anterior (readLine) no es nula,
esto es necesario para que `toInt` funcione.

# Flujo de control

## `if`

El operador `if` nos permite correr un bloque de código si una condición
se cumple.

``` kotlin
if (condition) {
    // Some code to run
}
```

- La condición en los paréntesis debe ser una operación booleana.
- Si la condición retorna `true`, el código dentro del bloque se
  ejecuta.
- Si la condición retorna `false`, el código dentro del bloque no se
  ejecuta.

``` kotlin
var age = 24
if (age >= 18) {
    println("Welcome")
}
```

## `esle if`

Podemos verificar varias condiciones encadenando bloques `else if`

``` kotlin
val num = -7
if (num > 0) {
    println("Positive")
}
else if (num < 0) {
    println("Negative")
}
else {
    println("Zero")
}
```

## Expresiones condicionales

Podemos usar `if` para asignar valores a variables, así como un operador
ternario.

``` kotlin
val num = -7
val result = if (num > 0) "Positive" else "Negative"
println(result)
```

## `when`

Si hay muchas condicionales podemos usar la expresión `when` como si
fuera un `switch`

``` kotlin
var num = -7

var result = when {
    num > 0 -> "Positive"
    num < 0 -> "Negative"
    else -> "Zero"
}
println(result)
```

Se compone de varias condicionales seguidas de una flecha y un
resultado.

Si lo usamos como `switch` podemos usar mas de un elemento en el `case`
reparándolo por comas.

``` kotlin
when(color) {
     "Amarillo" -> println("Amarillo")
     "Rojo", "Carmesí" -> println("Rojo")
     else -> println("Error!")
}
```

``` kotlin
val code = 501
when(code) {
    in 200..299 -> println("Todo OK")
    in 400..500 -> println("Algo ha fallado")
    else -> println("Error!")
}
```

## Combinando operadores

Podemos combinar diferentes condiciones usando operadores lógicos.

``` kotlin
var num = 42
if (num >= 18 && num <= 60) {
    println("Yes")
}
```

Ambas condiciones deben de ser verdaderas para que el operador `&&`
retorne `true`.

``` kotlin
var name = "John"
if (name == "Jon" || name == "John") {
    println("Hi there")
}
```

similarmente el operador `or` `||` puede ser usado para verificar si una
de las condiciones es `true`.

## Ciclos `while`

Un ciclo `while` es usado cuando deseas repetir un bloque de código
siempre y cuando una condición sea verdadera.

``` kotlin
var i = 1

while (i <= 5) {
    println("Hello")
    i++
}
```

> Cada ciclo de un ciclo es llamado iteración.

``` kotlin
var sum = 0
var i = 1
while (i < 100) {
    sum += i
    i++
}
println(sum)
```

## `break` y `continue`

La palabra `break` puede ser usada para parar un ciclo de manera
prematura.

``` kotlin
var sum = 0
var i = 1
while (i <= 100) {
    sum += 1
    i++
    if (sum > 100) {
        break
    }
}
println(sum)
```

De manera similar a `break,` `continue` se salta la iteración actual del
ciclo.

``` kotlin
var sum = 0
var i = 1
while (i <= 100) {
    i++
    if (i%2 != 0) {
        continue
    }
    sum += 1
}
println(sum)
```

El código de arriba salta los números pares en el ciclo.

## Arreglos

Un arreglo nos permite guardar múltiples valores en una variable.

``` kotlin
var contacts = arrayOf("John", "James", "Amy")
```

El arreglo es declarado usando la función `arrayOf` la cual contiene sus
valores separados por comas.

Cada elemento del arreglo tiene un índice, que es usado para acceder al
elemento.

Los índices empiezan por el número 0

``` kotlin
var contacts = arrayOf("John", "James", "Amy")
println(contacts[2]) // Amy
```

## Ciclos `for`

A veces trabajando con arreglos necesitamos iterar sobre los elementos,
para esto son útiles los ciclos `for`.

``` kotlin
var nums = arrayOf(2, 4, 6)
for (x in nums) {
    println(x)
}
```

También podemos usar un ciclo `for` para iterar sobre un `string`

``` kotlin
val name = "James"
for (x in name) {
    println(x)
}
```

Esto es posible ya que los `strings` son similares a un arreglo de
caracteres, También podemos acceder a las posiciones de un `string` como
si fuera un arreglo.

``` kotlin
val name = "James"
println(name[1]) // a
```

## Rangos

Kotlin permite crear rangos de valores de manera fácil.

``` kotlin
for (i in 2..5) {
    println(i)
}
```

`2..5` crea un rango de valores del 2 al 5.

También podemos crear un rango de caracteres.

``` kotlin
for (x in 'a'..'e') {
    println(x)
}
```

También podemos verificar si un valor esta en un rango usando el
operador `in`.

``` kotlin
val x = 42
if (x in 15..100) {
    println("Yes")
}
```

Con este operador podemos verificar si un valor esta presente en un
arreglo.

``` kotlin
val x = arrayOf(8, 9, 42, 111)
if (42 in x) {
    println("Yes")
}
```

También podemos iterar en un rango el cual no incluye el elemento final
con la función `until`.

``` kotlin
for (i in 1 until 5) {
    // El 5 quedaría excluido del rango.
}
```

# Funciones

## Funciones

- Es un grupo de código que es usado para hacer una tarea.
- El nombre enfrente de los paréntesis es el nombre de la función y lo
  que se pone entre ellos son los argumentos de la función.
- Un ejemplo es la función `println()`

## Definiendo funciones

Podemos definir nuestras propias funciones con la palabra `fun`.

``` kotlin
fun welcome() {
    println("Hey there")
}
```

Después de definirla podemos llamarla de la siguiente manera.

``` kotlin
fun main(args : Array<String>) {
    welcome()
}
```

## Argumentos de funciones

Los argumentos le dan entradas a nuestras funciones.

por ejemplo si quisiéramos pasarle a una función un parámetro nombre

``` kotlin
fun welcome(name : String) {
    println("Hello " + name)
}
```

Nuestra función toma un argumento nombre de tipo `String`

``` kotlin
fun main(args : Array<String>) {
    welcome("Amy")
}
```

## Retornando de las funciones

A veces necesitaremos que las funciones retornen un valor para guardarlo
en una variable.

``` kotlin
var result = sum (8, 42)
```

Para lograr esto debemos definir el tipo de retorno en la función `sum`.

``` kotlin
fun sum(x : Int, y : Int): Int {
    return (x+y)
}
```

Nuestra función `sum` toma dos argumentos tipo entero y retorna un
entero.

## Funciones anónimas

No todas las funciones tienen un nombre, en algunos casos una función
hace una tarea muy simple con su `input`.

Estos son casos en los que es mejor usar una función anónima.

Podemos definir la función anterior `sum` como una función anónima.

``` kotlin
val f: (Int, Int) -> Int = {a, b -> a + b}
```

Nuestra función toma dos enteros y retorna un entero eso es
`(Int, Int) -> Int`, los paréntesis definen los tipos de nuestra entrada
y la flecha define el tipo de la salida.

Ahora que ya tenemos una función anónima podemos asignarla a una
variable y usarla en nuestro código.

``` kotlin
val f: (Int, Int) -> Int = {a, b -> a + b}
var result = f(8, 42)
println(result)
```

En el código anterior asignamos la función anónima a la variable `f` y
la usamos.

> También podemos acortar la función anónima saltándonos el tipo de
> retorno ya que kotlin puede adivinarlo por si mismo.

## `Foreach`

A veces debemos iterar sobre los items de un arreglo, para esto kotlin
provee la función `foreach`.

Esta toma una función, definiendo una acción a realizar para cada
elemento.

``` kotlin
fun main (args: Array<String>) {
    var arr = arrayOf(1, 3, 5)
    arr.foreach {
        item -> println(item * 4)
    }
}
```

En el código de arriba llamamos a cada elemento del arreglo `item` e
imprimimos el valor multiplicándolo por 4.

la función `foreach` es llamada con el nombre el arreglo usando la
notación de punto y debe de seguir de una función.

Kotlin también provee la palabra `it`, esto nos permitiría acortar el
código de arriba:

``` kotlin
fun main (args: Array<String>) {
    var arr = arrayOf(1, 3, 5)
    arr.foreach {
        println(it * 4)
    }
}
```

## Funciones de orden superior

Una función puede tomar como argumento otra función, estas son llamadas
funciones de orden superior.

Esto es útil cuando queremos cambiar el comportamiento de una función

``` kotlin
fun apply(x:Int, action:(Int) -> Int) : Int {
    return action(x)
}
```

`apply` es una función de orden superior que toma un entero y una
función llamada `action` con sus argumentos.

Después llama a `action` con un argumento y retorna el resultado.

Ahora podemos llamar a `apply` y pasarle diferentes funciones anónimas.

``` kotlin
println(apply(4, {x -> x*2}))
println(apply(4, {x -> x/2}))
```

En nuestras funciones anónimas no necesitamos definir el tipo de sus
argumentos, porque kotlin los adivina automáticamente.

Kotlin tiene muchas funciones de orden superior ya definidas.

Un ejemplo es `filter()` es una función que toma un arreglo y una
función booleana y retorna los elementos que dan `true` a una condición.

``` kotlin
var arr = arrayOf(42, 3, 10, 6, 4, 1)
var res = arr.filter({it > 5})
println(res)
```

El código de arriba solo imprimirá los números que sean mayores a 5.

# OOP

## Clases y Objetos

En kotlin definimos una clase con la palabra `class`

``` kotlin
class User {
    var name = ""
    var age = 0
}
```

Esta clase tiene dos propiedades: `name` y `age`.

> Una propiedad es una variable definida dentro de una clase.

Cuando tenemos una clase definida, podemos crear objetos de esa clase.

``` kotlin
val u1 = User()
u1.name = "James"
u1.age = 42
```

En el código de arriba `u1` es un objeto de tipo `User`.

Podemos acceder a las propiedades usando la sintaxis de punto junto al
nombre de la propiedad.

## Constructores

Un constructor permite inicializar propiedades cuando los objetos son
creados.

Un constructor es definido usando los paréntesis de la definición de la
clase.

``` kotlin
class User(val name:String, val age:Int) {
    // stuff
}
```

Ahora cuando creemos un objeto tipo `User` debemos pasarle los valores
para `name` y `age`.

``` kotlin
val u1 = User("James", 42)
println(u1.name)
```

> De manera similar a los argumentos de una función, podemos pasarles
> valores por defecto para los argumentos.

Kotlin nos permite crear clases con más de un constructor usando la
palabra `constructor`

``` kotlin
class User {
    var name = ""
    var age = 0

    constructor(nm: String) {
        name = nm
    }

    constructor(nm: String, a: Int) {
        name = nm
        age = a
    }
}
```

Los constructores se son como funciones tomando argumentos.

## `Getters` y `Setters`

Hasta ahora hemos accedido a las propiedades de manera directa.

Pero podemos modificar como accedemos a una propiedad, podemos poner
`getters` y `setters` para una propiedad.

Un `getter` define como accedemos a una propiedad y un `setter` define
como escribimos o modificamos esa propiedad.

``` kotlin
class User {
    var name = ""

    var age = 0
        get() = field

        set(value) {
            field = value
        }
}
```

En el código de arriba definimos un `getter` y un `setter` para la
propiedad `age`.

Se ocupa la palabra reservada `field` para referirnos a la propiedad de
la cual es el `getter` o `setter` y la palabra `value` se refiere al
valor que queremos guardar en la propiedad.

En este caso, es un `getter` y un `setter` por defecto, esto significa
que no hay una lógica detrás de como accedemos o modificamos la
propiedad.

Ahora podemos modificar la lógica del `getter` y `setter`.

``` kotlin
class User {
    var name = ""

    var age = 0
       get ()  = field - 1

       set(value) {
           if (value > 0) {
               field = 18
           }
           else {
               field = value
           }
       }
}
```

En el código de arriba, definimos un `getter` para el campo de `age`
para que retorne la edad - 1.

El `setter` esta definido para poner el número de 18 en caso de que el
valor dado sea negativo.

## Funciones de clase

Una clase puede tener funciones, las cuales definen su comportamiento.

``` kotlin
class User(var name: String, var age: Int) {
    fun login() {
        println("Login from user" + name)
    }
}
fun main(args: Array<String>) {
    var u = User("James", 42)
    u.login()
}
```

Las funciones también pueden ser llamadas usando la sintaxis del punto.

``` kotlin
class User(var name: String, var age: Int) {
    fun isAdult(): Boolean {
        if (age >= 18) {
            return true
        }
        else {
            return false
        }
    }
}
```

justo como otras funciones, podemos pasarle argumentos a estas.

## Herencia

La herencia nos permite crear clases basadas en otras clases, heredando
sus funciones.

``` kotlin
open class User(var name: String, var age: Int) {
    // ...
}

class Admin(name: String, age: Int): User(name, age) {
    // ...
}

class Moderator(name: String, age: Int): User(name, age) {
    // ...
}
```

`Admin` y `Moderator` son clases que heredan de la clase `User`, Usamos
dos puntos para definir la clase de la cual heredaremos Ambas clases
usan el constructor para inicializar sus propiedades.

La palabra `open` es necesaria para poder heredar, ya que por defecto
todas las clases son `final`.

Las clase heredadas pueden tener sus propias propiedades y funciones.

``` kotlin
open class User(var name: String, var age: Int) {
    // ...
}

class Moderator(name: String, age: Int, var country: String): User(name, age) {
    // ...
}

fun main(args: Array<String>) {
    val b = Moderator("Amy", 23, "USA")
    println(b.country)
}
```

## Modificadores de Visibilidad

Kotlin provee modificadores de visibilidad para restringir el acceso a
propiedades y métodos

- **public**: Visible en todos lados.

- **protected**: Visible solo para las subclases.

- **private**: no visible desde afuera.

  Por defecto todas las propiedades y métodos son públicos.

``` kotlin
class User(var name:String, private var age: Int) {
    // ...
}

fun main(args: Array<String>) {
    val u1 = User("Amy", 23)
    println(u1.age) // Esto dará un error ya que age es privado
}
```

> Esto permite asegurarnos de que no modifiquen la propiedad
> directamente.

Ahora cuando `age` es privado podemos definir funciones para modificar
sus valores

``` kotlin
class User(var name: String, private var age: Int) {

    fun getAge(): Int {
        if (age < 18)
            return 18
        else
            return age
    }

    fun setAge(a: Int) {
        if (a < 0)
            age = 18
        else
            age = a
    }
}
```

Esto nos permite poner y leer los valores de una manera controlada.

> Los modificadores de visibilidad también pueden aplicarse a clases.

## Clases abstractas

En algunos casos la clase base solo es necesaria por sus clases
derivadas y no crearás objetos de la clase base.

Para estos casos podemos definir una clase como abstracta.

``` kotlin
abstract class User(var name: String, var age: Int) {
    //...
}

class Admin(name: String, age: Int): User(name, age) {
    //...
}

class Moderator(name: String, age: Int, var Country: String): User(name, age) {
    //...
}
```

Ahora no podemos crear objetos tipo `User` solo crearemos objetos tipo
`Admin` y `Moderator`.

> Las clases abstractas siempre son `open` así que no necesitas poner la
> palabra `open`.

Las clases abstractas también pueden contener funciones abstractas,
funciones sin una definición que las clases derivadas tendrán que
implementar.

``` kotlin
abstract class User(var name: String, var age: Int) {
    abstract fun display()
}

class Admin(name: String, age: Int): User(name, age) {
    override fun display() {
        println(name + " is " + age + " years old")
    }
}

class Moderator(name: String, age: Int, var Country: String): User(name, age) {
    override fun display() {
        println(name + " is from " + country)
    }
}
```

Ahora cada clase tiene su propia implementación de la función `display`.
