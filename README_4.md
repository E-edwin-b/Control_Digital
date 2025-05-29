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

## 2. Tipos de ADRC

- **ADRC No Lineal(NADRC):**

Esta tecnica de control extiende el ADRC e incorpora funciones no lineales para mejorar el comportamiento y desempeño para sistemas con dinamicas complejas, generalmente consiste en estimar y rechazar en tiempo real una perturbacion total por medio de un observador de estado extendido no lineal.



$$
\begin{cases}
 \dot{x}1  = x2\\
 \dot{x}2  = f(x,t)+b_{0}u  \\
 y  = x1 
\end{cases}
$$

para generalizar un poco se asocia el termino  f(x,t) para agrupar las dinamicas y perturbaciones, ademas el observador estima la siguiente funcion con la ganacia variable fal, de la siguiente manera

$$
\begin{cases}
\dot{z}_1 = z_2 - \beta_1 \, \text{fal}(e, \alpha_1, \delta) \\
\dot{z}_2 = z_3 + b_0 u - \beta_2 \, \text{fal}(e, \alpha_2, \delta) \\
\dot{z}_3 = -\beta_3 \, \text{fal}(e, \alpha_3, \delta)
\end{cases}
$$

a profundidad la funcion no lineal fal es la que permite la adaptabilidad del ADRC no lineal y se compone de la siguiente manera

$$
\text{fal}(e, \alpha, \delta) =
\begin{cases}
\displaystyle \frac{e}{\delta^{1 - \alpha}}, & \text{si } |e| \leq \delta \\
|e|^{\alpha} \cdot \text{sign}(e), & \text{si } |e| > \delta
\end{cases}
$$

el implementar la funcion fal permite tener un alto rendimiento cuando el error es grande, ademas el comportamiento sera suave cuando el error sea pequeño y contara con una trnasicion continua entre regionesestos parametros estan definidos

* α (0 < α < 1): Controla el grado de no linealidad
* δ: Define la región lineal alrededor del origen
* βi Ganancia del observador

  

- **ADRC Lineal(LADRC):**

## 2. Definiciones

> 🔑 *Control ADRC:* Estrategia de control basada en estimar y rechazar activamente perturbaciones e incertidumbres, permitiendo el control robusto sin un modelo preciso.

> 🔑 *(Observador de Estados Extendido):* Observador que estima los estados del sistema y la perturbación total como un estado adicional.

> 🔑 *Perturbación total:* Suma de la dinámica no modelada, incertidumbre paramétrica y perturbaciones externas que afectan el desempeño del sistema.

> 🔑 *LADRC:* Versión lineal del ADRC que utiliza observadores tipo Luenberger y control por realimentación lineal.

> 🔑 *NADRC:* Versión no lineal del ADRC que emplea funciones no lineales para estimar y compensar perturbaciones.

## 3. Observador de Estado Extendido (ESO)

### 3.1. Modelo extendido del sistema
Un sistema típico de segundo orden se modela inicialmente como:


Donde:

$\tau$: Torque aplicado [Nm] 

## 3. Observador de Estado Extendido (ESO)

### 3.1. Modelo extendido del sistema
Un sistema típico de segundo orden se modela inicialmente como:

$$
\\ddot{y}(t) = K u(t) + \\varepsilon(t)
$$

Donde $\\varepsilon(t)$ representa la perturbación total. Este modelo se reescribe en espacio de estados extendido, introduciendo $\\varepsilon$ como una nueva variable de estado:

$$
\\begin{aligned}
\\dot{x}_1 &= x_2 \\\\
\\dot{x}_2 &= K u + x_3 \\\\
\\dot{x}_3 &= x_4 \\\\
\\dot{x}_4 &= \\ddot{\\varepsilon}
\\end{aligned}
$$

### 3.2. Diseño del observador
El observador calcula una estimación $\\hat{x}$ de los estados verdaderos. Su diseño se basa en la corrección del error $e = y - \\hat{y}$ y tiene la forma:

$$
\\begin{aligned}
\\dot{\\hat{x}}_1 &= \\hat{x}_2 + \\lambda_3 e \\\\
\\dot{\\hat{x}}_2 &= K u + \\hat{x}_3 + \\lambda_2 e \\\\
\\dot{\\hat{x}}_3 &= \\hat{x}_4 + \\lambda_1 e \\\\
\\dot{\\hat{x}}_4 &= \\lambda_0 e
\\end{aligned}
$$

El polinomio característico asociado a la dinámica del error del observador es:

$$
P_e(s) = s^4 + \\lambda_3 s^3 + \\lambda_2 s^2 + \\lambda_1 s + \\lambda_0
$$

## 4. Diseño del Controlador

La ley de control se estructura para garantizar seguimiento de la referencia y rechazo activo de la perturbación:

$$
 u(t) = \\frac{1}{K} \\left( y^{(n)*} - \\sum_{i=0}^{n-1}k_i e^{(i)} - \\hat{\\varepsilon}(t) \\right)
$$

Donde:
- $y^{(n)*}$: Derivada de orden $n$ de la trayectoria deseada.
- $k_i$: Ganancias del controlador.
- $\\hat{\\varepsilon}(t)$: Perturbación estimada por el ESO.

Esta estructura permite imponer una dinámica deseada al error de seguimiento, expresada mediante un polinomio característico:

$$
P_e(s) = s^2 + k_1 s + k_0
$$

## 7. Conclusiones

El controlador ADRC se establece como una herramienta eficaz y flexible en el diseño de sistemas de control modernos. Su capacidad para rechazar perturbaciones en tiempo real, sin requerir un modelo matemático exacto, lo hace ideal para sistemas complejos, no lineales o con incertidumbre estructural. A través del Observador de Estado Extendido, se obtiene una estimación precisa de la perturbación total, lo que permite cancelar su efecto directamente mediante la ley de control.

El ADRC tiene aplicaciones en múltiples campos: control de movimiento, robótica, sistemas eléctricos, automatización industrial, entre otros. La implementación en entornos como Simulink o plataformas embebidas demuestra que es un método práctico y computacionalmente eficiente.

Para lograr un buen desempeño con ADRC, es fundamental entender cómo diseñar adecuadamente el observador y elegir parámetros de control apropiados que aseguren estabilidad y velocidad deseada. Este controlador representa un cambio de paradigma en la ingeniería de control, promoviendo un enfoque centrado en el rechazo activo de perturbaciones como pilar del diseño.

## 8. Referencias

- Gao, J. (2003). *Scaling and bandwidth-parameterization based controller tuning*, American Control Conference.
- Gao, J. (2014). *On the centrality of disturbance estimation and rejection in automatic control*, ISA Transactions.
- Rodríguez, J. E. (2025). *Presentación de clase ADRC*, Universidad ECCI.
- Ogata, K. (2010). *Ingeniería de Control Moderna*, Prentice Hall.
- Khalil, H. K. (2002). *Nonlinear Systems*, Prentice Hall.
- Isermann, R. (2006). *Automatic Control Systems*, Springer.
"""
