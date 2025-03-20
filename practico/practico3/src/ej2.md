# Ejercicio 2

## Consigna

Coloque letras proposicionales en lugar de $p_i$ de forma que la fórmula obtenida sea una tautología. ¿Puede realizar esta tarea en todos los casos? Justifique.

(a) $p \to p_i$

(b) $(p \to q) \to ((q \to p_i) \to (p \to r))$

(c) $(p \to (q \to r)) \to (p_i \to (p \to p_i))$

(d) $(p \to q) \to p_i$

(e) $(p \to (q \to r)) \to ((p_i \to q) \to (p \to r))$

(f) $((p \to q) \to p) \to p_i$

## Resolución

Enfrentaremos este problema usando el concepto de tableau semántico. Lo aplicaremos de una forma diferente debido a que su implementación en ese ambiente es complejo.

### Parte (a)

Queremos verificar cuando la proposición $p\rightarrow p_i$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

- $F.\quad p\rightarrow p_i$
    1. $V.\quad p$
    2. $F.\quad p_i$

A partir de esto ya tenemos la respuesta, como no queremos que el primer paso sea falso, tenemos que encontrar una contradicción en la rama del árbol. La única forma de que pase esto es que $p_i = p$
Por lo que esto nos deja con la proposición:

$$
\models p\rightarrow p
$$

### Parte (b)

Queremos verificar cuando la proposición $(p \to q) \to ((q \to p_i) \to (p \to r))$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

![Tableau semántico parte b](/practico/practico3/images/ej2fig1.png)

Para que la proposición sea una tautología queremos encontrar una contradicción en todas las ramas del árbol. Observemos que para que esto suceda, $p_i = r$, para que también la última rama tenga una contradicción. Esto con deja con la proposición

$$
\models (p \to q) \to ((q \to r) \to (p \to r))
$$

### Parte (c)

Queremos verificar cuando la proposición $(p \to (q \to r)) \to (p_i \to (p \to p_i))$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

![Tableau semántico parte c](/practico/practico3/images/ej2fig2.png)

Para que la proposición sea una tautología queremos encontrar una contradicción en todas las ramas del árbol. Observemos que no importa el valor de $p_i$, siempre tendremos una contradicción.

$$
\models (p \to (q \to r)) \to (p_i \to (p \to p_i))
$$

### Parte (d)

Queremos verificar cuando la proposición $(p \to q) \to p_i$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

![Tableau semántico parte d](/practico/practico3/images/ej2fig3.png)

Para que la proposición sea una tautología queremos encontrar una contradicción en todas las ramas del árbol. Observemos que sin importar el valor de $p_i$ la primer rama nunca podrá contener una contradicción , ya que nos dice que ambas letras proposicionales en juego siempre serán falsas.

$$
\not\models (p \to q) \to p_i
$$

### Parte (e)

Queremos verificar cuando la proposición $(p \to (q \to r)) \to ((p_i \to q) \to (p \to r))$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

![Tableau semántico parte e](/practico/practico3/images/ej2fig4.png)

Para que la proposición sea una tautología queremos encontrar una contradicción en todas las ramas del árbol. Observemos hay una sola rama que no tiene una contradicción, la única forma de que esta lo sea es si $p_i = p$. Esto nos deja con la proposición:

$$
\models (p \to (q \to r)) \to ((p \to q) \to (p \to r))
$$

### Parte (f)

Queremos verificar cuando la proposición $((p \to q) \to p) \to p_i$ es tautología según quién es $p_i$. Apliquemos el concepto de Tableau semántico.

![Tableau semántico parte f](/practico/practico3/images/ej2fig5.png)

Para que la proposición sea una tautología queremos encontrar una contradicción en todas las ramas del árbol. Observemos hay una dos ramas que no tienen una contradicción, pero si $p_i = p$, en ambas encontramos una contradicción. Por lo que esto nos deja con la proposición

$$
\models ((p \to q) \to p) \to p
$$