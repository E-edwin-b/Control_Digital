# CLASE 13/03/2025
# Simscape multibody

La herramienta Simscape Multibody es una herramienta que hace parte de matlab que permite el desarrollo y la simulacion de sistemas mecanicos en 3D. Simscape Multibody permite hacer analisis a profundidad de la dinamica de los cuerpos rigidos, articulaciones y mecanismos mas complejos.
para comprender a profundidad las herramientas de Simscape Multibody se debe conocer sus princcipales funciones, como lo son la creacion de solidos, la simulacion de mecanismos, las articulaciones, rotacionales y prismaticas, entre otros.

## 1. Aspectos generales, Simscape Multibody.
un aspecto fundamental para la creación de un nuevo archivo de Simscape Multibody es tener en cuenta que en lugar de crear un archivo en simscape en blanco, podemos implementar el comando Smnew el cual nos creara un nuevo archivo simulink con las herramientas fundamentales para modelar sistemas multibody, con esta herramienta podremos crear solidos, tambien definir los sistemas de coordenadas, como tambien simular su movimiento y dinamica.

![image](https://github.com/user-attachments/assets/89aa13ee-0fff-4af3-80dc-8ba54f1952b1)
**Imagen 1: Archivo nuevo Simscape Multibody**


## 2. Creación de Sólidos
Partiendo del conocimiento que un solido es un cuerpo rigido que se define por su geometria y propiedades, compredidas por su masa, inercia, etc.

podemos usar un solido para representar componenetes mecanicos para un modelo, ese solido cuenta con unas caracteristicas especificas que se comprenden de la siguiente manera.

### 2.1 Configuración de geometría

El bloque comprendido por el solido cuenta con un amplia variedad de coonfiguraciones, tanto en tamaño, como en forma, en la imagen 2 podemos observar un ejemplo practico donde modificamos los valores de ancho, alto y profundidad en los ejes correspondientes de (x, y, z).

![image](https://github.com/user-attachments/assets/e9cc26ff-6b91-4e43-be9d-0552acefa3f1)

**Imagen 2: Configuraciones Solido**

### 2.2 propiedas gráficas del solido
Junto con la geometria, otro parametro que se puede ajustar al solid solo sus prametros graficos, como su color (en formato RGB), la trasparencia y opacidad para tener una mejor visualización del solido en el plano.

![image](https://github.com/user-attachments/assets/7245af50-0d6b-480a-8c65-da7a86ea26ab)

**Imagen 3: Configuraciones graficas del Solido**


### 2.3 Definicion y configuración de los frames

teniendo en cuenta que un frame es ese punto de refrencia en el que el solido establece sus articulaciones, juntas, o conexiones con otros componentes. Podemos realizar un ajuste segun la geometria del solido para asi poder agregar frames adicionales para unir con otros solidos, o articulaciones nuestro solido.

![image](https://github.com/user-attachments/assets/87c9c0c1-3a06-4a7c-be08-0798c69a8361)


**Imagen 4: Configuraciones frames del solido**

##  3. Articulaciones y Mecanismos

En el area de trabajo de Simscape Multibody contamos con articulaciones que son las que nos permiten el movimiento de nuestros solidos con respecto a un eje de refrencia lo cual en aspecto generales permite simular y analizar la dinamica de los solidos o mecanismos.

### 3.1 Articulación Rotacional (Revolute Joint)

La articulacion rotacional es aquella que permite la rotacion de un solido con respecto a un eje coordenado especifico, para la articulacion rotacional el eje z, esta articulacion tiene dos entradas en donde se pueden agregar 2 solidos para evidenciar de manera grafica ese movimiento rotacional.

como aspecto importante en nuestro archivo de Simscape Multibody el eje vertical por defecto es z, el eje horizontal es x y el tercer eje, de profundidad esta definido por Y, para tener un eje de referencia más comun, en nuestro bloque de configuracion del mecanismo, desplazamos la gravedad del eje z al eje ya para que nuetro eje vertical este establecido en y. Ahora esto facilita la visualización correcta del movimiento de los sólidos.

![image](https://github.com/user-attachments/assets/d1344c0d-3c46-43f5-977d-194af8edde25)

**Imagen 5: Union eslabones con articulación rotacional**


### 3.2 Articulación prismatica (Prismatic Joint)

La articulación prismatica es aquella que permite un movimiento en un solo eje, especificamente en el eje Z, cuenta con caracteristicas mas especificas como implementar actuadores que apliquen una fuerza o una posicion lineal de forma automatica y tambien con sensores que permiten monitoreas el comportamiento del solido en un Scope.

de igual manera que en el caso anterior con la articulación rotacional debemos intercambiar los ejes de nuestro solido asi como de nuestra articulacion prismatica ya que si por ejemplo queremos una rotacion en el eje horizontal que es y, no funcionara debido a que la ariculacion prismatica, solo hace el desplazamiento en el eje z, entonces intercambiamos los ejes para poder realizr el movimiento de manera correcta.

![image](https://github.com/user-attachments/assets/7c9a8fe8-7835-4b48-90e5-4372faf4cb88)

**Imagen 6: Union eslabon con articulación prismatica**

##  4. Definiciones
>🔑 Frame: Punto de referencia en un sólido donde se establecen articulaciones o conexiones con otros componentes.
Por defecto, el frame se ubica en el centro del sólido, pero puede ocultarse o añadirse nuevos frames en cualquier área del sólido según sus características geométricas.
>
>🔑 Articulación Rotacional (Revolute Joint): Permite la rotación de un sólido respecto a un eje específico, en este caso, el eje Z.
>
>🔑 Transformación Rígida: Bloque que permite trasladar o rotar los ejes de coordenadas de un sólido para evitar que se superpongan en un mismo punto.
>
>🔑 Articulación Prismática (Prismatic Joint): Restringe el movimiento de un sólido a lo largo de un solo eje (por defecto, el eje Z).
>
>🔑 Sólido: Un cuerpo rígido definido por su geometría, masa y propiedades inerciales, utilizado para representar componentes mecánicos en un modelo.
>

## 4. Ejercicios

## 5. Conclusiones

* Es importante reconocer la importancia del control cascada cuando se busca mejorar la estabilidad, así como la respuesta del sistema frente a las perturbaciones que se buscan reducir con el mismo.
* realizar correctamente la sintonización de los controladores es indispensable para obtener un rendimiento optimo independientemente de los métodos empleados bien sean empíricos o por medio de técnicas computacionales.
* a la hora de elegir un método de sintonización dependerá de las características con las cuente el sistema, así como también de las pruebas que se le puedan realizar al mismo lo que también permite tener una amplia variedad de pruebas, tanto en lazo abierto, como en lazo cerrado.
* aplicar el control cascada es eficaz cuando la variable secundaria de un sistema es más rápida que la primaria, por ende, habrá perturbaciones que afectaran el tiempo de establecimiento del sistema y allí es cuando se buscara mejorar es tiempo de establecimiento o cuando se quiere mejorar la dinámica del sistema.

## 6. Referencias
* J. E. Cote Ballesteros, E.P.2. Control movimiento. Control cascada, Universidad ECCI, 2025.
* C. Smith and A. Corripio, Principles and Practice of Automatic Process Control, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2005.






