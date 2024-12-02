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
	- Teniendo como centro la portadora, la información se repite a la izquierda y a la derecha de esta;
		- Se requ