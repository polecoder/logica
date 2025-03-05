# Ejercicio 4

## Consigna

Sea la siguiente propiedad:

*Para toda $\varphi$ subfórmula de $\psi$, $\varphi$ ocurre en cualquier secuencia de formación para $\psi$.*

Dé una prueba inductiva de la misma.

## Resolución

### Premisa

Para resolver este ejercicio demos algo de notación para poder formalizar la proposición y ver como aplicar inducción:

- Llamemos $secFORM_{\psi}$ al conjunto de todas las secuencias de formación para $\psi$.
- $s\in secFORM_{\psi}$, $|s|$ es la longitud de la secuencia $s$.
- $s\in secFORM_{\psi},\psi\in PROP;\psi\in s$ significa que $\psi$ ocurre en $s$

Con esto podemos describir más formalmente la propiedad que queremos probar de la siguiente forma.

$$
(\forall\psi\in PROP)(\forall\varphi\in PROP)\\
(\varphi\text{ subfórmula }\psi\Rightarrow(\forall s\in secFORM_{\psi})(\varphi\in s))
$$

Esto nos da las herramientas necesarias para poder aplicar inducción.

### Recordatorio (PIP para $PROP$)

Sea $\mathcal{P}$ una propiedad sobre las palabras de $PROP$ que cumple:

*BASE1*: $\mathcal{P}(p)$ para todo $p\in P$
*BASE2*: Se cumple $\mathcal{P}(\bot)$
*IND1*: Para todo $*\in C_2$ y $\alpha,\beta\in PROP$ que cumplen $\mathcal{P}(\alpha)$ y $\mathcal{P}(\beta)$, se cumple $\mathcal{P}((\alpha * \beta))$
*IND2*: Para todo $\alpha\in PROP$ que cumple $\mathcal{P}(\alpha)$, se cumple $\mathcal{P}((\neg\alpha))$

Entonces, $\mathcal{P}$ se cumple para todas las palabras de $PROP$.

### Comienzo del ejercicio

Observemos que para aplicar inducción tenemos que primero llevar a la propiedad a una forma más adecuada para probarla con el PIP de $PROP$. Determinemos sobre cuál de las dos proposiciones ($\psi, \varphi$) queremos aplicar el PIP:

- Si fijamos $\varphi$, no podemos decir casi nada sobre $\psi$, esto porque estaríamos trabajando con una subfórmula de una proposición arbitraria.

- En cambio si fijamos $\psi$, podemos decir algo sobre todas las subfórmulas de $\psi$, especialmente en los casos más triviales donde $\psi$ es una variable proposicional o una constante lógica.

Por lo tanto, fijaremos $\psi$ y aplicaremos inducción sobre la estructura de $\psi$, la propiedad que queremos probar se convierte en:

$$
P(\psi):(\forall\varphi\in PROP)(\varphi\text{ subfórmula }\psi\Rightarrow(\forall s\in secFORM_{\psi})(\varphi\in s))
$$

#### PASO BASE

##### PARTE 1

$P(p_i): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }p_i\Rightarrow(\forall s\in secFORM_{p_i})(\varphi\in s))$

Para este caso, como $p_i\in AT$ sabemos que su única subfórmula es si misma.
Por otra parte, cualquier secuencia de formación para $p_i$ debe terminar en si misma por construcción, por lo que $\varphi\in s\quad\forall\varphi\in\{p_i\}$.

##### PARTE 2

$P(\bot): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }\bot\Rightarrow(\forall s\in secFORM_{\bot})(\varphi\in s))$

Para este caso, como $\bot\in AT$ sabemos que su única subfórmula es si misma.
Por otra parte, cualquier secuencia de formación para $\bot$ debe terminar en $\bot$ por construcción, por lo que $\varphi\in s\quad\forall\varphi\in\{\bot\}$.

#### PASO INDUCTIVO

(H) $P(\psi): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }\psi\Rightarrow(\forall s\in secFORM_{\psi})(\varphi\in s))$

##### PARTE 1

(T) $P(\neg\psi): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }(\neg\psi)\Rightarrow(\forall s\in secFORM_{(\neg\psi)})(\varphi\in s))$

