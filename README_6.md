# CLASE 07/11/2024
# Observadores de estados y error de estado estacionario  

L

## 1. Controlabilidad
La controlabilidad la podemos conocer como la capacidad con la que cuenta un sistema para poder modificar o cambiar en todas las variables de estado utilizando las entradas del sistema. 
por lo tanto, podemos inferir que, si un sistema es controlable, el mismo se podrá variar de un estado a otro deseado mediante un control en un intervalo de tiempo finito.


### 1.1 Matriz de Controlabilidad
La podemos conocer como el medio que se implementa para analizar si un sistema es controlable. Esta misma se construye utilizando la matriz de estado y la matriz de entrada. 
teniendo en cuenta nuestros parámetros podemos saber el rango de la misma el cual será igual al número de variables de estado para que el sistema pueda ser controlable

* La matriz de controlabilidad es:

 $$U=\left[ B AB \right]$$

 💡**Ejemplo 1:**
  
  $$x\left( k+1 \right)= Ax\left( k \right)+Bu\left( k \right)$$

con matrices

$$A= \begin{bmatrix} 
   0.8 & 0.3 \\ 
   0.2 & 0.5 
\end{bmatrix}$$

$$B= \begin{bmatrix} 
   1  \\ 
   0
\end{bmatrix}$$

Calculamos su determinante:

$$det(U)=0.2$$ 

por lo tanto podemos inferir que el sistema es controlable

## 2. Observabilidad 
la observabilidad de un sistema se puede conocer como el análisis de las salidas de un sistema en donde es posible deducir el estado interno en cualquier instante.

## 2.1 Matriz de Observabilidad
Esta se implementa para verificar si un sistema es observable, esta matriz de observabilidad se construye usando la matriz de salida y la matriz de estado.
una característica a tener en cuenta es que es matriz cuenta con un rango completo cuando el sistema es observable.

la matriz de observabilidad es:

$$V= \begin{bmatrix}
   C \\ 
   CA  
\end{bmatrix}$$

💡**Ejemplo 2:**
* Se tiene un sistema con salida:
  
  $$y\left( k \right)= Cx\left( k \right)$$

* en donde C:
  
$$C=\begin{bmatrix}
   1 & -1\\  
\end{bmatrix}$$

* en donde A:

$$A=\begin{bmatrix}
   0.8 & 0.3\\ 
   0.2 & 0.5
\end{bmatrix}$$

* La matriz de observabilidad es

$$V=\begin{bmatrix}
   1 & -1 \\ 
   0.5 & 0  
\end{bmatrix}$$

* El determinante de la matriz es:

$$det(V)=0.5$$

de igual forma también podemos inferir que el sistema es controlable

## 3 Control por retroalimentación de estados

Se conoce como el método de control que se enfoca en el ajuste de una señal de entrada del sistema teniendo en cuenta el valor de sus variables de estado, para así poder modificar la posición de sus polos en el lazo cerrado.
es importante destacar que este método es bastante practico para poder controlar el comportamiento del sistema y también para poder tener estabilidad del sistema.

$$u\left( k \right)=-K*x\left( k \right)$$

## 4 Representación de bloques
Es la forma visual de poder representar la interacción de las variables de estados y la señal de control en el sistema
esta representación permite analizar y verificar la estructura del sistema y poder comprobar si se cumplen las condiciones específicas y necesarias para el control de la misma.

![image](https://github.com/user-attachments/assets/f38e54df-2e47-4386-a17f-f6a723b1a693)

para la misma representación se tienen en cuentan características como:
* Que todas las variables puedan ser medidas
* Que el sistema sea controlable.
* Que se puedan determinar los coeficientes del polinomio característico
  

##  5. Definiciones
>🔑*Controlabilidad:* Propiedad de un sistema que indica si es controlable cuando todas sus variables de estado pueden ser modificadas mediante la acción de control, permitiendo llevar al sistema de un estado inicial a otro estado específico en un tiempo finito.
>
>🔑 Observabilidad: Capacidad con la que cuenta un sistema para deducir todas sus variables de estado a partir de sus salidas, lo cual permite conocer el estado completo del sistema en un instante finito de tiempo.
>
>🔑 Retroalimentación de Estados: Es un método de control por medio del que la entrada del sistema es ajustada en función de sus variables de estado, lo cual permite una ubicación específica de los polos en el lazo cerrado.
>
## 6. Ejercicios

📚 Ejercicio 1: Controlabilidad

   Se tiene el siguiente sistema:
   
$$A=\begin{bmatrix} 
   1 & 0 \\ 
   0 & 0.5 
\end{bmatrix}$$

$$B=\begin{bmatrix} 
   1  \\ 
   1 
\end{bmatrix}$$    

$$U=\begin{bmatrix} 
   B  \\ 
   AB  
\end{bmatrix}$$

$$U=\begin{bmatrix} 
   1 & 1 \\ 
   1 & 0.5 
\end{bmatrix}$$

$$det(U)=(1)(0.5)-(1)(1)=0.5-1$$

$$det(U)=0.5$$


## 7. Conclusiones
por medio de esta clase se desarrollaron los conocimientos para implementar herramientas como la retroalimentación de estados, herramienta eficaz para el control de sistema complejos, por lo tanto, la misma nos permitirá controlar nuestro sistema obteniendo respuesta de acuerdo con los parámetros deseados durante la previa manipulación de los polos en el lazo cerrado.
es importante también destacar la controlabilidad y observabilidad de un sistema ya que por medio de esta cuando se cumplen con los requisitos necesarios la misma nos garantizara que podremos hacer un control completo de acuerdo a las matrices de controlabilidad y observabilidad del sistema.
## 8. Referencias
* JORGE EDUARDO COTE BALLESTEROS (31 oct 2024). E.P.1.Control digital. Controladores por 
retroalimentación de estados. universidad ECCI
