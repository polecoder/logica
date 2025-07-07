# CLASE 17 - 04/07/2025

## Semántica de la lógica proposicional

### Equivalencia y generalización de las Leyes de De Morgan

#### Teorema 2.5.1 (Leyes de De Morgan generalizadas)

##### (CONTINUACIÓN) Demostración: $\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha$

Entonces, con el procedimiento que realizamos nos surgen algunas complicaciones:

1. Por fuera queda siempre $\overline{\forall}\mathcal{M}$.
2. Se arrastran constantes que surgen de la clausura.

Veamos una posible solución para cada problema:

1. Una práctica muy común en matemáticas, cuando no hay suposiciones adicionales sobre un elemento, considerar un elemento cualquiera. Si hubiera consideraciones adicionales hay que tenerlas en cuenta.
2. Veamos una mejora para las constantes:
    - El problema es acarrear las constantes del lenguaje extendido durante toda la demostración
    - Para esto podemos separar la prueba en dos partes: primero probarlo para sentencias, y luego usar esa prueba para probar el caso general

**Demostración: $\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha$ para sentencias**

Suponemos que $FV(\alpha)\subseteq\{x\}$. Queremos probar que:

$$
(\overline{\forall}\mathcal{M})\mathcal{M}\models\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha
$$

Tomando $\mathcal{M}$ de tipo adecuado cualquiera, hay que probar que:

$$
\mathcal{M}\models\neg(\forall x)\alpha\leftrightarrow(\exists x)\neg\alpha
$$

Aplicando 2.4.5, tenemos que probar:

$$
\mathcal{M}\models\neg(\forall x)\alpha\iff\mathcal{M}\models(\exists x)\neg\alpha\quad(i)
$$

Probemos $(i)$:

$$
\begin{aligned}
&\mathcal{M}\models\neg(\forall x)\alpha\\
&\iff\scriptstyle{(\text{2.4.5})}\\
&\mathcal{M}\not\models(\forall x)\alpha\\
&\iff\scriptstyle{(\text{2.4.5})}\\
&(\overline{\exists}a\in |\mathcal{M}|)\mathcal{M}\not\models \alpha[\overline{a}/x]\\
&\iff\scriptstyle{(\text{2.4.5})}\\
&(\overline{\exists}a\in |\mathcal{M}|)\mathcal{M}\models\neg\alpha[\overline{a}/x]\\
&\iff\scriptstyle{(\text{2.4.5})}\\
&\mathcal{M}\models(\exists x)\neg\alpha
\end{aligned}
$$

Con esto, podemos volver al primer paso probando lo que queríamos para las sentencias.

**Demostración: $\neg(\forall x)\alpha\text{ eq }(\exists x)\neg\alpha$ en general**

Para esta parte repetimos el mismo proceso, y cuando clausuremos la fórmula vamos a obtener una sentencia, para la cual ya sabemos que la propiedad se cumple.

#### Propiedades de los cuantificadores

- $(\forall x)(\forall y)\alpha\text{ eq }(\forall y)(\forall x)\alpha$
- $(\exists x)(\exists y)\alpha\text{ eq }(\exists y)(\exists x)\alpha$
- $(\forall x)\alpha\text{ eq }\alpha$ si $x\notin FV(\alpha)$
- $(\exists x)\alpha\text{ eq }\alpha$ si $x\notin FV(\alpha)$

#### Teorema 2.5.6 (cambio de variables)

Sean $x,z$ tales que $x,z\notin FV(\alpha)$. En estas condiciones se cumplen las siguientes propiedades:

- $((\forall x)\alpha)[x/y]\text{ eq }((\forall z)\alpha)[z/y]$
- $((\exists x)\alpha)[x/y]\text{ eq }((\exists z)\alpha)[z/y]$

##### Informalmente

Sea $z$ tal que $z\notin FV(\alpha)$.
En estas condiciones se cumplen las siguientes propiedades:

- $(\forall x)\alpha(x)\text{ eq }(\forall z)\alpha(z)$
- $(\exists x)\alpha(x)\text{ eq }(\exists z)\alpha(z)$

#### Teorema 2.5.3 (distributividad generalizada)

- $(\forall x)(\alpha\land\beta)\text{ eq }(\forall x)\alpha\land(\forall x)\beta$
- $(\exists x)(\alpha\lor\beta)\text{ eq }(\exists x)\alpha\lor(\exists x)\beta$
- $(\forall x)(\alpha\lor\beta)\text{ eq } (\forall x)\alpha\lor\beta$ con $x\notin FV(\beta)$
- $(\exists x)(\alpha\land\beta)\text{ eq } (\exists x)\alpha\land\beta$ con $x\notin FV(\beta)$
- $(\forall x)(\alpha\to\beta)\text{ eq }(\exists x)\alpha\to\beta$ con $x\notin FV(\beta)$
- $(\exists x)(\alpha\to\beta)\text{ eq }(\forall x)\alpha\to\beta$ con $x\notin FV(\beta)$
- $(\forall x)(\alpha\to\beta)\text{ eq }\alpha\to(\exists x)\beta$ con $x\notin FV(\alpha)$
- $(\exists x)(\alpha\to\beta)\text{ eq }\alpha\to(\forall x)\beta$ con $x\notin FV(\alpha)$

