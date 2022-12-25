---
title: Curso de Bases técnicas de android
description: 
published: true
date: 2022-12-24T19:31:55.809Z
tags: cursos, android
editor: markdown
dateCreated: 2022-12-24T19:31:50.749Z
---

# Android

## Introducción a android

- Sistema operativo basado en el kernel de Linux
- Creado por google.
- Código abierto.

## Retos de desarrollo en android

- Disponibilidad.
  - Las plataformas a las cuales queremos llegar.
  - Fragmentación de dispositivos.
  - Versionamiento de sistemas operativos.
  - DPIs de las pantallas.
- Rendimiento.
  - Consumo del CPU y uso de memoria.
- Calidad.
  - La aplicación haga lo que dice que hace.
  - Debemos de conocer bien el sistema operativo para evitar sorpresas.
  - Métricas de diseño.
  - Workflow.
  - Testing.

## Tipos de dispositivos Android y soporte

- Compatibilidad
  - Compatibilidad con el dispositivo.
    - Hay mucha variedad de hardware.
    - Características de hardware.
    - Versión de android.
    - Configuración de pantalla.
  - Compatibilidad con la aplicación.
  - Debemos especificar dos versiones de API con la aplicación.
    - `minSdkVersion`
      - La versión mínima de android que soportaremos.
    - `targetSdKVersion`
      - La versión objetivo de android que queremos soportar.

# Componentes de una aplicación

## `Activity`

- Es una pantalla de una aplicación.
- Se compone de:
  - Es una clase de java que herede de la clase `activity`.
  - El `layout` (La Interfaz gráfica).
- Ciclo de vida de una actividad.
  1.  La actividad es creada con el método `onCreate()`.
      - Recibe el estado de la actividad anterior como estado.
        - De tipo `Bundle`.
  2.  Pasamos al estado `Started` con el método `onStart()`.
      - Esto es cuando la actividad está por ser mostrada.
  3.  Llegamos al estado `Resumed` con el método `onResume()`.
      - Esto es cuando la actividad ya es visible.
  4.  Podemos llegar a un estado `Paused` con el método `onPause()`.
      - En este estado otra actividad tiene el focus de la aplicación.
  5.  Podemos llegar al estado `Stopped` con el método `onStop()`.
      - La actividad ya no es visible.
      - Esto pasa cuando por ejemplo presionamos el botón de home.
      - Podemos regresar de este estado a `Started` con el método
        `onRestart()`
  6.  Al final llegamos a el estado `Destroyed` con el método
      `onDestroy()`
      - Esto pasa cuando por ejemplo presionamos el botón de back en el
        dispositivo.

## `Fragments`

- Todas las aplicaciones tiene una barra inferior o una barra superior.
  - Funcionan a partir de un concepto llamado `fragments`.
    - Son un tipo de contenedor que tienen una parte de la FUI.
  - Usamos ciertas clases para manejarlos.
    - `FragmentManager`
      - Manejar los `fragments`
      - Junto con nuestra librería de soporte.
    - `Transacciones`
      - Todas las acciones que podemos realizar con los `fragments`
    - `Commits`
      - Cada que se hace una transacción, se hace un `commit`

## `Intent`

- Es muy común tener un flujo de navegación o de ventanas en una
  aplicación.
  - Es decir, más de una `activity` conectadas entre si.
- los `Intent` nos ayudan a unir los componentes de una aplicación.
- Podemos tener dos casos:
  - Unir varios `activity`.
    - Estos son `intent` explícitos.
  - Unir `activitys` que viven en diferentes aplicaciones.
    - `intent` implícitos.
- Todos los componentes de android están aislados.
  - Con los `intent` permitimos la comunicación entre diferentes partes
    de una apeo.

## `Services`

- Los servicios nos permiten hacer cosas cuando la aplicación no esta
  corriendo.
  - O para ejecutar tareas en segundo plano.
