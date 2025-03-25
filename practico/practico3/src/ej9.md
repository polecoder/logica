# Ejercicio 9

## Consigna

(a) Denotamos por "$|$" la barra de Sheffer cuya función de valuación es la siguiente:

$$
v(\varphi | \psi) = 0 \text{ si y solo si } v(\varphi) = v(\psi) = 1
$$

Denotamos por "$\downarrow$" el conectivo cuya función de valuación es la siguiente:

$$
v(\varphi \downarrow \psi) = 1 \text{ si y solo si } v(\varphi) = v(\psi) = 0 \text{ (ni } \varphi \text{ ni } \psi)
$$

Demuestre que los conjuntos de conectivos $\{|\}$ y $\{\downarrow\}$ son funcionalmente completos. (Sugerencia: Pruebe que $(\neg p_1) \equiv (p_1 | p_1)$ y que $(\neg p_1) \equiv (p_1 \downarrow p_1)$)

(b) Considere la conectiva ternaria $\$$ cuya función de valuación es la siguiente (conectiva mayoría):

$$
v(\$(\varphi_1, \varphi_2, \varphi_3)) = 1 \text{ si y solo si } v(\varphi_1) + v(\varphi_2) + v(\varphi_3) \geq 2
$$

Exprese $\$$ en términos de $\lor$ y $\neg$.

(c) Considere el conectivo $\#$ cuya función de valuación es la siguiente:

