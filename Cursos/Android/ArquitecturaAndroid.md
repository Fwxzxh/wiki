---
title: Arquitectura de Software en Android
description: Repaso sobre algunos patrones de arquitectura en android
published: true
date: 2022-12-25T00:28:22.833Z
tags: mvvm, android, mvc, arquitectura
editor: markdown
dateCreated: 2022-12-25T00:28:17.365Z
---

# Arquitectura de Software

## Arquitectura en Android

- Deuda técnica
  - Esfuerzo adicional causado por la elección de un desarrollo
    sencillo.
- Las aplicaciones deben ser:
  - Rápidas.
  - Fluidas.
  - Seguras.
  - Mantenibles.
- Necesitamos una buena arquitectura para cumplir los puntos anteriores.

## Patrón de diseño VAS Arquitectura de diseño

- Patrón de diseño.
  - Solución a un problema común de código.
  - Solo se refiere a un componente o elemento de la aplicación.
  - Ejemplos:
    - `Singleton`.
    - `Adapter`.
    - `Builder`.
    - `Factory`.
- Arquitectura de diseño.
  - Proporciona la estructura, funcionamiento e interacción entre las
    partes del software.
  - La organización y estructura de la aplicación.
  - Ejemplos:
    - `MVC: Model-View-Controler`.
    - `MVP: Model-View-Presenter`.
    - `MVVM: Model-View-ViewModel`.

## Qué es la Arquitectura de diseño

- Se encarga de la Estructura, funcionamiento e Interacción de las
  partes del software.
- El modelo de capas:
  - `UI`
    - La presentación.
    - `FrontEnd`.
  - `Business Logic`
    - Las reglas de negocio.
    - Casos de uso de la aplicación.
    - Qué, como y cuando de la aplicación.
  - `Data`
    - Persistencia y/o procesamiento de la información.
- Arquitecto de software:
  - Analiza
  - Planea con anticipación.
  - Toma decisiones para evitar riesgos.
  - Tiene una amplia experiencia resolviendo problemas.
- Organiza mejor el código para trabajar en equipo.
- Hace el código más intuitivo de leer y de escribir.
- Hace más fácil testear e integrar nueva funcionalidad.

## Principios `SOLID`

- `S`: `Single Responsability`.
  - Cada clase debe de tener una sola responsabilidad.
  - Esto nos ayuda a modularizar el código.
  - Facilita cambiar funcionalidades.
- `O`: `Open/Closed Principle`
  - Organizar el código modularmente.
  - Las clases, módulos, interfaces deben de estar abiertas para la
    extensión pero no para la modificación.
  - Nos permite componer las clases.
  - Composición \> Herencia.
- `L`: `Liskov substitution`
  - Deberíamos de poder usar una clase hija para sustituir una clase
    padre sin errores.
- `I`: `Interface Segregation`
  - Si una interfaz crece demasiado viola el primer principio.
  - Usar Clases abstractas e interfaces para que cada interfaz cumpla el
    primer principio.
- `D`: `Dependency Inversion`
  - Inversión de dependencias.
  - Un elemento debe de depender de una abstracción y no de algo
    concreto.
  - Un módulos de alto nivel no debe depender de los de bajo nivel.
    ambos deben de depender de abstracciones.
    - P. Ej: interfaces.
  - Las abstracciones no deberían depender de los detalles.
    - Son los detalles los que deberían depender de abstracciones.
  - Los módulos no deben de depender unos de otros, si no de
    abstracciones.

## Evolución de arquitectura en Android

- MVC
- MVP
- MVVM
- Android Jetpack: arquitectura por componentes

# Arquitectura MVC

## Qué es la arquitectura Model-View-Controler

- `View`
  - La UI.
- `Controler`
  - Lógica de negocio.
  - Casos de uso.
- Ambos el `View` y el `Controler` están en la misma clase
- `Model`
  - Contenido en una clase aparte.
  - Conexión a almacenamiento.

# Arquitectura MVP

## Qué es la arquitectura Model-View-Presenter (MVP)

- Ayuda a no recargar de código la `MainActivity` y las clases de las
  `activity`.
- `View`
  - Activity
  - Fragment
  - UI en general
- `Presenter`
  - Orquesta lo que la vista pide.
  - Es un intermediario entre el `model` y el `view`.
  - Cada activity tiene su propio presenter.
- `Model`
  - `Interactor`
    - Decide de donde sacar los datos.

## Qué es clean architecture

- Hacen referencia a buenas prácticas de diseño y arquitectura que se
  aplican a ciertos elementos.
- Tiene como objetivo separar el código en sus diferentes
  responsabilidades.
  - `Presentation layer`
  - `Business logic layer`
  - `Data layer`
- Tiene 5 principios:
  - Independiente de cualquier Framework.
  - Testeadle.
  - Independiente de la UI.
  - Independiente de la base de datos.
  - Independiente de cualquier elemento externo.
