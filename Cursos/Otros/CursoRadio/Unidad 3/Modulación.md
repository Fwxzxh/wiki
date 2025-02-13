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

```python
import numpy as np
import matplotlib.pyplot as plt

# Configuración de la señal
fs = 1e5  # Frecuencia de muestreo (100 kHz)
t = np.arange(-3e-3, 3e-3, 1/fs)  # Vector de tiempo de -3 ms a 3 ms
fm = 1e3  # Frecuencia de la señal mensaje (1 kHz)
fc = 10e3  # Frecuencia portadora (10 kHz)
Am = 1  # Amplitud de la señal mensaje
Ac = 1  # Amplitud de la portadora
mod_index = 0.5  # Índice de modulación

# Señal mensaje
m_t = Am * np.sin(2 * np.pi * fm * t)

# Señal modulada en amplitud (AM-DSB)
s_t = Ac * (1 + mod_index * np.sin(2 * np.pi * fm * t)) * np.cos(2 * np.pi * fc * t)

# Transformadas de Fourier
frequencies = np.fft.fftfreq(len(t), 1/fs)
m_f = np.fft.fft(m_t)
s_f = np.fft.fft(s_t)

# Filtrar solo las frecuencias positivas
positive_freq = frequencies > 0

# Crear los gráficos
plt.figure(figsize=(12, 8))

# Señal mensaje en el dominio del tiempo
plt.subplot(2, 2, 1)
plt.plot(t * 1e3, m_t, color='blue')
plt.title("Señal mensaje")
plt.xlabel("Tiempo (ms)")
plt.ylabel("Amplitud")
plt.grid()

# Magnitud del espectro de la señal mensaje (ajustar a -2 a 2 kHz)
plt.subplot(2, 2, 2)
plt.plot(frequencies[positive_freq] / 1e3, np.abs(m_f[positive_freq]), color='blue')
plt.title("Magnitud del espectro de la señal mensaje m(t)")
plt.xlabel("Frecuencia (kHz)")
plt.ylabel("Magnitud")
plt.xlim(0, 2)  # Escala ajustada
plt.grid()

# Señal AM-DSB en el dominio del tiempo
plt.subplot(2, 2, 3)
plt.plot(t * 1e3, s_t, color='blue')
plt.title("Señal AM DSB")
plt.xlabel("Tiempo (ms)")
plt.ylabel("Amplitud")
plt.grid()

# Respuesta de frecuencia de la señal AM-DSB (ajustar a -2 a 2 kHz)
plt.subplot(2, 2, 4)
plt.plot(frequencies[positive_freq] / 1e3, np.abs(s_f[positive_freq]), color='blue')
plt.title("Respuesta de frecuencia de la señal DSB")
plt.xlabel("Frecuencia (kHz)")
plt.ylabel("Magnitud")
plt.xlim(7, 13)  # Escala ajustada
plt.grid()

plt.tight_layout()
plt.show()
```


![[EspectroFrecuenciasAM.png]]

```python
import numpy as np
import matplotlib.pyplot as plt

# Configuración de la señal
fs = 1e5 # Frecuencia de muestreo (100 kHz)
t = np.arange(-5e-3, 5e-3, 1/fs) # Vector de tiempo de -5 ms a 5 ms
fm = 1e3 # Frecuencia de la señal mensaje (1 kHz)
fc = 10e3 # Frecuencia portadora (10 kHz)
Am = 1 # Amplitud de la señal mensaje
Ac = 1 # Amplitud de la portadora

# Señal mensaje (banda base)
m_t = Am * np.cos(2 * np.pi * fm * t)

# Señal AM pura
s_t = Ac * (1 + m_t) * np.cos(2 * np.pi * fc * t)

# Transformada de Fourier
frequencies = np.fft.fftfreq(len(t), 1/fs)
s_f = np.fft.fft(s_t)

# Filtrar frecuencias positivas para visualizar mejor
positive_freq = frequencies > 0

# Crear los gráficos
plt.figure(figsize=(10, 6))

# Espectro de la señal AM (frecuencias positivas) con escala ajustada
plt.plot(frequencies[positive_freq] / 1e3, np.abs(s_f[positive_freq]), color='blue')
plt.title("Duplicación de la información en AM (Espectro de Frecuencia)")
plt.xlabel("Frecuencia (kHz)")
plt.ylabel("Magnitud")
plt.xlim(8, 12) # Escala ajustada alrededor de la portadora (10 kHz)
plt.grid()

# Resaltar las bandas laterales
plt.axvline((fc + fm) / 1e3, color='green', linestyle='--', label="Banda Lateral Superior")
plt.axvline(fc / 1e3, color='orange', linestyle='--', label="Portadora")

plt.legend()
plt.tight_layout()
plt.show()
```

![[EspectroFrecuenciasAM2.png]]


Una modulación pura en AM representa varios inconvenientes:
- Uno de ellos es la repetición de la información
	- Teniendo como centro la portadora, la información se repite a la izquierda y a la derecha de esta.
		- Se requiere el doble de la banda base para su transmisión.

### Banda lateral única

Conocida como SSD (Single Side Band), es una forma más avanzada de modulación AM.

A travez de filtros, se reducen los elementos no deseados y repetidos.
1. Se utiliza un filtro paso-banda del doble de ancho de banda centrado en la espiga positiva de la portadora.
2. Se conserva la portadora y dos componentes a cada lado, cada uno del ancho de la banda base.

![[SSB.png]]

Bajo este esquema sólo es necesario tomar una de las bandas laterales ya que ambas contienen la misma información y así reducir el ancho de banda necesario para la transmisión.

### Banda lateral única con portadora suprimida

