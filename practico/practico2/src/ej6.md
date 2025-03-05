# Ejercicio 6

## Consigna

Una relación binaria entre dos conjuntos $A$ y $B$ puede entenderse como un subconjunto del producto cartesiano $A \times B$. En particular, la relación subfórmula la podemos definir como un conjunto de pares de fórmulas:

- $SUBF \subseteq PROP \times PROP$
- $SUBF = \{\langle \varphi, \psi \rangle : \varphi \text{ es subfórmula de } \psi\}$

(a) Escribir una definición inductiva del conjunto $SUBF$.

(b) Formular el PIP correspondiente a la definición anterior.

(c) Demostrar por inducción en $SUBF$ la propiedad dada en el Ejercicio 4.

## Resolución (parte a)

Veamos como definir inductivamente el conjunto $SUBF$.

1. $\langle \varphi, \varphi \rangle \in SUBF$ para todo $\varphi \in PROP$.
2. Si $\langle \varphi, \psi_1 \rangle\in SUBF$ entonces $\langle \varphi, (\psi_1 * \psi_2) \rangle, \langle \varphi, (\psi_2 * \psi_1) \rangle \in SUBF$ para todo $\psi_2 \in PROP$ y $*\in C_2$.
3. Si $\langle \varphi, \psi \rangle\in SUBF$, entonces $\langle \varphi, \neg\psi \rangle \in SUBF$

La construcción viene a partir de la definición original de subfórmula.

## Resolución (parte b)

Formulemos el PIP para el conjunto $SUBF$.

Sea una propiedad $P$ sobre $SUBF$. Si:

1. $P(\varphi, \varphi)$ para todo $\varphi \in PROP$
2. Si $P(\varphi, \psi_1)$ entonces $P(\varphi, (\psi_1 * \psi_2))$ y $P(\varphi, (\psi_2 * \psi_1))$ para todo $\psi_2 \in PROP$ y $*\in C_2$.
3. Si $P(\varphi, \psi)$ entonces $P(\varphi, \neg\psi)$

Entonces $P(\varphi, \psi)$ para todo $\langle \varphi, \psi \rangle \in SUBF$.

## Resolución (parte c)

Vamos a demostrar por inducción en $SUBF$ la propiedad dada en el Ejercicio 4, es decir:

$$P(\psi):(\forall\varphi\in PROP)(\varphi\text{ subfórmula }\psi\Rightarrow(\forall s\in secFORM_{\psi})(\varphi\in s))$$

Pero esta propiedad está formulada sobre $PROP$, ahora formulémosla para $SUBF$:

$$P(\langle \varphi,\psi \rangle): (\langle \varphi,\psi \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{\psi})(\varphi\in s))$$

Ahora si podemos probarla usando el PIP:

### PASO BASE

$P(\langle \varphi, \varphi \rangle): (\langle \varphi,\varphi \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{\varphi})(\varphi\in s))$

Esto es trivial, ya que obviamente $\varphi$ está en su propia secuencia de formación.

### PASO INDUCTIVO

(H) $P(\langle \varphi, \psi_1 \rangle): (\langle \varphi,\psi_1 \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{\psi_1})(\varphi\in s))$

#### PARTE 1

(T1) $P(\langle \varphi, (\psi_1 * \psi_2) \rangle): (\langle \varphi,(\psi_1 * \psi_2) \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{(\psi_1 * \psi_2)})(\varphi\in s))$

(T2) $P(\langle \varphi, (\psi_2 * \psi_1) \rangle): (\langle \varphi,(\psi_2 * \psi_1) \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{(\psi_2 * \psi_1)})(\varphi\in s))$

Trabajemos sobre (T1), ya que (T2) es análoga. Utilizando la hipótesis (H) sabemos que:

- $\langle \varphi,\psi_1 \rangle\in SUBF$ entonces (por regla 2 de la definición inductiva de $SUBF$) $\langle \varphi, (\psi_1 * \psi_2) \rangle\in SUBF$
- También sabemos que $(\forall s\in secFORM_{\psi_1})(\varphi\in s)$

Por lo tanto, $\varphi$ está en todas las secuencias de formación de $\psi_1$, y como todas las secuencias de formación de $(\psi_1*\psi_2)$ contienen a una secuencia de formación de $\psi_1$, $\varphi$ está en todas las secuencias de formación de $(\psi_1*\psi_2)$.

#### PARTE 2

(T) $P(\langle \varphi, \neg\psi \rangle): (\langle \varphi,\neg\psi \rangle\in SUBF \Rightarrow (\forall s\in secFORM_{(\neg\psi)})(\varphi\in s))$

Utilizando la hipótesis (H) sabemos que:

- $\langle \varphi,\psi \rangle\in SUBF$ entonces (por regla 3 de la definición inductiva de $SUBF$) $\langle \varphi, \neg\psi \rangle\in SUBF$
- También sabemos que $(\forall s\in secFORM_{\psi})(\varphi\in s)$

Por lo tanto, $\varphi$ está en todas las secuencias de formación de $\psi$, y como todas las secuencias de formación de $(\neg\psi)$ contienen a una secuencia de formación de $\psi$, $\varphi$ está en todas las secuencias de formación de $(\neg\psi)$.