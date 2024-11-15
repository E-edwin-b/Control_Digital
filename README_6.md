# CLASE 07/11/2024
# Observadores de estados y error de estado estacionario  

Los observadores de estados son una herramienta muy importante ya que permiten realizar estimaciones precisas de variables que no pueden ser accesibles implementnado solo las entradas y salidas del sistema teniendo asi un enfoque para el diseño de controladoress de retroalimentación gracias a su altyto grado de presicion.

## 1. Observadores de estados
Son fundamentales como se menciono anteriormente ya que en las ocasiones cuando el sistema no cuenta con todos sus etados medibles esta herramienta se implementa paa hacer una estimacion de las variables de estado teniendo en cuenta los valores que ya conocemos como lo son las entrda y salidas del sistema, esto nos permite desarrollar controladores de retroalimentación que funcionen de manera correcta.

## 2. Desarrollo e implementación Observadores de Estados

### 2.1 Comprobación de Observabilidad
para el desarrollo del observador es importante previamente tener en cuenta si el sistema es observable, recordemos que esto se hace por medio de la matriz de observabilidad del sistema.

💡**Ejemplo 1:**

$$A= \begin{bmatrix} 
   1.7999 & -0,.8025\\ 
   1 & 0 
\end{bmatrix}$$

$$B= \begin{bmatrix} 
   0.01563 \\ 
   0
\end{bmatrix}$$

$$C= \begin{bmatrix} 
   0.0119 & 0.01107 \\  
\end{bmatrix}$$

$$V= \begin{bmatrix} 
   C  \\ 
   CA  
\end{bmatrix}$$

$$V= \begin{bmatrix} 
   0.01191 & 0.01107 \\ 
  CA & 0.5 
\end{bmatrix}$$

$$det(V)=-0,0004737$$

### 2.2 Cálculo del Polinomio Característico
en el desarrolo del observador de estados es importante tener en cuenta el calcular el polinomio caracteristico ya que a partir de la matriz A de nuestro sistema que podremos determinar el comportamiento del sistema asi como tambien la ubicación de sus polos.

### 2.3 Determinación de la Matriz de Ganancias del Observador


se deben implementar las ganancias:

$$K_a$$

ya que son importantes en el desarrollo del observadores pues estas permiten realizar ajustes tanto a la velocidad como a la precision de las estimaciones, de acuerdo a los polos deseados y definidos para el observador.


### 2.4 Implementación de la Ley de Control
unas vez que se tienen las matrices de estado asi como tambien las ganancias, el objetivo principal es implementar la ley de control con el fin de ajustar el sistema y minimizar el error de estimación.

##  5. Definiciones
>🔑 *Observador de Estados:* Herramienta que  estima las variables de estado no medibles de un sistema teniendo en cuenta sus entradas y salidas conocidas.
>
>🔑 *Observabilidad:* Capacidad con la que cuenta un sistema para deducir todas sus variables de estado a partir de sus salidas, lo cual permite conocer el estado completo del sistema en un instante finito de tiempo.
>
>🔑 *Error de Estimación:* Diferencia entre el valor real de la variable de estado y su estimación realizada por el observador, es importante conocer que este error depende de la matriz de control y puede ser minimizado con la inclusión de un vector de ganancias.
>
## 6. Ejercicios

📚 Ejercicio 1: Controlabilidad

   Se tiene el siguiente sistema:
   
$$A=\begin{bmatrix} 
   0.7 & -0.3 \\ 
   0.4 & 0.6 
\end{bmatrix}$$

$$C=\begin{bmatrix} 
   1 & 0 \\ 
    
\end{bmatrix}$$    

$$CA=\begin{bmatrix} 
   0.7 & -0.3  \\  
\end{bmatrix}$$

$$V=\begin{bmatrix} 
   1 & 0 \\ 
   0.7 & -0.3 
\end{bmatrix}$$

$$det(V)=(1)(0.3)-0.7*0=-0.3$$

$$det(V)=0.3$$

## 7. Conclusiones
por medio de esta clase se desarrollaron los conocimientos para implementar los obervadores de estados en sistemas con multpiles variables esto permite que se puedan hacer estimaciones de variables que no son medibles, esto para mejorar el desempeño y tambien la estabilidad del sistema.
es importante tener en cuenta que de un buen diseño de la matriz de ganancia asi como tambien de la verificación de la observabilidad es que se puede reducir de manera adecuada el error de esstimacion.

## 8. Referencias
* JORGE EDUARDO COTE BALLESTEROS (7 nov 2024). E.P.1.Control digital. Observadores de estados y error 
de estado estacionario. universidad ECCI






