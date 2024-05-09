---
layout: default
title: Inferencial Statistic
nav_order: 8
parent: Probability & Statistics
---

## Estadística inferencial

La estadística descriptiva y la estadística inferencial son dos subcampos de la estadística. La estadística descriptiva incluye temas tratados anteriormente en este camino, incluidos resúmenes numéricos y visuales de datos. La prueba de hipótesis, por otro lado, es una forma de estadística inferencial, que se utiliza para hacer inferencias sobre una población utilizando una muestra más pequeña de datos.

Esto es importante porque las estadísticas descriptivas pueden informarnos sobre los datos que tenemos, pero a veces no podemos recopilar todos los datos que necesitamos para responder nuestras preguntas. Por ejemplo, tal vez queramos saber si las personas que reciben una vacuna tienen menos probabilidades de contraer una enfermedad. No podemos vacunar a todas las personas del mundo para probar esto, por lo que tendremos que vacunar a una muestra más pequeña de personas. Luego, si la vacuna parece funcionar en nuestra muestra, necesitamos saber si pudo haber sido una casualidad aleatoria o si es probable que sea cierto para el resto de la población. ¡Aquí es donde las pruebas de hipótesis pueden ayudar!

{: .note}
**La estadística inferencial consiste en utilizar una muestra (un subconjunto de una población) para hacer inferencias sobre una población de interés más grande.** Esto es útil cuando queremos saber algo sobre una población pero no podemos observar a todos sus miembros, a menudo debido a limitaciones de tiempo, viabilidad o monetarias. Algunos métodos que se utilizan en estadística inferencial incluyen la **prueba de hipótesis** y la **regresión**.

**La clave de la estadística inferencial es comprender que las muestras no siempre reflejan con precisión la población de la que proceden**. Una gran parte de la estadística inferencial consiste en cuantificar nuestra incertidumbre sobre una población observando una muestra más pequeña.

Por ejemplo, la población que se muestra a continuación se compone de 10 puntos azules y 5 puntos rojos, lo que significa que dos tercios de la población es azul y un tercio es rojo. Supongamos que tomamos una muestra aleatoria de 3 puntos y queremos usar esa muestra para estimar la proporción de la población que es azul. Si tenemos suerte, tomaremos una muestra de 2 puntos azules y 1 punto rojo, como se muestra a la izquierda, lo que representaría con precisión las proporciones de puntos azules y rojos en la población. Sin embargo, también podríamos muestrear aleatoriamente 3 puntos azules, o 2 puntos rojos y 1 punto azul, los cuales no coinciden con la población. La estadística inferencial nos permite observar una muestra y luego cuantificar nuestra incertidumbre sobre cuán similar (o diferente) podría ser toda la población.

