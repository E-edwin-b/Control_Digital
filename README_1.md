# CLASE 13/02/2025
# Control Cascada

El control cascada tiene como objetivo principal rechazar las perturbaciones, es una estrategia que se implementa con el objetivo de mejorar la respuesta de un sistema antes perturbaciones, de igual manera que tambien mejorando la estabilidad.
Su desarrollo consiste en el uso de dos controladores en serie, en los que se tiene en cuenta caracteristicas tales como que las variables que voy a controlar debe ser la mas externa, que el controlador secudario debe ser más rapido que el controlador primario y aqui es donde se aclara que el controlador secundaria deberia tener un controlador P o PI, para que el controlador primario pueda ser PI o PID con el fin de que se pueda eliminar el error de estado estacionario, es importante tener en cuenta que esta arquitectura del control cascada se desea implementar donde se desee hacer más rapida la dinamica de la variable controlada.



## 1. Control cascada
### 1.1 Control cascada
Teniendo en cuenta la breve introducción, el control cascada busca emplear dos lazos de control en donde el controlador primario actue sobre una variable especifica, mientras que el controlador secundario controle una variable dependiente de la primaria y asi mejorar el funcionamiento optimo del sistema y reducir el error de estado estacionario.



### 1.2 Aplicaciones para el control cascada
El control cascada se puede implementar en sistemas que cumplan con unas caracteristicas especificas calsificadas a continuación:
* cuando se presentan perturbaciones que afectan en gran manera la variable que esta siendo controlada.
* cuando se busca mejorar la repsuesta de nuestro sistema en comparacion en cambios significativos en la entrada.
* casos particulares cuando las variables secundarias tienen una dinamica más rapida que la variable primaria que quiere ser controlada.

## 2. Metodos de Sintonización

### 2.1 Metodos de sintonizacion en lazo abierto
Este metodo se desarrolla por medio de pruebas en lazo abierto y sin retroalimentación para obtener los parametros que haran parte de nuestros controladores.
las pruebas se hacen de manera separadas en cada lazo de control y asi mismo se obtienen las ganancias, las constantes de tiempo y el tiempo muerto para posteriormente calcular los ajustes para el funcionamiento optimo de los controladores.

