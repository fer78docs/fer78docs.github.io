---
layout: default
title: Random Experiment
nav_order: 2
parent: Probability & Statistics
---

## Experimento Aleatorio

- [Experimento Aleatorio](#experimento-aleatorio)
- [Resultado](#resultado)
- [Eventos](#evento)
- [Eventos Mutuamente Excluyentes](#eventos-mutuamente-excluyentes)

Un **experimento aleatorio** es un concepto fundamental en el estudio de la probabilidad y la estadística.

{: .note}
Se refiere a cualquier proceso o acción que se realiza bajo condiciones específicas y controladas, pero que, sin embargo, puede producir diferentes resultados en cada realización, sin que sea posible predecir con certeza cuál será el resultado específico en una instancia particular del experimento. La característica distintiva de un experimento aleatorio es esta incertidumbre inherente en el resultado.

### Características de un Experimento Aleatorio

1. **Múltiples Resultados Posibles:** Un experimento aleatorio tiene más de un resultado posible. Cada uno de estos resultados es un posible "estado del mundo" que podría ser observado después de realizar el experimento.

2. **Resultado Imposible de Predecir con Certeza:** Antes de realizar el experimento, no es posible predecir con seguridad cuál será el resultado específico.

3. **Repetibilidad:** El experimento se puede repetir bajo las mismas condiciones iniciales. Aunque los resultados individuales pueden variar, el conjunto de posibles resultados y sus probabilidades asociadas permanecen constantes a través de repeticiones.

### Ejemplos de Experimentos Aleatorios

- **Lanzar una Moneda:** Donde los resultados posibles son cara o cruz.
- **Lanzar un Dado:** Donde los resultados posibles son los números 1, 2, 3, 4, 5, o 6.
- **Extraer una Carta de una Baraja:** Donde cada carta de la baraja representa un posible resultado.
- **Medir el Tiempo de Vida de un Componente Electrónico:** Donde el resultado es el tiempo hasta que el componente falla, que puede variar incluso bajo condiciones de uso similares.

### Espacio Muestral y Eventos

{: .highlight}
El conjunto de todos los posibles resultados de un experimento aleatorio se denomina **espacio muestral**, simbolizado comúnmente como $$S$$ o $$\Omega$$. Cada resultado individual dentro del espacio muestral es un **punto muestral**.

{: .highlight}
Un **evento** es un conjunto de resultados (puntos muestrales) del espacio muestral. Por ejemplo, en el lanzamiento de un dado, el evento "obtener un número par" incluiría los resultados 2, 4 y 6.

### Probabilidad de Eventos

{: .highlight}
La **probabilidad** de un evento se define como una medida de cuán probable es que ocurra ese evento en una realización del experimento. Se basa en la relación entre el número de resultados que satisfacen el evento y el número total de resultados posibles en el espacio muestral, asumiendo que cada resultado es igualmente probable.

## Resultado

{: .note}
En el contexto de experimentos aleatorios en probabilidad y estadística. Un **resultado** es definido como el resultado observable de realizar un experimento, el cual, bajo las mismas condiciones, puede variar en cada realización. Esto ilustra la naturaleza aleatoria de tales experimentos, donde no es posible predecir con certeza el resultado específico antes de realizar el experimento.

Se ofrecen varios ejemplos para explicar este concepto:

1. **Lanzar una Moneda:** Cada lanzamiento de una moneda (considerada justa) puede resultar en cara o cruz. Cada resultado es independiente y no predecible con certeza, ilustrando la aleatoriedad del experimento.

2. **Lanzar Dos Monedas Simultáneamente:** En este caso, los posibles resultados incluyen todas las combinaciones de cara y cruz para las dos monedas, como cara-cara, cara-cruz, cruz-cara, y cruz-cruz.

3. **Lanzar una Moneda Hasta Obtener Cara:** Este experimento se continúa hasta que se observa el primer resultado de cara, demostrando que un experimento aleatorio puede tener múltiples resultados y ser repetido bajo las mismas condiciones hasta alcanzar un resultado específico.

### Espacio Muestral

{: .highlight}
El **espacio muestral** se introduce como el conjunto de todos los resultados posibles de un experimento. Por ejemplo, en el caso de lanzar dos monedas, el espacio muestral incluiría todas las combinaciones posibles de cara y cruz.

Es posible que el número total de resultados posibles en algunos experimentos puede ser infinito, aunque contable, lo que significa que estos resultados pueden ser enumerados o indexados de alguna manera. Esto se ilustra con el ejemplo de seguir lanzando una moneda hasta que aparece una cara, donde teóricamente, el experimento podría continuar indefinidamente, generando un conjunto infinito pero contable de posibles secuencias de resultados.

Este concepto se ilustra claramente con el experimento de lanzar repetidamente una moneda hasta que aparezca una cara. Teóricamente, este experimento podría continuar indefinidamente si se obtienen cruces sucesivas, lo que lleva a una infinita secuencia de lanzamientos. Sin embargo, a pesar de la infinitud de este conjunto de resultados, es un conjunto contable. 

## Evento

En el ámbito de la teoría de probabilidad, el concepto de **evento** es central y fundamental para entender cómo funcionan los experimentos aleatorios y cómo se calculan las probabilidades de diferentes resultados. Un evento es básicamente una colección de posibles resultados de un experimento aleatorio, es decir, un subconjunto del espacio muestral asociado a dicho experimento.

{: .note}
Formalmente, un **evento** se define como cualquier conjunto de resultados posibles de un experimento. El espacio muestral $$S$$ o $$\Omega$$ de un experimento es el conjunto de todos los posibles resultados individuales, y un evento es cualquier subconjunto de este espacio. Esto incluye desde el conjunto vacío, que representa un evento que nunca ocurre, hasta el espacio muestral completo, que es un evento que siempre ocurre.

### Clasificación de Eventos

Los eventos se pueden clasificar de varias maneras dependiendo de sus características:

- **Eventos Simples o Elementales:** Son aquellos que contienen un solo resultado del espacio muestral. Por ejemplo, en el lanzamiento de un dado, obtener un "3" es un evento simple.
- **Eventos Compuestos:** Incluyen dos o más resultados del espacio muestral. Siguiendo con el dado, que la cara superior sea un número par es un evento compuesto, ya que incluye los resultados 2, 4 y 6.

{: .highlight}
**Eventos Mutuamente Exclusivos:** Dos eventos son mutuamente exclusivos si no pueden ocurrir al mismo tiempo, es decir, no tienen resultados en común.

{: .highlight}
**Eventos Independientes:** Dos eventos son independientes si la ocurrencia de uno no afecta la probabilidad del otro.

### Ejemplos de Eventos

1. **Lanzamiento de Moneda:** El espacio muestral es $$\{cara, cruz\}$$. Un evento podría ser obtener "cara" en un lanzamiento. Otro evento podría ser obtener "cruz".

2. **Lanzamiento de Dos Dados:** Aquí el espacio muestral es más complejo, incluyendo todas las combinaciones posibles de ambos dados. Un evento de interés podría ser "la suma de los dados es 7", que incluiría resultados como $$(1, 6), (2, 5), (3, 4), (4, 3), (5, 2), (6, 1)$$.

## Eventos mutuamente excluyentes

Dos eventos se consideran mutuamente excluyentes si no pueden ocurrir al mismo tiempo. Por ejemplo, considere un lanzamiento de una sola moneda: los eventos “cruz” y “cara” son mutuamente excluyentes porque no podemos obtener ambas caras y cruces en un solo lanzamiento.

{: .note}
Eventos mutuamente excluyentes son aquellos que no pueden ocurrir al mismo tiempo. Es decir, si ocurre uno, no puede ocurrir el otro.

Podemos visualizar dos eventos mutuamente excluyentes como un par de círculos que no se superponen. No se superponen porque no hay ningún resultado para un evento que también esté en el espacio muestral para el otro:

¿Qué pasa con los eventos que no son mutuamente excluyentes? 

Si el evento $$A$$ arroja un número impar y el evento $$B$$ arroja un número mayor que dos, estos eventos no son mutuamente excluyentes. Tienen una intersección de $$\{3, 5\}$$ . Cualquier evento que tenga una intersección no vacía no es mutuamente excluyente.

**Ejemplos:**

**a)** Tenemos una bolsa con cinco canicas: tres son verdes y dos son azules. Supongamos que sacamos una canica de la bolsa. El evento $$A$$ es que la canica es verde. El evento $$B$$ es que la canica es azul. ¿Son estos eventos mutuamente excluyentes? La respuesta es si, **son eventos mutualmente excluyentes**

**b)** Lanzamos un dado una vez. En el evento $$A$$ sale un número impar. El evento $$B$$ es sacar un número mayor que cuatro. ¿Son estos eventos mutuamente excluyentes? No, son eventos **No mutalmente excluyentes**

Explicacion: En el caso del lanzamiento de un dado:

- El evento $$A = {1, 3, 5}$$.
- El evento $$B = {5, 6}$$.

Para que $$A$$ y $$B$$ sean mutuamente excluyentes, no deberían tener ningún resultado en común. Sin embargo, como puedes ver, ambos eventos incluyen el número 5. Esto significa que hay una situación en la que ambos eventos pueden ocurrir al mismo tiempo (si el dado cae en 5). Dado que existe esta posibilidad, los eventos no son mutuamente excluyentes.

Por lo tanto, es posible que ocurra $$A$$ y $$B$$ simultáneamente, lo cual sucede si el resultado del lanzamiento del dado es un 5, satisfaciendo tanto la condición de ser impar (evento $$A$$) como la condición de ser mayor que cuatro (evento $$B$$).

**c)** Lanzamos un dado una vez. En el evento $$A$$ sale un número par. El evento $$B$$ es sacar un número menor que dos. ¿Son estos eventos mutuamente excluyentes? La respuesta es si, **son eventos mutualmente excluyentes**

