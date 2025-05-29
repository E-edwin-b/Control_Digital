
# Control por Rechazo Activo de Perturbaciones (ADRC): Teoría y Aplicaciones

## 1. Introducción Histórica y Conceptual

El Control por Rechazo Activo de Perturbaciones (ADRC, por sus siglas en inglés: *Active Disturbance Rejection Control*) fue desarrollado por el Dr. Zhiqiang Gao a principios de los años 2000 como una respuesta a las limitaciones del controlador PID tradicional. Esta estrategia surge de la necesidad de controlar sistemas que presentan dinámicas internas desconocidas, perturbaciones externas no medidas, no linealidades marcadas y parámetros inciertos o variables en el tiempo.

La filosofía del ADRC se sustenta en tres pilares fundamentales:

- **Estimación activa:** todas las incertidumbres se tratan como una “perturbación generalizada” que es posible observar.
- **Cancelación en tiempo real:** la perturbación estimada se compensa antes de afectar significativamente la salida del sistema.
- **Simplificación del proceso:** se transforma el sistema en estructuras canónicas simples, típicamente cadenas de integradores.

## 2. Tipos de ADRC: Lineal vs No Lineal

### 2.1 ADRC No Lineal (NADRC)

El NADRC representa la formulación original, utilizando funciones no lineales para un rechazo más agresivo de perturbaciones. Es eficaz frente a:

- No linealidades como fricción, histéresis, saturación.
- Perturbaciones de alta frecuencia.
- Requisitos de respuesta rápida.

#### Observador de Estado Extendido No Lineal (NESO)

El observador NESO emplea la función no lineal `fal`, definida como:

```math
\text{fal}(e, \alpha, \delta) = 
\begin{cases} 
\frac{e}{\delta^{1-\alpha}} & \text{si } |e| \leq \delta \\
|e|^{\alpha} \cdot \text{sign}(e) & \text{si } |e| > \delta
\end{cases}
```

Las ecuaciones del observador:

```math
\begin{cases}
\dot{z}_1 = z_2 - \beta_1 \text{fal}(e, \alpha_1, \delta) \\
\dot{z}_2 = z_3 + b_0 u - \beta_2 \text{fal}(e, \alpha_2, \delta) \\
\dot{z}_3 = -\beta_3 \text{fal}(e, \alpha_3, \delta)
\end{cases}
```

La ley de control no lineal:

```math
u = \frac{1}{b_0} (u_0 - z_3), \quad
u_0 = k_1 \text{fal}(r_1 - z_1, \alpha'_1, \delta') + k_2 \text{fal}(r_2 - z_2, \alpha'_2, \delta')
```

### 2.2 ADRC Lineal (LADRC)

El LADRC usa componentes lineales, facilitando análisis y diseño. Es ideal para:

- Sistemas cuasi-lineales.
- Recursos computacionales limitados.

#### Observador de Estado Extendido Lineal (LESO)

Modelo extendido:

```math
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = x_3 + b_0 u \\
\dot{x}_3 = h(t)
\end{cases}, \quad y = x_1
```

Estructura del LESO:

```math
\begin{cases}
\dot{z}_1 = z_2 + l_1(y - z_1) \\
\dot{z}_2 = z_3 + b_0 u + l_2(y - z_1) \\
\dot{z}_3 = l_3(y - z_1)
\end{cases}
```

Ganancias:

```math
\ell_i = \frac{(n+1)!}{i!(n+1-i)!} \omega_0^i
```

#### Ley de Control Lineal

```math
u = \frac{1}{b_0} (u_0 - z_3), \quad
u_0 = k_1 (r - z_1) + k_2 (\dot{r} - z_2)
```

## 3. Representación en Espacio de Estados y Estimación de Perturbaciones

Ejemplo con sistema masa-resorte-amortiguador:

```math
M \ddot{y} + B \dot{y} + K y = u(t) \Rightarrow
\ddot{y} = \frac{1}{M} u(t) - \frac{B}{M} \dot{y} - \frac{K}{M} y = b_0 u + \xi(t)
```

Modelo extendido:

```math
\dot{X} = A X + B u, \quad y = C X
A = \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix}, \quad
B = \begin{bmatrix} 0 \\ b_0 \end{bmatrix}, \quad
C = \begin{bmatrix} 1 & 0 \end{bmatrix}
\dot{x}_3 = h(t)
```

## 4. Aplicaciones, Comparativas y Desarrollo Futuro

### Aplicación práctica

- Error < 1% en régimen permanente
- Rechazo de escalones en < 0.1 s
- Robustez frente a ±50% en parámetros

### Comparativa de Desempeño

| Métrica               | NADRC   | LADRC   | PID     |
|-----------------------|---------|---------|---------|
| Tiempo establecimiento| 0.05 s  | 0.08 s  | 0.15 s  |
| Sobrepaso máximo      | 1.2%    | 2.5%    | 5.8%    |
| Rechazo perturbación  | 98%     | 92%     | 85%     |
| Robustez paramétrica  | Excelente | Buena | Regular |

### Desarrollo Futuro

- ADRC Adaptativo
- ADRC con IA (redes neuronales, deep learning)
- ADRC distribuido y multi-agente
- ADRC cuántico

## 5. Conclusiones

El ADRC ofrece una estrategia moderna de control robusto con capacidad de manejar incertidumbres y perturbaciones sin requerir modelos precisos. Su arquitectura modular, observadores de perturbaciones y diseño generalizable lo posicionan como una herramienta fundamental en la automatización moderna. La elección entre NADRC y LADRC depende del compromiso entre rendimiento, complejidad y recursos.

## 6. Referencias

- Gao, Z. (2014). *Active Disturbance Rejection Control: A Paradigm Shift in Feedback Control System Design*. ACC.
- Han, J. (2009). *From PID to Active Disturbance Rejection Control*. IEEE Trans. Industrial Electronics.
- Rodríguez, J. E. (2025). *Control de Movimiento - ADRC*. Universidad ECCI.
- Herbst, G. (2013). *A Simulative Study on ADRC*. Control Engineering Practice.
- Xue, W. (2020). *ADRC for Nonlinear Systems: Theory and Applications*. Springer.
