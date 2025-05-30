# Ejercicio 8

## Consigna

Considere un lenguaje de primer orden del tipo $\langle 1,\ 1,\ 2;\ 2,\ 1;\ 0 \rangle$ con símbolos de predicado $P_1,\ P_2$ (unarios), $P_3$ (binario) y símbolos de función $f_1$ (binario), $f_2$ (unario).

Sea la estructura:

$M = \langle PROP,\ \{ \varphi\ |\ \models \varphi \},\ \{\bot\},\ \{(\varphi_1,\ \varphi_2)\ |\ \varphi_1 \text{ eq } \varphi_2\},\ F_\land,\ F_\neg \rangle$

Donde $F_\land(\varphi_1,\ \varphi_2) = (\varphi_1 \land \varphi_2)$ y $F_\neg(\varphi) = (\neg \varphi)$.

Indique si las siguientes frases son verdaderas o falsas. Justifique su respuesta.

1. $M \models (\forall x)(P_1(f_2(x)) \rightarrow ((\exists y)(P_2(y) \land P_3(x,y))))$

2. $M \models (P_1(x) \rightarrow P_2(x))$

3. $M \models (\forall x)(\forall y)(P_1(x) \land P_1(y) \rightarrow P_1(f_1(x,y)))$

## Resolución

La idea para esta parte es usar las siguientes propiedades sobre la relación $\models$:

La relación $\models$ refleja el significado intuitivo de los conectivos y los cuantificadores en las sentencias.

Sean $\alpha,\beta\in SENT$, $\gamma\in FORM, FV(\gamma)\subseteq\{x\}$. Entonces,

- $\mathcal{M}\models(\alpha\land\beta)$ sii $\mathcal{M}\models\alpha$ y $\mathcal{M}\models\beta$
- $\mathcal{M}\models(\alpha\lor\beta)$ sii $\mathcal{M}\models\alpha$ o $\mathcal{M}\models\beta$
- $\mathcal{M}\models(\neg\alpha)$ sii $\mathcal{M}\not\models\alpha$
- $\mathcal{M}\models(\alpha\to\beta)$ sii (si $\mathcal{M}\models\alpha$ entonces $\mathcal{M}\models\beta$)
- $\mathcal{M}\models(\alpha\leftrightarrow\beta)$ sii ($\mathcal{M}\models\alpha$ sii $\mathcal{M}\models\beta$)
- $\mathcal{M}\models((\forall x)\gamma)$ sii para todo $a\in|\mathcal{M}|, \mathcal{M}\models\gamma[\overline{a},x]$
- $\mathcal{M}\models((\exists x)\gamma)$ sii existe $a\in|\mathcal{M}|$ tal que $\mathcal{M}\models\gamma[\overline{a},x]$

### Parte 1

$$
\begin{aligned}
&M \models (\forall x)(P_1(f_2(x)) \rightarrow ((\exists y)(P_2(y) \land P_3(x,y))))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP) M\models P_1(f_2(\overline{\alpha})) \rightarrow ((\exists y)(P_2(y) \land P_3(\overline{\alpha},y)))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } M\models P_1(f_2(\overline{\alpha}))\text{ entonces }M\models(\exists y)(P_2(y) \land P_3(\overline{\alpha},y)))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } M\models P_1(f_2(\overline{\alpha}))\text{ entonces }(\overline{\exists}\beta\in PROP)M\models(P_2(\overline{\beta}) \land P_3(\overline{\alpha},\overline{\beta})))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } M\models P_1(f_2(\overline{\alpha}))\text{ entonces }(\overline{\exists}\beta\in PROP)(M\models P_2(\overline{\beta}) \text{ y } M\models P_3(\overline{\alpha},\overline{\beta})))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } v^M(P_1(f_2(\overline{\alpha})))=1\text{ entonces }(\overline{\exists}\beta\in PROP)(v^M(P_2(\overline{\beta}))=1 \text{ y } v^M(P_3(\overline{\alpha},\overline{\beta}))=1))\\
&\iff\scriptstyle{(\text{predicados de }M)}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } f_2(\overline{\alpha})^M\in\{ \varphi\ |\ \models \varphi \}\text{ entonces }(\overline{\exists}\beta\in PROP)(\overline{\beta}^M\in\{\bot\} \text{ y } \overline{\alpha}^M\text{ eq }\overline{\beta}^M))\\
&\iff\scriptstyle{(\text{funciones de }M\text{ e interpretación de términos})}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } \neg\overline{\alpha}^M\in\{ \varphi\ |\ \models \varphi \}\text{ entonces }(\overline{\exists}\beta\in PROP)(\beta=\bot \text{ y } \alpha\text{ eq }\bot))\\
&\iff\scriptstyle{(\text{desarrollo de conjuntos y simplificación})}\\
&(\overline{\forall}\alpha\in PROP)(\text{ Si } \models\neg\alpha\text{ entonces }\alpha\text{ eq }\bot)\\
&\iff\scriptstyle{(\text{definición de }eq)}\\
&(\overline{\forall}\alpha\in PROP)(\models\neg\alpha\implies\models\alpha\leftrightarrow\bot)\\
&\iff\scriptstyle{(\text{definición de }\models\text{ en }PROP)}\\
&(\overline{\forall}\alpha\in PROP)((\overline{\forall}v\in Val)v(\neg\alpha)=1\implies (\overline{\forall}v\in Val)v(\alpha\leftrightarrow\bot)=1)\\
&\iff\scriptstyle{(\text{definición de valuación})}\\
&(\overline{\forall}\alpha\in PROP)((\overline{\forall}v\in Val)v(\alpha)=0\implies (\overline{\forall}v\in Val)v(\alpha)=v(\bot))\\
&\iff\scriptstyle{(\text{definición de valuación: } v(\bot)=0)}\\
&(\overline{\forall}\alpha\in PROP)((\overline{\forall}v\in Val)v(\alpha)=0\implies (\overline{\forall}v\in Val)v(\alpha)=0)\\
\end{aligned}
$$

