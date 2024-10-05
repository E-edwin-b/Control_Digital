# CLASE 12/09/2024
# Metodos Algebraicos
Metodos que nos ayudan a encontrar la funcion de transferencia de controlodares que satisfagan tanto las condicones de estabilidad como los parametros que hacen parte de la funcion de cualquier sistema.
## 1. Igualación de modelo
En igualación de modelo lo que tenemos es la funcion de transferencia del sistema y una funcion de transferencia qeu cuenta con las carecteristicas que deseamos que tenga nuestro sistema, por lo tanto lo que debemos hacer es encontrar un controlador el cual modifique las caracteristicas del sistema que tenemos.
Esto se logra de la siguiente manera:

  $$G(z)=\frac{n(z)}{d(z)}$$
  
  $$G0(z)=\frac{n(0)}{d(0)}$$
  
En donde G(z) es la funcion de tranferencia de nuestro sistema y G0(z) es la funcion a la que queremos llegar, por lo tanto debemos encontrar el controlador G(z) que se calcula con la siguiente formula:

  $$C(z)=\frac{G0(z)}{G(z)*(1-G0(z))}$$

Este controlador se implementa colocandolo antes del sistema en lazo cerrado.  

## 2. Igualación de coeficientes
Similar el metodo de igualación de modelo, busca encontrar un controlador por medio de despeje algebraico, pero en este caso en lugar de tener en cuenta toda una funcón solo se tienen en cuenta los polos del sistema es decir el denominador.
Por lo tanto lo que se hace es multiplicar el sistema con un controlador en lazo cerrado cuyas componentes son incognitas que debemos encontrar para que el sistema tenga los polos que se desean.
### 2.1 Consideraciones del controlador con incognitas
El nivel del polinomio en el denominador de nuestro controlador sera igual a el nivel del polinomio en el denominador de nuestro sistema menos uno

💡Ejemplo 1:
si nuestro sistema en el denominador tiene un polinomio de segundo orden ($s^2+s+1$) y el sistema al que queremos llegar es de orden 5 ($s^5+s^4+s^3+s^2+s+1$), entonces nuestro controlador debe tener un denominador de orden 3 ($s^3+s^2+s^1+s+1$) para que nuetro sistema llegue al orden 5 que es el deseado.



Recordando la ley de las ecuaciones la cual nos dice, que para que un sistema de ecuaciones se solucione este debe tener la misma cantidad de incognitas como de ecuaciones, siguiendo esta norma si nuestro polinomio deseado es de orden 5 esto quiere decir que tenemos 5 ecuaciones, para que estas se saisfagan debemos tener 5 incognitas, como ya tenemos 3 debido a la regla anterior debemos añadir dos mas en el numerador para cumplir esta norma:

💡Ejemplo 2:
si sabemos que nuestro sistema tiene la siguiente funcion de transferencia:

$$\frac{1}{s^3+s+1}$$

y si nuestro polinomio desdeado:

$$s^5+s^4+s^3+s^2+s+1$$

por lo tanto la funcion con incognitas de nuestro controlador sera:

$$\frac{b1s+b0s}{A1s^2+A0s}$$

## 2. Definiciones
>🔑 *Controlador:* dispositivo o algoritmo utilizado para regular el comportamiento de un sistema, ajustando sus salidas con el fin de alcanzar un estado deseado o seguir una referencia.
>
>🔑 *Coeficientes:* Números o factores constantes que multiplican variables o términos en ecuaciones algebraicas.
>
## 9. Ejercicios

Considere los siguientes sistemas:

### 📚ejercicio 1: 

$$G(z)=\frac{9}{s^2 + 2s + 3}$$

$$G0(z)=\frac{1}{20 s^2 + 2s + 1}$$

En donde por el metodo de igualacion de modelo, tenemos el sistema G(z), el cual queremos que tenga las caracteristicas del  sistema G0(z)
,por lo tanto aplicamos la ecuacion


$$C(z)=\frac{G0}{G(1-G0)}$$

La cual reemplazada nos da:

$$C(z)=\frac{\frac{1}{20 s^2 + 2s + 1}}{\frac{9}{s^2 + 2s + 3}(1-\frac{1}{20 s^2 + 2s + 1})}$$

Y resuelta nos da:

$$C(z)=\frac{20 s^4 + 42 s^3 + 65 s^2 + 8s + 3}{3600 s^4 + 720 s^3 + 216 s^2 + 18s}$$

### 📚ejercicio 2: 

tomando como referencia el ejercicio anterio, digamos que queremos que otro sistema llegue al mismo resultado, por lo tanto sabiendo que:

$$G(z)=\frac{5000}{s + 50.5}$$

$$G0(z)=\frac{1}{20 s^2 + 2s + 1}$$

entonces:

$$C(z)=\frac{\frac{1}{20 s^2 + 2s + 1}}{\frac{5000}{s + 50.5}*(1-\frac{1}{20 s^2 + 2s + 1})}$$

Y resuelto nos da:

$$C(z)=\frac{20 s^3 + 1012 s^2 + 102 s + 50.5}{  2e06 s^4 + 400000 s^3 + 120000 s^2 + 10000s}$$


 

## 10. Conclusiones
Por medio de esta clase se pudo adquirir conocimientos para el desarrolo y diseño de controladores para sistemas dinamicos que varian en funcion del tiempo, esto se obtiene por medio de los metodos algebraicos ya que es gracias a estos metodos que podemos encontrar controladores que modifiquen las caracteristicas de un sistema para satisfacer condiciones de estabilidad como parametros más especificos. 

10. Referencia
## 11. Referencias
* JORGE EDUARDO COTE BALLESTEROS (26 sep 2024). E.P.1.Control digital. Diseño redes de atraso en frecuencia. universidad ECCI


