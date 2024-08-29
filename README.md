# Transformada Z de adelantos y atrasos 
Metodo matemático por medio del cual se puede realizar el analisis y diseño de sistemas discretos en el tiempo, es importante destacar que este metodo es fundamental para dicho analisis ya que permite transformar señales y sistemas discretps en el dominio del tiempo al dominio complejo "Z", implementar este metodo es fundamental para analisar la respuesta de un sistema cuando las entradas son desplazadas en el tiempo.
## 1. Representación matemática de los sistemas
### 1.1. Ecuación en diferencias.
la ecuación en diferencias es la relación matemática que permite evidenciar el cambio de una señal discreta de un punto a otro, es importante tener en cuenta que la dinamica del sistema se representa teniendo en cuenta las muestras de las señales.

$b_{n}u\left( k \right)+b_{n-1}u\left( k-1 \right)=y\left( k \right)+a_{n-1}y\left( k-1 \right)$

### 1.2 Características ecuaciones en diferencias.
las ecuaciones en diferencias cuentan con unas caracteristicas que permiten clasificarlas de la siguiente manera:

* lineal, invariante en el tiempo, no homogénea
* homogeneas, lineales, invariantes en el tiempo
* Lineal, variante en el tiempo, homogénea
* No lineal, invariante en el tiempo, homogénea

### 1.3 Solución por métodos iterativos.
💡**Ejemplo 1:**
$y\left( k \right)=\frac{1}{3}\left( -2y\left( k-1 \right)+y\left( k-2 \right)
+2u\left( k-1 \right)-3u\left( k-2 \right)\right)$

$y\left( -2 \right)=1;y\left( -1 \right)=-2;u\left( k \right)$

$k=0$

$y\left( 0 \right)=\frac{1}{3}\left( -2\left( -2 \right)+1+2\left( 0 \right) -3\left( 0 \right)\right)=\frac{5}{3}$

## 2. Transformada Z
la transformada z es la parte opuesta de LaPlace por lo tanto contamos con caracteristicas diferentes, es importante destacar que es por medio de las transformada z que podemos obtener una expresion matematica para obtener una ecuacion para cuaquier muestra.

### transformada de LaPlace
$\mathcal{L}\{ f(t) \} = \int_{0}^{\infty} f(t) e^{-st} \ dt$

### transformada Z

$\mathcal{z}\{ f(k) \} = \sum_{k=0}^{\infty} f(k)z^{-k} \ $



### 2.3 Ecuaciones en diferencias por transformadas Z.
para las ecucaciones diferenciales por la transformada z se debe tener en cuenta que es un procedimiento similar al anterior visto de ecuaciones en diferencias, se debe aplicar transformada z a la ecuacion, luego despejar la variable desconocida y aplicar la trasformada z inversa.

## 3. Función de transferencia discreta 
### 3.1 Funciones de transferencia en el dominio Z
### 3.2 Función de transferencia a pulso.
### 3.3 Función de transferencia para dos sistemas en cascada.
### 3.4 Función de transferencia en lazo cerrado
### 3.5 Pasar una función de transferencia en atraso a adelanto.
### 3.6 Tiempo muerto en sistemas discretos

## 2. Definiciones
>🔑 *Muestreo:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Periodo:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Dinamica:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Discreto:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
>
>🔑 *Pulso:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.

## 3. Subsecciones
Las subsecciones pueden utilizarse para sub dividir ciertos temas que se tienen en clases, por ejemplo si se está trabajandolos conversores D/A, puede ser necesario subdividir este en circuito de resistencias ponderadas y circuito de escalera R2R. 
### 3.1. Título de subsecciones
Para la creación de estas subsecciones debe utilizar un tamaño de letra más pequeño, por lo tanto utilice la etiqueta '###' 
### 3.2. Numeración de subsecciones
Siga la numeración de la sección seguida de un punto y luego el número de la subsección.

## 4. Ejemplos
Si en algún caso pretende dar un ejemplo explicativo ya sea a través de texto o através de ecuaciones matemáticos, utilizar la palabra 'Ejemplo' seguido de una numeración consecutiva dentro de la clase. Utilice el emoji 💡 antecediendo la palabra.

## 5. Ecuaciones
Para la edición de ecuaciones debe utilizar la etiqueta '$$' al comienzo y final de la ecuación para que la ecuación quede centrada ocupando una línea. Si se quiere que la ecuación quede integrada en el texto debe utilizar la etiqueta '$' al comienzo y final de la ecuación. Las ecuaciones pueden ser editadas utilizando el código LATEX, en el siguiente enlace encuentran un editor de ecuaciones que les genera el código. http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp . Sin embargo hay muchas otras herramientas que pueden utilizar para esto.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,


$$R=\frac{V}{I}$$

## 6. Figuras
Todas las figuras que incluya deben ser generadas por ustedes, **no utilizar las figuras de las presentaciones**. Para incluir figuras puede seguir los siguientes pasos:
* Primero escribimos ![]().
* Después escribimos, dentro de los corchetes, el texto alternativo. Este es opcional y solo entra en acción cuando no se puede cargar la imagen correctamente.
* Después escribimos, dentro de los paréntesis, la ubicación del archivo (ya sea una url o una ubicación dentro de algun folder local). Se recomienda poner las imágenes en una carpeta que se llame imágenes dentro del repositorio github para que no tengan problemas al cargar las imágenes.

💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.png)

Figura 1. Figura de prueba

Incluya la respectiva etiqueta a modo de descripción de la figura y mantenga numeración consecutiva para todas las figuras de la clase.

## 7. Tablas
En caso de necesitar la inclusión de tablas para organizar información se recomienda el uso de la herramienta del siguiente enlace https://www.tablesgenerator.com/markdown_tables , la cual permite organizar la información dentro de la tabla y genera el código markdown automáticamente:

💡**Ejemplo 3:** 

| **Resultado** | **x = número de intentos hasta primer éxito** |
|---------------|-----------------------------------------------|
|       S       |                       1                       |
|       FS      |                       2                       |
|      FFS      |                       3                       |
|      ...      |                      ...                      |
|    FFFFFFS    |                       7                       |
|      ...      |                      ...                      |

Tabla 1. Tabla de ejemplo

Cada tabla debe llevar la etiqueta que describa su contenido y numeración consecutiva para todas las tablas

## 8. Código
Teniendo en cuenta que el curso requiere del desarrollo de código matlab, c, c++ u otro. Si requiere incluir pequeños segmentos de código en los apuntes hágalos de la siguiente manera:

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
