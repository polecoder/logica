# Ejercicio 1

## Consigna

Investigue cuáles de las siguientes proposiciones son tautologías.

(a) $(\neg p \lor q) \leftrightarrow (q \to p)$

(b) $(p \to (q \to r)) \leftrightarrow ((p \land q) \to r)$

(c) $\bot \to p$

(d) $(p \to q) \lor (\neg p \to r)$

## Resolución

Podemos trabajar con tablas de verdad para esta parte, porque estamos trabajando con letras proposicionales.

### Parte (a)

Construyamos la tabla de verdad para verificar si efectivamente la proposición es tautología.

$$
\begin{array}{c|c|c|c|c|c}
p&q&\neg p&(\neg p\lor q)&(q\rightarrow p)&((\neg p \lor q) \leftrightarrow (q \to p))\\
\hline
0&0&1&1&1&1\\
0&1&1&1&0&0\\
1&0&0&0&1&0\\
1&1&0&1&1&1
\end{array}
$$

Si tomamos una valuación $v$ tal que $v(p) = 0$ y $v(q) = 1$ tenemos que $v((\neg p \lor q) \leftrightarrow (q \to p)) = 0$. Por lo que podemos concluir que $\not\models (\neg p \lor q) \leftrightarrow (q \to p)$

### Parte (b)

Construyamos la tabla de verdad para verificar si efectivamente la proposición es tautología.

$$
\begin{array}{c|c|c|c|c|c|c|c}
p&q&r&(q\rightarrow r)&(p\rightarrow(q\rightarrow r))&(p\land q)&((p\land q)\rightarrow r)&(p \to (q \to r)) \leftrightarrow ((p \land q) \to r)\\
\hline
0&0&0&1&1&0&1&1\\
0&0&1&1&1&0&1&1\\
0&1&0&0&1&0&1&1\\
0&1&1&1&1&0&1&1\\
1&0&0&1&1&0&1&1\\
1&0&1&1&1&0&1&1\\
1&1&0&0&0&1&0&1\\
1&1&1&1&1&1&1&1
\end{array}
$$

Con esto verificamos que efectivamente $\models ((p \to (q \to r)) \leftrightarrow ((p \land q) \to r))$

### Parte (c)

Para este caso ni siquiera tenemos que hacer la tabla de verdad. Observemos que $v(\bot) = 0$ para toda valuación $v$ por definición de valuación.

Usando la definición de valuación tenemos que:

$$
\begin{aligned}
&v(\bot\rightarrow p)\\
&= {\scriptstyle (\text{definición de valuación})}\\
&max\{1-v(\bot), v(p)\}\\
&= {\scriptstyle (\text{definición de valuación})}\\
&max\{1-0, v(p)\}
\end{aligned}
$$

Donde trivialmente se cumple que el valor es 1. Con lo que verificamos que efectivamente $\models (\bot\rightarrow p)$

### Parte (d)

Construyamos la tabla de verdad para verificar si efectivamente la proposición es tautología.

$$
\begin{array}{c|c|c|c|c|c|c}
p&q&r&(p\rightarrow q)&\neg p&(\neg p\rightarrow r)&(p \to q) \lor (\neg p \to r)\\
\hline
0&0&0&1&1&0&1\\
0&0&1&1&1&1&1\\
0&1&0&1&1&0&1\\
0&1&1&1&1&1&1\\
1&0&0&0&0&1&1\\
1&0&1&0&0&1&1\\
1&1&0&1&0&1&1\\
1&1&1&1&0&1&1\\
\end{array}
$$

Con esto verificamos que efectivamente $\models (p \to q) \lor (\neg p \to r)$