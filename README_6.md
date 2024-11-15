# CLASE 07/11/2024
# Observadores de estados y error de estado estacionario  

Los observadores de estados son una herramienta muy importante ya que permiten realizar estimaciones precisas de variables que no pueden ser accesibles implementnado solo las entradas y salidas del sistema teniendo asi un enfoque para el diseño de controladoress de retroalimentación gracias a su altyto grado de presicion.

## 1. Observadores de estados
Son fundamentales como se menciono anteriormente ya que en las ocasiones cuando el sistema no cuenta con todos sus etados medibles esta herramienta se implementa paa hacer una estimacion de las variables de estado teniendo en cuenta los valores que ya conocemos como lo son las entrda y salidas del sistema, esto nos permite desarrollar controladores de retroalimentación que funcionen de manera correcta.

## 2. Desarrollo e implementación Observadores de Estados

### 2.1 Comprobación de Observabilidad
para el desarrollo del observador es importante previamente tener en cuenta si el sistema es observable, recordemos que esto se hace por medio de la matriz de observabilidad del sistema.

### 2.2 Cálculo del Polinomio Característico
en el desarrolo del observador de estados es importante tener en cuenta el calcular el polinomio caracteristico ya que a partir de la matriz A de nuestro sistema que podremos determinar el comportamiento del sistema asi como tambien la ubicación de sus polos.

### 2.3 Determinación de la Matriz de Ganancias del Observador


se deben implementar las ganancias:

$$K_a$$

ya que son importantes en el desarrollo del observadores pues estas permiten realizar ajustes tanto a la velocidad como a la precision de las estimaciones, de acuerdo a los polos deseados y definidos para el observador.


### 2.4 Implementación de la Ley de Control
unas vez que se tienen las matrices de estado asi como tambien las ganancias, el objetivo principal es implementar la ley de control con el fin de ajustar el sistema y minimizar el error de estimación.

##3

## 3. Ejemplos

💡**Ejemplo 1:** Verificación de Observabilidad  
Supongamos que tenemos un sistema con las siguientes matrices de estado:

$$ A = \begin{bmatrix} 1.2 & -0.5 \\ 0.3 & 0.8 \end{bmatrix}, \quad B = \begin{bmatrix} 0.1 \\ 0.4 \end{bmatrix}, \quad C = \begin{bmatrix} 1 & 0 \end{bmatrix} $$

Para verificar la observabilidad, calculamos la matriz de observabilidad del sistema. Si la matriz tiene rango completo, el sistema es observable.

💡**Ejemplo 2:** Diseño del Vector de Ganancias  
Para el sistema del Ejemplo 1, si deseamos colocar los polos del observador en $z = -0.3$, calculamos el vector de ganancias $K_e$ que permite hacer la estimación de los estados con una dinámica rápida.




