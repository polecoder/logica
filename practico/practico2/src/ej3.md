# Ejercicio 3

## Consigna

(a) Dé por lo menos dos secuencias de formación de largo diferente para cada una de las proposiciones del Ejercicio 1.

(b) Dé por lo menos dos secuencias de formación diferentes de largo mínimo para:

$$
((((p_1 \to p_2) \to p_1) \to p_2) \to p_1)
$$

## Resolución (parte a)

### Proposición 1

La proposición de este caso es la siguiente:

$$(((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))) \land (\neg p_3)) \in PROP$$

#### Secuencia 1

$$
\{p_1,p_2,p_3,(\neg p_2), (\neg p_3), (p_1\leftrightarrow p_2), (p_3 \lor (p_1 \leftrightarrow p_2)),\\((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))), (((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))) \land (\neg p_3))\}
$$

#### Secuencia 2

$$
\{p_1,p_2,p_3,\bot,(\neg p_2), (\neg p_3), (p_1\leftrightarrow p_2), (p_3 \lor (p_1 \leftrightarrow p_2)),\\((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))), (((\neg p_2) \to (p_3 \lor (p_1 \leftrightarrow p_2))) \land (\neg p_3))\}
$$

### Proposición 2

La proposición de este caso es la siguiente:

$$
((p_7 \to (\neg\bot)) \leftrightarrow ((p_4 \land (\neg p_2)) \to p_1))
$$

#### Secuencia 1

$$
\{p_1,p_2,p_4,p_7,\bot,(\neg p_2), (\neg\bot), (p_4 \land (\neg p_2)),(p_7 \to (\neg\bot)),\\ ((p_4 \land (\neg p_2)) \to p_1),((p_7 \to (\neg\bot)) \leftrightarrow ((p_4 \land (\neg p_2)) \to p_1))\}
$$

#### Secuencia 2

$$
\{p_1,p_2,p_4,p_7,\bot,(\neg p_1),(\neg p_2), (\neg\bot), (p_4 \land (\neg p_2)),(p_7 \to (\neg\bot)),\\ ((p_4 \land (\neg p_2)) \to p_1),((p_7 \to (\neg\bot)) \leftrightarrow ((p_4 \land (\neg p_2)) \to p_1))\}
$$

## Resolución (parte b)

Queremos hallar dos secuencias de formación diferentes de largo mínimo para la proposición:

$$
((((p_1 \to p_2) \to p_1) \to p_2) \to p_1)
$$

### Secuencia 1

$$
\{p_1,p_2,(p_1\to p_2),((p_1\to p_2)\to p_1),\\(((p_1\to p_2)\to p_1)\to p_2),((((p_1\to p_2)\to p_1)\to p_2)\to p_1)\}
$$

### Secuencia 2

$$
\{p_2,p_1,(p_1\to p_2),((p_1\to p_2)\to p_1),\\(((p_1\to p_2)\to p_1)\to p_2),((((p_1\to p_2)\to p_1)\to p_2)\to p_1)\}
$$

Solo existen estas dos secuencias, porque como todas dependen de la anterior, solo podemos permutar los elementos de $AT$ entre si.