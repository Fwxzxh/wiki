---
title: Fundamentos de Ingeniería de software
description: Apuntes sobre el curso, fundamentos de ingeniería de software
published: true
date: 2022-12-24T17:17:51.334Z
tags: software, fundamentos, ingeniería, email, bits, bytes, circuitos, cpu, redes, ip, sistemas operativos, metadatos
editor: markdown
dateCreated: 2022-12-24T17:17:46.118Z
---

# Computación, procesadores y memoria

## Cómo funcionan los correos electrónicos

En orden:

1.  Señal del teclado al presionar enter.
2.  Tarjeta madre
3.  CPU
4.  Sistema operativo (Drivers)
5.  Navegador de internet (recibe el enter)
6.  Evento del Navegador (en javascript)
7.  Javascript va a encapsular todo en una API
    1.  Aplication Program Interface - una interfaz para computadoras.
    2.  AJAX - Asyncronous JavaScript and XML.
        - Podemos enviar cualquier cosa que queramos a un servidor sin
          recargar la página.
        - Ecapsulan JSON
    3.  JSON - JavaScript Object Notation
    4.  REST - Representational State Transfer
        - El método de envio
    5.  HTTP - Hypertext transfer protocol
        - Protocolo de transferencia.
8.  URLs
    1.  `https://gmail.com/evias_email`
    2.  https - Llave de cifrado con el servidor, permite una conexión
        segura.
    3.  gmail.com - Dominio
        - DNS - Domain Name Server
          - Una base de datos que liga una IP a un nombre de dominio.
    4.  `/envias_email` - La instrución al servidor.
9.  Servidor - Corriendo en Linux
    1.  Ethernet
    2.  TCP/IP
    3.  HTTP
    4.  Servidores web (ngix, apache)
    5.  Lenguaje de programación (java)
10. Base de datos
    1.  MySql, Postgres, Oracle
11. Servidor de correo
    - Protocolos de correo
      - SMTP - Simple Mail Transfer Protocol
      - POP3 - Post Office Protocol
    - Servidores de correo
      - PostFix

## Qué es un `system on a chip`

- La combinación de los diferentes componentes que hacen una computadora
- Se compone de:
  - Bios: Arranca nuestro sistema.
  - Ram: Se encarga de guardar rápidamente todos los datos a los que
    queremos acceder.
  - CPU: Se encarga de procesar todo por dentro
  - Chip de Radio: Controla las señales, wifi, Bluetooth o celular.
  - GPU: Se encarga de hacer la representación gráfica de nuestro
    sistema.
  - Periféricos: Es el medio entre nosotros y el sistema.
  - Batería: Da energía al sistema y contiene su propio controlador.

## Qué son Bits y bytes

- Todo viene de las ondas eléctricas.
- Descubrimos que podemos modularlas y usarlas para transmitir
  información
- Modulandolas podemos usarlas para representar 0s y 1s
  - Estos son los bits, las partes altas y bajas de las ondas.
- IBM en los 50 definió el concepto de byte.
  - Un byte fue definido con 8 espacios (8 bits)
- Bit: Unidad mínima de información 0s y 1s.
- Bytes: Compuestos por 8 Bits, cada uno tiene un valor posicional y
  corresponde a uno de los 8 primeros lugares de una tabla de sistema
  binario.

## Como funcionan los circuitos electrónicos

- Son la base de la tecnología moderna.
- La electricidad es un flujo constante de electrones y se mide en
  voltaje y amperage.
  - Los voltios son la fuerza que mueve la electricidad por un cable.
    - Moviéndola del negativo de una batería al positivo.
    - El negativo también se conoce como polo a tierra (ground).
    - Podemos pensar en el voltaje como la presión de agua de una
      tubería.
  - El ohmio representa la resistencia que se opone a la electricidad.
  - El amperio representa la intensidad de corriente o cuanta corriente
    pasa por un circuito.
- Podemos crear movimiento con un motor eléctrico.
  - Por dentro tiene electro imanes, los cuales se repelen en un anillo
    metálico rotando sobre su propio eje.
- La electricidad se vuelve sonido cuando haces vibrar una membrana al
  ritmo de una onda eléctrica.
- Un circuito digital convierte las ondas eléctricas en 0s y 1s.

## Procesadores y arquitecturas de CPU

- los procesadores son los cerebros de las computadoras.
  - Tienen Ghz que son la cantidad de operaciones que pueden hacer por
    minuto.
  - Tienen Cores que son la cantidad de operaciones paralelas que pueden
    realizar.
  - Están hechas de silicio.
- Las CPUs requieren información.
  - La información primero viene de la BIOS que es un pequeño sistema
    operativo de arranque.
  - Lo primero que hace es verificar que cosas están conectadas a la
    computadora.
    - Disco duro, teclado, mouse.
- El Sistema operativo se carga a la memoria RAM.
  - La memoria RAM es más rápida que la del disco duro.
  - La memoria RAM es volátil, se borra cada que se pierde la
    electricidad.
