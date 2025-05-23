# Ejercicio 6

## Consigna

1. Sabemos que para toda sentencia $\sigma$ y estructura $A$ del tipo adecuado se cumple que $A \models \sigma$ o $A \models \neg \sigma$. Muestre que esta propiedad no vale para $\sigma$ con $FV(\sigma) \ne \emptyset$.

2. Muestre que ni aún para el caso en que $\sigma$ sea una sentencia vale que $\models \sigma$ o $\models \neg \sigma$.

## Resolución

### Parte 1

Para esta parte queremos buscar una fórmula $\sigma\in FORM_A$ tal que $FV(\sigma)\neq\emptyset$ y una estructura $A$ del tipo adecuado como contraejemplo, tal que se cumplen las siguientes afirmaciones:

1. $A\not\models\sigma$
2. $A\not\models\neg\sigma$

Veamos que significan ambas según la definición de $\models$:

1. Existe $v^A$ tal que $v^A(cl(\sigma))=0$
2. Existe $v^A$ tal que $v^A(cl(\neg\sigma))=0$

A partir de esto, establezcamos una estructura y la sentencia que vamos a usar:

- $A=\left<\mathbb{N},Primo,+,0\right>$ con el alfabeto predeterminado $(P_1,f_1,c_1)$
- $\sigma= P_1(x)$

Ahora, veamos que podemos decir sobre $A\models\sigma$:

$$
\begin{gathered}
A\models P_1(x)\\
\iff\scriptstyle{(\text{definición de }\models)}\\
v^A(cl(P_1(x)))=1\\
\iff\scriptstyle{(\text{definición de clausura})}\\
v^A((\forall x)P_1(x))=1\\
\iff\scriptstyle{(\text{como }v^A\text{ es una interpretación})}\\
min\{v^A(P_1(x)[\overline{n}/x])\mid n\in \mathbb{N}\}=1\\
\iff\scriptstyle{(\text{considerando el }4)}\\
\text{ABSURDO! Pues }4\text{ no es primo}
\end{gathered}
$$

Por lo tanto, la suposición inicial fue incorrecta, esto implica que $A \not\models\sigma$.
Veamos que podemos decir ahora sobre $A\models\neg\sigma$:

$$
\begin{gathered}
A\models \neg P_1(x)\\
\iff\scriptstyle{(\text{definición de }\models)}\\
v^A(cl(\neg P_1(x)))=1\\
\iff\scriptstyle{(\text{definición de clausura})}\\
v^A((\forall x)\neg P_1(x))=1\\
\iff\scriptstyle{(\text{como }v^A\text{ es una interpretación})}\\
min\{v^A(\neg P_1(x)[\overline{n}/x])\mid n\in \mathbb{N}\}=1\\
\iff\scriptstyle{(\text{considerando el }2)}\\
v^A(\neg P_1(\overline{2}))=1\\
\iff\scriptstyle{(\text{como }v^A\text{ es una interpretación})}\\
1-v^A(P_1(\overline{2}))=1\\
\iff\scriptstyle{(\text{aritmética})}\\
v^A(P_1(\overline{2}))=0\\
\iff\scriptstyle{(v^A(P_1(\overline{2})=1))}\\
\text{ABSURDO!}
\end{gathered}
$$

Lo que escribimos parece más complicado de lo que realmente es, pero básicamente llegamos a que "$2$ es primo" es una afirmación **FALSA** a partir de nuestras hipótesis, lo cual es claramente absurdo.
Esto implica que $A\not\models\sigma$.

Con esto concluimos la prueba de la primer parte.

### Parte 2

Para esta parte queremos ver que dada una sentencia $\sigma\in SENT$, tenemos que las siguientes afirmaciones se cumplen simultaneamente:

1. $\not\models\sigma$
2. $\not\models\neg\sigma$

Esto significa que lo que queremos probar es que existen dos estructuras $A,B$ del tipo adecuado que cumple lo siguiente:

1. $v^A(\sigma)=0$
2. $v^B(\neg\sigma)=0$

Consideremos $\sigma= (\forall x)P_1(x)$ y veamos ambas subpartes:

#### Subparte 1

Consideremos para este caso lo siguiente:

- $A=\left<\mathbb{N},Primo,+,0\right>$ con el alfabeto predeterminado $(P_1,f_1,c_1)$

Ya probamos en la parte anterior que $v^A(\sigma)=0$

#### Subparte 2

- $B=\left<\mathbb{R},Negativo,+,1 \right>$ con el alfabeto predeterminado $(P_1,f_1,c_1)$.

Donde negativo (unario) contiene todos los números negativos.

Probemos que $v^B(\sigma)=0$

$$
\begin{gathered}
v^B((\forall x)P_1(x))\\
=\scriptstyle{(\text{como }v^A\text{ es una interpretación})}\\
min\{v^B(P_1(\overline{y}))\mid y\in\mathbb{R}\}\\
=\scriptstyle{(\text{considerando el }1)}\\
0
\end{gathered}
$$

Esto concluye la prueba de la segunda parte.