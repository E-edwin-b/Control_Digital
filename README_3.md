# CLASE 22/08/2024
# Estabilidad en sistemas discretos
es un término que tiene un papel fundamental en el análisis de sistemas dinámicos y también en su diseño, es importante que un sistema es estable si cuando tiene una entrada limitada su salida también lo es, para el análisis de la estabilidad se usan métodos matemáticos tales como la transformada Z y el criterio de Judy, el término de estabilidad se puede estudiar por tipos como la estabilidad absoluta, la estabilidad asintótica y la estabilidad BIBO.
## 1. Estabilidad
### 1.1 Estabilidad Absoluta
la estabilidad absoluta se puede interpretar como el funcionamiento para un sistema que en su entrada que es limitada su salida también lo es, por lo tanto se puede relacionar este concepto con la ubicación de polos en el dominio de z o de la place 

### 1.2 Estabilidad Asintótica
Cuando se habla de estabilidad asintótica, se puede relacionar con el comportamiento de un sistema que cuando el tiempo tiende a infinito el mismo decae a cero, por lo tanto se puede interpretar que el sistema es estable.

$\lim_{k \to \infty }y\left( k \right)=0$

### 1.3 Estabilidad BIBO
Un sistema tiene estabilidad BIBO cuando si su entrada es acotada, su salida también lo será, por lo tanto la salida dará un resultado respectivo a la entrada por lo tanto satisface las necesidades requeridas.

$\left| y\left( k \right) \right| = b_{y}$

$k = 0,1,2,...$

$0< b_{y< \infty}$

## 2. Espacios de LaPlace y Z

### 2.1 Dominio de LaPlace vs. Dominio Z

para realizar el análisis de la estabilidad se puede implementar las transformadas de laplace y z ya que es por medio de estas que se estudia el tiempo continuo o discreto en un dominio complejo, para ello se tienen en cuenta los espacios de la place y z en donde:

* LaPlace: la estabilidad se define por la ubicación de los pinos teniendo en cuenta el eje vertical(es importante destacar que los polos deben estar ubicados en la parte izquierda para que el sistema sea estable).
*Z: la estabilidad en el sistema z se define igual que en LaPlace por la ubicación de los polos pero en este caso dentro de un círculo unitario y el sistema será estable si todos sus polos están dentro de este círculo.
 
### 2.2 Relación entre los Polos en LaPlace y Z
es importante tener en cuenta que los polos en el dominio de LaPlace  ($s = \sigma + j\omega$) tienen su equivalente en el dominio de z fundamentándose en la siguiente transformación:

z = e^{sT}

En esta transformación se tiene en cuenta a T como el tiempo de muestreo y se relaciona demostrando como un sistema estable en el dominio de la LaPlace se puede mapear dentro de un círculo unitario en el dominio Z se donde su estabilidad se  mantiene.

## 3. Criterio de Jury para la Estabilidad en el Dominio Z 

### 3.1 Introducción al Criterio de Jury
El criterio de Jury se conoce como un método o técnica analítica que permite determinar la estabilidad de un sistema discreto, para realizar el mismo es importante destacar que se debe aplicar al polinomio característico de la función de transferencia en z teniendo en cuenta unas condiciones específicas.

$D\left( z \right)=a_{0}z^{n}+a_{1}z^{n-1}+....$
### 3.2 Condiciones del Criterio de Jury
como se menciona anteriormente para aplicar el método de jury se deben tener en cuenta las siguientes condiciones:

* 𝑎0 > 0
* $\left| a_{n} \right|< a_{0}$
* $P\left( z \right)_{z=1}> 0$
* $P\left( z \right)_{z=-1}> 0$

## 2. Definiciones
>🔑 *Estabilidad:* Propiedad de los sistemas dinámicos que permite analizar la capacidad de un sistema para mantener su comportamiento dentro de ciertos límites frente a cambios en las condiciones iniciales.
>
>🔑 *Asintótico:* término usado para describir el comportamiento de una función o una secuencia cuando tiende a un valor del límite, es la capacidad de un sistema para volver al estado de equilibrio con el tiempo después de una perturbación.
>
>🔑 *Polinomio:* Expresión matemática que consiste en la suma de términos, que se implementa para modelar problemas matemáticos. 
>
## 9. Ejercicios

### 1 $z^{3}-0.8z^{2}+5z-0.9=0$
* 𝑎0 > 0 
* $\left| a_{n} \right|< a_{0}$
* $P\left( z \right)_{z=1}> 0$
* $P\left( z \right)_{z=-1}> 0$
* a0 = 1
* an = 0.9
* Pz=1  
* *1^{3}-0.8*1^{2}+5*1-0.9=0* = 4.3 > 0
* *-1^{3}-0.8*-1^{2}+5*-1-0.9=0* = -6.1 < 0 es menor a 0 por que su polinomio es impar
* ahora se aplican determinantes:
* **determinantes:**

| **z0** | **z1** |**z2** |**z3**|
|--------|--------|-------|------|
|  -0.9  |   5    | -0.8  |  1   |
|   1    |  -0.8  |   5   | -0.9 |
|  -4.28 |  -3.7  | -0.19 |
* $\left| -4.28 \right|\left| -0.19 \right|$
* $\left| 4.28 \right|>\left| 0.19 \right|$

### 2 $z^{4}+1.9z^{3}-2.8z^{2}+8z-0.2=0$
* 𝑎0 > 0 
* $\left| a_{n} \right|< a_{0}$
* $P\left( z \right)_{z=1}> 0$
* $P\left( z \right)_{z=-1}> 0$
* a0 = 1
* an = 0.9
* Pz=1
* 1^{4}+1.9*1^{3}-2.8*1^{2}+8*1-0.2=0 = 7.9 > 0
* -1^{4}+1.9*-1^{3}-2.8*-1^{2}+8*-1-0.2=0 = -8.3 > 0 tiene que ser mayor a 0 por que su polinomio es par
* Como no se cumplen los parámetros requeridos no se puede analizar por medio del método de Jury.

## 10. Conclusiones
Por medio de esta clase se pudo adquirir conocimientos para analizar la estabilidad de los sistemas discretos, implementando conocimientos previos como la transformada de LaPlace y transformada Z, el test de Jury es indispensable para analizar los sistemas de acuerdo a los polinomios característicos para sistemas en tiempo continuo y discreto.

10. Referencia
## 11. Referencias
* Jorge Eduardo Cote  (2024). Estabilidad Absoluta. Jorge Eduardo Cote, Control Digital. Universidad ECCI.