Vayamos con lo primero, para que $\varphi$ sea subfórmula de $(\neg\psi)$, tiene que cumplir uno de lo siguientes:

- $\varphi = (\neg\psi)$
- $\varphi$ es subfórmula de $\psi$

Si $\varphi = (\neg\psi)$, la propiedad se cumple porque $(\neg\psi)$ tiene que estar al final de todas las secuencias de formación para $(\neg\psi)$ por construcción.

Si $\varphi$ es subfórmula de $\psi$, nos veríamos muy tentados de usar la hipótesis inductiva, pero esta se cumple para $secFORM_{\psi}$, no para $secFORM_{(\neg\psi)}$. Por lo que no podemos aplicarla directamente, para esto introducimos el siguiente lema:

###### LEMA

El prefijo de una secuencia de formación para $(\neg\psi)$ es una secuencia de formación para $\psi$.

**Demostración:**

Sea $s\in secFORM_{(\neg\psi)}$, entonces $s$ tiene la forma:

$$
s = \{p_1,p_2,\ldots,p_n,\alpha,\ldots,\psi,\beta,\ldots,(\neg\psi)\}
$$

Sabemos que $s$ es una secuencia de formación, por lo tanto si quitamos elementos de $s$ del lado derecho (es decir que ningún elemento depende de ellos), seguiremos teniendo una secuencia de formación. Mantengamos el siguiente conjunto:

$$
s' = \{p_1,p_2,\ldots,p_n,\alpha,\ldots,\psi\}
$$

Por la forma en la que quitamos elementos, $s'$ sigue siendo una secuencia de formación, y como su último elemento es $\psi$, $s'$ es una secuencia de formación para $\psi$.

##### Continuación

Ahora, usando la hipótesis tenemos que:

$$P(\psi): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }\psi\Rightarrow(\forall s\in secFORM_{\psi})(\varphi\in s))$$

Entonces, como nosotros sabemos que $\varphi$ es subfórmula de $\psi$, podemos decir que $(\forall s\in secFORM_{\psi})(\varphi\in s)$.

Observemos que para cualquier secuencia de formación $s\in secFORM_{(\neg\psi)}$ podemos tomar su prefijo $s'\in secFORM_{\psi}$ que es una secuencia de formación para $\psi$, por lo que $\varphi\in s'$, y como $s'$ es prefijo de $s$, $\varphi\in s$. 

Esto prueba la propiedad para $(\neg\psi)$.

##### PARTE 2

(T) $P((\alpha*\beta)): (\forall\varphi\in PROP)(\varphi\text{ subfórmula }(\alpha*\beta)\Rightarrow(\forall s\in secFORM_{(\alpha*\beta)})(\varphi\in s))$

En primer lugar, para que $\varphi$ sea subfórmula de $(\alpha*\beta)$, tiene que cumplir uno de lo siguientes:

- $\varphi = (\alpha*\beta)$
- $\varphi$ es subfórmula de $\alpha$
- $\varphi$ es subfórmula de $\beta$

Si $\varphi = (\alpha*\beta)$, la propiedad se cumple porque $(\alpha*\beta)$ tiene que estar al final de todas las secuencias de formación para $(\alpha*\beta)$ por construcción.

Para los otros dos casos, podemos aplicar la hipótesis inductiva, ya que $\varphi$ es subfórmula de $\alpha$ o $\beta$, y por lo tanto $\varphi\in s\quad\forall s\in secFORM_{\alpha}$ o $\varphi\in s\quad\forall s\in secFORM_{\beta}$.

Pero si $s$ está en la secuencia de formación de $\alpha$ o $\beta$, también está en la secuencia de formación de $(\alpha*\beta)$ por construcción, por lo que $\varphi\in s\quad\forall s\in secFORM_{(\alpha*\beta)}$.

Esto prueba la propiedad para $(\alpha*\beta)$, y termina la prueba total.

### Conclusión

Entiendo que la segunda parte del paso inductivo no necesita un lema, pero lo que estamos dando por entendido es que si $\varphi$ es subfórmula de $\alpha$ o $\beta$, entonces $\varphi$ es subfórmula de $(\alpha*\beta)$. Me da la sensación que esto es directo de la definición de subfórmula, pero no estoy seguro.