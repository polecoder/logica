# CLASE 1 - 10/02/2025

## Inducción

### Ejemplo (definición inductiva de los naturales)

La definición inductiva de los números naturales es la siguiente:

1. $0 \in \mathbb{N}$
2. Si $n \in \mathbb{N}$, entonces $n+1 \in \mathbb{N}$

### Idea

Para definir un conjunto $A$ inductivamente, debemos seguir algunos pasos:

1. Indicar el universo en el que nos paramos
2. Indicar los elementos que pertenecen a $A$ sin necesidad de justificación (los elementos base)
3. Indicar cómo se construyen nuevos elementos de $A$ a partir de los que ya tenemos con el paso 2

Con esto podemos entender lo que hicimos en el ejemplo de la construcción del conjunto $\mathbb{N}$

### Visiones

Tenemos dos visiones para entender el conjunto formado por las reglas que establecimos al definir un conjunto inductivamente:

1. **Visión constructiva**: Entendemos el conjunto como el conjunto de elementos que se pueden construir a partir de los elementos base y las reglas de construcción.

2. **Visión declarativa**: Se considera la familia de subconjuntos del universo que cumplen con las reglas dadas. El conjunto que definimos inductivamente es el mínimo de todos los subconjuntos que cumplen con las reglas (o la intersección de todos los subconjuntos que cumplen con las reglas).

**Observación**: La visión constructiva es más intuitiva, mientras que la declarativa se puede ver mejor si no miramos los elementos base del conjunto. Haciendo eso podemos definir más que el conjunto de los naturales $\mathbb{N}$, que no es lo que queremos.

### Ejemplo (definición inductiva de los números pares)

La definición inductiva de los números pares es la siguiente:

1. $0 \in \mathbb{P}$
2. Si $n \in \mathbb{P}$, entonces $n+2 \in \mathbb{P}$

**Observación**: Decimos que el conjunto base es $\{0\}$, como lo establecen las reglas.

**Otra definición**: Veamos otra forma de definirlo:

1. $0 \in \mathbb{P}'$
2. $2 \in \mathbb{P}'$
3. Si $n \in \mathbb{P}'$, entonces $n+4 \in \mathbb{P}'$

Esto también nos da el conjunto de los pares, pero la definición es diferente. El conjunto base de este caso es $\{0,2\}$.

### Observación

Es importante entender que la definición que damos a un conjunto, cambia varias cosas en la forma de verlo, por más que no cambie el conjunto. Por ejemplo, la forma de mostrar que un elemento es par o no, cambia según la definición que tengamos del mismo.