---
title: Introducción a la Ciencia de datos e Inteligencia artificial
description: 
published: true
date: 2022-12-25T00:52:17.561Z
tags: data science, ia
editor: markdown
dateCreated: 2022-12-25T00:52:11.986Z
---

# Importancia y usos de Data Science e Inteligencia Artificial

## Glosario

- Base de datos `OLAP`:
  - Acrónimo en ingles de Procesamiento analítico en linea.
    - `Online Analaytical Processing`
  - Son bases de datos especializadas para generar consultas de grandes
    cantidades de datos.
- Base de datos `OLTP`:
  - Procesamiento de transacciones en linea.
    - `Online Translation Processing`
  - Se enfocan al registro y actualización de datos.
  - Se usan generalmente en aplicaciones donde se encuentran los datos
    que necesitan estas mismas.
- Computo en la nube:
  - Servicios para almacenar, administrar y procesar datos, servidores,
    bases de datos, redes y software.
  - `AWS`, `Google Cloud Plataform`, `Azure`.
- `Data pipeline`:
  - Es un proceso donde con diferentes tecnologías movemos y procesamos
    datos.
  - Se usan para mover datos de bases de datos `OLTP` a `OLAP`.
- `Data Science`:
  - Es un campo que involucra métodos científicos, procesos y sistemas
    para obtener información.
    - A través de análisis de datos y `machine learning`.
- `ETL`:
  - `Extract, Transform, Load`.
  - Es un tipo de `pipeline` de datos donde extraemos datos de diversas
    fuentes.
  - Los transformamos para poder almacenarlos y los cargamos en bases de
    datos especializadas para analítica.
- `Insights`
  - Información de valor.
  - Es la información que se ha obtenido después de analizar datos.
  - Generalmente sirve para tomar una decisión de negocio o generar
    estrategias en una organización.
- Inteligencia Artificial:
  - Es inteligencia expresada por máquinas.
  - Algoritmos que hacen que las máquinas aprendan bajo repetición para
    emular la inteligencia natural.
  - Para ello reconocen patrones en grandes cantidades de datos.
- Limpieza de datos:
  - Cuando se descubren datos erróneos o faltantes en una tabla o base
    de datos y se corrigen o eliminan.
- `Machine Learning`:
  - Aprendizaje automático.
  - Es una rama de la inteligencia artificial.
  - Su objetivo es que las computadoras aprendan.
  - Las computadoras observan grandes cantidades de datos y construyen
    un modelo capaz de generar predicciones para resolver problemas.
- Modelo Machine:
  - Es la salida de información que se genera cuando se entrena un
    algoritmo de `machine learning`.
  - Después del entrenamiento podemos darle nuevos datos similares y
    obtener una predicción de salida.
- Transformar datos:
  - Implica separar datos, limpiar datos nulos, agregar nuevas columnas
    con nueva información, e incluso cambiarles el formato.

## Qué es data Science?

- **El proceso de descubrir información valiosa de los datos.**
- Para:
  - Tomar decisiones y crear estrategias de negocio.
  - Crear productos de software más inteligentes y funcionales.
- De que trata el proceso:
  - Obtención de datos
  - Transformar y limpiar los datos.
  - Explorar, analizar y visualizar los datos.
  - Usar modelos de `machine learning` (Opcional).
  - Integrar datos e IA a productos de software.
- El proceso entre proyecto a proyecto cambia poco.
- El proceso es el método científico aplicado a los datos.
- Es un proceso iterativo.

## Qué es Inteligencia Artificial y su diferencia con `data science`

- Son algoritmos para emular nuestra inteligencia natural.
- Reconocen patrones en grandes cantidades de datos.
- La IA solo va a hacer lo que nosotros la entrenemos que haga (`one trick pony`).
- `Machine learning`
  - Una rama de la inteligencia artificial.
- Proceso de integrar `machine learning` a un producto:
  1.  Obtener Datos de entrenamiento
  2.  Validación de los datos.
  3.  Preparación de los datos
  4.  Entrenamiento de modelo.
  5.  Evaluación de modelo.
  6.  Validación de modelo.
  7.  Despliegue de modelo.
- `Data Science + IA`
  - En el proceso de data science utilizamos inteligencia artificial
    como una de sus herramientas.

