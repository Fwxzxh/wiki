---
title: Curso de principios de visualización de datos para Business Intelligence
description: 
published: true
date: 2022-12-26T08:50:07.190Z
tags: cursos, data science, visualización
editor: markdown
dateCreated: 2022-12-25T06:56:13.447Z
---

**Recursos:** [Catalogue Data
Visualization](https://datavizcatalogue.com/ES/index.html)

# Fundamentos de la visualización de datos

## Qué es la visualización de datos?

- **Son representaciones simbólicas de conceptos complejos**.
- Input:
  - Es donde iniciamos el proceso de visualización de datos.
- Output:
  - Nos ayuda a representar los datos de manera visual.
  - Para reconocer fácilmente patrones.
  - Al usar más de un sentido podemos facilitar el entendimiento de los
    datos.
- Estamos en la era de información, así que hay más datos que nunca.

## Importancia de la visualización de datos

- **Reduce la carga cognitiva para retener y entender los datos**.
- Nos ayuda a entregar un mensaje de una manera clara y eficiente.

> Visualization gives you answers to questions you didn't know you had.

- Nos ayuda a comunicar mejor a una audiencia.

## Buenas prácticas para visualización de datos

- Define una audiencia y un motivo (mensaje).
- Utiliza la percepción visual.
  - Para disminuir la carga cognitiva.
- Estandarizar.
  - Utilizar medidas.
  - No cortar los axis.
  - Alinear todo siempre.
  - Todo para evitar confundir los números.
- Simplificar pero no recortar.
- Disminuir el sesgo (bias), no `cherry-picking`.
- Principios [Gestalt](/Cursos/Diseno/IntroduccionDiseno)

## Conflictos de ética en la ciencia de datos y `Big data`

- Nuestro papel ante la audiencia es evitar el sesgo y el bias en la
  visualización.
- Siempre el mensaje debe de ser sin preferencias personales.

# Elige la gráfica correcta para tus reportes

- `Data viz` es el termino con el que se refiere a una representación
  gráfica

## Gráfica de barras

- Existen verticales, horizontales y stackeadas.
- Debemos usar un color distinto para cada categoría
- Debemos representar las cosas de menor a mayor.

## Gráfica de pie

- Para menos de 6 categorías de preferencia para mantener la claridad.
- No usar gráficas en 3D porque afectan la visualización.
- Pueden ser de pie o de dona.
- Si no se alcanza a ver las diferencias entre categorías, procurar usar
  otro tipo de gráfica.

## Gráfica de dispersión (scatter plot)

- los colores son importantes.
- Necesitamos buscar correlaciones ya sea positiva o negativa o que no
  haya alguna.
- Tener cuidado al poner anotaciones para que no dificulte la lectura
  del gráfico.

## Gráfica de Burbujas

- El tamaño de la burbuja nos puede mostrar una variable más para la
  visualización.
- Pueden ser como una gráfica de dispersión o solo usar el tamaño de la
  burbuja para denotar una cantidad.
- Tener cuidado con el tamaño de las anotaciones.
- Colores diferentes.
- No gráficos 3D.

## Gráfica de mapas

- Es una representación gráfica de datos ubicados geográficamente.
- Puede ser complicado para ubicar los datos.
- Los mapas pueden ser una representación sencilla y no tan precisa.

## Tipos de mapas:

### Mapas de Isolíneas

- Utilizan líneas para pode unir áreas que determinen cierta similitud.
  - Estos espacios suelen colorearse para mostrar distinción entre
    ellos.
- Son muy utilizados en el aspecto metereológico.
- [Ejemplos](google:Mapas+de+Isolíneas&sourceid=chrome&ie=UTF-8)

### Mapas Coroplágticos

- Son mapas que representan con color los lugares donde ocurrieron
  ciertos sucesos.
- [Ejemplo](google:Mapas+Coropléticos&sourceid=chrome&ie=UTF-8)

### Mapas de diagramas

- Estos pueden considerarse mapas combinados, ya que por lo general
  utilizan el color para hacer una distinción variable y alguna otra
  visualización.
- Son utilizados en estadística, geografía, reportes económicos, salud,
  etc.

### Mapas Antártico

- Utilizan distintos tipos de figuras geométricas para identificar
  sucesos en determinadas ubicaciones.

## Gráfica de `heap map`

- Nos permiten sobreponer una paleta de colores para representar la
  frecuencia de los datos que queremos representar.
- Nos permite ver las zonas en las que más se repiten nuestros datos.
- Debemos estar al pendiente de la calibración de la paleta de colores.
  - Debe de ser clara para representar los cambios de frecuencia.

## Gráfica de tablas

- Se utiliza junto con otro elemento de data visualización.
- No utilizar datos extensos ya que afecta la claridad y la carga
  cognitiva.
- Podemos utilizar colores para denotar ciertos valores.

## Importancia del storytelling en la visualización de datos

- El storytelling es la técnica de comunicación en la cual hilamos
  historias para comunicar un mensaje.
- Nos ayuda a retener la atención y entregar el mensaje de manera más
  efectiva.
- Siempre es bueno tener técnicas de storytelling en nuestros reportes.

# Data Visualization para Business Intelligence

## Cómo afecta la visualización de datos en tu negocio?

- Nos ayudan a que dirección y gerencia entiendan claramente el mensaje
  que buscamos transmitirles.
- Nos permite que nuestro mensaje sea claro y fácil de interpretar.
- Nos permite poner en palabras conclusiones a las que no podríamos
  llegar sin verlas plasmadas en una forma visual.

## Agregar valor con los datos

- Ofrecer información relevante.
- Explora, descubre, pregunta.
- Trabajar en equipo.

# Flujo de trabajo y etapas del business Intelligence

## Recolección de datos

- La primera etapa del proceso.
- Bases públicas y privadas.
  - Publicas:
    - data.nasa.gov
    - www.makeovermonday.co.uk/data/
    - maxar.com
    - podaac.jpl.nasa.gov/datasetlist
    - science.nasa.gov/citizenscience
    - kaggle.com/datasets
    - developers.google.com/earth-engine/datasets
  - Puede venir de manera estructurada o no estructurada.

## Limpieza de datos

- Antes de interpretar los datos necesitamos que estos tengan un formato
  estandarizado.
- Garbage in garbage out.
  - Entre mejor sea nuestra información mejores serán nuestros
    resultados.
  - El producto final depende de la calidad de los datos.
- Es entre el 60/70% del trabajo de un data scientist.

## Exploración de datos

- Descubre, pregunta, reformula, analiza.
- Los datos sin historias son sólo números.