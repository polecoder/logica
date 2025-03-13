# CLASE 6 - 13/03/2025

## Semántica proposicional

Veamos la diferencia entre sintáxis, semántica e interpretación de un lenguaje:

- **Sintáxis**: Describe el conjunto de las frases válidas del lenguaje, típicamente como un conjunto inductivo
- **Semántica**: Es el significado de las frases válidas del lenguaje. Usualmente involucra diversos conjuntos y relaciones entre ellos
- **Interpretación**: Es un mecanismo que permite la asociación entre los elementos de la sintaxis (frases del lenguaje) y los elementos de la semántica

Veamos estos conceptos aplicado al lenguaje $PROP$:

- **Sintáxis**: Se define un conjunto inductivo, con ciertas fórmulas base (letras proposicionales) y ciertos operadores que construyen nuevas fórmulas
- **Semántica**: El conjunto $\{0, 1\}:(\{falso, verdadero\})$
- **Interpretación**: Función recursiva que para cada elemento de $PROP$ devuelve el valor $0$ o $1$ en base al valor de las letras proposicionales

### Valuación (Intuición)

- La semántica de una palabra (fórmula) de PROP está dada por su valor de verdad (o sea, si es verdadera o falsa).
- Ese valor se obtiene aplicando una función a la fórmula que se desea evaluar
- Cada función representa un estado de la realidad (o mundo).
    - $v(p_0) = 0, v(p_1) = 1, \ldots$ es la representación de un mundo, y $v(p_0) = 1, \ldots , v(p_2) = 1$ es una representación de otro mundo distinto
    - En cada mundo cada proposición de $PROP$ puede representar una afirmación distinta de la realidad

### Semántica de $PROP$ (Intuición)

La semántica de una palabra (fórmula) de PROP está dada por su valor de verdad (o sea, si es verdadera o falsa). Ese valor se obtiene aplicando una función a la fórmula que se desea evaluar. Cada función representa un estado del universo que se obtiene de la siguiente forma:

- En cada función, cada una de las letras proposicionales puede tomar un valor de verdad
- $\bot$ es falsa en cualquier función
- Los valores de verdad de las fórmulas atómicas se extienden a las fórmulas no atómicas de acuerdo al significado de los conectivos que la forman
- Las letras proposicionales tienen un valor de verdad conocido
- Se abstraen las proposiciones simples a letras
- La frase "Los perros comen salchichas con
tuco" colapsa a, por ejemplo, $p_0$
- Y si esa frase es verdad en una situación $v$, diremos que $v(p_0) = 1$. Y si es falsa, diremos que $v(p_0) = 0$.
- $PROP$ está definido inductivamente
- La semántica está dada por los valores de verdad de las proposiciones, ya sean simples o complejas
- Se buscará la forma de construir esa semántica teniendo en cuenta que:
    - Las letras proposicionales pueden tomar cualquier valor
    - El valor de las letras proposicionales se "transmite", lo que permite calcular el valor de las proposiciones complejas en función del valor de las proposiciones más simples

#### Significado de algunos conectivos

- El dos es par o impar. **VERDAD**
- El dos es par o natural. **VERDAD**
- Si $n$ es múltiplo de $6$, entonces $4$ es par. **VERDAD**
- Si $4$ es impar, entonces $3$ es par. **VERDAD**

### Valuación (definición)

Una función $v: PROP\to \{0,1\}$ es una valuación si satisface:

- $v(\bot) = 0$
- $v(\alpha\lor\beta) = min\{v(\alpha),v(\beta)\}$
- $v(\alpha\land\beta) = max\{v(\alpha),v(\beta)\}$
- $v(\alpha\rightarrow\beta) = max\{1-v(\alpha),v(\beta)\}$
- $v(\alpha\leftrightarrow\beta) = 1\iff v(\alpha)=v(\beta)$
- $v(\neg\alpha) = 1-v(\alpha)$

### Teorema

El valor de verdad de los átomos, determina una única valuación (el valor para cualquier fórmula)

(H) Sea $w: P\to \{0,1\}$
(T) Existe una única valuación $v:PROP\to\{0,1\}$ tal que $v(p) = w(p)\quad\forall p\in P$

#### Demostración

Consideremos una función $v:PROP\to\{0,1\}$ definida por recursión primitiva tal que:

- $v(p) = w(p)$ para todo $p\in P$
- $v$ es una valuación

Esta función existe, y es única porque fue definida por recursión primitiva. Además es valuación (por su propia definición). $\blacksquare$

### Lema

El valor de verdad de una fórmula depende únicamente de los valores de verdad de sus letras proposicionales.

(H) Sea $\alpha\in PROP$. Sean $v,v'$ dos valuaciones tales que $v(p)=v'(p)$ para todo $p\in P$ que ocurre en $\alpha$

(T) Entonces $v(\alpha) = v'(\alpha)$

### Tautología y consecuencia lógica (definición)

- **Tautología**: Decimos que $\alpha\in PROP$ es una tautología sii para cualquier valuación $v$ se cumple que $v(\alpha) = 1$
- **Consecuencia lógica**: Dadas $\Gamma\subseteq PROP$ y $\alpha\in PROP$, decimos que $\alpha$ es consecuencia lógica de $\Gamma$ sii para cualquier valuación $v$:

    - Si $(\forall\gamma\in\Gamma)v(\gamma)=1$, entonces $v(\alpha)=1$

#### Notación

- $\Gamma\models\alpha$ se lee "$\alpha$ es consecuencia lógica de $\Gamma$"
- $\gamma_1,\ldots,\gamma_n\models\alpha$ se lee $\{\gamma_1,\ldots,\gamma_n\}\models\alpha$
- $\models\alpha$ se lee $\{\}\models\alpha$
- $\models\alpha$ se lee "$\alpha$ es tautología"

### Aplicaciones

#### Investigar $\models(p_0\rightarrow p_0)$

Sea $v$ una valuación cualquiera, luego:

$$
\begin{aligned}
&v(p_0\rightarrow p_0)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&max\{1-v(p_0), v(p_0)\}\\
&= {\scriptstyle (v(p_0)\in\{0,1\})}\\
&1
\end{aligned}
$$

Como cualquier valuación $v$ cumple $v(p_0\rightarrow p_0) = 1$, concluimos que $\models(p_0\rightarrow p_0)$

#### Investigar $\models(\varphi\rightarrow \varphi)$

Sea $v$ una valuación cualquiera, luego:

$$
\begin{aligned}
&v(\varphi\rightarrow \varphi)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&max\{1-v(\varphi), v(\varphi)\}\\
&= {\scriptstyle (v(\varphi)\in\{0,1\})}\\
&1
\end{aligned}
$$

Como cualquier valuación $v$ cumple $v(\varphi\rightarrow \varphi) = 1$, concluimos que $\models(\varphi\rightarrow \varphi)$