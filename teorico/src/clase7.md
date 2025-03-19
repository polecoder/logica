# CLASE 7 - 18/03/2025

## Semántica proposicional (continuación)

### Más aplicaciones y usos directos de la definición de valuación

#### Investigar $\models (p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)$

Sea $v$ una valuación, luego:

$$
\begin{aligned}
&v((p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)) = 1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&v(p_1 \lor p_2) = v(\neg p_1 \rightarrow p_2)\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&max\{v(p_1), v(p_2)\} = max\{1-v(\neg p_1), v(p_2)\}\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&max\{v(p_1), v(p_2)\} = max\{1-(1-v(p_1)), v(p_2)\}\\
&\Rightarrow {\scriptstyle \text{(operatoria)}}\\
&max\{v(p_1), v(p_2)\} = max\{v(p_1), v(p_2)\}\\
\end{aligned}
$$

Lo cual es obviamente cierto, por lo que efectivamente $(p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)$ es tautología.

#### Investigar $\models p_0\rightarrow p_1$

Sea $v$ una valuación, luego:

$$
\begin{aligned}
&v(p_0\rightarrow p_1)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&max\{1-v(p_0), v(p_1)\}
\end{aligned}
$$

Observemos que si $v(p_0) = 1$ y $v(p_1) = 0$ tenemos que $v(p_0\rightarrow p_1) = 0$.
Como existe una valuación que cumple que $v(p_0\rightarrow p_1) = 0$, concluímos que $\not\models p_0\rightarrow p_1$

#### Investigar $\varphi,\psi\models\varphi\land\psi$

Sea $v$ una valuación tal que $v(\varphi) = 1$ y $v(\psi) = 1$, luego:

$$
\begin{aligned}
&v(\varphi\land\psi)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&min\{v(\varphi), v(\psi)\}
\end{aligned}
$$

Como cualquier valuación dada en este contexto cumple que $v(\varphi) = 1$ y $v(\psi) = 1$, tendremos que $min\{v(\varphi), v(\psi)\} = 1$, entonces podemos concluir que $(\forall \varphi,\psi)\varphi,\psi\models\varphi\land\psi$

### Tablas de verdad

#### Investigar $p_0\rightarrow p_0$

Construimos una tabla de verdad considerando todos los valores posibles que pueden tomar las letras en juego.

$$
\begin{array}{c|c}
p_0 & p_0\rightarrow p_0\\
\hline
0 & 1\\
1 & 1\\
\end{array}
$$

Como cualquier valuación cumple $v(p_0\rightarrow p_0) = 1$ concluimos que $\models p_0\rightarrow p_0$

**Observación:** Esto es el mismo problema anterior pero lo solucionamos de otra forma. Es importante entender que las tablas de verdad solo las puedo utilizar cuando conozco TODAS las letras proposicionales que utilizo.

#### Investigar $\models (p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)$

$$
\begin{array}{c|c|c|c|c|c}
p_1 & p_2 & (p_1\lor p_2) & \neg p_1 & \neg p_1\rightarrow p_2 & (p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)\\
\hline
0 & 0 & 0 & 1 & 0 & 1\\
0 & 1 & 1 & 1 & 1 & 1\\
1 & 0 & 1 & 0 & 1 & 1\\
1 & 1 & 1 & 0 & 1 & 1\\
\end{array}
$$

Como cualquier valuación $v$ cumple que $v((p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)) = 1$ podemos concluir que $\models (p_1 \lor p_2) \leftrightarrow (\neg p_1 \rightarrow p_2)$.

### Tableau semántico

En esta clase se introduce este concepto, que consiste en utilizar un árbol para evaluar un juicio. No tomaré notas sobre este tema, ya que no hay forma de que quede prolijo en este ámbito.
La teoría sobre esto se encuentra en las diapositivas correspondientes a la clase.
De todos modos es importante observar que el principal valor que aporta es poder determinar a que corresponde un juicio donde las metavariables son proposiciones, y no letras proposicionales, esto también se puede hacer directamente con la definición de valuación.

### Tautología, contradicción y contingencia

- Tautología: Fórmulas que son verdaderas en todas las valuaciones
- Contingencia: Fórmulas que son verdaderas en algunas valuaciones, y falsas en otras
- Contradicción: Fórmulas que son falsas en todas las valuaciones

Cuando se trabaja con implicaciones, puede ser más simple analizar cuando NO es tautología.

Cuando se trabaja con consecuencias lógicas, puede ser más simple analizar cuando NO se cumple

### Equivalencia entre proposiciones

#### Definición

Decimos que dos proposiciones $\alpha$ y $\beta$ son equivalente sii: $\alpha\leftrightarrow\beta$ es una tautología.
Cuando esto sucede lo denotamos como "$\alpha\text{ eq }\beta$"

**Observación:** Se cumple $\alpha\text{ eq }\beta$ sii para cualquier valuación $v: PROP\to\{0,1\}$ se cumple $v(\alpha) = v(\beta)$

##### Lema

La relación que definimos "eq" es una relación de equivalencia en $PROP\times PROP$

#### Aplicaciones

Esta noción nos da un montón de aplicaciones, veamos algunas de ellas por categorías:

##### Leyes algebraicas

- $\models (\alpha\lor\beta)\lor\gamma\leftrightarrow \alpha\lor\beta\lor\gamma$
- $\models\alpha\lor\beta\leftrightarrow\beta\lor\alpha$
- $\models\alpha\lor\alpha\leftrightarrow\alpha$
- $\models\alpha\lor(\alpha\land\beta)\leftrightarrow\alpha$
- $\models\alpha\lor(\beta\land\gamma)\leftrightarrow(\alpha\lor\beta)\land(\alpha\lor\gamma)$
- $\models\neg(\alpha\lor\beta)\leftrightarrow\neg\alpha\land\neg\beta$