Como el antecedente y el consecuente son iguales, la propiedad es **VERDADERA**

### Parte 2

$$
\begin{aligned}
&M \models (P_1(x) \rightarrow P_2(x))\\
&\iff\scriptstyle{(\text{clausura y propiedades de }\models)}\\
&M \models (\forall x)(P_1(x) \rightarrow P_2(x))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(M\models P_1(\overline{\alpha})\to P_2(\overline{\alpha}))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{Si }M\models P_1(\overline{\alpha})\text{ entonces } M\models P_2(\overline{\alpha}))\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&(\overline{\forall}\alpha\in PROP)(\text{Si }v^M(P_1(\overline{\alpha}))=1\text{ entonces } v^M(P_2(\overline{\alpha}))=1)\\
&\iff\scriptstyle{(\text{predicados de }M)}\\
&(\overline{\forall}\alpha\in PROP)(\text{Si }\overline{\alpha}^M\in\{\alpha\mid\models\alpha\}\text{ entonces } \overline{\alpha}^M\in\{\bot\})\\
&\iff\scriptstyle{(\text{interpretación de términos y desarrollo de conjuntos})}\\
&(\overline{\forall}\alpha\in PROP)(\text{Si }\models\alpha\text{ entonces } \alpha=\bot)\\
\end{aligned}
$$

Tomemos por ejemplo $\alpha=\neg\bot$. Sabemos que $\models\neg\bot$, pero $\alpha\neq\bot$. Por lo tanto esta propiedad es **FALSA**.

### Parte 3

$$
\begin{aligned}
&M \models (\forall x)(\forall y)(P_1(x) \land P_1(y) \rightarrow P_1(f_1(x,y)))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall} \alpha,\beta\in PROP) M\models(P_1(\overline{\alpha}) \land P_1(\overline{\beta}) \rightarrow P_1(f_1(\overline{\alpha},\overline{\beta})))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall} \alpha,\beta\in PROP) (\text{Si }M\models(P_1(\overline{\alpha}) \land P_1(\overline{\beta}))\text{ entonces }M\models P_1(f_1(\overline{\alpha},\overline{\beta})))\\
&\iff\scriptstyle{(\text{propiedades de }\models)}\\
&(\overline{\forall} \alpha,\beta\in PROP) (\text{Si }(M\models P_1(\overline{\alpha})\text{ y }M\models P_1(\overline{\beta}))\text{ entonces }M\models P_1(f_1(\overline{\alpha},\overline{\beta})))\\
&\iff\scriptstyle{(\text{definición de }\models)}\\
&(\overline{\forall} \alpha,\beta\in PROP) (\text{Si }(v^M(P_1(\overline{\alpha}))=1\text{ y } v^M(P_1(\overline{\beta}))=1)\text{ entonces }v^M(P_1(f_1(\overline{\alpha},\overline{\beta})))=1)\\
&\iff\scriptstyle{(\text{interpretación de predicados y funciones de }M)}\\
&(\overline{\forall} \alpha,\beta\in PROP) (\text{Si }(\overline{\alpha}^M\in\{\varphi\mid\models\varphi\}\text{ y }\overline{\beta}^M\in\{\varphi\mid\models\varphi\} )\text{ entonces }f_1(\overline{\alpha},\overline{\beta})^M\in\{\varphi\mid\models\varphi\})\\
&\iff\scriptstyle{(\text{desarrollo de conjuntos e interpretación de términos de }M)}\\
&(\overline{\forall} \alpha,\beta\in PROP) (\text{Si }(\models\alpha\text{ y }\models\beta)\text{ entonces }(\overline{\alpha}^M\land\overline{\beta}^M)\in\{\varphi\mid\models\varphi\})\\
&\iff\scriptstyle{(\text{desarrollo de conjuntos e interpretación de términos de }M)}\\
&(\overline{\forall} \alpha,\beta\in PROP)((\models\alpha\text{ y }\models\beta)\implies\models(\alpha\land\beta))\\
&\iff\scriptstyle{(\text{definición de }\models\text{ en }PROP)}\\
&(\overline{\forall} \alpha,\beta\in PROP)((\overline{\forall}v\in Val)v(\alpha)=1\text{ y }(\overline{\forall}v\in Val)v(\beta)=1\implies(\forall v\in Val) v(\alpha\land\beta)=1)\\
&\iff\scriptstyle{(\text{definición de valuación})}\\
&(\overline{\forall} \alpha,\beta\in PROP)((\overline{\forall}v\in Val)v(\alpha)=1\text{ y }(\overline{\forall}v\in Val)v(\beta)=1\implies(\forall v\in Val) \min\{v(\alpha),v(\beta)\}=1)\\
\end{aligned}
$$

Con esto vemos que la propiedad es **VERDADERA**, pues $\min\{v(\alpha),v(\beta)\}=\min\{1,1\}$ por el antecedente. Y esto último obviamente es igual a 1.