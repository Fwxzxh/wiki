# Voltaje y corriente eléctrica

## Ley de Ohm

> [!info]
> Explica la relación que existe entre voltaje, corriente y resistencia en un material.


![[LeyOhm.png]]

En un circuito, un mayor voltaje impulsa una mayor corriente, pero esta también depende de la resistencia del material.

## Voltaje (Diferencia de potencial)
- Cantidad de energía que se transfiere por unidad de carga entre dos puntos de un circuito.
- Se mide en **voltios (V)**.
- Representa la "presión eléctrica" que impulsa a las cargas a moverse a través de un conductor.
- Es como la fuerza que empuja el agua en una tubería.

## Corriente eléctrica
- Es el flujo de cargas eléctricas (generalmente electrones) a través de un conductor.
- Se mide en **Amperios (A)**.
- Representa la cantidad de *carga* que pasa por un punto del circuito en un segundo.
- Es como el flujo de agua que realmente pasa por una tubería.

# Resistencia, Impedancia y potencia.

- Resistencia e impedancia afectan la corriente en el circuito.
- Potencia depende del voltaje, la corriente y el factor de potencia.

## Resistencia
- Es la oposición que un material ofrece al flujo de corriente eléctrica.
- Se mide en **Ohmnios ($\Omega$)**.
- Depende de las prioridades del material, su longitud, área de sección transversal y temperatura.
- Se utiliza cuando se trabaja con voltajes y corrientes directas (que no varían en el tiempo).
- Es como la fricción que ralentiza el flujo de agua en una tubería.

## Impedancia
- Es la generalización de la resistencia para circuitos de corriente alterna (CA).
- Se mide en **Ohmios**, pero incluye tanto la **resistencia** como la oposición adicional causada por elementos inductivos y capacitivos.
- Tiene dos componentes:
	- **Resistencia (R)**: Oposición al flujo de corrientes continua y alterna.
	- **Reactancia (X)**: Oposición especifica a cambios en la corriente alterna debido a inductores y condensadores.
- Se utiliza en lugar de la resistencia cuando se trabaja con corrientes alternas (que varían en el tiempo).
- Es como la combinación de fricción y efectos inerciales en el flujo de agua de un sistema más complejo.

## Potencia
- Es la cantidad de energía transferida o convertida por unidad de tiempo.
- Se mide en **vatios (W)**.
- En circuitos:
	- Potencia en corriente continua (DC):
		- $P = V \cdot I$
	- Potencia en corriente alterna (CA):
		- $P = V \cdot I \cdot cos(\theta)$
		- Donde $\cos(\theta)$ es el factor de potencia que mide la proporción de potencia útil frente a la total.
- Es como la cantidad de agua entregada por una tubería por un segundo, tomando en cuenta el esfuerzo aplicado.

![[LeyOhm2.png]]

# Capacitancia e inductancia

- Son propiedades complementarias en circuitos de corriente alterna (CA):
	- La capacitancia genera **reactancia capacitiva**.
		- La cual disminuye con frecuencias más altas.
	- La inductancia geenera **reactancia inductiva**.
		- Que aumenta con frecuencias más altas.
- Juntas forman circuitos resonantes, donde las propiedades capacitivas e inductivas se equilibran a una frecuencia específica.

## Capacitancia
- Es la capacidad de un componente (condensador) para almacenar carga eléctrica en un campo eléctrico.
- Se mide en **faradios (F)**.
- Formula básica
	- $C = Q/V$
	- Donde:
		- $C$ - Capacitancia.
		- $Q$ - Carga eléctrica almacenada.
		- $V$ - Voltaje aplicado.
- Los condensadores tienen diversas aplicaciones:
	- Almacenar energía temporalmente.
	- Filtrar señales en circuitos electrónicos.
	- Estabilizar voltajes.
- Es como un tanque de agua que puede almacenar líquido temporalmente antes de liberarlo.

![[Capacitancia.png]]

![[Capacitor.png]]

> Capacitor de placas planas. Entre las dos placas conductoras se almacena la carga cuyo efecto es un campo eléctrico 

## Inductancia
- Es la propiedad de un componente (inductor) que permite almacenar energía en un campo magnético generado por una corriente eléctrica.
- Es el comportamiento de una bobina de hilo eléctrico al resistir cualquier cambio en corriente eléctrica a través de ella.
- Se mide en **Henrios (H)**.
- Fórmula Básica:
	- $V = L\frac{dI}{dt}$
	- Donde:
		- $V$ - Voltaje inducido
		- $L$ - Inductancia.
		- $\frac{dI}{dt}$ - Taza de cambio de la corriente.
- Se utilizan en aplicaciones como filtros, transformadores y sistemas de energía.
- Es como un volante de inercia que almacena energía cinética y la libera cuando se necesita.

![[Inductancia.png]]


## Elementos pasivos y activos

Los elementos que realizan alguna transformación eléctrica se clasifican en pasivos y activos

Pasivos:
- No requieren ninguna energia para funcionar.
	- Resistencias, capacitores e inductancias.
- con sólo aplicarles una diferencia de potencial y hacerles pasar una corriente se producen los efectos respectivos.

Activos:
- Requieren de energía para funcionar.
	- Deben polarizarse para que produzcan los efectos correspondientes.
	- Diodos, transistores y sus derivados.

## Conexiones en serie y paralelo

En la conexión en serie, los dispositivos se conectan sucesivamente.
La salida de un dispositivo se conecta a la entrada del siguiente, de tal forma que por ellos circula la misma corriente y la diferencia de potencial total es igual a la suma de la caída en cada uno de los elementos conectados.

En la conexión en paralelo, los dispositivos se conectan al mismo potencial por lo que la corriente que pasa por ellos se divide proporcionalmente de acuerdo con las características de cada uno de ellos.

## Radiación electromagnética

También conocida como EMR (Electro Magnetic Radiation).

Se produce por la oscilación o aceleración de cargas eléctricas o por campos mangnéticos.

![[RadiacionEletromagnetica.png]]