---
layout: default
title: Probability Model
nav_order: 3
parent: Probability & Statistics
---

## Temas

- [Espacio Muestral](#espacio-muestral-el-fundamento-del-modelo-de-probabilidad)
- [Asignacion de Probabilidades](#asignación-de-probabilidades-medida-de-confianza-en-los-eventos)
- [Probability Axioms](#probability-axioms)
- [Derivaciones de axiomas de probabilidad](#derivaciones-de-axiomas-de-probabilidad)
- [Modelos de probabilidad continua](#modelos-de-probabilidad-continua)
- [La probabilidad condicional](#la-probabilidad-condicional)
- [Probabilidad condicional en la Ley de Probabilidad Total](#probabilidad-condicional-en-la-ley-de-probabilidad-total)
- [Independencia de los modelos de probabilidad](#independencia-de-los-modelos-de-probabilidad)
- [Modelos de probabilidad de Independencia condicional](#modelos-de-probabilidad-de-independencia-condicional)

## Modelo de Probabilidad

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
La **asignación de probabilidades** es el proceso mediante el cual se atribuyen valores numéricos a los eventos en el espacio muestral, reflejando la confianza o la creencia en la ocurrencia de esos eventos. La probabilidad de un evento $$A$$, denotada como $$P(A)$$, es un **número no negativo** que indica qué tan probable es que $$A$$ ocurra cuando se realiza el experimento. 

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

El segundo axioma, conocido como la aditividad o **la regla de suma para eventos disjuntos, especifica que si dos eventos $$A$$ y $$B$$ son mutuamente excluyentes (es decir, no pueden ocurrir al mismo tiempo), entonces la probabilidad de que ocurra $$A$$ o $$B$$ es igual a la suma de sus probabilidades individuales.** Esto se extiende a una cantidad finita o infinita contable de eventos mutuamente excluyentes, asegurando que la probabilidad de su unión sea la suma de las probabilidades de cada evento.

### Axioma 3: Probabilidad del Espacio Muestral

El tercer axioma dicta que **la probabilidad del espacio muestral completo es 1.** Esto se alinea con la idea de que el espacio muestral representa todos los posibles resultados de un experimento, y dado que uno de esos resultados debe ocurrir, la certeza total se representa como una probabilidad de 1.

### Consecuencias de los Axiomas

A partir de estos axiomas, se pueden derivar varias propiedades importantes de la probabilidad:

- **Intervalo de Probabilidad:** Todo evento tiene una probabilidad que se encuentra en el intervalo $$[0, 1]$$, inclusivo. Esto se sigue del tercer axioma y del hecho de que ningún evento puede ser más probable que el espacio muestral completo.
- **Probabilidad del Complemento:** La probabilidad de que un evento no ocurra (su complemento) es 1 menos la probabilidad de que el evento ocurra.
- **Probabilidad del Conjunto Vacío:** La probabilidad del conjunto vacío, que representa un evento imposible, es 0. Esto es coherente con la interpretación del conjunto vacío como un evento sin resultados posibles.

### Aplicaciones y Ejemplos

Los axiomas de probabilidad son aplicados en una gran variedad de contextos para calcular probabilidades de eventos complejos y para desarrollar modelos de probabilidad más sofisticados. Por ejemplo, en un experimento de lanzar un dado justo, la probabilidad asignada a cada cara sería $$1/6$$, reflejando la equiprobabilidad de cada resultado. A partir de ahí, se pueden calcular las probabilidades de eventos compuestos, como obtener un número par, mediante la suma de las probabilidades de los eventos simples relevantes.

## Derivaciones de axiomas de probabilidad

{: .highlight}
Las **derivaciones de los axiomas de probabilidad** se refieren a las propiedades y reglas que se pueden inferir directamente a partir de los axiomas fundamentales de la probabilidad. 

Estos axiomas, como ya se ha mencionado, son la no negatividad, la aditividad (o regla de suma para eventos disjuntos) y que la probabilidad del espacio muestral completo es 1. A partir de estos axiomas, se pueden deducir varias reglas importantes que son esenciales para el trabajo práctico en probabilidad y estadística.

### 1. **Probabilidad del Complemento de un Evento**

**Una de las derivaciones más directas es la probabilidad del complemento de un evento**. Si $$A$$ es un evento, entonces el complemento de $$A$$, denotado $$A^c$$, representa la ocurrencia de $$no-A$$. Utilizando los axiomas, se puede demostrar que:

$$P(A^c) = 1 - P(A)$$

Esto se deduce del hecho de que $$A$$ y $$A^c$$ son mutuamente excluyentes y su unión es el espacio muestral completo, cuya probabilidad es 1.

### 2. **Probabilidad de la Unión de Eventos**

**Para dos eventos $$A$$ y $$B$$, la probabilidad de su unión puede ser expresada en términos de las probabilidades de $$A$$, $$B$$, y su intersección $$A ∩ B$$**. Esta regla se aplica incluso si $$A$$ y $$B$$ no son disjuntos y se deriva como sigue:

$$P(A ∪ B) = P(A) + P(B) - P(A ∩ B)$$

Esto ajusta la aditividad para el caso de eventos qsue no son mutuamente excluyentes, evitando la sobrecontabilización de la intersección de $$A$$ y $$B$$.

### 3. **Subaditividad**

La subaditividad se refiere a la propiedad de que **la probabilidad de la unión de cualquier colección de eventos es menor o igual a la suma de sus probabilidades individuales.** Para una secuencia de eventos $$A1, A2,...., An$$:

Esta propiedad es particularmente útil para tratar con uniones de eventos que no son necesariamente disjuntos.

### 4. **Probabilidad de Eventos Vacíos y Ciertos**

Directamente de los axiomas, se establece que la **probabilidad del conjunto vacío** `{∅}`, que es un evento imposible, es 0:

$$P(∅) = 0$$

Asimismo, la probabilidad del espacio muestral completo $$(Ω)$$, que representa un evento seguro, es 1:

$$P(Ω) = 1$$

### 5. **Monotonicidad**

**Si un evento $$A$$ es un subconjunto de otro evento $$B$$, entonces la probabilidad de $$A$$ es menor o igual a la probabilidad de $$B$$**. Esto refleja la idea de que la ocurrencia de $$B$$ incluye la ocurrencia de $$A$$ junto con posiblemente otros resultados:

$$A ⊆ B -> P(A) ≤ P(B)$$

### 6. **Límites de Probabilidad**

**Cualquier probabilidad $$P(A)$$ para un evento $$A$$ siempre estará en el rango de 0 a 1, inclusive.** Esto se deriva del hecho de que todas las probabilidades son no negativas y que la probabilidad del espacio muestral, el conjunto más grande posible, es 1.

### Ejemplos de modelos de probabilidad discretos:

Este ejemplo nos permitirá entender cómo definir un espacio muestral y cómo asignar probabilidades a los eventos dentro de ese espacio. Los modelos de probabilidad discretos se ocupan de experimentos donde el número de posibles resultados es finito o contable. Un ejemplo clásico es el lanzamiento de dados, donde los resultados posibles pueden listarse de manera explícita.

Supongamos que tenemos dos dados de cuatro caras, donde cada resultado tiene una probabilidad de $$1/16$$, podemos construir una tabla que muestre todas las combinaciones posibles de los resultados de los dos dados. Cada dado puede mostrar uno de cuatro resultados posibles (1, 2, 3, o 4), lo que nos da un total de $$4 \times 4 = 16$$ combinaciones posibles para los dos dados. Aquí está la tabla que modela el espacio muestral con la probabilidad asignada a cada par de resultados. Cada uno de estos nuemros deben ser positivos y la suma de todos debe ser 1.

|        | 1       | 2       | 3       | 4       |
|--------|---------|---------|---------|---------|
| **1**  | 1/16    | 1/16    | 1/16    | 1/16    |
| **2**  | 1/16    | 1/16    | 1/16    | 1/16    |
| **3**  | 1/16    | 1/16    | 1/16    | 1/16    |
| **4**  | 1/16    | 1/16    | 1/16    | 1/16    |

Cada celda representa una posibilidad de resultado: 

|        | 1       | 2       | 3       | 4       |
|--------|---------|---------|---------|---------|
| **1**  | {1,1}   | {1,2}   | {1,3}   | {1,4}   |
| **2**  | {2,1}   | {2,2}   | {2,3}   | {2,4}   |
| **3**  | {3,1}   | {3,2}   | {3,3}   | {3,4}   |
| **4**  | {4,1}   | {4,2}   | {4,3}   | {4,4}   |

Una vez establecido el espacio muestral y las probabilidades, podemos investigar ciertas preguntas:

**Probabilidad de Suma Par:** ¿Cuál es la probabilidad de que la suma de los resultados de los dos dados sea un número par? Para responder, identificamos los pares cuya suma es par y calculamos la probabilidad combinada de estos pares.

|        | 1     | 2      | 3     | 4      |
|--------|-------|--------|-------|--------|
| **1**  | **2** | 3      | **4** | 5      |
| **2**  | 3     | **4**  | 5     | **6**  |
| **3**  | **4** | 5      | **6** | 7      |
| **4**  | 5     | **6**  | 7     | **8**  |

La cantidad de celdas con valores pares es 8 asi que seria 8 * 1/16 = 1/2, asi que la probabilidad de que la suma de los resultados sea un numero par es de un 50%.

**Probabilidad de que al Menos un Dado Muestre un Cuatro:** ¿Cuál es la probabilidad de que al menos uno de los dados muestre un cuatro? Nuevamente, seleccionamos los pares que cumplen con esta condición y sumamos sus probabilidades.
Segun nuestra tabla de espacio muestral hay 7 eventos que pueden tener 4 como resultado. Seria 7 * 1/16 = 7/16.

**Ejemplo Práctico: Predicciones de Enfermedades por un Médico**

Imaginemos que tenemos un médico con 20 años de experiencia que, basándose en datos históricos, ha desarrollado un modelo para predecir la probabilidad de que el próximo paciente que llegue a su clínica tenga malaria o tifoidea, o ambas enfermedades. Según este modelo:

- La probabilidad de que el próximo paciente tenga malaria es del 0.6.
- La probabilidad de que el próximo paciente tenga tifoidea es del 0.7.
- La probabilidad de que el próximo paciente tenga tanto malaria como tifoidea es del 0.4.

Con esta información, se nos plantea la pregunta: ¿Cuál es la probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea?

### Solución Utilizando Teoría de Conjuntos y Axiomas de Probabilidad

Para resolver este problema, aplicaremos las leyes de De Morgan, que nos permiten relacionar la unión y la intersección de eventos con sus complementos, y los axiomas de probabilidad, que definen cómo calcular la probabilidad de eventos compuestos.

#### Paso 1: Aplicación de la Ley de De Morgan

De acuerdo con la ley de De Morgan, el complemento de la unión de dos eventos es igual a la intersección de sus complementos:

$$(M \cup T)^c = M^c \cap T^c$$

Donde $$M$$ es el evento de tener malaria, $$T$$ es el evento de tener tifoidea, y los complementos representan no tener cada enfermedad.

#### Paso 2: Cálculo de la Probabilidad Deseada

La probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea se puede calcular como:

$$P((M \cup T)^c) = 1 - P(M \cup T)$$

Y aplicando la regla de adición para probabilidades:

$$P(M \cup T) = P(M) + P(T) - P(M \cap T)$$

Sustituyendo los valores dados:

$$P((M \cup T)^c) = 1 - (0.6 + 0.7 - 0.4) = 0.1$$

Por lo tanto, la probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea es del 0.1, o 10%.

Este ejemplo nos muestra cómo combinar los axiomas de probabilidad con la teoría de conjuntos para resolver problemas complejos de probabilidad. A través de un enfoque paso a paso, hemos podido determinar la probabilidad de un evento compuesto utilizando información sobre eventos individuales y su intersección.

## Modelos de probabilidad continua

En los modelos de probabilidad discretos donde el espacio muestral es contable. Esto significa que, ya sea finito o infinito, los resultados posibles de nuestro experimento se pueden enumerar o indexar de manera secuencial. Estos modelos **permiten asignar probabilidades positivas a eventos específicos**, incluso a aquellos que contienen un único resultado.

Sin embargo, **nos encontramos con una complejidad adicional cuando el espacio muestral se vuelve incontable.** Imaginemos, por ejemplo, una rueda de dardos. Si consideramos el punto donde impacta el dardo dentro de un círculo unitario, cada punto tiene la misma probabilidad de ser elegido. Pero, ¿cómo asignamos probabilidades a eventos tan infinitesimales como un punto específico dentro del círculo?

Cuando el espacio muestral es incontable, asignar probabilidades positivas a cada evento individual resulta imposible. Incluso asignando la más mínima probabilidad positiva a cada posible punto de impacto del dardo en el círculo, nos encontraríamos rápidamente con que la suma total de estas probabilidades excedería el límite de 1, violando así los axiomas fundamentales de la probabilidad.

### La Solución: Trabajar con Intervalos

**En los modelos de probabilidad continua, en lugar de tratar con eventos individuales, trabajamos con intervalos de eventos.** No asignamos probabilidades a puntos específicos, sino a la probabilidad de que un evento ocurra dentro de un rango determinado. Por ejemplo, en lugar de preguntar por la probabilidad de que el dardo impacte exactamente a una distancia de 0.73 del centro, preguntaríamos por la probabilidad de que impacte dentro de un intervalo, como entre 0.5 y 0.7.

Consideremos un círculo unitario. Si el juego consiste en lanzar un dardo y calcular la distancia desde el origen hasta el punto de impacto, nos enfrentamos a un espacio muestral incontable. Cada punto dentro del círculo tiene una probabilidad de ser alcanzado, pero es imposible asignar una probabilidad específica a cada punto. En cambio, debemos enfocarnos en los intervalos de distancia.

## La probabilidad condicional

{: .note}
La probabilidad condicional nos indica la probabilidad de que ocurra un evento $$A$$, dado que ya sabemos que otro evento $$B$$ ha ocurrido. Esta se denota como $$P(A\|B)$$ y se calcula usando la fórmula:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

donde $$P(A \cap B)$$ es la probabilidad de que ocurran $$A$$ y $$B$$ juntos, y $$P(B)$$ es la probabilidad de que ocurra $$B$$.

### Espacio Muestral y Probabilidades en Modelos Discretos y Continuos

Antes de adentrarnos en ejemplos, es importante recordar la diferencia entre modelos de probabilidad discretos y continuos:

{: .highlight}
**Modelos Discretos:** El espacio muestral es contable, lo que significa que podemos enumerar todos los posibles resultados del experimento.

{: .highlight}
**Modelos Continuos:** El espacio muestral es incontable, como los puntos en un segmento de línea. Aquí, no podemos asignar probabilidades a eventos individuales de manera directa.

### Ejemplo Práctico con un Dado Cargado

Imaginemos que tenemos un dado de seis caras que está cargado de tal manera que los números pares tienen el doble de probabilidades de salir que los números impares. Si definimos dos eventos:
- $$A$$: Sacar un número no mayor que 4: $$A = \{1, 2, 3, 4\}$$.
- $$B$$: Sacar un número par: $$B = \{2, 4, 6\}$$.

Dado que los números pares tienen el doble de probabilidades de salir que los números impares y que todos los números pares entre sí son igualmente probables, así como todos los números impares entre sí, podemos establecer lo siguiente:

- Las probabilidades de sacar un número par $$P(E2) = P(E4) = P(E6) = x$$ es el doble que la de sacar un número impar $$P(E1) = P(E3) = P(E5) = y$$, por lo que $$x = 2y$$.
- Teniendo en cuenta que el dado es de seis caras y todas las probabilidades deben sumar 1, tenemos $$3x + 3y = 1$$.

Sustituyendo $$x$$ por $$2y$$ en la ecuación $$3x + 3y = 1$$, obtenemos $$3(2y) + 3y = 1$$, lo que simplifica a $$6y + 3y = 1$$, dando $$9y = 1$$. De aquí, podemos resolver $$y = \frac{1}{9}$$.

Como $$x = 2y$$, entonces $$x = \frac{2}{9}$$.

Esto significa que las probabilidades para cada resultado son:
- Para números impares $$(1, 3, 5)$$: $$y = \frac{1}{9}$$.
- Para números pares $$(2, 4, 6)$$: $$x = \frac{2}{9}$$.

Ahora, para calcular la probabilidad de $$P(A)$$ (sacar un número no mayor que 4), sumamos las probabilidades de los resultados individuales en $$A$$:

$$
\begin{aligned}
P(A) = P(E1) + P(E2) + P(E3) + P(E4) \\
P(A) = \frac{1}{9} + \frac{2}{9} + \frac{1}{9} + \frac{2}{9} \\
P(A) = \frac{6}{9} \\
P(A) = \frac{2}{3}
\end{aligned}
$$

Por lo tanto, la probabilidad de sacar un número no mayor que 4 con este dado cargado es de $$\frac{2}{3}$$.

### Calculando la Probabilidad de $$A$$ dado $$B$$

Si sabemos con certeza que el resultado será un número par, entonces nuestro espacio muestral se reduce a $$B$$, y los resultados posibles son únicamente los números pares. Dado este nuevo espacio muestral, ¿cómo cambia la probabilidad de $$A$$? En este escenario, solo los resultados que son comunes a $$A$$ y $$B$$ (es decir, 2 y 4) serán relevantes para calcular $$P(A\|B)$$.

La fórmula para calcular la probabilidad condicional es:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

Donde:
- $$P(A\|B)$$ es la probabilidad de que ocurra $$A$$, dado que $$B$$ ha ocurrido.
- $$P(A \cap B)$$ es la probabilidad de que ocurran tanto $$A$$ como $$B$$ juntos.
- $$P(B)$$ es la probabilidad de que ocurra $$B$$.

**3. Ejemplo Práctico: Dado Cargado**

Imaginemos un dado de seis caras cargado, donde los números pares $$2, 4, 6$$ tienen el doble de probabilidades de aparecer que los impares $$1, 3, 5$$. Definimos dos eventos:

- $$A$$: Sacar un número no mayor que 4: $$A = \{1, 2, 3, 4\}$$.
- $$B$$: Sacar un número par: $$B = \{2, 4, 6\}$$.

**4. Cálculo de la Probabilidad Condicional en el Ejemplo**

Para calcular $$P(A\|B)$$, primero identificamos la intersección de $$A$$ y $$B$$, que es $$A ∩ B = \{2, 4\}$$, cuyas probabilidades suman $$4/9$$. Normalizamos esta suma con la probabilidad de $$B$$, \(2/3\), obteniendo:

$$P(A|B) = \frac{4/9}{2/3} = \frac{4/9}{6/9} = \frac{4}{6} = \frac{2}{3}$$

Este resultado nos indica que, sabiendo que el resultado será un número par, la probabilidad de que también sea un número no mayor a 4 es $$2/3$$, igual que la probabilidad de $$A$$ sin condicionar. Esto demuestra la independencia de $$A$$ respecto a $$B$$.

## Probabilidad condicional en el aprendizaje automático

En el mundo del aprendizaje automático, la probabilidad condicional juega un papel crucial, siendo la base sobre la cual se construyen la mayoría de los modelos.

#### Aplicaciones en el Aprendizaje Automático

El aprendizaje automático utiliza extensivamente la probabilidad condicional para modelar y predecir resultados basándose en datos históricos o condiciones previas. Veamos algunos ejemplos:

- **Reconocimiento Facial:** Imagina una cámara que desbloquea una puerta si reconoce a una persona autorizada. Aquí, la probabilidad condicional nos ayuda a predecir la probabilidad de que la persona frente a la cámara sea, de hecho, un empleado autorizado, basándose en la imagen capturada.

- **Reconocimiento de Actividades en Videos:** Al analizar un video, podemos querer identificar qué actividad se está realizando. Utilizamos variables aleatorias para representar tanto la actividad como los datos del video, y mediante la probabilidad condicional, modelamos la probabilidad de que se esté realizando una actividad específica.

- **Sistemas de Reconocimiento de Voz a Texto:** Aquí, la probabilidad condicional se usa para modelar la probabilidad de que ciertas palabras o frases sean dichas, basándose en los sonidos capturados.

## Probabilidad condicional en la Ley de Probabilidad Total

La Ley de Probabilidad Total, un concepto fundamental en la teoría de probabilidad que nos permite calcular la probabilidad de un evento a partir de la suma de las probabilidades de varios eventos mutuamente excluyentes que forman una partición del espacio muestral.


{: .note}
Para definir la **Ley de la Probabilidad Total**, Consideremos un espacio muestral $$\Omega$$ dividido en varios eventos mutuamente excluyentes $$A_1, A_2, ..., A_n$$ que forman una partición de $$\Omega$$. Esto significa que cada elemento de $$\Omega$$ pertenece exactamente a uno de los eventos $$A_i$$ y la unión de todos los $$A_i$$ recupera el espacio muestral completo. La Ley de Probabilidad Total nos dice que para cualquier evento $$B$$, la probabilidad de $$B$$ se puede expresar como:

$$
P(B) = P(B \cap A_1) + P(B \cap A_2) + ... + P(B \cap A_n)
$$

Para ilustrar, imagina que tenemos un espacio muestral representado por un conjunto $$\Omega$$, y este espacio se divide en 4 partes $$A_1, A_2, A_3$$ y $$A_4$$, formando una partición completa de $$\Omega$$. Supongamos que tenemos un evento $$B$$ que ocurre dentro de este espacio. La probabilidad de $$B$$ se puede calcular considerando sus intersecciones con cada uno de los conjuntos $$A_i$$.

![Ley de la probabilidad Total](https://fer78docs.github.io/assets/images/ley_probabilidad_total.jpg)

Esta ley es especialmente útil cuando trabajamos con variables aleatorias que representan datos reales. A menudo, nos encontramos con distribuciones conjuntas que involucran varias variables aleatorias y deseamos calcular distribuciones marginales. La Ley de Probabilidad Total nos proporciona una forma de hacerlo, sumando las probabilidades de eventos que están condicionados por las particiones del espacio muestral.

## Independencia de los modelos de probabilidad

La **independencia**, también conocida como independencia estadística, es una propiedad clave entre dos o más eventos en la teoría de la probabilidad. Dos eventos, $$A$$ y $$B$$, se consideran independientes si la ocurrencia de uno no afecta la probabilidad de ocurrencia del otro. Matemáticamente, esto se expresa como:

$$P(A \cap B) = P(A) \times P(B)$$

donde $$P(A \cap B)$$ es la probabilidad de que ambos eventos sucedan simultáneamente, y $$P(A)$$ y $$P(B)$$ son las probabilidades de que cada evento suceda independientemente.

### Ejemplos de Independencia

1. **Lanzamiento de una moneda y un dado**: Supongamos que lanzamos una moneda y un dado al mismo tiempo. La probabilidad de que la moneda muestre cara $$P(cara) = \frac{1}{2}$$, y la probabilidad de que el dado muestre un seis $$P(B_6) = \frac{1}{6}$$. Estos dos eventos son independientes porque el resultado de la moneda no influye en el resultado del dado, entonces:

$$P(A \cap B) = P(A) \times P(B) = \frac{1}{2} \times \frac{1}{6} = \frac{1}{12}$$

2. **Elegir cartas de diferentes barajas**: Si eliges una carta de una baraja y otra de una baraja diferente, estos dos eventos son independientes porque el resultado de una elección no afecta el resultado de la otra.

### Profundización en la Independencia Mutua

La pregunta central en la transcripción es si la independencia es mutua; es decir, si $$A$$ es independiente de $$B$$, ¿implica esto que $$B$$ también es independiente de $$A$$? La respuesta es sí, porque la independencia entre dos eventos **es siempre mutua** dado que la relación matemática no cambia al invertir los roles.

### Independencia en Conjuntos de Más de Dos Eventos

Cuando tratamos con más de dos eventos, establecer la independencia se vuelve más complejo. Para que tres eventos, por ejemplo, $$A$$, $$B$$, y $$C$$, sean mutuamente independientes, deben cumplir todas las siguientes condiciones:

- $$P(A \cap B \cap C) = P(A) \times P(B) \times P(C)$$
- $$P(A \cap B) = P(A) \times P(B)$$ 
- $$P(A \cap C) = P(A) \times P(C)$$
- $$P(B \cap C) = P(B) \times P(C)$$

Estas condiciones garantizan que la independencia se mantiene en todos los subconjuntos de eventos.

## Modelos de probabilidad de Independencia condicional

{: .note}
La **independencia condicional** es un concepto más refinado que indica que **dos eventos pueden ser independientes bajo la condición de un tercer evento**. Matemáticamente, dos eventos $$A$$ y $$B$$ son condicionalmente independientes dado un tercer evento $$C$$ si:

$$P(A \cap B | C) = P(A | C) \times P(B | C)$$

Este concepto es crucial en contextos donde la independencia absoluta no se mantiene, pero se establece una vez que se considera un evento condicionante.

### Ejemplo de Independencia Condicional

Considera el caso de testear un software bajo diferentes condiciones de red. Dos fallos distintos, $$A$$ y $$B$$, pueden no ser independientes en general (es decir, que uno ocurra puede afectar la probabilidad del otro), pero si condicionamos al tipo de red $$C$$ (por ejemplo, 4G vs. WiFi), estos fallos pueden volverse independientes dentro de cada tipo de red.

## Modelos de probabilidad Regla de Bayes

La **Regla de Bayes** o **Teorema de Bayes**, es un pilar fundamental en la probabilidad y estadística, especialmente crucial en el campo del aprendizaje automático. Este concepto se presenta como un puente hacia el entendimiento de cómo se pueden utilizar modelos estadísticos para interpretar y predecir a partir de datos. 

{: .note}
La Regla de Bayes proporciona una forma de calcular la probabilidad posterior de un evento, dado algún conocimiento previo. Matemáticamente, se expresa como:

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

donde:
- $$P(A\|B)$$ es la probabilidad de $$A$$ dado que $$B$$ ha ocurrido.
- $$P(B\|A)$$ es la probabilidad de $$B$$ dado que $$A$$ ha ocurrido.
- $$P(A)$$ es la probabilidad a priori de $$A$$.
- $$P(B)$$ es la probabilidad total de $$B$$.

### Prueba de la Regla de Bayes

La prueba se basa en el principio de que la probabilidad conjunta de dos eventos, $$A$$ y $$B$$, es la misma sin importar el orden en que se consideren, es decir, $$P(A \cap B) = P(B \cap A)$$. Aplicando la definición de probabilidad condicional a ambos lados, obtenemos la regla de Bayes.

### Ejemplo 

Imagina que tienes una enfermedad rara (Evento $$A$$) y una prueba que detecta dicha enfermedad (Evento $$B$$). La Regla de Bayes te permite calcular la probabilidad de tener la enfermedad dado que la prueba es positiva, utilizando el conocimiento previo sobre la prevalencia de la enfermedad y la precisión de la prueba.

### Aplicaciones en el Aprendizaje Automático

La Regla de Bayes es la base del clasificador Bayesiano, un algoritmo de aprendizaje automático que clasifica los datos basándose en la probabilidad de que pertenezcan a una clase dada la observación de sus características. Este clasificador se utiliza en:
- Filtros de spam en correos electrónicos.
- Clasificación de documentos y textos.
- Diagnósticos médicos automáticos.

### Modelo Generativo vs. Modelo Discriminativo

La distinción entre modelado generativo y discriminativo es fundamental en el aprendizaje automático:

- **Modelo Generativo**: Intenta modelar cómo se generan los datos, combinando las distribuciones de las características y las clases. Ejemplos incluyen el clasificador Bayesiano y la mezcla de modelos Gaussianos.
- **Modelo Discriminativo**: Se enfoca en la frontera entre las clases, intentando directamente predecir la clase a partir de las características observadas. Ejemplos incluyen la regresión logística y las máquinas de soporte vectorial (SVM).

## Modelos de probabilidad hacia variables aleatoria

Las **variables aleatorias** son entidades matemáticas que asignan resultados de procesos aleatorios a valores numéricos. **Son fundamentales para describir fenómenos en términos cuantitativos, permitiendo el uso de herramientas matemáticas y estadísticas para análisis y predicción.** Estas variables nos permiten la transición de conceptos teóricos de probabilidad a su aplicación práctica para modelar y analizar **datos reales**. 

Este paso es crucial, ya que en el aprendizaje automático, los datos —y, por ende, los eventos que representan— se expresan casi exclusivamente a través de números. Aquí, se propone una sólida comprensión de cómo los principios de probabilidad y estadística subyacen en la base de modelos complejos de aprendizaje automático, particularmente a través del ejemplo del reconocimiento facial.
