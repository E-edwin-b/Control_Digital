# Estabilidad en sistemas discretos
es un termino que tiene un papel fundamental en el analisis de sistemas dinamicos y tambien en su diseño, es importante que un sistema es estable si cuando tiene una entrada limitada su salida tambien lo es, para el analisis de la estbilidad se usan metodos matemáticos tales como la transformada Z y el criterio de Judy, el termino de estabilidad se puede estudiar por tipos como la estabilidad absoluta, la estabilidad asintotica y la estabilidad BIBO.
## 1. Estabilidad
### 1.1 Estabilidad Absoluta
la estabilidad absoluta se puede interpretar como el funcinamiento para un sistema que en su entrada que es limitada su salidad tambien lo es, por lo tanto se puede relacionar este concepto con la ubicacion de polos en el dominio de z o de la place 

### 1.2 Estabilidad Asintótica
cuando se habla de estabilidad asintotica, se puede relacionar con el comportamiento de un sistema que cuando el tiempo tiende a infinito el mismo decae a cero, por lo tanto se puede interpretar que el sistema es estable.

$\lim_{k \to \infty }y\left( k \right)=0$

### 1.3 Estabilidad BIBO
un sistema tiene estabilidad BIBO cuando si su estrada es acotada, su salida tambien lo sera, por lo tanto la salida dara un resultado respectivo a la entrada por lo tanto satisface las necesidades requeridas.

$\left| y\left( k \right) \right| = b_{y}$

$k = 0,1,2,...$

$0< b_{y< \infty}$

## 2. Espacios de LaPlace y Z

### 2.1 Dominio de LaPlace vs. Dominio Z

para realizar el analisis de la estabilidad se puede implementar las transfromadas de la place y z ya que es por medio de estas que se estudia el tiempo continuio o discreto en un dominio complejo, para ello se tienen en cuenta los espacios de la place y z en donde:

* LaPlace: la estabilidad se define por la ubicacion de los ponos teniendo en cuenta el eje vertical(es importante destacar que los polos deben estar ubicados en la parte izquierda para que el sistema sea estable).
*Z: la estabilidad en el sistema z se define igual que en LaPlace por la ubicación de los polos pero en este caso dentro de un círculo unitario y el sistema sera estable si todos sus polos estan dentro de este círculo.
 
### 2.2 Relación entre los Polos en LaPlace y Z
es importante tener en cuenta que los polos en el dominio de LaPlace  ($s = \sigma + j\omega$) tienen su equivalente en el domio de z fundamentandose en la siguiente transformacion:

z = e^{sT}

en esta transformacion se tiene en cuenta a T como el tiempo de muestreo y se relaciona demostrando como un sistema estable en el dominio de la LaPlace se puede mapear dentro de un circulo unitario en el dominio Z se donde su estabilidad se  mantiene.

## 3. Criterio de Jury para la Estabilidad en el Dominio Z 

### 3.1 Introducción al Criterio de Jury
el criterio de Jury se conoce como un metodo o tecnica analitica que permmite determinar la estabilidada de un sistema discreto, para realizar el mismo es importante destacar que se debe aplicar al polinomio caracteristico de la funcion de tranferencia en z  y teniendo en cuenta unas condiciones especificas.

$D\left( z \right)=a_{0}z^{n}+a_{1}z^{n-1}+....$
### 3.2 Condiciones del Criterio de Jury
como se menciona anteriormente para aplicar el metodo de jury se deben tener en cuenta las siguientes condiciones:

* 𝑎0 > 0
* $\left| a_{n} \right|< a_{0}$
* $P\left( z \right)_{z=1}> 0$
* $P\left( z \right)_{z=-1}> 0$

## 2. Definiciones
>🔑 *Estabilidad:* Propiedad de los sistemas dinamicos que permite analisar la capacidad de un sistema para mantener su comportameinto dentro de ciertos limites frente a cambios en las condiciones iniciales.
>
>🔑 *Asintotico:* termino usado para describir el comportamiento de una función o una secuencia cuando tiende a un valor del limimte, es la capacidad de un sistema para volver al estado de equilibrio con el tiempo despues de una perturbacion.
>
>🔑 *Polinomio:* Expresion matemática que consiste en la suma de términos, que se implementa para modelar problemas matematicos. 
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
* **determminantes:**

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
* como no se cumplen los paraetros requeridos no se puede analisar por medio del metodo de Jury.

## 10. Conclusiones
Por medio de esta clase se pudo adquirir conocimientos para analizar la estabilidad de los sitemas discretos, implementando conocimientos previos como la transformada de LaPlace y transformada Z, el test de Jury es indispensable para analizar los sistemas de acuerdo a los polinomios caracteristicos para sistemas en tiempo continuo y discreto.

10. Referencia
## 11. Referencias
* Jorge Eduardo Cote  (2024). Estabilidad Absoluta. Jorge Eduardo Cote, Control Digital. universidad ECCI.
