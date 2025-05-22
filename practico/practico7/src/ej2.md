# Ejercicio 2

## Consigna

Considere un lenguaje de primer orden del tipo $\langle -;\ 1,\ 2;\ 1 \rangle$ con símbolos función $f_1$ (unario), $f_2$ (binario) y símbolo de constante $c_1$.  
Sean $A, B$ estructuras del mismo tipo definidas como sigue:

- $A = \langle \mathbb{N},\ S,\ +,\ 0 \rangle$ donde $S(x) = x + 1$  
- $B = \langle \mathbb{N},\ D,\ \ast,\ 1 \rangle$ donde $D(x) = 2 \ast x$

Demuestre por inducción que para todo término cerrado $t$ (sin constantes extendidas) se cumple que:

$$
t^B = 2^{t^A}
$$

## Resolución

El primer paso del ejercicio es definir $TERM_C$ para poder aplicar el PIP y trabajar con lo que queremos probar de manera formal.

Definimos $TERM_C$ por:
1. $c_1\in TERM_C$
2. Si $t_1\in TERM_C$ entonces $f_1(t_1)\in TERM_C$
3. Si $t_1,t_2\in TERM_C$ entonces $f_2(t_1,t_2)\in TERM_C$

La propiedad que queremos probar sobre $t\in TERM_C$ es la siguiente:

- $P(t): (\overline{\forall}t\in TERM_C)t^B=2^{t^A}$

### Demostración

#### Paso base

- $P(c_1): c_1^B = 2^{(c_1)^A}$

Evaluemos:

$$
\begin{gathered}
c_1^B = 2^{(c_1)^A}\\
\iff\scriptstyle{(\text{interpretación de }c_1\text{ en }A,B)}\\
1 = 2^0\\
\iff\scriptstyle{(\text{aritmética})}\\
1=1
\end{gathered}
$$

Por lo que se cumple $P(c_1)$.

#### Paso inductivo

##### Parte 1

(H) $P(t_1): (t_1)^B = 2^{(t_1)^A}$
(T) $P(f_1(t_1)): f_1(t_1)^B = 2^{f_1(t_1)^A}$

Evaluemos la tesis a ver que podemos decir de ella:

$$
\begin{gathered}
f_1(t_1)^B = 2^{f_1(t_1)^A}\\
\iff\scriptstyle{(\text{interpretación de }f_1\text{ en }B)}\\
2\cdot(t_1)^B = 2^{f_1(t_1)^A}\\
\iff\scriptstyle{(\text{interpretación de }f_1\text{ en }A)}\\
2\cdot(t_1)^B = 2^{(t_1)^A+1}\\
\iff\scriptstyle{(\text{aritmética})}\\
2\cdot(t_1)^B = 2\cdot 2^{(t_1)^A}\\
\iff\scriptstyle{(\text{aritmética})}\\
(t_1)^B = 2^{(t_1)^A}\\
\end{gathered}
$$

Donde esto último es verdadero por hipótesis, por lo que esta parte queda probada.

##### Parte 2

(H1) $P(t_1): (t_1)^B = 2^{(t_1)^A}$
(H2) $P(t_2): (t_2)^B = 2^{(t_2)^A}$
(T) $P(f_2(t_1,t_2)): f_2(t_1,t_2)^B = 2^{f_2(t_1,t_2)^A}$

Evaluemos la tesis a ver que podemos decir de ella:

$$
\begin{gathered}
f_2(t_1,t_2)^B = 2^{f_2(t_1,t_2)^A}\\
\iff\scriptstyle{(\text{interpretación de }f_2\text{ en }B)}\\
t_1^B\cdot t_2^B = 2^{f_2(t_1,t_2)^A}\\
\iff\scriptstyle{(\text{interpretación de }f_2\text{ en }A)}\\
(t_1)^B\cdot (t_2)^B = 2^{(t_1)^A+(t_2)^A}\\
\iff\scriptstyle{(\text{aritmética})}\\
(t_1)^B\cdot (t_2)^B = 2^{(t_1)^A}\cdot 2^{(t_2)^A}\\
\iff\scriptstyle{(\text{por H2: }(t_2)^B=2^{(t_2)^A}\neq 0)}\\
(t_1)^B = 2^{(t_1)^A}\\
\end{gathered}
$$

Donde esto último se cumple por hipótesis (H1), por lo que esta parte queda probada.

Esto concluye la demostración. $\blacksquare$