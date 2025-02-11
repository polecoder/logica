# Ejercicio 3

## Consigna

Considere el conjunto inductivo $F$ definido mediante las siguientes reglas:
1. $\langle 0, 1\rangle \in F$
2. Si $\langle n, m\rangle \in F$, entonces $\langle m, n + m\rangle \in F$

Demostrar que
$$(\forall n \in N)\langle Fibo(n), Fibo(n + 1)\rangle \in F$$

donde la función $Fibo$ se define como:

$$
Fibo: \mathbb{N} \to \mathbb{N} \\
Fibo(0) = 0 \\
Fibo(1) = 1 \\
Fibo(n+2) = Fibo(n) + Fibo(n+1)
$$

## Resolución

Observemos que la propiedad que queremos probar, tiene la forma de la tesis del PIP de $\mathbb{N}$, por lo que usaremos dicho principio para probar esta propiedad. Enunciemos la propiedad $P$

$$P:(\forall n\in\mathbb{N}) \langle Fibo(n), Fibo(n + 1)\rangle \in F$$

**CASO BASE**

Sea $n=0$. Entonces:

$$
P(0): \langle Fibo(0), Fibo(0 + 1)\rangle \in F \\
P(0): \langle 0, 1\rangle \in F
$$

Acá usamos las reglas ya dadas de $Fibo(0)$ y $Fibo(1)$, y que $\langle 0, 1\rangle$ es un elemento base de $F$

**PASO INDUCTIVO**

Asumimos que $P(k)$ se cumple, queremos probar que se cumple para $P(k+1)$. Enunciemos $P(k+1)$:

$$
P(k+1): \langle Fibo(k+1), Fibo(k+1+1)\rangle \in F \\
P(k+1): \langle Fibo(k+1), Fibo(k+2)\rangle \in F \\
$$

Por la regla de construcción de $F$, sabemos que:

Si $\langle n,m\rangle \in F$, entonces $\langle m,n+m\rangle \in F$

También sabemos que:

$$
P(k): \langle Fibo(k), Fibo(k+1)\rangle \in F \\
$$

Entonces, con la regla de construcción de $F$, podemos decir que:

$$
\langle Fibo(k), Fibo(k+1)\rangle\in F \Rightarrow \\
\langle Fibo(k+1), Fibo(k) + Fibo(k+1)\rangle\in F
$$

Pero con la regla de construcción de $Fibo$ sabemos que:

$$Fibo(n+2) = Fibo(n) + Fibo(n+1)$$

Entonces concluimos que:

$$
\langle Fibo(k+1), Fibo(k) + Fibo(k+1)\rangle\in F \Rightarrow\\
P(k+1): \langle Fibo(k+1), Fibo(k+2)\rangle\in F
$$

Con esto, queda demostrado el ejercicio