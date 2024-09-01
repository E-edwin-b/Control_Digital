# Transformada Z de adelantos y atrasos 
Método matemático por medio del cual se puede realizar el análisis y diseño de sistemas discretos en el tiempo, es importante destacar que este método es fundamental para dicho análisis ya que permite transformar señales y sistemas discretos en el dominio del tiempo al dominio complejo "Z", implementar este método es fundamental para analizar la respuesta de un sistema cuando las entradas son desplazadas en el tiempo.
## 1. Representación matemática de los sistemas
### 1.1. Ecuación en diferencias.
La ecuación en diferencias es la relación matemática que permite evidenciar el cambio de una señal discreta de un punto a otro, es importante tener en cuenta que la dinámica del sistema se representa teniendo en cuenta las muestras de las señales.

$b_{n}u\left( k \right)+b_{n-1}u\left( k-1 \right)=y\left( k \right)+a_{n-1}y\left( k-1 \right)$

### 1.2 Características y ecuaciones en diferencias.
las ecuaciones en diferencias cuentan con unas características que permiten clasificarlas de la siguiente manera:

* lineal, invariante en el tiempo, no homogénea
* homogéneas, lineales, invariantes en el tiempo
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
La transformada z es la parte opuesta de LaPlace por lo tanto contamos con características diferentes, es importante destacar que es por medio de las transformada z que podemos obtener una expresión matemática para obtener una ecuación para cualquier muestra.

### transformada de LaPlace
$\mathcal{L}\{ f(t) \} = \int_{0}^{\infty} f(t) e^{-st} \ dt$

### transformada Z

$\mathcal{z}\{ f(k) \} = \sum_{k=0}^{\infty} f(k)z^{-k} \ $



### 2.3 Ecuaciones en diferencias por transformadas Z.
Para las ecuaciones diferenciales por la transformada z se debe tener en cuenta que es un procedimiento similar al anterior visto de ecuaciones en diferencias, se debe aplicar transformada z a la ecuación, luego despejar la variable desconocida y aplicar la transformada z inversa.

## 3. Función de transferencia discreta 
Se usa como una herramienta matemática que se implementa en el análisis y diseño de sistemas discretos en el dominio de la frecuencia, para esto se tienen en cuenta la relación entre la entrada y la salida de un sistema en términos de la transformada z
### 3.1 Funciones de transferencia en el dominio Z
En el análisis del tiempo discreto se pueden obtener las representaciones de las funciones de transferencia en el dominio Z así como también se pueden identificar los comportamientos de los sistemas por medio de sus parámetros.
### 3.2 Función de transferencia a pulso.
Esta función de transferencia se interpreta como esa relación que existe entre una entrada y la salida que se tienen en cuenta en un sistema dinámico.

$H\left( z \right)=\frac{Y\left( z \right)}{X\left( z \right)}$

### 3.3 Tiempo muerto en sistemas discretos
el tiempo muerto hace referencia a el atraso en la respuesta de un sistema, en ese tiempo hay un intervalo en el cual la salida no responde a un cambio en la entrada, es importante destacar que el tiempo muerto es más fácil medir en sistemas discretos ya que el mismo se tiene en cuenta al comparar el grado de los polinomios de la función de transferencia, es importante tener en  cuenta que r se relacion con la cantidad de muestras que hay de tiempo muerto.

$r = m - n$



## 2. Definiciones
>🔑 *Muestreo:* Proceso mediante el cual se analiza y procesa las señales, permite tomar un conjunto de valores de la señal en intervalos de tiempo específicos .
>
>🔑 *Periodo:* intervalo  de tiempo en el cual una función se reparte de manera cíclica, es fundamental para el análisis de señales y sistemas tanto en el dominio continuo como en el dominio discreto.
>
>🔑 *Dinámica:* estudia las fuerzas y los movimientos de los cuerpos, analiza cómo las fuerzas afectan el cambio del movimiento de un objeto. 
>


## 10. Conclusiones
por medio de la clase se desarrollaron los conocimientos para analizar, estudiar y diseñar sistemas discretos en relación con el tiempo, es importante tener en cuenta el dominio del tiempo y el dominio z, asi como tambien el uso de las ecuaciones en diferencias que representan 
El comportamiento dinámico de un sistema en términos de sus señales de entrada y salida.

## 11. Referencias
* Jorge Eduardo Cote  (2024). Transformada Z de adelantos y 
atrasos. Jorge Eduardo Cote, Control Digital. Universidad ECCI.


