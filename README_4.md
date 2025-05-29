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

<p align="center">
  <img src="https://github.com/user-attachments/assets/09ca765d-c468-4ebc-ae25-197d9775aead" alt="image" width="500">

</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/95fdf07a-1902-4628-b60c-4a5e1f73c5db" alt="image" width="500">

</p>

## 2. Tipos de ADRC

### 2.1 ADRC No Lineal (NADRC)

El NADRC representa la formulación original del ADRC, donde se emplean funciones no lineales para obtener un rechazo de perturbaciones más agresivo y adaptativo. Esta variante es particularmente eficaz en sistemas con fuertes no linealidades como fricción, histéresis o saturaciones, así como en presencia de perturbaciones de alta frecuencia o requerimientos de respuesta rápida.

Su componente central es el Observador de Estado Extendido No Lineal (NESO), el cual incluye la perturbación total como un estado adicional. Para ajustar las ganancias de manera flexible, se emplea la función no lineal tipo “fal”, definida como:

$$
\text{fal}(e, \alpha, \delta) = \begin{cases} 
\frac{e}{\delta^{1-\alpha}} & \text{si } |e| \leq \delta \\
|e|^{\alpha} \cdot \text{sign}(e) & \text{si } |e| > \delta
\end{cases}
$$

El observador en NADRC modela explícitamente la perturbación generalizada como un estado adicional con dinámica propia. Por ejemplo, para un sistema de segundo orden, la estructura del observador es la siguiente:

$$
\begin{cases}
\dot{z}_1 = z_2 - \beta_1 \text{fal}(e, \alpha_1, \delta) \\
\dot{z}_2 = z_3 + b_0 u - \beta_2 \text{fal}(e, \alpha_2, \delta) \\
\dot{z}_3 = -\beta_3 \text{fal}(e, \alpha_3, \delta)
\end{cases}
$$

La ley de control para el NADRC incluye una realimentación proporcional de errores en estados y la cancelación explícita de la perturbación estimada:

$$u = \frac{1}{b_0} \left( u_0 - z_3 \right)$$

Donde $u_0$ es generado como:

$$u_0 = k_1 \text{fal}(r_1 - z_1, \alpha'_1, \delta') + k_2 \text{fal}(r_2 - z_2, \alpha'_2, \delta')$$

Esta estructura permite al controlador actuar con rapidez ante cambios bruscos o no modelados en el sistema, garantizando precisión en el seguimiento de referencia. Sin embargo, su implementación exige experiencia para seleccionar los parámetros $\beta_i$, $\alpha_i$, y $\delta$, y conlleva una carga computacional mayor.

### 2.2 ADRC Lineal (LADRC)

El LADRC es una simplificación del esquema ADRC que emplea componentes lineales, lo cual permite un diseño más sistemático y un análisis de estabilidad más directo. Está especialmente recomendado para sistemas con no linealidades suaves o para implementaciones en plataformas con recursos computacionales limitados.

En el LADRC, el Observador de Estado Extendido Lineal (LESO) se formula con una estructura matricial que extiende el espacio de estados para incluir la perturbación generalizada como un estado adicional. Para un sistema de segundo orden, el modelo extendido es:

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

Las ganancias del observador $l_1, l_2, l_3$ se seleccionan para que los polos de la dinámica del error del observador se ubiquen en el semiplano izquierdo, típicamente asignando un valor fijo de frecuencia $\omega_0$ y aplicando la fórmula binomial:

$$
\ell_i = \frac{(n+1)!}{i!(n+1-i)!} \omega_0^i
$$

La ley de control se basa en el principio de realimentación de estados y cancelación de perturbación, y se expresa como:

$$u = \frac{1}{b_0} \left( u_0 - z_3 \right), \quad u_0 = k_1 (r - z_1) + k_2 (\dot{r} - z_2)$$

Donde $r$ y $\dot{r}$ son la referencia y su derivada. Los parámetros $k_1$ y $k_2$ se seleccionan para ubicar los polos de la dinámica del error de seguimiento mediante un polinomio característico de Hurwitz:

$$
P_{e_y}(s) = s^2 + k_1 s + k_0
$$

