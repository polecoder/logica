# Ejercicio 9

## Consigna

Sea el conjunto $\mathcal{T}(PROP)$ de los árboles etiquetados con elementos de $PROP$ y la función:

$$
ARBOL : PROP \to \mathcal{T}(PROP)
$$

que asocia cada proposición de $PROP$ con su árbol (vista en el teórico).


(a) Defina una función $CantAt : PROP \to \mathbb{N}$ tal que $CantAt(\varphi)$ sea la cantidad de átomos que ocurren en $\varphi$.

Por ejemplo, $CantAt((p_1 \land (\neg p_2))) = 2$.

(b) Defina la función $CantNodos : \mathcal{T}(PROP) \to \mathbb{N}$ tal que $CantNodos(ARBOL(\varphi))$ sea la cantidad de nodos del árbol de $\varphi$.

Por ejemplo, $CantNodos(ARBOL((p_1 \land (\neg p_2)))) = 4$.

(c) Considere la función $sub$ del Ejercicio 5. Demuestre que $|sub(\varphi)| \leq CantNodos(ARBOL(\varphi))$.

## Resolución (parte a)

Esta parte la podemos resolver usando el ERP en $PROP$. Veamos como hacerlo:

1. $CantAt(\varphi) = 1$ con $\varphi\in AT$
2. $CantAt((\alpha * \beta)) = CantAt(\alpha) + CantAt(\beta)$ con $\alpha,\beta\in PROP$
3. $CantAt((\neg\alpha)) = CantAt(\alpha)$ con $\alpha\in PROP$

**Observación**: En este caso comparado con el ejercicio anterior, ignoramos el paso de las funciones $H$ y vamos directo a la definición de $CantAt$. Es muy claro ver como pasamos de definirlas explicitamente a definir $CantAt$ directamente

## Resolución (parte b)

Para esta parte tendremos que usar el ERP en $\mathcal{T}(PROP)$. Definamos primero el esquema (ya que no lo hemos visto todavía) y luego apliquemoslo a la resolución del ejercicio.

### ERP para $\mathcal{T}(PROP)$

Sea $B$ un conjunto, y:

1. una función $H_{\mathcal{T}(AT)}: \mathcal{T}(AT)\rightarrow B$, y
2. para cada conectivo $*\in C_2$, una función $H_*: \mathcal{T}(PROP)\times B\rightarrow B$, y:
3. una función $H_{\neg}: \mathcal{T}(PROP)\times B\rightarrow B$

Entonces, existe una única función $F: \mathcal{T}(PROP)\rightarrow B$ tal que:

1. $F(\mathcal{T}(\varphi)) = H_{\mathcal{T}(AT)}(\mathcal{T}(\varphi))$ con $\varphi\in AT$
2. $F(\mathcal{T}(\alpha*\beta)) = H_*(\mathcal{T}(\alpha*\beta), F(\mathcal{T}(\alpha*\beta)))$ con $\alpha,\beta\in PROP$
3. $F(\mathcal{T}(\neg\alpha)) = H_{\neg}(\mathcal{T}(\neg\alpha), F(\mathcal{T}(\neg\alpha)))$ con $\alpha\in PROP$

Donde $\mathcal{T}(\varphi)$ es el árbol etiquetado de $\varphi$ para cualquier $\varphi\in PROP$.

**ATENCIÓN:** El resto del ejercicio se basa en si esto está correcto o no. Entiendo que debería ser correcto, pero no lo tengo 100% confirmado.

### Continuación del ejercicio

Con esto podemos definir $CantNodos$ de la siguiente forma:

1. $CantNodos(\mathcal{T}(\varphi)) = 1$ con $\varphi\in AT$
2. $CantNodos(\mathcal{T}(\alpha*\beta)) = 1 + CantNodos(\mathcal{T}(\alpha)) + CantNodos(\mathcal{T}(\beta))$ con $\alpha,\beta\in PROP$
3. $CantNodos(\mathcal{T}(\neg\alpha)) = 1 + CantNodos(\mathcal{T}(\alpha))$ con $\alpha\in PROP$

