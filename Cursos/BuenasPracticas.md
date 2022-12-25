---
title: Buenas Practicas en el código
description: Breve introducción sobre las buenas prácticas en el código
published: true
date: 2022-12-24T17:11:12.731Z
tags: cursos, buenas practicas, solid, programacion
editor: markdown
dateCreated: 2022-12-24T17:11:08.232Z
---

# Ejes que hacen la calidad del código

Características internas (que solo ve el programador)

**Legibilidad**
¿Que tan fácil es interpretar lo que el código hace.

**Mantenibilidad**
Cuanto esfuerzo supone adaptar el código a nuevos requerimientos.

**Testeabilidad**
Cuanto esfuerzo supone realizar pruebas a el código.

# Código legible

- Define un estándar(o usa uno) y respétalo.
- Apóyate con un *linter*.
- Genera código claro y consistente.
- Identificadores mnemotématicos, específicos y precisos.

# Código mantenible

- Código modular.
  - Encapsular los procesos y decisiones del programa en métodos y
    funciones.
- Código reutilizable.
  - Funciones que hagan solamente una cosa.
  - No repitas código, haz una función.
- Código organizado.
  - Usa nombres de archivos con sentido.

# Código libre de vicios

- Evitar el hardcoding, usar identificadores siempre.
- Evitar efectos colaterales.
  - Se refiere a efectos que suceden más allá del código que se esta
    leyendo.
  - Evita variables globales.

# Conocer Principios SOLID

- SOLID significa:
  - (S) Single Responsability Principle.
    - Una clase solo debe de tener un objetivo.

  - (O) Open/Closed Principle.
    - Una entidad de software debe de estar abierta para su extención y
    cerrada para su modificación.

  - (L) Liskov Substitution Principle.
    - Establece que cada clase que hereda de otra puede usarse como su
    padre sin necesidad de conocer las diferencias entre ellas.

  - (I) Interface Segregation Principle.
    - Establece que los clientes del programa solo deberían conocer de
    éste los métodos que realmente usan.

  - (D) Dependency Inversion Principle.
    - Los modulos de alto nivel no deben depender de los de bajo nivel,
    ambos deben de depender de abstracciones.

# Patrones de diseño y su aplicación

- Son soluciones conceptuales que se pueden aplicar a la hora de diseñar
  las clases.
- tres tipos
  - Creación 
    - Nos dice como se crean nuevas instancias de los objetos.
  - Estructurales
    - Nos dicen como debemos de estructurar nuestras clases.
  - Comportamiento  
    - Nos dicen como deben de comportarse nuestros objetos.
- No siempre son aplicables, pero nos ayudan a pensar desde una hoja en
  blanco.
- Patrón Singlenton.
  - Creación/comportamiento.
  - Una clase que solo tenga una instancia al lo largo de toda nuestra
    aplicación.
  - Se utiliza para optimizar recursos.
- Patrón Factory
  - Creacional.
  - Se utiliza cuando la creación de un objeto es algo compleja.
- Patrón Command
  - Se utiliza cuando una operación compleja que debe de ser realizada
    desde diferentes puntos de entrada.
  - Permite solicitar una operación a un objeto sin conocer realmente el
    contenido de esta operación.

# Comprender las nociones del testing automático

- Testing manual, es costoso, lento y poco confiable.
- Testing automatizado, (escribes programas que puedan testear tu
  programa) es más barato, rápido y más confiable.
- Tipos de testing automatizado:
  - Unit Testing
    - Evaluamos el funcionamiento de los componentes individualmente.

  - Integration Testing  
    - Validar la integración entre los componentes y el sistema completo.
- Test Driven Development
  - Propone primero escribir las pruebas y después el software.
    1.  Escribimos un test que falle.
    2.  Hacemos que el código funcione con el test.
    3.  Eliminamos todo el código redundante y lo simplificamos pero
        siempre intentando pasar el test.
- Documentación
  - ¿Qué documentar?
    - Como implementar una nueva funcionalidad.
    - Como se realizan las pruebas.
  - ¿Como documentar?
    - UML como documentación.
  - ¿Donde documentar?
    - Propio código.
    - Sistema de documentación.
  - ¿Cuando documentar?
    - Documentar inmediatamente después de escribir código.
    - Cuando se resuelve un problema.
