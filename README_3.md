# CLASE 03/04/2025
# Elementos de Transmisión en Sistemas de Control de Movimiento

## Introducción

Los sistemas de transmisión mecánica constituyen la interfaz crítica entre los actuadores (motores) y las cargas en aplicaciones de control de movimiento. Este documento explora en profundidad los principios de funcionamiento, modelos matemáticos, criterios de selección y aplicaciones prácticas de los principales elementos de transmisión utilizados en ingeniería de control.

> 🔑 *Sistema de Transmisión Mecánica:* Conjunto de componentes que adaptan y transfieren energía cinética desde una fuente motriz hasta una carga, modificando características como velocidad, torque, dirección o tipo de movimiento (rotacional-lineal), garantizando que los requerimientos dinámicos de la aplicación sean satisfechos.

## 1. Fundamentos Teóricos

### 1.1. Conceptos Básicos de Dinámica Rotacional

#### 1.1.1. Leyes de Newton para Rotación
La dinámica rotacional se rige por principios análogos a los de traslación:

$$ \sum \tau = J\alpha $$

Donde:
- $\tau$: Torque aplicado [Nm]
- $J$: Momento de inercia [kg·m²]
- $\alpha$: Aceleración angular [rad/s²]

#### 1.1.2. Energía Cinética Rotacional
$$ E_k = \frac{1}{2}J\omega^2 $$

### 1.2. Parámetros Clave en Diseño de Transmisiones

| Parámetro | Descripción | Fórmula | Unidades |
|-----------|-------------|---------|----------|
| Relación de transmisión (N) | Cociente entre velocidad de entrada y salida | $N = \frac{\omega_{in}}{\omega_{out}}$ | Adimensional |
| Eficiencia (η) | Relación potencia salida/entrada | $\eta = \frac{P_{out}}{P_{in}}$ | % o decimal |
| Inercia reflejada ($J_{ref}$) | Inercia equivalente vista desde el motor | Depende del sistema | kg·m² |
| Torque reflejado ($\tau_{ref}$) | Torque equivalente en el eje motor | Depende del sistema | Nm |

## 2. Tipología de Elementos de Transmisión

### 2.1. Transmisiones Rotacional-Rotacional

#### 2.1.1. Engranajes (Gearboxes)
**Características:**
- Alta precisión de posicionamiento
- Mínimo backlash (en sistemas de calidad)
- Eficiencias típicas: 85-98%

**Ecuaciones Fundamentales:**
$$ N_{GB} = \frac{n_2}{n_1} = \frac{d_1}{d_2} $$
$$ J_{ref} = \frac{J_{load}}{\eta N_{GB}^2} $$
$$ \tau_{ref} = \frac{\tau_{load}}{\eta N_{GB}} $$

**Aplicaciones Típicas:**
- Robots industriales
- Cabezales de máquinas herramienta
- Sistemas de posicionamiento de alta precisión

#### 2.1.2. Sistemas Polea-Correa
**Variantes:**
- Correas planas
- Correas dentadas (timing belts)
- Correas trapezoidales

**Modelado Matemático:**
$$ N_{BP} = \frac{r_{lp}}{r_{ip}} $$
$$ J_{belt} = \frac{m_{belt}r_{ip}^2}{\eta} $$
$$ J_{total} = J_{ip} + J_{belt} + \frac{J_{lp} + J_{load}}{\eta N_{BP}^2} $$

**Ventajas Comparativas:**
- Absorción de vibraciones
- Mayor tolerancia a desalineaciones
- Operación silenciosa

### 2.2. Transmisiones Rotacional-Lineal

#### 2.2.1. Tornillos de Potencia
**Tipos:**
- Tornillos ACME (η ≈ 35-85%)
- Tornillos de bolas (η ≈ 85-95%)
- Tornillos de rodillos

**Parámetros Clave:**
- Paso (lead): Distancia por revolución [mm/rev]
- Cabeceo (pitch): Revoluciones por unidad de longitud [rev/m]