- Las pantallas requieren de una GPU.
  - Las GPU son chips que están hechas para procesar gráficos den manera
    eficiente.
  - Es buena para hacer procesos en paralelo.

## Qué es la memoria RAM y cómo funcionan los discos duros.

- Disco duro
  - Memoria persistente.
  - Guarda archivos de manera secuencial.
  - Se guardan de manera estructurada.
    - Sistemas de archivos (dados por el sistema operativo).
  - En la cabecera de el sistema de archivos tenemos un índice.
    - Tiene una lista de archivos y las direcciones en donde están.
  - Cuando borramos archivos, solo eliminamos la entrada de ese archivo
    en la cabecera.
- Memoria cache.
  - La memoria más rápida de la computadora.
  - Esta en la CPU.
  - Aquí se guardan cosas esenciales para el CPU.
- RAM.
  - Allí vive el sistema operativo junto con los archivos que están en
    uso.
  - La CPU siempre sabe donde esta todo, son las direcciones de memoria.
    - Es muy rápida.
- Las conexiones entre los componentes se llaman bus de datos.

## GPUs

- La GPU se encarga de los gráficos en la computadora.
- Tiene su propia RAM (VRAM), GHz y cores.
  - Generalmente no tienen tantos GHz como el CPU.
  - Tienen mucho más cores que la CPU.
    - Esto les ayuda a representar los pixeles de la pantalla.
- También cuentan con Operadores 3D y Codecs para optimizar algunas
  operaciones gráficas.

## Periféricos y sistemas de entrada de información

- El kernel es la parte más importante del Sistema Operativo.
  - Es lo primero que se carga a la RAM y carga todo el hardware de la
    computadora.
  - Contiene los Drivers para comunicarse con los periféricos.
- Los sistemas operativos tienen diferentes anillos de acceso.
  - 0: Kernel
  - 1: Drivers
  - 2: Drivers especializados
  - 3: Apps
- Entre Más alto sea el número, tienen menos permisos.

# Cómo funciona Internet

## Introducción a las redes, protocolos e internet

- Ethernet: cable de red
- IP (Internet Protocol): matricula que te define dentro de una red.
- Switch (Conmutador): Aparato que conecta varios dispositivos a una red
  mediante Ethernet.
- Router (Enrutador): Aparato que interconecta varios dispositivos, se
  encarga de enrutar cada paquete de datos dentro de una red.
- DHPC: Protocolo que asigna dinámicamente una IP en una red.
- Dirección MAC: identificador único que esta grabado en la interfaz de
  red de cada dispositivo.
  - Los dispositivos con más de una interfaz tienen más de una mac.
- Modem: Aparato que convierte las señales digitales a analógicas y
  viceversa.
- ISP: (Internet Service Provider) Proveedor de servicio de internet.

## Puertos y protocolos de red

- Podemos tener diferentes IPs.
  - Tenemos una IP interna, la cual nos identifica en nuestra red.
    - Los routers Deciden que IP obtenemos en la red local.
  - Tenemos una IP pública, la cual nos identifica en internet.
- Tenemos una IP que apunta a la IP de nuestro dispositivo.
  - 127.0.0.1 también llamada `localhost`.
- También tenemos una IP LAN.
  - Esa apunta a la IP de nuestra red.
  - Generalmente es 192.168.0.XXX
- Cada uno de los números de las IPs identifica cuantas subredes podemos
  tener.
- Generalmente las IPs que terminan en 255 se usan para broadcast.
- Tenemos redes internas de la computadora con puertos.
  - Tenemos 65,535, puertos:
    - Dos bytes disponibles para definir puertos
  - Los puertos del 1 al 1024, son puertos reservados para el sistema
    operativo.
  - El protocolo HTTP tiene asignado el puerto 80.

## Qué es una dirección IP y el protocolo de internet

- Una IP 192.168.10.50.
  - Tiene 4 bytes (cada numero).
    - 32 Bits.
    - Hablando de su representación binaria.
- Mascaras de red:
  - Nos indica que bytes de la IP no pueden y si pueden cambiar dentro
    de una red.
  - Hay clases:
    - Clase A: 255.0.0.0
    - Clase B: 255.255.0.0
    - Clase C: 255.255.255.0
  - También hay mascaras variables.
  - Nos números indican que bytes pueden cambiar, en este caso el 255
    indica que ningún byte puede cambiar para la IP.
- `Gateway`:
  - La IP del router de la red.

## Cables Submarinos, antenas y satélites en internet

- Internet funciona globalmente con cables submarinos.
- Las ISP son las que conectan nuestras casas a el internet.
- Los que conectan a los países/continentes se llaman IXP (internet
  exchange points).
- Los ISP se conectan a los cables submarinos mediante los IXP.
  - Dándonos acceso a internet.

## Qué es un dominio, DNS o Domain Name System

- Servidores que tienen una base de datos la cual indica a que nombre o
  dirección corresponde una IP.
