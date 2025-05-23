# Ejercicio 4

## Consigna

Considere un lenguaje de primer orden del tipo $\langle -;\ 2,\ 2,\ 1;\ 1 \rangle$.  
Sea $A$ una estructura de dicho tipo definida como sigue: 
$A = \langle \mathbb{N},\ +,\ \ast,\ S,\ 0 \rangle$ donde $S(x) = x + 1$.

1. Defina los símbolos del alfabeto y dé dos términos distintos $t_1$ y $t_2$ del lenguaje tales que:

$$
t_1^A = t_2^A = 3
$$

2. Demuestre que para todo $n \in \mathbb{N}$ hay un término $t$ tal que $t^A = n$.

3. Sea $t$ un término y $n$ un natural. Demuestre que si $t^A = n$ entonces existe $t'$ tal que $t'^A = n$ y tiene más ocurrencias de los símbolos $f_1$ y $c_1$.

4. Demuestre por el absurdo que para todo $n \in \mathbb{N}$ hay infinitos términos $t$ tales que $t^A = n$.

## Resolución

### Parte 1

Considerando el alfabeto por defecto para el tipo definido:

- $f_1,f_2,f_3; c_1$

Encontremos dos términos diferentes tal que su interpretación sea $3$:

- $t_1=f_3(f_3(f_3(c_1)))$
- $t_2=f_1(f_3(f_3(f_3(c_1))), c_1)$

Es bien fácil ver que ambos términos evaluados en la estructura $A$ son $3$.

### Parte 2

Probemos la propiedad dada usando el PIP sobre $\mathbb{N}$. Definimos la propiedad como:

$P(n): (\overline{\forall} n\in\mathbb{N})\overline{\exists}t\in TERM_A$ tal que $t^A=n$

#### Demostración

##### Paso base

$P(0):\overline{\exists}t\in TERM_A$ tal que $t^A=0$

Esto es trivial pues $c_1^A=0$, y sabemos que $c_1\in TERM_A$

##### Paso inductivo

(H) $P(n):\overline{\exists}t_1\in TERM_A$ tal que $(t_1)^A=n$
(T) $P(n+1):\overline{\exists}t_2\in TERM_A$ tal que $(t_2)^A=n+1$

Evaluemos la tesis para ver que podemos decir sobre ella:

$$
\begin{gathered}
n+1\\
=\scriptstyle{(\text{por hipótesis inductiva: }(t_1)^A=n)}\\
(t_1)^A+1\\
=\scriptstyle{(\text{por interpretación de }f_3)}\\
f_3((t_1)^A)\\
=\scriptstyle{(\text{por interpretación de términos cerrados})}\\
f_3(t_1)^A\\
\end{gathered}
$$

Por lo que encontramos $t_2\in TERM_A$ tal que se cumple que:

$$
f_3(t_1)^A = n+1
$$

Lo que prueba la tesis, y por lo tanto la propiedad para todos los naturales. $\blacksquare$

### Parte 3

Para probar esta parte, tomaremos un $t\in TERM_A$ cualquiera, que cumpla con $t^A=n$.

Veamos que:

$$
\begin{gathered}
t^A=n\\
\iff\scriptstyle{(\text{aritmética})}\\
t^A+0 = n\\
\iff\scriptstyle{(\text{interpretación de }f_1,c_2)}\\
f_1(t,c_1)^A = n
\end{gathered}
$$

Por lo que encontramos $t'=f_1(t,c_1)$ que cumple con lo que buscabamos, es decir que $t'^A=n$.

También se observa trivialmente que $t'$ tiene más ocurrencias de $f_1$ y $c_1$ que $t$, esto porque tiene las mismas que tiene $t$ (pues lo incluye) y a eso le suma una ocurrencia de ambas $f_1$ y $c_1$

Para finalizar, podemos concluir que esto se cumple para cualquier $t$, porque hicimos el razonamiento para un $t$ cualquiera.

### Parte 4

Supongamos que existe un $n\in\mathbb{N}$ tal que solo hay $m\in\mathbb{N}$ términos $t\in\{t_1,\ldots,t_m\}$ que cumplen que $t^A=n$.

Consideremos $t'\in\{t_1,\ldots,t_m\}$ como el término con la máxima cantidad de ocurrencias de $f_1$, esto es posible pues los términos son finitos.

De la forma en la que elegimos $t'$, sabemos que $t'^A=n$, por lo que podemos aplicar la propidad que probamos en la parte anterior (parte 3). Con esto obtenemos a quién llamamos $t''\in TERM_A$, veamos lo que podemos decir sobre este término:

1. Cómo $t''^A=n$ por la propiedad de la parte 3, podemos decir que $t''\in\{t_1,\ldots,t_m\}$.
2. También por la propiedad de la parte 3, $t''$ tiene más ocurrencias de $f_1$ que $t'$.

Pero estas dos observaciones son contradictorias, pues $t'$ era el elemento con mayor cantidad de ocurrencias del conjunto $\{t_1,\ldots,t_m\}$. ABSURDO!

Por lo tanto, queda probado que para todo $n \in \mathbb{N}$ hay infinitos términos $t$ tales que $t^A = n$. $\blacksquare$