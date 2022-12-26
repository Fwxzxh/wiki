---
title: Go
description: 
published: true
date: 2022-12-26T08:53:36.242Z
tags: go
editor: markdown
dateCreated: 2022-12-26T00:49:04.719Z
---

# Basics

## Hello world

``` go
package main

import "fmt"

func main() {
    fmt.Println("Hello world")
}
```

``` example
Hello world
```

## Paquetes

- Todo programa de go esta hecho de paquetes (`package`).
- Siempre se empieza con el paquete `main`.

``` go
package main
```

## `Imports`

- Además del paquete `main`.
  - Go tiene diferentes paquetes que pueden ser importados.
- El más común es el paquete `fmt`.
  - `fmt` es por la palabra `format`, y nos da la habilidad de hacer
    `Imput` y `Output` de manera fácil.

``` go
import (
    "fmt"
    "math"
)
```

> Se pueden importar varios paquetes a la vez poniéndolos entre
> paréntesis.

- Cada paquete tiene palabras claves las cuales pueden ser usadas
  después de importar el paquete.
  - Cada una de estas palabras siempre empieza con mayúscula.
- En el ejemplo de arriba accedimos a la palabra clave (método)
  `Println`.
  - Este escribe texto en la consola.

> Similar a otros lenguajes `func main()` es el punto de entrada del
> programa.

## Comentarios

- Podemos poner en nuestro código comentarios.
  - Esto se hace poniendo `//`, para un comentario de una sola linea.
  - Los comentarios multilínea se hacen rodeando el texto con `/* */`.

``` go
// comentario de una sola linea
fmt.Println("go go go go!")
/* comentario
   multilínea */
```

# Conceptos básicos

## Variables

- Se usan para guardar valores.
- Se usa la palabra clave `var` para declararlas.

``` go
var i int // var <nombre de la variable> <tipo>
```

``` go
var i int = 8 // var <nombre> <tipo> = <valor de la variable>
fmt.print(i)
```

- También podemos asignar múltiples variables en una sola linea.
- Go tiene inferencia de tipos.
  - Esto significa que Go puede adivinar el tipo de la variable si a
    esta le es asignada un valor.

``` go
var i, j = 69, 42 // Go sabe que i y j son int (enteros)
```

- Go soporta asignación corta de variables.

``` go
i := 8
x, y, z := 1, 2, 3
```

> Este operador automáticamente define e inicializa las variables.

## Tipos de datos

- Los tipos de dato más comunes en go son:
  - `float32`
  - `float64`
  - `string`
  - `bool`

> La diferencia entre `float32` y `float64` es la precisión, `float64`
> representara el número con mayor precisión en los decimales.

- Go también posee `zero values` (valores cero).
  - Son variables que son inicializadas sin un valor y toman el valor 0
    de ese valor.
    - 0 para los entero.
    - `false` para los booleanos.
    - `""` para los `strings`.

## Constantes

- Las constantes son valores que no pueden cambiar su valor inicial.
- Son declaradas como las variables pero usando la palabra clave
  `const`.
- No pueden ser declaradas con la sintaxis =:.

``` go
const pi = 3.14
```

## Obteniendo `input`

- Necesitamos el paquete `fmt`.

``` go
var input string
fmt.Scanln(&input)

fmt.Println(input)
```

> El carácter `&` es usado para retornar la dirección de la variable.

``` go
var input int
fmt.Scanln(&input)

fmt.Println(input)
```

> En este ejemplo como declaramos la variable `input` como `int` go
> convertirá el input a un `int`.

## `if/else`

- Se usa para hacer decisiones.

``` go
x := 69

if x != 69 {
    fmt.Println("Not funny!")
}
else {
    fmt.Println("Maybe funny!")
}
```

> El código dentro de los corchetes no correrá a menos que la condición
> se cumpla.

- Es posible declarar una variable en el `if` si es que lo necesitas.

