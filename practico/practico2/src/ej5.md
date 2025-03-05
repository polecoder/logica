# Ejercicio 5

## Consigna

(a) Enumere todas las subfórmulas de las proposiciones del Ejercicio 2.

(b) Defina la función $\text{sub} : \text{PROP} \to 2^{\text{PROP}}$, que a cada proposición $\varphi$ le asigna el conjunto de sus subfórmulas.

(c) Demuestre que la relación "ser subfórmula de" es transitiva.

## Resolución (parte a)

### Proposición 1

$$\neg(\neg(\neg\bot))$$

Las subfórmulas son:

- $\neg(\neg(\neg\bot))$
- $\neg(\neg\bot)$
- $\neg\bot$
- $\bot$

Es decir, tenemos 4 subfórmulas.

### Proposición 2

$$(p_0\rightarrow\bot)\rightarrow((p_0\leftrightarrow p_1)\land p_5)$$

Las subfórmulas son:

- $(p_0\rightarrow\bot)\rightarrow((p_0\leftrightarrow p_1)\land p_5)$
- $(p_0\rightarrow\bot)$
- $p_0$
- $\bot$
- $(p_0\leftrightarrow p_1)\land p_5$
- $(p_0\leftrightarrow p_1)$
- $p_0$
- $p_1$
- $p_5$

Es decir, tenemos 9 subfórmulas.

### Proposición 3

$$\neg(\neg p_1\rightarrow \neg p_1)$$

Las subfórmulas son:

- $\neg(\neg p_1\rightarrow \neg p_1)$
- $\neg p_1\rightarrow \neg p_1$
- $\neg p_1$
- $p_1$

Es decir, tenemos 4 subfórmulas.

## Resolución (parte b)

Esta parte se hizo en el teórico (clase 5), la definición inductiva es la siguiente:

$SUB: PROP\to 2^{PROP}$

1. $SUB(\varphi) = \{\varphi\}$ con $\varphi\in AT$
2. $SUB((\alpha*\beta)) = SUB(\alpha)\cup SUB(\beta)\cup\{(\alpha*\beta)\}$
3. $SUB((\neg\alpha)) = SUB(\alpha)\cup\{(\neg\alpha)\}$

## Resolución (parte c)

Tenemos que demostrar que la relación de "ser subfórmula de" es transitiva, es decir que:

$$\forall \alpha,\beta,\varphi\in PROP:\\ 
\alpha\in SUB(\beta)\text{ y }\beta\in SUB(\varphi)\Rightarrow\alpha\in SUB(\varphi)$$

Para demostrar esto usaremos el PIP sobre $PROP$, en este caso sobre $\varphi$, ya que es el más fácil para los casos base. Vamos a probar la propiedad:

$$P(\varphi): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB(\varphi)\Rightarrow\alpha\in SUB(\varphi)$$

### PASO BASE

#### PARTE 1

$P(p_i): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB(p_i)\Rightarrow\alpha\in SUB(p_i)$

Observemos lo siguiente:

- $\beta\in SUB(p_i)$ implica que $\beta = p_i$ por la definición de subfórmula
- $\alpha\in SUB(\beta)$ implica que $\alpha\in SUB(p_i)$ por lo anterior, y en consecuencia $\alpha = p_i$

Juntando lo anterior, la implicancia final quedaría como:

-  $\alpha\in SUB(p_i)$ pero $\alpha=p_i$, por lo que se cumple la propiedad de forma trivial

#### PARTE 2

$P(\bot): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB(\bot)\Rightarrow\alpha\in SUB(\bot)$

Es exactamente análoga a la parte anterior.

### PASO INDUCTIVO

(H) $P((\varphi)): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB((\varphi))\Rightarrow\alpha\in SUB((\varphi))$

#### PARTE 1

(T) $P((\varphi_1*\varphi_2)): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB((\varphi_1*\varphi_2))\Rightarrow\alpha\in SUB((\varphi_1*\varphi_2))$

Observemos que para que $\beta\in SUB((\varphi_1*\varphi_2))$ solo hay tres posibilidades, o bien:

- $\beta = (\varphi_1*\varphi_2)$
- $\beta\in SUB(\varphi_1)$
- $\beta\in SUB(\varphi_2)$

El primer caso es trivial, ya que si $\beta = (\varphi_1*\varphi_2)$, entonces $\alpha\in SUB(\varphi_1*\varphi_2)$ y se cumple la propiedad.

Los siguientes dos casos también son bastante directos, utilizando la hipótesis, sabemos que lo siguiente es cierto:

- $(\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB((\varphi_1))\Rightarrow\alpha\in SUB((\varphi_1))$
- $(\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB((\varphi_2))\Rightarrow\alpha\in SUB((\varphi_2))$

Y como $\alpha\in SUB(\varphi_1)$ o $\alpha\in SUB(\varphi_2)$, entonces $\alpha\in SUB((\varphi_1*\varphi_2))$, por la construcción de la función $SUB$

#### PARTE 2

(T) $P((\neg\varphi)): (\forall\alpha,\beta\in PROP)\quad\alpha\in SUB(\beta)\text{ y }\beta\in SUB((\neg\varphi))\Rightarrow\alpha\in SUB((\neg\varphi))$

Este caso es análogo al anterior, solo que en este caso solo hay dos posibilidades para $\beta$:

- $\beta = (\neg\varphi)$
- $\beta\in SUB(\varphi)$

Y nuevamente, si $\beta = (\neg\varphi)$, entonces $\alpha\in SUB(\neg\varphi)$ y se cumple la propiedad.

Si $\beta\in SUB(\varphi)$, entonces $\alpha\in SUB(\varphi)$ por la hipótesis inductiva, y por lo tanto $\alpha\in SUB((\neg\varphi))$, por la construcción de la función $SUB$.

Esto demuestra la propiedad para todos los casos, por lo que la relación de "ser subfórmula de" es transitiva.

### Conclusión

Para estos ejercicios lo más importante es escribir lo que queremos probar formalmente, y entender bien que proposición de $PROP$ tomar para hacer el PIP. La buena elección de este nos llevará a demostraciones más simples