---
title: Flutter
description: Notas varias sobre flutter
published: true
date: 2022-12-25T18:01:37.856Z
tags: android, movil, ios, flutter, dart
editor: markdown
dateCreated: 2022-12-25T18:01:32.795Z
---

# Interfaz de usuario

## Introducción a los widgets

- Los `widgets` se inspiran de `react`.
- Se construye la `UI` a partir de `widgets`.
  - Estos describen como se deben ver, su configuración y estado.
  - Cuando el estado de uno de estos `widgets` cambia este se
    reconstruye.
    - El `widget`, reconstruye su descripción y hace un `diff` para
      determinar los cambios mínimos que se tienen que hacer a este.

### Hola mundo

``` dart
import 'package:flutter/material.dart'

void main() {
  runApp(
    const Center(
      child: Text(
        'Hello, world!',
        textDirection: TextDirection.ltr
      ),
    ),
  );
}
```

- La función `runApp()` toma el widget dado y lo hace la raíz del árbol
  de widgets.
- EL árbol de widgets en este caso consiste de dos:
  - El widget `Center().`
  - Su hijo (child) el widget `Text()`.
- El `framework` obliga al widget raíz a cubrir la pantalla entera.
  - Por lo tanto el mensaje termina centrado en la pantalla.
- el atributo `textDirection` necesita ser especificado en esta
  instancia.

Cuando se escribe una aplicación flutter, generalmente creamos nuevos
widgets, los cuales son subclases de las clases `StatelessWidget` o
`StatefulWidget`.

- El trabajo principal de un widget es implementar una función
  `build()`.
  - Esta describe el widget en términos de otros widgets de más "bajo
    nivel".
- El `framework` construye estos widgets hasta que llega al final de la
  jerarquía.
  - esto en los clientes que representan el `RenderObject`.
    - El cual se encarga de describir la geometría del widget.

### Widgets Básicos

- `Text`
  - Nos permite crear una serie de texto en su aplicación.
- `Row`, `Column`
  - Nos permiten crear layouts flexibles en dirección horizontal (`Row`)
    y vertical (`Column`).
  - Esta basado en `flexbox`.
- `Stack`
  - No es linearmente orientado (ni Horizontal y vertical).
  - Nos permite poner widgets uno encima del otro, en orden de dibujado.
  - Podemos usar el widget `Positioned` en un `chidren` de algún widget
    para darles posición
    - Posición relativa al `stack`.
    - Esta basado en la posición absoluta del desarrollo web.
- `Container`
  - Nos permite crear un elemento visual rectangular.
  - Estos pueden ser decorados con `BoxDecorator`.
    - `Background`, `Border`, `shadow`.
  - También puede tener `margins`, `padding`, y `constraints`.
  - También puede ser transformada en un espacio tridimensional usando
    una matriz.

``` dart
import 'package:flutter/material.dart';

class MyAppBar extends StatelessWidget {
  const MyAppBar({required this.title, super.key});

  // Fields in a Widget subclass are always marked "final".

  final Widget title;

  @override
  Widget build(BuildContext context) {
    return Container(
      height: 56.0, // in logical pixels
      padding: const EdgeInsets.symmetric(horizontal: 8.0),
      decoration: BoxDecoration(color: Colors.blue[500]),
      // Row is a horizontal, linear layout.
      child: Row(
        // <Widget> is the type of items in the list.
        children: [
          const IconButton(
            icon: Icon(Icons.menu),
            tooltip: 'Navigation menu',
            onPressed: null, // null disables the button
          ),
          // Expanded expands its child
          // to fill the available space.
          Expanded(
            child: title,
          ),
          const IconButton(
            icon: Icon(Icons.search),
            tooltip: 'Search',
            onPressed: null,
          ),
        ],
      ),
    );
  }
}

class MyScaffold extends StatelessWidget {
  const MyScaffold({super.key});

  @override
  Widget build(BuildContext context) {
    // Material is a conceptual piece
    // of paper on which the UI appears.
    return Material(
      // Column is a vertical, linear layout.
      child: Column(
        children: [
          MyAppBar(
            title: Text(
              'Example title',
              style: Theme.of(context) //
                  .primaryTextTheme
                  .headline6,
            ),
          ),
          const Expanded(
            child: Center(
              child: Text('Hello, world!'),
            ),
          ),
        ],
      ),
    );
  }
}

void main() {
  runApp(
    const MaterialApp(
      title: 'My app', // used by the OS task switcher
      home: SafeArea(
        child: MyScaffold(),
      ),
    ),
  );
}
```