- Hay muchos Servidores distribuidos por el mundo, y tienen copias de la
  base de datos.
- También tienen subdominios.
  - Por ejemplo las versiones móviles de diferentes sitios.
- También tienen los nombres para los emails.
- MXRecord:
  - Donde se encuentra la IP de un servidor de email.
- Se tiene una copia local de los DNS en cada PC.
  - Allí por ejemplo se guarda localhost para que sea 127.0.0.1.
    - Podríamos cambiarlo a otra ip allí.

## Cómo los ISP hacen Quality of Service QoS

- Los ISP crean prioridad en la red.
  - También dependiendo de el tipo de trafico le dan prioridad o no.
- Se le llama *Throtling* también.
- Van regulando la velocidad de ciertos sitios dentro de la red.
  - Todo para el usuario final.
- Para saltarse estos problemas se inventaron los CDNs.
  - Content delivery network.
  - Replican archivos estáticos por todo el mundo.
  - Para que los archivos internos estén más cerca del usuario final.
  - Están conectados o en los IXP.

## Cómo funciona la velocidad en internet

- Conectarnos a internet es como pasar agua por un tubo.
- 10 Mbps.
  - Mega bits, 10/8 = 1.25 MB/s
  - Es la cantidad de agua que cabe en la 'tuberia'
- El ping es cuanto tarda la conexión en establecerse.
  - Se mide en ms.
  - Es la velocidad real de la conexión.
  - Es lo que tarda un bit para llegar de un lugar a otro.
  - Seria la presión del tubo de agua.
- Podemos entender la velocidad minima comparandola con la velocidad de
  la luz.
  - La luz viaja 300 km/ms (kilometros/Milisegundo).
  - Si hay 9344 km desde Mountain View a Madrid.
    - El ping Minimo posible es de 31.14 ms.
- Las ISP venden el ancho de banda, La cantidad de bytes que pueden
  viajar al mismo tiempo.
  - AKA: El tamaño de la tubería.

## Qué es el modelo Cliente/Servidor

- Frontend
  - Es lo que un usuario ve de un sitio web.
- Backend
  - Son las acciones que se realizan cuando interactuamos con la página
    web.
  - Involucra conexiones a bases de datos y todo lo que ocurre en el
    servidor.
- El modelo Cliente/Servidor es la relación que existe entre el frontend
  y el backend.
  - Cliente (Navegador que lee HTML, CSS y JS).
  - El Backend recibe una solicitud y toma decisiones en base a ella.

## Cómo funciona realmente un sitio web.

- Cuando entramos a un sitio web:
  1.  Primero le preguntamos al DNS del sistema operativo si tiene la ip
      para ese dominio.
      - Si no lo tiene le pregunta a un servidor DNS remoto
  2.  Usamos una request HTTP GET.
      - La cual la recibe el Servidor en el puerto 80.
  3.  El servidor nos responde la petición.
      - Nos da un 200 OK o un 404, dependiendo de lo que pase.
      - Se le llama HTTP Response.
  4.  `Assets Request`
      - Volvemos al punto 1.
      - Obtenemos imágenes y otras cosas que necesita la pag web.
- Cookies
  - Son variables.
  - Se pegan al request y en las response.

# Sistemas Operativos

## Permisos, niveles de procesos y privilegios de ejecución

- Los permisos son los siguientes:
  - R: Read
  - W: Write
  - X: Execute
- Podemos dar permisos con el comando `chmod`
  - Podemos dar los permisos de manera numérica.
    - En \*nix hay diferentes grupos para los permisos.
      - Dueño del archivo
      - Grupo.
      - Todos los usuarios.
    - Podemos manejar los permisos de manera numérica.
      - 777, Sería darle todos los permisos a todos los grupos.
        - cada dígito, corresponde a los permisos de un grupo.
          - y cada dígito esta formado por 3 bits binarios que
            corresponden a:
            - 4,2,1
              - Si tenemos los 3 bits en 1, suman 7 (111) == 777j
              - Si tenemos solo el primero es 4 (100) 4
              - Si tenemos el primero y el último (101) 5
              - Cada dígito, corresponde a R,W,X en ese orden.
            - Damos 3 números (9 bits) ya que cada uno representa los
              permisos de un grupo.

# Archivos y estructuras de datos

## Metadatos, cabeceras y extensiones de archivos

- Los metadatos:
  - Son datos estructurados que describen el contenido y otras
    características de un archivo o datos.
- Cuando abrimos un archivo binario en un editor de texto.
  - Veremos caracteres raros, que representan el código binario.
  - Hay editores especiales para editar binario.
- Un sistema operativo lee la cabecera del archivo para saber que hacer
  con un archivo.
  - Cuando no se puede se usan `mime types`.
    - Originalmente fue hecho para email.
    - Tiene dos partes.
      - La primera es el tipo de archivo
      - El segundo es el formato.
      - EJ: image/jpeg, text/html,
