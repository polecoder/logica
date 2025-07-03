# CLASE 16 - 03/07/2025

## Semántica de la lógica de predicados

### Nomenclatura

1. $\mathcal{M}$ es modelo de $\alpha$ si $\mathcal{M}\models\alpha$
2. $\mathcal{M}$ es modelo de $\Gamma$ si $\mathcal{M}\models\Gamma$
3. $\alpha$ es verdadera si $\models\alpha$
4. $\alpha$ es consecuencia semántica de $\Gamma$ si $\Gamma\models\alpha$
5. $\alpha$ es satisfecha por $a_1,\ldots,a_k\in|\mathcal{M}|$ si $\mathcal{M}\models\alpha[a_1,\ldots,a_k/z_1,\ldots,z_k]$ con $FV(\alpha)=\{z_1,\ldots,z_k\}, k>0$
6. $\alpha$ es satisfactible en $\mathcal{M}$ si existen $a_1,\ldots,a_k\in|\mathcal{M}|$ que la satisfacen.
7. $\alpha$ es satisfactible si existe algún $\mathcal{M}$ tal que $\alpha$ es satisfactible en $\mathcal{M}$

### Lema 2.4.5: Propiedades de $\models$

La relación $\models$ refleja el significado intuitivo de los conectivos y los cuantificadores en las sentencias.

Sean $\alpha,\beta\in SENT$, $\gamma\in FORM, FV(\gamma)\subseteq\{x\}$. Entonces,

- $\mathcal{M}\models(\alpha\land\beta)$ sii $\mathcal{M}\models\alpha$ y $\mathcal{M}\models\beta$
- $\mathcal{M}\models(\alpha\lor\beta)$ sii $\mathcal{M}\models\alpha$ o $\mathcal{M}\models\beta$
- $\mathcal{M}\models(\neg\alpha)$ sii $\mathcal{M}\not\models\alpha$
- $\mathcal{M}\models(\alpha\to\beta)$ sii (si $\mathcal{M}\models\alpha$ entonces $\mathcal{M}\models\beta$)
- $\mathcal{M}\models(\alpha\leftrightarrow\beta)$ sii ($\mathcal{M}\models\alpha$ sii $\mathcal{M}\models\beta$)
- $\mathcal{M}\models((\forall x)\gamma)$ sii para todo $a\in|\mathcal{M}|, \mathcal{M}\models\gamma[\overline{a},x]$
- $\mathcal{M}\models((\exists x)\gamma)$ sii existe $a\in|\mathcal{M}|$ tal que $\mathcal{M}\models\gamma[\overline{a},x]$

#### Lema 2.4.5: Demostración

##### Conectivo $\land$

$$
\begin{aligned}
&\mathcal{M}\models\alpha\land\beta\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&v^{\mathcal{M}}(\alpha\land\beta)=1\\
&\iff\scriptstyle{(\text{definición de interpretación }v^{\mathcal{M}})}\\
&min\{v^{\mathcal{M}}(\alpha),v^{\mathcal{M}}(\beta)\}=1\\
&\iff\scriptstyle{(\text{aritmética})}\\
&v^{\mathcal{M}}(\alpha)=1\text{ y }v^{\mathcal{M}}(\beta)=1\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&\mathcal{M}\models\alpha\text{ y }\mathcal{M}\models\beta
\end{aligned}
$$

##### Conectivo $\neg$

$$
\begin{aligned}
&\mathcal{M}\models\neg\alpha\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&v^{\mathcal{M}}(\neg\alpha)=1\\
&\iff\scriptstyle{(\text{definición de interpretacion }v^{\mathcal{M}})}\\
&v^{\mathcal{M}}(\alpha)=0\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&\mathcal{M}\not\models\alpha
\end{aligned}
$$

##### Cuantificador $\forall$

$$
\begin{aligned}
&\mathcal{M}\models(\forall x)\alpha\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&min\{v^{\mathcal{M}}(\alpha[\overline{a}/x])\mid a\in|\mathcal{M}|\}=1\\
&\iff\scriptstyle{(\text{aritmética})}\\
&\text{para todo }a\in|\mathcal{M}|, \mathcal{M}\models\alpha[\overline{a}/x]
\end{aligned}
$$

##### Cuantificador $\to$

Queremos probar que $\mathcal{M}\models(\alpha\to\beta)$ sii (si $\mathcal{M}\models\alpha$ entonces $\mathcal{M}\models\beta$), que es equivalente a decir que:

$$
\mathcal{M}\models\alpha\to\beta\text{ sii }\mathcal{M}\models\alpha\Rightarrow\mathcal{M}\models\beta
$$

Como tenemos un "sii", tenemos que probar dos partes:

###### Directo

$$
\begin{aligned}
&\mathcal{M}\models\alpha\to\beta\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&v^{\mathcal{M}}(\alpha\to\beta)=1\\
&\iff\scriptstyle{(\text{definición de interpretación }v^{\mathcal{M}})}\\
&v^{\mathcal{M}}(\alpha)=0\text{ o }v^{\mathcal{M}}(\beta)=1\\
\end{aligned}
$$

Entonces a partir de acá separamos en dos casos:

**CASO 1: $v^{\mathcal{M}}(\alpha)=0$**

