---
title: Estructuras de datos en python
description: Explicación de algunas estructuras de datos en python
published: true
date: 2022-12-24T19:23:18.666Z
tags: python, data structures, estructuras de datos
editor: markdown
dateCreated: 2022-12-24T19:20:30.407Z
---

# Listas

## Funciones de listas:

`append(item)`  
Añade un elemento al final de la lista.

`insert(index, item)`  
Agrega un elemento en un índice en específico.

`remove(item)`  
Borra un elemento de nuestra lista.

`pop(index)`  
Borra un elemento de nuestra lista en un índice específico.

`count(item)`  
Retorna el número de elementos que coinciden con el elemento dado.

`reverse()`  
Invierte la lista.

`sort()`  
Ordena la lista, por defecto en orden ascendente.

- Para orden descendente, `sort(reverse=True)`

`max(list)`  
Retorna el valor máximo.

`min(list)`  
Retorna el valor mínimo

## List comprehensions

Se usan para crear listas que siguen ciertas reglas

``` python
cubes = [i**3 for i in range(5)]

return cubes
```

<table>
<tbody>
<tr class="odd">
<td>0</td>
<td>1</td>
<td>8</td>
<td>27</td>
<td>64</td>
</tr>
</tbody>
</table>

También podemos usar `if` para agregar condiciones:

``` python
evens = [i**2 for i in range(10) if i**2 % 2 == 0]

return evens
```

<table>
<tbody>
<tr class="odd">
<td>0</td>
<td>4</td>
<td>16</td>
<td>36</td>
<td>64</td>
</tr>
</tbody>
</table>

# Dictionaries, Tuples, Sets

## Diccionarios  
Nos permiten mapear valores arbitrarios como llaves o valores y pueden
ser indexados de la misma manera que listas.

- Puedes utilizar `strings`, `integers`, y `booleans` o otro tipo de
  dato *inmutable* como llaves de un diccionario.
- Para determinar si una llave esta en un diccionario se puede usar `in`
  o `not in`.
- Podemos obtener los pares de un diccionario con la función
  `diccionario.get(key, default)` si la llave no existe, podemos dar un
  valor por defecto opcional
- Para determinar la longitud de una lista, tenemos la función `len()`.
- Podemos agregar elementos al diccionario haciendo
  `dict[clave] = valor`.
  - Se puede eliminar un elemento o un diccionario completo con `del`
    ejemplo `del dict[clave]`
- Para iterar sobre los elementos de el diccionario podemos usar la
  función `values()`.
  - `for value in diccionario.values():`

## Tuplas  
Son parecidas a las listas, pero son inmutables (no cambian).

- Son creadas como las listas, pero en vez de corchetes se usan
  paréntesis.
- La ventaja de las tuplas es que podemos usarlas como llaves en un
  diccionario.
  - `dic = { ("David", 42): "Red", ("Bob", 24): "Green" }`
- Pueden ser creadas sin los paréntesis solo separando los elementos con
  comas. `dic = "one", "dos", "tre"`

### Tuple Unpacking  
Nos permite asignar cada elemento de una colección a una variable.

> Ejemplos:

``` python
numbers = (1, 2, 3)
a, b, c = numbers

return a, b, c
```

- 1
- 2
- 3

``` python
a, b, *c, d = [1, 2, 3, 4, 5, 6, 7, 8, 9]

return a, b, c, d
```

- 1

- 2

- (3 4 5 6 7 8)

- 9

  > la variable con el \* toma todos los valores de la colección que
  > quedan.

## Sets 
Son conjuntos de elementos que son únicos.

  - `num_set = {1, 2, 3, 4, 5}`
  - Es más rápido ver si hay un elemento dentro de un *set* que de una
    lista con el operador `in`.
  - No se puede acceder a ellos con un índice ya que no están indexados.
  - Se puede utilizar la función `add(item)` para agregar y la función
    `remove(item)` para eliminar un elemento.
  - Pueden ser combinados usando operaciones matemáticas.
    - El operador unión `|` combina dos conjuntos formando uno nuevo.
    - El operador intersección `&` obtiene los elementos en común de dos
      conjuntos.
    - El operador de diferencia `-` obtiene los elementos que están el
      primer conjunto pero no en el segundo.
    - El operador de diferencia simétrica `^` obtiene los elementos que
      no se repiten en ambos conjuntos.

## Resumen:

Algunas pautas para usar Estructuras de datos en Python:

- Usa un **diccionario** cuando necesitas una relación lógica entre
  `key:value`.

- Usa **listas** cuando tienes una colección de datos que no necesitan
  acceso aleatorio.

  - Intenta usar listas cuando necesitas una simple, colección de
    elementos que son modificados frecuentemente.

- Usa un **set** (conjunto) si necesitas elementos únicos.

- Usa **tuplas** si tus datos no cambian.

  > Muchas veces, una tupla es usada junto con diccionarios, por ejemplo
  > una tupla puede representar una llave.

# User-Defined Data Structures

Algunas aplicaciones requieren Estructuras de datos más complejas.

## Stack (pila)  
Es una estructura de datos que agrega y elimina elementos de un orden
particular.

- Cada vez que un elemento es añadido, va en la parte superior de la
  pila.

- Cada vez que un elemento es eliminado, se elimina el elemento de la
  parte superior de la pila.

- Este comportamiento es llamado **LIFO** (Last in, First out).

- Terminología:

  - Agregar un elemento a la pila es llamado `push`.
  - Eliminar un elemento de la pila es llamado `pop`.

