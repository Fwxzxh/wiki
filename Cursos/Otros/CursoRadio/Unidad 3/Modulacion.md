# Modulación

> [!info]
> Consiste en trasladar mensajes en forma de [[señales]] eléctricas a una frecuencia más elevada con respecto a aquellas en las que se producen; a esta frecuencia se le conoce como *banda base*.

La modulación coloca los mensajes a lo largo de frecuencias previamente definidas en el espectro radioeléctrico.
Las [[señales]] eléctricas moduladas son convertidas en [[señales]] electromagnéticas y transmitidas como ondas, mismas que son recibidas por otro dispositivo y trasladadas a su banda base para que puedan ser escuchadas.

Los equipos de radio cuentan con:
- Un dispositivo que modula los mensajes y los transmite (el transmisor).
- Otro que los recibe y los regresa a su banda base (el receptor).

Cuando la distancia entre el emisor y el receptor es muy larga, podemos convertir las [[señales]] eléctricas en ondas electromagnéticas, agregarles potencia y transmitirlas en por el espacio libre.

A grandes rasgos, este es el proceso de las [[radiocomunicaciones]].

> [!info] Objetivo
> Lograr que un mensaje (voz, música, datos, etc), a trávez de las ondas radioeléctricas llegue a la mayor distancia con la mejor calidad posible, es decir; el proceso mediante el cual se cumple con el esquema de la [[comunicación]].

La información producida en *banda base* no es adecuada para ser transmitida como señal electromagnética. Por eso es necesario modificarla.

En la modulación participan dos [[señales]]:
- Moduladora:
	- Es el mensaje que se desea transmitir en su banda base.
- Portadora:
	- Es una señal de alta frecuencia que es modificada por la moduladora en alguna de sus 3 características:
		- Amplitud
		- Frecuencia
		- Fase
	- Es el equivalente a un vehículo que lleva la información a frecuencias superiores para lograr su transmisión.

![[ProcesoModulacion.png]]

Entonces...

> [!info] Modulación
> Se refiere a alterar las características de una señal portadora para transmitir un mensaje.
# Técnicas de modulación

Hay 3 técnicas de modulación:
1. Modulación en amplitud (AM).
2. Modulación en frecuencia (FM).
3. Modulación en fase (PM)

![[TecnicasModulacion.png]]

> Para cada técnica aplican combinaciones entre la forma analógica, moduladora y portadora.

- **Analógico-Analógico**: AM, FM, PM.
- **Analógico-Digital**: ASK, FSK, PSK.
- **Digital-Analógico**: PAM, PWM, PCM.

## Amplitud Modulada

El modo más antiguo de transmisión de voz y el standard usado en radio.


![[EsquemaFuncionalAM.png]]

1. Señal Portadora:
	- Es una onda de alta frecuencia, generada por un **ocilador**.
	- Actúa como la "portadora del mensaje".
2. Señal Moduladora:
	- Es la **información** que se desea transmitir.
	- Es una señal de baja frecuencia generada por una **fuente analógica**.
3. Modulador AM:
	- Combina la *señal portadora* y la *señal moduladora*.
	- Cambia la amplitud de la portadora según la forma de la *señal moduladora*.
		- El resultado es la **señal modulada en amplitud**.
4. Señal modulada en Amplitud:
	- Es una señal cuya amplitud (la altura de las crestas) varia en función de la información original.
	- Esta señal puede ser transmitida a largas distancias por radiofrecuencia.

![[señal_modulada_am.svg]]

> Ejemplo de una señal AM modulada.

:TODO: Agregar el espectro en frecuencias AM

Una modulación pura en AM representa varios inconvenientes:
- Uno de ellos es la repetición de la información
	- Teniendo como centro la portadora, la información se repite a la izquierda y a la derecha de esta;
		- Se requ