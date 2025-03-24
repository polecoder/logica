# Ejercicio 4

## Consigna

Considere $\varphi, \psi, \sigma$ pertenecientes a $PROP$.

(a) Pruebe las siguientes consecuencias lógicas:

1. $\varphi \models \varphi$

2. $\varphi \lor \psi, \neg \psi \models \varphi$

3. $(\varphi \land \psi), (\psi \land \sigma) \models (\varphi \land \sigma)$

(b) Demuestre que:

1. Si $\varphi \models \psi$ y $\psi \models \sigma$, entonces $\varphi \models \sigma$

2. Si $\models \varphi \to \psi$, entonces $\varphi \models \psi$

3. Si $\models \neg \varphi$ y $\psi \models \varphi$, entonces $\models \neg \psi$

4. Si $\Gamma \models \varphi$ y $\Gamma \models \neg \psi$, entonces $\Gamma \models \neg (\neg \varphi \lor \psi)$ (donde $\Gamma \subseteq PROP$)

## Resolución (parte a)

Para esta parte usamos la definición de valuación para determinar si las fórmulas dadas son tautologías. Podríamos usar de forma alternativa el concepto de Tableau Semántico.

### 1. $\varphi \models \varphi$

Sea $v$ una valuación tal que $v(\varphi) = 1$, luego:

$$
\begin{aligned}
&v(\varphi)\\
&= {\scriptstyle \text{(hipótesis)}}\\
&1
\end{aligned}
$$

Como cualquier valuación dada en este contexto cumple que $v(\varphi) = 1$, podemos concluir que $\varphi\models\varphi$

### 2. $\varphi \lor \psi, \neg \psi \models \varphi$

Sea $v$ una valuación tal que $v(\varphi \lor \psi) = 1$ y $v(\neg \psi) = 1$, luego:

#### PARTE 1: $v(\varphi \lor \psi) = 1$

$$
\begin{aligned}
&v(\varphi\lor\psi)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&max\{v(\varphi), v(\psi)\}\\
&= {\scriptstyle \text{(hipótesis)}}\\
&1
\end{aligned}
$$

#### PARTE 2: $v(\neg \psi) = 1$

$$
\begin{aligned}
&v(\neg \psi)=1-v(\psi)\\
&\iff {\scriptstyle \text{(hipótesis)}}\\
&1-v(\psi) = 1\\
&\iff {\scriptstyle \text{(despeje)}}\\
&v(\psi) = 0
\end{aligned}
$$

Entonces ahora juntando con la primer parte, tenemos que:

$$
\begin{aligned}
&v(\varphi\lor\psi)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&max\{v(\varphi), v(\psi)\}\\
&= {\scriptstyle \text{(por parte 2)}}\\
&max\{v(\varphi), 0\}\\
&= {\scriptstyle \text{(hipótesis)}}\\
&1
\end{aligned}
$$

Entonces $v(\varphi) = 1$, por lo que podemos concluir que $\varphi \lor \psi, \neg \psi \models \varphi$

### 3. $(\varphi \land \psi), (\psi \land \sigma) \models (\varphi \land \sigma)$

Sea $v$ una valuación tal que $v(\varphi \land \psi) = 1$ y $v(\psi \land \sigma) = 1$, luego:

#### PARTE 1: $v(\varphi \land \psi) = 1$

$$
\begin{aligned}
&v(\varphi\land\psi)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&min\{v(\varphi), v(\psi)\}\\
&= {\scriptstyle \text{(hipótesis)}}\\
&1\\
&\Rightarrow {\scriptstyle \text{(despeje)}}\\
&v(\varphi) = 1; v(\psi) = 1
\end{aligned}
$$

#### PARTE 2: $v(\psi \land \sigma) = 1$

$$
\begin{aligned}
&v(\psi \land \sigma)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&min\{v(\psi), v(\sigma)\}\\
&= {\scriptstyle \text{(hipótesis)}}\\
&1\\
&\Rightarrow {\scriptstyle \text{(despeje)}}\\
&v(\psi) = 1; v(\sigma) = 1
\end{aligned}
$$

Ahora juntando ambas partes, tenemos que:

$$
\begin{aligned}
&v(\varphi \land \sigma)\\
&= {\scriptstyle \text{(definición de valuación)}}\\
&min\{v(\varphi), v(\sigma)\}\\
&= {\scriptstyle \text{(parte 1 y 2)}}\\
&min\{1, 1\}\\
&= {\scriptstyle \text{(despeje)}}\\
&1
\end{aligned}
$$

Como cualquier valuación dada en este contexto cumple que $v(\varphi \land \sigma) = 1$, podemos concluir que $(\varphi \land \psi), (\psi \land \sigma) \models (\varphi \land \sigma)$

## Resolución (parte b)

Para esta parte usaremos el concepto de absurdo combinado con la definición de valuación.

### 1. Si $\varphi \models \psi$ y $\psi \models \sigma$, entonces $\varphi \models \sigma$

(H) $\varphi \models \psi$ y $\psi \models \sigma$

(T) $\varphi \models \sigma$

