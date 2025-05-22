# Ejercicio 1

## Consigna

Considere un lenguaje de primer orden del tipo $\langle -;\ 1,\ 1,\ 2;\ 3 \rangle$ con símbolos de función $f_1,\ f_2$ (unarios), $f_3$ (binario) y símbolos de constante $c_1,\ c_2,\ c_3$.

Sea $B$ una estructura de dicho tipo definida como sigue:  
$B = \langle \mathbb{R},\ ^2,\ |\cdot|,\ -,\ 0,\ 1,\ 2 \rangle$ donde $^2$ es la función cuadrado, $|\cdot|$ el valor absoluto y $-$ la resta.

Evalúe:  
- $(f_2(f_3(f_1(c_3),\ f_1(c_2))))^B$  
- $(f_2(f_3(c_2,\ f_3(c_2,\ f_1(c_3)))))^B$

## Resolución

Hagamos dos partes, una para cada evaluación.

### Parte 1

Evaluemos $(f_2(f_3(f_1(c_3),\ f_1(c_2))))^B$

$$
\begin{gathered}
(f_2(f_3(f_1(c_3), f_1(c_2))))^B\\
=\scriptstyle{(\text{interpretación de }f_2\text{ en }B)}\\
|(f_3(f_1(c_3), f_1(c_2)))^B|\\
=\scriptstyle{(\text{interpretación de }f_3\text{ en }B)}\\
|f_1(c_3)^B - f_1(c_2)^B|\\
=\scriptstyle{(\text{interpretación de }f_1\text{ en }B)}\\
|((c_3)^B)^2 - ((c_2)^B)^2|\\
=\scriptstyle{(\text{interpretación de }c_2,c_3\text{ en }B)}\\
|2^2 - 1^2|\\
=\scriptstyle{(\text{aritmética})}\\
3
\end{gathered}
$$

### Parte 2

Evaluemos $(f_2(f_3(c_2,f_3(c_2,\ f_1(c_3)))))^B$.

$$
\begin{gathered}
(f_2(f_3(c_2,f_3(c_2, f_1(c_3)))))^B\\
=\scriptstyle{(\text{interpretación de }f_2\text{ en }B)}\\
|f_3(c_2,f_3(c_2, f_1(c_3)))^B|\\
=\scriptstyle{(\text{interpretación de }f_3\text{ en }B)}\\
|c_2^B-f_3(c_2, f_1(c_3))^B|\\
=\scriptstyle{(\text{interpretación de }c_2,f_3\text{ en }B)}\\
|1-(c_2^B - f_1(c_3)^B)|\\
=\scriptstyle{(\text{interpretación de }c_2,f_1\text{ en }B)}\\
|1-(1 - ((c_3)^B)^2)|\\
=\scriptstyle{(\text{interpretación de }c_3\text{ en }B)}\\
|1-(1 - 2^2)|\\
=\scriptstyle{(\text{aritmética})}\\
|1-(-3)|\\
=\scriptstyle{(\text{aritmética})}\\
4
\end{gathered}
$$