``` go
if x := 42; x > 18 { // se usa el ; para separar las dos operaciones.
    fmt.Println("Sup!")
}
else {
    fmt.Println("Sup'n!")
}
```

## `switch`

- Un `switch` es una manera más corta de hacer una secuencia de
  `if/else`.

``` go
num := 3

switch num {
case 1:
    fmt.Println("1")
case 2:
    fmt.Println("2")
case 3:
    fmt.Println("3")
default:
    fmt.Println(num)
}
```

- también podemos usar condiciones en los `case`.

``` go
num := 3

switch num {
    case num > 0 && x < 10:
    fmt.Println("algo")
    case num > 10:
    fmt.Println("otra cosa")
}
```

> Al igual que los `if/else`, el `switch` puede tener una declaración de
> variable antes de las expresiones condicionales.

## ciclos

- El único ciclo en Go es el ciclo `for`.
  - Este se compone de el inicio, la condición y el incremento.

``` go
for i := 0; i < 5 ; i++ {
    fmt.Println(i)
}
```

- Sin embargo podemos omitir el inicio y el incremento para hacerlo
  parecido a un `while`.

``` go
sum := 1
res := 0

for sum < = 1000 {
    res += sum
    sum ++
}
fmt.Println(res)
```

# Funciones

## Introducción a funciones

- Nos permiten definir un bloque de código que podemos llamar después.
- Nos permiten rehusar código.
- se usa la palabra `func` para definir funciones.

``` go
func welcome() {
    fmt.Println("hello")
}
```

> Hemos definido una función llamada `welcome` que imprime `Hello` en la
> consola.

``` go
func main() {
    welcome()
    welcome()
}
```

> Ahora podemos llamar a esa función cuantas veces queramos.

## Argumentos

- Son una manera de pasarle información a las funciones.
- Los argumentos se comportan como una variable dentro de el cuerpo de
  la función.
- Cuando llamemos a esta función debemos darle los argumentos que le
  hayamos puesto a la función.

``` go
func welcome(name string) {
    fmt.Println("hello,"+name)
}

func main() {
    welcome("david")
    welcome("james")
}
```

> En go el tipo del argumento va después de el nombre del argumento.

## Argumentos múltiples

- Para hacer que una función acepte múltiples argumentos usamos comas.

``` go
func sum(a int, b int) {
    fmt.Println(a+b)
}

func main() {
    sum(5,5)
}
```

> Si todos los argumentos son del mismo tipo podemos definir el tipo en
> el último ej. `sum(a, b, c int)`

## `return`

- A veces vamos a querer que nuestras funciones retornen valores.
- Para eso ocupamos la palabra `return`.
  - Este termina la función y retorna el valor dado.

``` go
func sum(x, y int) int {
    return x + y
}

func main() {
    result := sum(4, 5)
}
```

> Debemos definir el tipo de dato del retorno fuera de los argumentos de
> la función, en este caso es `int`.

## Múltiples `return`

- En go podemos retornar múltiples valores de una función.

``` go
func swap(x, y int) (int, int) {
    return y, x
}
```

> Al igual que retornando un solo valor, debemos declarar los tipos de
> los valores a retornar.

## `Defer`

- La palabra `defer` se asegura de que una función es llamada solo
  después de que la función en la que se encuentra termine o retorne.

``` go
import "fmt"

func welcome() {
    fmt.Println("welcome")
}

func main() {
    defer welcome()
    fmt.Println("Hey")
}
```

En este caso, no se llama a `welcome` hasta que se haya terminado de
ejecutar `fmt.Println("Hey")`.

> `defer` es usado normalmente para limpiar recursos, por ejemplo para
> liberar memoria usada por el código como archivos, conexiones, etc.

## Múltiples `defer`

- Si se usan múltiples `defer`, estas serán ejecutadas en orden
  `last-in-first-out`.
  - Tal como si fueran una pila.