$$
\begin{aligned}
&v^{\mathcal{M}}(\alpha)=0\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&\mathcal{M}\not\models\alpha\\
&\iff\scriptstyle{(\text{definición de implicancia})}\\
&\mathcal{M}\models\alpha\Rightarrow\mathcal{M}\models\beta
\end{aligned}
$$

**CASO 2: $v^{\mathcal{M}}(\beta)=1$**

$$
\begin{aligned}
&v^{\mathcal{M}}(\beta)=1\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&\mathcal{M}\models\beta\\
&\iff\scriptstyle{(\text{definición de implicancia})}\\
&\mathcal{M}\models\alpha\Rightarrow\mathcal{M}\models\beta
\end{aligned}
$$

Por lo tanto, $\mathcal{M}\models\alpha\Rightarrow\mathcal{M}\models\beta$

###### Recíproco

Para esta parte también habría dos casos que considerar:

1. Cuando $\mathcal{M}\not\models\alpha$
2. Cuando $\mathcal{M}\models\alpha$

Pero observemos que el primero es trivial, pues si $\mathcal{M}\not\models\alpha$, entonces $v^{\mathcal{M}}(\alpha)=0$ y por lo tanto: $v^{\mathcal{M}}(\alpha\to\beta)=1$.

Consideremos el segundo entonces:

$$
\begin{aligned}
&\mathcal{M}\models\alpha\\
&\iff\scriptstyle{(\text{por hipótesis})}\\
&\mathcal{M}\models\beta\\
&\iff\scriptstyle{(\text{definición de interpretación }v^{\mathcal{M}})}\\
&v^{\mathcal{M}}(\beta)=1\\
&\iff\scriptstyle{(\text{aritmética})}\\
&max\{1-v^{\mathcal{M}}(\alpha),v^{\mathcal{M}}(\beta)\}=1\\
&\iff\scriptstyle{(\text{definición de interpretación }v^{\mathcal{M}})}\\
&v^{\mathcal{M}}(\alpha\to\beta)=1\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&\mathcal{M}\models\alpha\to\beta
\end{aligned}
$$

#### Lema 2.4.5: Contrarrecíprocos

Sean $\alpha,\beta\in SENT$. Entonces,

- $\mathcal{M}\not\models(\alpha\land\beta)$ sii $\mathcal{M}\not\models\alpha$ o $\mathcal{M}\not\models\beta$
- $\mathcal{M}\not\models(\alpha\lor\beta)$ sii $\mathcal{M}\not\models\alpha$ y $\mathcal{M}\not\models\beta$
- $\mathcal{M}\not\models(\neg\alpha)$ sii $\mathcal{M}\models\alpha$
- $\mathcal{M}\not\models(\alpha\to\beta)$ sii $\mathcal{M}\models\alpha$ y $\mathcal{M}\not\models\beta$
- $\mathcal{M}\not\models(\alpha\leftrightarrow\beta)$ sii $(\mathcal{M}\not\models\alpha\text{ sii }\mathcal{M}\models\beta)$
- $\mathcal{M}\not\models(\forall x)\alpha$ sii existe $a\in|\mathcal{M}|$ tal que $\mathcal{M}\not\models\alpha[\overline{a}/x]$
- $\mathcal{M}\not\models(\exists x)\alpha$ sii para todo $a\in|\mathcal{M}|,\mathcal{M}\not\models\alpha[\overline{a}/x]$

### Equivalencia y generalización de las Leyes de De Morgan

#### Definición de $\text{eq}$

Dados $\alpha,\beta\in FORM$, decimos $\alpha \text{ eq }\beta$ sii $\models(\alpha\leftrightarrow\beta)$

#### Teorema 2.5.1 (Leyes de De Morgan generalizadas)

- $\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha$
- $\neg(\exists x)\alpha\text{ eq }(\forall x)\neg\alpha$
- $(\forall x)\alpha\text{ eq }\neg(\exists x)\neg\alpha$
- $(\exists x)\alpha\text{ eq }\neg(\forall x)\neg\alpha$

Veamos algunas consideraciones previas:

- No hay ninguna suposición sobre las fórmulas involucradas, por lo que se asume que pueden tener variables libres: $FV(\alpha)=\{z_1,\ldots,z_n\}$.
- Esto hace que se deban hacer las clausuras antes de hacer las demostraciones.
- Lo que hace que se deban manejar varias constantes en el proceso de demostración.

##### Demostración: $\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha$

$$
\begin{aligned}
&\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha\\
&\iff\scriptstyle{(\text{definición de eq})}\\
&\models\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&(\overline{\forall}\mathcal{M})\mathcal{M}\models\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha\\
&\iff\scriptstyle{(\text{clausura y definición }\models)}\\
&(\overline{\forall}\mathcal{M})\mathcal{M}\models(\forall z_1)\ldots(\forall z_n)(\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha)\\
&\iff\scriptstyle{(\text{aplicando 2.4.5 }n\text{ veces})}\\
&(\overline{\forall}\mathcal{M})(\overline{\forall}a_1,\ldots,a_n\in|\mathcal{M}|)\mathcal{M}\models(\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha)[\overline{a_1},\ldots,\overline{a_n}/z_1,\ldots,z_n]\\
\end{aligned}
$$

Observemos que esto se vuelve muy extenso, muy rápido. En la siguiente clase veremos una forma de encarar esta demostración con una mejor estrategia.