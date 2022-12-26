---
title: HTML
description: 
published: true
date: 2022-12-26T04:39:55.180Z
tags: html
editor: markdown
dateCreated: 2022-12-26T04:39:55.180Z
---

# HTML

HTML  
*Hyper Text Markup Language*.

- HTML usa etiquetas para identificar contenido.
- HTML es un *Markup Language* como lo puede ser markdown o org-mode.

``` html
<p> Soy un párrafo </p>
```

## Diseño web Moderno.

- Estructura de una web moderna.
  - **HTML** - Estructura.
  - **CSS** - Presentación.
  - **JavaScript** - Comportamiento.
  - **PHP o similares** - Backend.
  - **CMS** - Manejo de contenido.

## La etiqueta `<html>`

- La estructura de html se asemeja un poco a un sandwich en la cual cada
  elemento tiene su contra parte.

``` html
<html>

</html>
```

> Todo nuestro documento html esta dentro de las etiquetas html.

## La etiqueta `<head>`

- El elemento head contiene los elementos **no visuales** que ayudan a
  que la página funcione.

``` html
<html>
  <head></head>
</html>
```

## La etiqueta `<body>`

- Todos los elementos **visuales-estructurales** están dentro de esta
  etiqueta.

``` html
<html>
  <head>
  </head>
  <body>
  </body>
</html>
```

## La etiqueta `<title>`

- Define el titulo que aparecerá en la pestaña de tu navegador y es
  usado por los motores de búsqueda.

``` html
<html>
  <head>
    <title> Primera pagina yay </title>
  </head>
  <body>
    esta es una linea de texto xd.
  </body>
</html>
```

# Básicas de HTML

## Elemento `<p>`

- Sirve para crear párrafos.

``` html
<body>
  <p> Primer párrafo </p>
  <p> Segundo párrafo </p>
</body>
```

## Salto de linea

- Podemos usar la etiqueta `<br>` para añadir un salto de linea

``` html
<p> Esto es un <br> salto de linea </p>
```

## Elementos de formato.

- Hay una lista de elementos con los cuales podemos dar formato a texto.
- Solo es necesario poner el texto dentro de las etiquetas.

``` html
<p> Texto regular </p>
<p><b> Texto en negritas</b></p>
<p><big> Texto un poco más grande </big></p>
<p><i> Texto en itálicas </i></p>
<p><small> Texto un poco más pequeño </small></p>
<p><strong> Texto con énfasis </strong></p>
<p><sub> Texto subíndice </sub></p>
<p><sup> Texto superindice </sup></p>
<p><ins> Texto subrayado </ins></p>
<p><del> Texto tachado <del></p>
```

> Los navegadores muestran texto `<strong>` como `<b>`.

## Encabezados

- Podemos poner encabezados para los títulos con las etiquetas `<h1>` a
  `<h6>`

``` html
<h1> Encabezado tamaño 1</h1>
<h2> Encabezado tamaño 2</h2>
<h6> Encabezado tamaño 6</h6>
```

> Son importantes ya que la web usa los encabezados para indexar
> resultados y la estructura de la pagina.

## Lineas horizontales

- Para crear una linea horizontal usamos la tag `<hr/>`.

``` html
<h1> Encabezado tamaño 1</h1>
<h2> Encabezado tamaño 2</h2>
<hr/>
<h6> Encabezado tamaño 6</h6>
```

## Comentarios

- Podemos poner comentarios en código html para añadir descripciones a
  quien vea el código.

``` html
<!-- ​Tu comentario va aquí -->
```

## Atributos html

- Proveen información adicional sobre un elemento o etiqueta además de
  modificarla.

``` html
<p align="center">
 Este texto esta alineado al centro
</p>
```

## Unidades de medida de los atributos

- Hay diferentes unidades de medida.

``` html
<hr width="50px"/>
```

> Podemos usar píxeles (px)

``` html
<hr width="50%"/>
```

> También podemos usar porcentajes

## La etiqueta `<img>`

- Se usa para insertar una imagen.
- No tiene una etiqueta que la cierra.

``` html
<img src="image.jpg" />
```

### Tamaño de la imagen

``` html
<img src="image.jpg" height="150px" width="150px" alt="" />
```

> En el caso de que la imagen no pueda ser mostrada se mostrara lo que
> haya dentro de el parámetro alt