``` go
import "fmt"

func main() {
    fmt.Println("start")

    for i := 0; i < 5; i++ {
        defer fmt.Println(i)
    }

    fmt.Println("end")
}

```

``` example
start
end
4
3
2
1
0
```

## Alcance

- El alcance (scope) es el donde una variable puede ser usada.
- Hay dos alcances principales en go `local` y `global`.
- Una variable definida en una función es local, su alcance existe solo
  dentro de esa función, afuera no existe.
- Una variable definida fuera de la función es llamada global y pueden
  ser usadas en todo el `package`.

``` go
var x = 8 // global

func test() {
    var y = 9 // local
    fmt.Println(x)
}

func main() {
    fmt.Println(x)
}
```

> Variables globales son normalmente consideradas mala práctica, es
> mejor pasar variables como argumentos.

# Punteros y `structs`

## Punteros

- Todos los valores que definimos en nuestro programa son guardados en
  la memoria y tienen su dirección de memoria única.
- Los punteros son variables especiales que guardan la dirección de
  memoria de un valor.
- En go nos referimos a un puntero con `*`.

``` go
var p *int
```

p es un puntero a un valor tipo `int`.

> Los punteros permiten pasar referencias a valores en tu programa.

- A los punteros les asignamos una dirección de memoria usando el
  operador `&`.

``` go
x := 42
p := &x
```

Ahora `p` es un puntero y mantiene la dirección de memoria de x.

``` go
package main

import "fmt"

func main() {
  x := 42
  p := &x
  fmt.Println(p)
}
```

``` example
0xc0000ba000
```

Si queremos acceder al valor de el puntero, podemos usar el operador
`*`.

``` go
package main

import "fmt"

func main() {
  x := 42
  p := &x
  fmt.Println(*p)
}
```

El operador `*` puede ser usado para cambiar el valor de la dirección de
memoria que del puntero.

``` go
package main

import "fmt"

func main() {
  x := 42
  p := &x

  *p = 8
  fmt.Println(*p)
  fmt.Println(x)
}
```

``` example
8
8
```

> Somos capaces de cambiar el valor de x usando el puntero `p`.

## Pasando punteros a funciones

- Para leer texto de la consola hemos usado punteros.

``` go
package main

import "fmt"

func main() {
  var input string
  fmt.Scanln(&input)

  fmt.Println(input)
}
```

> Aquí pasábamos la dirección de memoria de la variable `input` a la
> función `Scanln`.

Podemos pasar punteros como parámetros de una función.

``` go
package main

import "fmt"

func change(val int) {
  val = 8
}

func change_ptr(ptr *int) {
  *ptr = 8
}

func main() {
  x := 42

  change(x)
  fmt.Println(x)

  change_ptr(&x)
  fmt.Println(x)
}
```

``` example
42
8
```

- La función `change()` toma como parámetro un `int` y cambia su valor.
- La función `change_ptr()` hace lo mismo, pero toma como argumento un
  puntero a un `int`.

> La `change()` no cambio el valor de x porque el argumento es una copia
> de x y `change_ptr()` si lo cambio porque le pasamos la dirección de
> memoria de x.

## `Structs`

- Go no soporta clases, en su lugar tiene `structs`.

``` go
type Contact struct {
  name string
  age  int
}
```

Nuestro contacto tiene dos campos, nombre y edad.

Ahora podemos crear un nuevo contacto.

``` go
x := Contract{ "James", 42 }
```

`x` es ahora un `struct` que ha sido inicializado con los valores
anteriores.

También podemos darle el nombre de los campos a la hora de crearlo.

``` go
x := Contact{name: "James", age: 42}
```

Podemos acceder a los campos del `struct` de la siguiente manera.

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func main() {
  x := Contact{"James", 42}

  x.age = 8
  fmt.Println(x.age)
  fmt.Println(x.name)
}
```

``` example
8
James
```

## Punteros a `Structs`

De manera similar a punteros simples, podemos hacer punteros a
`structs`.

``` go
x := Contact{"James", 42}
p := &x
```

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func main() {
  x := Contact{"James", 42}
  p := &x

  fmt.Println(p.age)
}
```

