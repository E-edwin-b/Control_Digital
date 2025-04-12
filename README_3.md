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
para la incercia reflejada se toma en cuenta el modelamiento de la correa como una masa rotatoria, que puede contar con una inercia equivalente a $$J=mr^2$$ por lo tanto se tiene que:

$$ J_{belt \rightarrow in} = \frac{W_{belt}}{g \cdot \eta} \cdot r_{ip}^2 $$

* Torque de carga
como se mencionó anteriormente en la trasmision de engranajes, la relacion de transmision se comporta igual y por ende el torque de la carga al motor es de la misma manera:

modelandose asi:

$$ T_{\rm load\rightarrow in} = \frac{T_{\rm ext}}{\eta N_{\rm BP}} $$

## 4. Definiciones

> 🔑 *Sistema de Transmisión Mecánica:* Conjunto de componentes que adaptan y transfieren energía cinética desde una fuente motriz hasta una carga, modificando características como velocidad, torque, dirección o tipo de movimiento (rotacional-lineal), garantizando que los requerimientos dinámicos de la aplicación sean satisfechos.

> 🔑 *Inercia reflejada:* Propiedad que representa la resistencia al cambio de velocidad angular de un sistema, ajustada según la relación de transmisión.

> 🔑 *Torque reflejado:* Torque equivalente en el eje del motor después de considerar la relación de transmisión y pérdidas.

## 5. Ejercicios

📚 **Ejercicio 1 - Análisis de Sistema con Engranajes**

se tiene un motor con inercia de rotor $J_m = 5\times10^{-4}$ kg·m² que acciona una carga de $J_{load} = 0.2$ kg·m² a través de un reductor de relación 10:1 con eficiencia del 95%. encuentre la inercia total reflejada al motor  y Relación de inercia del sistema  


$$J_{ref} = \frac{0.2}{0.95 \times 10^2} = 2.105 \times 10^{-3} \text{ kg·m²}$$
$$J_{total} = 5\times10^{-4} + 2.105\times10^{-3} = 2.605\times10^{-3} \text{ kg·m²}$$

$$J_R = \frac{2.605\times10^{-3}}{5\times10^{-4}} = 5.21$$


📚 **Ejercicio 2 - Análisis de Sistema con Engranajes**

Se tiene un motor con inercia de rotor $J_m = 8 \times 10^{-4} \, \text{kg·m}^2$ que acciona una carga de $J_{\text{load}} = 0.15 \, \text{kg·m}^2$ a través de un reductor de relación **5:1** con una eficiencia del **90%**. encuentre la inercia de la carga reflejada al lado del motor ($J_{\text{ref}}$), la inercia total del sistema ($J_{\text{total}}$) y la relación de inercia ($J_R$) del sistema.  

recordemos que la inercia de la carga reflejada al motor se calcula considerando la relación de reducción ($n$) y la eficiencia ($\eta$):

$$
J_{\text{ref}} = \frac{J_{\text{load}}}{\eta \cdot n^2} = \frac{0.15}{0.9 \times 5^2} = \frac{0.15}{22.5} = \boxed{6.666 \times 10^{-3} \, \text{kg·m}^2}
$$

ahora sumamos la inercia del rotor y la inercia reflejada:

$$
J_{\text{total}} = J_m + J_{\text{ref}} = 8 \times 10^{-4} + 6.666 \times 10^{-3} = \boxed{7.466 \times 10^{-3} \, \text{kg·m}^2}
$$

por ultimo tenemos en cuenta la razón entre la inercia total y la inercia del rotor:

$$
J_R = \frac{J_{\text{total}}}{J_m} = \frac{7.466 \times 10^{-3}}{8 \times 10^{-4}} = \boxed{9.33}
$$

## 6. Conclusiones

los elementos de transmision ocupan un papel importante en la industria, son fundamentales en los sistemas de acuacion y cargas mecanicas, con diversas aplicaciones como el control de movimiento, para desarrollar modelos de transmisiones potimos es importante considerar aspecos dinamicos, termicos y de eficiencia que permitan modelar los sistemas para cumplir su funcion especifica.

gracias a las herramientas como simulink y simscape multibody se pueden realizar analisis dinamicos de los sistemas de transmisiones, de igual manera que tambien verificar sus parametros fisicos antes de su implementación, lo que es muy interesante ya que ayuda a reducir costos, tiempo de desarrollo y optimiza los procesos mitigando  fallos.

comprender a profundidad los parametros que hacen parte de los sistemas de transmisión es fundamental para desarrollar los mismo de manera eficiente relacioando aspectos como la relación de engranajes, torque reflejado, eficiencia e inercia total.

## 7. Referencias

* J. E. Cote Ballesteros, E.P.2. Control movimiento. Control cascada, Universidad ECCI, 2025.
* C. Smith and A. Corripio, Principles and Practice of Automatic Process Control, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2005.
