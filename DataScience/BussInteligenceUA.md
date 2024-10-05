---
title: Curso de Business Intelligence Utilidad y Áreas de Oportunidad
description: 
published: true
date: 2022-12-25T07:08:21.606Z
tags: business inteligence
editor: markdown
dateCreated: 2022-12-25T07:08:16.376Z
---

# Fundamentos

## Introducción

- `Business Intelligence (BI)` vs `Data Science (DS)`
  - `BI` es un análisis descriptivo y situational del presente:
    - Qué está pasando? Qué estuvo pasando?
  - `DS` puede ir más allá por ejemplo, con modelos predicativos:
    - Hacia donde vamos?

------------------------------------------------------------------------

- Procesos del `BI`
  - `ETL`
    - `Extract`:
      - Recopilar información que podamos de la manera que sea
        necesaria.
    - `Transform`:
      - Limpieza de la información porque no siempre esta estructurada,
        organizada o sin errores.
    - `Load`:
      - Continuar con el proceso porque la intención es subir esta a
        algún software para analizarla.
  - Exploración:
    - Es la etapa más larga, estar indagando en la data, que ocurre
      según los datos.
  - Descubrimientos:
    - Fue lo encontrado, que hay de interesante, que patrones?
  - `Reporting`:
    - Entregar el mensaje de lo obtenido con los datos.
- Presentar La información:
  - Visualización de datos:
    - La manera en la que presentamos la información de manera visual.
  - `Story telling`:
    - Manera en la que se narran los descubrimientos para cautivar a la
      audiencia.

## Qué es `stakeholders`

- También llamados grupos de intereses.
- Son personas que tienen algún interés en la compañía.
  - Y que pueden afectar o ser afectados por esta.
  - Algunos comunes pueden ser:
    - Primarios:
      - Accionistas.
      - Clientes.
      - Proveedores.
      - Empleados.
    - Secundarios:
      - Sociedad.
      - Gobierno.
      - Comerciantes.
  - Pueden ser internos o externos a la organización

------------------------------------------------------------------------

- Tenemos que pensar en los intereses de los `stakeholders` que tengan
  mayor prioridad.
  - Para esto debemos de entender sus intereses.
    - Accionistas:
      - Retorno de inversión.
    - Clientes:
      - Calidad de productos, servicios y necesidades.
    - Empleados:
      - Seguridad y estabilidad.
    - Proveedores:
      - Estabilidad e ingresos.

------------------------------------------------------------------------

- Debemos priorizar a los nuestros y a los más importantes.
  - Depende de la organización.
    - Ejemplos:
      - Empresa tradicional:
        - Accionistas.
        - Clientes.
        - Empleados.
      - Una `Startup`:
        - Clientes.
        - Empleados.
        - Accionistas.
  - Básicamente debemos salvaguardar los intereses de los
    `stakeholders`.

## Tipos de empresa: venta de productos o servicios

- Es importante diferenciarlos para entender la afectación de cada una
  en el estado de resultados.
- Estado de resultados (EDR):
  - Es un documento.
  - Tiene las pautas de como funcionan las utilidades de la empresa.
  - **Utilidad Bruta** = ingresos - Costos de venta.
  - **Utilidad Operativa** = Utilidad Bruta - Gastos de administración.
  - **Utilidad Neta** = Utilidad Operativa - Otras gastos e impuestos -
    Impuestos.
    - Es la más importante.
- EDR según el tipo de empresa:
  - Productos:
    - En general las ventas menos los costos de producción.
  - Servicios:
    - Generalmente los gastos están en la nómina, gastos
      administrativos, etc.

## `Income statement` simplificado: utilidad bruta, operativa y neta

- `Income statement` = Estado de resultados
- Siempre es recomendado ir de los particular a lo general.
  - Tomar una actividad y llevarla al `income statement`.
- Utilidad Bruta:
  - Si es negativa, deberíamos arreglarlo inmediatamente ya que estamos
    perdiendo dinero.
