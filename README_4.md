# CLASE 20/05/2025
# Controlador por Rechazo Activo de Perturbaciones (ADRC)

El ADRC tambien conocido como el controlador por rechazo de peturbaciones, se conoce como un modelo que innova en el campo del control moderno ya que es un modelo que surge debido a la necesidad de diseñar e implementar controladores robustos con altas capacidades para funcionar de manera eficaz en sistema que cuentan con modelos matematicos incompletos, incertidumbres externas, pertubarciones externas inpredecibles, entre otros.

Esta tecnica fue desarrollada por el Dr Zhiqiang Gao en la decada de los 90, en comparacion con los controladores tradicionales como el controlador PID que consiste en contar con un modelo preciso del sistema, con parametros que usualmente se ajustan de manera empirica, el controlador ADRC cuenta con una perspectiva mucho mas amplia y que se puede adaptar a diferentes circunstancias, es en este caso donde el controlador PID se queda un poco corto, ya que en muchos casos es muy eficaz, se ve muy limitado a la hora de enfrentar perturbaciones imprevistas o variaciones significativas en el sistema. Por otro lado el ADRC se separa del controlador PID, deja de depender directamente de un modelo preciso del sistema, contemplando el sistema del control como una perturbacion total, en donde se incluyen perturbaciones externas, efectos del sistema que no se hallan modelado, incertidumbres y errores en el modelado del sistema, por ende se estima esa perturbacion total en tiempo real, posteriormente se rechaza mediante una accion de control correspondiente a la misma.

## 1. Conceptos fundamentales del ADRC

El ADRC cuenta con un enfoque general en rechazar de manera activa cualquier tipo de perturbacion sin necesidad de tener en cuenta especificamente la naturaleza de la misma, de igual manera se enfoca en confomar un observador que permita estimar las variables de estado y la perturbacion total que afectara al sistema. una vez establecido esto, posteriormente se aplica una accion de control que tenie en cuenta la informacion anterior y genera las respectivas acciones correctivas.

### 1.1. Componentes del ADRC

Un sistema ADRC esta constituido de la siguiente manera:

- **Generador de trayectoria:** Generalmente se puede conocer como el encargado de definir los perfiles de movimiento deseados pues genera señales de referencia suaves y diferenciables, que permite evitar discontinuidades en la entrada de control.

- **Observador de Estado Extendido:** Se encarga de estimar tanto los estados internos del sistema como la perturbación total, es importante considerar esta estimación pues es clave para garantizar el rechazo activo de perturbaciones.

- **Ley de control por realimentación de estados:** Su enfoque combina la realimentacion de estados y la compesacion de pertubaciones, con base en los valores estimados calcula la señal de control necesaria para seguir la trayectoria deseada, mientras cancela la perturbación.

es importante tener claro que estos componentes deben trabajar en conjunto para asi contar con una respuesta rapida, robusta y efecctiva frente a las condiciones que se puedan presentar en el sistema a controlar.

<div align="center">
  <img src="https://github.com/user-attachments/assets/09ca765d-c468-4ebc-ae25-197d9775aead" width="70%" >
  <p><strong>Imagen 1: Estructura del controlador en primer orden</strong></p>
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/95fdf07a-1902-4628-b60c-4a5e1f73c5db" alt="image" width="70%">
  <p><strong>Imagen 2: Estructura del controlador en segundo orden</strong></p>
</div>

## 2. Tipos de ADRC

### 2.1 ADRC No Lineal (NADRC)

El NADRC, su fundamento principal se establece por medio de la no linealidad y así obtener un rechazo a las perturbaciones con una respuesta mucho mas fuerte y que se pueda adaptar, este tipo de controlador suele ser mucho mas eficaz en sistemas con no linealidades como la histéresis, fricción y algunos otros, además de perturbaciones que pueden ser de alta frecuencia o con necesidades de rápida respuesta.

En el NADRC cuenta en su estructura general con un observador de estados extendido no lineal, que es el encargado de incluir la perturbación total como un estado y así se ajustan las ganancias del controlador de una manera mucho mas "flexible", también se implementa una función para no  linealidades conocida como "fal" y que se constituye de la siguiente manera:

$$
\text{fal}(e, \alpha, \delta) = \begin{cases} 
\frac{e}{\delta^{1-\alpha}} & \text{si } |e| \leq \delta \\
|e|^{\alpha} \cdot \text{sign}(e) & \text{si } |e| > \delta
\end{cases}
$$

El observador que constituye principalmente el NADRC es el encargado de modelar la perturbación general en un estado adicional, como se puede observar en la siguiente estructura de un observador para un sistema de segundo orden:

$$
\begin{cases}
\dot{z}_1 = z_2 - \beta_1 \text{fal}(e, \alpha_1, \delta) \\
\dot{z}_2 = z_3 + b_0 u - \beta_2 \text{fal}(e, \alpha_2, \delta) \\
\dot{z}_3 = -\beta_3 \text{fal}(e, \alpha_3, \delta)
\end{cases}
$$

implementar la ley de control, establece una retroalimentación proporcional de errores en los estados de la perturbación estimada:

$$u = \frac{1}{b_0} \left( u_0 - z_3 \right)$$

Donde $u_0$ es generado como:

$$u_0 = k_1 \text{fal}(r_1 - z_1, \alpha'_1, \delta') + k_2 \text{fal}(r_2 - z_2, \alpha'_2, \delta')$$

la anterior estructura es indispensable para que el controlador tenga una respuesta rápida frente a los cambios que se presenten en el sistema, permitiendo verificar la precisión para el seguimiento de referencias.  

### 2.2 ADRC Lineal (LADRC)

El LADRC contempla el ADRC y lo simplifica solo empleando  los componentes lineales, esto permite tener un diseño mas compacto y así realizar un análisis de estabilidad más completo.
implementar el LADRC es esencial frente a necesidades especificas como pueden serlo sistemas con no linealidades muy prominentes o cuando se cuenta con recursos computacionales limitados.

En el desarrollo del LADRC, se obtiene el observador de estado extendido, conocido por sus siglas "LESO" el cual se conforma por su estructura matricial que agrega un espacio mas para poder incluir las perturbaciones generalizadas como un estado mas.
un ejemplo practico del "LESO" es el siguiente modelo extendido para un sistema de segundo orden:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = x_3 + b_0 u \\
\dot{x}_3 = h(t)
\end{cases}, \quad y = x_1
$$

Donde $x_3$ representa la perturbación generalizada $\xi(t)$, que puede ser constante, variable lentamente o incluso de forma conocida. El LESO estima estos estados mediante:

$$
\begin{cases}
\dot{z}_1 = z_2 + l_1(y - z_1) \\
\dot{z}_2 = z_3 + b_0 u + l_2(y - z_1) \\
\dot{z}_3 = l_3(y - z_1)
\end{cases}
$$

Las ganancias del observador $l_1, l_2, l_3$ se seleccionan para que los polos de la dinámica del error del observador se ubiquen en el semiplano izquierdo, asignando un valor fijo de frecuencia $\omega_0$:

$$
\ell_i = \frac{(n+1)!}{i!(n+1-i)!} \omega_0^i
$$

La ley de control esta fundamentada en lae realimentación de estados y cancelación de perturbación, y se expresa como:

$$u = \frac{1}{b_0} \left( u_0 - z_3 \right), \quad u_0 = k_1 (r - z_1) + k_2 (\dot{r} - z_2)$$

Donde $r$ y $\dot{r}$ son la referencia y su derivada. Los parámetros $k_1$ y $k_2$ se seleccionan para ubicar los polos de la dinámica del error de seguimiento mediante un polinomio característico de Hurwitz:

$$
P_{e_y}(s) = s^2 + k_1 s + k_0
$$

la anterior estructura es importante para implementar un controlador robusto y que además sea eficiente, pues contamos con una gran capacidad al rechazo de perturbaciones y una fácil interpretación de la estabilidad del mismo.

## 3. Representación en Espacio de Estados y Estimación de Perturbaciones

El ADRC cuenta con una característica que resalta, esta consta en la transformación del sistema original, sea considerado lineal o no lineal, en una forma canónica permitiendo un diseño modular más practico, como se modela el siguiente sistema masa-resorte-amortiguado:  

$$M \ddot{y} + B \dot{y} + K y = u(t)$$

La ecuación puede expresarse como:

$$\ddot{y} = \frac{1}{M} u(t) - \frac{B}{M} \dot{y} - \frac{K}{M} y = b_0 u + \xi(t)$$