- Una pila puede implementarse usando una lista.

  > Implementación de una pila con una lista.

  ``` python
  class stack:
      def __init__(self):
          self.items = []

      def isEmpty(self):
          return self.items == []

      def push(self, item):
          self.items.insert(0, item)

      def pop(self):
          return self.items.pop(0)

      def printStack(self):
          print(self.items)
  ```

## Queue (cola)  
Es similar a una pila, pero tiene una manera diferente de agregar o
remover datos.

- Los nuevos elementos son agregados al final de la cola.

- los elementos son eliminados del principio de la cola.

- Este comportamiento es llamado **FIFO** (First in, First out).

- Terminología:

  - Agregar nuevos elementos es llamado `enqueue`.
  - Eliminar elementos es llamado `dequeue`.

- Aplicaciones:

  - Son usadas cuando necesitamos manejar objetos en orden empezando por
    el primero.

- Las colas pueden ser implementadas usando una lista.

  > Implementación de una cola usando una lista.

  ``` python
  class Queue:
      def __init__(self):
          self.items = []

      def isEmpty(self):
          return self.items == []

      def enqueue(self, item):
          self.items.insert(0, item)

      def dequeue(self):
          return self.items.pop() # <-- last element

      def printQueue(self):
          print(self.items)
  ```

## Linked List (listas enlazadas)  
Son una secuencia de nodos en los cuales cada nodo guarda su información
y un enlace al siguiente nodo formando una cadena.

- El primer nodo es llamado `head` y es usado como el inicio de
  cualquier iteración en la lista.

- El último nodo debe de llevar su enlace apuntando a nada para
  determinar el fin de la lista.

- A diferencia de las pilas o las colas, uno puede insertar elementos en
  cualquier lugar de la lista enlazada.

- Aplicaciones:

  - Son útiles cuando la información esta enlazada, por ejemplo en un
    undo/redo.

- Las listas enlazadas pueden usarse para implementar otras estructuras
  de datos como pilas, colas y grafos.

  > Implementación de una lista enlazada.

  ``` python
  class Node:
      def __init__(self, data, next):
          self.data = data
          self.next = next

  class LinkedList:
      def __init__(self):
          self.head = None

      def addAtFront(self, data):
          self.head = Node(data, self.head)

      def addAtEnd(self, data):
          if not self.head:
              self.head = Node(data, None)
              return
          curr = self.head
          while curr.next:
              curr = curr.next
          curr.next = Node(data, None)

      def getLastNode(self):
          n = self.head
          while(n.next != None):
              n = n.next
          return n.data

      def isEmpty(self):
          return self.head == None

      def printList(self):
          n = self.head
          while n != None:
              print(n.data, end = " => ")
              n = n.next

  s = LinkedList()
  s.addAtFront(5)
  s.addAtEnd(8)
  s.addAtFront(9)

  s.printList()
  print()
  print(s.getLastNode())
  ```

  ``` example
  9 => 5 => 8 =>
  8
  ```

## Graph (grafos)  
Son un conjunto de nodos conectados donde cada nodo es llamado vértice
(vertex) y las conexiones entre dos son llamados bordes (edge).

- Un grafo puede representarse usando una matriz cuadrada, esta es
  llamada matriz adyacente (Adjacency Matriz).
  - Cada elemento indica los bordes, 0 indica que no hay borde, y 1
    indica un borde.

  - Las columnas y filas representan los vértices.

    ``` example
    0 1 1
    1 0 0
    1 0 0
    ```

    > La matriz de ejemplo representa un grafo de 3 vértices (por esa
    > razón es 3x3)

    - Los 1s representan los los bordes, hay dos bordes, el primero esta
      conectado el segundo y el tercero.

    - Hay 4 1s en la matriz, debido a que el nodo A esta conectado con
      B, entonces B esta conectado con A.

      > Implementación de un grafo usando una matriz adyacente.

      ``` python
      class Graph():
          def __init__(self, size):
              self.adj = [ [0] * size for i in range(size)]
              self.size = size

          def addEdge(self, orig, dest):
              if orig > self.size or dest > self.size or orig < 0 or dest < 0:
                  print("Elemento invalido")
              else:
                  self.adj[orig-1][dest-1] = 1
                  self.adj[dest-1][orig-1] = 1

          def removeEdge(self, orig, dest):
              if orig > self.size or dest > self.size or orig < 0 or dest < 0:
                  print("Elemento invalido")
              else:
                  self.adj[orig-1][dest-1] = 0
                  self.adj[dest-1][orig-1] = 0

          def display(self):
              for row in self.adj:
                  for val in row:
                      print('{:4}'.format(val),end="")
                  print()

      G = Graph(4)
      G.addEdge(1, 3)
      G.addEdge(3, 4)
      G.addEdge(2, 4)
      G.display()
      ```

      ``` example
         0   0   1   0
         0   0   0   1
         1   0   0   1
         0   1   1   0
      ```

  - Guardamos la matriz en un arreglo de dos dimensiones.

  - El método `__init__` crea una matriz `adj` con el tamaño solicitado
    e inicializa los valores con 0.

  - El método `addEdge()` crea un borde poniendo sus respectivos valores
    a 1.

  - El método `removeEdge()` pone los valores en 0.

    > [Implementación](https://github.com/Fwxzxh/IA/blob/main/Sem_5/rutas.py)
    > de un grafo con listas de adyacentes

