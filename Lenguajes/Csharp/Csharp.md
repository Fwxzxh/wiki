---
title: Guia Csharp
description: 
published: true
date: 2022-12-26T00:42:43.592Z
tags: c#, oop
editor: markdown
dateCreated: 2022-12-26T00:14:27.129Z
---

# Conceptos Básicos

## C#

- Un elegante lenguaje orientado objetos.
- Corre sobre el .NET Framework.

## .NET Framework

- Consiste en:
  - `CLR (Common Language Runtime)`
    - Es la fundación de .NET.
    - Maneja muchas cosas.
      - Código en tiempo de ejecución.
      - Manejo de memoria.
      - Etc.
  - `.NET Framework Class Library`.
    - Colección de clases, interfaces y Tipos de datos que te permiten
      hacer Un rango de tareas de programación comunes.
    - C# La Usa extensivamente.

## Variables

- Reservan información en memoria.
- Deben tener nombres descriptivos.
- También son llamadas identificadores.

## Tipos de variables

- Define el tipo de valor que va a ser guardado en la variable asi como
  la memoria que se necesita.

``` csharp
int myAge;
```

> Una linea de código que completa una acción es llamada declaración y
> terminan con punto y coma.

- Podemos asignarle un valor a la variable cuando la declaras.

``` csharp
int myAge = 18;
```

## Tipos de datos

- Hay algunos tipos de datos por defecto en C#.
    - `int`  
        - Entero.
    - `float`  
        - Números de coma flotante (Con decimales pues.).
    - `double`  
        - Una versión con más precisión (más dígitos) de float.
    - `char`  
        - Un carácter.
    - `bool`  
        - `true` o `false`.
    - `string`  
        - Cadenas de caracteres.

> valores `char` son definidos con comillas simples y `string` con
> comillas dobles.

## Mi primer programa en C#

- Cada aplicación de consola en C# debe tener una función llamada `Main`
  - Esta función es el punto de entrada para cada aplicación.

## Mostrando texto

- La mayoría de las aplicaciones necesitan algún tipo de `input` y nos
  tan algún tipo de `output`.
- Para mostrar texto en pantalla usamos `Console.write()` o
  `Console.WriteLine()`.
  - La diferencia es que con el segundo al final del texto da un salto
    de linea.

``` csharp
Console.WriteLine("Hola Mundo!");
```

- Para imprimir una cadena con un formato especifico podemos hacer.

``` csharp
int x = 10;
double y = 20;

Console.WriteLine("x = {0}; y = {1}", x, y);
```

> `{0}` sera remplazado por el valor de `x` y `{1}` por el valor de `y`.

## Leyendo texto

- Podemos leer texto de la terminal con `Console.ReadLine()` y asignarlo
  a una variable.

``` csharp
yourInput = Console.ReadLine();
```

> Esto siempre retorna un `string`.

- Podemos Convertir este `string` en otro tipo de dato fácilmente con el
  método `Convert.ToXXX`.
  - EJ. `Convert.ToDouble` o `Convert.ToBoolean`.
    - También podemos convertir a enteros de un tamaño en especifico
      `Convert.ToInt16`, `Convert.ToInt32`, etc.
      - El tipo de dato por defecto en enteros es `Int32`.

## Comentarios

- Empiezan con `//`.
- Comentarios multilinea son `/* texto */`.

## La palabra `var`

- C# provee una forma de declarar variables y hacer que el compilador
  determine el tipo de dato de esta.

``` csharp
var num = 15;
```

- Estas variables son llamadas de **Tipo implícito**.
- Estas variables **deben** ser inicializadas con un valor.

``` csharp
// Esto dará un error!
var num;
num = 15;
```

> Es buena práctica declarar tus variables con su tipo de dato y usar
> `var` solo para casos especiales.

## Constantes

- Se definen constantes con la palabra `const`.

``` csharp
//Ejemplo
const double PI = 3.14;
```

- Las constantes siempre deben se ser inicializadas asignándoles un
  valor.
- Son variables que no pueden ser cambiadas.

## Operadores Aritméticos

- Son los mismos de toda la vida `+, -, *, /, %`.
- Tienen una jerarquía de evaluación normal y esta puede afectarse con
  los paréntesis.

## Operadores de asignación e incremento

    x += 2; // equivalente a x = x + 2;
    x %= 2; // equivalente a x = x % 2;
    // y de la misma manera con los operadores anteriores.

### Operadores de incremento

- Podemos incrementar un valor a una variable cada que nuestro programa
  pase por allí.
  - Es especialmente útil en ciclos.

``` csharp
x++; // equivalente a x = x + 1;
```

### Formas de prefijo y postfijo

- El operador de incremento tiene dos formas.

``` csharp
++x; // prefijo
x++; // postfijo
```

- Prefijo: Incrementa el valor y después procede con la expresión.
- Postfijo: Evalúa la expresión y después incrementa el valor.

``` csharp
int x = 3;
int y = ++x;
// x es 4, y es 4
```

``` csharp
int x = 3;
int y = x++;
// x es 4, y es 3
```

> Esto también funciona con el operador de decremento `-`, siendo x– y
> –x.

# Condicionales y loops

## `if else`

- Ejecuta un bloque de código si una condición se cumple.

``` csharp
if (x > y)
    {
        Console.WriteLine("x es más grande que y");
    }
```

### Operadores Relacionales

- Se usan para evaluar condiciones.
- Son los mismos de siempre; !=, \>=, \<=, ==.

### Operador `else`

- Se ejecuta cuando no se cumple la condición dentro del `if`.

``` csharp
if (x > y)
    {
        Console.WriteLine("x es más grande que y");
    }
else
    {
        Console.WriteLine("y es más grande que x");
    }
```

- Podemos combinarlos y agruparlos como queramos

``` csharp
if ( x )
    {
        // algo
    }
else if ( y )
    {
        // otra cosa
    }
else if ( z )
    {
        //aaaaaa
    }
else
    {
        //final
    }
```

## operador `switch`

- Provee una manera más elegante de comparar una variable con ciertos
  casos predefinidos.
- Cada caso es llamado `case`.

``` csharp
int num = 3;
switch (num)
    {
        case 1:
            Console.WriteLine("one");
            break;
        case 2:
            Console.WriteLine("two");
            break;
        case 3:
            Console.WriteLine("Three");
            break;
        default:
            Console.WriteLine("No es uno, dos o tres");
            break;
    }
```

> Un `switch` puede incluir n número de casos, pero cada caso debe de
> ser único.

> El bloque `default` solo se ejecuta si no se cumple ninguno de los
> `case`.

### La palabra `break`

- Se usa para romper el ciclo de ejecución del `switch`
  - Sin el, el `switch` seguirá comparando con otros case a pesar de
    entrar en uno.
  - También sirve para romper ciclos `for` o `while`.
  - En C# `break` es obligatorio al final de cada `case`.

## El ciclo `while`

- Ejecuta un bloque de código siempre y cuando una condición se cumpla.

``` csharp
int num = 1;
while (num < 6)
    {
        Console.WriteLine(num);
        num++;
    }
```

> El código anterior imprime los números del 1 al 5.

## El ciclo `for`

- Ejecuta un bloque de código un número especifico de veces.

``` csharp
for (init; condition; increment)
    {
        //code
    }
```

**Ejemplo:**

``` csharp
for (int x = 10; x < 15; x++)
    {
        Console.WriteLine("Value of x: {0}", x);
    }
```

- En el bloque del incremento podemos hacer otras cosas como incrementar
  de 3 con `x+=3` o decrementar de la misma manera el contador.
- También podemos quitar el bloque `init` e `increment` del bloque, pero
  los puntos y comas son obligatorios.

``` csharp
int x = 10;
for ( ; x > 10 ; )
    {
        Console.WriteLine(x);
        x -= 3;
    }
```

