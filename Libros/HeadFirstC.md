---
title: Head First C
description: Notas sobre Head First C de David Griffith & Dawn Griffiths.
published: true
date: 2022-12-24T03:21:13.839Z
tags: libros, c, head first
editor: markdown
dateCreated: 2022-12-24T03:21:06.301Z
---

# Getting started with C

## but what does a complete C program look like?

-   Para crear un programa necesitas escribir tu código en un archivo
    -   Normalmente terminan con la extensión `.c`{.verbatim}.
-   Normalmente empiezan con un comentario.
    -   Este describe el propósito del código o programa
-   Luego viene la sección de `imports`{.verbatim}
    -   C es un lenguaje muy pequeño y casi no puede hacer nada sin el
        uso de librerías externas
    -   Necesitas decirle al compilador que código externo usar con el
        uso de `header files`{.verbatim}
    -   Un header común es `stdio.h`{.verbatim} este contiene código que
        permite leer y escribir datos de la terminal
-   Lo ultimo que verás en un archivo de c serán las funciones
    -   Todo el código en C corre dentro de funciones.
    -   La función más importante es llamada `main()`{.verbatim}.
        -   Esta es el punto de inicio de todo el código en tu programa

``` c
/*
 * Program to calculate the number of cards in the shoe.
 * This code is released under the Vegas Public License.
 * (c)2014, The College Blackjack Team.
 */

#include <stdio.h>

int main () {
    int decks;
    puts("Enter a number of decks");
    scanf("%i", &decks);
    if (decks < 1) {
        puts("That is not a valid number of decks");
        return 1
    }
    printf("There are %i cards\n", (decks * 52));
    return 0
}
```

### La función `main`{.verbatim}

-   La computadora empezará a correr el programa desde la función main
    -   El nombre es importante, debe de llamarse `main()`{.verbatim}.
-   Esta tiene un tipo de retorno `return type`{.verbatim} de entero
    (`int`{.verbatim}).
    -   Esto es porque la computadora necesita tener un método de saber
        si tu programa ejecuto sin errores.
        -   La computadora sabe esto verificando el valor de retorno de
            la función `main`{.verbatim}.
    -   Si el programa retorna 0, significa que el programa se ejecuto
        sin errores.
    -   Si le dices que retorne algún otro número, significa que hubo un
        problema.
-   El nombre de la función se escribe después del tipo de retorno.
    -   Si la función `main`{.verbatim} necesitará algún parámetro estos
        irían entre los paréntesis `()`{.verbatim}.
    -   Después viene el cuerpo de la función, el cual debe estar entre
        llaves `{}`{.verbatim}.

### La función `printf`{.verbatim}

-   Es usada para mostrar texto formateado en la terminal.
-   Reemplaza caracteres de formato con los valores de las variables.

``` c
printf("%s says the count is %s", "ben", 21);
```

-   `%s`{.verbatim} será insertado como un `string`{.verbatim}.
-   `%i`{.verbatim} será insertado como un `int`{.verbatim}.
-   Y estos van en orden junto con los otros parámetros
    -   `"ben"`{.verbatim} siendo un `string`{.verbatim}.
    -   `21`{.verbatim} siendo un `int`{.verbatim}.

### Ejemplo

``` c
// Program to evaluate face values.

#include <stdio.h>
#include <stdlib.h>

int main() {
    char card_name[3];
    puts("Enter the card_name: ");
    scanf("%2s", card_name); // leemos 2 caracteres
    int val = 0;
    if (card_name[0] == 'K') { // Obtenemos el primer carácter de card_name
        val = 10;
    } else if (card_name[0] == 'Q') {
        val = 10;
    } else if (card_name[0] == 'J') {
        val = 10;
    } else if (card_name[0] == 'A') {
        val = 11;
    } else {
        val = atoi(card_name);
    }


    printf("The card value is: %i\n" val);
    return 0;
}
```

## But How do you run the program?

-   C es un lenguaje compilado
    -   Esto significa que necesitas convertir (compilar) el código a
        código maquina.
    -   Para hacer esto necesitas un programa llamado compilador.
    -   Uno de los más populares es gcc.

Suponiendo que se guardo el programa anterior con el nombre
`cards.c`{.verbatim}:

-   Necesitamos escribir:
    -   `gcc cards.c -o cards`{.verbatim}
        -   Esto dice: compila el archivo `cards.c`{.verbatim} en un
            ejecutable llamado `cards`{.verbatim}.
    -   ahora podemos correr el programa escribiendo
        `./cards`{.verbatim}.
-   Podemos compilar y correr nuestro código en un solo comando
    haciendo:
    -   `gcc cards.c -o cards && ./cards`{.verbatim}
        -   el `&&`{.verbatim} básicamente dice \"si se completa con
            éxito, haz esto otro\".
        -   En un sistema windows podrías necesitar escribir
            `cards`{.verbatim} solamente en lugar de
            `./cards`{.verbatim}.

### Teoría de `Strings`{.verbatim}