- Utilidad operativa:
  - Su relación con la utilidad bruta nos permite descubrir gastos
    excesivos y recortarlos.
- Cómo afecta cada actividad al `income statement`?
  - Costo en materia prima.
  - Incremento en nómina.
  - Cambio de oficinas.
  - etc.

## Ingreso, utilidad y costos

- Utilidad vs ingresos:
  - Un ingreso (revenue) es todo aquello a lo que no se le ha sustraído
    los gastos.
    - Mayor ingreso, no implica mayor utilidad (ej. descuentos).
    - Mayor costo no siempre implica menor utilidad (ej. gasto de
      marketing).
- Costos:
  - **Costo fijo**:
    - Ocurren de manera periódica, como la renta de oficinas.
  - **Costo variable:**
    - Están relacionados a una actividad, en donde mayor actividad,
      mayor costo.
    - Como con las ventas.
  - **Costo semivariable**:
    - Es fijo hasta cierto punto y luego variable.
    - Como el costo de la electricidad.
  - Mayores costos no significan siempre menor utilidad.

## Margen de contribución

- Es la diferencia entre el precio de mis productos menos el costo del
  producto
- Nos ayuda a encontrar nuestro punto de equilibrio.
  - El punto en donde no tenemos ni ganancias ni perdidas.

$$PE = \frac {\textrm{Costos fijos}} {\textrm{Precio de venta} - \textrm{costo variable por unidad}}$$

## Razones matemáticas en los negocios

- La relación entre dos distintas magnitudes
  - O pensar en porcentajes.
- Responde a cuanto hay de una magnitud en otra?.
- Sirven para comparar rendimientos de manera sencilla.
- Ejemplos:
  - Utilidad / ingresos:
    - Conocer el rendimiento respecto a otros productos, empresas e
      industrias.
  - Margen de contribución / Precio:
    - Conocer cuál producto conviene vender más.

# `Business intelligence`

## Extracción de datos y ejemplos de archivos

- Debemos recordar el proceso `ETL`.
- Es probable que la información este fragmentada en diferentes sitios
  (silos de información).
  - cada departamento guarda información de manera diferente así que es
    probable que sea complicado relacionarla.
- Debemos de saber como extraer la información de diferentes softwares.

## Limpieza de datos con excel y python

- La segunda parte del `ETL`.
- debemos limpiar los datos para que sean entendibles para la siguiente
  fase.
- `garbage in, garbage out`.
  - Si ingresas contenido basura a tu proceso, lo que saldrá de este es
    basura también.
  - Debemos de ser cuidadosos con la limpieza.
- Es el primer acercamiento para ver que tipo de información tenemos.

## Exploración de datos

- debemos explorar estos para poder encontrar patrones y tendencias en
  los datos podemos hacernos preguntas para comprender los datos.
- Cambio de hipótesis iniciales ya que puede que la información cambie
  estas preguntas.

## Descubrimientos, highlights, top y bottom data

- Los highlights son los que nos ayuda a tomar decisiones.
- Siempre iniciar con lo más usado.
- Intentar buscar lo más y lo menos.
- Tomar en cuenta el tiempo y ver patrones allí.

## Reporting

- Debemos pensar en la audiencia a la que le vamos a presentar los
  datos.
  - Reportes van personalizados a la audiencia.
  - Debemos centrarnos en el mensaje del reporte.
- Debemos de dar **contexto**.
- Concentrar nuestros esfuerzos en un dashboard.
- usar storytelling para entretener a la audiencia.
- Dejar sugerencias sobre esta información.

# Buenas prácticas

## Alertas, automatización y `live reporting`

- Es mejor que tus reportes estén conectados a las fuentes de
  información.
  - Usamos automatización con software.
- Podemos poner alarmas para monitorear ciertos parámetros.

## Eficiencia, max profit y min cost

- Mejorar un proceso nos permite mejorar nuestros recursos a largo
  plazo.
- Siempre debemos de buscar mejorar la utilidad.
- Pensar siempre en la jerarquía de stakeholders.