Más propiedades:

- $\models(\forall x)\alpha\lor(\forall x)\beta\to(\forall x)(\alpha\lor\beta)$
- $\models(\exists x)(\alpha\land\beta)\to(\exists x)\alpha\land(\exists x)\beta$

#### Propiedades de sustitución

1. Si $z\notin FV(t)$ entonces $t[c/x]=t[z/x][c/z]$
2. Si $z$ no ocurre en $\alpha$ entonces $\alpha[c/x]=\alpha[z/x][c/z]$
3. Sea $t$ libre para $x$ en $\alpha$ y $\beta$, y $\beta$ libre para $\$$ en $\alpha$. Entonces, $\alpha[\beta/\$][t/x]=\alpha[t/x][\beta[t/x]/\$]$

#### Teorema 2.5.6 de sustitución

Sean $s,t,t'\in TERM,\alpha,\beta,\varphi\in FORM$ tal que $t$  y $t'$ están libres para $x$ en $\alpha$, y $\alpha$ y $\beta$ están libres para $\$$ en $\varphi$. Entonces:

- $\models t='t'\to s[t/x]='s[t'/x]$
- $\models t='t'\to\alpha[t/x]\leftrightarrow\alpha[t'/x]$
- $\models(\alpha\leftrightarrow\beta)\to(\varphi[\alpha/\$]\leftrightarrow\varphi[\beta/\$])$

##### Más propiedades

1. Sean $\alpha,\beta,\varphi\in FORM$ tales que $\models\alpha\leftrightarrow\beta$ (sin importar si $\alpha$ y $\beta$ están libres para $\$$ en $\varphi$). Entonces:

    $$
    \models\varphi[\alpha/\$]\leftrightarrow\varphi[\beta/\$]
    $$

2. Sean $\alpha,\beta\in FORM$ tales que $\models\alpha\leftrightarrow\beta$. Entonces:

    - $(\forall x)\alpha\leftrightarrow(\forall x)\beta$
    - $(\exists x)\alpha\leftrightarrow(\exists x)\beta$

##### Idea

La idea de todo esto es formalizar la noción muy interiorizada que tenemos sobre sustituir expresiones equivalentes entre si.

### Forma normal prenexa

Sea $\alpha\in FORM$. Decimos que $\alpha$ está en forma normal prenexa sii $\alpha$ es una fórmula abierta precedida de cero o más cuantificadores. Por ejemplo:

- $(\forall x)(\exists y)(\forall z)(\forall w)(f(z,w)='x\to f(w,z)='y)$

#### Teorema 2.5.8

Para toda $\alpha\in FORM$ existe $\beta$ tal que $\beta$ está en forma normal prenexa y $\alpha\text{ eq }\beta$

### Relativización

Como podemos traducir la siguiente oración?

- $(\forall\varepsilon>0)(\exists n)(\forall m > n)|f(n)-f(m)|<\varepsilon$

Primero tengamos en cuenta que hay convenciones para los nombres de variables:

- $\varepsilon\in\mathbb{R}$
- $m,n\in\mathbb{N}$

Una primera traducción sería:

$$
(\forall\varepsilon)(\varepsilon>0\to(\exists n\in\mathbb{N})(\forall m\in\mathbb{N})(m>n\to|f(n)-f(m)|)<\varepsilon)
$$

Para terminar la traducción, definamos la siguiente estructura:

- $\mathcal{R}=\{\mathbb{R},\mathbb{N}, >,f, F, 0\}$ donde $F(a,b)=|f(a)-f(b)|$

Por lo tanto ahora ser un natural es un nuevo predicado:

$$
(\forall\varepsilon)(\varepsilon>0\to(\exists n)\mathbb{N}(n)\land(\forall m)(\mathbb{N}(m)\to(m>n\to\varepsilon>F(n,m)))<\varepsilon)
$$

#### Cuantificadores relativizados

Se definien cuantificadores relativizados para esto:

- $(\forall n\in\mathbb{N})\alpha:=(\forall n)(\mathbb{N}(n)\to\alpha)$
- $(\exists n\in\mathbb{N})\alpha:=(\exists n)(\mathbb{N}(n)\land\alpha)$