> `for (;;){}` es un ciclo for infinito.

## `do-while`

- Es similar a un ciclo `while`, solo que en este el bloque de código es
  ejecutado al menos una vez.

``` csharp
int a = 0;
do {
    Console.WriteLine(a);
    a++;
} while (a < 5);
```

## `break` y `continue`

- Otro uso de `break` es en ciclos, ya que "rompe" la ejecución de
  estos.

``` csharp
int num = 0;
while (num < 20)
    {
        if (num == 5)
            break;

        Console.WriteLine(num);
        num++;
    }
```

> En el bloque de anterior, el `while` parará cuando `num` sea igual a
> 5.

- La palabra `continue` es similar al `break`, pero este solo se salta
  una iteración del ciclo.

``` csharp
for (int i = 0; i < 10; i++) {
    if (i == 5)
        continue;

    Console.WriteLine(i);
}
```

## Operadores lógicos

- Son usados para unir múltiples expresiones y retornar `true` o
  `false`.
- son `&&, ||, !`, AND, OR y NOT respectivamente.

``` csharp
int age = 42;
double money = 540;
if (age > 18 && money > 100) {
    Console.WriteLine("Welcome");
}
```

## El operador condicional

- También llamado operador ternario.
- Podemos hacer una operación condicional asi como en el if pero con una
  sola línea de código.

``` csharp
Expr1 ? Expr2 : Expr3;
```

- La Expr1, es evaluada, si esta es verdadera.
  - Entonces Exp2 es evaluada y se convierte en el valor de toda la
    expresión.
- Si Expr1 es falsa, entonces Exp3 es evaluada y se convierte en el
  valor de toda la expresión.

``` csharp
int age = 42;
string msg;
msg = (age >= 18) ? "Welcome" : "Sorry";
Console.WriteLine(msg)
```

# Métodos

## Introducción a los métodos

- Un método es un grupo de declaraciones que hacen una tarea en
  particular.
- Además de los métodos que tiene C# puedes definir los tuyos.
- Tienen muchas ventajas:
  - Son código reusable.
  - Fáciles de testear.
  - Modificaciones a un método no afectan al programa.
  - Un método puede aceptar diferentes tipos de inputs.

> Todo programa de C# tiene al menos un método, el método `Main`.

## Declarando métodos

- Para usar un método primero necesitas declararlo, y después llamarlo.
- Cada declaración de método incluye:
  - El tipo de dato que retorna.
  - El nombre del método.
  - Una lista opcional de parámetros.

``` csharp
<tipo de dato de retorno> name(type1 part1, type2 part2, ..., typeN partN){
    //Bloque de código..
    return <tipo de dato>
}
```

``` csharp
int Sqr(int x)
    {
        int result = x * x;
        return result;
    }
```

- Podemos hacer que métodos no retornen nada poniéndoles el tipo de dato
  `void`.

## Llamando a métodos

``` csharp
static void SayHi()
    {
        Console.WriteLine("Hello");
    }

static void Main(string[] args)
    {
        SayHi();
    }
```

> Aquí declaramos un método y lo llamamos desde `Main`, la palabra
> `static` es para hacer los métodos accesibles al `Main`.

## Parámetros

- Las declaraciones de métodos pueden definir una serie de parámetros
  para trabajar.
- Estos parámetros son variables que aceptan valores específicos.

``` csharp
void Print(int x)
    {
        Console.WriteLine(x);
    }
```

> Las declaraciones de parámetros son similares a las declaraciones de
> variables; Estas solo existen dentro del método donde se declararon.

``` csharp
void Print(int x)
    {
        Console.WriteLine(x);
    }

static void Main(string[] args)
    {
        Print(42);
    }
```

> Ahora podemos llamar a nuestro método y pasarle argumentos.

### Parámetros múltiples

- Se pueden tener N número de parámetros en un método separándolos con
  comas en la definición.

``` csharp
int Sum(int x, int y)
    {
        return x + y;
    }
```

> Los métodos retornan valores con la palabra `return`.

``` csharp
int Sum(int x, int y)
    {
        return x + y;
    }

static void Main(string[] args)
    {
        suma = Sum(42, 45);
        Console.WriteLine(suma);
    }
```

> Podemos asignar parámetros múltiples cuando llamamos al método,
> separándoles con comas, asi como también guardar lo que nos regresa el
> método en una variable para usarlo después.

### Parámetros opcionales

- Cuando defines métodos puedes declarar valores por defecto a
  parámetros opcionales.
- Si estos parámetros no están presentes cuando se llama al método se
  usan los valores por defecto.

``` csharp
static int Pow(int x, int y=2)
    {
    int result = 1;
    for (int i = 0; i < y; i++)
        {
            result *= x;
        }

    return result;
    }
```

> El método `Pow` asigna un valor por defecto de 2 al parámetro y.

``` csharp
static void Main(string[] args)
    {
        Console.WriteLine(Pow(4));
        Console.WriteLine(Pow(4,3));
    }
```

### Parámetros nombrados

- Los argumentos nombrados nos ayudan a no tener que recordar el orden
  de los parámetros.
- Cada argumento puede ser especificado a la variable a la que
  pertenece.

``` csharp
static int Are(int h, int w)
    {
        return h * w;
    }

static void Main(string[] args)
    {
        int res = Area(w: 5, h: 8);
        Console.WriteLine(res);
    }
```

## Pasando argumentos

- Hay tres maneras de pasar argumentos a un método cuando este es
  llamado.
  - Por valor, por referencia y como *Output*.
  - Si se hace por valor, copia el argumento del valor dentro del
    parámetro formal del método.
    - Este es el comportamiento por defecto de C#.

``` csharp
static void Sqrt(int x)
    {
        x = x * x;
    }
static void Main()
    {
        int a = 3;
        Sqrt(a);
        Console.WriteLine(a); // imprime 3
    }
```

- En este caso `x` es parámetro de `Sqrt`, y a es el valor pasado al
  método.

> El método `Sqrt()` no cambia el valor de la variable, trabaja con el
> valor, no con la variable.

### Pasando por referencia

- Pasar un argumento por referencia, copia la dirección de memoria en el
  parámetro formal del método.
  - Dentro de este, esta dirección es usada para acceder al argumento.
    - Esto significa que los cambios que se hacen dentro del método,
      afectan al parámetro.

``` csharp
static void Sqrt(ref int x) // <---
    {
        x = x * x;
    }
static void Main()
    {
        int a = 3;
        Sqrt(ref a); // <---
        Console.WriteLine(a); // imprime 9
    }
```

### Pasando por Output

- Parecidos a pasar por referencia.
  - La diferencia esta en que estos transfieren datos fuera del método
    (como un return).
- Son útiles para retornar varios valores de un método.
- Son denotados por la palabra `out`.

``` csharp
static void GetValues(out int x, out int y) // <---
    {
        x = 5;
        y = 10;
    }
static void Main()
    {
        int a, b;
        GetValues(out a, out b);
        // Ahora a = 5 y b = 10
    }
```

> Las variables deben de estar inicializadas, pero no tener ningún
> valor.

## Sobrecarga

- La Sobrecarga de métodos es cuando dos métodos tienen el mismo nombre
  pero diferentes parámetros.

``` csharp
void Print(int a)
    {
        Console.WriteLine("Value: " + a);
    }
void Print(double a)
    {
        Console.WriteLine("Value: " + a);
    }
```

> Con la sobrecarga podemos tener una misma función que funcione con
> `int` y con `double`.

- Cuando se hace sobrecarga, la definición de los métodos debe diferir
  en su tipo o numero de argumentos.
  - Cuando se llame, esta llamada llegara a la implementación que
    coincida con lo que se da.
- Todos los métodos deben coincidir en el tipo de retorno que tienen.

## Recursividad

- Es un método que se llama a si mismo.
- Un ejemplo puede ser el calculo del factorial de un número.
  - num \* num-1 hasta 1.