Esta estructura permite implementar un controlador robusto y eficiente, con bajo costo computacional, buena capacidad de rechazo de perturbaciones y facilidad para el análisis de estabilidad mediante herramientas clásicas de teoría de control lineal.

## 3. Representación en Espacio de Estados y Estimación de Perturbaciones

Una característica distintiva del ADRC es que transforma el sistema original, sea lineal o no lineal, en una forma canónica que facilita el diseño modular. Para un sistema masa-resorte-amortiguador modelado como:

$$M \ddot{y} + B \dot{y} + K y = u(t)$$

La ecuación puede expresarse como:

$$\ddot{y} = \frac{1}{M} u(t) - \frac{B}{M} \dot{y} - \frac{K}{M} y = b_0 u + \xi(t)$$

Esta forma revela la estructura que el ADRC intenta modelar: una planta lineal ideal más una perturbación generalizada $\xi(t)$, que incluye los efectos de la dinámica desconocida y perturbaciones externas.

Esta forma se representa en espacio de estados extendido como:

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

Esta extensión permite la estimación simultánea del estado y la perturbación mediante el observador extendido. Cuando el sistema se discretiza, también se puede extender el modelo de espacio de estados para incluir perturbaciones discretas, tratando $d(k+1) = d(k)$ como una señal constante estimable por el observador.

El mecanismo de rechazo de perturbaciones en ADRC se fundamenta en estimar la perturbación en tiempo real y cancelar su efecto mediante prealimentación antes de que afecte la salida del sistema. Esto permite una alta robustez frente a perturbaciones desconocidas o modeladas de forma inexacta.

<p align="center">
  <img src="https://github.com/user-attachments/assets/39a61253-8e83-4151-8fac-20bba0966e62" alt="image" width="500">

</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/fee9e2f4-584c-4a54-a481-1fc57d9566d6" alt="image" width="500">

</p>


## 3. Definiciones

> 🔑 *Control ADRC:* Estrategia de control basada en estimar y rechazar activamente perturbaciones e incertidumbres, permitiendo el control robusto sin un modelo preciso.

> 🔑 *(Observador de Estados Extendido):* Observador que estima los estados del sistema y la perturbación total como un estado adicional.

> 🔑 *Perturbación total:* Suma de la dinámica no modelada, incertidumbre paramétrica y perturbaciones externas que afectan el desempeño del sistema.

> 🔑 *LADRC:* Versión lineal del ADRC que utiliza observadores tipo Luenberger y control por realimentación lineal.

> 🔑 *NADRC:* Versión no lineal del ADRC que emplea funciones no lineales para estimar y compensar perturbaciones.


## 4. Conclusiones

El controlador ADRC se establece como una herramienta eficaz y flexible en el diseño de sistemas de control modernos. Su capacidad para rechazar perturbaciones en tiempo real, sin requerir un modelo matemático exacto, lo hace ideal para sistemas complejos, no lineales o con incertidumbre estructural. A través del Observador de Estado Extendido, se obtiene una estimación precisa de la perturbación total, lo que permite cancelar su efecto directamente mediante la ley de control.

El ADRC tiene aplicaciones en múltiples campos: control de movimiento, robótica, sistemas eléctricos, automatización industrial, entre otros. La implementación en entornos como Simulink o plataformas embebidas demuestra que es un método práctico y computacionalmente eficiente.

Para lograr un buen desempeño con ADRC, es fundamental entender cómo diseñar adecuadamente el observador y elegir parámetros de control apropiados que aseguren estabilidad y velocidad deseada. Este controlador representa un cambio de paradigma en la ingeniería de control, promoviendo un enfoque centrado en el rechazo activo de perturbaciones como pilar del diseño.

## 5. Referencias

- Gao, J. (2003). *Scaling and bandwidth-parameterization based controller tuning*, American Control Conference.
- Gao, J. (2014). *On the centrality of disturbance estimation and rejection in automatic control*, ISA Transactions.
- Rodríguez, J. E. (2025). *Presentación de clase ADRC*, Universidad ECCI.
- Ogata, K. (2010). *Ingeniería de Control Moderna*, Prentice Hall.
- Khalil, H. K. (2002). *Nonlinear Systems*, Prentice Hall.
- Isermann, R. (2006). *Automatic Control Systems*, Springer.
"""
