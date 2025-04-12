# CLASE 03/04/2025
# Diseño de transmisión en Sistemas de Control de Movimiento

en el control de movimiento, se presentan necesidades para cumplir con ciertas necesidades en donde se trabajen con actuadores, en este caso "Motores", y cargas en distintas aplicaciones, es importante conocer los principos fundamentales para el funcionamiento de los sistemas de transmision que se implementan cotidianamente en la industria.

## 1. Caracteristicas del diseño de transmision

El diseño de una transmision esta regido por unos parametros que son clave para obtener un funcionamiento optimo del mismo, es fundamental asegurar que el torque cuando el motor esta maxima velocidad sea superior al requerido para lo que se va a utilizar, esto lo podemos definir, como el margen de seguridad en donde se tenga un rango en que el motor no se va a quedar sin torque para que su funcionamiento con carga sea el optimo, la inercia tiene un papel fundamental ya que se debe tener una inercia apropiada entre el motor y la carga.


### 1.1. Conceptos Básicos en el diseño de una transmisión

* uno de los parametros a tener en cuenta para el motor es la inercia que podemos comprender como la propiedad que presenta un objeto a cambios en su velocidad angular de igual manera se comprende que la inercia es la contraparte rotacional de la masa.
la inercia en este punto se modela de la siguiente manera partiendo de que:

* Inercia J

$$ \sum \tau = J\alpha $$

Donde:

$\tau$: Torque aplicado [Nm] 

$J$: Momento de inercia [kg·m²] 

$\alpha$: Aceleración angular [rad/s²] 

## 2. Transmisión Engranajes

la transmison de engranajes cuenta con un alta precision de posicionamiento, tiene un alto indice de eficiencia cercanas entre el 85-98%
el analisis de los engranajes se tiene en cuenta su relacion partiendo de una variable que los relacione a ambos, partiendo de las siguientes ecuaciones podemos observar:

**Ecuaciones Fundamentales:**

$$N_{GB} = \frac{n_2}{n_1} = \frac{d_1}{d_2}$$

* Inercia Reflejada

La inercia total vista desde el motor se calcula como:

$$J_{\text{Ref}} =\frac{J_{\text{load}}}{N^2GB}$$

* Torque Reflejado

para el torque reflejado se puede considerar como la relacion que se obtiene entre la transmision y la eficiencia.

$$T_{\text{m}} =\frac{T{\text{l}}}{\eta NGB}$$

recordemos que $${\eta}$$ es interpretada como la efciencia del sistema.

* inercia total

  $${J_{\text{total}}}={J_{\text{m}}}+{J_{\text{on motor shaft}}}+{J_{\text{ref}}}$$

## 3. Transmisión Polea-Correa

la transmision polea-correa es otro mecanismo que se fundamenta en generar un movimiento rotacional, que consta de dos ruedas conectadas, por medio de una correa, en donde el radio de las ruedas es el que permite determinar la transformacion de energia.

la velocidad que se genera en la transmision polea correa se distribuye de la misma manera en las dos ruedas y es asi que podemos modelar la velocidad tangencial de la siguiente manera

**Ecuaciones Fundamentales:**

$$V_{\mathrm{tangential}} = \omega_{lp} \cdot r_{lp} = \omega_{lp} \cdot r_{lp}$$

$$N_{\mathrm{BP}} = \frac{\omega_{lp}}{\omega_{lp}} = \frac{r_{lp}}{r_{lp}}$$

* Inercia reflejada

* Torque de carga
  

## 4. Definiciones

> 🔑 *Sistema de Transmisión Mecánica:* Conjunto de componentes que adaptan y transfieren energía cinética desde una fuente motriz hasta una carga, modificando características como velocidad, torque, dirección o tipo de movimiento (rotacional-lineal), garantizando que los requerimientos dinámicos de la aplicación sean satisfechos.

> 🔑 *Inercia reflejada:* Propiedad que representa la resistencia al cambio de velocidad angular de un sistema, ajustada según la relación de transmisión.

> 🔑 *Torque reflejado:* Torque equivalente en el eje del motor después de considerar la relación de transmisión y pérdidas.

## 5. Ejercicios

📚 **Ejercicio 1 - Análisis de Sistema con Engranajes**

Un servomotor con inercia de rotor $J_m = 5\times10^{-4}$ kg·m² acciona una carga de $J_{load} = 0.2$ kg·m² a través de un reductor de relación 10:1 con eficiencia del 95%. Calcular:

a) Inercia total reflejada al motor  
b) Relación de inercia del sistema  
c) Torque requerido en el motor para acelerar la carga a 2 rad/s²

**Solución:**

a) 
$$J_{ref} = \frac{0.2}{0.95 \times 10^2} = 2.105 \times 10^{-3} \text{ kg·m²}$$
$$J_{total} = 5\times10^{-4} + 2.105\times10^{-3} = 2.605\times10^{-3} \text{ kg·m²}$$

b)
$$J_R = \frac{2.605\times10^{-3}}{5\times10^{-4}} = 5.21$$

c)
$$\tau_{motor} = J_{total} \times \alpha_{motor} = 2.605\times10^{-3} \times (2 \times 10) = 0.0521 \text{ Nm}$$

📚 **Ejercicio 2 - Diseño de Sistema Tornillo de Bolas**

Se requiere mover una carga lineal de 150 kg (incluyendo carro) con un tornillo de bolas (η=90%, pitch=5 mm/rev). Determinar:

a) Inercia equivalente  
b) Torque para acelerar a 1 m/s²  
c) Velocidad angular del motor a 0.5 m/s

**Solución:**

a)
$$p = \frac{1}{0.005} = 200 \text{ rev/m}$$
$$J_{ref} = \frac{150}{(2\pi \times 200)^2} = 9.49\times10^{-5} \text{ kg·m²}$$

b)
$$F = ma = 150 \times 1 = 150 \text{ N}$$
$$\tau = \frac{150}{2\pi \times 200 \times 0.9} = 0.133 \text{ Nm}$$

c)
$$\omega = v \times 2\pi p = 0.5 \times 2\pi \times 200 = 628.32 \text{ rad/s} \approx 6000 \text{ RPM}$$

## 6. Conclusiones

Los elementos de transmisión constituyen el nexo crítico entre los sistemas de actuación y las cargas mecánicas en aplicaciones de control de movimiento. Un diseño óptimo requiere considerar múltiples factores dinámicos, térmicos y de eficiencia energética. Las modernas herramientas de simulación permiten validar los diseños antes de su implementación física, reduciendo costos y tiempos de desarrollo.
El futuro de las transmisiones mecánicas apunta hacia sistemas más inteligentes, integrados y eficientes, capaces de auto-monitorear su condición y adaptarse a cambios operativos en tiempo real.

## 7. Referencias