### Borde de imagen

- Por defecto las imágenes no tienen borde, podemos usar el atributo
  `border` para esto.

``` html
<img src="image.jpg" height="150px" width="150px" border="1px" alt="" />
```

## la etiqueta `<a>`

- Podemos definir links con la etiqueta `<a>`.

``` html
<a href="www.google.com"> Un link a google</a>
```

> Podemos meter un bloque de imagen entre uno de links.

### El atributo `target`

- Este define donde se va a abrir un link, con el atributo `_blank`, se
  abrirá en una nueva pestaña.

``` html
<a href="www.google.com" target="_blank"> Un link a google</a>
```

## Listas ordenadas.

- Las listas ordenadas van dentro del bloque `<ol>`.
- Cada elemento de la lista esta definido con el bloque `<li>`.

``` html
<ol>
  <li> lista 1 </li>
  <li> lista 2 </li>
  <li> elemento 1 </li>
</ol>
```

## Listas no ordenadas.

- Van dentro del bloque `<ul>`.
- Cada elemento de la lista esta definido con el bloque `<li>`.

``` html
<ul>
  <li> lista 1 </li>
  <li> lista 2 </li>
  <li> elemento 1 </li>
</ul>
```

## Tablas

- Son definidas por la etiqueta `<table>`.
- Agregamos columnas con la etiqueta `<tr>`.
- Las filas son definidas por la etiqueta `<td>`.

Una tabla con una fila y tres columnas.

``` html
<table>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
```

> Las etiquetas `<td>` pueden contener todo tipo de elementos, como
> texto, imágenes, listas así como otras tablas.

### Atributos `border` y `colspan`

- Podemos añadir bordes con el atributo `border`.

``` html
<table border="2">
  <tr>
    <td>Red</td>
    <td>Blue</td>
    <td>Green</td>
  </tr>
  <tr>
    <td><br /></td>
    <td colspan="2"><br /></td>
  </tr>
</table>
```

> Con `colspan` tenemos celdas que ocupan más de un espacio en la tabla.

### Los atributos `align` y `bgcolor`

- Para cambiar la posición de la tabla usamos el atributo `align`.

``` html
<table align="center">
```

- Podemos especificar el color de fondo de una celda con el atributo
  `bgcolor`.

``` html
<table border="2">
  <tr>
    <td bgcolor="red">Red</td>
    <td>Blue</td>
    <td>Green</td>
  </tr>
  <tr>
    <td>Yellow</td>
    <td colspan="2">Orange</td>
  </tr>
</table>
```

## Tipos de elementos

En html la mayoría de los elementos son definidos como elementos de
bloque (*bock level*) o elementos de linea (*inline*).

- Elementos de bloque:
  - Normalmente empiezan en una linea nueva.
  - `<h1>, <form>, <li>, <p>`
- Elementos en linea:
  - Normalmente son presentados en la misma linea donde se declaran.
  - `<b>, <a>, <strong>, <img>`
- El elemento `<div>` se usa como contenedor de otros elementos HTML.

``` html
<html>
  <body>
    <h1>Headline</h1>
    <div style="background-color:green; color:white; padding:20px;">
      <p>Some paragraph text goes here.</p>
      <p>Another paragraph goes here.</p>
    </div>
  </body>
</html>
```

Otros elementos pueden ser usados como elementos de bloque o elementos
de linea.

- APPLET : Applet de java embebido.
- IFRAME : Marco en linea.
- INS : Texto insertado.
- MAP : Mapa de imágenes.
- OBJECT : Objeto embebido
- SCRIPT : Script dentro de un documento html.

> Los elementos de linea no pueden contener ningún elemento de bloque.

## El elemento `<form>`

- Son usados para obtener información del usuario.

``` html
<body>
  <form>
  </form>
</body>
```

Podemos utilizar el atributo `action` para apuntar a otra pagina web
después de que el usuario termine el formulario.

``` html
<form action="https://www.google.com">
</form>
```

### Los atributos `method` y `name`

- El atributo `method` especifica que tipo de petición HTTP (`GET` o
  `POST`) sera utilizada para cuando el formulario sea mandado.

``` html
<form action="url" method="GET">
```

> Cuando usas `GET`, la información que mandes sera visible en la url de
> la pagina.

``` html
<form action="url" method="POST">
```

