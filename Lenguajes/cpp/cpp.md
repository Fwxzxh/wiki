---
title: C++
description: Oh no!!!
published: true
date: 2023-03-24T07:48:04.895Z
tags: cpp, lenguajes
editor: markdown
dateCreated: 2022-12-25T18:07:47.487Z
---

# Conceptos Básicos
![cirno_teaches_cpp.jpg](/lenguajes/cpp/cirno_teaches_cpp.jpg){.align-center}
## C++

- Es un popular lenguaje multiplataforma de uso general.
- Puede ser usado para hacer aplicaciones de alto rendimiento.
- C++ esta derivado de C.
- Es considerado un superset de C, pero no lo es.

------------------------------------------------------------------------

Un programa de C++ es una colección de comandos

``` cpp
#include <iostream>

int main() {
    return 0;
}
```

El punto de entrada para cualquier programa de C++ es la función `main`.

## Compiladores, linkers y librerías
Para convertir nuestro código en algo útil necesitamos un compilador.
Este corre con cada uno de nuestros archivos y hace dos cosas importantes.

1. Verifica que nuestro código sea código valido de C++, si no, te dará un error.
2. Convierte tu código de C++ en un archivo de código máquina llamado `object file`.
   1. Generalmente tienen una forma parecida a `name.o` (Unix) o `name.obj` (Windows).
   2. Cada uno corresponde a un archivo de C++.

Después de que el compilador crea los objetos, otro programa llamado `linker` entra este:

1. Toma todos los objetos generados por el compilador y los combina en un solo ejecutable
2. Linkea los archivos de librerías (Código escrito por alguien más y empaquetado para usarlo).
3. Se encarga de que todas las dependencias entre archivos estén resueltas.

### Hola mundo

``` cpp
#include <iostream>

int main()
{
    cout << "Hello world!";
    cout << " This " << "is " << "awesome";
    return 0;
}
```

- `cout` es usado para imprimir en la salida estándar (consola).
- Es usado en conjunto con el operador de inserción `<<`.

## `Headers` y `namespaces`

- C++ ofrece diversos `headers` cada uno conteniendo información para
  que los programas se ejecuten de manera correcta.
- El `header` `iostream` define los objetos estándar para la entrada y
  salida de datos

``` cpp
#include <iostream>
using namespace std; // <- Namespace

int main()
{
    cout << "Hello world!";
    return 0;
}
```

- Un `namespace` es un espacio de nombres, provee un alcance a los
  identificadores que se encuentran dentro del `namespace`.
- En nuestro código, `using namespace std` dice que vamos a usar el
  espacio de nombres `std`, en nuestro archivo.
  - `std` incluye funcionalidades de la biblioteca estándar de c++.

## Salto de linea

Para meter saltos de línea a nuestro mensaje en consola utilizamos
`endl`.

``` cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    cout << "I love programing";
    return 0;
}
```

También podemos hacer uso del carácter de salto de linea en lugar de
`endl`

``` cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world! \n";
    cout << "I love programing";
    return 0;
}
```

El `\` indica que es un carácter especial.

## Comentarios

Los comentarios son lineas que el compilador ignora y son usadas para
documentar el código.

``` cpp

#include <iostream>
using namespace std;

int main()
{
    // <- Esto es un comentario
    cout << "Hello world! \n";
    cout << "I love programing";
    /*
      comentari multilinea
     */
    return 0;
}
```

- Los comentarios que empiezan con `/*` y terminan con `*/` son
  comentarios multilinea.
- Los comentarios que empiezan con dos diagonales son comentarios de una
  sola línea.

## Statements
Un `statement` o declaración, es un tipo de instrucción que hace que el programa haga *algo*.

Estos son los más comunes en un programa de c++ ya que son la unidad más pequeña de computación.

Hay algunos tipos diferentes de statements:
* Declaration Statements
* Jump Statements
* Expression Statements
* Compound Statements
* Selection Statements (Condicionales!)
* Iteration Statements (loops!)
* Try Blocks

## Funciones y la función main
En c++ los statements se agrupan en unidades llamadas **funciones**.

Una función es una colección de statements que es ejecutada sequencialmente.

> Todo programa de c++ debe tener una función main

Los programas suelen terminar su ejecución con el ultimo statement de la función main.

> Las funciones son escritas para que hagan un trabajo en especifico.

## Variables

- Crear una variable reserva un espacio en la memoria para guardar esta
  variable.
  - Para esto el compilador necesita el tipo de esta variable, para
    guardar la cantidad exacta de espacio.
- C++ tiene tipos por defecto además de que podemos definir los
  nuestros.
- Diferentes sistemas operativos y arquitecturas pueden reservar
  diferentes tamaños de memoria para cada tipo.

``` cpp
#include <iostream>
using namespace std;

