# Ejercicio 2

## Consigna

(a) Enuncie el principio de inducción primitiva para el conjunto $P$ definido inductivamente por las siguientes cláusulas:

1. $0 \in P$
2. Si $n \in P$ entonces $n + 2 \in P$

(b) Pruebe utilizando este principio, que para todo $n\in P$ , existe $m\in\mathbb{N}$ tal que $n = m+m$

## Resolución (parte a)

Enunciemos el PIP para el conjunto $P$:

Sea $S$ una propiedad sobre el conjunto $P$, si:

1. $S(0)$
2. Si $S(n)$ entonces $S(n+2)$

Entonces la propiedad $S$ se cumple para todos los elementos de $P$

## Resolución (parte b)

Llamemos $S$ a la propiedad que queremos probar:

$$S: \forall n\in P, \text{ existe } m\in\mathbb{N} \text{ tal que } n = m+m$$

**CASO BASE**
$S(0)$: Se cumple y $m = 0$

**PASO INDUCTIVO**
Suponemos que $S(n)$ se cumple, queremos probar que se cumple también $S(n+2)$.

Cómo $S(n)$ se cumple, puedo decir que $n= m_1+m_1$ con $m_1\in \mathbb{N}$.
Con este razonamiento, podemos decir que: $n+2 = m_1 + m_1 + 2 = (m_1+1) + (m_1+1)$
De esto derivamos que para $n+2$ el valor de $m$ es: $m=m_1+1$

Esto concluye la prueba.