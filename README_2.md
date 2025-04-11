# CLASE 13/03/2025
# Simscape multibody

La herramienta Simscape Multibody es una herramienta que hace parte de matlab que permite el desarrollo y la simulación de sistemas mecánicos en 3D. Simscape Multibody permite hacer análisis a profundidad de la dinámica de los cuerpos rígidos, articulaciones y mecanismos más complejos.
para comprender a profundidad las herramientas de Simscape Multibody se debe conocer sus principales funciones, como lo son la creación de sólidos, la simulación de mecanismos, las articulaciones, rotacionales y prismáticas, entre otros.

## 1. Aspectos generales, Simscape Multibody.
un aspecto fundamental para la creación de un nuevo archivo de Simscape Multibody es tener en cuenta que en lugar de crear un archivo en simscape en blanco, podemos implementar el comando Smnew el cual nos creara un nuevo archivo simulink con las herramientas fundamentales para modelar sistemas multibody, con esta herramienta podremos crear sólidos, también definir los sistemas de coordenadas, como también simular su movimiento y dinámica.

<div align="center">
<img src="https://github.com/user-attachments/assets/89aa13ee-0fff-4af3-80dc-8ba54f1952b1" width="70%" >
<p><strong>Imagen 1: Archivo nuevo Simscape Multibody</strong></p>
</div>

## 2. Creación de Sólidos
Partiendo del conocimiento que un sólido es un cuerpo rígido que se define por su geometría y propiedades, comprendidas por su masa, inercia, etc.

podemos usar un sólido para representar componentes mecánicos para un modelo, ese solido cuenta con unas características específicas que se comprenden de la siguiente manera.

### 2.1 Configuración de geometría

El bloque comprendido por el sólido cuenta con una amplia variedad de configuraciones, tanto en tamaño, como en forma, en la imagen 2 podemos observar un ejemplo práctico donde modificamos los valores de ancho, alto y profundidad en los ejes correspondientes de (x, y, z).

<div align="center">
<img src="https://github.com/user-attachments/assets/e9cc26ff-6b91-4e43-be9d-0552acefa3f1" width="50%" >
<p><strong>Imagen 2: Configuraciones Solido</strong></p>
</div>

### 2.2 propiedades gráficas del solido
Junto con la geometría, otro parámetro que se puede ajustar al solido solo sus parámetros gráficos, como su color (en formato RGB), la trasparencia y opacidad para tener una mejor visualización del solido en el plano.

<div align="center">
<img src="https://github.com/user-attachments/assets/7245af50-0d6b-480a-8c65-da7a86ea26ab" width="50%" >
<p><strong>Imagen 3: Configuraciones graficas del Solido</strong></p>
</div>

### 2.3 Definición y configuración de los frames

teniendo en cuenta que un frame es ese punto de referencia en el que el sólido establece sus articulaciones, juntas, o conexiones con otros componentes. Podemos realizar un ajuste según la geometría del solido para así poder agregar frames adicionales para unir con otros sólidos, o articulaciones nuestro sólido.

<div align="center">
<img src="https://github.com/user-attachments/assets/87c9c0c1-3a06-4a7c-be08-0798c69a8361" width="50%" >
<p><strong>Imagen 4: Configuraciones frames del solido</strong></p>
</div>

##  3. Articulaciones y Mecanismos

En el área de trabajo de Simscape Multibody contamos con articulaciones que son las que nos permiten el movimiento de nuestros solidos con respecto a un eje de referencia lo cual en aspecto generales permite simular y analizar la dinámica de los sólidos o mecanismos.

### 3.1 Articulación Rotacional (Revolute Joint)

La articulación rotacional es aquella que permite la rotación de un sólido con respecto a un eje coordenado especifico, para la articulación rotacional el eje z, esta articulación tiene dos entradas en donde se pueden agregar 2 solidos para evidenciar de manera grafica ese movimiento rotacional.

como aspecto importante en nuestro archivo de Simscape Multibody el eje vertical por defecto es z, el eje horizontal es x y el tercer eje, de profundidad está definido por Y, para tener un eje de referencia más común, en nuestro bloque de configuración del mecanismo, desplazamos la gravedad del eje z al eje ya para que nuestro eje vertical este establecido en y. Ahora esto facilita la visualización correcta del movimiento de los sólidos.

<div align="center">
<img src="https://github.com/user-attachments/assets/d1344c0d-3c46-43f5-977d-194af8edde25" width="50%" >
<p><strong>Imagen 5: Union eslabones con articulación rotacional</p>
</div>

