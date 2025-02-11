# Ejercicio 8

## Consigna

Cada ítem describe un lenguaje sobre el alfabeto \sum = \{a, b\}. Se le pide la definición inductiva de cada lenguaje.
$L_1: \{\varepsilon, a, aa, aaa, aaaa, \ldots\}$
$L_2: \{\varepsilon, ab, aabb, aaabbb, aaaabbbb, \ldots\}$
$L_3: \{b, aba, aabaa, aaabaaa, aaaabaaaa, \ldots\}$
$L_4: \{\varepsilon, ab, abab, ababab, \ldots , ba, baba, bababa, \ldots\}$
$L_5: \{\varepsilon, a, ab, aba, abab, ababa, ababab, \ldots\}$
$L_6: \{\alpha \in \sum^∗:\alpha\text{ es un palíndromo}\}$

## Resolución

Se describe una definición inductiva para cada lenguaje a continuación:

#### $L_1$

1. $\varepsilon \in L_1$
2. Si $w \in L_1$, entonces $wa \in L_1$

#### $L_2$

1. $\varepsilon \in L_2$
2. Si $w \in L_2$, entonces $awb \in L_2$

#### $L_3$

1. $b \in L_3$
2. Si $w \in L_3$, entonces $awa \in L_3$

#### $L_4$

1. $\varepsilon \in L_4$
2. Si $w \in L_4$, entonces $wab \in L_4$

#### $L_5$

1. $\varepsilon \in L_5$
2. $a \in L_5$
3. Si $w \in L_5$, entonces $abw \in L_5$

#### $L_6$

1. $\varepsilon \in L_6$
2. $\forall x\in\sum, x\in L_6$
3. Si $x\in\sum, w\in L_6$ entonces $xwx \in L_6$ 