![Estadistica Inferencial](https://fer78docs.github.io/assets/images/descriptive_inferential_statistics.webp)

**Ejemplo: contacto con el cliente**  

Suponga que trabaja en una empresa de ventas que está interesada en probar dos métodos diferentes de contacto con el cliente para ver si uno genera una tasa de respuesta más alta que el otro. Es imposible probar ambos métodos con toda la población de cada cliente pasado, presente y futuro. En su lugar, podría tomar una muestra de 1000 clientes y asignarlos aleatoriamente a un sistema de contacto por mensaje de texto o a un sistema de llamadas telefónicas. Después de un mes, podría calcular la diferencia en la tasa de respuesta (una estadística descriptiva) para los dos grupos de la muestra.

Suponga que descubre que los clientes que recibieron un mensaje de texto tenían un 12% más de probabilidades de responder que los clientes que recibieron una llamada telefónica. Esta es una estadística descriptiva de la muestra, pero lo que realmente desea saber es: si hubiera muestreado a toda la población de clientes, ¿habría encontrado al menos una diferencia del 12 % en la tasa de respuesta?

¡Aquí es donde los métodos de estadística inferencial resultan útiles! Por ejemplo, podría utilizar una prueba de hipótesis para estimar la probabilidad de que, en toda la población, observe una tasa de respuesta más alta para los mensajes de texto en comparación con las llamadas, dado que observó una tasa más alta en su muestra.

**Ejemplo: puntuaciones de exámenes**  

Supongamos que usted es un investigador que estudia la relación entre las calificaciones de las tareas de los estudiantes de secundaria y los puntajes de las pruebas estandarizadas. Sería muy difícil y costoso recopilar información sobre las calificaciones de las tareas y los resultados de los exámenes estandarizados de cada estudiante de secundaria del mundo. En su lugar, podría encontrar una muestra aleatoria de estudiantes e inspeccionar la relación entre las calificaciones de las tareas y los puntajes de las pruebas estandarizadas entre esa muestra. Finalmente, podría utilizar un análisis de regresión (otro método estadístico inferencial) para comprender si es probable que exista una relación similar en la población más grande de todos los estudiantes.

### Introducción a la prueba de hipótesis (simulación de una prueba T de una muestra)

La prueba de hipótesis es un marco para hacer preguntas sobre un conjunto de datos y responderlas con declaraciones probabilísticas. Existen muchos tipos diferentes de pruebas de hipótesis que se pueden utilizar para abordar diferentes tipos de preguntas y datos. En este artículo, analizaremos una simulación de una prueba t de una muestra para desarrollar una intuición sobre cuántos tipos diferentes de pruebas de hipótesis funcionan.

**El Caso**

El Programa de Bachillerato Internacional (IBDP) es un programa educativo a nivel mundial. Cada año, los estudiantes de las escuelas participantes pueden realizar una evaluación estandarizada para obtener su título. Las puntuaciones totales de esta evaluación oscilan entre 1 y 45. Según los datos proporcionados aquí , la puntuación total promedio de todos los estudiantes que tomaron este examen en mayo de 2020 fue de alrededor de 29,92. La distribución de puntuaciones se parece a esto:

![Distribucion Prueba T](https://fer78docs.github.io/assets/images/distribucion_pruebaT.svg)

Imagine una hipotética escuela en línea, Statistics Academy, que ofrece un programa de preparación para exámenes de cinco semanas. Supongamos que 100 estudiantes que tomaron la evaluación del IBDP en mayo de 2020 fueron elegidos al azar para participar en el primer grupo de este programa y que estos 100 estudiantes obtuvieron una puntuación promedio de 31,16 puntos en el examen, ¡aproximadamente 1,24 puntos más que el promedio internacional! ¿Estos estudiantes realmente están superando a sus compañeros? ¿O podría atribuirse esta diferencia al azar?

### Paso 2: definir las hipótesis nula y alternativa

Antes de intentar responder esta pregunta, es útil reformularla de manera que sea comprobable. En este momento, nuestra pregunta (**“¿Los estudiantes de la Academia de Estadística realmente están superando a sus compañeros?”**) no está claramente definida. Objetivamente, este grupo de 100 estudiantes tuvo un mejor desempeño que la población general, pero respondieron “¡sí, superaron a sus compañeros!” No se siente particularmente satisfactorio.

La razón por la que no es satisfactorio es la siguiente: si elegimos aleatoriamente CUALQUIER grupo de 100 estudiantes de la población de todos los examinados y calculamos el puntaje promedio para esa muestra, hay un 50% de posibilidades de que sea más alto que el promedio de la población. No es sorprendente observar un promedio más alto para una sola muestra.

Por supuesto, las grandes diferencias con el promedio de la población son menos probables: si todos los estudiantes de la Academia de Estadística obtuvieran 45 puntos en el examen (la puntuación más alta posible), probablemente estaríamos convencidos de que estos estudiantes tenían una ventaja real. El truco consiste en cuantificar cuándo las diferencias son “lo suficientemente grandes” como para convencernos de que estos estudiantes son sistemáticamente diferentes de la población general. Podemos hacer esto reformulando nuestra pregunta para centrarnos en la(s) población(es), en lugar de en nuestra(s) muestra(s) específica(s).

Una prueba de hipótesis comienza con dos hipótesis en competencia sobre la población de la que proviene una muestra particular (en este caso, los 100 estudiantes de la Academia de Estadística):

**Hipótesis 1 (técnicamente llamada Hipótesis Nula ):** Los 100 estudiantes de la Academia de Estadística son una muestra aleatoria de la población general de examinados, que obtuvieron una puntuación promedio de 29,92. Si esta hipótesis es cierta, los estudiantes de la Academia de Estadística obtuvieron una puntuación promedio ligeramente más alta por casualidad. Visualmente, esta configuración se parece a esto:

![Hipotesis](https://fer78docs.github.io/assets/images/Statistics_HypothesisTestingDiagram_2.svg)

**Hipótesis 2 (técnicamente llamada Hipótesis Alternativa ):** Los 100 estudiantes de la Academia de Estadística provenían de una población con una puntuación promedio diferente de 29,92. En esta hipótesis, debemos imaginar dos poblaciones diferentes que en realidad no existen: una en la que todos los estudiantes tomaron el programa de preparación para exámenes de la Academia de Estadística y otra en la que ninguno de los estudiantes tomó el programa. Si la hipótesis alternativa es cierta, nuestra muestra de 100 estudiantes de la Academia de Estadística provenía de una población diferente a la de los demás examinados. Esto se puede visualizar de la siguiente manera:

![Hipotesis](https://fer78docs.github.io/assets/images/Statistics_HypothesisTestingDiagram_1.svg)

Hay una aclaración más que debemos hacer para especificar completamente la hipótesis alternativa. Observe que, hasta ahora, no hemos dicho nada sobre el puntaje promedio para la “población 1” en el diagrama anterior, aparte de que NO es 29,92. En realidad, tenemos tres opciones para lo que dice la hipótesis alternativa sobre este promedio poblacional:

- es MAYOR QUE 29.92
- NO ES IGUAL A (es decir, MAYOR O MENOR QUE) 29,92
- es MENOS DE 29,92

Más adelante, analizaremos cómo la elección entre “mayor que”, “distinto de” y “menor que” afecta la prueba.

### Paso 3: determinar la distribución nula

Ahora que tenemos nuestra hipótesis nula, podemos generar una distribución nula : la distribución (entre muestras repetidas) de la estadística que nos interesa si la hipótesis nula es verdadera. En el ejemplo del IBDP descrito anteriormente, esta es la distribución de puntuaciones promedio para muestras repetidas de tamaño 100 extraídas de una población con una puntuación promedio de 29,92.

¡Esto puede resultarle familiar si ha aprendido sobre el teorema del límite central (CLT)! La teoría estadística nos permite estimar la forma de esta distribución utilizando una sola muestra. Puede aprender cómo hacer esto leyendo más sobre CLT, pero para los propósitos de este ejemplo, simulemos la distribución nula usando nuestra población. Podemos hacer esto mediante:

- Tomar muchas muestras aleatorias de 100 puntuaciones, cada una, de la población.
- Calcular y almacenar la puntuación promedio para cada una de esas muestras.
- Trazar un histograma de las puntuaciones medias

Esto produce la siguiente distribución, que es aproximadamente normal y centrada en el promedio de la población:

![Null Distribution_](https://fer78docs.github.io/assets/images/null_distribution.png)

Si la hipótesis nula es cierta, entonces la puntuación promedio de 31,16 observada entre los estudiantes de la Academia de Estadística es simplemente uno de los valores de esta distribución. Tracemos el promedio muestral en la distribución nula. Observe que este valor está dentro del rango de la distribución nula, pero está hacia la derecha donde hay menos densidad:

![null distribution_2](https://fer78docs.github.io/assets/images/null_distribution2.png)

### Paso 4: Calcule un valor P (o intervalo de confianza)

Aquí está la pregunta básica formulada en nuestra prueba de hipótesis:

Dado que la hipótesis nula es cierta (que los 100 estudiantes de la Academia de Estadística fueron seleccionados de una población con una puntuación promedio del IBDP de 29,92), ¿qué probabilidad hay de que su puntuación promedio sea 31,16?

El problema menor de esta pregunta es que la probabilidad de cualquier puntuación promedio exacta es muy pequeña, por lo que realmente queremos estimar la probabilidad de un rango de puntuaciones. Volvamos ahora a nuestras tres posibles hipótesis alternativas y veamos cómo la pregunta y el cálculo cambian ligeramente, dependiendo de cuál elijamos:

**Opción 1**

**Hipótesis alternativa:** La muestra de 100 puntajes obtenidos por estudiantes de la Academia de Estadística provino de una población con un puntaje promedio superior a 29,92.

En este caso, queremos saber la probabilidad de observar un promedio muestral mayor o igual a 31,16 dado que la hipótesis nula es verdadera. Visualmente, esta es la proporción de la distribución nula que es mayor o igual a 31,16 (sombreada en rojo a continuación). Aquí, la región roja representa alrededor del 3,1% de la distribución total. Esta proporción, que normalmente se escribe en forma decimal (es decir, 0,031), se denomina valor p .

![null distribution_3](https://fer78docs.github.io/assets/images/null_distribution_3.png)

**opcion 2**

**Hipótesis alternativa:** La muestra de 100 puntajes obtenidos por estudiantes de la Academia de Estadística provino de una población con un puntaje promedio que no es igual (es decir, mayor o menor que) 29,92.

Observamos un promedio muestral de 31,16 entre los estudiantes de la Academia de Estadística, que es 1,24 puntos más alto que el promedio poblacional (si la hipótesis nula es cierta) de 29,92. En la primera versión de la prueba de hipótesis (opción 1), estimamos la probabilidad de observar un promedio muestral que sea al menos 1,24 puntos mayor que el promedio poblacional. Para la hipótesis alternativa descrita en la opción 2, nos interesa la probabilidad de observar un promedio de muestra que sea al menos 1,24 puntos DIFERENTE (mayor O menor) que el promedio de la población. Visualmente, esta es la proporción de la distribución nula que está al menos a 1,24 unidades del promedio de la población (sombreado en rojo a continuación). Tenga en cuenta que esta área es dos veces mayor que en el ejemplo anterior, lo que lleva a un valor p que también es dos veces mayor: 0,062.


![null distribution_4](https://fer78docs.github.io/assets/images/null_distribution_4.png)

Si bien la opción 1 a menudo se conoce como prueba de una cara o de una cola , esta versión se conoce como prueba de dos caras o de dos colas , y hace referencia a las dos colas de la distribución nula que se cuentan en el valor p. Es importante tener en cuenta que la mayoría de las funciones de prueba de hipótesis en Python y R implementan una prueba de dos colas de forma predeterminada.

**Opción 3** 

**Hipótesis alternativa:** La muestra de 100 puntajes obtenidos por estudiantes de la Academia de Estadística provino de una población con un puntaje promedio inferior a 29,92.

Aquí queremos saber la probabilidad de observar un promedio muestral menor o igual a 31,16, dado que la hipótesis nula es verdadera. Esta también es una prueba unilateral, justo el lado opuesto de la opción 1. Visualmente, esta es la proporción de la distribución nula que es menor o igual a 31,16. Esta es un área muy grande (¡casi el 97% de la distribución!), lo que lleva a un valor p de 0,969.

![null distribution_5](https://fer78docs.github.io/assets/images/null_distribution_5.png)

En este punto, usted puede estar pensando: ¿por qué alguien elegiría esta versión de la hipótesis alternativa? En la vida real, si un programa de preparación de exámenes planeaba realizar un experimento riguroso para ver si sus estudiantes obtienen calificaciones diferentes a las de la población general, deberían elegir la hipótesis alternativa antes de recopilar datos. En ese momento, no sabrán si su muestra de estudiantes tendrá una puntuación promedio mayor o menor que el promedio de la población, aunque probablemente esperan que sea mayor.

Paso 5: interpretar los resultados
En los tres ejemplos anteriores, calculamos tres valores p diferentes (0,031, 0,062 y 0,969, respectivamente). Considere el primer valor p de 0,031. La interpretación de este número es la siguiente:

Si los 100 estudiantes de la Academia de Estadística fueron seleccionados al azar de toda la población (que obtuvo una puntuación promedio de 29,92), hay un 3,1% de posibilidades de que su puntuación promedio sea de 31,16 puntos o más.

Esto significa que es relativamente improbable, pero no imposible, que los estudiantes de la Academia de Estadística obtengan puntuaciones más altas (en promedio) que sus compañeros por casualidad, a pesar de que no hay una diferencia real a nivel de población. En otras palabras, los datos observados son improbables si la hipótesis nula es cierta. Tenga en cuenta que hemos probado directamente la hipótesis nula, ¡pero no la hipótesis alternativa! Por lo tanto, debemos tener un poco de cuidado al interpretar esta prueba: no podemos decir que hemos demostrado que la hipótesis alternativa es la verdad, sólo que los datos que recopilamos serían improbables bajo la hipótesis nula y, por lo tanto, creemos que la hipótesis alternativa es cierta. La hipótesis alternativa es más consistente con nuestras observaciones.

### Umbrales de significancia

Si bien es perfectamente razonable informar un valor p, muchos científicos de datos utilizan un umbral predeterminado para decidir si un valor p particular es significativo o no. Los valores P por debajo del umbral elegido se declaran significativos y llevan al científico de datos a "rechazar la hipótesis nula en favor de la alternativa". Una elección común para este umbral, que a veces también se denomina Alfa , es 0,05, ¡pero es una elección arbitraria! Usar un umbral más bajo significa que es menos probable que encuentre resultados significativos, pero también es menos probable que informe erróneamente un resultado significativo cuando no lo hay.

Utilizando el primer valor p de 0,031 y un umbral de significancia de 0,05, la Academia de Estadística podría rechazar la hipótesis nula y concluir que los 100 estudiantes que participaron en su programa obtuvieron puntuaciones significativamente más altas en la prueba que la población general.

Impacto de la hipótesis alternativa
Tenga en cuenta que diferentes hipótesis alternativas pueden llevar a conclusiones diferentes. Por ejemplo, la prueba unilateral descrita anteriormente (p = 0,031) llevaría a un científico de datos a rechazar la nula en un nivel de significancia de 0,05. Mientras tanto, una prueba bilateral sobre los mismos datos conduce a un valor p de 0,062, que es mayor que el umbral de 0,05. Por tanto, para la prueba bilateral, un científico de datos no podría rechazar la hipótesis nula. ¡Esto resalta la importancia de elegir una hipótesis alternativa con anticipación!

### Resumen y aplicaciones adicionales

Como seguramente habrá aprendido de este artículo, las pruebas de hipótesis pueden ser un marco útil para formular y responder preguntas sobre datos. Antes de utilizar las pruebas de hipótesis en la práctica, es importante recordar lo siguiente:

Un valor p es una probabilidad, generalmente expresada como un decimal entre cero y uno.
Un valor p pequeño significa que es poco probable que ocurra una estadística de muestra observada (o algo más extremo) si la hipótesis nula es cierta.
Se puede utilizar un umbral de significancia para traducir un valor p en un resultado "significativo" o "no significativo".
En la práctica, la hipótesis alternativa y el umbral de significancia deben elegirse antes de la recopilación de datos.
Existen muchas pruebas de hipótesis diferentes que se pueden utilizar para responder diferentes tipos de preguntas sobre datos. ¡Ahora que has aprendido sobre uno, tienes todas las habilidades que necesitas para comprender muchos más!