Con nuestra nueva noción podemos decir que:

- $(\alpha\lor\beta)\lor\gamma\text{ eq } \alpha\lor\beta\lor\gamma$
- $\alpha\lor\beta\text{ eq }\beta\lor\alpha$
- $\alpha\lor\alpha\text{ eq }\alpha$
- $\alpha\lor(\alpha\land\beta)\text{ eq }\alpha$
- $\alpha\lor(\beta\land\gamma)\text{ eq }(\alpha\lor\beta)\land(\alpha\lor\gamma)$
- $\neg(\alpha\lor\beta)\text{ eq }\neg\alpha\land\neg\beta$

Y muchas más... (ubicadas en las diapositivas correspondientes a esta clase también)

##### Equivalencias entre conectivos

- $\alpha\leftrightarrow\beta\text{ eq }(\alpha\rightarrow\beta)\land(\beta\rightarrow\alpha)$
- $\alpha\rightarrow\beta\text{ eq }\neg\alpha\lor\beta$
- $\alpha\lor\beta\text{ eq }\neg\alpha\rightarrow\beta$
- $\alpha\lor\beta\text{ eq }\neg(\neg\alpha\land\neg\beta)$
- $\alpha\land\beta\text{ eq }\neg(\neg\alpha\lor\neg\beta)$
- $\neg\alpha\text{ eq }\alpha\rightarrow\bot$
- $\bot\text{ eq }\alpha\land\neg\alpha$

Estas aplicaciones se mirarán con más detalle en los ejercicios del práctico. Entiendo que obviamente la idea no es memorizarse esto, cada una de ellas se puede demostrar usando los métodos que aprendimos anteriormente.

### Sustitución por fórmulas equivalentes

Recordemos la definición de la función de sustitución:

#### $\_[\_/\_]: PROP\times PROP\times P\to PROP$

1. $\bot[\varphi/p] = \bot$
2. $q[\varphi/p] =\begin{cases}\varphi\quad\text{ si }q = p\\q\quad\text{ si }q\neq p\end{cases}$
3. $(\alpha*\beta)[\varphi / p] = (\alpha[\varphi / p]*\beta[\varphi / p])$

- Si $\alpha_1,\alpha_2$ son fórmulas equivalentes, entonces puedo sustituir una letra proposicional en una fórmula $\beta$ cualquiera por $\alpha_1$ y $\alpha_2$ y obtener fórmulas equivalentes.

#### Teorema de sustitución

(H) $\alpha_1\text{ eq }\alpha_2$
(T) Para cualesquiera $\beta\in PROP$ y $p\in P$, se cumple:
$$\beta[\alpha_1/p]\text{ eq } B[\alpha_2/p]$$

Esta es otra herramienta con la que podemos evaluar juicios, podemos reducir determinadas proposiciones, a proposiciones equivalentes pero más simples.

### Conectivas n-arias

Sea $f: \{0,1\}^n\to \{0,1\}$. Una conectiva lógica n-aria $\$$ queda definida por la función $f$ si para cualquier valuación $v$ se cumple:

$$
(\forall q_1,q_2,\ldots,q_n\in P)\quad v(\$(q_1,\ldots,q_n)) = f(v(q_1),\ldots,v(q_n))
$$

Es decir que, la valuación de la conectiva lógica $\$$ de n parámetros queda definida por $f$ si podemos describirla a partir de las valuaciones de las letras proposicionales que la componen.

De esto depende la siguiente definición:

#### Conjuntos completos de conectivos

$K$ es un conjunto completo de conectivos si para cada conectivo n-ario $\$$ y letras proposicionales $q_1,\ldots,q_n$ existe una fórmula $\alpha\in PROP$ cuyos conectivos están en $K$, sus letras en $\{q_1,\ldots,q_n\}$, y tal que $\alpha\text{ eq }\$(q_1,\ldots,q_n)$

#### Ejemplos de conjuntos completos de conectivos:

- $\{\neg,\lor\}$
- $\{\neg,\land\}$
- $\{\bot,\rightarrow\}$
- $\{\neg,\rightarrow\}$

### Formas normales

#### Conjunciones y disyunciones

Entendemos y denotamos una conjunción como:

1. $\bigwedge_{i\leq0}\varphi_i = \varphi_i$
2. $\bigwedge_{i\leq n+1}\varphi_i = \bigwedge_{i\leq n}\varphi_i\land \varphi_{n+1}$

Entendemos y denotamos una disyunción como:

1. $\bigvee_{i\leq0}\varphi_i = \varphi_i$
2. $\bigvee_{i\leq n+1}\varphi_i = \bigvee_{i\leq n}\varphi_i\lor \varphi_{n+1}$

#### Forma normal conjunctiva

Una fórmula está en forma normal conjuntiva sii es de la forma $\bigwedge_{i\leq n}(\bigvee_{j\leq m_i}\varphi_{ij})$ donde cada $\varphi_{ij}$ es una fórmula atómica o la negación de una fórmula atómica.

**IDEA:** Esto es que básicamente tenemos una fórmula grande juntada con $\land$, compuesta por subfórmulas que solo usan $\neg,\lor$

#### Forma normal disyuntiva

Una fórmula está en forma normal disyuntiva sii es de la forma $\bigvee_{i\leq n}(\bigwedge_{j\leq m_i}\varphi_{ij})$ donde cada $\varphi_{ij}$ es una fórmula atómica o la negación de una fórmula atómica.

**IDEA:** Esto es que básicamente tenemos una fórmula grande juntada con $\lor$, compuesta por subfórmulas que solo usan $\neg,\land$