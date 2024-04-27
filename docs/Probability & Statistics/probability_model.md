---
layout: default
title: Probability Model
nav_order: 3
parent: Probability & Statistics
---

## Temas

- [Asignacion de Probabilidades](#asignación-de-probabilidades-medida-de-confianza-en-los-eventos)
- [Axiomas de la Probabilidad](#axiomas-de-la-probabilidad)
- [Derivaciones de axiomas de probabilidad](#derivaciones-de-axiomas-de-probabilidad)
- [Modelos de probabilidad continua](#modelos-de-probabilidad-continua)
- [La probabilidad condicional](#la-probabilidad-condicional)
- [Probabilidad condicional en la Ley de Probabilidad Total](#probabilidad-condicional-en-la-ley-de-probabilidad-total)
- [Independencia de los modelos de probabilidad](#independencia-de-los-modelos-de-probabilidad)
- [Modelos de probabilidad de Independencia condicional](#modelos-de-probabilidad-de-independencia-condicional)

## Asignación de Probabilidades: Ley de Laplace

### Modelo de Probabilidad

{: .note}
El modelo de probabilidad es un **marco conceptual y matemático esencial en estadística y teoría de probabilidad que permite analizar y predecir el comportamiento de fenómenos aleatorios.** Este modelo se basa en dos pilares fundamentales: **la definición del espacio muestral** que se aborda en la seccion anterior y **la asignación de probabilidades** a los eventos dentro de este espacio.

El objetivo principal de un modelo de probabilidad es establecer una regla (la ley de probabilidad) **que asigne valores no negativos a los subconjuntos del espacio muestral, reflejando nuestra confianza o creencia en la ocurrencia de esos eventos**. Estos valores se conocen como probabilidades y representan nuestra estimación de qué tan probable es que un resultado específico, o un conjunto de resultados, ocurra. desarrolla esto

### Asignacion de Probabilidades

{: .highlight}
La asignación de probabilidades es el **proceso mediante el cual se atribuyen valores numéricos a los eventos en el espacio muestral, reflejando la confianza o la creencia en la ocurrencia de esos eventos**. La probabilidad de un evento $$A$$, denotada como $$P(A)$$, es un **número no negativo, entre 0 y 1**,  que indica qué tan probable es que $$A$$ ocurra cuando se realiza el experimento. 

### Ley de Laplace

{: .note}
También conocida como la regla de la probabilidad clásica o equiprobable, establece que si un experimento aleatorio tiene resultados igualmente probables, entonces la probabilidad de un evento $$𝐸$$ es el número de resultados en $$\|E\|$$ dividido por el número total de resultados posibles en el espacio muestral $$\|S\|$$.

$$P(E) = \frac{|E|}{|S|}$$

### Ejemplo Práctico

Imagina que un bol contiene 3 bolas rojas y 2 bolas azules. Si se va a extraer una bola al azar, la probabilidad de sacar una bola roja, usando la Ley de Laplace, se calcula como el número de bolas rojas dividido por el número total de bolas:

$$P(\text{Roja}) = \frac{3}{5}$$

Si no supiéramos los colores de las bolas en el bol, pero sabemos que hay 5 bolas, y asumimos equiprobabilidad (ignorando cualquier información adicional), la probabilidad de sacar cualquier bola específica sería $$\frac{1}{5} $$.

## Axiomas de la Probabilidad

{: .highlight}
Son las reglas fundamentales **para definir las probabilidades de los eventos dentro del marco de la teoría de probabilidad**. Estos axiomas son esenciales para construir modelos de probabilidad que permitan analizar y predecir el comportamiento de fenómenos aleatorios de manera matemáticamente rigurosa. Hay tres axiomas principales de probabilidad, y a partir de ellos se pueden derivar diversas reglas y propiedades.

### Axioma 1: No Negatividad

El primer axioma establece que **la probabilidad de cualquier evento es siempre un número no negativo**. Esto refleja la idea de que la probabilidad mide la confianza o expectativa de que un evento ocurra, lo cual no puede ser una cantidad negativa. Este axioma también permite que la probabilidad de un evento sea cero, lo que indica que el evento es imposible dentro del contexto del experimento.

### Axioma 2: Aditividad, Regla de la Suma

La **regla de la suma**, también conocida como la **regla de adición**, es un principio fundamental en la teoría de probabilidades que se utiliza para calcular la probabilidad de que ocurra al menos uno de dos eventos. 

#### Eventos Mutuamente Excluyentes

Para dos eventos $$A$$ y $$B$$ que no pueden ocurrir al mismo tiempo (es decir, son mutuamente excluyentes), la regla de la suma establece que la probabilidad de que ocurra $$A$$ o $$B$$ es simplemente la suma de sus probabilidades individuales:

$$P(A \cup B) = P(A) + P(B)$$

Por ejemplo, si tienes un mazo de cartas y quieres saber la probabilidad de sacar un rey o una reina, sumarías la probabilidad de sacar un rey con la probabilidad de sacar una reina, dado que no puedes sacar una carta que sea ambos a la vez.

#### Eventos No Mutuamente Excluyentes

Cuando los eventos pueden ocurrir simultáneamente (es decir, no son mutuamente excluyentes), se debe ajustar la regla de la suma para evitar contar dos veces la intersección de los eventos. La regla modificada es:

$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

Esto significa que se suma la probabilidad de $$A$$ y $$B$$, pero se resta la probabilidad de que $$A$$ y $$B$$ ocurran al mismo tiempo. Este ajuste es necesario para obtener una medida precisa de la probabilidad de que ocurra cualquiera de los eventos.

### Ejemplos Prácticos de eventos no excluyentes

1. **Cartas**:
   - Si tienes un mazo de 52 cartas y quieres saber la probabilidad de sacar un as o un corazón, primero sumarías la probabilidad de sacar un as $$4/52$$ con la probabilidad de sacar un corazón $$13/52$$. Luego, restarías la probabilidad de sacar un as de corazones, la intersección de los eventos $$1/52$$:
     - Sacar un As, 4 cartas: $$P(A) = \frac{4}{52}$$
     - Sacar un corazon (5, 6): $$P(B) = \frac{13}{52}$$
     - Sacar el As de corazones, 1 carta: $$P(A \cap B) = \frac{1}{52}$$
   
     $$
     P(\text{As} \cup \text{Corazón}) = \frac{4}{52} + \frac{13}{52} - \frac{1}{52} = \frac{16}{52} = \frac{4}{13}
     $$

     Los datos puedes darse de tres maneras: $$\frac{4}{13}$$, 0,3076 o como porcentaje multiplicando el resultado anterior por 100: 30,76%. 

2. **Dados**:
   - Si lanzas un dado y quieres saber la probabilidad de obtener un número impar o un número mayor que 4, primero determinarías la probabilidad de cada uno de estos eventos y luego su intersección:
     - Número impar (1, 3, 5): $$P(A) = \frac{3}{6}$$
     - Número mayor que 4 (5, 6): $$P(B) = \frac{2}{6}$$
     - Número impar y mayor que 4 (5): $$P(A \cap B) = \frac{1}{6}$$
   
     Aplicando la regla de la suma:
   
    $$P(A \cup B) = \frac{3}{6} + \frac{2}{6} - \frac{1}{6} = \frac{4}{6} = \frac{2}{3}$$

3. **Sala de espera**
   - En la sala de espera de un consultorio medico, el 60% de los pacientes toma cafe, el 50% lee revistas y unicamente el 20% delas personas toma cafe mientras lee revistas. Si se selecciona un paciente al azar ¿cual es la probabilidad de que tome cafe o lea revistas?
   - C = pacientes que toman cafe
   - R = Pacientes que leen revistas
   - $$P(C \cup R) = 60\% + 50\% - 20\% = 90\%$$

  ![Ejercicio de Suma](https://fer78docs.github.io/assets/images/ejercicio3suma.jpg)

4. **Solucion utilizando una Tabla**
   - En una ciudad el 60% de las personas tienen ojos negros, el 80% tienen cabello negro y el 50% tienen cabello negro y ojos negros. Si se selecciona una persona al azar, calcule la probabilidad que:
   1. No tenga los ojos negros.
   2. Tenga los ojos o cabello negro
   - O = Personas con ojos negros
   - C = Personas con cabellos negros
  
  ![Ejercicio de Suma](https://fer78docs.github.io/assets/images/Ejercicio_2_suma.jpg)

  Solucion a traves de una tabla:

  |               | O Negros | O No Negros | Total |
  |---------------|----------|-------------|-------|
  | C Negros      | 50%      | 30%         | 80%   |
  | C No Negros   | 10%      | 10%         | 20%   |
  | Total         | 60%      | 40%         | 100%  |

  Probabilidad de que no tenga ojos negros: 40%  
  Personas con ojos o cabellos negros: 

  $$P(O\cup C) = P(O) + P(C) - P(O\cup C) = 60\% + 80\% - 50\% = 90\%$$


### Regla de multiplicación

Hemos analizado la regla de la suma, que describe la probabilidad de que ocurra un evento U otro evento (o ambos). ¿Qué pasa si queremos calcular la probabilidad de que dos eventos sucedan simultáneamente? Para dos eventos, $$A$$ y $$B$$ , esto es $$P(A y B)$$ o la probabilidad de la intersección de $$A∩B$$.

La fórmula general para la probabilidad de que dos eventos dependientes ocurran simultáneamente es:

$$P(A∩B) = P(A) * P(B|A)$$

En la formula se calcula la probabilidad de que ocurran un eventos dado que ya ha ocurrido otro que modifica las probabilidades. 

Sin embargo, para eventos independientes, podemos simplificar ligeramente esta fórmula como: 

$$P(A∩B) = P(A) * P(B)$$

### Ejercicios Eventos dependientes

1. **Canicas**: 
- En una urna hay 5 canicas azules, 2 rojas y una verde. Si se sacan canicas consecutivas al azar sin remplazo, calcule la probabilidad que:

1. La primera sea azul y la segunda sea verde.
2. Las dos sean rojas

Calcular la probabilidad de que la primera canica sea azul $$A$$ y la segunda sea verde $$V$$

$$P(A∩V) = P(A) * P(V|A) = \frac{5}{8} * \frac{1}{7} = \frac{5}{56} = 0.089 = 8,9%$$

Calcular la probabilidad de que las dos sean rojas $$R$$:

$$P(R∩R) = P(R) * P(R|R) = \frac{2}{8} * \frac{1}{7} = \frac{2}{56} = 0.035 = 3,5%$$


2. **Una Clase** 
 - En una clase hay 10 niños y 8 niñas, si se seleccionan 3 estudiantes al azar:

1. ¿Cual es la probabilidad de que todos sean niños?
2. ¿Cual es la probabilidad de que todos sean niñas?

Probabilidad de que todos sean niños:

$$P(Nº∩Nº∩Nº) = P(Nº)  *  P(Nº|Nº)  *  P(Nº|Nº∩Nº)$$

$$P(Nº∩Nº∩Nº) = \frac{10}{18} * \frac{9}{17} * \frac{8}{16}$$

$$P(Nº∩Nº∩Nº) = \frac{5}{34} = 0.147 = 14,7%$$

Probabilidad de que todos sean niñas:

$$P(Nª∩Nª∩Nª) = P(Nª)  *  P(Nª|Nª)  *  P(Nª|Nª∩Nª)$$

$$P(Nª∩Nª∩Nª) = \frac{8}{18} * \frac{7}{17} * \frac{6}{16}$$

$$P(Nª∩Nª∩Nª) = \frac{336}{4896} = 0.068 = 6,8%$$

Una forma de visualizar todos los resultados posibles de un par de eventos es un diagrama de árbol .

### El diagrama de arbol

Los diagramas de árbol tienen las siguientes propiedades:

- Cada rama representa un conjunto específico de eventos.
- Las probabilidades de que las ramas terminales (todos los conjuntos posibles de resultados) sumen uno.
- Multiplicamos entre ramas (¡usando la regla de la multiplicación!) para calcular la probabilidad de que ocurra cada rama (conjunto de resultados).

¡En el navegador de la derecha podrás jugar con uno en este enlace: 

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/tree-diagram/tree.html)

### Eventos independientes

Para dos eventos independientes, la regla de la multiplicación se vuelve menos complicada. La probabilidad de que ocurran dos eventos independientes es:

$$P(A y B) = P(A) * P(B)$$

Esto se debe a que lo siguiente es cierto para eventos independientes:

$$P(B|A) = P(B)$$

Veamos el ejemplo más sencillo: lanzar dos veces una moneda justa. El evento $$A$$ es que obtenemos cruz en el primer lanzamiento, y el evento $$B$$ es que obtenemos cruz en el segundo lanzamiento. $$P(A) = P(B) = 0.5$$ , entonces según nuestra fórmula, la probabilidad de obtener cruz en ambos lanzamientos sería:

$$P(B y A ) = 0.5 * 0.5 = 0.25$$

#### Ejemplo de evento independiente 

El subprograma del enlace hay un diagrama de árbol y diez canicas azules y naranjas debajo del diagrama de árbol (es posible que deba desplazarse hacia abajo para ver las canicas). Si haces clic en una de las canicas, el diagrama de árbol se completará según lo que hayas seleccionado. 

Después de seleccionar dos canicas, aparecerá una ecuación para la regla del producto encima de las canicas. 

El número de canicas naranjas y azules se aleatoriza cada vez que golpeas Reset, por lo que verás muchos valores diferentes para prob1 , prob2 y final_prob .

Pruebe todos los resultados posibles y observe el diagrama de árbol en consecuencia:

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/tree-diagram/tree.html)

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

#### Probabilidad de Suma Par 

¿Cuál es la probabilidad de que la suma de los resultados de los dos dados sea un número par? Para responder, identificamos los pares cuya suma es par y calculamos la probabilidad combinada de estos pares.

|        | 1     | 2      | 3     | 4      |
|--------|-------|--------|-------|--------|
| **1**  | **2** | 3      | **4** | 5      |
| **2**  | 3     | **4**  | 5     | **6**  |
| **3**  | **4** | 5      | **6** | 7      |
| **4**  | 5     | **6**  | 7     | **8**  |

La cantidad de celdas con valores pares es 8 asi que seria 8 * 1/16 = 1/2, asi que la probabilidad de que la suma de los resultados sea un numero par es de un 50%.

#### Probabilidad de que al Menos un Dado Muestre un Cuatro:

¿Cuál es la probabilidad de que al menos uno de los dados muestre un cuatro? Nuevamente, seleccionamos los pares que cumplen con esta condición y sumamos sus probabilidades.
Segun nuestra tabla de espacio muestral hay 7 eventos que pueden tener 4 como resultado. Seria 7 * 1/16 = 7/16.

### Ejemplo Práctico: Predicciones de Enfermedades por un Médico

Imaginemos que tenemos un médico con 20 años de experiencia que, basándose en datos históricos, ha desarrollado un modelo para predecir la probabilidad de que el próximo paciente que llegue a su clínica tenga malaria o tifoidea, o ambas enfermedades. Según este modelo:

- La probabilidad de que el próximo paciente tenga malaria es del 0.6.
- La probabilidad de que el próximo paciente tenga tifoidea es del 0.7.
- La probabilidad de que el próximo paciente tenga tanto malaria como tifoidea es del 0.4.

Con esta información, se nos plantea la pregunta:   
**¿Cuál es la probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea?**

Para calcular la probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea, podemos utilizar la teoría de probabilidad de conjuntos, específicamente la ley de la probabilidad del complemento y la fórmula para la unión de dos eventos.

### Leyes y Fórmulas Utilizadas

1. **Probabilidad del Complemento**:  
   $$P(\text{no } A) = 1 - P(A)$$
   Esta fórmula se utiliza para encontrar la probabilidad de que un evento no ocurra, que es uno menos la probabilidad de que el evento ocurra.

2. **Fórmula de la Unión de Dos Eventos**:
   $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
   Aquí, $$P(A \cup B)$$ representa la probabilidad de que ocurra al menos uno de los eventos $$A$$ o $$B$$, $$P(A)$$ y $$P(B)$$ son las probabilidades de los eventos individuales, y $$P(A \cap B)$$ es la probabilidad de que ambos eventos ocurran simultáneamente.

Dado que:
- La probabilidad de tener Malaria: $$P(M) = 0.6 $$
- La probabilidad de tener Tifoidea:  $$P(T) = 0.7 $$
- La probabilidad de tener ambos: $$P(M \cap T) = 0.4$$

Queremos calcular $$P(\text{ni malaria ni tifoidea}) $$, que es el complemento de la probabilidad de que el paciente tenga malaria o tifoidea. Primero, calcularemos $$P(\text{malaria} \cup \text{tifoidea})$$ usando la fórmula de la unión de dos eventos:

$$P(M \cup T) = P(M) + P(T) - P(M \cap T) = 0.6 + 0.7 - 0.4 = 0.9$$

Luego, aplicaremos la probabilidad del complemento para obtener la probabilidad de que el paciente no tenga ninguna de las dos enfermedades:

$$P(\text{ni malaria ni tifoidea}) = 1 - P(M \cup T) = 1 − 0.9 = 0.1$$

Así que, basado en estos cálculos, la probabilidad de que el próximo paciente no tenga ni malaria ni tifoidea es del 10%. Si puedes acceder a un entorno de Python, simplemente puedes utilizar estos cálculos directamente para confirmar el resultado.



## La probabilidad condicional

{: .note}
La probabilidad condicional nos indica la probabilidad de que ocurra un evento $$A$$, dado que ya sabemos que otro evento $$B$$ ha ocurrido. Esta se denota como $$P(A\|B)$$ y se calcula usando la fórmula:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

donde $$P(A \cap B)$$ es la probabilidad de que ocurran $$A$$ y $$B$$ juntos, y $$P(B)$$ es la probabilidad de que ocurra $$B$$.

### Ejemplos Prácticos 

1. **Ejemplo 1**
En una ciudad el 40% de la poblacion tiene pelo castaño (PC), el 25% tiene ojos castaños(OC) y el 15% tiene cabellos y ojos castaños. Si se selecciona una persona al azar y esta tiene ojos castaños ¿Cual es la probabilidad de que tenga tambien cabello castaño?
Formula de la probabilidad condicional:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

Solucion: 

- Probabilidad de que tenga el cabello castaño: $$P(C) = 40\%$$
- Probabilidad de que tenga los ojos castaños: $$P(O) = 25\% $$
- Probabilidad de que tenga el cabello castaño y los ojos castaños: $$P(C \cap O) = \15%$$

Formulacion: 


$$
\begin{aligned}
P(C|O) = \frac{P(C \cap O)}{P(O)} \\
P(C|O) = \frac{15}{25} \\
P(C|O) = \frac{0.15}{0.25} \\
P(C|O) = 0.6 = 60\%
\end{aligned}
$$

![Ejercicio de Suma](https://fer78docs.github.io/assets/images/procondicional_ejercicio1.jpg)





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


## Modelos de probabilidad continua

En los modelos de probabilidad discretos donde el espacio muestral es contable. Esto significa que, ya sea finito o infinito, los resultados posibles de nuestro experimento se pueden enumerar o indexar de manera secuencial. Estos modelos **permiten asignar probabilidades positivas a eventos específicos**, incluso a aquellos que contienen un único resultado.

Sin embargo, **nos encontramos con una complejidad adicional cuando el espacio muestral se vuelve incontable.** Imaginemos, por ejemplo, una rueda de dardos. Si consideramos el punto donde impacta el dardo dentro de un círculo unitario, cada punto tiene la misma probabilidad de ser elegido. Pero, ¿cómo asignamos probabilidades a eventos tan infinitesimales como un punto específico dentro del círculo?

Cuando el espacio muestral es incontable, asignar probabilidades positivas a cada evento individual resulta imposible. Incluso asignando la más mínima probabilidad positiva a cada posible punto de impacto del dardo en el círculo, nos encontraríamos rápidamente con que la suma total de estas probabilidades excedería el límite de 1, violando así los axiomas fundamentales de la probabilidad.

### La Solución: Trabajar con Intervalos

**En los modelos de probabilidad continua, en lugar de tratar con eventos individuales, trabajamos con intervalos de eventos.** No asignamos probabilidades a puntos específicos, sino a la probabilidad de que un evento ocurra dentro de un rango determinado. Por ejemplo, en lugar de preguntar por la probabilidad de que el dardo impacte exactamente a una distancia de 0.73 del centro, preguntaríamos por la probabilidad de que impacte dentro de un intervalo, como entre 0.5 y 0.7.

Consideremos un círculo unitario. Si el juego consiste en lanzar un dardo y calcular la distancia desde el origen hasta el punto de impacto, nos enfrentamos a un espacio muestral incontable. Cada punto dentro del círculo tiene una probabilidad de ser alcanzado, pero es imposible asignar una probabilidad específica a cada punto. En cambio, debemos enfocarnos en los intervalos de distancia.

### Espacio Muestral y Probabilidades en Modelos Discretos y Continuos

Antes de adentrarnos en ejemplos, es importante recordar la diferencia entre modelos de probabilidad discretos y continuos:

{: .highlight}
**Modelos Discretos:** El espacio muestral es contable, lo que significa que podemos enumerar todos los posibles resultados del experimento.

{: .highlight}
**Modelos Continuos:** El espacio muestral es incontable, como los puntos en un segmento de línea. Aquí, no podemos asignar probabilidades a eventos individuales de manera directa.