``` example
42
```

> Podríamos acceder a `p` con `(*p).age` pero go nos permite hacerlo con
> solo `p.age`.

También podemos usar punteros cuando creamos un nuevo `struct`.

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func main() {
  p := &Contact{"John", 15}

  fmt.Println(p.name)
}
```

``` example
John
```

Ahora `p` es un puntero a el `struct` que se acaba de crear.

## Métodos

- Podemos agregarle funcionalidad a nuestros `structs` añadiéndoles
  métodos.
- Los métodos son simplemente funciones con un argumento recibidor
  adicional.

``` go
func (x Contact) welcome() {
  fmt.Println(x.name)
  fmt.Println(x.age)
}
```

> El argumento recibidor va entre el nombre del método y la palabra
> `func`.

Después de definir un método podemos acceder a el con la sintaxis punto.

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func (x Contact) welcome() {
  fmt.Println(x.name)
  fmt.Println(x.age)
}

func main() {
  x := Contact{"James", 42}
  x.welcome()
}
```

Como los métodos son solo funciones con un argumento recibidor, podemos
alcanzar la misma funcionalidad usando una función regular que toma un
`struct` como parámetro.

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func welcome(x Contact) {
  fmt.Println(x.name)
  fmt.Println(x.age)
}
func main() {
  x := Contact{"James", 42}
  welcome(x)
}
```

``` example
James
42
```

En el caso de que necesitemos cambiar los datos del `struct` en un
método podemos usar punteros.

``` go
func (ptr *Contact) increase(val int) {
  ptr.age += val
}
```

El método `increase()` usa un puntero como argumento y puede modificar
el campo de `age` del `struct`.

``` go
package main

import "fmt"

type Contact struct {
  name string
  age int
}

func (ptr *Contact) increase(val int) {
  ptr.age += val
}

func main() {
  x := Contact{"James", 42}
  x.increase(8)
  fmt.Println(x.age)
}
```

``` example
50
```

# `Array`, `Range`, `Map`

## `Arrays`

Un arreglo es una secuencia de elementos del mismo tipo.

Un arreglo es definido usando corchetes en el cual se define el número
de elementos que tendrá.

``` go
var a [5]int
```

Ahora `a` es un arreglo de 5 elementos.

También podemos inicializar los valores del arreglo usando la siguiente
sintaxis.

``` go
a := [5]int{0, 2, 4, 6, 8}
```

> Debemos dar el tamaño del arreglo cuando lo declaremos, los arreglos
> tienen siempre un tamaño fijo.

Después podemos acceder a los elementos del arreglo usando corchetes y
su índice

``` go
var a [5]int

a[0] = 8
a[1] = 42

fmt.Println(a[1])
```

Cada elemento del arreglo tiene su propio índice iniciando en 0.

> Por defecto, los elementos del arreglo son inicializados al valor cero
> de su tipo.

## `Slices`

Por defecto los arreglos tienen un tamaño definido y fijo, para mejorar
esto go provee `slices`

Un `slice` es una vista dinámica de los elementos de un arreglo.

Esta basado en un en un arreglo y se define dando dos índices, el índice
inferior y el superior.

``` go
a := [5]int{0, 2, 4, 6, 8}

var s []int = a[1:3]
```

Este código selecciona los elementos desde el índice 1 a 3 del arreglo
`a`, incluyendo el primer índice pero excluyendo el último.

Así que el `slice` `s` ahora incluye los valores `[2,4]`

> Podemos omitir ya sea el índice inferior o el superior, omitir el
> inferior dará por defecto al índice 0 y omitir el superior tomara el
> tamaño del arreglo.

Por ejemplo: `a[:3]` tomará los primeros 3 elementos del arreglo.

Podemos acceder a los valores de un `slice` usando la misma sintaxis que
un arreglo.

``` go
a := [5]int{0, 2, 4, 6, 8}
var s[]int = a[1:3]