Para transmitir una señal modulada bajo cualquier técnica se debe agregar potencia a la señal, por lo que es deseable que la mayoría de la potencia disponible en el transmisor se invierta de la mejor manera.

Una vez modulada la portadora (transladando el mensaje a una frecuencia superior) podría no ser necesario transmitir a la portadora.

La portadora es necesaria para demodular el mensaje. Si el equipo transmisor y el receptor están sintonizados a la misma frecuencia, entonces se puede eliminar la portadora al transmitir y el receptor puede agregarla cuando demodule la señal.

> A este proceso se le conoce como: `banda lateral única con portadora suprimida`.

### Ventajas y desventajas del AM

Ventajas:
- Los circuitos transmisores y receptores son sencillos y baratos.
- Las distancias de transmisión son muy grandes.
- En varios lugares solo es posible la recepción de AM.

Desventajas:
- Es sensiblemente afectada por fenómenos atmosféricos y a las interferencias.
- Perdida de calidad en la señal.
- Desperdicio de potencia si no se eliminan las bandas laterales.

## Modulación en Fase

> [!info] 
> En esta técnica la fase de la portadora varía directamente proporcional a la amplitud de la moduladora.

No es una técnica muy usada debido a la complejidad de los dispositivos electrónicos.

## Técnicas de modulación de moduladoras digitales con portadoras analógicas

En estas técnicas las información o moduladora es de naturaleza digital, Generalmente binaria con estados eléctricos equivalentes al 0 y 1.

Hay 3 técnicas de este tipo:
1. Modulación por desplazamiento de amplitud (*Amplitude shift keying* o ASK).
2. Modulación por cambio de frecuencia (*Frecuency shift keying* o FSK).
3. Modulación por cambio de fase (*Phase shift keying* o PSF).

### Modulación por desplazamiento de amplitud ASK

> [!info]
> La modulación ASK usa los cambios en la amplitud de una señal portadora para transmitir información digital (1's y 0's).

Se basa en los siguientes principios:
1. Bit 1: La portadora tiene una amplitud determinada.
2. Bit 0: La portadora no tiene amplitud (es cero).

![[ASKModulation.png]]

1. Señal portadora:
	- Es una onda sinusoidal con frecuencia especifica que sirve como base para transmitir datos.
2. Señal digital de banda base:
	- Representa la información que se desea transmitir, en forma de una serie de bits (1 y 0's).
3. Modulador ASK.
	- Es el dispositivo que combina la señal digital y la portadora.
		- Genera la señal modulada en amplitud.
		- Cuando el bit es 1, la señal portadora aparece con amplitud alta.
		- Cuando el bit es 0 la portadora desaparece.

ASK puede ser vulnerable, ya que el ruido puede alterar fácilmente la amplitud y afectar la interpretación de los bits.

### Modulación por cambio de frecuencia FSK

> [!info]
> En la modulación FSK existe una frecuencia para el estado 1 y una segunda para el estado 0, analógicamente, es como si se tuviera un interruptor que selecciona una de las dos frecuencias.

![[FSKModulation.png]]

### Modulación por cambio de fase PSK

> [!info]
> Utiliza los cambios de estado lógico de la moduladora para producir un cambio de fase en la portadora, Si la señal binaria no cambia de estado la portadora se mantiene sin cambio

![[PSKModulation.png]]

En función de la diferencia de fase existen cuatro tipos de modulación PKS:
1. Bifásica
2. Tetrafásica
3. Cuadratura (QAM8).

### Técnicas de modulación de moduladoras analógicas con portadoras digitales

En estas técnicas, el mensaje es discreteado a travéz del muestreo para crear un tren de pulsos con las tres características propias de una señal:

1. Amplitud
2. Frecuencia
3. Fase

Las técnicas de modulación son:
1. Modulación por amplitud de pulso (Pulse amplitude modulation PAM)
2. Modulación por ancho de pulso (Pulse wide modulation PWM)
3. Modulación por posición de pulso (Pulse position modulation PPM)
4. Modulación por codificación de pulsos (Pulse code modulation PCM)

#### Modulación por amplitud de pulso PAM

Las variaciones en la amplitud de la portadora analógica se reflejan en la amplitud de los pulsos.

![[PAMModulation.png]]

Como la información esta en la amplitud, cualquier ruido en el canal puede afectar la calidad de la señal.

#### Modulación por ancho de pulso PWM

La información en la moduladora se refleja en las variaciones de la amplitud del ancho de los pulsos obtenidos en el muestreo.

![[PWMModulation.png]]

#### Modulación por posición del pulso PPM

La información es transmitida mapeando las variaciones de amplitud de la moduladora en variaciones de posición de los pulsos dentro de un rango de posiciones obtenidos de muestreo.

![[PPMModulation.png]]

#### Modulación por codificación de pulsos PCM

La información es transmitida mapeando las variaciones de amplitud de la moduladora analógica en variaciones en la amplitud de los pulsos obtenidos del muestreo (PAM);

La señal muestreada es procesada por un retenedor/cuantificador que asigna el nivel eléctrico correspondiente a la altura de cada pulso, un codificador asigna una trama de bits de acuerdo con el nivel eléctrico del pulso, codificando su amplitud.

![[PCMModulation.png]]

### Técnicas de modulación de moduladoras digitales con portadoras digitales

Hay sistemas de telefonía celular (TDMA, GSM, etc) y de voz con TCP/IP (VoIP) o el radio móvil digital (DMR).

No son directamente utilizadas en el servicio de aficionados.

## Modos digitales en la radioafición

### Telegrafía (Continous wave o CW)

Fue el primer modo de radiocomunicación y al mismo tiempo, el primer modo digital.

Para transmitir un mensaje se utliza el código Morse.

Este es la traducción del alfabeto a una secuencia de puntos y rayas.

![[MorseCode.png]]