$$
v(\varphi \# \psi) = 1 \text{ si y solo si } v(\varphi) \neq v(\psi)
$$

Exprese $\#$ en términos de $\lor$ y $\neg$.

(d) Demuestre que el conjunto $\{\land, \bot\}$ no es funcionalmente completo. (Sugerencia: Pruebe que ninguna fórmula que use solamente esos conectivos puede ser una tautología).

## Resolución (parte a)

La idea para demostrar esto es demostrar que podemos expresar cualquier fórmula de $PROP$ reducido a un conjunto completo de conectivos conocido, solo usando los conectivos "$|$" y "$\downarrow$" respectivamente. Es decir que:

$$
(\forall\alpha\in PROP_{\{\neg,\land\}})(\exists\beta\in PROP_{\{|\}})\text{ tal que }\alpha\text{ eq }\beta
$$

Usando en este caso el conjunto de conectivos completo: $\{\neg,\land\}$

### Conectivo "$|$"

Definamos $PROP_{\{|\}}$ para poder trabajar sobre él.

1. $p\in PROP_{\{|\}}$ con $p\in P$
2. Si $\alpha,\beta\in PROP_{\{|\}}$, entonces $(\alpha|\beta)\in PROP_{\{|\}}$

Definamos también $PROP_{\{\neg,\land\}}$ para poder trabajar con el PIP sobre él.

1. $p\in PROP_{\{\neg,\land\}}$ con $p\in P$
2. Si $\alpha\in PROP_{\{\neg,\land\}}$, entonces $\neg\alpha\in PROP_{\{\neg,\land\}}$
3. Si $\alpha,\beta\in PROP_{\{\neg,\land\}}$, entonces $\alpha\land\beta\in PROP_{\{\neg,\land\}}$

#### Lemas

##### Lema \#1

$$(\neg \varphi)\equiv(\varphi|\varphi)$$

**Demostración:**
$v(\varphi|\varphi) = 0$ sii $v(\varphi) = 1$ y en cualquier otro caso vale 1. Esto coincide con $\neg\varphi$

##### Lema \#2

$$(\alpha\land\beta)\equiv(\alpha|\beta)|(\alpha|\beta)$$

**Demostración:**
$v(\alpha\land\beta) = v(\neg(\alpha|\beta))$ porque $v(\neg(\alpha|\beta)) = 1$ sii $v(\alpha) = v(\beta) = 1$.
Usando el lema #1 tenemos que:

$$
\begin{aligned}
v(\neg(\alpha|\beta)) &= v((\alpha|\beta)|(\alpha|\beta))
\end{aligned}
$$

#### Demostración

Enunciemos la propiedad $P(\varphi)$ que queremos demostrar:

$$
P(\varphi): (\exists\beta\in PROP_{\{|\}})\text{ tal que }\varphi\text{ eq }\beta
$$

##### PASO BASE

$P(p_i): (\exists\beta\in PROP_{\{|\}})\text{ tal que }p_i\text{ eq }\beta$

Esto es directo porque por la definición de $PROP_{\{|\}}$, $p_i\in PROP_{\{|\}}$

##### PASO INDUCTIVO

###### PARTE 1

(H) $P(\alpha): (\exists\alpha'\in PROP_{\{|\}})\text{ tal que }\alpha\text{ eq }\alpha'$
(H) $P(\beta): (\exists\beta'\in PROP_{\{|\}})\text{ tal que }\beta\text{ eq }\beta'$

(T) $P(\alpha\land\beta): (\exists\psi\in PROP_{\{|\}})\text{ tal que }\alpha\land\beta\text{ eq }\psi$

$$
\begin{aligned}
&\alpha\text{ eq }\alpha'\text{ y }\beta\text{ eq }\beta'\\
&\Rightarrow {\scriptstyle \text{(por sustitución por fórmulas equivalentes)}}\\
&(\alpha\land\beta)\text{ eq }(\alpha'\land\beta')\\
&\Rightarrow {\scriptstyle \text{(por lema \#2)}}\\
&(\alpha'\land\beta')\text{ eq }((\alpha'|\beta')|(\alpha'|\beta'))\\
\end{aligned}
$$

Cómo este elemento $((\alpha'|\beta')|(\alpha'|\beta'))$ pertenece a $PROP_{\{|\}}$, hemos demostrado que $P(\alpha\land\beta)$ se cumple.

###### PARTE 2

(H) $P(\varphi): (\exists\varphi'\in PROP_{\{|\}})\text{ tal que }\varphi\text{ eq }\varphi'$

(T) $P(\neg\varphi): (\exists\psi\in PROP_{\{|\}})\text{ tal que }\neg\varphi\text{ eq }\psi$

$$
\begin{aligned}
&\varphi\text{ eq }\varphi'\\
&\Rightarrow {\scriptstyle \text{(por sustitución por fórmulas equivalentes)}}\\
&\neg\varphi\text{ eq }\neg\varphi'\\
&\Rightarrow {\scriptstyle \text{(por lema \#1)}}\\
&\neg\varphi'\text{ eq }(\varphi|\varphi)\\
\end{aligned}
$$

Cómo este elemento $(\varphi|\varphi)$ pertenece a $PROP_{\{|\}}$, hemos demostrado que $P(\neg\varphi)$ se cumple.

### Conectivo "$\downarrow$"

Definamos $PROP_{\{\downarrow\}}$ para poder trabajar sobre él.

1. $p\in PROP_{\{\downarrow\}}$ con $p\in P$
2. Si $\alpha,\beta\in PROP_{\{\downarrow\}}$, entonces $(\alpha\downarrow\beta)\in PROP_{\{\downarrow\}}$

Definamos también $PROP_{\{\neg,\lor\}}$ para poder trabajar con el PIP sobre él.

1. $p\in PROP_{\{\neg,\lor\}}$ con $p\in P$
2. Si $\alpha\in PROP_{\{\neg,\lor\}}$, entonces $\neg\alpha\in PROP_{\{\neg,\lor\}}$
3. Si $\alpha,\beta\in PROP_{\{\neg,\lor\}}$, entonces $\alpha\lor\beta\in PROP_{\{\neg,\lor\}}$

#### Lemas

##### Lema \#1

$$(\neg \varphi)\equiv(\varphi\downarrow\varphi)$$

**Demostración:**
$v(\varphi\downarrow\varphi) = 1$ sii $v(\varphi) = 0$ y en cualquier otro caso vale 1. Esto coincide con $\neg\varphi$

##### Lema \#2

$$(\alpha\lor\beta)\equiv((\alpha\downarrow\beta)\downarrow(\alpha\downarrow\beta))$$

**Demostración:**
$v(\alpha\lor\beta) = v(\neg(\alpha\downarrow\beta))$ porque $v(\neg(\alpha\downarrow\beta)) = 0$ sii $v(\alpha) = v(\beta) = 0$, en todos los demás casos $v(\neg(\alpha\downarrow\beta)) = 1$.
Usando el lema #1 tenemos que:

$$
\begin{aligned}
v(\neg(\alpha\downarrow\beta)) &= v((\alpha\downarrow\beta)\downarrow(\alpha\downarrow\beta))
\end{aligned}
$$

#### Demostración

Enunciemos la propiedad $P(\varphi)$ que queremos demostrar:

$$
P(\varphi): (\exists\beta\in PROP_{\{\downarrow\}})\text{ tal que }\varphi\text{ eq }\beta
$$

##### PASO BASE

$P(p_i): (\exists\beta\in PROP_{\{\downarrow\}})\text{ tal que }p_i\text{ eq }\beta$

Esto es directo porque por la definición de $PROP_{\{\downarrow\}}$, $p_i\in PROP_{\{\downarrow\}}$

##### PASO INDUCTIVO

###### PARTE 1

(H) $P(\alpha): (\exists\alpha'\in PROP_{\{\downarrow\}})\text{ tal que }\alpha\text{ eq }\alpha'$
(H) $P(\beta): (\exists\beta'\in PROP_{\{\downarrow\}})\text{ tal que }\beta\text{ eq }\beta'$

(T) $P(\alpha\lor\beta): (\exists\psi\in PROP_{\{\downarrow\}})\text{ tal que }\alpha\lor\beta\text{ eq }\psi$

$$
\begin{aligned}
&\alpha\text{ eq }\alpha'\text{ y }\beta\text{ eq }\beta'\\
&\Rightarrow {\scriptstyle \text{(por sustitución por fórmulas equivalentes)}}\\
&(\alpha\lor\beta)\text{ eq }(\alpha'\lor\beta')\\
&\Rightarrow {\scriptstyle \text{(por lema \#2)}}\\
&(\alpha'\lor\beta')\text{ eq }((\alpha'\downarrow\beta')\downarrow(\alpha'\downarrow\beta'))\\
\end{aligned}
$$

Cómo este elemento $((\alpha'\downarrow\beta')\downarrow(\alpha'\downarrow\beta'))$ pertenece a $PROP_{\{\downarrow\}}$, hemos demostrado que $P(\alpha\lor\beta)$ se cumple.

###### PARTE 2

(H) $P(\varphi): (\exists\varphi'\in PROP_{\{\downarrow\}})\text{ tal que }\varphi\text{ eq }\varphi'$

(T) $P(\neg\varphi): (\exists\psi\in PROP_{\{\downarrow\}})\text{ tal que }\neg\varphi\text{ eq }\psi$

$$
\begin{aligned}
&\varphi\text{ eq }\varphi'\\
&\Rightarrow {\scriptstyle \text{(por sustitución por fórmulas equivalentes)}}\\
&\neg\varphi\text{ eq }\neg\varphi'\\
&\Rightarrow {\scriptstyle \text{(por lema \#1)}}\\
&\neg\varphi'\text{ eq }(\varphi\downarrow\varphi)\\
\end{aligned}
$$

Cómo este elemento $(\varphi\downarrow\varphi)$ pertenece a $PROP_{\{\downarrow\}}$, hemos demostrado que $P(\neg\varphi)$ se cumple.

## Resolución (parte b)

La estrategia que usaremos para esta parte consiste en primero hallar una fórmula de $PROP$ para expresar $\$$ en términos de todos los conectivos, y luego encontrar una fórmula equivalente a la última que tenga solo $\lor$ y $\neg$.

### Hallar fórmula de $PROP$ para $\$$

$$
\$(\varphi_1, \varphi_2, \varphi_3) = 1 \text{ si y solo si } v(\varphi_1) + v(\varphi_2) + v(\varphi_3) \geq 2
$$

Analicemos primero los casos donde $\$(\varphi_1,\varphi_2,\varphi_3)$ es verdadera:

1. $\varphi_1 = 1, \varphi_2 = 1, \varphi_3 = 1$
2. $\varphi_1 = 1, \varphi_2 = 1, \varphi_3 = 0$
3. $\varphi_1 = 1, \varphi_2 = 0, \varphi_3 = 1$
4. $\varphi_1 = 0, \varphi_2 = 1, \varphi_3 = 1$

Busquemos una fórmula para representar cada una de estas situaciones:

1. Puede ser cualquier fórmula de las que vemos posteriormente porque todas valen 1.
2. $(\varphi_1\land\varphi_2)$
3. $(\varphi_1\land\varphi_3)$
4. $(\varphi_2\land\varphi_3)$

Por lo tanto, la fórmula $\alpha\in PROP$ que representa a $\$$ es:

$$
\alpha=(\varphi_1\land\varphi_2)\lor(\varphi_1\land\varphi_3)\lor(\varphi_2\land\varphi_3)
$$

La intuición de la fórmula que encontramos es que cuando pase alguno de los casos, quiero devolver verdadero. Si no pasa ninguno de ellos entonces tendré que devolver falso.

### Hallar fórmula de $PROP$ para $\$$ en términos de $\lor$ y $\neg$

En esta parte tenemos que usar fórmulas equivalentes para reemplazar el $\land$. Usemos la siguiente fórmula equivalente conocida:

$$
\alpha\land\beta\equiv\neg(\neg\alpha\lor\neg\beta)
$$

Reemplazando en la fórmula $\alpha$ que encontramos anteriormente:

$$
\alpha=\neg(\neg\varphi_1\lor\neg\varphi_2)\lor\neg(\neg\varphi_1\lor\neg\varphi_3)\lor\neg(\neg\varphi_2\lor\neg\varphi_3)\\
$$

## Resolución (parte c)

Usaremos la misma estrategia que para la parte anterior.

### Hallar fórmula de $PROP$ para $\#$

$$
v(\varphi \# \psi) = 1 \text{ si y solo si } v(\varphi) \neq v(\psi)
$$

Analicemos primero los casos donde $(\varphi\#\psi)$ es verdadera:

1. $\varphi = 1, \psi = 0$
2. $\varphi = 0, \psi = 1$

Busquemos una fórmula para representar cada una de estas situaciones:

1. $(\varphi\land\neg\psi)$
2. $(\neg\varphi\land\psi)$

Por lo tanto, la fórmula $\alpha\in PROP$ que representa a $\#$ es:

$$
\alpha=(\varphi\land\neg\psi)\lor(\neg\varphi\land\psi)
$$

### Hallar fórmula de $PROP$ para $\#$ en términos de $\lor$ y $\neg$

En esta parte tenemos que usar fórmulas equivalentes para reemplazar el $\land$. Usemos la siguiente fórmula equivalente conocida:

$$
\alpha\land\beta\equiv\neg(\neg\alpha\lor\neg\beta)
$$

Reemplazando en la fórmula $\alpha$ que encontramos anteriormente:

$$
\alpha=\neg(\neg\varphi\lor\psi)\lor\neg(\varphi\lor\neg\psi)\\
$$

## Resolución (parte d)

La estrategia para esta parte es seguir la sugerencia dada en la letra.
Queremos probar entonces que ninguna fórmula que use solamente los conectivos $\land$ y $\bot$ puede ser una tautología. Traduciendo esto a una propiedad $P$, tenemos que:

$$P(\varphi): \exists v\in Val\mid v(\varphi) = 0 \quad(\forall\varphi\in PROP_{\{\land,\bot\}})$$

Usemos el PIP sobre $PROP_{\{\land,\bot\}}$ para demostrar esto.

### Demostración

#### PASO BASE

##### PARTE 1

$P(\bot): \exists v\in Val\mid v(\bot) = 0$

Esto es trivialmente cierto para todas las valuaciones $v\in Val$ por la definición de lo que es una valuación.

##### PARTE 2

$P(p_i): \exists v\in Val\mid v(p_i) = 0$

Basta con tomar una valuación $v$ tal que $v(p_i) = 0$. Por lo que este paso también se cumple.

#### PASO INDUCTIVO

(H) $P(\alpha): \exists v\in Val\mid v(\alpha) = 0$
(H) $P(\beta): \exists v\in Val\mid v(\beta) = 0$

(T) $P(\alpha\land\beta): \exists v\in Val\mid v(\alpha\land\beta) = 0$

Sea $v$ una valuación cualquiera que cumple con las hipótesis inductivas, veamos que podemos decir sobre $v(\alpha\land\beta)$:

$$
\begin{aligned}
&v(\alpha\land\beta)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&min\{v(\alpha),v(\beta)\}\\
&= {\scriptstyle \text{(por hipótesis inductiva)}}\\
&min\{0,0\}\\
&= 0
\end{aligned}
$$

Entonces, $v$ es una valuación que cumple con la tesis. Por lo tanto, hemos demostrado que $P(\alpha\land\beta)$ se cumple.

Esto prueba la propiedad $\forall\varphi\in PROP_{\{\land,\bot\}}$, es decir que no existen fórmulas que usen solamente los conectivos $\land$ y $\bot$ que sean tautologías. Por lo tanto, el conjunto $\{\land,\bot\}$ no es funcionalmente completo.
