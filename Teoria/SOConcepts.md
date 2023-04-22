---
title: Conceptos de Sistemas operativos
description: Breves explicaciónes sobre algunos conceptos de sistemas operativos
published: true
date: 2023-04-22T21:48:48.191Z
tags: sistemas operativos
editor: markdown
dateCreated: 2023-04-22T06:38:29.299Z
---

# Conceptos dell sistema operativo Windows

## Procesos
> Una instancia de un executable en particular.

Es un contenedor que contiene todo lo necesario para que una aplicación pueda correr.

![process.png](/teoria/conceptos_so/process.png){.align-center}

Contiene:
- El código a ejecutar.
- Los archivos.
- Data necesaria
- Su stack y sus registros.
- También contiene sus Threads.


![memorylayoutwin.png](/teoria/conceptos_so/memorylayoutwin.png){.align-center}

> Memory layout in window.

Una aplicación puede lanzar diferentes procesos y estos correr independientemente uno de otro, y estos a su vez crear más procesos "hijos".

> Chrome va a lanzar un nuevo proceso por cada tab que abras.

Un proceso típicamente no tiene contexto ni conocimiento de los otros procesos corriendo en la computadora.
> En mayor parte piensa que es el único proceso corriendo en la computadora.

Cada proceso tiene su propio *Virtual Address Space*.
- El cual piensa que es unicamente asignado para el.


Los procesos son a veces vistos como programas en si, pero esto no es cierto, generalmente un programa o aplicación contiene muchos procesos por detrás.

> Hay 3 tipos de procesos en Windows.
> - Application Process
>   - Si una aplicación tiene una ventana visible.
> - Windows Process
>   - Si el proceso esta marcado como *critical*.
> - Background Process
>   - los que no cumplen con cualquiera de las dos condiciones anteriores.

Los procesos también tienen una prioridad.
- Esta los diferencia entre uno y otro.
- Esto es para darle más o menos tiempo en el CPU.
- Si el proceso esta en prioridad Low.
  - Solo se le da tiempo en el CPU cuando nadie lo esta utilizando.
- Si el proceso esta como RealTime.
  - Se le dan acceso prioritario al CPU.
    - Dado por el sistema de Scheduling.
  - Lo cual no siempre es una buena idea.
- Estos además tienen:
  - PID.
  - El path del ejecutable (image path).
  - Los procesos reciben memoria virtual.

![memoryaddress.png](/teoria/conceptos_so/memoryaddress.png){.align-center}

> Virtual memory.

Cada proceso es iniciado con un solo hilo, También llamado *primary thread*.

## Hilos
> Un hilo es una entidad dentro de un proceso que puede ser agendado (scheduled) para su ejecución, todos los hilos de un proceso comparten su espacio de direcciones virtual y sus recursos del sistema.

![processwthreads.png](/teoria/conceptos_so/processwthreads.png){.align-center}

Un proceso puede tener multiples hilos, los cuales se encargan de diferentes tareas dentro de un proceso.

Esto es llamado multithreading y es bastante común en aplicaciones modernas ya que provee:
- Responcividad.
- Mejor utilización de recursos.
- Multiples tareas en paralelo.
- etc.

![procsvsthread.png](/teoria/conceptos_so/procsvsthread.png){.align-center}


Los procesos pueden además crear hilos adicionales desde cualquiera de sus hilos.

> Los hilos son unidades de ejecución.

> Los hilos son Lightweight y los procesos no. toma más tiempo hacer cosas con un hilo que con un proceso.

A diferencia de los procesos, los hilos son dependientes de su proceso padre y comparten recursos con el.

Los hilos también tienen IDs, Handles, etc.

## Handles
> Unidad genérica de identificación, nos permite interactuar con el sin acceder directamente a sus direcciones de memoria.

Hay handles a procesos y a hilos