- Se arrancan a partir de las `activity`.
- Se crean con el método `onStartCommand()`.
- Tipos de servicios:
  - En primer plano:
    - Es un servicio que realiza una tarea que el usuario puede notar.
    - Estos continúan ejecutándose incluso si el usuario deja de
      interactuar con la aplicación.
  - En segundo plano:
    - Este realiza una tarea que el usuario no nota directamente.
    - Son servicios en segundo plano.
  - Enlace (`Bind`)
    - Podemos enlazar un servicio con `onBind()` y des enlazarlo con
      `onUnbind()`.
    - Un servicio es de enlace cuando un componente de la app se vincula
      a el con el método `bindService()`
    - Este ofrece una interfaz cliente-servidor que permite que los
      componentes interactúen con el servicio.
      - Permitiendo comunicación con distintos procesos (IPC).
    - Este solo se ejecuta mientras otro componente de la app este
      enlazado a el.

## `Broadcast`

- Transmisiones.
- Conocidos también como `broadcast receivers`
- Estos están siempre alerta a lo que pasa en el sistema operativo.
- archivo `Android Manifest`
  - Tiene declarado todo lo que tenga que ver con el sistema operativo.
  - La capa que tiene contacto con el dispositivo.
  - Si quiero que mi app tenga acceso a algo, el tiene que estar
    declarado aquí.
  - Es el puente entre tu aplicación y el hardware.
  - Aquí se definen los `broadcast`.
    - Aquí ponemos escuchas para diferentes eventos del dispositivo.
      - EJ: batería baja, Llamada entrante, Carga conectada, etc.
- Debemos heredar de la clase `broadcastReceiver`.

# Desarrollo

## Qué es y como funciona `gradle`

- Es una herramienta que facilita la construcción de aplicaciones.
- Genera el sistema de archivos del proyecto.
- Gestiona dependencias.
- Genera archivos ejecutables.
- Esta basado en el lenguaje `groovy`.
  - Es un lenguaje de dominio (un lenguaje diseñado para usarlo en un
    solo ámbito).
- archivo `build.gradle`
  - Dependencias del proyecto.
  - Compilación del código.
  - Empaquetado.

## Generación de un APK

- El compilador convierte el código a bytecode.
  - Este bytecode es diferente al que podrías encontrarte para java.
    - Tiene la extensión `.dex` en lugar de ser `.jar`.
- Gradle empaqueta los archivos `.dex` junto con todos los otros
  archivos que tu aplicación necesita.
  - Generando con esto un `.apk`.
- Gradle Firma este APK on una `key`.
- Los APK generados pueden ser de `debug` o de `release`.

## `Google Play Services`

- Google proporciona servicios como autentificación o analíticas.
  - Para esto ocupamos los servicios de google play.

# Almacenamiento

## Niveles de almacenamiento y tipos

- Almacenamiento Interno.
- Almacenamiento Externo.
- `Shared preferences`.
  - Modelo de datos primitivos con formato xml.
  - Vive en la APK.
- Bases de datos
  - Se pueden guardar dentro de la APK o dentro del almacenamiento.
- `WebService`.
  - Guardas datos en un servidor externo mediante internet.

## `File` y `shared preferences`

- File
  - Crea un archivo de cualquier tipo.
  - Trabaja con la clase `file`.
- `Shared Preferences`
  - Datos sencillos.
  - Funciona con XML.
  - Necesitamos una `key` y un valor.
    - En forma de pares.
  - Se almacena dentro de la aplicación.

## `Content Providers`, Bases de datos y `Network`

- Las bases de datos se utilizan con `sqlite`.
  - Estos datos viven hasta que la aplicación es desinstalada.
  - Solo son accesibles para la aplicación.
- `Content providers`.
  - Almacenamiento que pueden usar todas las apps.
  - Funcionan como una base de datos.
  - La aplicación de contactos funciona con esto.
- `Network`
  - Usamos una conexión a internet.
  - Mandamos los datos a un servidor remoto.
  - Siempre debe de estar conectado para tener persistencia.

# `Testing` y `UI Test`

- El `testing` es necesario para asegurar la calidad de tu aplicación.
- Hay diferentes tipos de pruebas:
  - Pruebas de unidad local (unitarias).
    - Son pequeños `tests` automatizados para probar pequeñas partes del
      código.
  - Pruebas instrumentadas.
    - Son pruebas donde integras los test anteriores.
    - Aquí testeamos que varios módulos funcionen bien en conjunto.
  - Pruebas de interfaz de usuario.
    - Se enfocan en el flujo de la interfaz de usuario.
    - Con esto nos aseguramos que las tareas que realizará el usuario
      funcionen como se esperan.
