---
title: Bash Scripting
description: Introducción corta al scripting en bash
published: true
date: 2022-12-31T01:55:49.248Z
tags: cursos, bash, scripting, linux
editor: markdown
dateCreated: 2022-12-24T17:24:43.512Z
---

[CheatSheet](https://devhints.io/bash)

# Programación de shell básica

Nuestro primer programa…



Hola mundo en bash, archivo `hola.sh`

</div>

``` bash
#!/usr/bin/bash

echo "Hola mundo"
```

</div>

``` example
Hola mundo
```

Para poder ejecutar nuestro script debemos darle permisos de ejecución
con `chmod +x hola.sh`, y ejecutamos con `./hola.sh`.

Podemos saber más información sobre un comando de bash con el comando
`type`, por ejemplo.

``` bash
#!/usr/bin/bash

type man
```

``` example
man is /usr/sbin/man
```

También podemos saber si el nombre que le pongamos a nuestro script es
único con el comando `type -a`, el cual nos muestra todos los comandos
con el mismo nombre.

``` bash
#!/usr/bin/bash

type -a man
```

<table>
<tbody>
<tr class="odd">
<td>man</td>
<td>is</td>
<td>/usr/sbin/man</td>
</tr>
<tr class="even">
<td>man</td>
<td>is</td>
<td>/sbin/man</td>
</tr>
<tr class="odd">
<td>man</td>
<td>is</td>
<td>/usr/bin/man</td>
</tr>
</tbody>
</table>

## Definir variables y su alcance

Tenemos dos tipos de variables:

- Variables de usuario.
- Variables de entorno o de sistema operativo.
  - Podemos verlas si abrimos con un editor de texto `/etc/profile`.
  - Estas son las variables del sistema operativo, aplican para todos
    los usuarios.

``` bash
#!/usr/bin/bash
# Programa para verificar la declaración de variables.
# definición de variables a nivel de programa
option=0
nombre=David

echo "Opción: $option y nombre: $nombre"

```

``` example
Opción: 0 y nombre: David
```

- Estas variables solo son accesibles en el proceso en el que fueron
  creadas.
- Podemos usar la palabra `export` para utilizarlas afuera.


``` bash
#!/usr/bin/bash
nombre=Daniel
export nombre
```

### Variables especiales

`$1, $2, $3, $...`
Parámetros de posición que hacen referencial al primer, segundo, etc. parámetro pasado al script

`$_`
El ultimo argumento pasado al ultimo comando ejecutado (Justo después de arrancar la shell)
este valor guarda la ruta absoluta del comando que inicio la shell.

`$*`
La lista completa de argumentos pasados al script. 
Este valor es una cadena de texto.

`$@`
la lista completa de argumentos pasados al script, este valor es un array

`$-`
La lista de opciones de la shell actual

`$$`
El PID de la shell actual

`$IPS`
El separador utilizado para delimitar los campos.

`$?`
El código de salida del pipe más reciente.

`$!`
El PID del último comando ejecutado en segundo plano.

`$0`
El nombre de la shell o del script de shell

## Tipos de operadores

``` bash
# !/usr/bin/bash
numA=5 # todo junto <---
numB=10

echo "A + B =" $((numA + numB)) # los operadores aritméticos y relacionales son los mismos que siempre
# operadores de asignación también son los normales +=, -=, etc

```

``` example
A + B = 15
```

Para aplicar formato al echo podemos usar `echo -e "\ntexto aquí"`

## Script con argumentos

`$0`  
Nos da el nombre del script.

`$1 al ${10}`  
El número de argumentos dados (si son más de 9, se agrupan con llaves).

`$#`  
Contador de argumentos.

`$*`  
Todos los argumentos.


Teniendo el script `argumentos.sh`

</div>

``` bash
#!/usr/bin/bash

nombreCurso=$1
horarioCurso=$2

echo "El nombre el curso es $nombreCurso y el horario es $horarioCurso"
echo "El numero de parámetros dados es $#"
echo "los parámetros enviados son $*"

```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./argumentos.sh bashCourse "10 a 11 am"
El nombre el curso es bashCourse y el horario es 10 a 11 am
El numero de parámetros dados es 2
los parámetros enviados son bashCourse 10 a 11 am
pi@rasp-server:~/bashCourse $
```

## Sustitución de comandos en variables

La idea es usar la salida de un comando y guardarla en una variable.

Se puede hacer con:

- `'`
- `$(comando)`


Script `comandos.sh`

</div>

``` bash
#!/usr/bin/bash

ubicacionActual='pwd'
infoKernel=$(uname -a)

echo "ruta actual $ubicacionActual"
echo "información del Kernel $infoKernel"
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./comandos.sh
ruta actual /home/pi/bashCourse
información del kernel Linux rasp-server 5.10.17-v7l+ #1403 SMP Mon Feb 22 11:33:35 GMT 2021 armv7l GNU/Linux
```

## Debug un script

- Para debugear un script de bash tenemos los siguientes argumentos del comando `bash`.

`-v`  
Utilizado para ver el resultado detallado de nuestro script, evaluado
línea por línea.

`-x`  
Se utiliza para desplegar la información de los comandos que son
utilizados, capturando el comando y su salida.

``` example

pi@rasp-server:~/bashCourse $ bash -v comandos.sh
# !/usr/bin/bash

ubicacionActual=`pwd`
infoKernel=$(uname -a)

echo "ruta actual $ubicacionActual"
ruta actual /home/pi/bashCourse
echo "información del kenrel $infoKernel"
información del kenrel Linux rasp-server 5.10.17-v7l+ #1403 SMP Mon Feb 22 11:33:35 GMT 2021 armv7l GNU/Linux

pi@rasp-server:~/bashCourse $ bash -x comandos.sh
++ pwd
+ ubicacionActual=/home/pi/bashCourse
++ uname -a
+ infoKernel='Linux rasp-server 5.10.17-v7l+ #1403 SMP Mon Feb 22 11:33:35 GMT 2021 armv7l GNU/Linux'
+ echo 'ruta actual /home/pi/bashCourse'
ruta actual /home/pi/bashCourse
+ echo 'información del kernel Linux rasp-server 5.10.17-v7l+ #1403 SMP Mon Feb 22 11:33:35 GMT 2021 armv7l GNU/Linux'
información del Kernel Linux rasp-server 5.10.17-v7l+ #1403 SMP Mon Feb 22 11:33:35 GMT 2021 armv7l GNU/Linux

```

# Scripts interactivos

## Capturar información del usuario

Se usa el comando `read`

`read -p`  
Permite ingresar una frase o prompt a la hora de leer un dato.

`read -s`  
No muestra ningún carácter en la terminal (bueno para contraseñas)

`read -n [num]`
permite leer como máximo n caracteres.

`read -r`  
*Raw*, toma el botón de retroceso como un carácter y no borra nada.


Script `test.sh`

</div>

``` bash
#!/usr/bin/bash

echo "test"
read -p "hola: " resp

echo "..."
echo "$resp"

echo -n "Ingrese su nombre: "
read
name=$REPLY
echo "Tu nombre es: $name"
```

</div>

``` example

pi@rasp-server:~/bashCourse $ ./test.sh
test
hola: holaaaaaaaa
...
holaaaaaaaa
Ingrese su nombre: Jorge
Tu nombre es: Jorge

```

## Validar la información

Hay dos maneras:

- Con `read -n num-de-caracteres`.
- Con expresiones regulares.

## Paso de parametros y opciones

- Opciones vs Parámetros.
- Envió independiente.
- Envió complementario.
- Leer los valores.


Con el script `opciones.sh`

</div>

``` bash
#/usr/bin/bash

echo "Progama opciones"
echo "Opcion 1 enviada $1"
echo "Opcion 2 enviada $2"
echo "Opcion 3 enviada $3"
echo "opciones enviadas $*"
echo -e "\n"
echo "Recuperando valores"
while [ -n "$1" ]
do
case "$1" in
        -a) echo "Opcion -a utilzada";;
        -b) echo "Opcion -b utilzada";;
        -c) echo "Opcion -c utilzada";;
        *) echo "$1 no es una opción";;
esac
shift
done
```

</div>

``` example

pi@rasp-server:~/bashCourse $ ./opciones.sh -a -b holaaaa
Programa opciones
Opcion 1 enviada -a
Opcion 2 enviada -b
Opcion 3 enviada holaaaa
opciones enviadas -a -b holaaaa


Recuperando valores
Opcion -a utilizada
Opcion -b utilizada

```

## Descargar archivos de internet

- Archivos pequeños -\> `wget`.
- Para comunicarse a un servicio (Ej. una api restful) -\> `curl`.
- Archivos grandes -\> `aria2`.

``` bash
#!/usr/bin/bash

echo "descargando información de internet"
wget https://downloads.apache.org/tomcat/tomcat-8/v8.5.54/bin/apache-tomcat-8.5.54.zip
```

# Condicionales.

## `If else`

``` bash
if [ contidion ]; then # siembre debe de haber espacios entre las llaves
    statement1
elif [ condition ]; then
    statement2
else
    statement3
fi
```

> Ejemplo:


`if.sh`

</div>

``` bash
#!/bin/bash

notaClase=0
edad=0

read -n1 -p "Indique cual es su nota: " notaClase
echo -e "\n"
if (( $notaClase >= 7 )); then # (()) y [] son lo mismo.
        echo "El alumno aprobó"
else
        echo "El alumno reprobó"
fi

read -p "Indique su edad: " edad
if [ $edad -le 19 ]; then
        echo "la persona puede sufragar"
else
        echo "La persona no puede sufragar"
fi
```

</div>

``` example

pi@rasp-server:~/bashCourse $ ./if.sh
Indique cual es su nota: 8

El alumno aprobó
Indique su edad: 19
la persona puede sufragar

```

> Para if anidados solo necesitamos un `fi`

### Operadores relacionales

`-eq`  
Igual a.

`-ne`  
No es igual a.

`-gt`  
Mayor a.

`-ge`  
Mayor igual a.

`-lt`  
Menor a.

`-le`  
Menor igual a.

## Expresiones condicionales

- `[001 = 1]` Da falso ya que la cadena de caracteres no es la misma.
- `[001 -eq 1]` es verdadero, los ceros no tienen valor.
- `-d` te permite saber si un directorio existe.
- `-e` te permite saber si un archivo existe.
- `-r` te permite saber si un archivo tiene permiso de lectura.
- `-s` te permite saber si el tamaño de un archivo es mayor a 0.
- `-w` te permite saber si un archivo tiene permisos de escritura.
- `-x` te permite saber si un archivo tiene permisos de ejecución.

### Corchetes simples `[]` vs Corchetes Dobles `[[]]`

Los dobles corchetes resultan ser una mejora respecto a los simples.
Así, las diferencias entre uno y otro son las siguientes:

- No necesitas usar comillas con las variables `[ -f "$file" ]` a
  `[[ -f $file ]]`.
- con `[[]]` puedes usar los operadores `||`, `&&` y puedes usar el
  operador `=~` para expresiones regulares.
  - `[[ $respuesta =~ ^s(i)?$ ]]`

## Sentencias `case`

``` bash

#!/bin/bash

option=""
echo "Ejemplo sentencia case"
read -p "Ingrese la opción de la A - Z: " option
echo -n "\n"

case $option in
        "A") echo "Operación guardar archivo";;
        "B") echo "Operación Eliminar archivo";;
        [C-E]) echo "No esta implementada la operación";; # <- en el rango de C a E.
        "*") "Opción incorrecta"
esac
```

# Sentencias de iteración

## Arreglos

- Para remover elementos de un arreglo se ocupa el comando
  `unset nombreArreglo[pos]`.
- Índice 0.


Script `arreglos.sh`

</div>

``` bash
#!/bin/bash

arregloNumeros=(1 2 3 4 5 6)
arregloCadenas=(Marco, Antonio, Pedro, Susana)
arregloRangos=({A..Z} {10..20})  # list comprehension


echo "Arreglo números: ${arregloNumeros[*]}" # imprime todos los elementos
echo "Arreglo de cadenas: ${arregloCadenas[*]}"
echo "Arreglo de rangos: ${arregloRangos[*]}"


echo "Arreglo números: ${#arregloNumeros[*]}" # imprime la longitud del arreglo


echo "Arreglo de cadenas: ${arregloCadenas[3]}" # elemento en posición 3


arregloNumeros[5]=20 # Cambiamos el elemento 5
unset arregloNumeros[0] # eliminamos el elemento 0
echo "Arreglo números: ${arregloNumeros[*]}"

```

</div>

``` example

pi@rasp-server:~/bashCourse $ ./arreglos.sh
Arreglo números: 1 2 3 4 5 6
Arreglo de cadenas:
Arreglo de rangos: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 10 11 12 13 14 15 16 17 18 19 20
Arreglo números: 6
Arreglo de cadenas:
Arreglo números: 2 3 4 5 20

```

## Sentencia `for`


archivo `for.sh`

</div>

``` bash
#!/bin/bash

arregloNumeros=(1 2 3 4 5 6 7)

echo "iterar en una lista de números"
for num in ${arregloNumeros[*]}
do
    echo "Numero: $num"
done

echo "Iterar en la lista de Cadenas"
for nom in "Marco" "Pedro" "Luis" "Daniela"
do
    echo "Nombres: $nom"
done

echo "Iterar en archivos"
for fil in *
do
    echo "Nombre de archivo $fil"
done

echo "Iterar con el resultado de un comando"
for fil in $(ls)
do
    echo "Nombre de archivo $fil"
done
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./for.sh
iterar en una lista de numeros
Numero: 1
Numero: 2
Numero: 3
Numero: 4
Numero: 5
Numero: 6
Numero: 7
Iterar en la lista de Cadenas
Nombres: Marco
Nombres: Pedro
Nombres: Luis
Nombres: Daniela
Iterar en archivos
Nombre de archivo argumentos.sh
Nombre de archivo arreglos.sh
Nombre de archivo case.sh
Nombre de archivo comandos.sh
Nombre de archivo descargas.sh
Nombre de archivo for.sh
Nombre de archivo if.sh
Nombre de archivo opciones.sh
Nombre de archivo test.sh
Iterar con el resultado de un comando
Nombre de archivo argumentos.sh
Nombre de archivo arreglos.sh
Nombre de archivo case.sh
Nombre de archivo comandos.sh
Nombre de archivo descargas.sh
Nombre de archivo for.sh
Nombre de archivo if.sh
Nombre de archivo opciones.sh
Nombre de archivo test.sh
```

## Sentencia `while loop`

``` bash
#!/bin/bash

numero=1

while [ $numero -ne 10 ]
do
    echo "Imprimiendo el $numero"
    numero=$(( numero + 1 ))
done
```

``` example
Imprimiendo el 1
Imprimiendo el 2
Imprimiendo el 3
Imprimiendo el 4
Imprimiendo el 5
Imprimiendo el 6
Imprimiendo el 7
Imprimiendo el 8
Imprimiendo el 9
```

## `loops` anidados


Script `forAnidado.sh`

</div>

``` bash
#!/bin/bash

echo "Loops anidados"
for fil in $(ls)
do
    for nombre in {1..4}
    do
        echo "Nombre archivo: $fil _ $nombre"
    done
done
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./forAnidado.sh
Loops anidados
Nombre archivo: argumentos.sh _ 1
Nombre archivo: argumentos.sh _ 2
Nombre archivo: argumentos.sh _ 3
Nombre archivo: argumentos.sh _ 4
Nombre archivo: arreglos.sh _ 1
Nombre archivo: arreglos.sh _ 2
Nombre archivo: arreglos.sh _ 3
Nombre archivo: arreglos.sh _ 4
Nombre archivo: case.sh _ 1
Nombre archivo: case.sh _ 2
Nombre archivo: case.sh _ 3
Nombre archivo: case.sh _ 4
Nombre archivo: comandos.sh _ 1
Nombre archivo: comandos.sh _ 2
Nombre archivo: comandos.sh _ 3
Nombre archivo: comandos.sh _ 4
Nombre archivo: descargas.sh _ 1
Nombre archivo: descargas.sh _ 2
Nombre archivo: descargas.sh _ 3
Nombre archivo: descargas.sh _ 4
Nombre archivo: forAnidado.sh _ 1
Nombre archivo: forAnidado.sh _ 2
Nombre archivo: forAnidado.sh _ 3
Nombre archivo: forAnidado.sh _ 4
Nombre archivo: for.sh _ 1
Nombre archivo: for.sh _ 2
Nombre archivo: for.sh _ 3
Nombre archivo: for.sh _ 4
Nombre archivo: if.sh _ 1
Nombre archivo: if.sh _ 2
Nombre archivo: if.sh _ 3
Nombre archivo: if.sh _ 4
Nombre archivo: opciones.sh _ 1
Nombre archivo: opciones.sh _ 2
Nombre archivo: opciones.sh _ 3
Nombre archivo: opciones.sh _ 4
Nombre archivo: test.sh _ 1
Nombre archivo: test.sh _ 2
Nombre archivo: test.sh _ 3
Nombre archivo: test.sh _ 4
```

## Utilizando las sentencias `break` y `continue`

- Se ocupa `break` para romper el loop en el que se encuentra.
- Se usa la sentencia `continue` para continuar con la siguiente
  iteración.


Script `breakContinue.sh`

</div>

``` bash
#!/bin/bash

echo "sentencia break y continue"

for fil in $(ls)
do
    for nombre in {1..4}
    do
        if [ $fil = "forAnidado.sh" ]; then
            break;
        elif [[ $fil == 4* ]]; then
            continue;
        else
            echo "Nombre de archivo: $fil - $nombre"
        fi
    done
done
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./breakContinue.sh
sentencia break y continue
Nombre de archivo: argumentos.sh - 1
Nombre de archivo: argumentos.sh - 2
Nombre de archivo: argumentos.sh - 3
Nombre de archivo: argumentos.sh - 4
Nombre de archivo: arreglos.sh - 1
Nombre de archivo: arreglos.sh - 2
Nombre de archivo: arreglos.sh - 3
Nombre de archivo: arreglos.sh - 4
Nombre de archivo: breakContinue.sh - 1
Nombre de archivo: breakContinue.sh - 2
Nombre de archivo: breakContinue.sh - 3
Nombre de archivo: breakContinue.sh - 4
Nombre de archivo: case.sh - 1
Nombre de archivo: case.sh - 2
Nombre de archivo: case.sh - 3
Nombre de archivo: case.sh - 4
Nombre de archivo: comandos.sh - 1
Nombre de archivo: comandos.sh - 2
Nombre de archivo: comandos.sh - 3
Nombre de archivo: comandos.sh - 4
Nombre de archivo: descargas.sh - 1
Nombre de archivo: descargas.sh - 2
Nombre de archivo: descargas.sh - 3
Nombre de archivo: descargas.sh - 4
Nombre de archivo: for.sh - 1
Nombre de archivo: for.sh - 2
Nombre de archivo: for.sh - 3
Nombre de archivo: for.sh - 4
Nombre de archivo: if.sh - 1
Nombre de archivo: if.sh - 2
Nombre de archivo: if.sh - 3
Nombre de archivo: if.sh - 4
Nombre de archivo: opciones.sh - 1
Nombre de archivo: opciones.sh - 2
Nombre de archivo: opciones.sh - 3
Nombre de archivo: opciones.sh - 4
Nombre de archivo: test.sh - 1
Nombre de archivo: test.sh - 2
Nombre de archivo: test.sh - 3
Nombre de archivo: test.sh - 4
pi@rasp-server:~/bashCourse $ ls
argumentos.sh  breakContinue.sh  comandos.sh   forAnidado.sh  if.sh        test.sh
arreglos.sh    case.sh           descargas.sh  for.sh         opciones.sh
pi@rasp-server:~/bashCourse $
```

### Generando un menú de opciones

``` bash
#!/bin/bash

opcion=0

while:
do
    clear # limpiar pantalla
    # desplegar menu de opciones
    echo "___________________________________"
    echo "_____________ MENU X ______________"
    echo "___________________________________"
    echo "1. Haz x cosa."
    echo "2. Haz y cosa."
    echo "3. salir."

    # Leer los datos del usuario
    read -n1 -p "Ingrese una opción [1-3]: " opcion

    # validar la opción
    case $opcion in
        1)
            echo -e "\nInstalandoooo x..."
            sleep 3

            .
            .
            .
```

# Archivos

## Creación de archivos y directorios

- Directorios `mkdir nombreDirectorio`.
- Archivos `touch nombreArchivo`.


Script `archivosDir.sh`

</div>

``` bash
#!/bin/bash

echo "Archivos - Directorios"

if [ $1 = "d" ]; then
    mkdir -m 755 $2
    echo "Directorio creado correctamente"
    ls -la $2
elif [ $1 == "f" ]; then
    touch $2
    echo "Archivo creado correctamente"
    ls -la $2
else
    echo "No existe esa opción: $1"
fi
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./archivosDir.sh d dirTest
Archivos - Directorios
Directorio creado correctamente
total 8
drwxr-xr-x 2 pi pi 4096 Mar 28 19:13 .
drwxr-xr-x 3 pi pi 4096 Mar 28 19:13 ..
pi@rasp-server:~/bashCourse $ ls
archivosDir.sh  arreglos.sh       case.sh      descargas.sh  forAnidado.sh  if.sh        test.sh
argumentos.sh   breakContinue.sh  comandos.sh  dirTest       for.sh         opciones.sh
pi@rasp-server:~/bashCourse $ ./archivosDir.sh f archTest
Archivos - Directorios
Archivo creado correctamente
-rw-r--r-- 1 pi pi 0 Mar 28 19:13 archTest
pi@rasp-server:~/bashCourse $
```

## Escribir dentro de un archivo

Podemos utilizar el comando `echo` así como el comando `cat`.


Script `writeFile.sh`

</div>

``` bash
#/bin/bash

echo "Escribir en un archivo"
echo "Valores escritos con el comando echo" >> $1 # mandamos la cadena a la variable $1

# adición multininea
cat <<EOM>>$1 # EOM=END OF MESSAGE
$2
EOM
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./writeFile.sh archivo.txt algooooo
Escribir en un archivo
pi@rasp-server:~/bashCourse $ cat archivo.txt
Valores escritos con el comando echo
algooooo
```

## Leer de un archivo

Script `readFile.sh`

</div>

``` bash
#!/bin/bash

echo "Leer de un archivo"
cat $1
echo -e "\nAlmacenar los valores en una variable"
valorCat=`cat $1`
echo "$valorCat"

# se utiliza la variable IFS (Internal Field Separator) para evitar que los espacios en blanco al inicio o al final se recorten
echo -e "\nLeer archivos linea por linea"
while IFS= read linea
do
    echo "$linea"
done < $1
```

</div>

``` example
pi@rasp-server:~/bashCourse $ ./readFile.sh archivo.txt
Leer de un archivo
Valores escritos con el comando echo
algooooo

Almacenar los valores en una variable
Valores escritos con el comando echo
algooooo

Leer archivos linea por linea
Valores escritos con el comando echo
algooooo
```

## Copiar, mover y eliminar archivos

- Una vez creado el archivo se pueden hacer varias operaciones sobre el
  como `cp` copiar, `mv` mover o `rm` eliminar.

``` bash
#!/bin/bash

echo "Operaciones de un archivo"
mkdir -m 755 backupScripts
echo -e "\nCopiar los scripts del directorio actual al nuevo directorio backupScripts"
cp *.* backupScripts/ # copiamos todos los scripts de la carpeta actual a la nueva carpeta
ls -la backupScripts/

echo -e "\nMover el directorio backupScript a otra ubicación: $HOME"
mv backupScripts $HOME

echo -e "\nEliminar los archivos .txt"
rm *.txt
```
## Empaquetamiento

**tar**
Empaqueta múltiples archivos>

**gzip**
Comprime un archivo.

## Empaquetamiento de archivos usando `tar`

``` bash
#!/bin/bash

echo "Empaquetar algo en un tar"
tar -cvf shellCourse.tar *.sh
```

## Empaquetamiento con `gzip`

- `gzip` solo puede ser aplicado para comprimir un archivo simple o un
  flujo de datos; es decir, no puede comprimir carpetas.
- permite configurar el ratio de compresión de 1 a 9, siento 1 la más
  baja pero más rápida y 9 la más alta pero la más lenta.

``` bash
#!/bin/bash

echo "Empaquetar todos los scripts de la carpeta shellCourse"
tar -cvf shellCourse.tar *.sh

# cuando se empaqueta con gzip el empaquetamiento anterior se elimina.
gzip shellCourse.tar

echo "Empaquetar un solo archivo, con un ratio de 9"
gzip -9 9_options.sh
```

## Empaquetamiento con clave
```bash
echo "Empaquetar todos los scripts de la carpeta con zip y asignarle la clave de seguridad"
zip -e shellCourse.zip *.sh
```

## Transferir información red
```bash
host = ""
usuario = ""

echo "mandando archivos por la red"
read -p "Ingresar el host:" host
read -p "Ingresar el usuario:" usuario
echo -e "\n En este momento se procederá a empaquetar la carpeta y transferirla según los datos dados\n"

rsync -avz $(pwd) $usuario@$hostA:/home/$usuario
# podemos hacer la operación inversa (traernos los archivos de un host remoto con)
# $rsync -avz user@host/directory 
```

# Funciones

- Son bloques de código con funcionalidad especifica que existen en
  memoria y que ayudan a organizar el código del programa

## Creando funciones

``` bash
#!/bin/bash

opcion=0

# función para instalar sql
instalarSQL() {
    echo "instalando SQL"
}

desinstalarSQL() {
    echo "desinstalando SQL"
}

# ...
```

## Llamando funciones

``` bash
# ...

case $option in
    1)
        instalarSQL
        sleep 3
        ;;
    2)
        desinstalarSQL
        sleep 3
        ;;

# ...
```

## Paso de argumentos a una función

``` bash

sacarRespaldo () {
    echo "Sacar respaldo"
    echo "Directorio backup" $1
}

restaurarRespaldo () {
    echo "restaurar respaldo"
    echo "Directorio respaldo" $1
}

# ...

case $option in
    1)
        read -p "Directorio backup: " directorioBackup
        sacarRespaldo $directorioBackup
        sleep 3
        ;;
    2)
        read -p "Directorio respaldos" directorioRespaldos
        restaurarRespaldo $directorioRespaldos
        sleep 3
        ;;

# ...
```

## Ejecutar función en segundo plano

- Para ejecutar una función o comando se utiliza el operador `&`.

-