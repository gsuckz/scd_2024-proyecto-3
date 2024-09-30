# Sistemas de Comunicaciones Digitales - Proyecto 3
#### Autor: Jesus Avila 

## Resumen

## Introduccion

A través de una definicion primitiva de cuantizacion,  error cuadrático medio y entroía de una fuente analógica, se busca exponer el problema de elegir los intervalos de cuantización, usando el $E_{rms}$ y la entropía de la fuente como criterios. Se propone una solucion usando cuantizaciones uniformes.


---

### Fuente Analogica
Una fuente analógica es un proceso, el cual entrega valores que para ser descritos, requieren un conjunto infinito *continuo*. En el contexto de teoría de la informacion se usa una descripcion  a través de un modelo probabilístico, ya que uno no sabe que es lo que va a mandar *"exactamente"*, sin embargo, si sabe *"Qué podemos esperar"*. Ejemplos de fuentes analógicas: Temperatura de un objeto, la duración de un fenómeno, o la rápidez de un vehículo.



#### Fuentes Vectoriales
Existen fuentes, tambien analógicas, en el sentido de que los valores que pueden tomar forman un *continuo* pero, este valor no se puede describir con un solo número, sino que es necesario un conjunto finito de numeros reales. Por ejemplo una velocidad, o el campo eléctrico. 

### Cuantizacion
Si se quiere *transmitir cualquier valor analógico* a través de un medio digital, es claro que estaríamos ante un problema. Esto es debido a que no podemos encontrar una representación unívoca del continuo a través de conjuntos contables. Esta verdad, se puede probar de manera matemática<sup>1</sup>, sin embargo intuitivamente podemos explorar algunas nociones:
* Un numero Real tiene *infinitas* cifras.

 Si quisieramos representarlos por medio de simbolos, necesitaríamos *infinitos* para *cada* numero. Esto obviamente no es posible en ningún canal. 
* La probabilidad de recibir un número real es 0. 

Esto significa que no podemos *esperar* un numero real determinado, mas bien podemos hablar de la probabilidad de que el valor recibido *pertenezca a un intervalo*. Vale la pena *intentar* calcular la cantidad de informacion que podría enviarse, si pudieramos recuperar *exactamente* el numero real $x$. $$I(x)= -\log(Pr(x)) = -\log(0) = \infty$$ 
    Este resultado nos confirma que necesitaríamos infinitos digitos para *especificar* un numero *real entre todos*

* Si dividimos un intervalo $A$ en $N$ sub-intervalos *disjuntos* (de ahora en adelante se entiende que es la forma de dividir los intervalos) $A_n$ , la probabilidad de cualquiera estos será menor que la del primero, y $\sum_{n}^{N} Pr(A_n) = Pr(A)$.

 Podemos entonces dividir el intervalo (Que puede ser ifninito) que contiene todos los valores posibles de la Fuente, en $n$ sub-intervalos, cada uno con una cierta probabilidad, de forma que $\sum_{n}^{N} Pr(A_n) = 1$. Y describir nuestra fuente analógica a traves de una pmf, y como $N$ es un numero *entero*, podemos usar $N$ símbolos para los intervalos. 
 
De esta forma podemos intentar hacer una descripción *discreta* de nuestra fuetne analógica. Este proceso llamaremos *cuantizacion*. Si este proceso es realizado sobre una variable analógica vectorial, hablaremos de *cuantización vectorial*

Llamaremos *cuantizacion*  o *cuantizador* a una funcion $Q$:
$$Q(x) = y_n, \space si \space x \in X_n $$
Siendo $X_n$ los intervalos de dividir el $Dom(f)$

#### Entropia de la salida

Cuando describimos nuestra salida como una fuente discreta. Podemos calcular su entropía. Obviamente esto dependerá de la pdf de la fuente analógica, y (mas importante para nosotros) y de los intervalos en los que dividimos el rango de la fuente analogica, no solamente de la cantidad. 
* Si dividimos un intervalo $A_j$ en $R$ intervalos $A_{jr}$, pasando el numero de intervalos total $N$ a $N´$ la Entropía $E$ aumenta.

Recordemos la definicionde entropía:


$$E = -\sum_n^{N´} Pr(A_n)\log Pr(A_n) $$

Ademas:
$$ Pr(A_j) >  Pr(A_{jr}) $$
$$ -\log Pr(A_j) < -\log   Pr(A_{jr}) $$
Y aun mas:
$$ -\log Pr(A_j) < \sum_r^R - Pr(A_jr)\log   Pr(A_{jr}) $$

Como los intervalos $A_{jr}$ son conjuntos del total, podemos ver que aumentan las entroía de la fuente, esto es lógico ya que se agregas mas "opciones" cada una con menos probabilidad (mayor informacion).
De esto podemos intuir, que la entropía de la fuente discreta obtenida, aumenta con el número de sucesivas divisiones realizadas, no necesariamente el numero de intervalos tomados. Es posible demostrar que no existe un límite para este valor.
Es interesante señalar, que disponer de mas intervalos siempre aumenta la cantidad de información que podemos esperar recibir(aumenta el uso del canal). 

