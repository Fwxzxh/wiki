---
title: Fundamentos matemáticos para data science
description: 
published: true
date: 2022-12-25T06:44:34.244Z
tags: data science, mátematicas
editor: markdown
dateCreated: 2022-12-25T06:36:51.734Z
---

# Aritmética

## Operaciones básicas de matemáticas

- Qué es la aritmética?
  - La rama de las matemáticas que estudia los números y las operaciones
    que se hacen con ellos.
  - Trabaja solo con números.
- Operaciones básicas:
  - Suma (+).
  - Resta (-).
  - Multiplicación (\*).
    - Es una suma repetida.
    - Es conmutativa:
      - El orden de los factores no altera el producto.
  - División (/).
    - Es una resta repetida.

## Potenciación y sus propiedades

> $m^n$

- $m$ es la base y $n$ es el exponente.
- Es una multiplicación repetida.
- Propiedades:
  - En la multiplicación de dos potencias con la misma base los
    exponentes se suman.
  - En la división de dos potencias con la misma base los exponentes se
    restan
  - Una potencia elevada a la cero da 1.
  - Una potencia cuya base es 0 siempre va a dar 0, no importa el
    exponente.

## Radicación y sus propiedades

$4^2 = 16$

$\sqrt[2]{16} = 4$

- Es la operación inversa a la potencia.
- Encuentra la base de la potencia, es decir de donde vino el número.
- También podríamos pensar en por ejemplo $\sqrt[2]{16} = 2$ como:
  - Qué número debemos de multiplicar 4 veces para obtener 16?
- A esta operación se le llama raíz.

## Orden de operadores

1.  Paréntesis / Corchetes.
2.  Exponentes / Raíces.
3.  Multiplicación/ División.
4.  Adición / Sustracción

## Factorización

- Es el proceso de encontrar factores.
  - Son elementos que podemos multiplicar para sacar el resultado.
  - Todo esto para dividir una expresión en una más pequeña.
- Métodos:
  - Test de divisibilidad.
    - 1 Siempre es un factor de cualquier número.
    - **No existe un factor mayor a la mitad del número**.
      - Por lo tanto podemos empezar a buscar sus factores desde la
        mitad del número.
      - Podemos empezar a sacarlos dividiendo el número entre 1,2,3,4…
        - Si el resultado es entero, entonces es un factor.
  - Método de primos:
    - Los números primos son divisibles por ellos mismos y por 1.
      - Son la base para componer todos demás números usándolos de
        factores.
      - Son primos de *primero*.
    - Podemos usarlos para sacar los factores de un número.
      - dividiendo entre números primos.

# Principios del álgebra

## Principios del álgebra

- la $x$ simboliza una variable.
  - Es desconocida, puede cambiar y es variable.
- Una ecuación es una igualdad entre dos expresiones y con una o más
  variables.
- Un sistema de ecuaciones es un grupo de ecuaciones relacionadas las
  cuales comparten sus variables.
  - El resultado de sus variables debe de ser el mismo.

## Propiedades de las ecuaciones

- Reflexiva/idéntica:
  - Toda cantidad o expresión matemática es igual a si misma.
  - *b* = *b*, *a* = *a*
- Simétrica:
  - Establece que sin importar el orden de los miembros de la igualdad
    prevalece.
  - *a* + *b* = *c*, *c* = *a* + *b*
- Transitiva:
  - Si los miembros que conforman una igualdad tienen un elemento en
    común, se dice que este elemento es igual a cualquiera de los 2
    miembros de la igualdad.
  - *a* = *b*, *b* = *a*, *a* = *c*, *a* = *b*, *a* = *c*, *b* = *c*
- Uniforme:
  - Si se aumenta/disminuye la misma cantidad de los miembros de una
    igualdad, esta prevalece.
  - 4 + 3 = 7, 4 + 3 + 2 = 7 + 2
- Cancelativa:
  - Al suprimir 2 elementos/cantidades iguales en ambos miembros (lados)
    la igualdad se mantiene:

## Orden de despeje

- Se usa el orden inverso a el orden de operadores:
  1.  Adición y sustracción.
  2.  Multiplicación y división.
  3.  Exponentes y Raíces.
  4.  Paréntesis y corchetes.
- **Esto se usa como orden de despeje**

## Despejando exponentes y raíces en álgebra

