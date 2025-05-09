# Ejercicio 4

## Consigna

Considere un lenguaje de primer orden del tipo $\left<1,2;2;0\right>$ con dos símbolos de relación $P_1$ (unario) y $P_2$ (binario) y un símbolo de función $f_1$ (binario). Sea $FORM$ el conjunto de fórmulas de dicho lenguaje. Indique cuáles de las siguientes son fórmulas bien formadas de dicho lenguaje
(o sea, cuáles cumplen la definición de $FORM$).

1. $((\forall x_1)((\exists x_2) P_2(x_1, x_2)))$
2. $(P_1(x_1) \to (((\exists x_2) f_1(x_1, x_2) =' x_2) \land((\exists x_1) P_2(x_1, x_2))))$
3. $(((\exists x_1)((\exists x_2) f_1(x_1, x_2))) \to ((\forall x_1) P_1(f_1(x_1, x_1))))$
4. $((\forall x_1)((\forall x_2) (P_1(x_1) \lor ((\exists x_1) P_2(x_1, x_2)))))$
5. $(P_1((\forall x_1) P_2(x_1, x_2)) \leftrightarrow ((\forall x_1) P_1(P_2(x_1, x_2))))$
6. $((\exists x_1) \land ((\forall x_2) P_2(x_1, x_2)))$
7. $((\forall x_1) (P_1(x_1) \to (P_1(f_1(x_1, x_2)) \land ((\exists x_1) P_1(f_1(x_1, f_1(x_1, x_2)))))))$ 

## Resolución

Para esto es conveniente recordar como definimos $FORM$:

Sea $A$ el alfabeto de tipo $\left<r_1,\ldots,r_n;a_1,\ldots,a_m;k\right>$. El conjunto $FORM_A$ de las fórmulas del lenguaje de primer orden con alfabeto $A$ se define inductivamente por:

1. $\bot\in FORM_A$
2. Si $t_1,\ldots,t_{r_i}\in TERM_A$, entonces $P_i(t_1,\ldots,t_{r_i})\in FORM_A$
3. Si $t_1,t_2\in TERM_A$, entonces $t_1='t_2\in FORM_A$
4. Si $\alpha,\beta\in FORM_A$, entonces $(\alpha\square\beta)\in FORM_A$
5. Si $\alpha\in FORM_A$, entonces $(\neg\alpha)\in FORM_A$
6. Si $\alpha\in FORM_A$, entonces $((\forall x_i)\alpha), ((\exists x_i)\alpha)\in FORM_A$

Vamos a pensar la definición basado en el tipo de alfabeto que tenemos.

### Parte 1

$$(\forall x_1)((\exists x_2)P_2(x_1,x_2))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

$$
\begin{aligned}
&(\forall x_1)((\exists x_2)P_2(x_1,x_2))\in FORM_A\\
&\iff\scriptstyle{(\text{regla 6 de }FORM_A)}\\
&((\exists x_2)P_2(x_1,x_2))\in FORM_A\\
&\iff\scriptstyle{(\text{regla 6 de }FORM_A)}\\
&P_2(x_1,x_2)\in FORM_A\\
&\iff\scriptstyle{(\text{regla 2 de }FORM_A)}\\
&x_1,x_2\in TERM_A\quad\square
\end{aligned}
$$

Donde lo último se cumple, por lo que efectivamente la proposición pertenece a $FORM_A$

### Parte 2

$$(P_1(x_1) \to (((\exists x_2) f_1(x_1, x_2) =' x_2) \land((\exists x_1) P_2(x_1, x_2))))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

1. $P_1(x_1)\in FORM_A\quad\square$
2. $(((\exists x_2) f_1(x_1, x_2) =' x_2) \land((\exists x_1) P_2(x_1, x_2)))\in FORM_A\quad\square$
    - $((\exists x_2) f_1(x_1, x_2) =' x_2)\in FORM_A\quad\square$
        - $f(x_1,x_2)='x_2\in FORM_A\quad\square$
            - $f(x_1,x_2)\in TERM_A\quad\square$
    - $((\exists x_1) P_2(x_1, x_2))\in FORM_A\quad\square$
        - $P_2(x_1,x_2)\in FORM_A\quad\square$
            - $x_1,x_2\in TERM_A\quad\square$ 

Como cada paso se cumple, efectivamente la proposición pertenece a $FORM_A$

### Parte 3

$$(((\exists x_1)((\exists x_2) f_1(x_1, x_2))) \to ((\forall x_1) P_1(f_1(x_1, x_1))))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

1. $((\exists x_1)((\exists x_2) f_1(x_1, x_2)))\in FORM_A$
    - $((\exists x_2) f_1(x_1, x_2))\in FORM_A$
        - $f_1(x_1, x_2)\in FORM_A\quad\text{¡ABSURDO!}$
2. $((\forall x_1) P_1(f_1(x_1, x_1)))\in FORM_A$

Observemos que $f_1(x_1,x_2)\in TERM_A$, por el razonamiento que hicimos debería estar en $FORM_A$, por lo cual la proposición **NO** pertenece a $FORM_A$.

### Parte 4

$$((\forall x_1)((\forall x_2) (P_1(x_1) \lor ((\exists x_1) P_2(x_1, x_2)))))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

1. $((\forall x_2) (P_1(x_1) \lor ((\exists x_1) P_2(x_1, x_2))))\in FORM_A\quad\square$
    - $(P_1(x_1) \lor ((\exists x_1) P_2(x_1, x_2)))\in FORM_A\quad\square$
        - $P_1(x_1)\in FORM_A\quad\square$
        - $((\exists x_1) P_2(x_1, x_2))\in FORM_A\quad\square$
            - $P_2(x_1, x_2)\in FORM_A\quad\square$
                - $x_1,x_2\in TERM_A\quad\square$

Como cada paso se cumple, efectivamente la proposición pertenece a $FORM_A$.

### Parte 5

$$(P_1((\forall x_1) P_2(x_1, x_2)) \leftrightarrow ((\forall x_1) P_1(P_2(x_1, x_2))))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

1. $P_1((\forall x_1) P_2(x_1, x_2))\in FORM_A$
    - $(\forall x_1) P_2(x_1, x_2)\in TERM_A\quad\text{¡ABSURDO!}$
2. $((\forall x_1) P_1(P_2(x_1, x_2)))\in FORM_A$

Observemos que $(\forall x_1) P_2(x_1, x_2)\in FORM_A$, por el razonamiento que hicimos debería estar en $TERM_A$, por lo cual la proposición **NO** pertenece a $FORM_A$.

### Parte 6

$$((\exists x_1) \land ((\forall x_2) P_2(x_1, x_2)))$$

Veamos si efectivamente la proposición pertenece a $FORM_A$:

1. $\land ((\forall x_2) P_2(x_1, x_2))\in FORM_A\quad\text{¡ABSURDO!}$

Observemos que $\land ((\forall x_2) P_2(x_1, x_2))$ está mal construido, ninguna regla permite construir proposiciones a partir de un conectivo binario con una sola proposición, por lo cual la proposición **NO** pertenece a $FORM_A$.

### Parte 7

$$((\forall x_1) (P_1(x_1) \to (P_1(f_1(x_1, x_2)) \land ((\exists x_1) P_1(f_1(x_1, f_1(x_1, x_2)))))))$$

1. $P_1(x_1)\in FORM_A\quad\square$
    - $x_1\in TERM_A\quad\square$
2. $(P_1(f_1(x_1, x_2)) \land ((\exists x_1) P_1(f_1(x_1, f_1(x_1, x_2)))))\in FORM_A\quad\square$
    - $P_1(f_1(x_1, x_2))\in FORM_A\quad\square$
        - $f_1(x_1, x_2)\in TERM_A\quad\square$
    - $(\exists x_1) P_1(f_1(x_1, f_1(x_1, x_2)))\in FORM_A\quad\square$
        - $P_1(f_1(x_1, f_1(x_1, x_2)))\in FORM_A\quad\square$
            - $f_1(x_1, f_1(x_1, x_2))\in TERM_A\quad\square$
                - $x_1\in TERM_A\quad\square$
                - $f_1(x_1, x_2)\in TERM_A\quad\square$

Como cada paso se cumple, efectivamente la proposición pertenece a $FORM_A$