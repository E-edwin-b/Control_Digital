# CLASE 19/09/2024
# Análisis de frecuencia y diagramas de bode

## 1. Análisis en frecuencia
Para poder analizar sistemas dinamicos un metodo muy importante es por medio del comportamiento en la salida de acuerdo a los cambios de frecuencia en la entrada, este analisis se hacer implementando señales sinusoidales tales que permitan un comportamiento lineal.
al implementar estas señales se producen cambios que se pueden evidenciar como una salida con amplitud proporcional y frecuencia igual a la de entrada.
cabe destacar que la implementacion de las señales sinusoidales es porque se pueden representar en forma de fasores los cuales asumen una frecuencia constante.

  $$\frac{Mo<Φo(w)}{Mi<Φi(w)}=M<Φ(w)$$

Es importante saber como cambir la variable Z en terminos de frecuencia de la siguiente manera:

 $$z=e ^ Jwt$$
 
teniendo en cuenta la equivalencia de z en terminos de frecuencia podemos expresar una funcion de transferencia teniendo en cuenta una parte real y una parte imaginaria de la siguiente forma:

$$z=a+bi$$

## 2. Diagramas de Frecuencia
Teniendo en cuenta que a la funcion de transferencia se le puede separar la parte real e imaginaria tambien se pueden obtener de estas dos partes la magnitus y la fase, este analisis de magnitus y fase se puede realizar por medio un grafico y asi estudiar su comportamiento.
es importante destacar que estos graficos estaran regidos respecto a la fercuencia de forma lineal o logaritmica "Decibelios" y regidos respecto a la fase por medio de coordenadas porlares, estos se dividen de la siguiente manera:

* Diagramas de Bode

![image](https://github.com/user-attachments/assets/2d65bf68-5d5e-4f12-b3b8-c7ef4caf639f)

* Diagrama polar
  
![image](https://github.com/user-attachments/assets/303b2de8-9ff9-40fa-b0c1-67c5deaba266)

## 3. Analisis Frecuencial en tiempo discreto
Cuado hablamos de frecuencia es importante destacar que el analisis en tiempo discreto no se puede hacer por ende se debe implementar una aproximacion al tiempo continuo teniendo en cuenta que:

$$w=\frac{2}{T}\frac{z-1}{z+1}$$

cuando implementamos esta aproximacion cabe destscar que hacemos un análisis grafico del tiempo discreto en donde los polos y los ceros variarian en tanto en el plano z como en el plano W.

## 4. Diagramas de Bode
los podemos conocer como los graficos que se obtienen del resultado de cambios que ocurren en un sistema cuando su ganancia y angulo de desfase varian en funcion de cambios en la frecuencia de la señal de entrada.

cuentan con algunas caracteristcas generales como: 

* Presentan un escala logaritmica
* las unidades de decibelios no son una unidad fisica por lo tanto se usan como la interpolacion de ganancia teniendo en cuenta la siguiente formula:

$$Adb=20log10*A$$

* cuando aumenta o disminuye la ganancia siempre sera en 20dB/decada y en la fase siempre sera de 45°/decada.
  
* otro coportamiento a tener en cuenta es el de zíta en los zeros ya que en la ganancia cuando zíta tiende a 1.5 sera casi lineal pero cuando tiende a 0.1 sera asintotico, de igual manera en la fase ocurrira lo mismo.

  ![image](https://github.com/user-attachments/assets/307c3dd8-12c7-4503-93fd-061e4be53dd5)

* zíta en los polos actuara de la misma manera pero con un comportamiento inverso al anterior ya que la asintota tendera hacia el lado postivo del grafico viendo una reaccion inversamente proporcional.

![image](https://github.com/user-attachments/assets/fe77127d-62f5-4bb5-9748-2e0263699f81)

## 2. Definiciones
>🔑 *Diagrama Bode:* Herramienta gráfica utilizada para analizar el comportamiento en frecuencia de sistemas lineales e invariantes en el tiempo.
>
>🔑 *Frecuencia:* Número de repeticiones de un evento periódico en una unidad de tiempo.
>
>🔑 *Tiempo Discreto:* Marco temporal donde los eventos y señales están definidos en instantes separados. 
>

## 10. Conclusiones
Por medio de esta clase se pudo adquirir conocimientos para analisar los diagramas de Bode y de frecuencia los cuales son herramientas esenciales para comprender cómo varía la ganancia y el desfase de un sistema en función de la frecuencia cabe destcar que estas representaciones permiten evaluar la estabilidad y el desempeño de un sistema, especialmente en el diseño y ajuste de controladores.
## 11. Referencias
* JORGE EDUARDO COTE BALLESTEROS (19 sep 2024). E.P.1.Control digital. Análisis de frecuencia y diagramas de bode. universidad ECCI



