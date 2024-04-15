---
layout: default
title: Continuous Random Variables
nav_order: 5
parent: Probability & Statistics
---




## Zero Probability to Individual Values

¿Podemos realmente decir que es imposible que ocurran eventos de probabilidad cero? No se puede encontrar ningún ejemplo mientras se permanece en el ámbito de los espacios muestrales finitos. Por otro lado, en  espacios muestrales infinitos , abundan los posibles resultados de probabilidad cero. Las variables aleatorias continuas pueden tomar cualquier valor dentro de un intervalo continuo, y estos valores son no numerables.

### Experimento del Círculo Unitario

![Experimento del Circulo Unitario](https://fer78docs.github.io/assets/images/circulo_unitario.png)

Consideremos un experimento ilustrativo para entender mejor las variables aleatorias continuas. Imaginemos un círculo unitario, es decir, un círculo de radio uno, centrado en el origen de un sistema de coordenadas. En este experimento, el acto aleatorio consiste en colocar puntos dentro del círculo. La variable de interés en este caso es la distancia desde el origen hasta el punto donde cada punto es colocado aleatoriamente.

En este experimento, la variable aleatoria que define la distancia desde el origen hasta el punto puede tomar cualquier valor entre 0 y 1. El valor 0 se alcanzaría si el punto cae exactamente en el centro del círculo (el origen), mientras que el valor 1 se alcanza si el punto cae en cualquier parte del perímetro del círculo. Entre estos dos extremos, hay infinitos valores posibles que la distancia podría tomar, como 0.1, 0.001, 0.7213, etc. Estos valores forman un continuo y son ejemplos de una variable aleatoria continua.

Si consideramos anillos concéntricos dentro del círculo, cada anillo podría representar un intervalo específico para $$X$$, y la probabilidad de que $$X$$ tome un valor dentro de un anillo sería proporcional al área de ese anillo.

#### Asignación de Probabilidades

En el caso de variables continuas, la asignación de probabilidades presenta desafíos únicos. En teoría, la probabilidad de que la variable aleatoria tome un valor específico exacto dentro del intervalo es cero. Esto se debe a que la cantidad de posibles valores en un intervalo continuo es infinita, y asignar una probabilidad positiva a cada posible valor individual resultaría en una suma de probabilidades que excedería 1, violando la propiedad de normalización de probabilidades.

#### Propiedad de Normalización

La propiedad de normalización establece que la suma total de todas las probabilidades debe ser igual a 1. En el contexto de las variables aleatorias continuas, si asignáramos una probabilidad positiva, aunque sea muy pequeña, a cada posible valor individual, la suma infinita de estos valores positivos sería infinita, lo que claramente superaría el total permitido de 1.

#### Funciones de Densidad de Probabilidad (PDF)

Para manejar probabilidades en el caso de variables continuas, utilizamos lo que se conoce como**Funciones de Densidad de Probabilidad (PDF)** . Estas funciones no asignan probabilidades a valores individuales sino que describen la densidad de probabilidad en diferentes regiones del espacio de valores de la variable.

Por ejemplo, en lugar de preguntar cuál es la probabilidad de que la variable aleatoria sea exactamente 0.5, utilizamos la PDF para determinar la probabilidad de que la variable esté dentro de un intervalo, como entre 0.3 y 0.7.

## Probability Density Functions

{: .note}
En el estudio de las variables aleatorias continuas, las **Funciones de Densidad de Probabilidad** (PDFs, por sus siglas en inglés) son esenciales para modelar y comprender la distribución de probabilidad de estas variables. A diferencia de las Funciones de Masa de Probabilidad (PMFs), que asignan probabilidades a valores específicos de variables discretas, las PDFs se utilizan para construir modelos de probabilidad sobre intervalos de variables continuas.

### Conceptos Básicos de PDFs

{: .highlight}
Una PDF no proporciona directamente la probabilidad de un valor específico; en cambio, describe cómo se distribuye la probabilidad a lo largo de un intervalo de posibles valores. En el contexto de las variables continuas, una PDF es útil para calcular la probabilidad de que la variable caiga dentro de un rango específico.

#### Modelado de Probabilidades:

- Para construir una PDF, se puede comenzar definiendo la función en todo su rango posible, asegurando que el área bajo la curva de la función sea igual a uno.
- Por ejemplo, para una variable $$X$$ uniforme que varía de 0 a 1, una PDF simple podría ser una función constante donde el valor de la función (altura) es siempre 1 en el intervalo [0,1].

#### Cálculo de Probabilidades:

- Para calcular la probabilidad de que $$X$$ esté en un intervalo específico, como entre 0.2 y 0.4, calculamos el área bajo la PDF en ese intervalo.
- Esta área se obtiene integrando la función de densidad de probabilidad desde 0.2 hasta 0.4, y el resultado representa la probabilidad de que $$X$$ caiga dentro de ese rango.

### Propiedades Clave de las PDFs

1. **Positividad:**Todos los valores de una PDF deben ser no negativos, una propiedad compartida con las PMFs.

2. **Integración a Uno:**A diferencia de las PMFs, donde cada valor individual puede tener una probabilidad directamente asignada (y sumar todas las probabilidades da uno), en las PDFs el total del área bajo la curva debe ser igual a uno para que el modelo de probabilidad sea válido.

3. **Diferencias con PMFs:** Mientras que los valores de una PMF siempre deben ser menores o iguales a uno, los valores de una PDF pueden ser mayores que uno, siempre que el área bajo la curva se mantenga en uno. Esto es importante porque los valores de la PDF no representan probabilidades directas sino densidades de probabilidad, que ayudan a calcular probabilidades sobre intervalos.

### Aplicaciones y Contexto Real

Las PDFs son herramientas cruciales para modelar variables continuas en muchos campos, incluyendo la física, economía, y la biología. Por ejemplo, en la recolección de datos sensoriales o en estudios estadísticos donde los valores se distribuyen de manera continua, las PDFs permiten una modelación precisa de las probabilidades que se pueden esperar para diferentes rangos de valores, facilitando así la toma de decisiones basada en datos probabilísticos.

En resumen, las Funciones de Densidad de Probabilidad son fundamentales en la teoría de probabilidades para manejar y entender las variables aleatorias continuas, permitiendo modelar y calcular probabilidades en una manera que se ajusta a la naturaleza continua de los datos en estudio.