fmt.Println(s[1])
```

Un `slice` no guarda ningún dato, solo describe una sección de un
arreglo de fondo. Cambiar los elementos de un `slice` modifica el
arreglo de fondo.

> Podemos tener muchos `slices` del mismo arreglo, y cualquier cambio en
> alguno de ellos se reflejara en todos lados.

Go provee la función `make()` para crear `slices`, es así como creamos
arreglos dinámicos.

``` go
a := make([]int, 5)
```

La función `make()` crea un arreglo del tipo dado y tamaño y retorna un
`slice` que se refiere a ese arreglo.

Después de crear la `slice`, podemos agregar nuevos elementos a el
usando la función `append()`.

``` go
package main

import "fmt"

func main() {
    a := make([]int, 5)
    a = append(a, 8)
    fmt.Println(a)
}
```

``` example
[0 0 0 0 0 8]
```

La función `append()` toma una `slice` como primer argumento y los
elementos a ser añadidos al final de este como su siguiente argumento.

Esta retorna un nuevo `slice` que contiene el viejo `slice` más los
nuevos elementos.

> Podemos agregar múltiples valores al mismo tiempo reparándolos por
> comas, EJ: `append(s, 1, 2, 3, 5)`

## `Range`

La variación `range` del ciclo `for` nos permite iterar en una `slice`

``` go
package main

import "fmt"
func main() {
    a := make([]int, 5)
    a[1] = 2
    a[2] = 3

    for i, v := range a {
        fmt.Println(i, v)
    }
}
```

``` example
0 0
1 2
2 3
3 0
4 0
```

Por cada iteración del ciclo, imprime el índice del elemento y cada
valor del `slice`.

Si solo queremos los valores, podemos ignorar el índice con un guion
bajo.

``` go
for _, v := range a {
    fmt.Println(v)
}
```

> Podemos usar `range` para `slices` y para arreglos.

También podemos usarlo para iterar sobre los caracteres de un `string`

``` go
package main

import "fmt"

func main() {
    x := "hello"
    for _, c := range x {
        fmt.Println(c)
    }
}
```

Esto imprimirá los números de los caracteres unicode de la palabra, si
queremos los caracteres debemos usar la función `Printf()`

``` go
for _, c := range x {
    fmt.Printf("%c \n", c)
}
```

> La función `Printf` es similar a la que existe en C.

## `Maps`

Los `maps` son usados para guardar pares `llave:valor` donde la llave es
siempre única.

Podemos crear un `map` usando la función `make()`, de manera similar a
los arreglos.

``` go
m := make(map[string]int)
```

ahora `m` es un `map` que mapea una llave tipo `string` a un valor
`int`.

``` go
package main

import "fmt"

func main() {
    m := make(map[string]int)
    m["James"] = 42
    m["Amy"] = 24

    fmt.Println(m["James"])
}
```

``` example
42
```

También podemos inicializar un `map` con la siguiente sintaxis:

``` go
m := map[string]int{
    "James": 42,
    "Amy": 24
}

