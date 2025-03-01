# CLASE 5 - 26/02/2025

## Lógica proposicional

### Más ejemplos de ERP en $PROP$

#### $RANGO: PROP\to\mathbb{N}$

1. $RANGO(\varphi) = 0$ con $\varphi\in AT$
2. $RANGO((\alpha * \beta)) = 1 + \max\{RANGO(\alpha), RANGO(\beta)\}$ con $\alpha,\beta\in PROP$
3. $RANGO((\neg\alpha)) = 1 + RANGO(\alpha)$ con $\alpha\in PROP$

#### Sustitución $\rightarrow \_[\_/\_]: PROP\times PROP\times P\to PROP$

Observemos que $P$ es el conjunto donde solamente tenemos las proposiciones simples de $PROP$

1. $\bot[\varphi/p] = \bot$
2. $q[\varphi/p] =\begin{cases}\varphi\quad\text{ si }q = p\\q\quad\text{ si }q\neq p\end{cases}$
3. $(\alpha*\beta)[\varphi / p] = (\alpha[\varphi / p]*\beta[\varphi / p])$

**Observación:** recordar que $q$ es una proposición simple, es decir $q\in P$

##### Ejemplo

Veamos como hallar la siguiente sustitución: $(p_1\rightarrow((p_2\land p_1 )\lor \bot))[(p_3\land p_4)/p_1]$:

$$
\begin{aligned}
&(p_1\rightarrow((p_2\land p_1 )\lor \bot))[(p_3\land p_4)/p_1]\Rightarrow\\
&((p_3\land p_4)\rightarrow((p_2\land(p_3\land p_4))\lor \bot))
\end{aligned}
$$

Entonces con el ejemplo, observamos que los parámetros en orden, cumplen el siguiente rol:

1. Es la proposición compuesta sobre la que vamos a trabajar.
2. Es la proposición compuesta (o simple) que vamos a sustituir.
3. Es la proposición simple que vamos a buscar en la primer proposición compuesta para reemplazar en su lugar.

### Definición (secuencia de formación)

Una secuencia $\alpha_1,\alpha_2,\ldots,\alpha_n$ de palabras de $\Sigma_{PROP}^*$ es una secuencia de formación para $\alpha_n$ si y solamente si para todo $k\leq n$ se cumple que:

- $\alpha_k\in AT$ o,
- $\alpha_k = (\alpha_i*\alpha_j)$ con $i,j<k$ y $*\in C_2$ o,
- $\alpha_k = \neg\alpha_j$ con $j<k$

#### Ejemplos

1. $(p_1\land p_2)$ tiene una secuencia de formación $(p_1,p_2,(p_1\land p_2))$
2. $(p_1\land p_2)$ tiene una secuencia de formación $(p_1,p_2,p_3,\bot,(p_1\land p_2))$
3. $(p_1,p_3,\bot,(p_1\land p_2))$ no es una secuencia de formación de $(p_1\land p_2)$, ya que no tiene a $p_2$ en su secuencia.

Concluyendo, podemos decir que una secuencia de formación es una secuencia de palabras que nos permite llegar a una proposición compuesta, tienen que estar TODAS las proposiciones simples que se usan en la proposición compuesta. También observamos con el ejemplo (1) y (2) que para una proposición compuesta dada, no hay una única secuencia de formación.

### Definición (subfórmula)

Una fórmula $\varphi\in PROP$ es subfórmula de $\alpha\in PROP$ si y solamente si se cumple:

1. $\alpha = \varphi$ o,
2. $\alpha = (\varphi_1 * \varphi_2)$ con $*\in C_2; \varphi_1,\varphi_2\in PROP$ y $\varphi$ es subfórmula de $\varphi_1$ o,
3. $\alpha = (\varphi_1 * \varphi_2)$ con $*\in C_2; \varphi_1,\varphi_2\in PROP$ y $\varphi$ es subfórmula de $\varphi_2$ o,
4. $\alpha = (\neg\varphi_1)$ con $\varphi_1\in PROP$ y $\varphi$ es subfórmula de $\varphi_1$

#### Conjunto de subfórmulas

Veamos una función de $PROP$ para calcular la cantidad de subfórmulas de una proposición:

$SUB: PROP\to 2^{PROP}$

1. $SUB(\varphi) = \{\varphi\}$ con $\varphi\in AT$
2. $SUB((\alpha*\beta)) = SUB(\alpha)\cup SUB(\beta)\cup\{(\alpha*\beta)\}$
3. $SUB((\neg\alpha)) = SUB(\alpha)\cup\{(\neg\alpha)\}$

### Teorema

Veamos dos versiones de un teorema que relaciona la función que creamos para hallar todas las subfórmulas de una proposición, con la definición que dimos anteriormente de subfórmula.

1. $(\forall\alpha,\varphi\in PROP)\quad\varphi$ es subfórmula de $\alpha$ si y solamente si $\varphi\in SUB(\alpha)$

2. $(\forall\alpha\in PROP)\quad SUB(\alpha) = \{\varphi\in PROP:\varphi\text{ es subfórmula de }\alpha\}$

#### Demostración

La demostración de este teorema se hace por inducción sobre $PROP$, realmente lo que queremos probar es trivial, si observamos bien como construimos la función $SUB$. De todos modos está hecha en el libro y en la clase se ve.

### Teorema

$PROP$ es el conjunto de todas las palabras de $\Sigma^*_{PROP}$ que tienen una secuencia de formación.

#### Corolario

Sea $\mathcal{P}$ una propiedad de $\Sigma^*_{PROP}$. Para demostrar que: 
para todo $\alpha\in PROP$ se cumple $\mathcal{P}(\alpha)$

Podemos hacer la prueba:
- por inducción primitiva
- por inducción sobre la longitud de la secuencia de formación de $\alpha$

### Convenciones sintácticas

Definimos $PROP$ utilizando paréntesis para todas las fórmulas no atómicas, esto por que es la única fórma de que el lenguaje sea libre. A la hora de trabajar con $PROP$ vamos a usar las siguientes convenciones, para no utilizar todos los paréntesis:

- Omitimos los paréntesis exteriores de una fórmula, y los que rodean a $\neg$.
- Los conectivos $\land,\lor$ tienen la misma precedencia.
- Los conectivos $\rightarrow$ y $\leftrightarrow$ tienen la misma precedencia.
- El conectivo $\neg$ tiene la mayor precedencia de todos los conectivos.
- Los conectivos $\rightarrow$ y $\leftrightarrow$ tienen la menor precedencia de todos los conectivos.
- Los conectivos de igual precedencia se asocian a la derecha.

#### Ejemplos

- $\neg\neg p_1$ abrevia a $(\neg(\neg p_1))$
- $p_1\rightarrow p_2 \leftrightarrow p_3$ abrevia a $(p_1\rightarrow (p_2\leftrightarrow p_3))$
- $p_2 \land\bot\lor\neg(p_3\rightarrow p_1)$ abrevia a $(p_2\land(\bot\lor(\neg(p_3\rightarrow p_1))))$

**ATENCIÓN:** Cuando tenemos igual precedencia, agrupamos POR LA DERECHA, esto es opuesto a lo tradicional, por lo tanto MUY importante de recordar.