``` csharp
static int Fact(int num)
    {
        if (num == 1) {
            return 1;
        }
        return num * Fact(num-1);
    }
```

# Clases y objetos

## Clases

- En la programación orientada a objetos una clase es un tipo de dato
  que define un conjunto de:
  - Variables y métodos para un objeto declarado.
- Una clase es como un plano.
  - Define datos y comportamientos para un tipo.

``` csharp
class MiPrimeraClase
    {
        //variables, métodos, etc.
    }
```

> Define un tipo de dato para objetos, pero no es un objeto.

## Objetos

- Una clase puede usarse para declarar múltiples objetos.
- Un objeto es llamado también es llamado una instancia de una clase.
- Cada objeto tiene sus propias características, llamadas atributos.
  - Las cuales son heredadas de la clase de la cual es instancia.

## Valor y tipos de referencia

### Tipos de Valor

- C# tiene dos formas de guardar valores, por referencia y por valor.
- Los tipos de dato predeterminados son usados para declarar variables
  que son tipos de valor.
  - Su valor es guardado en la memoria en un lugar llamado *stack* (la
    pila).

### Tipos de referencia.

- El tipo de referencia es usado para guardar objetos.
  - Como por ejemplo cuando instancias un objeto es guardado como un
    tipo de referencia.
- Estos son guardados en una parte de la memoria llamada *heap*
  (Montículo).
  - Cuando instancias un objeto, los datos de este son guardados en la
    *heap* mientras que la dirección de memoria de la heap es guardada
    en el *stack*.

![ss-01.png](/lenguajes/csharp/ss-01.png)

`Stack`  
Es usado para asignación de memoria estática, eso incluye a todas tus
variables como x.

`Heap`  
Es usada para asignación de memoria dinámica, eso incluye objetos
*custom* que podrían necesitar más memoria durante la ejecución de un
programa.

## Clases

``` csharp
class Person
    {
        int age;
        string name;
        public void SayHi()
            {
                Console.WriteLine("Hola");
            }
    }
```

- En el código de arriba tenemos una clase Persona.
  - Tiene las variables `age` y `name`, asi como el método `SayHi`.
- Podemos incluir `access modifiers` (modificadores de acceso), también
  llamados `members` (miembros).
  - Son palabras claves usadas para especificar la accesibilidad a un
    miembro.
  - Un miembro definido como público puede se accedido desde afuera de
    la clase.
    - Por eso es que `SayHi()` es público.

``` csharp
class Person {
    int age;
    string name;
    public void SayHi() {
        Console.WriteLine("Hi");
    }
}
static void Main(string[] args)
{
    Person p1 = new Person();
    p1.SayHi();
}
```

- El operador `new`, instancia al objeto y retorna una referencia de
  este a su posición en la heap.
- El código de arriba instancia un objeto tipo `Person` llamado `p1` y
  lo usa para llamar al método público `SayHi()`.

``` csharp
class Dog
{
    public string name;
    public int age;
}
static void Main(string[] args)
{
    Dog bob = new Dog();
    bob.name = "Bobby";
    bob.age = 3;

    Console.WriteLine(bob.age);
}
```

- Podemos acceder a los miembros públicos de una clase, en el ejemplo
  las variables nombre y edad.

## Encapsulación

- En programación se refiere a restringir el acceso a ciertas partes de
  una clase.
  - Es llamado también `information hiding`.
  - Nos permite ocultar detalles de una clase.
- C# nos da las siguientes modificadores de acceso:
  - `public`.
    - Hace un miembro accesible desde fuera de la clase.
  - `private`.
    - Hace los miembros accesibles solo dentro de la clase y los oculta
      fuera de esta.
  - `protected`.
  - `internal`.
  - `protected internal`.

``` csharp
class BankAccount {
    private double balance=0;
    public void Deposit(double n) {
        balance += n;
    }
    public void Withdraw(double n) {
        balance -= n;
    }
    public double GetBalance() {
        return balance;
    }
}
class Program
{
    static void Main(string[] args)
    {
        BankAccount b = new BankAccount();
        b.Deposit(199);
        b.Withdraw(42);
        Console.WriteLine(b.GetBalance());
    }
}
```

- Usamos encapsulación para ocultar la variable `balance`.
- Aun así podemos acceder a `balance` mediante los métodos `Deposit()`,
  `Withdraw()` y `GetBalance()`.
  - Así podemos tener el control sobre lo que pasa con la variable
    `balance` y aplicar distintas verificaciones sobre lo que queremos
    hacer.
- La encapsulación nos permite:
  - Controlar la manera en la que se accede a los datos o en la que se
    modifican.
  - Podemos extender el código de una manera más segura y limpia a
    nuevos requerimientos.

## Constructores

- Es un miembro especial de una clase que se ejecuta cuando se crea un
  nuevo objeto de esta clase.
- Tienen el mismo nombre que la clase, son públicos y no tienen ningún
  retorno.

``` csharp
class Person
{
  private int age;
  public Person()
  {
    Console.WriteLine("Hi there");
  }
}
```

- Esto es útil cuando necesitamos que el objeto sea creado con ciertos
  parámetros.
  - Por default no tienen parámetros, pero si se necesitan pueden
    agregarse.

``` csharp
class Person
{
    private int age;
    private string name;
    public Person(string nm)
    {
        name = nm;
    }
    public string getName()
    {
        return name;
    }
}
static void Main(string[] args)
{
    Person p = new Person("David");
    Console.WriteLine(p.getName());
}
```

> En el ejemplo creamos un objeto pasándole un argumento al constructor.

## Propiedades

- Es una buena práctica encapsular los miembros de una clase y proveer
  acceso a ellos solo cuando es necesario.
- Una propiedad es un miembro que provee un mecanismo flexible para
  leer, escribir o computar el valor de un campo privado.
  - Estas pueden ser usadas como miembros públicos pero incluyen métodos
    llamados `accessors`.
    - Estos incluyen declaraciones que podemos usar para obtener *get*
      (leer o computar) o *set* (escribir) un campo en especifico.

``` csharp
class Person {
    private string name; //campo

    public string Name // Propiedad
        {
            get { return name; }
            set { name = value; }
        }
}
```

- En el ejemplo, la clase `Person` tiene una propiedad llamada `Name`
  que tiene un `set` y un `get` para acceder a el campo `name`.

> `value` representa el valor que le asignemos a una propiedad usando
> `set`.

> Se le puede llamar a una propiedad con cualquier nombre pero la
> convención es que las propiedades tengan el mismo nombre que el campo
> peo con mayúscula en la primera letra.

Una vez la propiedad es definida podemos usarla para asignar o leer del
miembro.

``` csharp
static void Main(string[] args)
    {
        Person p = new Person;
        p.Name = "Bob";
        Console.WriteLine(p.Name);
    }
```

> Se accede a la propiedad por su nombre, como cualquier miembro público
> de la clase.

- Podemos tener una propiedad con solo un `get` y sin un `set` o hacer
  la propiedad privada.
- Las propiedades nos permiten tener la opción de controlar la lógica de
  acceder a una variable.

``` csharp
class Person {
    private int age=0;
    public int Age;
    {
        get { return age; }
        set {
            if (value > 0) {
                age = value;
            }
        }
    }
}
```

> En el ejemplo verificamos que el valor que le asignemos a `age` sea
> mayor a 0.

## Propiedades auto implementadas.

- Cuando no necesitas ninguna lógica las propiedades, C# provee una
  manera rápida para declarar miembros privados a través de sus
  propiedades.

``` csharp
public string Name { get; set; }
```

- Esta es la llamada propiedad auto-implementada.
- Usándola ya no necesitamos declarar el campo privado por separado.