**Ecuaciones:**
$$ N_S = 2\pi p $$
$$ J_{ref} = \frac{m}{(2\pi p)^2} $$
$$ \tau_{load} = \frac{F_{ext}}{2\pi p\eta} $$

#### 2.2.2. Sistemas Piñón-Cremallera
**Consideraciones de Diseño:**
- Radio primitivo del piñón
- Módulo de los dientes
- Juego mecánico (backlash)

**Modelo Dinámico:**
$$ N_{RP} = \frac{1}{r_{pinion}} $$
$$ J_{ref} = J_{pinion} + \frac{m}{\eta N_{RP}^2} $$

### 2.3. Sistemas Especializados

#### 2.3.1. Bandas Transportadoras
**Configuraciones:**
- Polea simple
- Múltiples rodillos de soporte
- Sistemas curvos

**Análisis de Inercia:**
$$ J_{eq} = 2J_{pulley} + \frac{m_{belt} + m_{load}}{\eta N_{CV}^2} + \sum \frac{J_{idler}}{\eta (r_{idler}/r_{drive})^2} $$

## 3. Criterios de Selección

### 3.1. Relación de Inercia Óptima

La relación de inercia ($J_R$) es un parámetro crítico:

$$ J_R = \frac{J_{ref} + J_{transmission}}{J_{motor}} $$

**Guías de Diseño:**
- $J_R \leq 5$ para aplicaciones dinámicas
- $J_R \leq 10$ para aplicaciones estáticas
- $J_R \leq 2$ para servosistemas de alta performance

### 3.2. Análisis Térmico

La potencia disipada en la transmisión afecta la vida útil:

$$ P_{loss} = (1-\eta)P_{in} $$
$$ \Delta T = \frac{P_{loss}}{hA} $$

Donde:
- h: Coeficiente de transferencia térmica
- A: Área superficial

### 3.3. Consideraciones de Resonancia

Frecuencia natural del sistema:

$$ \omega_n = \sqrt{\frac{K_{shaft}}{J_{eq}}} $$

Donde $K_{shaft}$ es la rigidez torsional.

## 4. Ejercicios Resueltos

📚 **Ejercicio 1 - Análisis de Sistema con Engranajes**

Un servomotor con inercia de rotor $J_m = 5\times10^{-4}$ kg·m² acciona una carga de $J_{load} = 0.2$ kg·m² a través de un reductor de relación 10:1 con eficiencia del 95%. Calcular:

a) Inercia total reflejada al motor  
b) Relación de inercia del sistema  
c) Torque requerido en el motor para acelerar la carga a 2 rad/s²

**Solución:**

a) 
$$ J_{ref} = \frac{0.2}{0.95 \times 10^2} = 2.105 \times 10^{-3} \text{ kg·m²} $$
$$ J_{total} = 5\times10^{-4} + 2.105\times10^{-3} = 2.605\times10^{-3} \text{ kg·m²} $$

b)
$$ J_R = \frac{2.605\times10^{-3}}{5\times10^{-4}} = 5.21 $$

c)
$$ \tau_{motor} = J_{total} \times \alpha_{motor} = 2.605\times10^{-3} \times (2 \times 10) = 0.0521 \text{ Nm} $$

📚 **Ejercicio 2 - Diseño de Sistema Tornillo de Bolas**

Se requiere mover una carga lineal de 150 kg (incluyendo carro) con un tornillo de bolas (η=90%, pitch=5 mm/rev). Determinar:

a) Inercia equivalente  
b) Torque para acelerar a 1 m/s²  
c) Velocidad angular del motor a 0.5 m/s

**Solución:**

a)
$$ p = \frac{1}{0.005} = 200 \text{ rev/m} $$
$$ J_{ref} = \frac{150}{(2\pi \times 200)^2} = 9.49\times10^{-5} \text{ kg·m²} $$

b)
$$ F = ma = 150 \times 1 = 150 \text{ N} $$
$$ \tau = \frac{150}{2\pi \times 200 \times 0.9} = 0.133 \text{ Nm} $$

c)
$$ \omega = v \times 2\pi p = 0.5 \times 2\pi \times 200 = 628.32 \text{ rad/s} \approx 6000 \text{ RPM} $$

