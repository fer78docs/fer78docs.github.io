---
layout: default
title: Probability Model
nav_order: 3
parent: Probability & Statistics
---

## Modelo de Probabilidad

- [Espacio Muestral](#espacio-muestral-el-fundamento-del-modelo-de-probabilidad)
- [Asignacion de Probabilidades](#asignación-de-probabilidades-medida-de-confianza-en-los-eventos)

{: .note}
El **modelo de probabilidad** es un marco conceptual y matemático esencial en estadística y teoría de probabilidad que permite analizar y predecir el comportamiento de fenómenos aleatorios. Este modelo se basa en dos pilares fundamentales: **la definición del espacio muestral** y **la asignación de probabilidades** a los eventos dentro de este espacio. 

El objetivo principal de un modelo de probabilidad es establecer una regla (la ley de probabilidad) que asigne valores no negativos a los subconjuntos del espacio muestral, reflejando nuestra confianza o creencia en la ocurrencia de esos eventos. Estos valores se conocen como probabilidades y representan nuestra estimación de qué tan probable es que un resultado específico, o un conjunto de resultados, ocurra. desarrolla esto

### Espacio Muestral: El Fundamento del Modelo de Probabilidad

{: .note}
El **espacio muestral** de un experimento aleatorio es el **conjunto de todos los posibles resultados que el experimento puede producir**. 

Es la base sobre la cual se construye el modelo de probabilidad, ya que define el universo de resultados posibles. Este espacio puede ser **finito**, como en el lanzamiento de un dado (donde los resultados posibles son los números del 1 al 6), o **infinito**, como en el tiempo de espera hasta un determinado evento, aunque aún contable si cada resultado puede ser enumerado.

### Eventos: Subconjuntos del Espacio Muestral

Un **evento** es cualquier subconjunto del espacio muestral que representa una colección de resultados posibles en los que estamos interesados. Por ejemplo, en el lanzamiento de dos dados, un evento podría ser "obtener una suma par". Los eventos pueden variar desde el conjunto vacío (un evento imposible) hasta el espacio muestral completo (un evento seguro), incluyendo eventos más específicos que reflejan preguntas particulares sobre el experimento.

### Asignación de Probabilidades: Medida de Confianza en los Eventos

{: .note}
La **asignación de probabilidades** es el proceso mediante el cual se atribuyen valores numéricos a los eventos en el espacio muestral, reflejando la confianza o la creencia en la ocurrencia de esos eventos. La probabilidad de un evento `A`, denotada como `P(A)`, es un **número no negativo** que indica qué tan probable es que `A` ocurra cuando se realiza el experimento. 

Las probabilidades deben cumplir con ciertas propiedades o axiomas, como que:

- La suma de las probabilidades de todos los eventos elementales en el espacio muestral es igual a 1
- La probabilidad de cualquier evento es la suma de las probabilidades de los resultados individuales que lo componen.

### Ejemplos y Aplicaciones

- **Lanzamiento de Dados:** Consideramos un experimento donde se lanzan dos dados de cuatro caras. El espacio muestral incluye todas las combinaciones posibles de resultados, y un evento de interés podría ser "obtener una suma par". La probabilidad de este evento se calcula considerando todos los pares de resultados que cumplen con la condición y asignando probabilidades basadas en la regla de conteo uniforme o datos históricos.

- **Control de Temperatura:** En un centro comercial que utiliza un sensor de temperatura para evaluar la fiebre de los visitantes, el espacio muestral incluye todas las temperaturas posibles registradas. Un evento relevante podría ser "registrar una temperatura menor o igual a 98 grados Fahrenheit", y su probabilidad refleja la proporción de visitantes que se espera que cumplan con esta condición.

## Probability Axioms

{: .highlight}
Los **axiomas de la probabilidad**, son las *reglas fundamentales para definir las probabilidades de los eventos* dentro del marco de la teoría de probabilidad. Estos axiomas son esenciales para construir modelos de probabilidad que permitan analizar y predecir el comportamiento de fenómenos aleatorios de manera matemáticamente rigurosa. Hay tres axiomas principales de probabilidad, y a partir de ellos se pueden derivar diversas reglas y propiedades.

### Axioma 1: No Negatividad

El primer axioma establece que **la probabilidad de cualquier evento es siempre un número no negativo**. Esto refleja la idea de que la probabilidad mide la confianza o expectativa de que un evento ocurra, lo cual no puede ser una cantidad negativa. Este axioma también permite que la probabilidad de un evento sea cero, lo que indica que el evento es imposible dentro del contexto del experimento.

### Axioma 2: Aditividad

El segundo axioma, conocido como la aditividad o **la regla de suma para eventos disjuntos, especifica que si dos eventos `A`y `B` son mutuamente excluyentes (es decir, no pueden ocurrir al mismo tiempo), entonces la probabilidad de que ocurra `A` o `B` es igual a la suma de sus probabilidades individuales.** Esto se extiende a una cantidad finita o infinita contable de eventos mutuamente excluyentes, asegurando que la probabilidad de su unión sea la suma de las probabilidades de cada evento.

### Axioma 3: Probabilidad del Espacio Muestral

El tercer axioma dicta que **la probabilidad del espacio muestral completo es 1.** Esto se alinea con la idea de que el espacio muestral representa todos los posibles resultados de un experimento, y dado que uno de esos resultados debe ocurrir, la certeza total se representa como una probabilidad de 1.

### Consecuencias de los Axiomas

A partir de estos axiomas, se pueden derivar varias propiedades importantes de la probabilidad:

- **Intervalo de Probabilidad:** Todo evento tiene una probabilidad que se encuentra en el intervalo `[0, 1]`, inclusivo. Esto se sigue del tercer axioma y del hecho de que ningún evento puede ser más probable que el espacio muestral completo.
- **Probabilidad del Complemento:** La probabilidad de que un evento no ocurra (su complemento) es 1 menos la probabilidad de que el evento ocurra.
- **Probabilidad del Conjunto Vacío:** La probabilidad del conjunto vacío, que representa un evento imposible, es 0. Esto es coherente con la interpretación del conjunto vacío como un evento sin resultados posibles.

### Aplicaciones y Ejemplos

Los axiomas de probabilidad son aplicados en una gran variedad de contextos para calcular probabilidades de eventos complejos y para desarrollar modelos de probabilidad más sofisticados. Por ejemplo, en un experimento de lanzar un dado justo, la probabilidad asignada a cada cara sería `1/6`, reflejando la equiprobabilidad de cada resultado. A partir de ahí, se pueden calcular las probabilidades de eventos compuestos, como obtener un número par, mediante la suma de las probabilidades de los eventos simples relevantes.

## Derivaciones de axiomas de probabilidad

Las **derivaciones de los axiomas de probabilidad** se refieren a las propiedades y reglas que se pueden inferir directamente a partir de los axiomas fundamentales de la probabilidad. Estos axiomas, como ya se ha mencionado, son la no negatividad, la aditividad (o regla de suma para eventos disjuntos) y que la probabilidad del espacio muestral completo es 1. A partir de estos axiomas, se pueden deducir varias reglas importantes que son esenciales para el trabajo práctico en probabilidad y estadística.

### 1. **Probabilidad del Complemento de un Evento**

Una de las derivaciones más directas es la probabilidad del complemento de un evento. Si \(A\) es un evento, entonces el complemento de \(A\), denotado \(A^c\), representa la ocurrencia de no-\(A\). Utilizando los axiomas, se puede demostrar que:

\[P(A^c) = 1 - P(A)\]

Esto se deduce del hecho de que \(A\) y \(A^c\) son mutuamente excluyentes y su unión es el espacio muestral completo, cuya probabilidad es 1.

### 2. **Probabilidad de la Unión de Eventos**

Para dos eventos \(A\) y \(B\), la probabilidad de su unión puede ser expresada en términos de las probabilidades de \(A\), \(B\), y su intersección \(A \cap B\). Esta regla se aplica incluso si \(A\) y \(B\) no son disjuntos y se deriva como sigue:

\[P(A \cup B) = P(A) + P(B) - P(A \cap B)\]

Esto ajusta la aditividad para el caso de eventos que no son mutuamente excluyentes, evitando la sobrecontabilización de la intersección de \(A\) y \(B\).

### 3. **Subaditividad**

La subaditividad se refiere a la propiedad de que la probabilidad de la unión de cualquier colección de eventos es menor o igual a la suma de sus probabilidades individuales. Para una secuencia de eventos \(A_1, A_2, \ldots, A_n\):

\[P\left(\bigcup_{i=1}^{n} A_i\right) \leq \sum_{i=1}^{n} P(A_i)\]

Esta propiedad es particularmente útil para tratar con uniones de eventos que no son necesariamente disjuntos.

### 4. **Probabilidad de Eventos Vacíos y Ciertos**

Directamente de los axiomas, se establece que la probabilidad del conjunto vacío (\(\emptyset\)), que es un evento imposible, es 0:

\[P(\emptyset) = 0\]

Asimismo, la probabilidad del espacio muestral completo (\(\Omega\)), que representa un evento seguro, es 1:

\[P(\Omega) = 1\]

### 5. **Monotonicidad**

Si un evento \(A\) es un subconjunto de otro evento \(B\), entonces la probabilidad de \(A\) es menor o igual a la probabilidad de \(B\). Esto refleja la idea de que la ocurrencia de \(B\) incluye la ocurrencia de \(A\) junto con posiblemente otros resultados:

\[A \subseteq B \Rightarrow P(A) \leq P(B)\]

### 6. **Límites de Probabilidad**

Cualquier probabilidad \(P(A)\) para un evento \(A\) siempre estará en el rango de 0 a 1, inclusive. Esto se deriva del hecho de que todas las probabilidades son no negativas y que la probabilidad del espacio muestral, el conjunto más grande posible, es 1.

Estas derivaciones son fundamentales para el trabajo en probabilidad, proporcionando herramientas esenciales para el cálculo de probabilidades en contextos más complejos y para el entendimiento profundo de la naturaleza de los fenómenos aleatorios.