por medio de esto podemos interpretar la estructura que se va a generar por medio del ADRC: en una planta que cuenta con mas de una perturbación $\xi(t)$ y que además cuenta con una dinámica desconocida y perturbaciones externas, se puede representar como:

$$
\dot{X} = AX + Bu, \quad y = CX
$$

Donde:

$$
A = \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ b_0 \end{bmatrix}, \quad C = \begin{bmatrix} 1 & 0 \end{bmatrix}
$$

Y se extiende el modelo con una variable adicional $x_3$ que representa la perturbación total, con su dinámica incluida como:

$$
\dot{x}_3 = h(t)
$$

realizar esta ampliación nos permite tener una estimación del estado y la perturbación por el observador extendido, el sistema de rechazo de perturbaciones que tiene el ADRC es primordial ya que este se encarga de estimar las perturbaciones en tiempo real y cancelarlas antes de que se afecte la salida del sistema, esto es lo que nos permite contar con un alta robustez y respuesta frente a esas perturbaciones desconocidas o mal modeladas.

<div align="center">
  <img src="https://github.com/user-attachments/assets/39a61253-8e83-4151-8fac-20bba0966e62" alt="image" width="40%">
  <p><strong>Imagen 3: Pruebas de desempeño</strong></p>
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/fee9e2f4-584c-4a54-a481-1fc57d9566d6" alt="image" width="40%">
  <p><strong>Imagen 4: Pruebas de desempeño</strong></p>
</div>


## 3. Definiciones

> 🔑 *Control ADRC:* Estrategia de control basada en estimar y rechazar activamente perturbaciones e incertidumbres, permitiendo el control robusto sin un modelo preciso.

> 🔑 *(Observador de Estados Extendido):* Observador que estima los estados del sistema y la perturbación total como un estado adicional.

> 🔑 *Perturbación total:* Suma de la dinámica no modelada, incertidumbre paramétrica y perturbaciones externas que afectan el desempeño del sistema.

> 🔑 *LADRC:* Versión lineal del ADRC que utiliza observadores tipo Luenberger y control por realimentación lineal.

> 🔑 *NADRC:* Versión no lineal del ADRC que emplea funciones no lineales para estimar y compensar perturbaciones.


## 4. Conclusiones

El ADRC es un controlador eficaz y flexible para el diseño y modelamiento de sistemas de control, del ADRC podemos destacar su gran capacidad para rechazar perturbaciones en tiempo real sin la necesidad de contar con un modelo matemático exacto del sistema, por ende este controlador es ideal para esos sistemas complejos, que no son lineales o que cuentan con perturbaciones externas que afectan en gran manera, el observador de estados extendidos es primordial para obtener una estimación precisa de esta perturbación total y así poder cancelar las misma mediante la ya conocida ley de control.

En el desarrollo del controlador ADRC es importante conocer que si se desea un optimo desempeño del mismo, es de suma importancia poder interpretar como diseñar de manera correcta el observador y así seleccionar los parámetros apropiados para el controlador, que permitan tener estabilidad y un tiempo de respuesta optimo, por ultimo este controlador presenta una solución importante a las perturbaciones con el rechazo activo de las misma cuando se implementa com un pilar fundamental en el diseño del mismo controlador ADRC.

el controlador PID el cual es comúnmente implementado, presenta una gran variedad de limitaciones ya que este depende de un modelamiento preciso del sistema así como de la sintonización del mismo al ser empírica, estos aspectos hacen que el controlador pueda verse afectado por las perturbaciones que no sean tenidas en cuenta durante el modelamiento, en contraste, el ADRC presenta una solución eficaz partiendo de la no dependencia de un  modelo exacto, así com también estimando y rechazando constantemente las perturbaciones, bien sena internas o externas en tiempo real gracias a sus observador de estados extendido, la capacidad del ADRC de interpretar las incertidumbres como una perturbación total, le da esa robustez en entornos dinámicos, en donde el PID se ve afectado.

## 5. Referencias

- Gao, J. (2003). *Scaling and bandwidth-parameterization based controller tuning*, American Control Conference.
- Rodríguez, J. E. (2025). *control de movimiento ADRC*, Universidad ECCI.
- Ogata, K. (2010). *Ingeniería de Control Moderna*, Prentice Hall.
"""