## Qué es `Big Data`? Cuál es su diferencia con Data Science?

- Grandes volúmenes de datos muy variados y muy veloces.
- Resulta complicado procesarlos con métodos tradicionales.
- Las 5 V de `Big Data`:
  - Volumen:
    - El almacenamiento de la masiva cantidad de datos que pueden ser
      recolectados de múltiples fuentes.
  - Velocidad:
    - Los datos se generan en tiempo real gracias a las interacciones
      con las fuentes mencionadas.
    - Deben de ser procesados con la misma velocidad.
  - Variedad:
    - Todo tipo de datos, ya sea estructurados o no estructurados.
  - Veracidad:
    - Es la calidad y la confiabilidad de los datos.
  - Valor:
    - Los datos deben poder proporcionar un valor o beneficio a la
      empresa que los esta usando.
- Procesamiento de `Big Data`
  - Se procesa al dividirla en partes pequeñas en varias máquinas.
  - Tecnologías como `Spark`, `Hadoop` y servicios de computo en la
    nube.
- `Data Science + IA + Big Data`
  - `Big data` es la materia prima que podemos usar en `data science`
    para hacer análisis mas exhaustivos.
  - Incluso podemos usar `machine learning` en ese mismo proceso para
    perfeccionar y evaluar los algoritmos de IA que creemos.

## Áreas de aplicación de `Data Science` e Inteligencia Artificial

- Ramas de `IA`
  - `Machine Learning`.
  - `Deep Learning`.
  - `RPA`.
  - Visión artificial.
  - Procesamiento de lenguaje natural.
  - Robótica.
- Áreas de Aplicación de `data science`
  - Salud.
  - Procesos productivos.
  - Procesos comerciales.
  - Redes sociales.

## Roles en la industria: Cómo funcionan los equipos de datos e inteligencia artificial

- Roles de la industria:
  - `Data Scientist`.
  - `Data Analyst`.
  - `Data Engineer`.
  - `Machine Learning Engineer`.
- No se puede empezar a implementar modelos de `machine learning` sin
  antes tener una **Cultura data-driven**.
