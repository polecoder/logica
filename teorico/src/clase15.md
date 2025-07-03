# CLASE 15 - 19/05/2025

## Semántica de la lógica de predicados

### Interpretación de sentencias de $\mathcal{L(M)}$ en $\mathcal{M}$

La interpretación de las sentencias de $\mathcal{L(M)}$ en $\mathcal{M}$ es una función $v^{\mathcal{M}}: SENT\to\{0,1\}$ que satisface:

- $v^{\mathcal{M}}(t_1='t_2)=\begin{cases}1\quad\text{si }t_1^{\mathcal{M}}=t_2^{\mathcal{M}}\\0\quad\text{si }t_1^{\mathcal{M}}\neq t_2^{\mathcal{M}}\end{cases}$
- $v^{\mathcal{M}}(P_j(t_1,\ldots,t_{r_j}))=\begin{cases}1\quad\text{si }\left<t_1^{\mathcal{M}},\ldots,t_{r_j}^{\mathcal{M}} \right>\in R_j\\0\quad\text{si }\left<t_1^{\mathcal{M}},\ldots,t_{r_j}^{\mathcal{M}} \right>\notin R_j\end{cases}$
- $v^{\mathcal{M}}(\bot)=0$
- $v^{\mathcal{M}}((\neg\alpha))= 1-v^{\mathcal{M}}(\alpha)$
- $v^{\mathcal{M}}(\alpha\land\beta)=min\{v^{\mathcal{M}}(\alpha),v^{\mathcal{M}}(\beta)\}$
- $v^{\mathcal{M}}(\alpha\lor\beta)=max\{v^{\mathcal{M}}(\alpha),v^{\mathcal{M}}(\beta)\}$
- $v^{\mathcal{M}}(\alpha\to\beta)=max\{1-v^{\mathcal{M}}(\alpha),v^{\mathcal{M}}(\beta)\}$
- $v^{\mathcal{M}}(\alpha\leftrightarrow\beta)=1\iff v^{\mathcal{M}}(\alpha)=v^{\mathcal{M}}(\beta)$
- $v^{\mathcal{M}}((\forall x)\alpha)=min\{v^{\mathcal{M}}(\alpha[\overline{a}/x])\mid a\in|\mathcal{M}|\}$
- $v^{\mathcal{M}}((\exists x)\alpha)=max\{v^{\mathcal{M}}(\alpha[\overline{a}/x])\mid a\in|\mathcal{M}|\}$

#### Ejemplo 1

Sea $\mathcal{M}=\left<\mathbb{Z}, Primo, +,-,0,1\right>$ con tipo $\left<1;2,1;2\right>$. La interpretación de las sentencias de $\mathcal{L(M)}$ en $\mathcal{M}$ debe satisfacer:

- $v^{\mathcal{M}}(P_1(t_1))=\begin{cases}1\quad\text{si }t_1^{\mathcal{M}}\text{ es primo}\\0\quad\text{si }t_1^{\mathcal{M}}\text{ no es primo}\end{cases}$

#### Ejemplo 2

Sea $\mathcal{M}=\left<\mathbb{Z}, Primo, +,-,0,1\right>$ con tipo $\left<1;2,1;2\right>$. Qué valor de verdad tienen las sentencias $f_1(f_2(c_1),c_2)='c_2$ y $P_1(f_2(c_1),c_2)$.

$$
\begin{aligned}
v^{\mathcal{M}}(f_1(f_2(c_1),c_2)='c_2)=1\\
\iff\scriptstyle{(\text{interpretación de sentencias }(='))}\\
f_1(f_2(c_1),c_2)^{\mathcal{M}}=c_2^{\mathcal{M}}\\
\iff\scriptstyle{(\text{interpretación de términos cerrados})}\\
-c_1^{\mathcal{M}}+c_2^{\mathcal{M}}=c_2^{\mathcal{M}}\\
\iff\scriptstyle{(\text{interpretación de términos cerrados})}\\
-0+1=1
\end{aligned}
$$

Lo cual se cumple, por lo que el valor de verdad de la sentencia $v^{\mathcal{M}}(f_1(f_2(c_1),c_2)='c_2)=1$. Vayamos con el otro ejemplo:

$$
\begin{aligned}
v^{\mathcal{M}}(P_1(f_1(f_2(c_1),c_2)))=1\\
\iff\scriptstyle{(\text{interpretación de sentencias})}\\
f_1(f_2(c_1),c_2)^{\mathcal{M}}\text{ es primo}\\
\iff\scriptstyle{(\text{interpretación de términos cerrados})}\\
-c_1^{\mathcal{M}}+c_2^{\mathcal{M}}\text{ es primo}\\
\iff\scriptstyle{(\text{interpretación de términos cerrados})}\\
-0+1\text{ es primo}
\end{aligned}
$$

Dónde lo último se cumple pues 1 pertenece al conjunto de los números primos definido por la estructura $\mathcal{M}$.

#### Ejemplo 3

Sea $\mathcal{M}=\left<\mathbb{Z}, Primo, +,-,0,1\right>$ con tipo $\left<1;2,1;2\right>$. Qué valor de verdad tienen las sentencias $(\forall x)P_1(x)$ y $(\exists x)f_2(x)='x$?

$$
\begin{aligned}
v^{\mathcal{M}}((\forall x)P_1(x))\\
\iff\scriptstyle{(\text{interpretación de sentencias})}\\
min\{v^{\mathcal{M}}(P_1(\overline{a}))\mid a\in|\mathcal{M}|\}\\
=\scriptstyle{(\text{considerando el }4)}\\
0
\end{aligned}
$$

Veamos el otro ejemplo:

$$
\begin{aligned}
v^{\mathcal{M}}((\exists x)f_2(x)='x)\\
\iff\scriptstyle{(\text{interpretación de sentencias})}\\
max\{v^{\mathcal{M}}(f_2(\overline{a})='\overline{a})\mid a\in|\mathcal{M}|\}\\
=\scriptstyle{(\text{considerando el }0)}\\
1
\end{aligned}
$$

#### Ejemplo 4

Sea $\mathcal{M}=\left<\mathbb{Z}, Primo, +,-,0,1\right>$ con tipo $\left<1;2,1;2\right>$. Qué valor de verdad tiene la secuencia $(\forall x)P_1(x)\to\neg P_1(f_1(x,c_2))$?

$$
\begin{gathered}
v^{\mathcal{M}}((\forall x)P_1(x)\to\neg P_1(f_1(x,c_2)))\\
=\scriptstyle{(\text{interpretación de sentencias})}\\
min\{v^{\mathcal{M}}(P_1(\overline{a})\to\neg P_1(f_1(\overline{a},c_2)))\mid a\in|\mathcal{M}|\}\\
=\scriptstyle{(\text{interpretación de sentencias})}\\
min\{max\{1-v^{\mathcal{M}}(P_1(\overline{a})),v^{\mathcal{M}}(\neg P_1(f_1(\overline{a},c_2)))\}\mid a\in|\mathcal{M}|\}\\
=\scriptstyle{(\text{interpretación de sentencias})}\\
min\{max\{1-v^{\mathcal{M}}(P_1(\overline{a})),1-v^{\mathcal{M}}(P_1(f_1(\overline{a},c_2)))\}\mid a\in|\mathcal{M}|\}\\
=\scriptstyle{(\text{interpretación de sentencias})}\\
min\{max\{1-v^{\mathcal{M}}(P_1(\overline{a})),1-v^{\mathcal{M}}(P_1(f_1(\overline{a},c_2)))\}\mid a\in|\mathcal{M}|\}\\
\end{gathered}
$$

Observemos que tenemos un mínimo afuera del todo. Si encontramos un solo valor de $a\in|\mathcal{M}|$ para el cual alguna de las expresiones indicadas en el conjunto de adentro tenga valor $0$, entonces podremos confimar que $v^{\mathcal{M}}((\forall x)P_1(x)\to\neg P_1(f_1(x,c_2)))=0$.

Veamos que:

$$
\begin{gathered}
v^{\mathcal{M}}(P_1(\overline{2})) = 1\text{ y }v^{\mathcal{M}}(P_1(f_1(\overline{2},c_2)))=1\\
\implies\scriptstyle{(\text{interpretación de sentencias})}\\
v^{\mathcal{M}}(P_1(\overline{2})) = 1\text{ y }v^{\mathcal{M}}(\neg P_1(f_1(\overline{2},c_2)))=0\\
\implies\scriptstyle{(\text{interpretación de sentencias})}\\
v^{\mathcal{M}}(P_1(\overline{2})\to\neg P_1(f_1(\overline{2},c_2)))=0\\
\implies\scriptstyle{(\text{operatoria})}\\
min\{v^{\mathcal{M}}(P_1(\overline{a})\to\neg P_1(f_1(\overline{a},c_2)))\mid a\in|\mathcal{M}|\}=0\\
\implies\scriptstyle{(\text{interpretación de sentencias})}\\
v^{\mathcal{M}}((\forall x)P_1(x)\to\neg P_1(f_1(x,c_2)))=0\\
\end{gathered}
$$

**Observación:** Es exactamente el mismo razonamiento que aplicamos en matemática cuando queremos demostrar que una propiedad para todo un conjunto de elementos no se cumple: encontrar un contraejemplo.

#### Clausura universal de una fórmula

Antes de interpretar términos, nos aseguraremos de que estén cerrados.
Antes de interpretar fórmulas, nos aseguraremos de que sean sentencias.

Sean $\alpha\in FORM$ y $FV(\alpha)=\{z_1,\ldots, z_k\}$.
- Definimos $cl(\alpha)=(\forall z_1)\ldots(\forall z_k)\alpha$

#### Uso de $\models$

- Sea $\alpha\in SENT$. Entonces $\mathcal{M}\models\alpha$ sii $v^{\mathcal{M}}(\alpha)=1$
- Sea $\alpha\in FORM$. Entonces $\mathcal{M}\models\alpha$ sii $v^{\mathcal{M}}(cl(\alpha))=1$
- Sea $\Gamma\subseteq FORM$. Entonces $\mathcal{M}\models\Gamma$ sii $\mathcal{M}\models\alpha$ para todo $\alpha\in\Gamma$
- Sea $\alpha\in FORM$. Entonces $\models\alpha$ sii para toda estructura $\mathcal{M}$ del tipo adecuado $\mathcal{M}\models\alpha$
- Sea $\alpha\in SENT, \Gamma\subseteq SENT$. Entonces $\Gamma\models\alpha$ sii para toda estructura $\mathcal{M}$ del tipo adecuado, si $\mathcal{M}\models\Gamma$ entonces $\mathcal{M}\models\alpha$