## 5. Simulación y Validación

### 5.1. Modelado en Simscape Multibody

**Flujo de trabajo recomendado:**
1. Creación de geometrías CAD
2. Definición de joints y constraints
3. Especificación de parámetros dinámicos
4. Configuración de actuadores/sensores
5. Análisis de resultados

**Parámetros clave a simular:**
- Respuesta transitoria
- Pérdidas por fricción
- Fuerzas de reacción
- Efectos térmicos

### 5.2. Análisis de Resultados Típicos

![Respuesta dinámica de sistema piñón-cremallera](images/transmision/pinion_cremallera_response.png)
*Figura 1: Curvas de velocidad angular vs desplazamiento lineal en sistema piñón-cremallera*

## 6. Casos de Estudio

### 6.1. Sistema de Posicionamiento de Alta Precisión

**Requerimientos:**
- Resolución: 0.01 mm
- Velocidad máxima: 1 m/s
- Carga: 50 kg
- Aceleración: 5 m/s²

**Solución Implementada:**
- Motor: Servomotor 400W, 3000 RPM
- Transmisión: Tornillo de bolas de 10 mm de paso
- Relación de inercia resultante: 3.8

### 6.2. Transportador Industrial de Alta Velocidad

**Desafíos:**
- Cargas variables (5-20 kg)
- Ciclos rápidos (1.5 segundos)
- Ambiente con polvo

**Configuración Óptima:**
- Transmisión por correa dentada
- Motores brushless con control vectorial
- Sistema de tensión automático

## 7. Mantenimiento y Diagnóstico

### 7.1. Indicadores de Fallo Comunes

| Síntoma | Causa Probable | Acción Correctiva |
|---------|----------------|-------------------|
| Aumento de ruido | Desgaste de dientes/rodamientos | Reemplazo de componentes |
| Calentamiento excesivo | Fricción aumentada, lubricación insuficiente | Revisar alineación, relubricar |
| Juego mecánico | Desgaste de componentes | Ajuste o reemplazo |
| Vibraciones | Desbalanceo, resonancia | Análisis modal, balanceo |

### 7.2. Protocolos de Mantenimiento Preventivo

1. **Inspección visual:** Semanal
2. **Verificación de lubricación:** Mensual
3. **Análisis de vibraciones:** Trimestral
4. **Chequeo de alineación:** Semestral
5. **Reemplazo preventivo:** Según horas de operación

## 8. Tendencias Tecnológicas

### 8.1. Avances en Materiales
- Compuestos poliméricos autolubricados
- Cerámicas estructurales para alta temperatura
- Recubrimientos DLC (Diamond-Like Carbon)

### 8.2. Integración con Sistemas Inteligentes
- Sensores embebidos para monitoreo de condición
- Transmisiones autoajustables
- Diagnóstico predictivo basado en IA

### 8.3. Diseño Generativo
- Optimización topológica para reducción de peso
- Estructuras lattice para amortiguación
- Fabricación aditiva de componentes complejos

## Conclusiones

Los elementos de transmisión constituyen el nexo crítico entre los sistemas de actuación y las cargas mecánicas en aplicaciones de control de movimiento. Un diseño óptimo requiere considerar múltiples factores dinámicos, térmicos y de eficiencia energética. Las modernas herramientas de simulación permiten validar los diseños antes de su implementación física, reduciendo costos y tiempos de desarrollo.

El futuro de las transmisiones mecánicas apunta hacia sistemas más inteligentes, integrados y eficientes, capaces de auto-monitorear su condición y adaptarse a cambios operativos en tiempo real.

## Referencias

1. Norton, R. L. (2020). *Diseño de Maquinaria*. McGraw-Hill.
2. Erdman, A. G. (2012). *Mecanismos: Diseño, Análisis y Síntesis*. Prentice Hall.
3. Datasheets fabricantes (THK, HIWIN, Gates, Apex Dynamics)
4. Documentación MathWorks Simscape Multibody (2023)
5. Artículos técnicos ASME Journal of Mechanical Design