C no tiene soporte para `strings`{.verbatim} por defecto (esto porque es
de más bajo nivel que otros lenguajes), así que tenemos que usar un
arreglo de caracteres para simular un `string`{.verbatim}.

-   Los `strings`{.verbatim} son en esencia un arreglo de caracteres
    individuales.
-   De esta manera podemos referirnos a los caracteres de un
    `string`{.verbatim} con su índice.

C al ser de más bajo nivel que otros lenguajes no siempre puede saber el
que tan largo un arreglo es.

Si C va a escribir algo en la pantalla, necesita saber en donde termina
este `string`{.verbatim}, y lo hace usando un **carácter centinela**.

Este carácter es un carácter al final del `string`{.verbatim} que tiene
el valor `\0`{.verbatim}. Entonces cuando escribe carácter por carácter
se va a detener cuando encuentre este centinela.

> Se suele referir a este como el carácter `null`{.verbatim}.

Si tenemos `s = "shatner"`{.verbatim} C lo guarda en la memoria como
`shatner\0`{.verbatim}

Esta es la razón por la que en nuestro código usamos
`char card_name[3];`{.verbatim}. Vamos a leer 2 caracteres, pero ponemos
que nuestro arreglo es de 3 porque hacemos espacio para el centinela.

1.  `string literals`{.verbatim} y arreglos

    -   Los arreglos son numerados desde el 0 y no desde el 1 porque:
        -   El índice en C es un `offset`{.verbatim} una compensación.
            -   La computadora va a guardar caracteres en bytes
                consecutivos de memoria.
            -   La computadora puede usar este índice para calcular la
                posición de un carácter en la memoria.
                -   Si `c[0]`{.verbatim} esta en la posición de memoria
                    `1000000`{.verbatim}, C puede calcular que
                    `c[96]`{.verbatim} esta en
                    `1000000 + 96`{.verbatim}.
    -   Debemos usar comillas simples `''`{.verbatim} para los
        caracteres individuales y las comillas dobles `""`{.verbatim}
        para los `strings literals`{.verbatim}.
        -   Podemos usar estos como `strings`{.verbatim} normales, pero
            estos son inmutables.
            -   Entonces no podemos cambiar el contenido de estos una
                vez son creados.
                -   Si lo hacemos obtendremos un error al compilar.

### Painless Operations

En C, el símbolo de igual (=) es usado para asignaciones. pero un doble
igual es usado para verificar igualdad. Pero también lo podemos usar
para hacer operaciones

``` c
teeth = 4; // asignación
teeth == 4; // igualdad
teeth += 2; // Sumar dos a teeth
teeth -+ 2; // Sestar dos a teeth
theeth ++; // Incrementar teeth 1
theeth --; // Decrementar teeth 1
```

## Dos tipos de comandos

Hasta ahora cada comando que se ha visto cae en una de dos categorías:

### Haz algo

La mayoría de los comandos en C son expresiones. Estos **hacen** cosas y
nos **dicen** cosas.

``` c
split_hand(); // <- expresión simple
```

A veces agrupamos expresiones juntas para crear un **bloque** y estos
están entre llaves.

``` c
{
    deal_first_card();
    deal_second_card();
    cards_in_hand = 2;
}
```

### Haz algo **solo si** algo más es verdadero

Expresiones de control como el `if`{.verbatim} verifican una condición
antes de correr el código.

``` c
if (value_of_hand <= 16) // Condición
    hit(); // Esta expresión correrá si la condición es verdadera.
else
    stand(); // Corre esta expresión si la condición es falsa.
```

Si una expresión `if`{.verbatim} necesita hacer más de una cosa, podemos
agregar las llaves para hacer un bloque

``` c
if (dealer_card == 5) {
    double_down();
    hit();
}
```

## There\'s more to booleans than equals

Hay ocasiones en las cuales queremos ver si varios elementos son
verdaderos

### `&&`{.verbatim} verifica si dos condiciones son verdaderas

El operador `&&`{.verbatim} retorna verdadero, solo si **ambas**
condiciones dadas son verdaderas.

``` c
if ((dealer_up_card == 6) && (hand == 11))
    double_down();
```

Si la primera condición es verdadera, entonces se evalúa la segunda. Si
este no fuera el caso, la computadora no evalúa la segunda.

### `||`{.verbatim} Evalúa si una de las condiciones es verdadera

El operador `or`{.verbatim} (`||`{.verbatim}) retorna verdadero si
**cualquiera** de las condiciones dadas es verdadera.

``` c
if (cupcakes_in_fridge || chips_on_table)
    eat_food();
```

### `!`{.verbatim} Invierte el resultado de la condición

`!`{.verbatim} es el operador `not`{.verbatim}, este invierte el
resultado de una condición.

``` c
if (!brad_on_phone)
    answer_phone();
```

### booleanos

En C los valores booleanos son representados con números, Para C el
número 0 es falso y cualquier número que no sea 0 es tratado como
verdadero.

Así que código como el siguiente funciona.