![image](https://github.com/user-attachments/assets/b5b9b3b5-b53e-4586-b7b6-b07d43b56687)


### 2.2 Metodos empiricos de sintonizacion en lazo abierto Austin
El metodo de Austin es una alternativa de sintonizacion que permite sintonizar ambos controladores en una sola  prueba de lazo abierto.

con la aplicacion de este metodo es importante tener en cuenta una caracteristica especifica que se trata que si el controlador secundario es P o PI se pueden proporcionar ecuaciones de ajuste para el controlador primario PI o PID 

para realizar este metodo se realiza un cambio en la entrada, bien sea una señal de escalon al actuador del sistema y se registran las respuestas de las variables secundarias y primarias.

con la respuesta que obtuvimos de la variable secundaria podemos determinar la ganancia en este caso K2, tambien el tiempo secundario T2 y el tiempo de muestreo secundario tm2.

![image](https://github.com/user-attachments/assets/8faba7ff-e8d5-48f3-92ed-5d78892c4060)

es importante tener en cuenta que nuestra primer tabla es funcional cuando T2/T1 es mayor a 0.38, sino se recomienda usar nuestra segunda tabla.

![image](https://github.com/user-attachments/assets/066f5502-4156-48a2-ba0b-a011479aec6a)

luego de que realizamos el correspondiente ajuste al controlador secundario, de nuevo registramos la respuesta de nuestra variable primaria y tomamos tanto la ganancia del proceso primario K1 asi como T1 y tm1, asi se obtiene el tiempo muerto total y la constante de tiempo total para hallar los parametros del controlador primario.

### 2.3 Metodos empiricos de sintonizacion en lazo cerrado

* Metodo Hang
El desarrollo de este metodo propone una sintonizacion por medio de un lazo cerrado (Relé) el cual genera oscilascione en el sistema que permiten sintonizar progresivamente el lazo secundario y posteriormenten el primario dentro del lazo anterior.
con las oscilaciones generadas en el sistema se puede observar el comportamiendo del proceso controlado y obtener los parametros para sintonizar el controlador secundario.
posteroirmente se ubica el controlador secundario sintonizado en el lazo primario y se realiza de nuevo la sintonizacion con el metodo del relé, de nuevo se obtienen el comportamiendo del proceso y se sintoniza el controlador primario y asi se obtiene una mejora en la dinamica global del sistema.



##  3. Definiciones
>🔑 *Observador de Estados:* Herramienta que  estima las variables de estado no medibles de un sistema teniendo en cuenta sus entradas y salidas conocidas.
>
>🔑 *Observabilidad:* Capacidad con la que cuenta un sistema para deducir todas sus variables de estado a partir de sus salidas, lo cual permite conocer el estado completo del sistema en un instante finito de tiempo.
>
>🔑 *Error de Estimación:* Diferencia entre el valor real de la variable de estado y su estimación realizada por el observador, es importante conocer que este error depende de la matriz de control y puede ser minimizado con la inclusión de un vector de ganancias.
>>
>🔑 *Observador de Estados:* Herramienta que  estima las variables de estado no medibles de un sistema teniendo en cuenta sus entradas y salidas conocidas.
>
>🔑 *Observabilidad:* Capacidad con la que cuenta un sistema para deducir todas sus variables de estado a partir de sus salidas, lo cual permite conocer el estado completo del sistema en un instante finito de tiempo.
>
>🔑 *Error de Estimación:* Diferencia entre el valor real de la variable de estado y su estimación realizada por el observador, es importante conocer que este error depende de la matriz de control y puede ser minimizado con la inclusión de un vector de ganancias.
>
## 4. Ejercicios
### Sintonizacion en lazo abierto

📚 Ejercicio 1: 
 Datos del sistema:

### Lazo secundario:
- **Función de transferencia:**  
  $G_2(s) = \frac{0.6 e^{-0.8s}}{4s + 1}$
- **Ganancia \$(K_2\$):** 0.6  
- **Constante de tiempo (\$tau_2\$):** 4 min  
- **Tiempo muerto (\$(t_{m2}\$):** 0.8 min  

### Lazo primario:
- **Función de transferencia:**  
  $G_1(s) = \frac{e^{-12s}}{20s + 1}$
- **Ganancia (\$(K_1\$):** 1  
- **Constante de tiempo (\$tau_1\$):** 20 min  
- **Tiempo muerto (\$(t_{m1}\$):** 12 min  


- **Ganancia proporcional:**  
  $K_{c2} = \frac{0.9}{K_2} \left( \frac{\tau_2}{t_{m2}} \right)$
- **Tiempo integral:**  
  $T_{i2} = 3.33 \cdot t_{m2}$

- **Ganancia proporcional:**  
  $K_{c2} = \frac{0.9}{0.6} \left( \frac{4}{0.8} \right) = 7.5$
- **Tiempo integral:**  
  $T_{i2} = 3.33 \cdot 0.8 = 2.664 \text{ min}$

### Controlador secundario:
 PI  
- **Parámetros:**  
  - $K_{c2} = 7.5$  
  - $T_{i2} = 2.664$ min  


Sintonización del Lazo Primario

- **Ganancia proporcional:**  
  $K_{c1} = \frac{1.2}{K_{Total}} \left( \frac{\tau_{Total}}{t_{mTotal}} \right)$
- **Tiempo integral:**  
  $T_{i1} = 2 \cdot t_{mTotal}$
- **Tiempo derivativo:**  
  $T_{d1} = 0.5 \cdot t_{mTotal}$
  

- **Ganancia total:**  
  $K_{Total} = K_1 \cdot 1 = 1$
- **Tiempo muerto total:**  
  $t_{mTotal} = t_{m1} + t_{m2} = 12 + 0.8 = 12.8 \text{ min}$
- **Constante de tiempo total:**  
  $\tau_{Total} \approx \tau_1 = 20 \text{ min}$
- **Ganancia proporcional:**  
  $K_{c1} = \frac{1.2}{1} \left( \frac{20}{12.8} \right) = 1.875$
- **Tiempo integral:**  
  $T_{i1} = 2 \cdot 12.8 = 25.6 \text{ min}$
- **Tiempo derivativo:**  
  $T_{d1} = 0.5 \cdot 12.8 = 6.4 \text{ min}$

### Controlador primario:
 PID  
- **Parámetros:**  
  - \$(K_{c1} = 1.875\$)  
  - \$(T_{i1} = 25.6 \text{ min}\$)  
  - \$(T_{d1} = 6.4 \text{ min}\$)  


📚 Ejercicio 2:

Datos del sistema:

### Lazo secundario:
- **Función de transferencia:**  
  $G_2(s) = \frac{0.7 e^{-1.2s}}{5s + 1}$
- **Ganancia ($K_2$):** 0.7  
- **Constante de tiempo ($\tau_2$):** 5 min  
- **Tiempo muerto ($t_{m2}$):** 1.2 min  

### Lazo primario:
- **Función de transferencia:**  
  $G_1(s) = \frac{e^{-15s}}{25s + 1}$
- **Ganancia ($K_1$):** 1  
- **Constante de tiempo ($\tau_1$):** 25 min  
- **Tiempo muerto ($t_{m1}$):** 15 min  

- **Ganancia proporcional:**  
  $K_{c2} = \frac{0.9}{K_2} \left( \frac{\tau_2}{t_{m2}} \right)$
- **Tiempo integral:**  
  $T_{i2} = 3.33 \cdot t_{m2}$

- **Ganancia proporcional:**  
  $K_{c2} = \frac{0.9}{0.7} \left( \frac{5}{1.2} \right) = 5.357$
- **Tiempo integral:**  
  $T_{i2} = 3.33 \cdot 1.2 = 3.996 \text{ min}$

### Controlador secundario:
 PI  
- **Parámetros:**  
  - $K_{c2} = 5.357$  
  - $T_{i2} = 3.996$ min 

- **Ganancia proporcional:**  
  $K_{c1} = \frac{1.2}{K_{Total}} \left( \frac{\tau_{Total}}{t_{mTotal}} \right)$
- **Tiempo integral:**  
  $T_{i1} = 2 \cdot t_{mTotal}$
- **Tiempo derivativo:**  
  $T_{d1} = 0.5 \cdot t_{mTotal}$

- **Ganancia total:**  
  $K_{Total} = K_1 \cdot 1 = 1$
- **Tiempo muerto total:**  
  $t_{mTotal} = t_{m1} + t_{m2} = 15 + 1.2 = 16.2 \text{ min}$
- **Constante de tiempo total:**  
  $\tau_{Total} \approx \tau_1 = 25 \text{ min}$
- **Ganancia proporcional:**  
  $K_{c1} = \frac{1.2}{1} \left( \frac{25}{16.2} \right) = 1.852$
- **Tiempo integral:**  
  $T_{i1} = 2 \cdot 16.2 = 32.4 \text{ min}$
- **Tiempo derivativo:**  
  $T_{d1} = 0.5 \cdot 16.2 = 8.1 \text{ min}$

### Controlador primario:
PID  
- **Parámetros:**  
  - $K_{c1} = 1.852$  
  - $T_{i1} = 32.4$ min
  - $T_{d1} = 8.1$ min
    
### Sintonizacion en lazo abierto Austin

📚 Ejercicio 1: 
Datos del sistema:

### Lazo secundario:
- **Ganancia ($K_2$):** 0.5 %TT102/%CO2  
- **Constante de tiempo ($\tau_2$):** 3 min  
- **Tiempo muerto ($t_{02}$):** 0.8 min  

### Lazo primario:
- **Ganancia ($K_1$):** 0.4 %TT101/%CO2  
- **Constante de tiempo ($\tau_1$):** 10 min  
- **Tiempo muerto ($t_{01}$):** 2.5 min  

$frac{\tau_2}{\tau_1} = \frac{3}{10} = 0.3$

Como $0.02 \leq 0.3 \leq 0.38$, se usa la **Tabla 2**.

Si el controlador secundario es **P** y el primario es **PI**.

### controlador primario (PI):

- **Ganancia proporcional:**  
  $K_{c1} = 0.75 \left( \frac{K_2}{K_1} \right) \left( \frac{t_{01}}{\tau_1} \right)^{-1.07} \left( \frac{\tau_2}{\tau_1} \right)^{0.1}$

- **Tiempo integral:**  
  $\tau_{i1} = \tau_1$

- **Ganancia proporcional:**  
  $K_{c1} = 0.75 \left( \frac{0.5}{0.4} \right) \left( \frac{2.5}{10} \right)^{-1.07} \left( \frac{3}{10} \right)^{0.1}$
  $K_{c1} = 0.75 \cdot 1.25 \cdot 2.297 \cdot 0.851 = 1.83$
- **Tiempo integral:**  
  $\tau_{i1} = 10 \text{ min}$

### Controlador primario:
PI  
- **Parámetros:**  
  - $K_{c1} = 1.83$  
  - $\tau_{i1} = 10$ min  

El controlador secundario es **P**, por lo que solo necesita la ganancia proporcional.

- **Ganancia del controlador secundario (P):**  
  $$K_{c2} = 1 \quad \text{(valor típico para un controlador P en este método)}$$

### Controlador secundario:
P  
- **Parámetros:**  
  - $K_{c2} = 1$  

### Sintonizacion en lazo Cerrado Hang

📚 Ejercicio 1: 
Datos del sistema:

### Lazo secundario:
- **Función de transferencia:**  
  $$G_2(s) = \frac{e^{-0.6s}}{(1 + 0.6s)^2}$$
- **Ganancia ($K_2$):** 1  
- **Constante de tiempo ($\tau_2$):** 0.6 min  
- **Tiempo muerto ($t_{m2}$):** 0.6 min  

### Lazo primario:
- **Función de transferencia:**  
  $$G_1(s) = \frac{e^{-2.5s}}{(1 + 2.5s)^2}$$
- **Ganancia ($K_1$):** 1  
- **Constante de tiempo ($\tau_1$):** 2.5 min  
- **Tiempo muerto ($t_{m1}$):** 2.5 min  

Se realiza una prueba de relé en el lazo secundario para determinar los parámetros del controlador.
### Prueba de relé:
- **Amplitud de oscilación ($a$):** 1  
- **Período de oscilación ($T_{u2}$):** 0.8 min  
### Cálculo de la ganancia última ($K_{u2}$):
$$K_{u2} = \frac{4d}{\pi a}$$
Donde $d$ es la amplitud del relé (supongamos $d = 1$):

$$K_{u2} = \frac{4 \cdot 1}{\pi \cdot 1} = 1.273$$

### Ajuste del controlador secundario (PI):
- **Ganancia proporcional:**  
  $$K_{p2} = 0.45 \cdot K_{u2} = 0.45 \cdot 1.273 = 0.573$$
- **Tiempo integral:**  
  $$T_{i2} = \frac{T_{u2}}{1.2} = \frac{0.8}{1.2} = 0.666 \text{ min}$$

### Controlador secundario:
- **Tipo:** PI  
- **Parámetros:**  
  - $K_{p2} = 0.573$  
  - $T_{i2} = 0.666$ min  

Se realiza una prueba de relé en el lazo primario, incluyendo el lazo secundario ya sintonizado.

### Prueba de relé:
- **Amplitud de oscilación ($a$):** 1  
- **Período de oscilación ($T_{u1}$):** 6 min  

### Cálculo de la ganancia última ($K_{u1}$):

$$K_{u1} = \frac{4d}{\pi a}$$

Donde $d$ es la amplitud del relé (supongamos $d = 1$):

$$K_{u1} = \frac{4 \cdot 1}{\pi \cdot 1} = 1.273$$

### Ajuste del controlador primario (PID):
- **Ganancia proporcional:**  
  $$K_{p1} = 0.6 \cdot K_{u1} = 0.6 \cdot 1.273 = 0.764$$
- **Tiempo integral:**  
  $$T_{i1} = \frac{T_{u1}}{2} = \frac{6}{2} = 3 \text{ min}$$
- **Tiempo derivativo:**  
  $$T_{d1} = 0.125 \cdot T_{u1} = 0.125 \cdot 6 = 0.75 \text{ min}$$

### Controlador primario:
- **Tipo:** PID  
- **Parámetros:**  
  - $K_{p1} = 0.764$  
  - $T_{i1} = 3$ min  
  - $T_{d1} = 0.75$ min  


## 5. Conclusiones
* por medio de esta clase se desarrollaron los conocimientos para implementar los obervadores de estados en sistemas con multpiles variables esto permite que se puedan hacer estimaciones de variables que no son medibles, esto para mejorar el desempeño y tambien la estabilidad del sistema.
es importante tener en cuenta que de un buen diseño de la matriz de ganancia asi como tambien de la verificación de la observabilidad es que se puede reducir de manera adecuada el error de esstimacion.
* efe
* 

## 6. Referencias
* J. E. Cote Ballesteros, E.P.2. Control movimiento. Control cascada, Universidad ECCI, 2025.
* C. Smith and A. Corripio, Principles and Practice of Automatic Process Control, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2005.






