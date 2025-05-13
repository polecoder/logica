# Ejercicio 6

## Consigna

Considere un lenguaje de primer orden de tipo $\langle-;2;1\rangle$ con un símbolo de función $f_{1}$ y un símbolo de constante $c_{1}$.

(a) En las siguientes fórmulas determine cuáles ocurrencias de variables son libres y cuáles son ligadas. Para aquellas que sean ligadas, señale el cuantificador al cual están ligadas.

1. $x_{2} = x_{1}$
2. $x_{1} = x_{1}$
3. $x_{2} = c_{1}$
4. $(\exists x_{2})f_{1}(x_{2},x_{3}) = c_{1}$
5. $((\forall x_{4}) f_{1}(x_{1},x_{3}) = c_{1}) \land ((\exists x_{2}) x_{3} = x_{1})$
6. $((\forall x_{3}) x_{3} = x_{4}) \rightarrow ((\forall x_{5}) x_{5} = x_{2})$
7. $((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) x_{3} = x_{4})$

(b) Realice las siguientes sustituciones:

1. $x_{2} = x_{1}[x_{1}/x_{1}]$
2. $x_{1} = x_{1}[x_{3}/x_{1}]$
3. $x_{2} = c_{1}[f_{1}(x_{1},x_{3})/x_{3}]$
4. $((\forall x_{4}) f_{1}(x_{1},x_{3}) = c_{1}) \land ((\exists x_{2}) x_{3} = x_{1})[f_{1}(x_{1},x_{2})/x_{3}]$
5. $((\forall x_{3}) x_{3} = x_{4}) \rightarrow ((\forall x_{5}) x_{5} = x_{2})[f_{1}(x_{1},x_{2})/x_{5}]$
6. $((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) x_{3} = x_{4})[f_{1}(x_{1},x_{2})/x_{3}][x_{1}/x_{1}]$

(c) Para las fórmulas resultados de las sustituciones anteriores determine cuáles ocurrencias de variables son libres y cuáles son ligadas. Para aquellas que sean ligadas, señale el cuantificador al cual están ligadas. Compare el resultado con los obtenidos en la parte a.

## Resolución

### Parte a

Determinemos las ocurrencias ligadas y las ocurrencias libres de cada variable en las siguientes fórmulas.

#### Fórmula 1

$$x_{2} = x_{1}$$

- $x_2$ tiene 1 ocurrencia libre.
- $x_1$ tiene 1 ocurrencia libre.

#### Fórmula 2

$$x_{1} = x_{1}$$

- $x_1$ tiene 2 ocurrencias libres.

#### Fórmula 3

$$x_{2} = c_{1}$$

- $x_2$ tiene 1 ocurrencia libre.

#### Fórmula 4

$$(\exists x_{2})f_{1}(x_{2},x_{3}) = c_{1}$$

- $x_2$ tiene 2 ocurrencias ligadas. Ligada a $(\exists x_2)$.
- $x_3$ tiene 1 ocurrencia libre.

#### Fórmula 5

$$((\forall x_{4}) f_{1}(x_{1},x_{3}) = c_{1}) \land ((\exists x_{2}) x_{3} = x_{1})$$

- $x_4$ tiene 1 ocurrencia ligada. Ligada a $(\forall x_4)$.
- $x_1$ tiene 2 ocurrencias libres.
- $x_3$ tiene 2 ocurrencias libres.
- $x_2$ tiene 1 ocurrencia ligada. Ligada a $(\exists x_2)$.

#### Fórmula 6

$$((\forall x_{3}) x_{3} = x_{4}) \rightarrow ((\forall x_{5}) x_{5} = x_{2})$$

- $x_3$ tiene 2 ocurrencias ligadas. Ligada a $(\forall x_3)$.
- $x_4$ tiene 1 ocurrencia libre.
- $x_5$ tiene 2 ocurrencias ligadas. Ligada a $(\forall x_5)$.
- $x_2$ tiene 1 ocurrencia libre.

#### Fórmula 7

$$((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) x_{3} = x_{4})$$

- $x_3$ tiene 2 ocurrencias ligadas. Ligada a $(\exists x_3)$.
- $x_3$ tiene 1 ocurrencia libre.
- $x_4$ tiene 2 ocurrencias ligadas. Ligada a $(\exists x_4)$.

### Parte b

En esta parte realizamos las sustituciones dadas.

#### Sustitución 1

$$x_{2} = x_{1}[x_{1}/x_{1}]$$

El resultado es:

$$x_{2} = x_{1}$$

#### Sustitución 2

$$x_{1} = x_{1}[x_{3}/x_{1}]$$

El resultado es:

$$x_{3} = x_{3}$$

#### Sustitución 3

$$x_{2} = c_{1}[f_{1}(x_{1},x_{3})/x_{3}]$$

El resultado es:

$$x_{2} = c_{1}$$

#### Sustitución 4

$$((\forall x_{4}) f_{1}(x_{1},x_{3}) = c_{1}) \land ((\exists x_{2}) x_{3} = x_{1})[f_{1}(x_{1},x_{2})/x_{3}]$$

El resultado es:

$$((\forall x_{4}) f_{1}(x_{1},f_1(x_1,x_2)) = c_{1}) \land ((\exists x_{2}) f_1(x_1,x_2) = x_{1})$$

**ATENCIÓN:** Nos apareció una nueva ligadura en la subfórmula: $(\exists x_{2}) f_1(x_1,x_2) = x_{1}$

#### Sustitución 5

$$((\forall x_{3}) x_{3} = x_{4}) \rightarrow ((\forall x_{5}) x_{5} = x_{2})[f_{1}(x_{1},x_{2})/x_{5}]$$

El resultado es:

$$((\forall x_{3}) x_{3} = x_{4}) \rightarrow ((\forall x_{5}) x_{5} = x_{2})$$

En este caso la fórmula queda igual, ya que las dos ocurrencias de $x_5$ son ligadas.

#### Sustitución 6

$$((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) x_{3} = x_{4})[f_{1}(x_{1},x_{2})/x_{3}][x_{1}/x_{1}]$$

Vayamos paso a paso:

$$((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) f_{1}(x_{1},x_{2}) = x_{4})[x_{1}/x_{1}]$$

El resultado final es:

$$((\exists x_{3}) x_{3} = c_{1}) \lor ((\exists x_{4}) f_{1}(x_{1},x_{2}) = x_{4})$$

### Parte c

Análoga a la parte (a).