- La operación inversa de los exponentes son las raíces.
- Podemos expresar raíces como exponentes fraccionarios.
  - $$\sqrt[3]{x} = x^{1/3}$$ 
  - $$\sqrt{x} = x^{}{1/2}$$
  - $$\sqrt[5]{x} = x^{}{1/5}$$
- Pero por ejemplo también la raíz es la operación inversa de 
  $x^2$ y $\sqrt[3]{x}$ es la inversa de $x^3$.
  - Por lo tanto se eliminan los exponentes o las raíces directamente
    sin hacer operaciones con fracciones.

# Polinomios

## Polinomios

- Literalmente "Varios términos".
- Un termino:
  - Tiene una parte que es un número y una parte variable,
    - EJ: $4x$
    - El número es el coeficiente y la x la variable.
- Entre más términos tenga le podemos llamar, Monomio, Binomio o
  trinomio.
- Al termino con variable 0 le llamamos constante.

## Simplificando polinomios

- Necesitamos agrupar términos semejantes.
  - Son aquellos términos cuya variable es igual podemos sumar o restar
    estos términos.

## La propiedad distributiva de la multiplicación

- Básicamente:
  - $3 \ (4+6)$ podemos rae-escribirlo como: $(3\4) + (3\6)$.
  - Podemos distribuir la multiplicación.

# Funciones

## Qué es una función?

- Podemos pensar en una función como una caja.
  - Tenemos valores de entrada y tenemos valores de salida.
  - Lo que hay dentro de esa caja son reglas, una operación, que
    transforma los valores de entrada en los de salida.
  - Cada valor de entrada corresponde a **solo uno** de los valores de
    salida.
  - Tiene dominio (valores de entrada) y un rango (valores de salida).
- Función(entrada) = salida o expresado de otra manera: $f(x) = y$.

## Tabulación de funciones

- Hay variables dependientes y variables independientes.
- En este caso la variable dependiente son los valores de los cuales
  depende la función.
  - Los valores independientes son los que se le dan a la función.
  - En $f(x) = y$ $x$ seria la variable independiente y $y$ la
    variable dependiente.
- Las funciones las podemos tabular en una tabla.

Podríamos tabular la función: *y* = 2*x*

<table>
<thead>
<tr class="header">
<th>x</th>
<th>y</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>4</td>
<td>8</td>
</tr>
<tr class="even">
<td>2</td>
<td>4</td>
</tr>
<tr class="odd">
<td>0</td>
<td>0</td>
</tr>
<tr class="even">
<td>-2</td>
<td>-4</td>
</tr>
</tbody>
</table>

> La variable *y* depende del valor de *x* por lo tanto es la variable
> dependiente.

## El plano cartesiano

- Las funciones las podemos gráficar.
- Es una recta numérica de dos dimensiones para gráficar dos variables
  *x* y *y*.
- En esta podemos visualizar los resultados de una función, las
  variables independientes y dependientes.
- También conocido como el eje de las abscisas(x) y ordenadas(y).
- Nos permite visualizar los valores negativos y positivos.
- Hay 4 cuadrantes:
  - Cuadrante 1: *x* y *y* son positivos.
  - Cuadrante 2: *x* es negativos y *y* es positivo.
  - Cuadrante 3: *x* y *y* son negativos.
  - Cuadrante 4: *x* es positivo y *y* es negativo.

# Gráficas

## Test linea vertical

- Podemos gráficar una función y podemos saber si es una función desde
  la gráfica.
- Si trazamos una linea vertical y la gráfica de esta la corta en dos
  partes o más en cualquier punto de la gráfica.
  - Si esto pasa no es una función.
    - Esto porque en una función para cada *x* hay **solo una** *y*, y
      que la linea corte en dos o más lugares indica que existe más de
      una y para cada x.

## Funciones lineales

- Tienen la forma $y = m^x + b$.
  - Donde *m* es llamada la pendiente.
  - No importa que tan grande sea la *m*, no llegara a ser vertical.
  - Pero si *m* = 0 si podemos tocar el eje horizontal, teniendo una
    linea horizontal.
  - *b* es una constante y es el punto de corte en el eje y.

## Cómo identificar funciones lineales a partir de una ecuación

- Si hay un exponente elevado a una potencia cuadrada, no es una función
  lineal.
