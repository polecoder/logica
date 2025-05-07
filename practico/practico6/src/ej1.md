# Ejercicio 1

## Consigna

Considere un conjunto $A$ de números reales que incluya al 0. Considere un lenguaje de primer orden con un símbolo de relación binario $M$ que denota la relación $<$ de los reales y otro símbolo binario $='$ que denota la igualdad.
Considere un símbolo de función binario $m$ que denota la multiplicación.
Podemos usar el lenguaje de primer orden para expresar propiedades. Por ejemplo, la propiedad "ser neutro" puede expresarse como:

$$
SER\_NEUTRO(x_1) := (\forall x_2)m(x_2,x_1)='x_2
$$

Usando solamente los símbolos dados, escriba fórmulas de primer orden que expresen las siguientes nociones.

1. $x_1$ es el máximo de $A$
2. $x_1$ es un sucesor inmediato de $x_2$
3. No hay elementos entre $x_1$ e $x_2$
4. La función cuadrado es creciente

## Resolución

Primero definimos la estructura del lenguaje de la siguiente forma:

$$
E=\left<A,M,=',m,0 \right>
$$

### Parte 1

$$
ES\_MAXIMO(x_1):=(\forall x_2)M(x_2,x_1)\lor (x_2='x_1)
$$

### Parte 2

$$
ES\_SUCESOR(x_1,x_2):=M(x_2,x_1)\land\neg((\exists x_3)(M(x_2,x_3)\land M(x_3,x_1)))
$$

### Parte 3

$$
SIN\_INTERMEDIOS(x_1,x_2):=ES\_SUCESOR(x_1,x_2)\lor ES\_SUCESOR(x_2,x_1)
$$

### Parte 4

$$
(\forall x_1)(\forall x_2)(M(x_1,x_2))\to M(m(x_1,x_1),m(x_2,x_2))
$$