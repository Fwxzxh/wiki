---
title: Introducción al desarrollo backend
description: Apuntes sobre el desarrollo backend
published: true
date: 2022-12-25T00:47:58.746Z
tags: cursos, backend
editor: markdown
dateCreated: 2022-12-25T00:47:53.748Z
---

# Fundamentos del desarrollo Web

## Frontend y Backend

- Frontend
  - Se puede hacer con:
    - HTML
    - CSS
    - JavaScript
  - Es la cara visible de la aplicación
  - También tenemos Librerías y frameworks para facilitar tareas.
  - Empieza con el diseño de la aplicación.
    - UI/UX
- Backend
  - La lógica de la aplicación.
  - Se puede hacer con la mayoría de los lenguajes populares.
    - Estos tienen sus frameworks/librerías para facilitar tareas.

## Framework vs librería

- librería.
  - Código hecho por otra persona para hacer algo.
- Framework.
  - Es un marco de trabajo, conjunto de reglas para hacer algo.
  - Podrían definirse como un conjunto de librerías.

## Cómo se conecta el frontend con el backend

- Se usan las API.
  - Application Programming Interface
  - Nos permite que el frontend y el backend se comuniquen.
- Hay dos estándares.
  - SOAP
    - `Simple Object Acces Protocol`
    - Mueve la información con XML.
  - REST
    - `Representational state transfer`
    - Mueve la información con JSON.

## HTTP: el lenguaje que habla internet

- `Hypertext Transfer Protocol`
- Cliente y Servidor.
- Es un protocolo.
  - Es un conjunto de reglas.
- Tenemos una `request` y una `response`
  - Ambos hablan HTTP.
  - Tienen cabeceras.
    - Piezas de información.
  - Tenemos diferentes métodos para mandar la información.
- Códigos de estado:
  - 1xx : mensaje informativo.
  - 2xx : éxito.
  - 3xx : Redirección.
  - 4xx : Error del cliente.
  - 5xx : Error del servidor.

## El servidor:

- también llamado la nube.
- es una computadora que contiene una aplicación y la distribuye en
  internet.
  - Y nos permite mediante HTTP traer la aplicación a mi computadora
    (cliente).
- `IaaS`
  - Infraestructura como servicio.
  - Nos prestan el hardware que necesitemos.
    - Tenemos que gestionarlo.
  - Ejemplos: AWS, Azure, Digital Ocean
  - Dos tipos:
    - `VPS`:
      - `Virtual private server`
      - Un solo servidor dedicado para tu aplicación.
    - `Shared Hosting`
      - Se comparten los recursos del servidor entre varios clientes.
- `PaaS`
  - Plataforma como servicio.
  - Nos permite elegir que cosas necesita nuestra aplicación para
    funcionar.
  - Solo hacemos deploy.
  - Ejemplos: Google AppEngine, Firebase, Heroku.
- `SaaS`
  - Software como servicio.
  - Nos prestan el software.
  - Generalmente son `no code`.
  - Ejemplos: Google Docs, Slack, WordPress.

# Diseño de una API

## Diseño y bosquejo de API:

- `Twitter clone`.
- En python tenemos 3 opciones:
  - FastApi.
  - Django.
    - Con el rest framework.
  - Flask.
- `EndPoint` o Ruta o `Path`.
  - Es una sección de la URL del proyecto
  - En este caso `HTTP://twiter.com/[endpoint]`.
  - Nuestra aplicación tendrá el `EndPoint` base `/api/`

## Diseñando los `endpoints` de los tweets

- CRUD.
  - Create
  - Read.
  - Update.
  - Delete.
- `EndPoints`
  - `/tweets`
    - Muestra todos los tweets.
    - Read
  - `/post`
    - Publica un tweet.
    - Create
  - `/tweets/{tweetId}`
    - Muestra un tweet.
    - Read.
  - `/tweets/{tweetId}/update`
    - Edita un tweet.
    - Update.
  - `/tweet/{tweetId}/delete`
    - Borra un tweet.
    - Delete.

## Diseñando los `EndPoints` para los usuarios

- Modelos
  - Son tipos de datos en particular que voy a usar en la aplicación.
    - Usuarios
    - tweets
  - Corresponden a una o más tablas de SQL
- Cada uno de los endpoints nos va a dar un JSON.
- `/users`
  - Muestra todos los usuarios.
  - Read
- `/signup/`
  - nos permite registrar un usuario.
  - Create
- `/users/{userId}`
  - mostrar un usuario.
  - Read
- `/users/{userId}/update`
  - Actualizar un usuario.
  - Update
- `/users/{userId}/delete`
  - Borra un usuario.
  - Delete.

## aa