fmt.Printf(m["Amy"])
```

Si una llave no existe en el `map`, un valor 0 será retornado

> También son llamados diccionarios o arreglos asociativos o tablas de
> hash.

Podemos usar `delete` para eliminar un elemento del `map`

``` go
delete(m, "James")
```

## Funciones `Variadicas`

Estas funciones son funciones que pueden ser llamadas con cualquier
número de argumentos.

Por ejemplo, `Println()` es un función variadica ya que podemos darle n
número de argumentos separados por comas.

También podemos definir nuestras propias funciones:

``` go
func sums(nums ...int) {
    total := 0
    for _, v := range nums {
        total += v
    }
    fmt.Println(total)
}
```

La función de arriba calcula la suma de todos los argumentos que le
demos.

ahora podemos usarla dándole n número de argumentos:

``` go
sum(2, 4, 6)
sum(42, 8)
sum(1, 2, 3, 4, 5, 6)
```

> Los tres puntos antes del tipo la definen como variadica.

Si tenemos múltiples valores en un `slice` y queremos usarlos como
argumentos para una función variadica, podríamos usar la siguiente
sintaxis

``` go
s := []int{42, 33, 22, 11}
sum(s...)
```

# Concurrencia

## introducción

Concurrencia significa que múltiples tareas de computación están
sucediendo al mismo tiempo.

Es sobre crear múltiples procesos y ejecutarlos de manera independiente.

Cuando usamos concurrencia, somos capaces de lograr los resultados
deseados en menos tiempo, mejorando el rendimiento de nuestros
programas.

Para lograr la concurrencia go provee las `gorutinas`

Una `gorutina` es parecido a un hilo para lograr diferentes tareas, pero
consume menos recursos que hilos del sistema operativo.

> Las `gorutinas` son hilos virtuales, manejados por go, podemos tener
> cientos de `gorutinas` corriendo en un programa de go.

## `Gorutinas`

Teniendo el siguiente programa:

``` go
package main
import (
    "fmt"
    "time"
)

func out(from, to int) {
    for i := from; i <= to; i++ {
        time.Sleep(50 * time.Millisecond)
        fmt.Println(i)
    }
}

func main() {
    out(0, 5)
    out(6, 10)
}
```

``` example
0
1
2
3
4
5
6
7
8
9
10
```

La función `out()` solo imprime los números en un rango dado, usamos
`time.Sleep` para emular trabajo entre las iteraciones, espera 50
milisegundos en cada iteración.

> A esto se le llama programa secuencial, debido a que cada operación es
> ejecutada una después de la otra, y espera a que llamada anterior
> termine de ejecutarse antes de seguir con la siguiente.

Cuando corremos programas concurrentes, no queremos esperar a que
termine una tarea para hacer otra.

Podemos convertir el programa anterior a concurrente usando `gorutinas`
agregando la palabra `go` a las llamadas de la función.

``` go
package main
import (
    "fmt"
    "time"
)

func out(from, to int) {
    for i := from; i <= to; i++ {
        time.Sleep(50 * time.Millisecond)
        fmt.Println(i)
    }
}

func main() {
    go out(0, 5)
    go out(6, 10)
}
```

Si corremos este programa no recibiremos ningún `output`, eso pasa
porque la función `main()` termina antes que nuestras `gorutinas`.

> Nuestro programa tiene 3 hilos virtuales, las dos llamadas de
> funciones y la función `main`, las dos funciones son ejecutadas de
> manera concurrente pero `main` no espera a que terminen.

## Canales

Para permitir a las gorutinas comunicarse entre ellas, go provee
canales.

Un canal es como una tubería (pipe), permitiendo recibir y mandar datos
entre `gorutinas`, remitiéndolas comunicarse y sincronizarse.

Para crear un canal, primero debemos hacer uno con la función `make()`.

``` go
ch := make(chan int)
```

El tipo después de la palabra `chan` indica el tipo de datos que vamos a
mandar a través del canal.

Podemos mandar datos por el canal usando la siguiente sintaxis:

``` go
ch <- 8
```

De manera similar podemos recibir datos desde el canal usando la
siguiente sintaxis:

``` go
value := <- ch
```

Si no necesitamos el valor como una variable, podemos hacer lo
siguiente:

``` go
<- ch
```

Ahora podemos usar nuestro canal y re escribir el ejemplo anterior de
manera que tengamos `output`

``` go
package main
import (
    "fmt"
    "time"
)

func out(from, to int, ch chan bool) {
    for i := from; i <= to; i++ {
        time.Sleep(50 * time.Millisecond)
        fmt.Println(i)
    }
    ch <- true
}

