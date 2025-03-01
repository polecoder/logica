# Ejercicio 5

## Consigna

Sea un alfabeto $\sum = \{•, ◦, △, □\}$ y el conjunto $PAL$ definido inductivamente por las siguientes
reglas:
1. $\varepsilon \in PAL$
2. Si $x \in \sum$, entonces $x \in PAL$
3. Si $w \in PAL$ y $x \in \sum$, entonces $xwx \in PAL$

(a) Proporcione 3 elementos de $PAL$.
(b) Proporcione 3 elementos de $\sum^*$ que no pertenezcan a $PAL$.
(c) Enuncie el principio de inducción primitiva para $PAL$.

## Resolución

(a) Listemos 3 elementos de $PAL$:
- □□
- □△□
- □□◦□△□◦□□

(b) Listemos 3 elementos que no pertenecen a $PAL$:

- □□△
- □△□□
- □□◦□△□◦□□□

(c) Enunciemos el PIP para $PAL$:

Sea $P$ una propiedad sobre el conjunto $PAL$, si:

1. $P(\varepsilon)$
2. $\forall x \in\sum: P(x)$
3. Dados $w\in PAL, x\in\sum$; si $P(w)$ entonces $P(xwx)$

Entonces $P$ se cumple para todos los elementos de $PAL$