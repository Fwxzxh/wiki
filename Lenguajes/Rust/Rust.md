---
title: Rust
description: 
published: true
date: 2023-01-20T05:15:32.529Z
tags: lenguajes, rust
editor: markdown
dateCreated: 2023-01-17T05:34:28.256Z
---

# The Rust Programming Language
## Introducción
## Conceptos comunes
## Entendiendo Ownership
## Usando Structs
## Enums y Pattern Matching
## Manejando Proyectos con Packages, Crates y Módulos
## Colecciones comunes
Rust contiene ciertas estructuras de datos llamadas colecciones.

Algunas son:
- Vectores: Te permiten guardar un número variable de valores uno detrás del otro.
- `Strings`: Es una colección de caracteres.
- `hash map`: Nos permite asociar un valor con una llave particular.

### Vectores
Para crear un nuevo vector usamos:

```rust
let v: Vec<i32> = Vec:new();
```

> Se añade el tipo del vector ya que lo estamos inicializando sin valores.

Los vectores son genéricos `Vec<T>` asi que pueden tener cualquier tipo de valor, pero solo uno.

Si queremos inicializar un vector con valores iniciales podemos usar la macro:

```rust
let v = vec![1, 2, 3];
```

### Añadiendo elementos

También podemos añadir elementos a los vectores de la siguiente forma.

```rust
let mut v = Vec::new();

v.push(5);
v.push(6);
v.push(7);
v.push(8);
```

> para hacer esto necesitamos hacer v mutable.

### Leyendo elementos
Hay dos maneras de leer elementos de un vector:

```rust
let v = vec![1, 2, 3, 4, 5];

// 1. Accediendo con el indice (nos da solo la referencia al valor)
let third: &i32 = $v[2];
println!("The third element is {third}");

// 2. Obteniéndolo con la función get() (más seguro).
// Get nos retorna un Option
let third: Option<&i32> = v.get(2);
match third {
    Some(third) => println!("The third element is {third}"),
    None => println!("There is no third element"),
} 
```
Al intentar acceder a un elemento que no existe con el método 1 nuestro programa tirará un `panic`,
haciendo que nuestro programa crashee.

Con el segundo método, podremos manejar el debido caso que el valor no exista, usando estos dos 
métodos podemos controlar el comportamiento de nuestro programa en ciertas situaciones.

También tenemos que tener en cuenta las reglas de `ownership` al trabajar con vectores.

```rust
let mut v = vec![1, 2, 3, 4, 5]; // Los vectores son espacios *contiguos* de memoria.

let first = &v[0]; // Obtenemos una referencia al primer elemento.

v.push(6); // Error!!! 
// Si al agregar un elemento extra el espacio designado par v no alcanza,
// rust tiene que moverlo a otro lugar, invalidando la referencia en first.

println!("The first element is: {first}");
```
### Iterando sobre un vector

```rust
// Iterando y obteniendo referencias inmutables en cada elemento.
let v = vec![100, 32, 33];
for i in %v {
    println!("{i}");
}
```

```rust
// Iterando y modificando referencias mutables en cada elemento.
let mut v = vec![100, 32, 33];
for i in %mut v {
    *i += 50; // Derreferenciando i para sumarle 50.
    // Derreferenciar: tenemos una referencia mutable a v (una dirección de memoria).
    // De esa dirección obtenemos el valor al que apunta para modificarlo.
}
```

> La referencias que usa el for loop y el `borrow checker` mantienen nuestra memoria segura.

### Usando Enums para guardar multiples tipos
Los vectores solo pueden contener valores de un solo tipo, 
si necesitamos guardar elementos de diferente tipo podemos usar un Enum

```rust
enum SpreadsheetCell {
    Int(i32)
    Float(f64)
    Text(String)
}

let row = vec![
    SpreadsheetCell::Int(3),
    SpreadsheetCell::Text(String::from("blue")),
    SpreadsheetCell::Float(10.32),
];
```

> Para el vector todos los elementos son del tipo SpreadsheetCell, entonces no hay problema.

Rust debe de saber a tiempo de compilación el tipo de los valores que va a tener,
esto para saber a tiempo de compilación cuanto espacio en la heap ocupan estos elementos.

> Usar un `enum` con un `match` significa que rust podrá manejar todos los casos posibles a tiempo de compilación.


