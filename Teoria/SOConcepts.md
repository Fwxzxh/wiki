---
title: Conceptos de Sistemas operativos
description: Breves explicaciónes sobre algunos conceptos de sistemas operativos
published: true
date: 2023-04-22T06:38:29.299Z
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
> un hilo es una entidad dentro de un proceso que puede ser agendado (scheduled) para su ejecución, todos los hilos de un proceso comparten su espacio de direcciones virtual y sus recursos del sistema.

![processwthreads.png](/teoria/conceptos_so/processwthreads.png){.align-center}

## Handles