> Se usa `POST` cuando se quiere mejor seguridad porque la información
> no es visible en la url

Para obtener datos del usuario debemos de tener los elementos, como
pueden ser campos de texto.

``` html
<form>
  <input type="text" name="username" /><br />
  <input type="password" name="password" />
</form>
```

### Elementos de los `form`

- Si ponemos el tipo de input a `radio` el usuario puede seleccionar
  solo una de las opciones.

``` html
<input type="radio" name="gender" value="male" /> Male
<br />
<input type="radio" name="gender" value="female" /> Female
<br />
```

- El tipo `checkbox` permite al usuario elegir más de una opción.

``` html
<input type="checkbox" name="gender" value="male" /> Male
<br />
<input type="checkbox" name="gender" value="female" /> Female
<br />
```

- También tenemos un tipo `submit` que es un botón para mandar los
  datos.

``` html
<input type="submit" value="submit" />
```

## Colores HTML

- Se usa una escala hexadecimal.
- Son mostrados en una combinación de rojo (R), verde (G) y azul (B).
- Los valores hexadecimales son escritos usando el `#` y la combinación
  de 3 o 6 valores hexadecimales.

### Fondo y colores de letra

- Podemos usar el atributo `bgcolor` para cambiar el fondo.
- Podemos usar el atributo `color` dentro de la tag `<font>` para
  cambiar el color de la letra.

``` html
<html>
    <head>
        <title>first page</title>
    </head>
    <body bgcolor="#000099">
        <h1>
            <font color="#FFFFFF"> White headline </font>
        </h1>
    </body>
</html>
```

## La etiqueta `<frame>`

- Una pagina puede ser dividida en marcos.
- La etiqueta `<fame>` define una ventana especifica dentro de un
  `<frameset>`.
- Cada `frame` puede tener diferentes atributos, como borde, scroll, la
  habilidad de cambiar de tamaño, etc.
- El elemento `<fameset>` especifica el número de columnas o filas o el
  tamaño en píxeles

``` html
<frameset cols="100, 25%, *"></frameset>
<frameset rows="100, 25%, *"></frameset>
```

> `Frameset` no esta soportado en html 5

### Trabajando con `frames`

- Usamos el atributo `<noresize>` para especificar que el usuario no
  puede cambiar el tamaño de un frame.

``` html
<frame noresize="noresize">
```

- El elemento `<noframes>` provee una manera a los navegadores que no
  soportan frames.

``` html
<frameset cols="25%,50%,25%">
  <frame src="a.htm" />
  <frame src="b.htm" />
  <frame src="c.htm" />
  <noframes>Frames not supported!</noframes>
</frameset>
```

> `<frame>` no esta soportado en html 5

# HTML 5

- Al principio del documento va la declaración.

``` html
<!DOCTYPE HTML>
```

- Después va el charset.

``` html
<meta charset="UTF-8">
```

> El charset por defecto es UTF-8

## Modelos de contenido

HTML introduce 7 modelos de contenido principales.

- Metadata
  - La configuración de la presentación o el comportamiento del
    contenido.
  - Normalmente son los elementos que van dentro de `<head>`.
  - `<base>, <link>, <meta>, <noscript>, <script>, <style>, <title>`
- Embedded
  - Contenido que importa otros recursos dentro del documento.
  - `<audio>, <video>, <canvas>, <ifame>, <img>, <math>, <object>, <svg>`
- Interactive
  - Contenidos diseñados para que el usuario interactue con ellos.
  - `<a>, <audio>, <video>, <button>, <details>, <embeded>, <iframe>, <img>, <input>, <label>, <object>, <select>, <textarea>`
- Heading
  - Definen una cabecera de una sección.
  - `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <hgroup>`
- Phrasing
  - Elementos de linea en común con html 4.
  - `<img>, <span>, <strong>, <label>, <br />, <small>, <sub>`, etc
- Flow
  - Contiene la mayoría de los elementos html 5 que estan en el
    documento.
- Sectioning
  - Define el alcance de headers, contenido, footers, etc.
  - `<article>, <aside>, <nav>, <section>`

## Estructura de la pagina en HTML5