func main() {
    ch := make(chan bool)

    go out(0, 5, ch)
    go out(6, 10, ch)

    <- ch
}
```

``` example
0
6
7
1
2
8
3
9
10
```

Como podemos ver, el `output` no esta ordenado esto es porque ambas
tareas ocurrieron de manera concurrente.

Definimos un canal tipo `bool` y se lo pasamos a nuestra función `out`
como argumento, Después de que la función termina su tarea mandamos el
valor `true` al canal el cual es recibido en la función `main`.

Ahora `main` esta esperando a recibir datos del canal, haciendo que el
hilo `main` espere a que las `gorutinas` terminen de ejecutarse.

> La operación de recibir bloquea el código hasta que datos sean
> mandandos por la pipe, Si no se recibe ningún dato, ocurrirá un
> `deadlock`, bloqueando el programa.

También podemos mandar datos desde una `gorutina` y usarla en la función
`main()`

Nuestro programa necesita calcular e imprimir la suma de todos los
números pares en un rango dado más la suma de sus cuadrados e imprimir
el resultado.

``` go
package main
import (
    "fmt"
)

func evenSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i
        }
    }
    ch <- result
}

func squareSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i * i
        }
    }
    ch <- result
}

func main() {
    evenCh := make(chan int)
    sqCh := make(chan int)

    go evenSum(0, 100, evenCh)
    go squareSum(0, 100, sqCh)

    fmt.Println(<- evenCh + <- sqCh)
}
```

``` example
174250
```

Usamos canales para obtener el resultado de cada `gorutina` e imprimir
su suma.

> Si no necesitas mandar datos a un canal, puedes usar `close(ch)`,
> donde `ch` es el nombre del canal para cerrarlo.

## `Select`

La palabra `select` es usada para esperar en operaciones de múltiples
canales.

La sintaxis es similar al `switch`, solo que cada `case` será una
operación de canal.

``` go
package main
import (
    "fmt"
)

func evenSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i
        }
    }
    ch <- result
}

func squareSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i * i
        }
    }
    ch <- result
}

func main() {
    evenCh := make(chan int)
    sqCh := make(chan int)

    go evenSum(0, 100, evenCh)
    go squareSum(0, 100, sqCh)

    select {
        case x := <- evenCh:
            fmt.Println(x)
        case y := <- sqCh
            fmt.Println(y)
    }
}
```

El `select` espera que el canal reciba los datos y ejecuta el `case`.

Un `select` puede tener un caso `default`, este se ejecutará cuando
ninguno de los `case` esta listo.

``` go
package main
import (
    "fmt"
    "time"
)

func evenSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i
        }
    }
    ch <- result
}

func squareSum(from, to int, ch chan int) {
    result := 0
    for i := from; i <= to; i++ {
        if i%2 == 0 {
            result += i * i
        }
    }
    ch <- result
}

func main() {
    evenCh := make(chan int)
    sqCh := make(chan int)

    go evenSum(0, 100, evenCh)
    go squareSum(0, 100, sqCh)

    for {
        select {
            case x := <- evenCh:
                fmt.Println(x)
                return
            case y := <- sqCh:
                fmt.Println(y)
                return
            default:
                fmt.Println("Noting available")
                time.Sleep(50 * time.Millisecond)
        }
    }
}
```

``` example
Noting available
2550
```

En este ejemplo el ciclo `for` infinito usa un `select` para verificar
que canal obtuvo datos, si ninguno esta listo el caso `default` se
ejecutará y esperará 50 milisegundos.

En cuanto un canal obtenga datos, el `return` detendrá el ciclo y
saldrá.

El bloque `select` bloqueará el hilo hasta que ocurra uno de los `case`,
El `default` es útil para prevenir `deadlocks`, sin el `select` el
programa esperaría por siempre hasta que el programa se cerrara.
