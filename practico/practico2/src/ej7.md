# Ejercicio 7

## Consigna

(a) Considere una secuencia de formación de $\psi$ en la que ocurren fórmulas que no son subfórmulas de $\psi$: $\varphi_1, \dots, \varphi_n \equiv \psi$ de la fórmula $\psi$. Sea $\varphi_i$ la fórmula de la secuencia que no es subfórmula de $\psi$, y que aparece más a la derecha en la secuencia. Pruebe que si elimina $\varphi_i$ de la secuencia de formación dada, la secuencia resultante sigue siendo una secuencia de formación para $\psi$.

(b) A partir del resultado anterior, demuestre que si $\varphi$ ocurre en una secuencia de formación de largo mínimo para $\psi$, entonces $\varphi$ es una subfórmula de $\psi$.

## Resolución (parte a)

Consideremos una secuencia de formación $s\in secFORM_{\psi}$ como la mencionada en la letra. Veamos la forma que tendrá esta secuencia:

$$
s = \{\varphi_1, \dots, \varphi_i, \dots, \varphi_n, \psi\}
$$

Donde $\varphi_i$ es la fórmula que no es subfórmula de $\psi$ y que aparece más a la derecha en la secuencia. Si eliminamos $\varphi_i$ de la secuencia, tendremos:

$$
s' = \{\varphi_1, \dots, \varphi_{i-1}, \varphi_{i+1}, \dots, \varphi_n, \psi\}
$$

Ahora tenemos que ver que $s'$ es una secuencia de formación para $\psi$

Por una parte, los siguientes elementos sabemos que cumplirán con las propiedades necesarias para ser una secuencia de formación:

$$\varphi_1, \ldots, \varphi_{i-1}$$

Esto porque el elemento que eliminamos está a la derecha de estos elementos en la secuencia original $s$, y por lo tanto, no afecta a estos elementos.

Nos quedaría demostrar que los elementos $\varphi_{i+1},\ldots,\varphi_n, \psi$ también cumplen con las propiedades necesarias para ser una secuencia de formación. 

Estos a priori cumplen con las propiedades necesarias para ser una secuencia de formación (porque ya eran parte de una secuencia de formación), excepto en los siguientes casos (tomando $\varphi$ como un elemento cualquiera entre los mencionados anteriormente):

1. $\varphi = (\alpha_1 * \varphi_i)$ con $*\in C_2$
2. $\varphi = (\neg\varphi_i)$

Por una parte, sabemos que todos los elementos con los que estamos trabajando son subfórmulas de $\psi$ (porque quitamos el último elemento que no era una subfórmula), pero si $\varphi$ es de algunas de las formas mencionadas anteriormente:

1. Si $\varphi = (\alpha_1 * \varphi_i)$ con $*\in C_2$ entonces $\varphi_i$ es subfórmula de $\varphi$ y por lo tanto de $\psi$. ABSURDO! $\varphi_i$ no es subfórmula de $\psi$ por hipótesis.

2. Si $\varphi = (\neg\varphi_i)$ entonces $\varphi_i$ es subfórmula de $\varphi$ y por lo tanto de $\psi$. ABSURDO! $\varphi_i$ no es subfórmula de $\psi$ por hipótesis.

Por lo tanto, hemos demostrado que $s'$ es una secuencia de formación para $\psi$.

## Resolución (parte b)

Probaremos esta parte por absurdo. 

Supongamos que tenemos una secuencia $s\in secFORM_{\psi}$ de largo mínimo para $\psi$ y que existe una fórmula $\varphi_i$ que no es subfórmula de $\psi$.

Utilizando la parte anterior, sabemos que si eliminamos $\varphi_i$ de la secuencia, la secuencia resultante sigue siendo una secuencia de formación para $\psi$.

Pero esto es absurdo, porque si la secuencia original era de largo mínimo, entonces la secuencia resultante no puede ser una secuencia de formación para $\psi$.

Esto demuestra que si $\varphi$ ocurre en una secuencia de formación de largo mínimo para $\psi$, entonces $\varphi$ es una subfórmula de $\psi$.