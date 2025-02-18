# Ejercicio 9

## Consigna

Considere el alfabeto $\Sigma = \{a, b\}$, y los lenguajes $\Delta$ y $\Gamma$ definidos inductivamente con las siguientes reglas. Demuestre que $\Gamma = \Delta$.

**Reglas para $\Gamma$:**

1. $\varepsilon \in \Gamma$
2. Si $\alpha \in \Gamma$, entonces $a\alpha \in \Gamma$
3. Si $\alpha \in \Gamma$, entonces $b\alpha \in \Gamma$

**Reglas para $\Delta$:**

1. $\varepsilon \in \Delta$
2. Si $\alpha \in \Delta$, entonces $\alpha a \in \Delta$
3. Si $\alpha \in \Delta$, entonces $\alpha b \in \Delta$

## Resolución

Primero, cambiaremos ligeramente ambas las definiciones de los lenguajes $\Delta$ y $\Gamma$ para tener una regla inductiva menos. Veamos como hacerlo:

**Reglas para $\Gamma$:**

1. $\varepsilon\in\Gamma$
2. Si $\alpha\in\Gamma$, $x\in\Sigma$, entonces $x\alpha\in\Gamma$

**Reglas para $\Delta$:**

1. $\varepsilon\in\Delta$
2. Si $\alpha\in\Delta$, $y\in\Sigma$, entonces $\alpha y\in\Delta$

Bien, ahora queremos probar que $\Delta\subseteq\Gamma$ y $\Gamma\subseteq\Delta$, esto es equivalente a decir que son iguales.
Primero vamos a probar que $\Gamma\subseteq\Delta$; para esto usemos el PIP en $\Gamma$ con la propiedad $P:\alpha\in\Delta$, para probar que todos sus elementos, están incluidos en $\Delta$.

### PASO BASE

$P(\varepsilon): \varepsilon\in\Delta$: Esto se prueba por la regla (i) del lenguaje $\Delta$.

### PASO INDUCTIVO

(H) $P(\alpha): \alpha\in\Delta$
(T) $P(x\alpha): x\alpha\in\Delta$ con $x\in\Sigma$

Entonces, lo que queremos probar es que para todo $\alpha\in\Delta,\quad x\alpha\in\Delta$. Esto lo podemos probar usando el PIP para $\Delta$.
Sea $P'(\alpha):= x\alpha\in\Delta$

#### (SUB) PASO BASE

$P'(\varepsilon): x\varepsilon\in\Delta$.

Esto se cumple usando (i) y (ii) de la definición de $\Delta$, ya que por (i) sabemos que $\varepsilon$ está incluido en $\Delta$, y por (ii) sabemos que $\forall y\in\Sigma: \varepsilon y\in\Delta$. Pero observemos que:

$$x\varepsilon = \varepsilon y$$

Porque $\varepsilon$ es la palabra vacía, y $x,y$ representan un símbolo de $\Sigma$. Concluyendo, esto se cumple

#### (SUB) PASO INDUCTIVO

(H) $P'(\alpha): x\alpha\in\Delta$
(T) $P'(\alpha y): x\alpha y\in\Delta$

Asumimos que $P'(\alpha)$ es verdadera, entonces por la regla (ii) de $\Delta$ podemos decir que:

Como $x\alpha\in\Delta$ y $y\in\Sigma$; entonces:

$$x\alpha y\in\Delta$$

Esto prueba la tesis.

A su vez, volviendo a la primer inducción, esto prueba $P'(\alpha): x\alpha\in\Delta$. Por lo que probamos que $\Gamma\subseteq\Delta$.

Faltaría probar que $\Delta\subseteq\Gamma$, pero la prueba es básicamente un espejo de la que acabamos de realizar.