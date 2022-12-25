---
title: Android Jetpack Compose
description: Breve curso sobre Jetpack Compose con Kotlin
published: true
date: 2022-12-24T20:27:24.439Z
tags: android, ui, kotlin, jetpack compose
editor: markdown
dateCreated: 2022-12-24T20:27:19.441Z
---

# Conceptos generales

## Introducción

- Porqué usar `compose`?
  - Apps con menos código.
  - Desarrollo intuitivos.
    - Es una API declarativa.
  - Acelera nuestro desarrollo.
    - Es compatible con el código existente.
  - Es más potente.
    - Tiene más compatibilidad con APIs de android.

## Qué es `Jetpack Compose`

- Es un kit moderno de herramientas declarativas.
- API declarativa para renderizar sin cambiar de vista.

## Programación declarativa para creación de UI

- Modelo de UI declarativo.
  - Regeneración conceptual de toda la pantalla.
    - Aplicando solo los cambios necesarios.
  - Evita la complejidad de la jerarquía de vistas.
  - Ejemplos declarativos de UI:
    - React.
    - Switft UI.
    - Fluter.
    - Compose.
  - Desafíos de regenerar toda la pantalla.
    - Tiempo.
    - Uso de batería.
    - Uso de CPU
  - Recomposición:
    - Vuelve a llamar a la función que admite composición con datos
      nuevos.
    - Los componentes de la función se vuelven a dibujar con datos
      nuevos.
    - Recompone de forma inteligente solo los componentes que cambiaron.

# UI Con `Jetpack Compose`

## Funciones `composable`

Son funciones que llevan un `decorator` con el la palabra `Composable`

``` kotlin
class MainActivity : ComponentActvity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            HelloCompose()
        }
    }
}

@Composable
fun HelloCompose() {
    Text("Hello Compose!")
}
```

Usando estas funciones podemos declarar UI, en el código anterior
creamos un elemento tipo `Text` el cuál tiene de valor
`"Hello Compose!"`

También podemos hacer preview de nuestros elementos con el `decorator`
`Preview`.

``` kotlin
@Preview(
    showBackground = true
)
@Composable
fun HelloComposePreview() {
    HelloCompose()
}
```

- El decorator `Preview` puede definir argumentos sobre como mostrar el
  preview en el editor.
- Es común usar (nombreDeElemento)Preview para Nombrar las funciones de
  preview.
- Si no declaramos un preview, no aparecerá la preview en el editor.

## Componentes principales y `layouts`

- Las funciones `Composable` funcionan como un `stack`.
  - Si ponemos dos componentes.
    - Como dos elementos `Text`.
  - Ambos se sobrepondrán en el mismo espacio.
  - Debemos darle jerarquía con layouts.

``` kotlin
@Composable
fun HelloCompose() {
    Column() {
        Image(painterResource(id  = R.Drawable.imagen), contentDescription = "logo")
        Text("Este curso es lo mejor!!")
        Text("Hello Compose!!")
        Button(
            onClic = {
                // La acción a hacer con el evento onClic
            }
        ) {
            Text("Precioname!")
        }
    }
}
```

En las funciones `Composable` podemos definir elementos de la UI y
agruparlos de la manera que deseemos.

## Componentes personalizados y `modifiers`

- Todos los elementos tienen `modifiers`.
- Estos nos permiten cambiar cosas como el tamaño, bordes, etc.
- También cada componente tiene argumentos personalizados de cada
  componente.
- De esta manera podemos estilizar mejor nuestros componentes.
- Podemos encadenar diferentes `modifiers` separandolos con un punto.

``` kotlin
@Composable
fun HelloCompose() {
    Card(
        elevation = 4.dp,
        shape = RoundedCornerShape(20.dp)
    ) {
        Column(
            modifier = Modifier.padding(8.dp).padding(16.dp)
            horizontalAlignmet = Alignment.CenterHorizontally
        ) {
            Image(painterResource(id  = R.Drawable.imagen),
                  contentDescription = "logo",
                  modifier = Modifier.size(40.dp, 40.dp)
            )
            Text("Este curso es lo mejor!!", style = MaterialTheme.typography.h4)
            Text("Hello Compose!!")
            Button(
                onClic = {
                    // La acción a hacer con el evento onClic
                }
            , modifier = Modifier.padding(top = 16.dp)) {
                Text(text = "Precioname!")
            }
        }
    }
}
```

## `Material design` con `Compose`

- `Jetpack Compose` nos provee con otra manera de manejar los temas.
- Dentro del proyecto tendremos una carpeta que se llama `ui.teme`.
  - En `Color.kt` declaramos los colores de nuestra aplicación
  - En `Shape.kt` podemos definir distintas formas.
  - En `Theme.kt` podemos definir diferentes temas para nuestra
    aplicación.
  - En `Type.kt` podemos definir las diferentes tipografías.
  - En el `Theme.kt` unimos todo lo de los archivos anteriores para
    crear un tema.
- En la el archivo `Theme.kt` viene una función `Composable`.
  - En esa función, que se llama `(NombreProyecto)Theme` se definen
    todos los aspectos del tema.
  - Si queremos usar ese tema u otro en nuestros elementos o de manera
    global debemos poner nuestros elementos dentro del bloque del tema.

``` kotlin
@Composable
fun HelloCompose() {
    HelloComposeTheme() { // <- Bloque del tema.
        Card(
            elevation = 4.dp,
            shape = RoundedCornerShape(20.dp)
        ) {
            Column(
                modifier = Modifier.padding(8.dp),
                horizontalAlignmet = Alignment.CenterHorizontally
            ) {
                Image(painterResource(id  = R.Drawable.imagen),
                    contentDescription = "logo",
                    modifier = Modifier.size(40.dp, 40.dp)
                )
                Text("Este curso es lo mejor!!", style = MaterialTheme.typography.h4)
                Text("Hello Compose!!")
                Button(
                    onClic = {
                        // La acción a hacer con el evento onClic
                    }
                , modifier = Modifier.padding(top = 16.dp)) {
                    Text(text = "Precioname!")
                }
            }
        }
    }
}
```

Para verlo en la preview y/o aplicar el tema de forma global debemos
encerrar nuestro bloque de tema dentro de las funciones pertinentes.

``` kotlin
// a nivel de preview
@Preview(
    showBackground = true
)
@Composable
fun HelloComposePreview() {
    HelloComposeTheme() {
        HelloCompose()
    }
}
```

``` kotlin
// A nivel global
class MainActivity : ComponentActvity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            HelloComposeTheme() {
                HelloCompose()
            }
        }
    }
}
```
