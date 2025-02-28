# Ejercicio 1

## Consigna

Demuestre que:

(a) $(((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))) \land (\neg p_3)) \in PROP$

(b) $((p_7 \to (\neg\bot)) \leftrightarrow ((p_4 \land (\neg p_2)) \to p_1)) \in PROP$

(c) $((\rightarrow\notin PROP$

## Resolución

### Premisa (definición de $PROP$)

El lenguaje de la lógica proposicional $PROP\subseteq\Sigma_{PROP}^*$ está definido inductivamente por:

1. Si $p\in P$, entonces $p\in PROP$
2. $\bot\in PROP$
3. Si $\alpha,\beta\in PROP$, entonces:
    - $(\alpha\land\beta)\in PROP$
    - $(\alpha\lor\beta)\in PROP$
    - $(\alpha\rightarrow\beta)\in PROP$
    - $(\alpha\leftrightarrow\beta)\in PROP$
4. Si $\alpha\in PROP$, entonces $(\neg\alpha)\in PROP$


### Proposición (a)

Para demostrar que la proposición pertenece a $PROP$ tenemos que dar una forma de construirlo a partir de las reglas del conjunto $PROP$ definido inductivamente.

$$
\begin{align*}
&(((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))) \land (\neg p_3))\in PROP\\
&\iff (\text{por regla 3})\\
&\begin{cases}(\neg p_3)\in PROP\\ ((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2)))\in PROP\end{cases}\\
&\iff (\text{(i) por regla 4, (ii) por regla 3})\\
&\begin{cases}p_3\in PROP\quad(i)\\ \begin{cases}(\neg p_2)\in PROP\\ (p_3 \lor (p_1 \leftrightarrow p_2))\in PROP\end{cases}\quad (ii)\end{cases}\\
&\iff (p_3\in PROP\text{ es trivial, (ii) por regla 3 (iv) y 4 (iii)})\\
&\begin{cases}p_2\in PROP\\\begin{cases}p_3\in PROP\quad(iii)\\(p_1\leftrightarrow p_2)\in PROP\quad (iv)\end{cases}\end{cases}\\
&\iff (\text{saco los elementos de }AT\text{ y regla 3})\\
&\begin{cases}p_1\in PROP\\p_2\in PROP\end{cases}
\end{align*}
$$

Donde esto ultimo se cumple porque $p_1,p_2\in AT$.

#### Aclaración

La idea que tenemos cuando "sacamos" los elementos de $AT$, es que por la regla 1 y 2 de $PROP$ sabemos que los elementos de $AT$ pertenecen a $PROP$, por lo que estos elementos no cambian la implicancia de los si y solo si.

### Proposición (b)

$$
\begin{align*}
&((p_7 \to (\neg\bot)) \leftrightarrow ((p_4 \land (\neg p_2)) \to p_1)) \in PROP\\
&\iff (\text{por regla 3})\\
&\begin{cases}(p_7 \to (\neg\bot))\in PROP\\ ((p_4 \land (\neg p_2)) \to p_1)\in PROP\end{cases}\\
&\iff (\text{por regla 3})\\
&\begin{cases}
\begin{cases}p_7\in PROP\\ (\neg\bot)\in PROP\end{cases}\quad (i)\\
\begin{cases}(p_4 \land (\neg p_2))\in PROP\\p_1\in PROP\end{cases}\quad (ii)
\end{cases}\\
&\iff (\text{(i) por regla 4, (ii) por regla 3})\\
&\begin{cases}\bot\in PROP\\\begin{cases}p_4\in PROP\\(\neg p_2)\in PROP\end{cases}\end{cases}\\
&\iff (\text{por regla 4})\\
&p_2 \in PROP\\
\end{align*}
$$

En este caso eliminamos los elementos de $AT$ sin aclaración, recordar que $\bot\in AT$

### Proposición (c)

$$
((\rightarrow\in PROP\\
$$

Esto ya es absurdo, esto no puede pertenecer a $PROP$ porque por ejemplo, no hay paréntesis a la derecha, no se puede crear una proposición de esta forma utilizando las reglas de $PROP$.

Concluimos que esta palabra no pertenece a $PROP$