## Resolución (parte c)

Queremos demostrar que: 
$$|sub(\varphi)| \leq CantNodos(ARBOL(\varphi))\quad\forall\varphi\in PROP$$

Para aclarar, observemos que $|sub(\varphi)|$ es el cardinal del conjunto de subfórmulas de $\varphi$.

Para demostrar esto, vamos a usar el PIP sobre $PROP$:

### Definición de $sub: PROP\to 2^{PROP}$

Se hizo en la clase 5 de teórico:

1. $sub(\varphi) = \{\varphi\}$ con $\varphi\in AT$
2. $sub((\alpha*\beta)) = sub(\alpha)\cup sub(\beta)\cup\{(\alpha*\beta)\}$
3. $sub((\neg\alpha)) = sub(\alpha)\cup\{(\neg\alpha)\}$

### PASO BASE

$P(\varphi): sub(\varphi)\leq CantNodos(ARBOL(\varphi))$ con $\varphi\in AT$

Por la regla 1 de ambas las funciones que estamos usando tenemos que:

1. $|sub(\varphi)| = |\{\varphi\}| = 1$
2. $CantNodos(ARBOL(\varphi)) = 1$

Por lo que se cumple la propiedad.

### PASO INDUCTIVO

(H) $P((\varphi)): sub(\varphi)\leq CantNodos(ARBOL(\varphi))$ con $\varphi\in PROP$

#### PARTE 1

(T) $P((\varphi_1*\varphi_2)): sub(\varphi_1*\varphi_2)\leq CantNodos(ARBOL(\varphi_1*\varphi_2))$ con $\varphi_1,\varphi_2\in PROP$

Para demostrar esto, vamos a usar la definición de $sub$ y $CantNodos$:

1. $|sub(\varphi_1*\varphi_2)| = |sub(\varphi_1)\cup sub(\varphi_2)\cup\{(\varphi_1*\varphi_2)\}| = |sub(\varphi_1)|+|sub(\varphi_2)|+|\{(\varphi_1*\varphi_2)\}| = |sub(\varphi_1)|+|sub(\varphi_2)| + 1$
2. $CantNodos(ARBOL(\varphi_1*\varphi_2)) = 1 + CantNodos(ARBOL(\varphi_1)) + CantNodos(ARBOL(\varphi_2))$

Ahora comparemos ambos valores:

$$
|sub(\varphi_1)|+|sub(\varphi_2)|+1 \leq 1 + CantNodos(ARBOL(\varphi_1)) + CantNodos(ARBOL(\varphi_2))\iff\\
|sub(\varphi_1)|+|sub(\varphi_2)| \leq CantNodos(ARBOL(\varphi_1)) + CantNodos(ARBOL(\varphi_2))
$$

Pero por hipótesis tenemos que:

1. $|sub(\varphi_1)| \leq CantNodos(ARBOL(\varphi_1))$
2. $|sub(\varphi_2)| \leq CantNodos(ARBOL(\varphi_2))$

Entonces por estas observaciones, la propiedad se cumple

#### PARTE 2

(T) $P((\neg\varphi_1)): sub(\neg\varphi_1)\leq CantNodos(ARBOL(\neg\varphi_1))$ con $\varphi_1\in PROP$

Para demostrar esto, vamos a usar la definición de $sub$ y $CantNodos$:

1. $|sub(\neg\varphi_1)| = |sub(\varphi_1)\cup\{(\neg\varphi_1)\}| = |sub(\varphi_1)| + 1$
2. $CantNodos(ARBOL(\neg\varphi_1)) = 1 + CantNodos(ARBOL(\varphi_1))$

Ahora comparemos ambos valores:

$$
|sub(\varphi_1)| + 1\leq 1 + CantNodos(ARBOL(\varphi_1))\iff\\
|sub(\varphi_1)|\leq CantNodos(ARBOL(\varphi_1))
$$

Donde lo último se cumple por hipótesis. Esto prueba la propiedad para todo $\varphi\in PROP$