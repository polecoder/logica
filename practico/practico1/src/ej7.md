# Ejercicio 7

## Consigna

Considere el alfabeto $\sum = \{a,b,c\}$, y los lenguajes $\Delta$ y $\Gamma$ definidos en el ejercicio 6. Demuestre, usando el principio de inducción que corresponda, que:

(a) el largo de las palabras de $\Delta$ es múltiplo de tres.
(b) todas las palabras de $\Delta$ tiene una cantidad par de ocurrencias de la letra $b$.
(c) todas las palabras de $\Gamma$ tiene una cantidad par de ocurrencias de la letra $b$.
(d) en $\Gamma$ no hay palabras de largo dos.

## Resolución

Antes de empezar, enunciemos el PIP para ambos lenguajes:

**LENGUAJE $\Gamma$**

Sea $P$ una propiedad para el lenguaje $\Gamma$, si:

1. $P(\varepsilon)$
2. $P(a)$
3. Dados $\alpha, \beta \in \Gamma$; si $P(\alpha)$ y $P(\beta)$ entonces $P(b\alpha c\beta b)$

**LENGUAJE $\Delta$**

Sea $P$ una propiedad para el lenguaje $\Delta$, si:

1. $P(\varepsilon)$
2. Dado $\alpha \in \Delta$; si $P(\alpha)$ entonces $P(b\alpha bc)$
3. Dado $\alpha \in \Delta$; si $P(\alpha)$ entonces $P(b\alpha ba)$

Ahora si, empecemos a demostrar las propiedades:

### PARTE A

$P$: El largo de las palabras de $\Delta$ es múltiplo de 3

**CASO BASE**:

$P(\varepsilon)$: Se cumple trivialmente porque el largo de una palabra vacía es $0 = 3\cdot 0$

**PASO INDUCTIVO**:

Dado $\alpha \in \Delta$, quiero probar:

1. Si $P(\alpha)$ entonces $P(b\alpha bc)$
2. Si $P(\alpha)$ entonces $P(b\alpha ba)$

Entonces asumo $P(\alpha)$; es decir que el largo de $\alpha$ es múltiplo de tres. Se observa trivialmente que en ambos casos estoy sumando tres letras, entonces obtendré un múltiplo de 3. Algebraicamente:

$$|\alpha| = 3 \cdot k \text{ para algún }k\in\mathbb{N} \\
|b\alpha ba| = 3 \cdot (k+1) \text{ para algún }k\in\mathbb{N} \\
|b\alpha bc| = 3 \cdot (k+1) \text{ para algún }k\in\mathbb{N}
$$

Esto prueba la propiedad $P$: El largo de las palabras de $\Delta$ es múltiplo de 3

### PARTE B

Casi análoga a la parte A, es exactamente el mismo razonamiento

### PARTE C

$P$: Todas las palabras de $\Gamma$ tienen una cantidad par de ocurrencias de la letra $b$

**PASO BASE**

Consta de dos pasos porque tenemos dos elementos base:

- $P(\varepsilon)$: Se cumple trivialmente pues al no tener $b$, tiene $0 = 2\cdot 0$ ocurrencias de b

- $P(a)$: Se cumple por el mismo razonamiento.

**Paso inductivo**

Dado $\alpha,\beta \in \Delta$, quiero probar $P(b\alpha c\beta b)$ asumiendo lo siguiente:

- $P(\alpha)$: $\alpha$ tiene una cantidad de ocurrencias de $b$ par.
- $P(\beta)$: $\beta$ tiene una cantidad de ocurrencias de $b$ par.

Llamemos $O(b, \alpha)$, $O(b, \beta)$ a las ocurrencias de $b$ en $\alpha$ y $\beta$ respectivamente. Podemos decir que:

$$
O(b, \alpha) = 2 \cdot k_1 \\
O(b, \beta) = 2 \cdot k_2
$$

Para algunos $k_1,k_2 \in \mathbb{N}$
Ahora, queremos hallar $O(b, b\alpha c\beta b)$, podemos ver que esto está dado por:

$$O(b, b\alpha c\beta b) = O(b,\alpha) + O(b,\beta) + 2$$

Ya que entendemos que la cantidad de $b$ para esta palabra será la suma entre la cantidad de $b$ en $\alpha$ y $\beta$ más las dos que se agregan en el paso de construcción. Sustituyendo con lo que hallamos anteriormente:

$$
\begin{aligned}
O(b, b\alpha c\beta b) &= 2\cdot k_1 + 2\cdot k_2 + 2 \\
&= 2 \cdot (k_1 + k_2 + 1)
\end{aligned}
$$

Con esto concluimos que $b\alpha c\beta b$ tiene una cantidad de ocurrencias de $b$ par. Por lo que probamos la propiedad:
$P$: Todas las palabras de $\Gamma$ tienen una cantidad par de ocurrencias de la letra $b$

### PARTE D

Este ejercicio sale utilizando el PIP para $\Gamma$, quizás no es tan análogo a los anteriores, pero es muy sencillo de probar también