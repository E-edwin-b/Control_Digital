# Estabilidad en sistemas discretos
Metodo matemático por medio del cual se puede realizar el analisis y diseño de sistemas discretos en el tiempo, es importante destacar que este metodo es fundamental para dicho analisis ya que permite transformar señales y sistemas discretps en el dominio del tiempo al dominio complejo "Z", implementar este metodo es fundamental para analisar la respuesta de un sistema cuando las entradas son desplazadas en el tiempo.
## 1. Representación matemática de los sistemas
### 1.1. Ecuación en diferencias.
la ecuación en diferencias es la relación matemática que permite evidenciar el cambio de una señal discreta de un punto a otro, es importante tener en cuenta que la dinamica del sistema se representa teniendo en cuenta las muestras de las señales.

$b_{n}u\left( k \right)+b_{n-1}u\left( k-1 \right)=y\left( k \right)+a_{n-1}y\left( k-1 \right)$

### 1.2 Características ecuaciones en diferencias.
las ecuaciones en diferencias cuentan con unas caracteristicas que permiten clasificarlas de la siguiente manera:

* lineal, invariante en el tiempo, no homogénea
* homogeneas, lineales, invariantes en el tiempo
* Lineal, variante en el tiempo, homogénea
* No lineal, invariante en el tiempo, homogénea

### 1.3 Solución por métodos iterativos.
💡**Ejemplo 1:**
$y\left( k \right)=\frac{1}{3}\left( -2y\left( k-1 \right)+y\left( k-2 \right)
+2u\left( k-1 \right)-3u\left( k-2 \right)\right)$

$y\left( -2 \right)=1;y\left( -1 \right)=-2;u\left( k \right)$

$k=0$

$y\left( 0 \right)=\frac{1}{3}\left( -2\left( -2 \right)+1+2\left( 0 \right) -3\left( 0 \right)\right)=\frac{5}{3}$

## 2. Transformada Z
la transformada z es la parte opuesta de LaPlace por lo tanto contamos con caracteristicas diferentes, es importante destacar que es por medio de las transformada z que podemos obtener una expresion matematica para obtener una ecuacion para cuaquier muestra.

### transformada de LaPlace
$\mathcal{L}\{ f(t) \} = \int_{0}^{\infty} f(t) e^{-st} \ dt$

### transformada Z

$\mathcal{z}\{ f(k) \} = \sum_{k=0}^{\infty} f(k)z^{-k} \ $



### 2.3 Ecuaciones en diferencias por transformadas Z.
para las ecucaciones diferenciales por la transformada z se debe tener en cuenta que es un procedimiento similar al anterior visto de ecuaciones en diferencias, se debe aplicar transformada z a la ecuacion, luego despejar la variable desconocida y aplicar la trasformada z inversa.

## 3. Función de transferencia discreta 
Se usa como una herraienta matemática que se implementa en el analisis y diseño de sistemas discretos en el dominio de la frecuencia, para esto se tienen en cuenta la relacion entre la entrada y la salida de un sistema en terminos de la transformada z
### 3.1 Funciones de transferencia en el dominio Z
en el analisis del tiempo discreto se pueden obtener las repsentaciones de las funciones de transferencia en el dominio Z asi como tambien se pueden identificar los comportamientos de los sistemas por medio de sus parametros.
### 3.2 Función de transferencia a pulso.
esta funcion de transferencia se interpreta como esa relacion que existe entre una entrada y la salida que se tienen en cuenta en un sistema dinamico.

$H\left( z \right)=\frac{Y\left( z \right)}{X\left( z \right)}$

### 3.3 Tiempo muerto en sistemas discretos
el tiempo muerto hace referencia a el atraso en la respuesta de un sistema, en ese tiempo hay un intervalo en el cual la salida no responde a un cambio en la entrada, es importante destacar que el tiempo muerto es más facil medir en sistemas discretos ya que el mismo se tiene en cuenta al comparar el grado de los polinomios de la funcion de transferencia, es importante tener en  cuenta que r se relacion con la cantidad de muestras que hay de tiempo muerto.

$r = m - n$



## 2. Definiciones
>🔑 *Muestreo:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Periodo:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Dinamica:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Discreto:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Pulso:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.


## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
* Jorge Eduardo Cote  (2024). Transformada Z de adelantos y 
atrasos. Jorge Eduardo Cote, Control Digital. universidad ECCI.
