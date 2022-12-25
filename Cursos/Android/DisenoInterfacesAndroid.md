---
title: Curso de diseño de interfaces en android
description: 
published: true
date: 2022-12-24T19:28:46.662Z
tags: android, xml, ui
editor: markdown
dateCreated: 2022-12-24T19:28:39.906Z
---

# Introducción

## UI en Android

- `XML`
  - Lenguaje de marcado.
  - Se estructuran los datos a tráves de tags.
  - Pueden Contienen atributos.
- `Namespaces`
  - Una forma de darle contexto a un tag.
  - Una forma de contextualizar los elementos de un XML.
  - El `namespace` `android` es muy común en android.
  - Atributo xmlns (xml namespace).
    - Le damos una procedencia a un xml para que sepa de donde sacar el
      namespace.

## Enlazando nuestro `layout` con código

- Si en el visor de archivos ponemos la vista de `android` Encontraremos
  la carpeta res.
  - `res` es de recursos.
  - En esta carpeta encontraremos:
    - La carpeta `drawable`
      - Aquí se guardan todos los gráficos e imágenes.
    - La carpeta `layout`
      - Las estructuras de las pantallas.
    - La carpeta `mipmap`
      - Aquí guardaremos iconos.
    - La carpeta `values`
      - Es donde administramos los recursos
        - Textos, colores, estilos, temas, etc
      - archivos:
        - `colors.xml`
          - Aquí están definidos los colores de la aplicación
        - `strings.xml`
          - Donde se almacenan los textos de la aplicación.
          - Se almacenan en forma de variables con un nombre y un valor.
          - nos ayudan a poder cambiar de lenguaje nuestra aplicación.
        - `dimens.xml`
          - guardaremos dimensiones compartidas.

## `ViewGrup` y `View`

- Las vistas en android están dadas por un xml.
  - Por lo tanto, siempre terminaremos trabajando en texto.
- `ViewGrup`
  - Sirve para agrupar vistas.
  - Agrupa elementos en pantalla.
  - Los cambios que hagamos en el `ViewGrup` afectan los elements dentro
    de este.
  - EJ: `LinearLayout`
  - Pueden tener `ViewGrup` anidados.
- `View`
  - Es un elemento como tal que se va a mostrar en pantalla y
    generalmente se cierran en la misma linea.
    - `inline elements`
    - `<textView />`, `<ImageView />`, `<EditText />`

## Atributos Importantes: alto, ancho e id

- `wrap_content`
  - Nos permite que el elemento crezca tanto como su contenido.
- `match_parent`
  - Con esto el elemento va a cubrir todo el espacio disponible para el.
- `hint`
  - Nos permite mostrar una sugerencia o información del elemento.
- `background`
  - Nos permite poner el background de un elemento.
  - Podemos acceder a los recursos con `@`.

## Otros atributos y el `namespace` `tools`

- el elemento `id`
  - tienen la siguiente sintaxis `@+id/nombre` donde nombre es el nombre
    del elemento para referirnos a el.
    - Es útil usar nombres descriptivos para este elemento.
    - Con esto podremos acceder a ellos desde la clase `R` en el code
      behind.
      - `R.id.elemento`
- Atributos específicos y compartidos
  - `background` es un atributo compartido ya que todos los elementos lo
    tienen.
  - `hint` sería un atributo específico ya que solo algunos elementos lo
    tiene.
- El `namespace tools`
  - Nos permite ver como se verá nuestra aplicación sin tener que correr
    esta.
  - Por ejemplo poner texto de prueba para visualizarlo en el `preview`
    del editor.
  - Nos da varias opciones como `text`, `background`, etc.

## `LinearLayout`: organización lineal

- es parecido al `listbox` de xaml.
- Podemos ordenar los elementos verticalmente u horizontalmente.
  - esto lo hacemos con el parametro `orientation`.
  - Estos irán ocupando el espacio que necesitan uno detrás del otro.
  - En la orientación vertical.
    - Los elementos se llenan de arriba a abajo.
  - En la orientación horizontal.
    - Los elementos se llenan de izquierda a derecha.
- Podemos tener `LinearLayout` dentro de otro `LinearLayout`
  - Permitiendo ordenar los elementos de diferente manera.
- Los modificadores que empiezan con la palabra `layout` ej
  `layout_margin`, `layout_widith`
  - Solo modifican el elemento, no sus elementos hijos.

> dp significa `density points`, es la unidad de medida y escala con el
> dpi de la pantalla.

> Si queremos tener recursos, debemos nombrarlos solo con snake case y
> en minusculas EJ: recurso<sub>nuevo</sub>.xml