``` c
int people_moshing = 35;
if (people_moshing)
    take_off_glases();
```

En C también podemos usar `|`{.verbatim} y `&`{.verbatim} en lugar de
`||`{.verbatim} y `&&`{.verbatim}, pero estos **siempre** evalúan ambas
condiciones, mientras que los otros puede saltarse evaluar la segunda
condición.

Los operadores `| y &`{.verbatim} existen porque hacen operaciones de
bit a bit en los bits individuales de un número por ejemplo:

`6 & 4`{.verbatim} es igual a 4 ya que si verificamos que bits binarios
tienen en común 6 (110 en binario) y 4 (100 en binario) obtenemos (100).

## Pulling the ol\' switcheroo

A veces cuando escribimos lógica condicional, necesitamos verificar el
valor de la misma variable más de una vez, para evitar tener muchos
`if`{.verbatim} tenemos el `switch`{.verbatim}

``` c
switch (train) {
    case 37:
        winnings = winnings + 50;
        break;
    case 65:
        winnings = winnings + 80;
        break;
    case 12:
        winnings = winnings + 20;
        break;
    default:
        winnings = 0;
}
```

Cuando la computadora llega a un `switch`{.verbatim} verifica el valor
que se le dio y busca un caso que se sea igual. Cuando lo encuentra,
corre **todo** el código que sigue partir de allí en adelante hasta que
se encuentre un `break`{.verbatim}

No debemos olvidar poner `breaks`{.verbatim} cuando los necesitamos
porque nuestro código podría no funcionar como queremos.

## Sometimes once is not enough

### Usando ciclos `while`{.verbatim} en C

Ciclos son un tipo especial de sentencias de control. Un ciclo decide
cuantas veces una pieza de código será ejecutada.

El ciclo más básico de C es el ciclo `while`{.verbatim}. Este ejecuta
código una vez tras otra mientras una condición sea verdadera.

``` c
while (<some condition>) { // <- Verifica la condición antes de correr el bloque
    // Haz algo aquí // <- Si hay una sola linea en el cuerpo no necesitas las llaves.
} // <- Cuando la computadora llega al final del bloque vuelve a verificar si la condición es verdadera.
```

### `do while`{.verbatim}

Hay una variación de el ciclo `while`{.verbatim} que verifica la
condición del loop después de ejecutar el código.

Por lo tanto el código es ejecutado al menos una vez.

``` c
do {
    // Algo
} while (have_not_won);
```

## Los ciclos a veces siguen la misma estructura

-   Hacer algo simple antes del ciclo, como poner un contador
-   Tener una condición simple en el ciclo.
-   Hacer algo al final del ciclo, como actualizar un contador.

``` c
int counter = 1;
while (counter < 11) {
    printf("%i green bottles, hanging on a wall\n", counter);
    counter++;
}
```

### El ciclo `for`{.verbatim}

Los diseñadores de c crearon el ciclo `for`{.verbatim} para hacer esta
estructura más consista.

Este es el mismo ejemplo de arriba con un ciclo `for`{.verbatim}

``` c
int counter;
for (counter = 1; counter < 11; counter++){
    printf("%i green bottles, hanging on a wall\n", counter);
}
```

En el ciclo `for`{.verbatim} inicializamos la variable del ciclo
(`counter=1`{.verbatim}). Damos una condición que debe de ser verificada
(`counter < 11`{.verbatim}) en cada iteración y tenemos un código que va
a ser ejecutado al final (`counter++`{.verbatim}).

## Usas un `break`{.verbatim} para salir

Puedes crear ciclos que verifican una condición al inicio o al final de
un bloque de código. Pero también podemos salir del ciclo con la palabra
`break`{.verbatim}.

``` c
while (feeling_hungry) {
    eat_cake();
    if (fealing_queasy) {
        // Salimos del ciclo
        break; // El break te saca del ciclo inmediatamente
    }
    drink_coffee();
}
```

Los `breaks`{.verbatim} te sacan del ciclo saltándose todo el código que
siga dentro del bloque del ciclo.

### Usamos `continue`{.verbatim} para continuar

Si queremos saltarnos todo el código que sigue en el bloque e ir a la
siguiente iteración.

``` c
while (feeling_hungry) {
    eat_cake();
    if (fealing_queasy) {
        // Salimos del ciclo
        continue; // lo usamos para regresar al inicio del bloque de código
    }
    drink_coffee();
}
```

## Escribiendo funciones

Casi todas las funciones en C siguen el mismo formato, por ejemplo

``` c
#include <stdio.h>

int larger (int a, int b) { // <- Recibe dos argumentos a y b
    if (a > b)
        return a;
    return b;
    }

int main () {
    int greatest = larger(100, 1000);
    printf("%i is the largest!\n", greatest);
    return 0;
    }
```

-   La función `larger`{.verbatim} es diferente a `main`{.verbatim}
    porque recibe dos argumentos.
    -   Un argumento es una variable local (solo pertenece ese bloque de
        código) que obtiene su valor de cuando se llama.
    -   La función `larger`{.verbatim} toma como argumentos a y b que
        son enteros y estos deben de ser dados siempre.