``` csharp
class Person {
    public string Name { get; set; }
}
static void Main(string[] args)
    {
        Person p = new Person;
        p.Name = "Bob";
        Console.WriteLine(p.Name);
    }
// Imprime Bob
```

# Arreglos y Cadenas

## Arreglos

- También llamados *Arrays*.
- C# provee numerosas clases para guardar y manipular datos.
- Es una colección de elementos del **mismo tipo**.

``` csharp
// declaración de un array
int [ ] myArray;
```

> Con esto declaramos un arreglo de enteros.

- Pero sabiendo que los arreglos son objetos, debemos declararlos como
  tal.

``` csharp
int [ ] myArray = new int[5];
```

> Con esto instanciamos un arreglo de enteros con 5 espacios dentro de
> el.

- Después de crear un arreglo podemos asignar valores en un índice
  especifico.

``` csharp
int [ ] myArray = new int[5];
myArray[0] = 23
```

> Aquí asignamos el número 23 en la posición 0 del arreglo.

- En C# los arreglos empiezan en 0.

``` csharp
string [ ] names = new string[3] {"Jhon", "Cena", "Jose"};
```

> Podemos asignar valores iniciales a un arreglo se esta forma.

- Si asignamos valores iniciales podemos omitir el número de elementos
  que son en la declaración.
- Incluso podemos omitir el operador new.

``` csharp
string [ ] names = {"John", "Cena", "Jose"};
```

- Para acceder a los elementos del arreglo solo tenemos que especificar
  el número de índice que tiene el elemento.

``` csharp
Console.WriteLine(names[2]);
```

## Usando arreglos en ciclos

- A veces es necesario iterar sobre los elementos de un arreglo.

``` csharp
int[ ] a = new int[10];

for (int k = 0; k < 10; k++) {
  a[k] = k*2;
}
```

- Esto se puede lograr de manera fácil y rápida con un ciclo `for`.

``` csharp
for (int k = 0; k < 10; k++) {
    Console.WriteLine(a[k]);
}
```

### El ciclo `foreach`

- El ciclo `foreach` nos da una manera más fácil de acceder a los
  elementos de un arreglo.

``` csharp
foreach (int k in a) {
    Console.WriteLine(k);
}
```

> Este es el equivalente de el ejemplo anterior con un ciclo `for`.

- Este itera sobre el arreglo, y asigna el valor del elemento actual a
  `k`.

> El tipo de dato dentro del `foreach` debe de coincidir con el tipo de
> los elementos del arreglo.

``` csharp
// a veces se usa la palabra var dentro del foreach
foreach (var k in a) {
    //aaaaaa
}
```

- Esto se hace para que el compilador determine el tipo de dato
  apropiado automáticamente.

## Arreglos multidimensionales

- Los arreglos pueden tener múltiples dimensiones.

``` csharp
int [ , ] x = new int[3,4];
```

> Esto es una matriz de 3x4.

## Arreglos dentados

- También llamados *jagged arrays*.
- Es básicamente un arreglo en el cual sus elementos son arreglos.

``` csharp
int [][] = jaggedArr = new int[3][];
```

> Tenemos un arreglo de una sola dimensión, con 3 elementos, los cuales
> son arreglos de una sola dimensión.

``` csharp
int[ ][ ] jaggedArr = new int[ ][ ]
{
  new int[ ] {1,8,2,7,9},
  new int[ ] {2,4,6},
  new int[ ] {33,42}
};
```

> Si queremos tener valores iniciales, podemos declarar el mismo arreglo
> de esta manera.

``` csharp
int x = jaggedArr[2][1]; //42
```

> Podemos acceder a los elementos del arreglo de esta manera.

## Propiedades de los arreglos y métodos

### Propiedades de los arreglos

- La clase de `array` nos da distintas propiedades y métodos para
  trabajar con ella.
  - Por ejemplo las propiedades `Length` y `Rank` nos dejan saber la
    longitud y las dimensiones de un arreglo respectivamente.
  - Algunos métodos que nos da la clase `array` son: `Max`, `Min`, `Sum`
    que nos retornan el elemento máximo, mínimo y la suma de todos los
    elementos respectivamente.

## Trabajando con cadenas

### Cadenas

- Es común pensar en las cadenas de caracteres como un arreglo de
  caracteres, pero en C# son objetos.
- Cuando creas una cadena en C#, instancias un objeto de la clase
  `string`.
- Tenemos unas cuantas propiedades y métodos útiles para trabajar con
  cadenas.
  - `Length`: Nos retorna la longitud de una cadena.
  - `IndexOf(value)`: Retorna el índice del la primera ocurrencia al
    valor dado.
  - `Insert(index, value)`: Inserta el valor dado en la posición dada.
  - `Remove(index)`: Remueve todos los caracteres de la cadena desde el
    índice especificado.
  - `Substring(index, length)`: Retorna una porción de la cadena, con
    desde el índice y por la longitud dada.
  - `Contains(value)`: Retorna `True` si la cadena contiene el valor
    especificado.
- También podemos acceder a los elementos de una cadena por su índice,
  como si fuera un arreglo.

``` csharp
static void Main(string[] args)
        {
            string text = "This is some text about a dog. The word dog appears in this text a number of times. This is the end.";
            text = text.Replace("dog", "cat");
            text = text.Substring(0, text.IndexOf(".")+1);

            Console.WriteLine(text);
        }
```

> C# tiene muchos métodos para trabajar con cadenas.

# Más sobre clases

## Destructores

- Así como los constructores son usados cuando una clase es instanciada
  los destructores son usados cuando una clase es destruida o borrada.
- Los destructores tienes las siguientes características:
  - Una clase solo puede tener un solo destructor.
  - Los destructores no pueden ser llamados, son llamados
    automáticamente.
  - No toman parámetros o modificadores.
  - El nombre de el destructor tiene que ser el mismo que el de la clase
    con un `~` antes del nombre.

``` csharp
class Dog {
    ~Dog()
        {
            //Código
        }
}
```

> Son útiles para liberar recursos cuando sales del programa, ejemplos
> pueden ser: cerrando archivos, liberar memoria, etc.

``` csharp
class Dog
{
    public Dog() {
        Console.WriteLine("Constructor");
    }
    ~Dog() {
        Console.WriteLine("Destructor");
    }
}
static void Main(string[] args)
{
    Dog d = new Dog();
}
```

> En este ejemplo, cuando instanciamos el objeto el programa imprime
> "Constructor" y cuando el programa termina, el objeto es borrado y el
> destructor imprime "Destructor".

## Miembros estáticos

- Todos los miembros de una clase (variables, propiedades, métodos)
  pueden ser declarados como `static` (estáticos).
  - Esto hace que los miembros pertenezcan a la clase en vez de
    pertenecer al objeto individual.
    - No importa cuantos objetos de la clase son creados, solo hay una
      copia del miembro estático.

``` csharp
class Cat {
    public static int count=0;
    public Cat() {
        count++;
    }
}
```

> No importa cuantos objetos `Cat` instanciemos, `count` siempre sera el
> mismo para todos estos.

- Debido a su naturaleza global, estos miembros pueden ser accedidos
  directamente usando el nombre de la clase.

``` csharp
class Cat {
    public static int count=0;
    public Cat() {
        count++;
    }
}
static void Main(string[] args)
    {
        Cat c1 = new Cat();
        Cat c2 = new Cat();

        Console.WriteLine(Cat.count()); // 2
    }
```

> En el ejemplo accedemos a la variable `count` con el nombre de la
> clase y no el de las instancias, y esta variable es la misma en todas
> las instancias de `Cat`.

> Se debe acceder a los miembros estáticos con el nombre de la clase
> siempre.

**El mismo concepto se aplica a los métodos estáticos.**

``` csharp
class Dog {
    public static void Bark() {
        Console.WriteLine("Woof");
    }
}
static void Main(string[] args)
    {
        Dog.Bark();
    }
```

