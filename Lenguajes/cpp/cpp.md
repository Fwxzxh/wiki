---
title: C++
description: Oh no!!!
published: true
date: 2022-12-25T20:32:09.543Z
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

------------------------------------------------------------------------

Un programa de C++ es una colección de comandos

``` cpp
#include <iostream>

int main() {
    return 0;
}
```

El punto de entrada para cualquier programa de C++ es la función `main`.

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

Hay dos formas de este operador, prefix y posfix



![cirno_kirisame_marisa_learning_programming_cpp.png](/lenguajes/cpp/cirno_kirisame_marisa_learning_programming_cpp.png){.align-center}