- Necesidades de `Data Science`.
  - Es el orden de las etapas que las empresas deben seguir para su
    desarrollo en la cultura `Data-Driven`.
    1.  Recolección de datos:
        - Instrumentación.
        - `Logging` (creación de cuentas de los usuarios).
        - Sensores.
        - Datos Externos.
        - Contenido Generado por el usuario.
    2.  Movimiento y Almacenamiento:
        - Datos Confiables.
        - Flujo.
        - Infraestructura.
        - `Pipelines`.
        - `ETL` (`Extract, Transform, Load`).
        - Datos estructurados (que ya están organizados o clasificados
          por alguna estructura estándar).
        - Datos no estructurados (datos que están sueltos).
    3.  Exploración y transformación:
        - Limpieza.
        - Detección de anomalías.
        - Preparación.
    4.  Agregaciones y etiquetado:
        - Estadísticas.
        - Métricas (Las medidas de una actividad en concreto).
        - Segmentación
        - Agregaciones.
        - Características.
        - Entrenamiento de datos.
    5.  Aprendizaje y optimización:
        - Pruebas A/B [Wiki](wikipedia:https://es.wikipedia.org/wiki/Prueba_A/B)
        - Experimentación.
        - Algoritmos Simples de `ML`.
        - Inteligencia Artificial.
        - `Deep Learning`.

# `Data Analyst`

## Qué hace un `Data Analyst`?

- Utiliza los datos para obtener `Insights`.
- Extrae datos recolectados, los analiza y reporta los resultados con
  gráficos y tableros.
- Día a día:
  - Identifica necesidades de información.
  - Extraer datos de Fuentes con `SQL` y `python`.
  - Limpiar y organizar los datos.
  - Analizar los datos
  - Comunicar los hallazgos en tableros o `dashboards`.
- Flujo de trabajo:
  1.  Problema o pregunta.
  2.  Exploración y `queries`.
  3.  Recopilar información de valor.
  4.  Crear visualizaciones de la información.
  5.  Comunicar hallazgos.
- Roles relacionados:
  - `Business Analyst`
    - Persona que tiene conocimientos más profundos con el negocio.
  - `Data visualization specialist`
    - Especialistas en presentar datos y resultados.

## Herramientas y tecnologías para `Data Analyst`

- Bases de datos `SQL`.
- Software de visualización de datos como `Power BL` y `Tableau`.
- `Excel` y `Google Sheets`.
- Programación con `Python` o `R`.
  - `Jupyter Notebooks`.
  - `Pandas, Matplotlib, Numpy`.
- Probabilidad y Estadística descriptiva.

# `Data Scientist`

## Qué hace un `Data Scientist`?

- Toma datos y los utiliza para crear modelos de `machine learning`
- Toma decisiones basadas en datos.
- Incorpora datos a los productos de software.
- Día a día:
  - Obtener, limpiar y procesar.
  - Diseñar y utilizar modelos de `machine learning`.
  - Monitorear la precisión de los datos.
  - Automatizar los proceso de recolección y transformación de datos
  - Crea reportes de información en tableros.
  - Incorpora datos a los productos.

## Herramientas y tecnologías para `Data Scientist`

- Programación con `Python` o `R`.
  - `Jupyter Notebooks`.
  - `Pandas, Matplotlib, Numpy`.
- Algoritmos y librerías de `machine learning` como
  `scikit-learn, tensorflow`.
- bases de datos `SQL` y `NoSQL`.
- Matemáticas:
  - Álgebra.
  - Estadística descriptiva e inferencial.
  - Probabilidad.
  - Álgebra lineal.
  - Cálculo.

# `Data Engineer`

## Qué hace un `Data Engineer`

- El toma los datos crudos, los limpia y los almacena en una base de
  datos.
- Trabaja para que el equipo tenga datos para el análisis.
- Crea `Pipelines ETL`.
  - Extracción transformación y carga.
- Día a día:
  - mantiene y crea `Data Pipelines` y bases de datos.
  - Extrae datos de diferentes fuentes.
  - Transforma los datos para el análisis.
  - Los guarda en bases de datos especializadas para análisis.
    - Bases de datos `OLAP` no transaccionales(`OLTP`).
  - Crear automatizaciones pare el `ETL`.
- Proceso `ETL`:
  - Extraer:
    - Archivos.
    - Bases de datos (`OLTP`).
    - `APIs`
  - Transformar
  - Cargar (`load`).
    - los guardamos en `Data Warehouse` (`OLAP`).
  - Roles Relacionados:
    - `Data Architect`:
      - Se encarga de plantear las estrategias de datos de la
        organización.
    - `Big Data Architect`:
      - Trabaja con `Big Data`.

## Herramientas y tecnologías para `Data Engineers`

- Programación con `Python` y bases de ingeniería de software.
- `Linux`.
- Automatización y `Scripting`.
- `Jupyter Notebooks` y editores de código.
- Bases de datos SQL y NoSQL.
- `Pandas, Dask y Apache Spark`.
- `Airflow`.
- Tecnologías `Cloud` (`AWS`, `Azure`).
- Contenedores `Docker`.
- Orquestadores `Kubernetes`.
- Matemáticas:
  - Estadística Descriptiva.

# `Machine Learning Engineer`

## Qué hace un `Machine Learning Engineer`

- El encargado de recibir el modelo de un `Data Scientist` e integrarlo
  a producción.
- Crear productos basados en IA.
- Escalar modelos de IA.
- Día a día:
  - Generar una evaluación extensiva de métricas de modelos de
    `machine learning`.
  - Construir, escalar y robustecer sistemas de `machine learning` que
    funcionen en producción.
  - Colaborar con `Data Scientist` y otras áreas de ingeniería de
    software.
  - Monitorear el desempeño de los sistemas de `machine learning`.

## Herramientas y tecnologías para `Machine Learning Engineer`

- Programación avanzada con `Python, java y C++`.
- Bases sólidas de ingeniería en software.
- `Jupyter Notebooks`
- `Pandas, Numpy, Matplotlib, Seaborn`
- Uso extensivo de `frameworks` y librerías de `machine learning`.
- `Flask o FastAPI`.
- Tecnologías `Cloud`.
- Contenedores `Docker`.
- `Kubernetes`.
- Matemáticas:
  - Estadística descriptiva e inferencial.
  - Probabilidad.
  - Álgebra lineal.
  - Cálculo.