- Sus elementos son:
  - `Entities`
    - Modelos definidos que interactúan en el sistema.
    - Deben ser lo suficientemente abstractas para ser usadas por
      múltiples aplicaciones.
  - `Use cases`
    - Contienen reglas que le dan sentido a la aplicación.
    - Dirijan el flujo a las entidades y las orquestan para cumplir con
      el negocio.
  - `Repositiories y Presenters`. `Interface adapters`
    - Esta es la capa interceptora que convierte los datos extraídos por
      la UI a un formato más conveniente para los casos de uso.
  - `UI`, `Data source`, `Frameworks` y `Drivers`
    - En esta capa van todos los detalles, tanto para mostrar datos en
      la UI como para obtener los datos requeridos.

## Composición de clases

- Composición \> Herencia.
- Componemos los comportamientos en interfaces y se los vamos dando a
  las clases que deseamos.
- Abstraemos funcionalidades mediante una interfaz.
  - con esto podemos reutilizar el comportamiento de una interfaz.

## Model-view-Presenter explicado

- `View`
  - `MainActivity.kt`.
    - Necesita una instancia de `CouponsPresenterImpl`.
- `Presenter`.
  - `CouponsPresenterImpl.kt`.
    - Tiene contacto bidireccional con `MainActivity.kt`.
    - Ocupa:
      - `CoupounsView`.
        - Para comunicarse con el `View`.
      - `CoupunsInteractor`.
- `Model`.
  - `Interactor`.
  - `CouponsInteractorImpl.kt`
  - Tiene contacto unidireccional con `CouponsPresenterImpl.kt`.
  - Solo el presenter tiene contacto con el `interactor`.
  - `RepositoryAPI`.
    - Obtiene los datos a través de una API.
    - `CouponsRepositoryImpl.kt`.

# Arquitectura Model-View-ViewModel

## Qué es la arquitectura Model-View-ViewModel

- `View`
  - `Activity/Fragments`
  - El view manda los datos al `ViewModel`.
  - Usa `DataBinding` para comunicarse con el `ViewModel`.
    - También podemos usar `LiveData`.
    - O `RxJava`.
- `ViewModel`
  - `ViewModel`
  - Tiene comunicación con el `Model`.
- `Model`
  - `Repository`
    - Es de donde sacamos los datos ya sea una API o una BD.

## `Data Binding`

- Usa `AndroidX`
  - `Android Extencion Library`
- `View`
  - `Activity/XML`
  - Usa `DataBinding` Para comunicarse con el `ViewModel`.
    - `@{  }`
      - `Binding Expresion`.
    - Debemos habilitar el `dataBinding` en `build.gradle`.
- `ViewModel`
  - Permite la comunicación entre las otras dos capas.
  - Necesitamos heredar de la clase `ViewModel()` perteneciente a
    `androidx`.
- `Model`
- Debemos Hacer la migración a `AndroidX`.

## Patrón `observer` en `MVVM`

- Se da cuanto tenemos un elemento que contiene una lista de elementos.
  - Se le llama `subject` o sujeto.
  - El cual contiene una lista de `observers`.
    - Tiene un método llamado `observer`
    - Permite hacer cosas cuando los elementos de la lista son
      modificados.
  - Parecido a la `observableCollection` de C#.

# JetPack

## Android `JetPack`

- Acelera el desarrollo de android con componentes.
- Componentes:
  - Base.
  - Comportamiento.
  - Arquitectura.
  - UI.
- Esta basado en `MVVM`.
- Usa:
  - `Room`
    - es un ROM.
  - `Lifecycle`
  - `LiveData`
  - `ViewModel`

## Arquitectura por componentes.

- Es una forma de organizar el código deacuerdo a su función.
- Utiliza los principios de `MVVM`.
- Usan:
  - `LiveCycle`
    - `LiveCycleOwner`
      - Tiene ciclo de vida.
    - `LiveCycleObserver`
      - Observa el ciclo de vida.
    - Los `Activity` y los `Fragment` tienen ciclos de vida.
      - También llamados `Events`.
      - `OnCreate`
      - `OnStart`
      - `OnPause`
      - `OnResume`
      - `OnDestroy`
      - etc.
      - Delegan un estado (`State`).
    - Entonces el `LiveCycleObserver` pueden observar el cambio de
      estado de un `Activity`.
  - `LiveData`
    - Depende totalmente del `LiveCycle`.
  - Ambos basados en el patrón `observer`
  - Nos permiten estar al tanto cuando un elemento cambia, pudiendo
    hacer cosas cada que cambien los elementos.
  - `ViewModel`
    - Debemos tener una clase que hereda de `ViewModel`.
    - Provee los datos de la UI.
    - Sobrevive a cualquier cambio del ciclo de vida de la `Activity`.
    - Funciona como un observador de la UI.
