# CLASE 13/03/2025
# Simscape multibody

El control cascada tiene como objetivo principal rechazar las perturbaciones, es una estrategia que se implementa con el objetivo de mejorar la respuesta de un sistema antes perturbaciones, de igual manera que también mejorando la estabilidad.
Su desarrollo consiste en el uso de dos controladores en serie, en los que se tiene en cuenta características tales como que las variables que voy a controlar debe ser la más externa, que el controlador secundario debe ser más rápido que el controlador primario y aquí es donde se aclara que el controlador secundaria debería tener un controlador P o PI, para que el controlador primario pueda ser PI o PID con el fin de que se pueda eliminar el error de estado estacionario, es importante tener en cuenta que esta arquitectura del control cascada se desea implementar donde se desee hacer más rápida la dinámica de la variable controlada.



## 1. Control cascada
### 1.1 Control cascada
Teniendo en cuenta la breve introducción, el control cascada busca emplear dos lazos de control en donde el controlador primario actúe sobre una variable especifica, mientras que el controlador secundario controle una variable dependiente de la primaria y así mejorar el funcionamiento optimo del sistema y reducir el error de estado estacionario.



### 1.2 Aplicaciones para el control cascada
El control cascada se puede implementar en sistemas que cumplan con unas características especificas clasificadas a continuación:
* cuando se presentan perturbaciones que afectan en gran manera la variable que está siendo controlada.
* cuando se busca mejorar la respuesta de nuestro sistema en comparación en cambios significativos en la entrada.
* casos particulares cuando las variables secundarias tienen una dinámica más rápida que la variable primaria que quiere ser controlada.

## 2. Métodos de Sintonización

### 2.1 Métodos de sintonización en lazo abierto
Este método se desarrolla por medio de pruebas en lazo abierto y sin retroalimentación para obtener los parámetros que harán parte de nuestros controladores.
las pruebas se hacen de manera separadas en cada lazo de control y así mismo se obtienen las ganancias, las constantes de tiempo y el tiempo muerto para posteriormente calcular los ajustes para el funcionamiento óptimo de los controladores.


![image](https://github.com/user-attachments/assets/b5b9b3b5-b53e-4586-b7b6-b07d43b56687)

**Imagen 1: Diagrama de bloques sistema en lazo abierto**

### 2.2 Métodos empíricos de sintonización en lazo abierto Austin
El método de Austin es una alternativa de sintonización que permite sintonizar ambos controladores en una sola prueba de lazo abierto.

con la aplicación de este método es importante tener en cuenta una característica especifica que se trata que si el controlador secundario es P o PI se pueden proporcionar ecuaciones de ajuste para el controlador primario PI o PID 

para realizar este método se realiza un cambio en la entrada, bien sea una señal de escalón al actuador del sistema y se registran las respuestas de las variables secundarias y primarias.

con la respuesta que obtuvimos de la variable secundaria podemos determinar la ganancia en este caso K2, también el tiempo secundario T2 y el tiempo de muestreo secundario tm2.

![image](https://github.com/user-attachments/assets/8faba7ff-e8d5-48f3-92ed-5d78892c4060)

**Tabla 1: Coeficientes sintonización Metodo Austin T2/T1>0.38**

es importante tener en cuenta que nuestra primer tabla es funcional cuando T2/T1 es mayor a 0.38, sino se recomienda usar nuestra segunda tabla.

![image](https://github.com/user-attachments/assets/066f5502-4156-48a2-ba0b-a011479aec6a)

**Tabla 2: Coeficientes sintonización Metodo Austin T2/T1 <= 0.35**

luego de que realizamos el correspondiente ajuste al controlador secundario, de nuevo registramos la respuesta de nuestra variable primaria y tomamos tanto la ganancia del proceso primario K1, así como T1 y tm1, así se obtiene el tiempo muerto total y la constante de tiempo total para hallar los parámetros del controlador primario.

### 2.3 Métodos empíricos de sintonización en lazo cerrado

* Método Hang
El desarrollo de este método propone una sintonización por medio de un lazo cerrado (Relé) el cual genera oscilaciones en el sistema que permiten sintonizar progresivamente el lazo secundario y posteriormente el primario dentro del lazo anterior.
con las oscilaciones generadas en el sistema se puede observar el comportamiento del proceso controlado y obtener los parámetros para sintonizar el controlador secundario.
posteriormente se ubica el controlador secundario sintonizado en el lazo primario y se realiza de nuevo la sintonización con el método del relé, de nuevo se obtienen el comportamiento del proceso y se sintoniza el controlador primario y así se obtiene una mejora en la dinámica global del sistema.




##  3. Definiciones
>🔑 *Control Cascada:* Estrategia de control que utiliza dos lazos (primario y secundario) para mejorar la respuesta del sistema.
>
>🔑 *Lazo Secundario:* Bucle interno de control que regula una variable secundaria más rápida, actuando como un controlador auxiliar para mejorar la respuesta del sistema principal.
>
>🔑 *Lazo Primario:* Bucle externo de control que regula la variable principal, utilizando la salida del lazo secundario como referencia para lograr un control más preciso.
>>
>🔑 *Sintonización de Controladores:* Proceso de ajustar los parámetros de los controladores (ganancia, tiempo integral y tiempo derivativo) para optimizar el rendimiento del sistema en cascada.
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

* Es importante reconocer la importancia del control cascada cuando se busca mejorar la estabilidad, así como la respuesta del sistema frente a las perturbaciones que se buscan reducir con el mismo.
* realizar correctamente la sintonización de los controladores es indispensable para obtener un rendimiento optimo independientemente de los métodos empleados bien sean empíricos o por medio de técnicas computacionales.
* a la hora de elegir un método de sintonización dependerá de las características con las cuente el sistema, así como también de las pruebas que se le puedan realizar al mismo lo que también permite tener una amplia variedad de pruebas, tanto en lazo abierto, como en lazo cerrado.
* aplicar el control cascada es eficaz cuando la variable secundaria de un sistema es más rápida que la primaria, por ende, habrá perturbaciones que afectaran el tiempo de establecimiento del sistema y allí es cuando se buscara mejorar es tiempo de establecimiento o cuando se quiere mejorar la dinámica del sistema.



## 6. Referencias
* J. E. Cote Ballesteros, E.P.2. Control movimiento. Control cascada, Universidad ECCI, 2025.
* C. Smith and A. Corripio, Principles and Practice of Automatic Process Control, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2005.