> Métodos estáticos solo pueden acceder a miembros estáticos.

> El método `Main` es estático, y es el punto de entrada de cualquier
> programa, entonces cualquier método llamado directamente desde el Main
> tiene que ser estático.

- Las constantes son estáticas por definición.

``` csharp
class Math {
    public const int ONE = 1;
}
```

### Constructores estáticos

- Los constructores pueden ser declarados estáticos para inicializar
  miembros estáticos de la clase.

``` csharp
class SomeClass {
    public static int x { get; set; }
    public static int y { get; set; }

    static SomeClass() {
        x = 10;
        y = 10;
    }
}
```

> El constructor sera llamado cuando intentemos acceder a `SomeClass.X`
> o `SomeClass.Y`.

### Clases estáticas

- Una clase puede ser declarada como estática.
  - Solo puede contener miembros estáticos.
- No se puede instanciar un objeto de una clase estática, ya que solo
  una instancia puede existir en el programa.
- Son útiles para combinar propiedades lógicas y métodos.
  - La clase `Math` es un buen ejemplo.

``` csharp
Console.WriteLine(Math.Pow(2, 3));
```

> Podemos acceder a la clase `Math` usando el nombre de la clase, sin
> declarar un objeto

1.  Ejemplos

    La clase `Array` tiene algunos métodos estáticos para manipular
    arreglos.

    ``` csharp
    int[] arr = {1, 2, 3, 4};

    Array.Reverse(arr);
    //arr = {4, 3, 2, 1}

    Array.Sort(arr);
    //arr = {1, 2, 3, 4}
    ```

    La clase `String` también los tiene.

    ``` csharp
    string s1 = "some text";
    string s2 = "another text";

    String.Concat(s1, s2); // combines the two strings

    String.Equals(s1, s2); // returns false
    ```

    > La clase `Console` También es otro ejemplo de una clase estática.

## `This` & `readonly`

### `This`

- La palabra `This` es usada dentro de una clase y se refiere a la
  instancia actual de la clase.
  - Al objeto actual.
- Se usa comúnmente para distinguir los miembros de la clase de otros
  datos como.
  - Parámetros locales o formales de un método.

``` csharp
class Person {
    private string name;
    public Person(string name) {
        this.name = name;
    }
}
```

> Aquí, `this.name` representa el miembro de la clase y `name` el nombre
> el parámetro del constructor.

> Otro uso común de `this` es para pasar la instancia actual a un método
> como un parámetro: `ShowPersonInfo(this);`

### El modificador `readonly`

- Previene que un miembro de una clase sea modificado después de la
  construcción.
  - Esto significa que solo puede ser modificado cuando lo declaras
    desde un constructor.

``` csharp
class Person {
    private readonly string name = "John";
    public Person(string name) {
        this.name = name;
    }
}
```

> Si intentamos modificar el campo `name` en algún otro lugar tendremos
> un error.

- `readonly` y `const` son parecidos pero tienen ciertas diferencias.
  - Una campo `const` debe de ser inicializado con un valor y `readonly`
    no.
  - Un campo `readonly` puede ser cambiado en un constructor, el `const`
    no.
  - Un campo `readonly` puede ser asignado a un valor que es el
    resultado de un calculo, `const` no.

## Indexadores

- Permiten a objetos ser indexados como si fueran un arreglo.
- Un ejemplo es la clase `String`, la cual es un arreglo de objetos tipo
  `Char` implementando un indexadores para que podamos acceder a los
  elementos.

``` csharp
string str = "Hello World";
char x = str[4];
Console.WriteLine(x);
```

- La declaración de un indexador es similar a una propiedad.

``` csharp
class Clients {
    private string[] names = new string[10];

    public string this[int index] {
        get {
            return names[index];
        }
        set {
            names[index] = value;
        }
    }
}
```

- Todos los indexadores necesitan un índice.
- Se usan `get` y `set` para definir un indexador.
  - La diferencia es que los indexadores retornan o ponen un valor
    particular de la instancia del objeto.
- Son definidos con la palabra `this`.
  - Esto para obtener o poner el elemento de la instancia.

``` csharp
Clients c = new Clients();
c[0] = "Dave";
c[1] = "Bob";

Console.WriteLine(c[1]);
```

> Se usan indexadores típicamente si la clase representa una lista,
> colección o un arreglo de objetos.

## Sobrecarga de Operadores

- La mayoría de los operadores en C# puede ser sobrecargados.
  - Esto significa que pueden ser redefinidos para que hagan otras
    cosas.
- Por ejemplo, podemos redefinir el comportamiento de `+` en una clase.

``` csharp
class Box {
    public int Height {get; set;}
    public int Width {get; set;}
    public Box(int h, int w) {
        Height = h;
        Width = w;
    }
}
static void Main(string[] args) {
    Box b1 = new Box(14, 3);
    Box b2 = new Box(5, 7);
}
```

Teniendo dos objetos tipo `Box` si quisiéramos sumarlos para tener un
objeto `Box` más grande haríamos.

``` csharp
Box b3 = b1 + b2;
```

> Este comportamiento lo lograríamos a través de la sobrecarga de
> operadores.

- Son métodos con nombres especiales, donde la palabra `operator` va
  antes que el operador a definir.
- Similar a cualquier otro método, tienen tipos de retorno y una lista
  de parámetros.

``` csharp
public static Box operator+ (Box a, Box b) {
    int h = a.Height + b.Height;
    int w = a.Width + b.Width;
    Box res = new Box(h, w);
    return res;
}
```

> En el ejemplo estamos sobrecargando el operador `+` para objetos de
> nuestra clase `Box`.

> Todos los operadores sobrecargados deben ser estáticos.

``` csharp
class Box {
    public int Height { get; set; }
    public int Width { get; set; }
    public Box(int h, int w) {
        Height = h;
        Width = w;
    }
    public static Box operator+(Box a, Box b) {
        int h = a.Height + b.Height;
        int w = a.Width + b.Width;
        Box res = new Box(h, w);
        return res;
    }
}

static void Main(string[] args)
{
    Box b1 = new Box(14, 3);
    Box b2 = new Box(5, 7);
    Box b3 = b1 + b2;

    Console.WriteLine(b3.Height);// 19
    Console.WriteLine(b3.Width);// 10
}
```

> Podemos sobrecargar todos los operadores aritméticos y de comparación.

# Herencia y polimorfismo

## Herencia

- Nos permite definir una clase basada en otra clase.
- La clase que hereda sus propiedades a otra es llamada **clase base**.
  - La clase a la que se hereda es llamada **clase derivada**.
- Podemos definir una clase `Animal` con ciertas propiedades y usarla
  para construir las clases `Perro` y `Gato`.
  - Estas heredan todas las propiedades de la clase animal y pueden
    tener sus propias propiedades.

``` csharp
class Animal {
    public int Legs {get; set;}
    public int Age {get; set;}
}
```

> Podemos tener nuestra clase `Animal` que será nuestra clase base.

``` csharp
class Dog : Animal {
    public Dog() {
        Legs = 4;
    }
    public void Bark() {
        Console.Write("Woof");
    }
}
```

> Y con ella crear nuestra clase `Dog`, usando sus miembros y agregando
> unos propios de la clase nueva.

- Debemos definir la clase y con dos puntos después del nombre definir
  la clase base de nuestra clase.
- Todos los miembros públicos de la clase `Animal` se vuelven miembros
  públicos de la clase `Dog`, incluyendo métodos.

``` csharp
static void Main(string[] args)
    {
        Dog d = new Dog();
        Console.WriteLine(d.legs); // 4
        d.Bark();
    }
```

> Esto nos permite rehusar código ya escrito sin necesidad de reescribir.

> C# no soporta herencia múltiple, asi que no puedes heredar de varias
> clases al mismo tiempo.
>
> Sin embargo, puedes usar **interfaces** para implementar herencia
> múltiple.

