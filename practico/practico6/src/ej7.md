# Ejercicio 7

## Consigna

Considere un lenguaje de primer orden de tipo $\langle-,2;1\rangle$ con un símbolo de función $f_{1}$ y un símbolo de constante $c_{1}$. Verifique cuáles de las siguientes afirmaciones son correctas.  

(a) $x_{1}$ es libre para $x_{1}$ en la fórmula $x_{2} =' x_{1}$.  
  
(b) $x_{3}$ es libre para $x_{1}$ en la fórmula $x_{1} =' x_{2}$.  
  
(c) $c_{1}$ es libre para $f_{1}(x_{1},c_{1})$ en la fórmula $f_{1}(x_{1},c_{1}) =' c_{1}$.  
  
(d) $f_{1}(x_{1},x_{3})$ es libre para $x_{3}$ en la fórmula $x_{2} =' c_{1}$.  
  
(e) $x_{1}$ es libre para $f_{1}(x_{1},c_{1})$ en la fórmula $((\forall x_{1})\ f_{1}(x_{1},c_{1}) =' c_{1})$.  
  
(f) $f_{1}(c_{1},x_{2})$ es libre para $x_{2}$ en la fórmula $((\exists x_{2})\ x_{2} =' x_{1})$.  
  
(g) $f_{1}(c_{1},x_{2})$ es libre para $x_{1}$ en la fórmula $((\exists x_{2})\ x_{2} =' x_{1})$.  
  
(h) $f_{1}(x_{1},x_{2})$ es libre para $x_{5}$ en la fórmula $((\forall x_{3})\ x_{3} =' x_{4}) \rightarrow ((\forall x_{5})\ x_{5} =' x_{2})$.  
  
(i) $f_{1}(x_{1},x_{2})$ es libre para $x_{3}$ en la fórmula $((\exists x_{3})\ x_{3} =' c_{1}) \lor ((\exists x_{4})\ x_{3} =' x_{4})$.

## Resolución

### Recordatorio

Consideramos la siguiente definición para trabajar en este ejercicio.

Sean $t\in TERM,\psi\in FORM$. $t$ está libre para $x$ en $\psi$ si:

1. $\psi$ es atómica.
2. $\psi=(\psi_1\square\psi_2)$ y $t$ está libre para $x$ en $\psi_1$ y en $\psi_2$
3. $\psi=(\neg\psi_1)$ y $t$ está libre para $x$ en $\psi_1$
4. $\psi = ((\forall y)\psi_1)$ (o $\psi=((\exists y)\psi_1)$) y se cumple alguna de las siguientes:
    1. $x\notin FV(((\forall y)\psi_1))$ y respectivamente para $((\exists y)\psi_1)$
    2. $y\notin FV(t)$ y $t$ está libre para $x$ en $\psi_1$

### Afirmación a

$x_{1}$ es libre para $x_{1}$ en la fórmula $x_{2} =' x_{1}$.

La afirmación es **VERDADERA** pues la fórmula $\phi=(x_{2} =' x_{1})$ es atómica.

### Afirmación b

$x_{3}$ es libre para $x_{1}$ en la fórmula $x_{1} =' x_{2}$.

La afirmación es **VERDADERA** pues la fórmula $\phi=(x_{1} =' x_{2})$ es atómica.

### Afirmación c

$c_{1}$ es libre para $f_{1}(x_{1},c_{1})$ en la fórmula $f_{1}(x_{1},c_{1}) =' c_{1}$.

La afirmación es **FALSA**, pues estamos evaluando si un **término** es libre para una **variable** en una **fórmula**.
En este caso, no podemos evaluar la expresión pues $f_1(x_1,c_1)$ **NO** es una variable.

### Afirmación d

$f_{1}(x_{1},x_{3})$ es libre para $x_{3}$ en la fórmula $x_{2} =' c_{1}$.

La afirmación es **VERDADERA**, pues la fórmula $\phi=(x_{2} =' c_{1})$ es atómica.

### Afirmación e

$x_{1}$ es libre para $f_{1}(x_{1},c_{1})$ en la fórmula $((\forall x_{1})\ f_{1}(x_{1},c_{1}) =' c_{1})$.

La afirmación es **FALSA**, pues estamos evaluando si un **término** es libre para una **variable** en una **fórmula**.
En este caso, no podemos evaluar la expresión pues $f_1(x_1,c_1)$ **NO** es una variable.

### Afirmación f

$f_{1}(c_{1},x_{2})$ es libre para $x_{2}$ en la fórmula $((\exists x_{2})\ x_{2} =' x_{1})$.

La afirmación es **VERDADERA**, pues:
- $x_2\notin FV((\exists x_{2})\ x_{2} =' x_{1})$ (Regla 4.1 en la definición)

### Afirmación g

$f_{1}(c_{1},x_{2})$ es libre para $x_{1}$ en la fórmula $((\exists x_{2})\ x_{2} =' x_{1})$.

La afirmación es **FALSA**, pues:
- $x_2\in FV(f_1(c_1,x_2))$
- $x_1\in FV((\exists x_{2})\ x_{2} =' x_{1})$

Entonces se hace falsa por la regla 4 de la definición.

### Afirmación h

$f_{1}(x_{1},x_{2})$ es libre para $x_{5}$ en la fórmula $((\forall x_{3})\ x_{3} =' x_{4}) \rightarrow ((\forall x_{5})\ x_{5} =' x_{2})$.

Para este ejemplo vamos a tener que aplicar un paso de recursión, deberíamos evaluar las siguientes afirmaciones para verificar el resultado final:

- $f_{1}(x_{1},x_{2})$ es libre para $x_{5}$ en la fórmula $((\forall x_{3})\ x_{3} =' x_{4})$.
    - Esta es VERDADERA, pues $x_3\notin FV(f_1(x_1,x_2))$ (Regla 4.2 en la definición)
- $f_{1}(x_{1},x_{2})$ es libre para $x_{5}$ en la fórmula $((\forall x_{5})\ x_{5} =' x_{2})$.
    - Esta es VERDADERA, pues $x_5\notin FV((\forall x_{5})\ x_{5} =' x_{2})$ (Regla 4.1 en la definición)

Por lo que podemos concluir que esta afirmación es **VERDADERA**.

### Afirmación i

$f_{1}(x_{1},x_{2})$ es libre para $x_{3}$ en la fórmula $((\exists x_{3})\ x_{3} =' c_{1}) \lor ((\exists x_{4})\ x_{3} =' x_{4})$.

Para este ejemplo vamos a tener que aplicar un paso de recursión, deberíamos evaluar las siguientes afirmaciones para verificar el resultado final:

- $f_{1}(x_{1},x_{2})$ es libre para $x_{3}$ en la fórmula $((\exists x_{3})\ x_{3} =' c_{1})$.
    - Esta es VERDADERA, pues $x_3\notin FV((\exists x_{3})\ x_{3} =' c_{1})$ (Regla 4.1 en la definición)
- $f_{1}(x_{1},x_{2})$ es libre para $x_{3}$ en la fórmula $((\exists x_{4})\ x_{3} =' x_{4})$.
    - Esta es VERDADERA, pues $x_4\notin FV(f_1(x_1,x_2))$ (Regla 4.2 en la definición)

Por lo que podemos concluir que esta afirmación es **VERDADERA**.