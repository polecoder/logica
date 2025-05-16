# CLASE 14 - 16/05/2025

## Semántica de la lógica de predicados

### Visión intuitiva de la semántica

#### Términos

- Representan elementos del **Universo**. Conviene que cualquier elemento tenga al menos un nombre (una forma de referenciarlo):
    - Se modifica **TERM** para que todo elemento del universo tenga algún nombre.
    - Mostraremos que objetos del universo son representados por cada término cerrado: Símbolo de función aplicado a algún nombre de elemento del universo.

#### Fórmulas

- Representan lo que se dice en el **Universo**.
    - Algunas pueden ser verdaderas o falsas (sentencias - formulas cerradas) en una estructura dada
    - Mostraremos cómo averiguar si una sentencia es verdadera o falsa

#### Constantes

- Las constantes $c_1, c_2,\ldots$ son nombres para los elementos distinguidos del universo.
    - Se usan en cualquier fórmula y cualquier contexto de uso
- Después tenemos las constantes del lenguaje extendido: Una representación habitual de un elemento del universo con un techo $\overline{x}$, es un nombre para ese elemento del universo.
    - Ejemplo: $\overline{1}$ es una constante (sintáxis) para el número $1$ que es un elemento de un universo dado
    - Se usan para interpretar las fórmulas con variables

#### Definición (lenguaje extendido para una estructura)

Sea $\mathcal{M}$ una estructura.
El lenguaje extendido para $\mathcal{M}$, notado $\mathcal{L(M)}$ se obtiene del lenguaje $\mathcal{L}$ del tipo de $\mathcal{M}$ agregando símbolos de constante para todos los elementos de $|\mathcal{M}|$. Al símbolo de constante asociado a $a\in|\mathcal{M}|$ lo denotamos como $\overline{a}$

### Interpretación de términos cerrados de $\mathcal{L(M)}$ en $\mathcal{M}$

#### Definición

Sea $\mathcal{M} = \left<A,R_1,\ldots,R_n,F_1,\ldots,F_m,\{C_i\mid 1\leq i\leq k\}\right>$ con tipo $\left<r_1,\ldots,r_n;a_1,\ldots,a_m;k\right>$.
La interpretación de los términos cerrados de $\mathcal{L(M)}$ en $\mathcal{M}$ es una función $\_^{\mathcal{M}}:TERM_C\to|\mathcal{M}|$ que satisface:

- $c_i^\mathcal{M}=C_i$ para todo $1\leq i\leq k$
- $\overline{a}^\mathcal{M}$ para todo $a\in|\mathcal{M}|$
- $f_i(t_1,\ldots,t_{a_i})^\mathcal{M}=F_i(t_1^\mathcal{M},\ldots, t_{a_i}^\mathcal{M})$ para $i=1,\ldots,m$

#### Ejemplo

Sea $\mathcal{M}=\left<\mathbb{Z},Primo,+,-,0,1 \right>$ con tipo $\left<1;2,1;2\right>$. La interpretación de los términos cerrados de $\mathcal{L(M)}$ en $\mathcal{M}$ es una función $\_^\mathcal{M}:TERM_C\to\mathbb{Z}$ que satisface:

- $c_1^\mathcal{M} = 0$
- $c_2^\mathcal{M} = 1$
- $\overline{n}^\mathcal{M}$ para todo $n\in\mathbb{Z}$
- $f_1(t_1,t_2)^\mathcal{M} = t_1^\mathcal{M}+t_2^\mathcal{M}$
- $f_2(t_1)^\mathcal{M} = -t_1^\mathcal{M}$

1. Para este caso, qué valor representa el término $f_1(f_2(c_1), c_2)$?

$$
\begin{aligned}
&f_1(f_2(c_1), c_2)^\mathcal{M}\\
&=\\
&f_1(-c_1^\mathcal{M}, c_2^\mathcal{M})\\
&=\\
&-c_1^\mathcal{M}+c_2^\mathcal{M}\\
&=\\
&-0+1\\
&=\\
&1\\
\end{aligned}
$$

2. Para este caso, qué valor representa el término $f_2(f_1(c_1,c_2))$?

$$
\begin{aligned}
&f_2(f_1(c_1,c_2))^\mathcal{M}\\
&=\\
&f_2(c_1^\mathcal{M}, c_2^\mathcal{M})\\
&=\\
&-(c_1^\mathcal{M}+c_2^\mathcal{M})\\
&=\\
&-(0+1)\\
&=\\
&-1\\
\end{aligned}
$$
