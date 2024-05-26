---
title: The Rust Programming Languaje
description:
published: true
date: 2023-02-11T19:44:06.354Z
tags: libros, lenguajes, rust
editor: markdown
dateCreated: 2023-01-17T05:34:28.256Z
---

# Links de interés
- [Rust CheatSheet](https://cheats.rs/)

# Introducción
# Conceptos comunes
# Entendiendo Ownership
# Usando Structs
# Enums y Pattern Matching
# Manejando Proyectos con Packages, Crates y Módulos
# Colecciones comunes
## Guardando listas de valores con vectores
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
for i in &v {
    println!("{i}");
}
```

```rust
// Iterando y modificando referencias mutables en cada elemento.
let mut v = vec![100, 32, 33];
for i in &mut v {
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

### Liberando un vector
Como cualquier `struct`, un vector es liberado de memoria cuando se sale de su scope.

```rust
{
    let v = vec![1, 3, 4, 6];
    // Hacemos cosas con v
} // <- es liberado de memoria junto con todos sus contenidos.
```

## Guardando texto UTF-8 con Strings
En rust los `strings` son diferentes por tres cosas:
1. La propension de rust de exponer posibles errores.
2. Los strings siendo una estructura de datos más compleja de lo que se piensa.
3. UTF-8.

> En rust los strings son tratados como colecciones.

### Qué es un string?
En rust los strings son definidos por el `slice` `str` dado por el `core`de rust el cual vemos en la forma de `&str`
las cuales son referencias a datos encodeados en UTF-8.

El tipo `String` es un tipo (de la librería estándar) que puede crecer, mutar y tiene ownership,
cuando nos referimos a strings podemos referirnos al tipo `String` o al slice `&str`.

### Creando Strings
Muchas de las operaciones que tiene `Vec<T>` también las tiene `String`, esto porque
este ultimo esta implementado como un `wrapper` de `Vec`.

```rust
// Creando un nuevo string al cual podemos meterle datos.
let mut s = String::new();

let data = "initial contents";

let s = data.to_string();

// Los métodos de string también funcionan en string literales.
let s = "initial contents".to_string();
```

También podemos crear un string desde una cadena para ahorrarnos unos pasos.

```rust
let s = String::from("initial contents");
```

> Como los strings son por defecto UTF-8 pueden contener muchos caracteres dentro.

### Actualizando un String
Un `String` puede crecer y decrecer como los `Vec<T>`, También podemos usar la macro
`format!` junto con el operador `+` para concatenar.

```rust
let mut s = String::from("foo");
s.push_str("bar"); // push_str toma un slice como parámetro (no queremos ownership del valor)
// s == foobar
```

```rust
let mut s1 = String::from("foo")
let s2 = "bar"
s1.push_str(s2); // push_str, no toma ownership!
println!("s2 is {s2}")  // bar
```

```rust
let mut s = String::from("lo");
s.push('l');
// s = lol
```

### Concatenando con + y `format!`
Una manera de concatenar strings es con la macro `format!`

```rust
let s1 = String::from("hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // s1 ya no es usable ya que se ha movido aquí
```

Tomamos ownership de s1 ya que la función + tiene como firma:

```rust
fn add(self, s:&str) -> String {
    ...
```

Entonces tomamos ownership de `self` pero n de `s2` ya que solo necesitamos la referencia a
un slice `str`.

La función `add` también hace uso de tipos genéricos, y otras cosas para matchear los tipos de los argumentos que se le dan.

> También hace cosas por debajo para usar `s2` que es en realidad `&String`, a un `&str`

Lo que realmente esta pasando aquí es que rust, toma ownership de s1, sigue la referencia a s2
y se le agrega una copia a s1, retornando ownersip en s3, invalidando s1.

Para concatenar diferentes strings es mejor usar la macro `format!`

```rust
let s1 = String::from("tic");
let s2 = String::from("tac");
let s3 = String::from("toe");

let s = format!("{s1}-{s2}-{s3}"); // No toma ownership de los valores
// s = tic-tac-toe :D
```

### Indexando Strings
En rust no podemos indexar strings con un indice esto es debido a la representación interna dentro de rust de los strings.

Si bien los strings derivan de un `Vec<u8>`, están encodeados con utf-8 por lo que:

```rust
fn main() {
    let hello = String::from("السلام عليكم"); // big truble!
    let hello = String::from("Dobrý den");
    let hello = String::from("Hello");
    let hello = String::from("שָׁלוֹם"); // wtf?
    let hello = String::from("नमस्ते");
    let hello = String::from("こんにちは");
    let hello = String::from("안녕하세요");
    let hello = String::from("你好");
    let hello = String::from("Olá");
    let hello = String::from("Здравствуйте"); // len 24 (no 12)
    let hello = String::from("Hola"); // len 4 bytes long
}
```

Las longitudes de estos diferentes strings varia ya que dependiendo de los caracteres,
estos podrían no tener un largo exacto de 1 letra por byte.

Entonces acceder con un indice en un string podría no obtener un solo carácter, si no una fracción de este.

### Bytes, Valores Escalares y Clusters de Grafemas
Hay tres maneras relevantes para entender los strings en rust.

Si tomamos el string `नमस्ते` este esta guardado como un vector de `u8` como este:

`[224, 164, 168, 224, 164, 174, 224, 164, 184, 224, 165, 141, 224, 164, 164,
224, 165, 135]`

Lo cual son equivalentes a 18 bytes, si los vemos como valores Unicode escalares tendríamos:

`['न', 'म', 'स', '्', 'त', 'े']`

Hay 6 valores tipo `char` aquí, pero el cuarto y el sexto no son letras, son diacriticos,
entonces no tienen significado por si solos.

Ahora podemos ver el mismo string como clusters de grafemas:

`["न", "म", "स्", "ते"]`

Rust provee diferentes maneras de acceder a los valores de un string de acuerdo a nuestras necesidades.

Otra razón es que indexar un string tiene O(1) de complejidad en el tiempo, pero es imposible obtener esa velocidad en UTF-8 ya que tendríamos que recorrer todo el string antes para saber que cluster es el que queremos obtener.

### Slices de strings

Indexar es mala idea porque el resultado puede ser un byte, un carácter, o un cluster de grafema.

En lugar de indexar, podemos tomar un slice de un string

```rust
let hello = "Здравствуйте";
let s = &hello[0..4];
```
Esto nos dará los primeros 4 bytes del string, cada uno de estos caracteres vale 2bytes, entonces obtendríamos dos letras.

> Si accediéramos un slice de `[0..1]` tendríamos un crash en tiempo de ejecución, Cuidado!

### Iterando sobre strings
Para iterar es necesario ser explicito sobre lo que queremos obtener en la iteración,
ya sean caracteres, bytes u otra cosa.

```rust
for c in "Зд".chars() {
    println!("{c}");
}
```

O en bytes

```rust
for b in "Зд".bytes() {
    println!("{b}");
}
```

> Recuerda que Valores Unicode validos pueden ser de más de 1 byte.

## Hash Maps
El tipo `HashMap<K, V>` guarda un mapeo de llaves con valores, esto usando una función de hasheo que determina los lugar donde guarda estos valores en memoria.

### Creando un Hash Map

```rust
use std::collections::HashMap

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
```

> Al igual que los vectores, hash maps guardan sus datos en la heap.

### Accediendo a valores en un Hash Map

```rust
fn main() {
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    let team_name = String::from("Blue");
    let score = scores.get(&team_name).copied().unwrap_or(0);
}
```

En el ejemplo anterior el método `get()` nos retorna un `Option<&V>`,
Si no hay valores obtendremos un `None`, Manejamos el `Option` con `copied()`,
Esto para obtener un `Option<i32>` en lugar de un `Option<&i32>`,
con `unwrap_or()` retornamos un 0 si nuestro `Option` es None.


### Hash Maps y ownership

> Para tipos con el trait `Copy` estos serán copiados al hash map, para los que no se moverá el ownership al hash map.

```rust
use std::collections::HashMap;

let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);

// field_name & field_value son inválidos a partir de este punto, ahora map tiene el ownership.
```

### Actualizando un Hash Map

- Cada key, puede tener solo un valor asociado con esta.
- Podemos manejar el caso en el que queramos elegir si remplazar esta key o no.

> Si insertamos un valor y una key y luego otro con la misma key, el valor será reemplazado.


```rust
let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

// Como,  checa si existe esta entrada, y si no inserta *tal*
scores.entry(String::from("Yellow")).or_insert(50);
scores.entry(String::from("Blue")).or_insert(50);
```

El método `or_insert` en `entry` retorna una referencia mutable al valor de la entry, si esta existe y si no, inserta el parámetro como el nuevo valor para esta key.

### Actualiza un valor de un Hash Map basado en otro valor

Un uso común de los hash map es buscar un valor, y actualizarlo.

```rust
let text = "hello world";

let mut map = HashMap::new();

for world in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}
```

> Por defecto HashMap usa el algoritmo llamado SipHash para hash tables, pero este puede ser cambiado.

## Error Handling

Rust agrupa los errores en dos categorías:
- Errores recuperables.
    - Rust no tiene excepciones.
    - Para estos, rust tiene el tipo `Result<T, E>`
- Errores no recuperables.
    - Para estos rust tiene la macro `panic!` que detiene la ejecución del programa

### Errores no recuperables con panic!

Por defecto panic:
- Imprime un mensaje de error.
- unwind y limpia el stack.
- Termina la ejecución.

podemos modificar si queremos hacer unwinding del stack o no cuando llamamos a panic modificando el `Cargo.toml`.

```toml
[profile.release]
panic = 'abort'
```


```rust
fn main() {
    // panic example, duh!
    panic!("crash and burn");
}
```

### Errores recuperables con Result

Algunos errores no son tan serios como para que nuestro programa se detenga.

En rust existe el enum Result:

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

> No tenemos que definir este tipo ya que se importa automáticamente en el preludio del lenguaje

Donde:
- T representa el tipo del dato que retornaremos si la operación fue exitosa.
- E el tipo del error que será retornado en caso de que la operación no sea exitosa.

```rust
fn main() {
    let greeting = File::open("Hello.txt");

    let greeting_file = match greeting {
        OK(file) => file,
        Err(error) => panic!("Problem opening the file: {:?})", error),
    };
}
```

### Matcheando diferentes errores

Algunas veces queremos tomar diferentes acciones por diferentes tipos de fallos.

```rust
fn main() {
    let greeting = File::open("Hello.txt");

    let greeting_file = match greeting {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating the file {:?}", e),
            },
            other_error => {
                panic!("Problem opening the file: {:?}", other_error);
            }
        },
    };
}
```

En el ejemplo anterior:
- `File::open` retorna en la variante `Err` un `io::Error`.
    - Este es un struct que nos da la librería estándar.
        - Este struct tiene un método `kind` que podemos llamar para obtener un enum `io::ErrorKind`.
            - En este ejemplo nos encargamos de la variante del enum `ErrorKind::NotFound`.

### Atajos para el manejo de errores.

Usar un match puede ser un poco verbose, el tipo `Result<T, E>` tiene algunos métodos que pueden ser útiles.


```rust
fn main() {
    let greeting = File::open("Hello.txt").unwrap();
}
```

> unwrap() llamara a panic! si hay un error.

```rust
fn main() {
    let greeting = File::open("Hello.txt")
        .expect("hello.txt should be included in this project");
}
```

> expect() le dará el mensaje que le pases como argumento a panic!. (generalmente es mejor practica que unwrap())

### Propagando errores

A veces es mejor propagar el error al siguiente nivel en lugar de manejarlo en la misma función.

```rust
fn read_username_from_file() -> Result<String, io::Error> {
    let username_file_result = Fille::open("hello.txt");

    let mut username_file = match username_file_result {
        Ok(file) => file,
        Err(e) => return Err(e),
    }

    let mut username = String::new();

    match username_file.read_to_string(&mut username) {
        Ok(_) => Ok(username),
        Err(e) => Err(e),
    }
}
```

El patron de propagar errores es tan común en rust que existe el operador `?`.

```rust
fn read_username_from_file() -> Result<String, io::Error> {
    let mut username_file = File::open("hello.txt")?;
    let mut username = String::new();
    username_file.read_to_string(&mut username)?;
    Ok(username)
}
```

El `?` Esta hecho para funcionar de la misma manera que el match del primer ejemplo.

Incluso podemos chainear las llamadas anteriores.

```rust
fn read_username_from_file() -> Result<String, io::Error> {
    let mut username = String::new();
    File::open("hello.txt")?.read_to_string(&mut username)?;
    Ok(username)
}
```

> El operador `?` Solo puede ser usado en operaciones cuyo tipo de retorno coincida con el de la función padre.

## Tipos genéricos, Traits y lifetimes

Los tipos genéricos nos permiten remplazar tipos específicos con un placeholder que podría representar
cualquier tipo, para evitar duplicación.


```rust
fn largest<T>(list: &[T]) -> &T {}
```

en la sintaxis de una función genérica, decimos que la función es genérica con el tipo `T`, y recibe un slice de este tipo `T` y retorna una referencia a este tipo `T`, `T` Solo es el nombre que le damos al tipo que vamos a recibir como parámetro en la función.

También podemos definir structs genéricos

```rust
struct Point<T> {
    x: T,
    y: T
}
```