``` example

                     +------------------------------+
                     |           <header>           |
                     | Contiene cosas como logos    |
                     +------------------------------+
                     +------------------------------+
                     |             <nav>            |
                     | Contiene cosas relacionadas  |
                     | con la navegación del sitio  |
                     +------------------------------+
+-------------------------------------+ +-----------------------------------------+
|             <article>               | |                                         |
|  Contenido principal de la pagina   | |                <aside>                  |
|                                     | |                                         |
|  +-------------------------------+  | | Contiene información extra relacionada  |
|  |          <section>            |  | | con la pagina como links                |
|  | Sección dividida de la pagina |  | |                                         |
|  | principal                     |  | |                                         |
|  +-------------------------------+  | |                                         |
|                                     | +-----------------------------------------+
+-------------------------------------+
  +--------------------------------------------------------------------------+
  |                                <footer>                                  |
  |información sobre copyright, política de privacidad, términos de uso, etc |
  +--------------------------------------------------------------------------+
```

> Puede que no utilices todos los elementos, depende de la estructura de
> la página.

## La etiqueta `<header>`

- El elemento `<header>` puede ser usado dentro del `<body>`.

> El elemento `<header>` es diferente que `<head>`.

``` html
<!DOCTYPE HTML>
<html>
  <head></head>
  <body>
    <header>
      <h1> EL header más importante <h1>
    </header>
  </body>
</html>
```

## El elemento `<footer>`

- Normalmente nos referimos a la parte de abajo de la página como
  footer.
- Donde podemos encontrar:
  - Información de contacto.
  - Política de privacidad.
  - Iconos de redes sociales.
  - Términos de servicio.
  - Información de copyright.

``` html
<footer></footer>
```

## El elemento `<nav>`

- Esta etiqueta representa una sección que es usada para poner links a
  otras páginas o a ciertas partes de la misma página.

``` html
<nav>
  <ul>
    <li><a href="#">Home</li>
    <li><a href="#">Services</li>
    <li><a href="#">About us</li>
  </ul>
</nav>
```

> En este ejemplo tenemos enlaces de navegación a diferentes secciones
> de la página

## El elemento `<article>`

- Es una pieza de contenido autocontenido que puede ser usada de manera
  separada a los diferentes elementos de la página.
- Podría ser un Post de un foro, una revista o un articulo de periódico,
  un comentario, un widget interactivo o cualquier otro contenido
  independiente.
- Este elemento remplaza el `<div>` que se usaba en html4 junto con una
  clase o id.

``` html
<article>
  <h1> El titulo del articulo <h1>
  <p> Contenido </p>
</article>
```

## El elemento `<section>`

- Es un contenedor lógico dentro de una pagina o articulo.
- Pueden ser usados para dividir contenido dentro de un articulo.
- Cada `<section>` debería de ser identificada con un header.

``` html
<article>
  <h1> Welcome </h1>
  <section>
    <h1> Heading </h1>
    <p> Contenido o imagen </p>
  </section>
</article>
```

## El elemento `<aside>`

- Es un contenido secundario que puede considerarse separado pero
  relacionado a el contenido principal.
- Este tipo de contenido es representado regularmente en *sidebars*.
- Cuando `<aside>` esta dentro de `<article>` el contenido debe de estar
  relacionado al del articulo.

``` html
<article>
  <h1> Regalos para todos </h1>
  <p> Este es el mejor lugar para elegir regalos </p>
  <aside>
    <p> Los regalos serán entregados dentro de 24hrs después del pedido </p>
  </aside>
</article>
```

## Audio en la web

- Hay dos maneras de especificar el URL del audio.

``` html
<audio src="audio.mp3" controls>
  Audio element not supported by your browser
</audio>
```

``` html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
</audio>
```

- El bloque audio crea un reproductor de audio dentro de la pagina web.

### Atributos de audio

`controls`  
Especifica que los controles de audio deben ser mostrados (Play/pause).

`autoplay`  
Especifica que el audio debe de ser reproducido en cuanto este listo.

`loop`  
Especifica que el audio debe de reproducirse otra vez cuando termine.

``` html
<audio controls autoplay loop>
```

> Formatos soportados: MP3, OGG, WAV.

## Vídeos en HTML

- Es similar a audio.

``` html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.ogg" type="video/ogg">
  Video is not supported in your browser.
</video>
```

> Video comparte los mismos atributos que audio

> Formatos soportados: MP4, OGG, WebM.

## Barras de progreso

- El elemento `<progress>` provee barras de progreso.
- Pueden ser usadas en cualquier lugar dentro del `<body>`.

