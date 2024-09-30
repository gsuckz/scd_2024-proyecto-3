## Introduccion
En esta monografia se pretende desarrollar bajo ciertas definiciones, el concepto d

### Fuente Analogica

* Una fuente analogica es una secuencia de variables aleatorias $U_1,\space U_3, \space ... \space :U_n \in D \subset \real$, donde $D$ es un conjunto infinito continuo .(Esto es lo que Gallager llama "Valores Analogicos") 


Al ser un proceso estocastico. La fuente puede describirse usando una *"Funcion densidad de Probabilidad"*.

Existen procesos que generan multiples variables aleatrorias analogicas, simultaneamente y (relacionadas?). Por ejemplo: una velocidad. Las secuencias formadas por tuplas de variables aleatorias analogicas se llaman *"Fuentes Analogicas Vectoriales*"

(Gallager, R. G. (1989). Capítulo 3. En Principles of Digital Communications (pp. 67-72). MIT Press.)

### Cuantizador

Un cuantizador es, por definicion, una funcion $Q:$
$$Q(x) = Y_n, x \in X_N $$

Donde ${X_0,X_1,...,X_n}$ es un conjunto de intervalos disjuntos que cubre $\real$.

Se extiende la definicion a "Cuantizadores Vectoriales" 
$$Q(x) = Y_n, x \in X_N $$

Donde ${X_0,X_1,...,X_n}$ es un conjunto de subconjuntos disjuntos que cubre $\real^n$.

(Gallager, R. G. (1989). Capítulo 3. En Principles of Digital Communications (pp. 67-72). MIT Press.)
### Error cuadratico medio de un cuantizador

El eroror cuadratico medio o "mean square root" $MSE$ , de un cuantizador, se define como:
$$MSE = \int_{-\infty}^{\infty} f(x)(x - Q(x))^2 dx$$
Con $f$ la pdf de la fuente analogica, y $Q$ un cuantizador.

(Gallager, R. G. (1989). Capítulo 3. En Principles of Digital Communications (pp. 67-72). MIT Press.)

### Entropia diferencial<sup>1</sup>de una fuente analogica $U$ asociada a pdf $ f_U(u)$. Se define 
$$ h[U] = \int_{-\infty}^{\infty} -f_U(u) \log f_U(u)du $$
Esta integral debe restringirse a regiones donde la pdf sea no nula. Dado que $0\log 0$ Se interpreta como $0$.

Similar a la entropia discreta, es la esperanza del valor $-\log f_U(u)$

La entropia diferencial no se ve afectada pos traslaciones de $f_U$ sin embargo, ante un cambio de escala $a$ la entropia se ve incrementada en $\log a$. Ademas puede tomar cualquier valor real.

Para el caso de fuentes vectoriales:
$$h[U^n] = E[-\log f_{U^n}(U_n)]$$

Donde $E$ es el valor esperado de una variable aleatoria.

(Gallager, R. G. (1989). Capítulo 3. En 
Principles of Digital Communications (pp. 67-72). MIT Press.)