## `RelativeLayout`: Organizando con referencias

- Permite Generar `layouts` más flexibles.
- Permite que el elemento indique como debe alinearse con respecto a el
  padre.
- Podemos hacer que uno o más elementos se alineen usando
  identificadores.
- Todos estos elementos se alinean con respecto al elemento padre

Si queremos que un elemento se alinee arriba o abajo

    layout_alignParentTop="True"
    layout_alignParentBottom="True"

Si queremos que el elemento se alinea a la izquierda o derecha

    layout_alignParentStart="True"
    layout_alignParentEnd="True"

También podemos alinear un elemento respecto a otro, primero debemos
indicar su posición y después le damos el id del elemento que queremos
que este alineado.

    layout_alignParentEnd="True"
    layout_below="@id/name"

Con el código de arriba podríamos alinear un elemento a la derecha y
abajo de otro.

## `FrameLayout`: Alineación por región

- Nos permite ocupar una región de la pantalla basandonos en el elemento
  más grande de esa región.
- Otro uso común de `FrameLayout` es que podemos cargar vistas
  dinámicamente en el.
- También nos permite poner elementos enfrente de otro para crear nuevos
  efectos.

## `Layout` Externos: `ConstraintLayout`

- Es parecido a `RelativeLayout`
- Tiene la ventaja de que considera los elementos con los cuales se va
  alineando
  - Y cuando una modificación sucede, los elementos reaccionan.
- Todos los elementos deben de tener una alineación vertical y
  horizontal.

# Estilos

## Qué es un estilo

- los elementos suelen compartir características
  - Esto se le conoce como estilos.
- Los estilos están definidos en la carpeta `res/values/styles.xml`
  - Si no esta el archivo puedes crearlo añadiendo un nuevo recurso.
- Los estilos necesitan un nombre y los damos de alta con la tag
  `style`.
  - Podemos crear sub estilos y heredar de otros estilos que hayamos
    definidos.
- Dentro de estos estilos damos de alta etiquetas `item` cuyo nombre se
  refiere a algún tipo de elemento de la UI, por ejemplo
  `android:textSize` si queremos modificar el tamaño del texto.
- ya dentro del xml de nuestra `activity`, podemos llamar al estilo con
  el `@` y la ruta a este.

## Qué es un tema

- Tener estilos es una manera correcta de compartir atributos entre
  nuestros elementos.
- tema:
  - Es un estilo aplicado globalmente
  - Cuando hagamos una modificación todos los elementos se verán
    afectados.
- Dentro del `AndroidManifest` tenemos una etiqueta de tema.
  - Este el tema global de la aplicación y cualquier cambio afectará
    toda la aplicación.
- No hay manera de diferenciar un tema de un estilo (sintácticamente).
  - Ambos se crean con la tag `style`.
  - (al parecer ahora ya hay una carpteta de themes)
- Si ponemos un tema a nivel `layout` este afectará a todos los
  elementos hijos.
  - Aunque cada hijo puede sobreescribir los atributos de este.

## Distribuyendo nuestros valores

- Dentro de el archivo `res/values/dimens.xml`
  - Podemos definir diferentes dimensiones para nuestros elementos.
  - Esto nos sirve para normalizar o estandarizar nuestros elementos,
    como `pading`, `textSize`, `widith`, etc.

# Extendiendo los `widgets`

## Agregando `widgets` externos

- Podemos agregar librerías.
- Debemos seguir las instrucciones de la librería
  - No hay manejador de paquetes buh!
  - Generalmente Deberemos de pegar algo en el `build.gradle`.
    - En el que termina con .app
  - tendremos que refrescar el proyecto (o sincronizar).
    - Para que gradle se encargue de instalar la librería.

## Reutilizando elementos

- Es posible reutilizar `layouts` o elementos para evitar copiar código.
- Debemos agregar un nuevo `layout_resource_file` en la carpeta de
  `layout`.
- Una vez agregado, lo importamos a nuestra `activity` con la etiqueta
  `include`.
  - con el `tag` `layout` incluimos nuestro elemento externo haciendo
    uso de `@layout/elemento`.
  - Ahora debemos ponerle los atributos de posicionamiento que necesite
    ya que por defecto no tiene.
- El principal problema es que por defecto nuestros nuevos elementos
  vienen en un `LinearLayout`.
  - Esto nos causa anidación de `layouts`.
  - Para evitar esto, podemos remplazar la etiqueta `LinearLayout` por
    `merge`.
  - Esto nos permitirá referirnos al elemento por si solo.