No es cierto, en general, que dividir un intervalo mas probable aumente menos la entropía que dividir uno menos probable. Ya que podemos hacer este crecimiento arbitrariametne grande tomando algun sub-intervalo lo suficientemente pequeño.

Supongamos, sin embargo que dividimos 2 sub-intervalos $A$ y $B$, de forma tal que para cualquier $A_j$ o $B_j$ la probabilidad sea un valor $P$. Tal número P no es arbitrario, ya que debe satisfacer el hecho de que $P * N_a  = Pr(A)$, con $N_a$ entero, lo mismo para $B$, de acá se deduce que $Pr(A)/Pr(B)$ debe ser un numero *racional*. Lo que si es cierto es que se puede tomar un valor arbitrariamente chico. Además si consideramos que la densidad de probabilidad es no-nula esta división será única. Para esto podemos pensar en que desde el comienzo del intervalo la probabilidad será creciente a medida que movemos el extremo final del sub-intervalo, una vez que alcancemos el valor P, este sub-intervalo será el único posible (Que empiece donde el grande y tenga probabilidad P). Podemos repetir este proceso hasta completar todo el intervalo original.

Sabiendo que $Pr(A) < Pr(B) \Rightarrow N_a < N_b$ 

Al reemplazar un intervalo $X$, la entropía aumenta en:
$$\Delta E = -\sum_n^N Pr(X_n) \log Pr(X_n) +Pr(X) \log Pr(X)  $$

Al reemplazar A:
$$\Delta E = -\sum_n^N Pr(A_n) \log Pr(A_n) + Pr(A) \log Pr(A) = -P\sum_n^N \log P +Pr(A)\log Pr(A)  $$
$$\Delta E_ =  -N_a*P* \log P +Pr(A)\log Pr(A)  $$
Luego para B

$$\Delta E_ =  -N_b*P* \log P +Pr(B)\log Pr(B)  $$



No es claro cual $\Delta E$ sera mayor, pero si pensamos el procesor inverso de dividir, es decir unificar. Podemos decir que si unificamos los sub-intervalos de alguno de los 2 conjuntos, esto es,
si unimos varios intervalos de probabilidad $P$, disminuimos mas la entropía al unir mas de ellos (es decir al recomponer el intervalo mas probable).

Es decir, aumenta mas la entropía al dividir el intervalo que mayor entropía aumentaba, si las divisiones son igualmente probables. (Se puede probar con una cota minima?). Dicho de otra forma,si con estas condiciones,  queremos tomar mas intervalos, si estos pertencen a "zonas mas probables" aumentaremos menos la entropía.


Conociendo el teorema de codificacion de fuente<sup>2</sup> nos va a interesar no hacer demasiada grande la entropía de la fuente discreta resultante, con el objetivo de no aumentar demasiado la longitud de palabra esperada de un código óptimo.

### Error cuadratico medio
En general, si la lo que se transmite es una magnitud física, nos va a interesar que los valores obtenidos al recuperar la señal (representantes del intervalo) sean lo mas parecidos a los originales. Es decir minimizar la diferencia. Claramente la diferencia entre un valor del intervalo y su representante es menor, cuanto mas chico el intervalo. Esta es la razón por la que queremos aumentar el número de intervalos. Un $E_{rms}$ arbitrariamente chico, conduce a entropías arbitrariamente grandes. Sin embargo no es lo único a señalar.

El error cuadrático medio de la cuantizacion se define:
$$ E_{rms} =  \int_{-\infty}^\infty f(x) (x - Q(x))^2dx$$
Donde $Q :Q(x)$ es una cuantizacion.

#### Como elegir representantes de los intervalos
Demostrado en [3] se puede ver que el representante de un intervalo debe ser el valor esperado del intervalo.


### Minimizacion del error cuadratico medio para una dada entropia

Intuitivamente  interesará dividir los intervalos mas probables. Esto hará que el $Erms$ decrezca mas rápido ya que:
* Los intervalos mas probables intervienen mas en el error esperado, ya que habrá menos diferencia en los valores mas esperados.
* Aunque dependerá de nuestra forma de dividir, podríamos esperar aumentar menos la entropía de esta forma

Sin embargo, es de gran interés desarrollar un criterio para determinar estos intervalos, dados un error cuadrático medio deseado y una pdf  $f(x)$.

 Si seguimos nuestra primera intuicion podemos pensar que las funciones que tengan ciertos intervalos muy probables (o equivalentemente, intervalos muy improbables) nos van a permitir *cuantizarlas* con menos entropía. Esto es porque los valores de la fuetne discreta estarán mas *concentrados* en la medida que los de la fuente analogica lo esten. 

 #### Entropia diferencial

 Procedemos a generalizar esta idea de orden o cantidad de informacion esperada (Entropía) a una fuente Analógica.

 $$ E = -\int_{-\infty}^\infty f(x) \log f(x) dx $$


### Referencias
[1] 

[2] Gallager, R. G. (1968). Information theory and reliable communication (pp. 59-75). Wiley.

[3] Gallager, R. G. (1968). Information theory and reliable communication (p. 69). Wiley.