### Funciones `void`{.verbatim}

A veces necesitamos crear funciones que no tienen nada útil que
retornar, para esto esta el tipo `void`{.verbatim}. Con este nuestras
funciones no tienen que tener un `return`{.verbatim}.

``` c
void complain() {
    puts("I'm really not happy"); // :c
}
```

En C la palabra `void`{.verbatim} significa \"no importa\", cuando tu le
digas al compilador que no te importa retornar un valor en tu función,
no necesitaras un `return`{.verbatim}.

### Encadenando sentencias

Casi todo en C tiene un valor de retorno, no solo llamadas a funciones.
De hecho cosas como asignaciones tienen valores de retorno. Por ejemplo

``` c
x = 4;
```

Asigna el número 4 a una variable. la parte interesante es que la
expresión `x = 4`{.verbatim} en **si misma** tiene el valor que será
asignado

1.  

Esto es importante porque significa que puedes encadenar asignaciones.

``` c
y = (x = 4); // Ahora y es 4 también.
y = x = 4; // lo mismo que arriba.
```

Se usan sentencias encadenadas para asignar variables que tienen el
mismo valor.

# What are you pointing at?

El lenguaje C te da mucho más control sobre como tu programa usa la
memoria de la computadora de lo normal, es necesario saber como C maneja
la memoria.

## El código en C incluye Punteros

Un **puntero** es solo la dirección de una pieza de información en la
memoria.

Los punteros son usados por unas cuantas razones:

1.  En lugar de pasar un copia de los datos, solo pasas el puntero de
    donde esta la información en memoria.
2.  Podríamos querer que dos trozos de código trabajen con la misma
    pieza de información en lugar de con una copia.

## Escarbando en la memoria.

Cada vez que se declara una variable, la computadora crea espacio en
algún lugar de la memoria para estos datos.

Si declaras una variable dentro de la función `main`{.verbatim} la
computadora la guardará en una sección de la memoria llamada la pila
(`stack`{.verbatim}).

Si una variable es declarada afuera de **cualquier** función será
guardada en la sección global (`globals`{.verbatim}) de la memoria.

La computadora podría asignar la dirección de memoria de 4,100,000 en la
pila para la variable x, si en la variable x guardamos un 4 este se va a
guardar en la misma dirección de memoria.

Podemos saber la dirección de memoria de una variable con el operador
`&`{.verbatim}.

``` c
printf("x is stored at %p\n", &n); // &p es usado para dar formato a direcciones.
```

Dandonos algo como esto.

``` example
x is stored at 0x3E8FA0
```

`0x3E8FA0`{.verbatim} es 4,100,000 en formato hexadecimal (base 16).

Esta seria la dirección de memoria en donde se guarda nuestra variable,
se le llaman punteros porque apuntan a la variable en memoria.

## Usando punteros de memoria

Hay 3 cosas que debes de saber para usar punteros para leer y escribir
datos.

### Obtener la dirección de memoria

Podemos obtener la dirección de memoria de una variable con el operador
`&`{.verbatim}.

``` c
int x = 4;
printf("x lives at %p\n", &x);
```

Pero ya que podemos acceder a la dirección de memoria debemos guardarla
en algún lado, para eso necesitamos una **variable puntero**.

Una variable puntero es una variable que guarda una dirección de
memoria.

Cuando declaramos una variable puntero, debemos decir de que tipo de
dato esta guardado en esa dirección de memoria.

``` c
int *addres_of_x;
```

### Leer los contenidos de la variable

Cuando ya tienes la dirección de memoria guardada, querrás leer la
información que esta allí, lo haces con el operador `*`{.verbatim}.

``` c
int value_stored = *addres_of_x;
```

El operador `*`{.verbatim} y `&`{.verbatim} son opuestos.

El operador `&`{.verbatim} toma un pedazo de datos y te dice donde están
guardados. Y el operador `*`{.verbatim} toma una dirección y te dice que
esta guardado allí.

Los punteros a veces son llamados *referencias*, el operador
`*`{.verbatim} se dice que deferencia una asignación.

### Cambiar el contenido de una dirección

Si tienes una variable puntero y quieres cambiar la información de la
dirección podemos usar el operador `*`{.verbatim} de nuevo.

``` c
*addres_of_x = 99;
```

Solo debemos de tener en cuenta de usar el operador `*`{.verbatim} del
lado izquierdo del asignamiento.

## Como pasar un `string`{.verbatim} a una función

Ya podemos pasar argumentos simples como enteros y booleanos, pero que
pasa si queremos pasar algo más complejo, como un `string`{.verbatim}.

Los `strings`{.verbatim} son cadenas de caracteres, así que podemos
hacer lo siguiente:

``` c
void fortune_cookie(char msg[]) {
    printf("Message reads: %s\n", msg);
}

char quote[] = "Cookies make you fat :c";
fortune_cookie(quote);
```

### Honey, who shrank the string?

