# Ejercicio 3

## Consigna

Considere el conjunto $\mathbb{N}$ de los números naturales. Considere un lenguaje de primer orden con un símbolo de predicado $P_1$ (unario) que denota la relación “ser par”, un símbolo de relación binario $='$ que denota la igualdad, dos símbolos de función $f_1$ y $f_2$ (binarios) que denotan la suma y el producto respectivamente y tres símbolos de constante $c_1, c_2, c_3$ que denotan las constantes 1, 2, 6.
Traduzca a fórmulas de primer orden (utilizando solamente los símbolos definidos) cada uno de los siguientes enunciados:

1. Todo natural $n$ cumple que $n^2 + n$ es par.
2. Para todo natural par $p$ existe un natural $m$ tal que $p = 2 \times m$.
3. La suma de dos naturales impares cualesquiera es un natural par.
4. Para todo natural $n$ existe un natural m tal que $n \times (n + 1) \times (n + 2) = 6 \times m$.
5. No hay ningún natural que sea par e impar a la vez.
6. Hay un natural $n$ que es par y que además cumple que $n + n = n \times n$.
7. La suma posee un neutro, que además es único.
8. La suma es una función inyectiva.

## Resolución

Primero definimos la estructura del lenguaje de la siguiente forma:

$$
E=\left<\mathbb{N},P_1,=',f_1,f_2,c_1,c_2,c_3 \right>
$$

Que tiene el siguiente tipo de similaridad:

$$
\left<1,2;2,2;3 \right>
$$

### Parte 1

Todo natural $n$ cumple que $n^2 + n$ es par.

$$
(\forall n)P_1(f_1(f_2(n,n),n))
$$

### Parte 2

Para todo natural par $p$ existe un natural $m$ tal que $p = 2 \times m$.

$$
(\forall p)(P_1(p)\to ((\exists m)p='f_2(2,m)))
$$

### Parte 3

La suma de dos naturales impares cualesquiera es un natural par.

$$
(\forall n_1)(\forall n_2)(\neg P_1(n_1)\land\neg P_1(n_2))\to P_1(f_1(n_1,n_2))
$$

### Parte 4

Para todo natural $n$ existe un natural m tal que $n \times (n + 1) \times (n + 2) = 6 \times m$.

$$
(\forall n)(\exists m)f_2(n,f_2(f_1(n,1),f_1(n,2)))='f_2(6,m)
$$

### Parte 5

No hay ningún natural que sea par e impar a la vez.

$$
\neg((\exists n)P_1(n)\land\neg P_1(n))
$$

### Parte 6

Hay un natural $n$ que es par y que además cumple que $n + n = n \times n$.

$$
(\exists n)P_1(n)\land (f_1(n,n) =' f_2(n,n))
$$

### Parte 7

La suma posee un neutro, que además es único.

$$
(\forall n_1)(\exists n_2)(f_1(n_1,n_2)=n_1)\land(((\forall n_3)f_1(n_1,n_3)=n_1)\to n_2='n_3)
$$

### Parte 8

La suma es una función inyectiva.

$$
(\forall n_1)(\forall n_2)(\forall n_3)(\forall n_4)(\neg(n_1='n_3)\land\neg(n_2='n_4))\to(\neg(f_1(n_1,n_2)='f_1(n_3,n_4)))
$$