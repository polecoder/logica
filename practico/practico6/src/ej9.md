# Ejercicio 9

## Consigna

Considere un lenguaje de primer orden del tipo $\langle -; 1, 2; 1 \rangle$ con dos símbolos de función $f_1$ (unario) y $f_2$ (binario) y un símbolo de constante $c_1$.

(a) Defina inductivamente el conjunto $\text{TERM}_C$ de los términos cerrados pertenecientes a dicho lenguaje.

(b) Defina recursivamente la función $F : \text{TERM}_C \to \mathbb{N}$ que calcula la cantidad de ocurrencias de $c_1$ en un término $t \in \text{TERM}_C$.

(c) Demuestre por inducción que para todo $t \in \text{TERM}_C$ se cumple que $F(t) > 0$.

## Resolución

### Recordatorio

Sea $A$ el alfabeto de tipo $\left<r_1,\ldots,r_n;a_1,\ldots,a_m;k\right>$

- Un término $t$ es cerrado si $FV(t)=\emptyset$.
- Una fórmula es cerrada si $FV(\alpha)=\emptyset$. También se dice en este caso que $\alpha$ es una **sentencia**.
- Una fórmula $\alpha$ es abierta si no tiene cuantificadores.

**Notación:**

- $TERM_{CA}=\{t\in TERM_A\mid t\text{ es cerrado}\}$
- $SENT_A=\{\alpha\in FORM_A\mid \alpha\text{ es cerrada}\}$

### Parte a

Para definir inductivamente $TERM_C$, observemos que los elementos que pertenezcan a él serán aquellos que son o tienen constantes en él. Ya que si tienen alguna variable, esta pertenecerá a $FV(t)$.

Definimos $TERM_C$ por:

1. $c_1\in TERM_C$
2. Si $t\in TERM_C$, entonces $f_1(t)\in TERM_C$
3. Si $t_1,t_2\in TERM_C$, entonces $f_2(t_1,t_2)\in TERM_C$

### Parte b

Basandonos en la definición dada en el paso anterior tenemos que:

$F:TERM_C\to\mathbb{N}$
1. $F(c_1)=1$
2. $F(f_1(t)) = F(t)$
3. $F(f_2(t_1,t_2)) = F(t_1)+F(t_2)$

### Parte c

Queremos probar que para todo $t \in TERM_C$ se cumple que $F(t) > 0$.

Entonces definimos la propiedad $P$ sobre $TERM_C$ de la siguiente forma:

$P(t): F(t) > 0$

#### PASO BASE

$P(c_1): F(c_1) > 0$

Observemos que esto se cumple trivialmente por la regla 1 de la definición de la función $F$, que nos dice que $F(c_1) = 1$

#### PASO INDUCTIVO

##### PARTE 1

Primero probamos lo correspondiente a la parte 1, es decir que:

(H) $P(t): F(t) > 0$
(T) $P(f_1(t)): F(f_1(t)) > 0$

Esto también es muy trivial pues la definición de la función $F$, en la regla 2 nos dice que: $F(f_1(t)) = F(t)$. Por hipótesis tenemos que:

$$
F(f_1(t)) = F(t) > 0
$$

Aplicando transitividad probamos lo que queríamos verificar.

##### PARTE 2

(H) $P(t_1): F(t_1) > 0$
(H) $P(t_2): F(t_2) > 0$
(T) $P(f_2(t_1,t_2)): F(f_2(t_1,t_2)) > 0$

Veamos que podemos decir de la tesis:

$$
\begin{aligned}
&F(f_2(t_1,t_2))\\
&=\scriptstyle{(\text{por regla 3 de }F)}\\
&F(t_1)+F(t_2)\\
&>\scriptstyle{(\text{por hipótesis inductiva})}\\
&0+0
\end{aligned}
$$

Por lo que por transitividad probamos lo que queríamos verificar.

Esto concluye la prueba por inducción y podemos decir que:

$$
\forall t\in TERM_C: F(t)>0
$$