## Miembros protegidos

- El modificador `protected` es parecido a `private`.
  - La diferencia es que `protected` puede ser accedido desde las clases
    derivadas.

``` csharp
class Person {
    protected int Age {get; set;}
    protected string Name {get; set;}
}

class Student : Person {
    public Student(string nm) {
        Name = nm;
    }
    public void Speak() {
        Console.Write("Name: " + Name);
    }
}

static void Main(string[] args)
{
    Student s = new Student("David");
    s.Speak(); // Name: David
}
```

> En el ejemplo podemos acceder y modificar la propiedad `name`, desde
> la clase derivada.

``` csharp
static void Main(string[] args)
{
    Student s = new Student("David");
    s.Name = "Bob"; // Error!
}
```

> Si intentamos acceder a ella desde afuera de la clase obtendremos un
> error.

## Sellado

- Podemos prevenir a las clases de heredar sus miembros usando el
  modificador `sealed`.

``` csharp
sealed class Animal {
    //some code
}
class Dog : Animal { } //Error

static void Main(string[] args)
{

}
```

## Constructor y destructor de la clase derivada.

- Cada que se instancia un objeto se llama a su constructor y cada que
  se destruye se llama a su destructor.
- Con la herencia, la clase heredada no hereda el constructor y el
  destructor de la clase base.
  - Así que debes definir siempre unos nuevos cada que creas una clase
    heredada

``` csharp
class Animal {
    public Animal() {
        Console.WriteLine("Animal created");
    }
    ~Animal() {
        Console.WriteLine("Animal deleted");
    }
}

class Dog: Animal {
    public Dog() {
        Console.WriteLine("Dog created :D");
    }
    ~Dog() {
        Console.WriteLine("Dog deleted :c");
    }
}

static void Main(string[] args)
{
    Dog d = new Dog();
}
// Resultando en:
//Animal created
//Dog created
//Dog deleted
//Animal deleted
```

> Cuando se crea el objeto `Dog` llamamos primero a el constructor de la
> clase `Animal` y después al de la clase `Dog`, y con los destructores
> pasa lo mismo.

## Polimorfismo

- La palabra significa "Tener muchas formas".
- Significa que un método puede tener muchas implementaciones
  diferentes.
- Suponiendo que nuestro programa tiene un método `Draw`, y que
  necesitamos dibujar muchas formas diferentes.
  - Podemos usar polimorfismo para llamar al método `Draw` correcto de
    cualquier clase derivada.
  - Estos métodos deben de llevar la palabra `virtual` en la clase base.

``` csharp
class Shape {
    public virtual void Draw() {
        Console.Write("Base Draw");
    }
}
```

> La palabra `virtual`, permite al método ser sobre escrito en la clase
> derivada.

> Los métodos virtuales nos permiten trabajar con grupos de objetos
> relacionados en una manera uniforme.

``` csharp
class Circle : Shape {
    public override void Draw() { // <-- Llevan la palabra override en la clase derivada.
        // draw a circle...
        Console.WriteLine("Circle Draw");
    }
}
class Rectangle : Shape {
    public override void Draw() {
        // draw a rectangle...
        Console.WriteLine("Rect Draw");
    }
}
```

> Ahora podemos usar el método para sobre escribirlo y adecuarlo a lo
> que necesitamos.

``` csharp
static void main(string[] args)
    {
        Shape c = new Circle();
        c.Draw();

        Shape r = new Rectangle();
        r.Draw();
    }
```

> Cada instancia llama a su propio método `Draw` gracias al
> polimorfismo.

Para resumir, el polimorfismo es una manera de llamar al mismo método
para diferentes objetos y generar resultados diferentes basados en el
tipo de objeto, esto se logra mediante métodos virtuales en la clase
base.

Para implementar esto, creamos objetos del tipo de la clase base pero
los instanciamos con el tipo de la clase derivada.

``` csharp
Shape c = new Circle();
```

Podríamos solo instanciar cada objeto con su tipo y llamar a su método
también.

``` csharp
Circle c = new Circle();
c.Draw();
```

Pero, hacerlo con polimorfismo nos trae algunas ventajas.

- Nos permite tratar a los objetos de la misma manera.
  - Debido a que todos son objetos tipo `Shape`, es más fácil
    mantenerlos y trabajar con ellos.

## Clases abstractas

- Así como el polimorfismo es logrado con métodos virtuales que son
  `overridden` en la clase derivada.
- En algunas situaciones no es necesario que el método virtual tenga una
  definición separada de la clase base.
- Estos métodos son definidos usando la palabra `abstract`.
  - Con esto se especifica que las clases derivadas deben definir ese
    método por su cuenta.
    - No puedes crear objetos de una clase que tiene métodos abstractos,
      por esa misma razón, la clase misma debe de ser abstracta.

``` csharp
abstract class Shape {
    public abstract void Draw();
}
```

- El método `Draw` es abstracto, entonces no tiene cuerpo, no lo
  necesita puedes terminar la linea con un `;`.
- Y la clase debe de ser abstracta porque tiene un método abstracto.

Una clase abstracta se hace para ser la base de otras clases, actúa como
una plantilla para otras clases.

``` csharp
abstract class Shape {
    public abstract void Draw();
}
class Circle : Shape {
    public override void Draw() {
        Console.WriteLine("Circle Draw");
    }
}
class Rectangle : Shape {
    public override void Draw() {
        Console.WriteLine("Rect Draw");
    }
}
static void Main(string[] args)
{
    Shape c = new Circle();
    c.Draw(); // Circle Draw
}
```

> Ahora teniendo la clase abstracta, podemos usarla y definir su propio
> método `Draw`.

- Las clases abstractas tienen las siguientes características:
  - No pueden ser instanciadas.
  - Puede contener métodos abstractos y `accessors`.
  - Una clase no abstracta derribada de una clase abstracta debe de
    implementaciones de todos los miembros heredados.

> No es posible modificar una clase abstracta con la palabra `sealed`,
> porque son contrarios.
>
> El modificador `sealed` previene una clase de ser heredada y el
> modificador `abstract` requiere que una clase sea heredada.

## Interfaces

- Una interfaz es una clase completamente abstracta, que contiene
  **solo** miembros abstractos.
- Es declarada usando la palabra `interface`.

``` csharp
public interface IShape {
    void Draw();
}
```

- Todos los miembros de la interfaz son abstractos por defecto, así que
  no hay necesidad de poner la palabra.
- Las interfaces son públicas (por defecto), pero pueden ser privadas o
  protegidas.

> Es común usar la letra 'I' mayúscula al inicio del nombre de la
> interfaz.

> Pueden contener propiedades, métodos, etc, pero no pueden contener
> campos (variables).

- Cuando una clase implementa una interfaz, debe implementar o definir
  todos sus métodos.
  - El termino "Implementar una interfaz", es usado para describir el
    proceso de, crear una clase basada en una interfaz.
- La interfaz describe solamente que es lo que debe de hacer una clase.
  - La clase implementando la interfaz debe definir como cumplir esos
    comportamientos.
- La sintaxis para implementar una interfaz es la misma que para derivar
  una clase.

``` csharp
public interface IShape {
    void Draw();
}

class Circle : IShape {
    public void Draw() {
        Console.WriteLine("Circle Draw");
    }
}

static void Main(string[] args) {
    IShape c = new Circle();
    c.Draw();
}
```

> La palabra `override` no es necesaria cuando implementas una interfaz.

- ¿Porque usar interfaces en lugar de clases abstractas?
  - Una clase puede heredar de una sola clase base, pero puede
    implementar muchas interfaces.
- Usando interfaces puedes incluir comportamientos de distintas clases
  en una clase.
  - Para implementar muchas interfaces estas se separan usando comas
    cuando creas la clase.
    - `class A : IShape, IAnimal, etc...`

### Implementación por defecto