### 3.2 Articulación prismática (Prismatic Joint)

La articulación prismática es aquella que permite un movimiento en un solo eje, específicamente en el eje Z, cuenta con características más específicas como implementar actuadores que apliquen una fuerza o una posición lineal de forma automática y también con sensores que permiten monitoreas el comportamiento del solido en un Scope.

de igual manera que en el caso anterior con la articulación rotacional debemos intercambiar los ejes de nuestro sólido, así como de nuestra articulación prismática ya que, si por ejemplo queremos una rotación en el eje horizontal que es y, no funcionara debido a que la articulación prismática, solo hace el desplazamiento en el eje z, entonces intercambiamos los ejes para poder realizar el movimiento de manera correcta.

<div align="center">
<img src="https://github.com/user-attachments/assets/7c9a8fe8-7835-4b48-90e5-4372faf4cb88" width="50%" >
<p><strong>Imagen 6: Union eslabón con articulación prismática</p>
</div>

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

📚 Ejercicio 1: 

para este ejercicio tomamos 3 solidos en donde configuramos sus propiedades para que el primer solido sea más corto, el segundo solido un poco más largo y el tercer eslabón sea el más largo, definimos los frases del primer eslabón en uno de sus extremos laterales, luego el segundo eslabón se une por sus dos extremos de sus esquinas laterales y por último el tercer eslabón se une en uno de sus extremos laterales, implementamos las articulaciones rotacionales en cada uno de los eslabones y colocamos una trasformación rígida en el tercer eslabón para que no se unan los eslabones en el mismo punto, a continuación en la imagen 7 podemos observar el diseño de nuestro mecanismo.

<div align="center">
<img src="https://github.com/user-attachments/assets/6364a3e3-37d9-43a2-8407-18534041daec" width="50%" >
<p><strong>Imagen 7: Ejercicio 1 diseño mecanismo manivela balancín</p>
</div>


<div align="center">
  <img src="https://github.com/user-attachments/assets/664aba2e-b2de-443d-90d6-fe8c81038b10">
  <p><strong>Imagen 8: Ejercicio 1 Simulación mecanismo</p>
</div>


📚 Ejercicio 2: 

para este ejercicio tomamos 1 solido en donde configuramos sus propiedades para que sea esférico, con unas medidas de diámetro de 1cm, definimos solo un frame de la esfera en su centro, implementamos una articulación prismática recordando que su desplazamiento lo hace en el eje z usamos una transformación rígida para que se desplace en el eje y orientado verticalmente a continuación en la imagen 7 podemos observar el diseño de nuestro mecanismo.

<div align="center">
<img src="https://github.com/user-attachments/assets/8b4bcb5d-1298-4508-a288-9daa5813ed35" width="50%" >
<p><strong>Imagen 7: Ejercicio 2 diseño solido con traslación prismática</p>
</div>


<div align="center">
  <img src="https://github.com/user-attachments/assets/526310b2-8dcc-41c8-ab3f-ca4bcdee27aa">
  <p><strong>Imagen 8: Ejercicio 2 Simulación mecanismo</p>
</div>

## 5. Conclusiones
* Es importante tener en cuenta la precisión a la hora de definir los frames que harán parte de los elementos solidos que se vayan a usar, así como también otros aspectos como la geometría y los sistemas de coordenadas. ya que por medio de estos evitaremos errores inesperados en la simulación como articulaciones bloqueadas o solidos sobre puestos.
* cuando contamos con la gravedad del eje vertical por defecto "Eje z", es importante cambiarla el vertical a el "Eje y" para tener una interpretación que permita ver de una manera practica el movimiento en las simulaciones para mecanismo planares.
* un aspecto fundamental en la simulación de mecanismos por medio de Simscape multibody, es la capacidad de aplicar entradas, así como también medir variables "posición, velocidad, etc." ya que permite analizar a profundidad la dinámica de un sistema y por medio de pruebas concluir los funcionamientos de los mecanismos.
## 6. Referencias
* J. E. Cote Ballesteros, E.P.2. Control movimiento. Control cascado, Universidad ECCI, 2025.
* C. Smith and A. Corripio, Principles and Practice of Automatic Process Control, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2005.
* Mathworks.com. [En línea]. Disponible en: https://la.mathworks.com/help/sm/index.html. [Consultado: 11-abr-2025].







