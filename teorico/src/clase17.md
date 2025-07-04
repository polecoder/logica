# CLASE 17 - 16/06/2025

## Cálculo de la adjunta

### Ejemplo 1

Sea $V=W=\mathbb{R}^3$ con producto interno usual, considerando la siguiente transformación lineal:

- $T:\mathbb{R}^3\to\mathbb{R}^3$ definida por:
- $T(x,y,z)=(y+z,x+y+2z,5x-y)$

Para calcular $T^*(x',y',z')$ usamos la base canónica de $\mathbb{R}^3$, veamos de calcular $T^*$ para los vectores de la base canónica:

$$
\begin{aligned}
&\left<(x,y,z), T^*(1,0,0)\right>\\
&=\scriptstyle{(\text{definición de la adjunta})}\\
&\left<T(x,y,z), (1,0,0)\right>\\
&=\scriptstyle{(\text{definición de la transformación lineal})}\\
&\left<(y+z,x+y+2z,5x-y), (1,0,0)\right>\\
&=\scriptstyle{(\text{desarrollo})}\\
&y+z\\
&=\scriptstyle{(\text{producto interno usual})}\\
&\left<(x,y,z), (0,1,1)\right>\\
\end{aligned}
$$

Con esto concluimos que $T^*(1,0,0)=(0,1,1)$.

$$
\begin{aligned}
&\left<(x,y,z), T^*(0,1,0)\right>\\
&=\scriptstyle{(\text{definición de la adjunta})}\\
&\left<T(x,y,z), (0,1,0)\right>\\
&=\scriptstyle{(\text{definición de la transformación lineal})}\\
&\left<(y+z,x+y+2z,5x-y), (0,1,0)\right>\\
&=\scriptstyle{(\text{desarrollo})}\\
&x+y+2z\\
&=\scriptstyle{(\text{producto interno usual})}\\
&\left<(x,y,z), (1,1,2)\right>\\
\end{aligned}
$$

Con esto concluimos que $T^*(0,1,0)=(1,1,2)$

$$
\begin{aligned}
&\left<(x,y,z), T^*(0,0,1)\right>\\
&=\scriptstyle{(\text{definición de la adjunta})}\\
&\left<T(x,y,z), (0,0,1)\right>\\
&=\scriptstyle{(\text{definición de la transformación lineal})}\\
&\left<(y+z,x+y+2z,5x-y), (0,0,1)\right>\\
&=\scriptstyle{(\text{desarrollo})}\\
&5x-y\\
&=\scriptstyle{(\text{producto interno usual})}\\
&\left<(x,y,z), (5,-1,0)\right>\\
\end{aligned}
$$

Con esto concluimos que $T^*(0,0,1)=(5,-1,0)$.

Ahora, podemos decir que:

$$
\begin{aligned}
T^*(x',y',z')&=x'T^*(1,0,0)+y'T^*(0,1,0)+z'T^*(0,0,1)\\
&= x'(0,1,1)+y'(1,1,2)+z'(5,-1,0)\\
&=(y'+5z',x'+y'-z',x'+2y')\\
\end{aligned}
$$

Y con esto hallamos $T^*(x',y',z')$ para todo $(x',y',z')\in \mathbb{R}^3$

### Ejemplo 2

Sea $V=W=\mathcal{M}_{n\times n}$ con el producto interno $\left<A, B\right>=tr(B^tA)$, $\forall A,B\in\mathcal{M}_{n\times n}$.
Dada $M\in\mathcal{M}_{n\times n}$, tomamos la siguiente transformación lineal:

- $T:\mathcal{M}_{n\times n}\to\mathcal{M}_{n\times n}$
- $T(A)=MA\quad\forall A\in\mathcal{M}_{n\times n}$

Veamos como hallar $T^*$, sabemos que por definición de adjunta, debe cumplirse que:

$$
\left<T(A), B\right>=\left<A, T^*(B)\right>\quad\forall A,B\in\mathcal{M}_{n\times n}
$$

Partamos de $\left<T(A), B\right>$ y tratemos de llegar a $\left<A, T^*(B)\right>$:

$$
\begin{aligned}
&\left<T(A), B\right>\\
&=\scriptstyle{(\text{definición de T})}\\
&\left<MA, B\right>\\
&=\scriptstyle{(\text{definición del producto interno dado})}\\
&tr(B^tMA)\\
&=\scriptstyle{(\text{propiedades de la traspuesta})}\\
&tr((M^tB)^tA)\\
&=\scriptstyle{(\text{definición del producto interno dado})}\\
&\left<A, M^tB\right>\\
&=\scriptstyle{(\text{considerando }T^*(B)=M^tB)}\\
&\left<A, T^*(B)\right>
\end{aligned}
$$

Considerando que este razonamiento es válido para todo $A\in\mathcal{M}_{n\times n}$, podemos definir $T^*(B)=M^tB$

## Propiedades de la adjunta

Sean $V,W,U$ espacios vectoriales sobre el mismo $\mathbb{K}$ con producto interno.

1. Sean $T_1:V\to W$ y $T_2:V\to W$, entonces $(T_1+T_2)^*=T_1^*+T_2^*$
2. Sean $T:V\to W,\alpha\in\mathbb{K}$, entonces $(\alpha T)^*=\overline{\alpha}T^*$
3. Sean $T:V\to W$ y $S:W\to U$, $(S\circ T:V\to U)$, entonces $(S\circ T)^*=T^*\circ S^*$
4. Sea $T:V\to W$, entonces $(T^*)^*=T$
5. Sea $T:V\to W$, $T$ es invertible $\iff$ $T^*$ es invertible y además $(T^*)^{-1}=(T^{-1})^*$
6. Sea $Id:V\to V$ la transformación identidad, entonces $Id=Id^*$
7. Sea $T:V\to V$ un operador lineal. $\lambda$ es un valor propio de $T\iff\overline{\lambda}$ es un valor propio de $T^*$