- La implementación por defecto en una interfaz nos permite escribir una
  implementación de cualquier método.
- Esto es útil cuando necesitamos proveer una sola implementación para
  un funcionamiento común.

Digamos que queremos añadir una nueva funcionalidad común a una interfaz
ya existente, la cual es implementada por muchas clases.

Sin la implementación por defecto (antes de C# 8), esta operación
provocaría errores, porque el método que agregamos no esta implementado
en la clase, la implementación por defecto resuelve este problema.

``` csharp
public interface IShape {
    void Draw();
    void Finish() {
        Console.WriteLine("Done!");
    }
}
class Circle : IShape {
    public void Draw() {
        Console.WriteLine("Circle Draw");
    }
}
static void Main(string[] args)
{
    IShape c = new Circle();
    c.Draw(); // Circle Draw
    c.Finish(); // Done!
}
```

- Agregamos el método `Finish()` con la implementación por defecto en
  nuestra interfaz, y la llamamos sin implementarla en la clase
  `Circle`.

> Métodos con la implementación por defecto pueden ser sobre escritos
> libremente dentro de la clase que implementa esa interfaz.

## Clases anidadas

- C# soporta clases anidadas.
  - Una clase que es miembro de otra clase.

``` csharp
class Car {
    string name;
    public Car(string nm) {
        name = nm;
        Motor m = new Motor();
    }
    public class Motor {
        // some code
    }
}
```

- La clase `Motor` esta dentro de la clase `Car` y puede ser usada de la
  misma manera a otros miembros de la clase.

## `namespaces`

Cuando creas un proyecto, tiene una estructura parecida a la siguiente.

``` csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Learn {
    class Program {
        static void Main(string[] args) {

        }
    }
}
```

- Todo el Programa esta dentro de un `namespace`
  - Declaran un ámbito (scope) que contiene un conjunto de objetos
    relacionados.
  - Se pueden usar para organizar elementos de código.
    - Puedes definir tus propios `namespaces` y usarlos en tu programa.
- La palabra `using` declara que el programa esta usando un `namespace`.

``` csharp
using System;
// ...
Console.WriteLine("Hi");
```

> El `namespace` `System` es donde la clase `Console` esta declarada.

Si no usamos `using` tenemos que especificar el `namespace`.

``` csharp
System.Console.WriteLine("Hi");
```

> El .NET Framework usa `namespaces` para organizar sus clases, siendo
> `System` un ejemplo de esto.

> Declarar tus propios `namespaces` puede ayudar a agrupar tus clases y
> métodos en proyectos grandes.

# `Structs`, `Enums`, Excepciones & Archivos

## `Structs`

- Es un tipo de valor que es usado típicamente para encapsular pequeños
  grupos de variables relacionadas.

``` csharp
struct book {
    public string title;
    public double price;
    public string author;
}
```

- Comparten la mayoría de las sintaxis con las clases, pero están más
  limitadas que estas.
- Los `structs` pueden ser instanciados sin usar el operador `new`.

``` csharp
static void main(string[] args) {
    Book b;
    b.title = "Test";
    b.price = 5.99;
    b.author = "David";

    Console.WriteLine(b.title);
}
```

> No soportan herencia y no pueden contener métodos virtuales.

- `structs` pueden contener:
  - Métodos.
  - Propiedades.
  - Indexadores.
  - Etc.
- No pueden contener constructores por defecto (Constructores sin
  parámetros).
  - Pero pueden contener constructores que toman parámetros.
    - Si los usan, la palabra `new` es necesaria para instanciarlos de
      manera similar a una clase.

``` csharp
struct Point {
    public int x;
    public int y;
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
public void Main(string[] args) {
    Point p = new Point(10, 15);
    Console.WriteLine(p.x);
}
```

### `Structs` vs Clases

- Las clases son usadas para modelar comportamientos más complejos o
  datos que están destinados a ser modificados después de que se crea el
  objeto.

- Los `structs` son mejores para estructuras de datos pequeñas que
  contienen datos que no están destinados a cambiar después de crearse.

  > Todos los tipos de datos por defecto en C# son `structs` (int,
  > double, bool, char, etc).

## `Enums`

- La palabra `enum` es usada para declarar una enumeración.
  - Un tipo que consiste de un conjunto de constantes llamadas la lista
    del enumerador.

``` csharp
enum Days {Sun, Mon, Tue, Wed, Thu, Fri, Sat};
```

Puedes también asignar tus propios valores al `enum`.

``` csharp
enum Days {Sun, Mon, Tue=4, Wed, Thu, Fri, Sat};
```

- En el ejemplo de arriba, la enumeración empieza desde 0, siendo 1 Mon,
  y Tue 4 Wed 5 y asi, respetando los valores dados.
- Podemos acceder a los elementos de un `enum` con la sintaxis de punto.
- Para asignar los valores de un enum a variables necesitamos
  especificar el tipo entre paréntesis.

``` csharp
enum Days {Sun, Mon, Tue, Wed, Thu, Fri, Sat};

static void Main(string[] args) {
    int x = (int)Days.Tue;
    Console.WriteLine(x);
}
```

> `enums` definen variables que pertenecen a un conjunto fijo, como lo
> pueden ser los meses del año o los días de la semana.

Estos son usados en conjunto con `switch`

``` csharp
enum TrafficLights { Green, Red, Yellow };

static void Main(string[] args) {
    TrafficLights x = TrafficLights.Red;
    switch (x) {
        case TrafficLights.Green:
            Console.WriteLine("Go!");
            break;
        case TrafficLights.Red:
            Console.WriteLine("Stop!");
            break;
        case TrafficLights.Yellow:
            Console.WriteLine("Go faster!");
            break;
    }
}
```

## Manejo de excepciones

- Una excepción es un problema que ocurre durante la ejecución de un
  programa.
  - Estas causan que el programa termine de manera anormal.
- Estas pueden suceder por muchas razones, desde datos inválidos hasta
  fallas de lógica.

``` csharp
int[] arr = new int[] {4, 6, 8};
Console.WriteLine(arr[8]);
```

> Este código causara una excepción porque estamos intentando acceder a
> un valor que no existe.

- C# nos provee una manera de manejar estas excepciones con un
  `try-catch`.

``` csharp
try {
    int[] arr = new int[] {4, 6, 8};
    Console.WriteLine(arr[8]);
}
catch(Exeption e) {
    Console.Writeline("Un error ha ocurrido.")
}
```

- El código que puede detonar una excepción se pone dentro del bloque
  `try`.
  - Si una excepción ocurre, se ejecuta el bloque `catch` sin que el
    programa pare de manera abrupta.
- Dentro del bloque `catch` entre paréntesis se pone el tipo de
  excepción que queremos manejar, pero podemos usar la palabra
  `Exception` para manejar cualquier excepción.
- La excepción

``` csharp
try {
    int[] arr = new int[] {4, 6, 8};
    Console.WriteLine(arr[8]);
}
catch(Exception e) {
    Console.Writeline(e.Message);
}
```

### Manejando diferentes excepciones

- Podemos incluir diferentes bloques `catch` para cada `try` para tener
  comportamientos personalizados para cada excepción.

``` csharp
int x, y;
try {
    x = Convert.ToInt32(Console.Read());
    y = Convert.ToInt32(Console.Read());
    Console.WriteLine(x / y);
}
catch (DivideByZeroException e) {
    Console.WriteLine("Cannot divide by 0");
}
catch(Exception e) {
    Console.WriteLine("An error occurred");
}
```

> Las excepciones son muy útiles cuando manejamos input del usuario para
> validar la información que es dada al programa.

### `Finally`

- `finally` es un bloque que pone al final de los bloques `catch` y
  siempre se ejecuta, sin importar si una excepción ocurre o no.
- Es útil para cerrar archivos o conexiones, ya que siempre se tienen
  que cerrar sin importar si un error ocurre o no.