Usando las hipótesis tenemos que:

#### PARTE 1

$$
\begin{aligned}
&\varphi \models \psi\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid \text{Si }v(\varphi) = 1\text{, entonces }v(\psi) = 1\\
\end{aligned}
$$

#### PARTE 2

$$
\begin{aligned}
&\psi \models \sigma\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid \text{Si }v(\psi) = 1\text{, entonces }v(\sigma) = 1\\
\end{aligned}
$$

Queremos probar que para una valuación $v$ cualquiera se cumple la tesis, partamos de que $v(\varphi) = 1$:

$$
\begin{aligned}
&v(\varphi) = 1\\
&\Rightarrow {\scriptstyle \text{(por parte 1)}}\\
&v(\psi) = 1\\
&\Rightarrow {\scriptstyle \text{(por parte 2)}}\\
&v(\sigma) = 1
\end{aligned}
$$

Entonces, como cualquier valuación dada en este contexto cumple que $v(\varphi) = 1$ implica $v(\sigma) = 1$, podemos concluir que $\varphi \models \sigma$

### 2. Si $\models \varphi \to \psi$, entonces $\varphi \models \psi$

En este caso podemos trabajar con absurdo ya que tenemos una sola hipótesis.

Veamos que pasa si $\varphi\not\models\psi$:

$$
\begin{aligned}
&\varphi\not\models\psi\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\exists v_1\in Val)\mid v_1(\varphi) = 1;v_1(\psi) = 0\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&v_1(\varphi \to \psi) = 0\\
&\Rightarrow {\scriptstyle \text{(hipótesis)}}\\
&\text{ABSURDO!}
\end{aligned}
$$

Esto es absurdo porque por hipótesis sabemos que $\models \varphi \to \psi$.

Entonces, tenemos que si $\models \varphi \to \psi$, entonces $\varphi\models\psi$.

### 3. Si $\models \neg \varphi$ y $\psi \models \varphi$, entonces $\models \neg \psi$

(H) $\models \neg \varphi$ y $\psi \models \varphi$

(T) $\models \neg \psi$

Usando las hipótesis tenemos que:

#### PARTE 1

$$
\begin{aligned}
&\models\neg\varphi\\
&\iff {\scriptstyle \text{(definición de tautología)}}\\
&(\forall v\in Val)\mid v(\neg\varphi) = 1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid v(\varphi) = 0
\end{aligned}
$$

#### PARTE 2

$$
\begin{aligned}
&\psi \models \varphi\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid \text{Si }v(\psi) = 1\text{, entonces }v(\varphi) = 1\\
&\Rightarrow {\scriptstyle (\text{por parte 1: }v(\varphi)=0)}\\
&(\forall v\in Val)\mid v(\psi)\neq 1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid v(\psi)=0
\end{aligned}
$$

Queremos probar que para una valuación $v$ cualquiera se cumple la tesis:

$$
\begin{aligned}
&\models\neg\psi\\
&\iff {\scriptstyle \text{(definición de tautología)}}\\
&(\forall v\in Val)\mid v(\neg\psi)=1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid v(\psi)=0
\end{aligned}
$$

Donde esto último se cumple para toda valuación $v$ por la parte 2.

### 4. Si $\Gamma \models \varphi$ y $\Gamma \models \neg \psi$, entonces $\Gamma \models \neg (\neg \varphi \lor \psi)$

(H) $\Gamma \models \varphi$ y $\Gamma \models \neg \psi$

(T) $\Gamma \models \neg (\neg \varphi \lor \psi)$

Usando las hipótesis tenemos que las valuaciones $v$ cumplen que:

#### PARTE 1

$$
\begin{aligned}
&\Gamma \models \varphi\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\varphi)=1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\neg\varphi)=0\\
\end{aligned}
$$

#### PARTE 2

$$
\begin{aligned}
&\Gamma \models \neg\psi\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\neg\psi)=1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\psi)=0\\
\end{aligned}
$$

Veamos que pasa por absurdo si $\Gamma\not\models\neg(\neg\varphi\lor\psi)$:

$$
\begin{aligned}
&\Gamma\not\models\neg(\neg\varphi\lor\psi)\\
&\iff {\scriptstyle \text{(definición de consecuencia lógica)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\neg(\neg\varphi\lor\psi))=0\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }v(\neg\varphi\lor\psi)=1\\
&\Rightarrow {\scriptstyle \text{(definición de valuación)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }min\{v(\neg\varphi),v(\psi)\}=1\\
&\Rightarrow {\scriptstyle \text{(por parte 1 y parte 2)}}\\
&(\forall v\in Val)\mid\text{Si }(\forall \alpha\in\Gamma)v(\alpha) = 1\text{, entonces }min\{0,0\}=1\\
&\Rightarrow {\scriptstyle \text{(operatoria)}}\\
&\text{ABSURDO!}
\end{aligned}
$$

Entonces si $\Gamma \models \varphi$ y $\Gamma \models \neg \psi$, entonces $\Gamma \models \neg (\neg \varphi \lor \psi)$