### Atributos de las barras de progreso

`value`  
Especifica el valor de la tarea realizado.

`max`  
Especifica el valor máximo de la tarea a realizar.

``` html
Status: <progress min="0" max="100" value="35">
</progress>
```

> Se usa en conjunto con JavaScript para mostrar el porcentaje dinámico.

## Almacenamiento Web

- Con HTML5, sitios web pueden guardar datos en la computadora local del
  usuario.
- Ventajas del almacenamiento web:
  - Más seguro.
  - Más rápido.
  - Puedes almacenar más datos.
  - Etc.

> Almacenamiento local es por dominio, Solo las paginas de un dominio
> especifico pueden acceder a el almacenamiento de ese dominio.

### Tipos de Objetos de almacenamiento Web

- Hay dos tipos de almacenamiento web:
  - `sessionStorage()`
    - Es destruido una vez el usuario cierra el navegador.
  - `localStroage()`
    - Guarda datos sin fecha de vencimiento.

### Trabajando con valores.

- La información es guardada en forma de diccionario (key/value).

**Guardando un valor.**

``` javascript
localStroage.setItem("key1", "Value");
```

**Obteniendo un valor.**

``` javascript
//Esto imprimira el valor
alert(localStroage.getItem("key1"));
```

**Eliminando un valor.**

``` javascript
localStroage.removeItem("Key1");
```

**Eliminando todos los valores.**

``` javascript
localStroage.clear();
```

> La misma sintaxis aplica para `sessionStorage`.

## API de geolocalización

- Sirve para obtener la localización geográfica del usuario.
- Por privacidad, esta opción tiene que ser aprobada por el usuario.

``` javascript
navigator.geolocation.getCurrentPosition();
```

- Parámetros:
  - `showLocation` (Mandatorio): Define el método que recibe la
    información.
  - `errorHandler` (Opcional): Define un método que es llamado cuando
    ocurre un error.
  - `Options` (Opcional): Define una serie de opciones para recibir la
    información.

### Presentando los datos

- Los datos pueden ser presentados de dos formas:
- Geodetic:
  - Se refiere a datos de latitud y longitud.
- Civic:
  - Una forma más casual y legible por cualquier persona.

## Haciendo elementos *Draggables*

- Permite que un elemento pueda moverse y cambiarse de posición con el
  cursor.
- Para hacerlo *draggable* solo pon el atributo de ese mismo nombre a
  `true`.

``` html
<img draggable="true" />
```

> Cualquier elemento puede ser *draggable*

La API de HTML5 de *drag and drop* se maneja por eventos.

``` javascript
<!DOCTYPE HTML>
<html>
   <head>
   <script>
function allowDrop(ev) {
    ev.preventDefault();
}

function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
}

function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
   </script>
   </head>
<body>

   <div id="box" ondrop="drop(event)"
   ondragover="allowDrop(event)"
   style="border:1px solid black;
   width:200px; height:200px"></div>

   <img id="image" src="sample.jpg" draggable="true"
   ondragstart="drag(event)" width="150" height="50" alt="" />

</body>
</html>
```

### Lo que se va a mover

- Cuando un elemento es arrastrado con el mause, el atributo
  `ondragstart`, llama a la función `drag()` que especifica que se va a
  mover.
- El método `dataTransfer.setData()` pone el tipo de dato y el valor de
  los elementos a mover.

``` javascript
function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
}
```

> El tipo de dato es "text" y el valor es el ID del elemento a mover,
> "image".

### A donde ponerlo

- El atributo `ondragover` especifica donde el objeto puede ser soltado.
  - Por defecto, datos y elementos no pueden ser soltados dentro de
    otros.
    - Debemos prevenir el manejo por defecto de los elementos.
  - Esto se hace llamando al método `preventDefault()` para el evento
    `ondragover`.

### Hacer el Drop

- Cuando el objeto es soltado, ocurre el evento *drop*.
- En el ejemplo el atributo `ondrop` llama a la función `drop()`.

``` javascript
function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
```

- El método `preventDefault()` previene el el manejo por defecto del
  evento.
- Los datos de el elemento pueden obtenerse con
  `dataTransfer.getData()`.
  - Estos datos seria el ID del elemento movido `"image"`.
- El elemento movido es añadido al final del evento *drop*, usando la
  función `appendChild()`.

## SVG