``` csharp
int result=0;
int num1 = 8;
int num2 = 4;
try {
    result = num1 / num2;
}
catch (DivideByZeroException e) {
    Console.WriteLine("Error");
}
finally {
    Console.WriteLine(result);
}
```

## Trabajando con archivos

- El `namespace` `System.IO` tiene varias clases para trabajar con
  archivos.
- La clase `File` es una de ellos.

``` csharp
string str = "Some text";
File.WriteAllText("test.txt", str);
```

- El método `WriteAllText` crea un archivo en la ruta especificada y
  escribe su contenido en el.
  - Si el archivo existe lo sobre escribe.
- Podemos Leer el contenido de un archivo usando `ReadAllText`.

``` csharp
string text = File.ReadAllText("test.txt");
Console.WriteLine(text);
```

- La clase File tiene también otros métodos.
  - `AppendAllText()`
  - `Create()`
  - `Delete()`
  - `Exists()`
  - `Copy()`
  - `Move()`
- Todos estos métodos cierran el archivo cuando terminan de ejecutarse.

# Genéricos

## Genéricos

- Los genéricos nos permiten rehusar código con diferentes tipos.

``` csharp
static void Swap(ref int a, ref int b) {
    int temp = a;
    a = b;
    b = temp;
}
```

> En el código de arriba tenemos un método que cambia de lugar dos
> valores.

Este código solo funciona con enteros, si queremos usarlo con otros
tipos deberemos sobrecargarlo con todos los tipos que querremos usarlo.

- Con los genéricos podemos definir un tipo de dato genérico.

``` csharp
static void Swap<T>(ref T a, ref T b) {
    T temp = a;
    a = b;
    b = temp;
}
```

> `T` es el nombre de nuestro tipo genérico y se define con `<T>`.

## Métodos Genéricos

- Ahora podemos definir nuestro método `Swap` con diferentes tipos de
  datos.
- Cuando llamemos a un método genérico debemos de especificar el tipo de
  dato con el que vamos a trabajar.

``` csharp
static void Swap<T>(ref T a, ref T b) {
    T temp = a;
    a = b;
    b = temp;
}
static void Main(string[] args) {
    int a = 4, b = 9;
    Swap<int>(ref a, ref b);
    Console.WriteLine(a+" "+b);

    string x = "Hello";
    string y = "World";
    Swap<string>(ref x, ref y);
    Console.WriteLine(x+" "+y);
}
```

> Podemos tener múltiples parámetros de diferente tipo en un método
> genérico usando `<T,U>`.

## Clases genéricas

- Los tipos genéricos también pueden ser usados con clases.
- El uso más común para clases genéricas es con colecciones de
  elementos.
  - En estos las operaciones básicas como suma o resta se hacen sin
    importar que tipo de elemento sea.
- Podemos hacer una implementación de una pila genérica.

``` csharp
class Stack<T> {
    int index=0;
    T[] innerArray = new T[100];

    public void Push(T item) {
        innerArray[index++] = item;
    }

    public T Pop() {
        return innerArray[--index];
    }

    public T Get(int k) { return innerArray[k]; }
}
```

- Nuestra implementación de una pila genérica guarda elementos de
  cualquier tipo.
- Así que podemos crear objetos de nuestra clase genérica.

``` csharp
Stack<int> intStack = new Stack<int>();
Stack<string> strStack = new Stack<string>();
Stack<Person> PersonStack = new Stack<Person>();
```

## Colecciones

- Son usadas para agrupar objetos relacionados entre si.
- A diferencia de un arreglo, estos son dinámicos.
- Típicamente incluyen métodos para agregar, remover o contar los
  elementos dentro de ellas.
- Se puede iterar a través de ellas con `for`, `foreach`.
- Como son clases, debes de declarar una instancia de esta antes de
  añadir elementos a esta.

``` csharp
List<int> li = new List<int>();
```

### Colecciones genéricas

- Son el tipo de colección a usar siempre que todos los elementos sean
  del mismo tipo.
- El `namespace` `System.Collections.Generic` incluye las siguientes
  colecciones genéricas.
  - `List<T>.`
  - `Dictionary<TKey,TValue>.`
  - `SortedList<TKey,TValue>.`
  - `Stack<T>.`
  - `Queue<T>.`
  - `Hashset<T>.`

### Colecciones no genéricas

- Guardan elementos que son de tipo `Object`.
- Pueden ser más lentas que las genéricas.
- El `namespace` `System.Collections` incluye las siguientes colecciones
  no genéricas.
  - `ArrayList`
  - `SortedList`
  - `Stack`
  - `Queue`
  - `Hashtable`
  - `BitArray`

## `List` y `BitArray`

- Una lista es similar a un arreglo, pero en esta los elementos pueden
  ser agregados y removidos de manera dinámica.
- Requiere que todos los elementos sean del mismo tipo.
- Incluye los siguientes métodos:
    - `Count`  
        - Obtiene el número de elementos que contiene la lista.
    - `Add`  
        - Añade un elemento al final de la lista.
    - `RemoveAt(int index)`  
        - Remueve un elemento en el índice dado.
    - `Sort()`  
        - Ordena los elementos de la lista.
    - `Capacity`  
        - Obtiene el número de elementos que la lista puede tener antes de
        cambiar de tamaño.
    - `Clear()`  
        - Remueve los elementos de la lista.
    - `TrimExess()`  
        - Pone la capacidad de la lista a el número actual de elementos, útil
        para reducir memoria.
    - `AddRange(IEnumerable coll)`  
        - Añade los elementos de una colección con los elementos del mismo tipo
        de la lista al final de esta.
    - `Insert(int i, T t)`  
        - Inserta el elemento t en el índice i.
    - `Remove(T t)`  
        - Remueve la primera ocurrencia de el elemento t en la lista.
        RemoveRange(int i, int count)  
        Remueve un rango de elementos de la lista.
    - `Contains(T t)`  
        - Retorna `true` si el elemento especificado existe en la lista.
    - `Reverse()`  
        - Invierte el orden de los elementos en la lista.
    - `ToArray()`  
        - Copia los elementos de la lista en un nuevo arreglo.

### `SortedList`

- Es una colección de valores tipo llave/valor.
  - Son ordenados por la llave.
  - La llave puede ser usada para acceder al valor.
- Requiere que los elementos llave/valor sean del mismo tipo.
- Las llaves no pueden repetirse.
- Incluye los siguientes métodos.

### `BitArray`

- Son una colección de bits.
  - Sus valores pueden ser 0 o 1.
- Normalmente son usados para representar un grupo de banderas
  booleanas.
- Contiene las siguientes propiedades y métodos:
    - `Count`  
        - Obtiene el número de bits en el arreglo.
    - `IsReadOnly`  
        - Obtiene un valor indicando si el `BitArray` es de solo lectura.
    - `SetAll(bool value)`  
        - Pone todos los valores del arreglo en un valor especifico.
    - `And(BitArray ba)`  
        - Aplica un `and` al `BitArray` dado con el valor `ba`.
        - También puedes hacer `Or, Xor`.
    - `Not()`  
        - Invierte los valores del `BitArray`.
- Los `BitArray` pueden usarse para el procesamiento de imágenes.

## `Stack` y `Queue`

- Una pila (stack) es una lista tipo **last in, first out** (LIFO).
- Insertar un elemento a un stack es llamado `pushing`.
- Quitar un elemento del stack es llamado `pop`.
  - Esto solo puede hacerse en la parte superior del stack.

## `HashSet`

- Es un conjunto de valores únicos.
- Estos son diferentes a otras colecciones porque solo son un conjunto
  de valores, no tienen índice.

> Los HashSet proveen un alto rendimiento, en la búsqueda, adición y
> eliminación de elementos, puede ser usada para implementar otras
> estructuras de datos.