C tiene un operador llamado `sizeof`{.verbatim} que puede decirte
cuantos bytes de espacio algo tiene en memoria.

``` c
sizeof(int); // <- 4
sizeof("Turtles!"); // 9 ya que son 8 caracteres más el \0.
```

Algo extraño pasará si vemos la longitud de un `string`{.verbatim} que
pasamos a una función

``` c
void fortune_cookie(char msg[]) {
    printf("Message reads: %s\n", msg);
    printf("msg occupies %i bytes\n", sizeof(msg)); // Nos puede dar 4 u 8 bytes
}
```

## Variables arreglos son parecidos a los punteros

Cuando creamos una variable arreglo, puede ser usada como un puntero al
inicio de el arreglo en memoria.

``` c
char quote[] = "Cookies make you fat";
```

La variable `quote`{.verbatim} representará la dirección del primer
carácter en el `string`{.verbatim}.

La computadora, apartara el espacio en el `stack`{.verbatim} para cada
uno de los caracteres en el `string`{.verbatim} más el carácter
`\0`{.verbatim}, pero también asociará la dirección del primer carácter
con la variable `quote`{.verbatim}.

Cada vez que llamemos a esa variable la computadora la **sustituirá con
la dirección del primer carácter**, en el `string`{.verbatim}.

La variable arreglo es como un puntero.