int main()
{
    int myVariable = 10;
    cout << myVariable;
    return 0;
}
```

C++ es sensible a las mayúsculas con las variables.

------------------------------------------------------------------------

Podemos definir varias variables en una sola linea si son del mismo
tipo.

``` cpp
int a, b, c;
int sum = a + b + c;
```

Todas las variables deben de ser definidas con un nombre y un tipo antes
de ser utilizadas.

## Trabajando con variables

Podemos decidir si asignar un valor a una variable o hacerlo después.

``` cpp
int a;
int b;

a = 10;
b = 20;
```

Para leer la entrada de un valor en la consola ocupamos `cin`.

``` cpp
int num;
cin >> num;
```

El siguiente ejemplo le pide al usuario un valor y lo guarda en la
variable `a`.

``` cpp
#include <iostream>
using namespace std;

int main()
{
    int a;
    cout << "Please enter a number" << endl;
    cin >> a;
    return 0;
}
```

También podemos tener un ejemplo más complejo:

``` cpp
#include <iostream>
using namespace std;

int main()
{
    int a, b;
    cout << "Please enter a number" << endl;
    cin >> a;
    cout << "Enter another number \n";
    cin >> b;
    cout << "Sum is: " << sum << endl;
    return 0;
}
```

## Más sobre variables

- Especificar el tipo de dato es requerido solo una vez, cuando esta es
  declarada, después podemos usarla sin declarar su tipo.
- Una variable puede ser cambiada cada que sea necesario.
- Podemos usar la palabra `auto` para inferir el tipo automáticamente.
  - Las variables declaradas con `auto` deben ser inicializadas con un
    valor siempre.

``` cpp
auto x = 4; // integer
auto y = 3.37; // float
auto z = "hello"; // string
```

## Operador de asignación e incremento

- Todos los operadores aritméticos son los mismos: `+-*/%`
- También podemos hacer una asignación y operación aritmética en una
  sola linea.

``` cpp
int x = 20;
x += 4; // equivalente a x = x + 4
x -= 5; // equivalente a x = x - 4
```

También están los operadores de incremento y decremento

``` cpp
int x = 20;
x++; // equivalente a x = x + 1
x--; // equivalente a x = x - 1
```

Hay dos formas de este operador, prefix y postfix

```cpp
++x; // prefix
x++; // postfix
```

* **Prefix** Incrementa el valor y después procede con la expresión.
* **Postfix** Evalúa la expresión y después hace el incremento.

**Prefix**
```cpp
x = 5;
y = ++x;
// x es 6, y es 6
```
> Incrementamos el valor de x y después lo asignamos a y

**Postfix**
```cpp
x = 5;
y = x++;
// x es 6, y es 5
```
> Asignamos el valor de x a y y después incrementamos.

# Condicionales

## `if`
Es usado para ejecutar un bloque de código si la condición es verdadera,
si no, el bloque de código es ignorado.

```cpp
if (condition) {
    // statements
}
```

```cpp
if (7 > 4) {
    cout << "Yes";
}
```

```cpp
if (7 != 10) {
    cout << "Yes";
}
```

## `else`
Un `if` puede proseguir con un bloque `else` opcional, el cual se ejecuta si la condición es falsa.

```cpp
if (condition) {
  //statements
}
else {
 //statements
}
```

## ciclos
Un ciclo repite un bloque de código hasta que una condición es satisfecha.

un ciclo `while` ejecuta un bloque de código mientras una condición se cumpla.
```cpp
while (condition) {
    // statements..
}
```

![cirno_kirisame_marisa_learning_programming_cpp.png](/lenguajes/cpp/cirno_kirisame_marisa_learning_programming_cpp.png){.align-center}