Asegúrate de tener `uses-material-design: true` en el archivo
`pubsec.yaml` para usar los iconos de `material design` por defecto.

Muchos widgets de `material design` deben de estar dentro de un
`MaterialApp` para que funcionen de manera correcta y para heredar la
información del tema, por lo tanto debemos de correr la aplicación
dentro de un widget `MaterialApp`.

- El widget `MyAppBar` crea un `container` con una altura de 56 píxeles
  (independientes del dispositivo), con un `padding` de 8 pixeles, en la
  izquierda y derecha.
- Dentro del `container` usamos un `row` `layout` para organizar sus
  widgets hijos.
  - El widget de en medio está marcado como `Expanded` esto para que
    utilice todo el espacio sin usar por otros widgets.
  - Podemos tener múltiples widgets `Expanded`, y de terminar el ratio
    en el que consumen el espacio usando el argumento `flex` para
    `Expanded`
- El widget `MyScaffold` organiza sus hijos en una columna vertical.
  - En la parte superior de la columna coloca una instancia del widget
    `MyAppBar`.
    - Pasando a este un widget `Text` para que use como su titulo.
      - Pasar widgets como argumento a otros widgets nos permite crear
        widgets genéricos que pueden ser reutilizados de muchas maneras.
  - `MyScaffold` usa `Expanded` para llenar el espacio restante en su
    cuerpo, que consiste de un mensaje centrado.

## Usando componentes material

- Flutter provee widgets que nos ayudan a construir apps que siguen el
  estilo material.
- Las apps con `material design` empiezan con un widget `MaterialApp`.
  - Este widget construye otros widgets útiles como `Navigator`.
    - Este maneja un `stack` de widgets identificados con `strings`, los
      cuales llamamos rutas.
    - Nos permite navegar entre las diferentes ventanas de nuestra
      aplicación.
  - Usar el widget `MaterialApp` es opcional pero buena práctica.

``` dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    const MaterialApp(
      title: 'Flutter Tutorial',
      home: TutorialHome(),
    ),
  );
}

class TutorialHome extends StatelessWidget {
  const TutorialHome({super.key});

  @override
  Widget build(BuildContext context) {
    // Scaffold is a layout for
    // the major Material Components.
    return Scaffold(
      appBar: AppBar(
        leading: const IconButton(
          icon: Icon(Icons.menu),
          tooltip: 'Navigation menu',
          onPressed: null,
        ),
        title: const Text('Example title'),
        actions: const [
          IconButton(
            icon: Icon(Icons.search),
            tooltip: 'Search',
            onPressed: null,
          ),
        ],
      ),
      // body is the majority of the screen.
      body: const Center(
        child: Text('Hello, world!'),
      ),
      floatingActionButton: const FloatingActionButton(
        tooltip: 'Add', // used by assistive technologies
        child: Icon(Icons.add),
        onPressed: null,
      ),
    );
  }
}
```

Ahora que usamos los componentes `AppBar` y `Scaffold` en lugar de
nuestros widgets custom `MyAppBar` y `MyScaffold`. nuestra app va a
utilizar los estilos de `material design` además de que agregamos un
`floatingActionButton`.

> Material es uno de los dos estilos que incluye flutter, para crear
> apps con estilo IOS utilizamos componentes `Cupertino`, ya como
> `CupertinoApp` o `CupertinoNavigator`.

- El widget `Scaffold` toma una serie de diferentes widgets como
  argumentos con nombre.
  - Cada uno toma lugar en el layout del `Scaffold` en el lugar
    asignado.
- De manera similar el widget `AppBar` nos deja darle widgets para la
  posición `leading`, `actions` y `title`.

## Manejando Gestos

El primer paso para construir una aplicación interactiva es detectar
gestos.

``` dart
import 'package:flutter/material.dart';

class MyButton extends StatelessWidget {
  const MyButton({super.key});

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () {
        print('MyButton was tapped!');
      },
      child: Container(
        height: 50.0,
        padding: const EdgeInsets.all(8.0),
        margin: const EdgeInsets.symmetric(horizontal: 8.0),
        decoration: BoxDecoration(
          borderRadius: BorderRadius.circular(5.0),
          color: Colors.lightGreen[500],
        ),
        child: const Center(
          child: Text('Engage'),
        ),
      ),
    );
  }
}

void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: Center(
          child: MyButton(),
        ),
      ),
    ),
  );
}
```

a