> printf(\"The quote string is stored at: %p`\n`{=latex}\", quote); //
> Podemos usar quote como un puntero aunque sea un array

Dando algo como esto:

``` example
The quote string is stored at: 0x7fff69d4bdd7
```

### Así que a nuestra función se le paso un puntero.

Esta es la razón porque `sizeof`{.verbatim} nos daba un valor no
esperado, estaba recibiendo un puntero.

``` c
void fortune_cookie(char msg[]) {
    printf("Message reads: %s\n", msg); // msg apunta al mensaje.
    printf("msg occupies %i bytes\n", sizeof(msg)) // Nos dará el tamaño del puntero
}
```

En un sistema operativo de 32 bits, un puntero usa 4 bytes y en uno de
64 toma 8 bytes de memoria.

### Operadores y funciones

`sizeof`{.verbatim} es un operador, la diferencia entre un operador y
una función es que el primero es compilado a una secuencia de
instrucciones por el compilador. pero si el código llama a una función
tiene que saltar a una pieza separada de código.

## Ejemplo: Dating Game

``` c
#include <stdio.h>

int main () {
    int contestants[] = {1, 2, 3}; // Creamos el arreglo con 3 elementos
    int *choice = contestants; // creamos una variable puntero apuntando al arreglo
    contestants[0] = 2;
    contestants[1] = contestants[2];
    contestants[2] = *choice; // al leer la información del puntero obtendremos el primer elemento del array.
    printf("I'm going to pick contestant number %i\n", contestants[2]); // será el 2
    return 0;
    }
```

## Pero variables arreglo no son como punteros

Podemos usar los arreglos como punteros pero hay algunas diferencias.

``` c
char s[] = "How big is it?";
char *t = s;
```

### `sizeof(array)`{.verbatim} es un el tamaño del arreglo

Ya vimos que si hacemos `sizeof`{.verbatim} de un arreglo obtendremos 4
u 8, pero si hacemos lo mismo con un arreglo, C nos dará el tamaño de
ese arreglo

``` c
char s[] = "How b ..";
sizeof(s); // Nos dará la longitud del array
char *p = s;
sizeof(p); // Nos dará 4 u 8;
```

### La dirección del arreglo es la dirección del arreglo

Una variable puntero es *solo* una variable que guarda una dirección de
memoria, pero si usamos el operador `&`{.verbatim} en un arreglo, el
resultado es el arreglo en si mismo.

``` example
&s == s &t != t
```

`&s`{.verbatim} es la dirección del arreglo `s`{.verbatim}, y
`&t`{.verbatim} es la dirección de la variable `t`{.verbatim}

### Una variable arreglo no puede apuntar a ningún otro lado

Cuando creamos un arreglo, la computadora asignará el espacio de memoria
para guardar el arreglo, pero no guardará *ninguna* memoria para guardar
la variable arreglo.

La computadora solo guarda la dirección de memoria al inicio del
arreglo.

### Pointer decay

Debido a estas diferencias debemos de ser cuidadosos al asignar arreglos
a variables puntero.

Si asignamos un arreglo a una variable puntero, entonces la variable
solo tendrá la **dirección** del arreglo.

El puntero no sabe nada sobre el tamaño del arreglo, así que se perdió
un poco de información.

A esto se le llama *pointer decay* (deterioro de puntero)

Cada vez que pasamos un arreglo a una función, deterioramos el arreglo a
un puntero,

Esto es inevitable, así que debemos saber donde hay deterioros así en
nuestro código para evitar bugs.

## Porque los arreglos realmente empiezan en 0

Una variable arreglo puede ser usada como un puntero al primer elemento
en un arreglo.

Eso significa que puedes leer el primer elemento de un arreglo usando
los corchetes `[]`{.verbatim} o usando el operador `*`{.verbatim}.

``` c
int drinks[] = {4, 2, 3};
// Todas estas lineas son equivalentes
printf("1st order: %i drinks\n", drinks[0]);
printf("1st order: %i drinks\n", *drinks);
```

Pero porque las direcciones son solo un número, eso significa que
podemos hacer *aritmética de punteros* y *sumar* valores a una variable
puntero para encontrar la siguiente dirección.

En este caso, podemos usar los corchetes para leer el elemento con
índice 2 o añadir 2 a la dirección del primer elemento.

``` c
printf("3rd order: %i drinks\n", drinks[2]);
printf("3rd order: %i drinks\n", *(drinks + 2));
```

En general, las dos expresiones son equivalentes, es por eso que los
arreglos empiezan en 0, El índice es solo el número que se le agrega al
puntero para encontrar la dirección del elemento.

## Los punteros tienen tipos

La razón por lo que la aritmética de punteros tiene truco, es porque si
tu sumas 1 a un puntero de caracteres, el puntero apuntará ahora a el
siguiente carácter es porque un carácter ocupa **1 byte de memoria**.

Si tenemos un puntero tipo `int`{.verbatim}, estos usualmente toman 4
bytes de espacio, así que si sumamos 1 a un puntero tipo
`int`{.verbatim}, el código sumará 4 bytes a la dirección de memoria.

Los tipos en los punteros sirven para que el compilador sepa cuando
ajustar la aritmética de punteros.

así que podemos hacer cosas como estas:

``` c
int doses[] = { 1, 3, 2, 1000 };
// Todos los ejemplos de abajo son equivalentes.
doses[3] == *(doses + 3) == *(3 + doses) == 3[doses]
```

## Usando punteros para entrada de datos

Ya sabemos usar `scanf`{.verbatim} para leer del teclado.

``` c
char name[40];
printf("Enter your name: ");
scanf("%39s", name); // el %39 hace que solo leamos 39 caracteres ya que el 40 es \0
```

`scanf`{.verbatim} funciona cuando le damos una variable arreglo.

Funciones que necesitan actualizar una variable no necesitan el valor de
la variable en si, si no su **dirección**.

### Introduciendo números con `scanf`{.verbatim}

Para meter datos en un campo numérico le pasamos el puntero a una
variable numérica.

``` c
int age;
printf("Enter your age: ");
scanf("%i", &age); // %i significa que leeremos números enteros, y le pasamos la dirección de memoria de la variable.
```

También podemos usar `scanf`{.verbatim} para leer más de una pieza de
información al mismo tiempo.

``` c
char fist_name[20];
char last_name[20];
printf("Enter first and last name: ");
scanf("%19 %19", first_name, last_name); // Lee el primer nombre, luego un espacio y después el segundo nombre
printf("First: %s last: %s\n", firt_name, last_name);
```

## Se cuidadoso con `scanf`{.verbatim}

`scanf`{.verbatim} puede causar desbordamientos si no le ponemos un
límite, como en el siguiente ejemplo.

``` c
char food[5]; // Guardamos 5 caracteres
printf("Enter favorite food: ");
scanf("%s", food); // No ponemos limite en la cantidad de caracteres a leer
printf("Favorite food: %s\n", food);
```

Si en el código de arriba, damos una respuesta de más de 5 caracteres
nuestro programa crasheara ya que `scanf`{.verbatim} escribe más allá de
los 5 caracteres asignados para el arreglo `food`{.verbatim}.

A esto se le llama `buffer overflow`{.verbatim} y puede crashear nuestro
programa o crear bugs.

## `fgets()`{.verbatim} como alternativa a `scanf`{.verbatim}

`fgets`{.verbatim} es una función parecida a `scanf`{.verbatim}, pero a
diferencia de `scanf`{.verbatim} debemos darle una longitud máxima.

``` c
char foodp[5];
printf("Enter favorite food: ");
fgets(food, sizeof(food), stdin);
```

`fgets`{.verbatim} toma, un puntero, después el tamaño máximo a leer, y
después de donde leer estos datos, en este caso de decimos
`stdin`{.verbatim} que es `standard input`{.verbatim} o que lea del
teclado.

### Usando `sizeof`{.verbatim} con `fgets`{.verbatim}

En el código de arriba usamos `sizeof`{.verbatim} para dar el tamaño.

Debemos de ser cuidadosos con esto, ya que `sizeof`{.verbatim} nos da la
cantidad de espacio ocupado por una variable.

En el ejemplo, usamos `sizeof`{.verbatim} porque usado en un arreglo nos
da el tamaño del arreglo, si `food`{.verbatim} fuera un puntero normal a
una variable `sizeof`{.verbatim} nos daría el tamaño del puntero.

``` c
printf("Enter favorite food: ");
fgets(food, 5, stdin);
```

Generalmente cuando queremos leer datos estructurados usamos
`scanf`{.verbatim} y si queremos leer un solo string sin estructura es
más conveniente usar `fgets`{.verbatim}.

## En memoria

Si tenemos un código como este:

``` c
#include <stdio.h>

int main() {
    char *cards = "JQK";
    char a_card = cards[2];
    cards[2] = cards[1];
    cards[1] = cards[0];
    cards[0] = cards[2];
    cards[2] = cards[1];
    cards[1] = a_card;
    puts(cards);
    return 0;
}
```

obtendremos un error al correr el código, esto porque `cards`{.verbatim}
es un puntero a un `string`{.verbatim} literal, y estos son inmutables.

Lo que podríamos hacer es crear un arreglo con este `string`{.verbatim}
para que podamos modificarlo.

``` c
char cards[] = "JQK";
```

Para entender que pasa debemos saber como c y la computadora manejan la
memoria.

### La computadora carga el `string`{.verbatim} literal

Cuando la computadora carga el programa en memoria, pone todas las
constantes en un bloque de memoria inmutable, allí es donde esta
\"JQK\".

Esta sección es de solo lectura.

### El programa crea la variable `cards`{.verbatim} en el `stack`{.verbatim}.

El `stack`{.verbatim} (la pila), es la sección de memoria que la
computadora usa para variables locales.

Las variables locales son variables dentro de funciones, la variable
`cards`{.verbatim} estará allí.

### La variable `cards`{.verbatim} le es asignada la dirección de memoria de \"JQK\"

la variable `cards`{.verbatim} contiene la dirección de memoria del
`string`{.verbatim} \"JQK\".

Esta dirección de memoria pertenece a la memoria de solo lectura.

### La computadora trata de cambiar el `string`{.verbatim}

Cuando el programa intenta cambiar el contenido de el
`string`{.verbatim} al cual apunta la variable `cards`{.verbatim} no
puede, es de solo lectura.

## Si vas a cambiar un `string`{.verbatim}, haz una copia

Siempre que queramos cambiar los contenidos de un `string`{.verbatim}
debemos cambiar una copia.

Para crear una copia, creamos un nuevo `string`{.verbatim} como un
arreglo.

``` c
char cards[] = "JQK";
```

### `cards[]`{.verbatim} o `cards*`{.verbatim}

Si vemos una declaración así, que significa realmente?

``` c
char cards[]
```

Depende de donde la veamos.

Si es una declaración de variable normal, Entonces significa que
`cards`{.verbatim} es un arreglo, y debemos asignarle un valor
inmediatamente ya que no le dimos el tamaño:

``` c
int my_function() {
    char cards[] = "JQK";
}
```

Pero si `cards`{.verbatim} es declarado como un argumento de una
función, significa que `cards`{.verbatim} es un puntero.

``` c
void stack_deck(char cards[]) { // <- cards es un puntero
    // .....
}

void stack_deck(char *cards) { // Estas dos funciones son equivalentes.
    // ...
}
```

## Que sucede en memoria

Con el nuevo código, nuestro programa manejara la memoria de manera
diferente.

### La computadora carga el `string`{.verbatim} literal

La computadora carga el programa y guarda \"JQK\" en la memoria de solo
lectura.

### El programa crea un nuevo arreglo en el `stack`{.verbatim}

Declaramos un arreglo, así que nuestro programa creara uno del tamaño
necesario para guardar el `string`{.verbatim} \"JQK\".

### El programa inicializa el arreglo

Además de asignar el espacio la computadora también copia el contenido
del `string`{.verbatim} literal \"JQK\".

## Recordando como funciona la memoria

### `Stack`{.verbatim} (pila)

Esta sección de memoria es usada para guardar variables locales.

Cada vez que llamamos a una función, todas las variables son creadas en
el `stack`{.verbatim}.

Se llama `stack`{.verbatim} porque funciona como una pila, las variables
son añadidas una a una cuando se entras a una función y son retiradas de
este cuando sales.

### `Heap`{.verbatim} (montículo)

La `heap`{.verbatim} es para memoria dinámica, datos que son creados
cuando el programa esta corriendo y se quedan allí por un tiempo.

### Globales

Una variable global son variables que viven afuera de las funciones, y
por lo tanto son visibles para todas ellas.

Estas son creadas cuando el programa corre al principio y pueden ser
editadas.

### Constantes

Las constantes también son creadas cuando el programa corre al
principio, pero están en memoria de solo lectura.

### Código

La mayoría de los sistemas operativos ponen el código en las direcciones
de memoria más bajas.

El segmento de código es de solo lectura. Esta es la parte de la memoria
donde el código ensamblado se carga.

# Teoría de `strings`{.verbatim}

Ya sabemos que los `strings`{.verbatim} en C son solo arreglos de
caracteres, pero para hacer cosas útiles con ellos necesitamos
`string.h`{.verbatim}.

Este es parte de la librería estándar de C y se dedica a la manipulación
de `strings`{.verbatim}.

## Creando un arreglo de arreglos

En una situación donde queremos guardar muchos strings podemos usar un
arreglo de arreglos. Sabiendo que cada `string`{.verbatim} es un array
de caracteres.

``` c
char tracks[][80] = {
    "I left my heart in Harvard Med School",
    "Newark, Newark - a wonderful town",
    "Dancing with dork",
    "From here to maternity",
};
```

En el código anterior, el primer par de corchetes representa el arreglo
de todos los `strings`{.verbatim}, y el segundo es la cantidad de
caracteres que tiene cada `string`{.verbatim}.

De esta manera podemos encontrar un `string`{.verbatim} arbitrario así:

``` c
tracks[4] -> "The girl from Iwo Jima"
```

pero también podemos obtener los caracteres individuales de cada
`string`{.verbatim} de la siguiente manera:

``` c
tracks[4][6] -> 'r'
```

## Encontrando `strings`{.verbatim} que contienen una búsqueda

La librería estándar de C es un conjunto de código que obtienes al
instalar un compilador de C. La librería de código hace cosas útiles
como abrir archivos, hacer matemáticas o manejar memoria.

Esta librería esta dividida en muchas secciones, cada una tiene un
**header** (cabecera).

Esta cabecera lista todas las funciones que viven en una sección
particular de la librería.

Hemos usado la cabecera `stdio.h`{.verbatim} que contiene funciones para
la entrada/salida de datos, como `printf`{.verbatim} y
`scanf`{.verbatim}.

La librería estándar contiene código para procesar y manipular
`strings`{.verbatim}, para acceder a este debemos de agregarla al inicio
de nuestro programa de la siguiente manera:

``` c
#include <stdio.h>
#include <string.h> // <- Agregamos esta linea para usar sus funciones.
```

## Usando la función `strstr()`{.verbatim}

Digamos que queremos buscar la palabra \"fun\" en \"dysfunctional\":

``` c
strstr("dysfunctional", "fun");
```

La función buscará el segundo `string`{.verbatim} en el primero, cuando
lo encuentre retorna la dirección del `string`{.verbatim} en memoria.

Si `strstr`{.verbatim} no puede encontrar el `string`{.verbatim}
retornará el valor 0.

Ya que 0 para C es equivalente a `false`{.verbatim}, podemos usar esta
función para verificar la existencia de un `string`{.verbatim} dentro de
otro.

``` c
char s0[] = "dysfunctional";
char s1[] = "fun";
if (strstr(s0, s1))
    puts("I found the fun in dysfunctional");
```

## Arreglo de arreglos vs arreglo de punteros

Otra opción a un arreglo de arreglos, es un arreglo de punteros, este es
un arreglo de direcciones de memoria, este es útil para crear un una
lista de `strings`{.verbatim} literales.

``` c
char *names_for_dog[] = {"Bowser", "Bonza", "Snodgrass"};
```

# Haz una cosa y hazla bien

Cada sistema operativo incluye herramientas pequeñas.

Pequeñas herramientas escritas en C hacen pequeñas tareas especializadas
a lo largo del sistema operativo.

## Pequeñas herramientas pueden resolver problemas grandes

La mayoría de sistemas operativos vienen con un gran conjunto de
pequeñas herramientas que puedes usar desde la terminal (como linux),
cuando tenemos un problema grande que debemos resolver, podemos partirlo
en una serie de pequeños problemas y escribir una serie de pequeñas
herramientas para resolverlos.

## Errores estándar

La salida estándar es la manera por defecto de salida de datos de un
programa, pero no nos deja manejar errores de manera flexible.

Para esto tenemos el error estándar, este es una segunda salida de datos
creada para el manejo de errores.

## Por defecto el error estándar es mandado a la pantalla.

El sistema operativo crea el error estándar al mismo tiempo y de la
misma manera que la salida estándar.

Esto significa que cuando redireccionamos la salida estándar de nuestro
programa para que podamos redirigir la salida a un archivo, el error
estándar seguirá mandando los errores a la pantalla.

## `fprintf()`{.verbatim} imprime un `stream`{.verbatim} de datos.

Ya sabemos que `printf()`{.verbatim} manda información a la salida
estándar, pero lo que no sabemos es que `printf()`{.verbatim} es una
versión de otra función más general llamada `fprint()`{.verbatim}.

Los dos ejemplos siguientes son equivalentes:

``` c
printf("I like Tultles"); // Cuando llamamos a printf en realidad llamamos a fprintf
fprintf(stdout, "I like Tultles"); // stdout es la salida estándar
```

Esta función nos permite elegir a donde queremos mandar el texto,
podemos usar la `stdout`{.verbatim} (salida estándar) o la
`stderr`{.verbatim} (error estándar).

También existe `fscanf`{.verbatim} que es la función que es llamada
cuando usamos `scanf`{.verbatim}, allí leemos de `stdin`{.verbatim}
(entrada estándar).

Así como podemos redirigir la salida de nuestro programa a un archivo de
texto haciendo `./programa > text.txt`{.verbatim}, podemos redirigir el
error estándar haciendo `./programa 2> text.txt`{.verbatim}
