# CLASE 2 - 10/02/2025

## Inducción

### Ejemplo (metavariables)

Retomemos la definición inducitva de los números pares:

1. $0 \in \mathbb{P}$
2. Si $n \in \mathbb{P}$, entonces $n+2 \in \mathbb{P}$

**Observación**: Llamamos metavariables ($n$ en este caso) a los elementos que necesitan menos reglas para su construcción

### Definición (alfabeto)

Sea $\sum$ un conjunto conocido de cosas distinguibles entre si (símbolos, letras, marcas).

Decimos que:

- Una palabra (o secuencia, o tira, o string) es una secuencia finita de elementos de $\sum$
- Dadas dos palabras $w_1$ y $w_2$, podemos formar una nueva palabra $w_1w_2$ que es la concatenación de ambas.
- Existe una palabra vacía $\varepsilon$ que no tiene ninguna letra, y es el neutro de la concatenación.
- $\sum^*$ es el conjunto de todas las palabras que se pueden formar con los elementos de $\sum$
- Cualquier subconjunto de $\sum^*$ que cumpla con las reglas anteriores es un lenguaje.
- Hay lenguajes que se pueden definir inductivamente y tratar como conjuntos inductivos

#### Ejemplo 1 (lenguaje)

Definimos el lenguaje $L_1 \subset \{a,b\}^*$ con las siguientes reglas:

1. $a \in L_1$
2. Si $w \in L_1$, entonces $bwb \in L_1$

Veamos ejemplos de palabras que pertenecen a este lenguaje:

- $a \in L_1$
- $bab \in L_1$
- $bbabb \in L_1$
- $aba \not\in L_1$
- $ababab \not\in L_1$

Podemos decir que son todas las palabras con la misma cantidad de $b$ a ambos lados de una $a$ que queda en el medio.

#### Ejemplo 2 (lenguaje)

Definimos el lenguaje $L_2 \subset \{a,b,c\}^*$ con las siguientes reglas:

1. $b \in L_2$
2. Si $w \in L_2$, entonces $awc \in L_2$

### Pertenencia de un elemento a un conjunto inductivo

Para probar que un elemento pertenece a un conjunto inductivo, basta con mostrar como lo formamos. Su secuencia de formación indica cuáles reglas se usan y en que orden.

#### Ejemplo

$bbabb \in L_1$ porque:

1. $a \in L_1$ por $(i)$
2. $bab \in L_1$ por $(ii)$
3. $bbabb \in L_1$ por $(ii)$

### Probar propiedades de conjuntos

Según como definimos al conjunto, tenemos dos formas de probar propiedades:

- Si definimos por extensión: Probar que la propiedad se cumple para todos los elementos del conjunto
- Si definimos por comprensión: Probar que la propiedad se cumple para los elementos que cumplen con la definción del conjunto

#### Principio de inducción primitiva

Sea $N \subset \mathbb{N}$ definido inductivamente por:

1. $0 \in N$
2. Si $n \in N$, entonces $n+1 \in N$

Sea $P(n)$ una propiedad que queremos probar para todo $n \in \mathbb{N}$. Para probar que $P(n)$ es verdadera para todo $n \in \mathbb{N}$, basta con:

1. Mostrar que $P(0)$ es verdadera
2. Mostrar que si $P(n)$ es verdadera, entonces $P(n+1)$ es verdadera

##### Demostración

Queremos probar que si se cumplen 1 y 2, entonces $P(n)$ es verdadera para todo $n \in \mathbb{N}$.

Sea $X = \{n \in \mathbb{N} \mid P(n)\}$. Por hipótesis, sabemos que 1 y 2 se cumplen.
Podemos observar que $\mathbb{N}$ es el minimo subconjunto de $X$ que cumple con 1 y 2. Por lo tanto, $X \subset \mathbb{N}$.

#### Ejemplo

Dado el lenguaje $L_1$ definido anteriormente, probemos que todas las palabras de $L_1$ tienen una cantidad impar de letras.

##### Demostración

Por inducción en la formación de las palabras de $L_1$:

- **Caso base**: $a$ tiene una cantidad impar de letras
    - $|a| = 1$ es impar
- **Paso inductivo**: Si $w \in L_1$ tiene una cantidad impar de letras, entonces $bwb$ tiene una cantidad impar de letras.
    - Por hipótesis, $|w|$ es impar, entonces $|bwb| = |w| + 2$ es impar, ya que si sumo 2 a un número impar, obtengo otro número impar

Por el principio de inducción primitiva, todas las palabras de $L_1$ tienen una cantidad impar de letras.

#### Ejemplo 2

Probar que todas las palabras de $L_1$ son palíndromos

##### Demostración

Por inducción en la formación de las palabras de $L_1$:

- **Caso base**: $a$ es palíndromo
    - $a$ es palíndromo porque es una sola letra
- **Paso inductivo**: Si $w \in L_1$ es palíndromo, entonces $bwb$ es palíndromo
    - Por hipótesis, $w$ es palíndromo, entonces $bwb$ es palíndromo porque es la misma palabra al revés
