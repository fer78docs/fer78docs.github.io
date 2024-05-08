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

{: .note}
La prueba de hipótesis es un marco para hacer preguntas sobre un conjunto de datos y responderlas con declaraciones probabilísticas. Existen muchos tipos diferentes de pruebas de hipótesis que se pueden utilizar para abordar diferentes tipos de preguntas y datos. En este artículo, analizaremos una simulación de una prueba t de una muestra para desarrollar una intuición sobre cuántos tipos diferentes de pruebas de hipótesis funcionan.

**El Caso**

El Programa de Bachillerato Internacional (IBDP) es un programa educativo a nivel mundial. Cada año, los estudiantes de las escuelas participantes pueden realizar una evaluación estandarizada para obtener su título. Las puntuaciones totales de esta evaluación oscilan entre 1 y 45. Según los datos proporcionados aquí , la puntuación total promedio de todos los estudiantes que tomaron este examen en mayo de 2020 fue de alrededor de 29,92. La distribución de puntuaciones se parece a esto:

![Distribucion Prueba T](https://fer78docs.github.io/assets/images/distribucion_pruebaT.svg)

Imagine una hipotética escuela en línea, Statistics Academy, que ofrece un programa de preparación para exámenes de cinco semanas. Supongamos que 100 estudiantes que tomaron la evaluación del IBDP en mayo de 2020 fueron elegidos al azar para participar en el primer grupo de este programa y que estos 100 estudiantes obtuvieron una puntuación promedio de 31,16 puntos en el examen, ¡aproximadamente 1,24 puntos más que el promedio internacional! ¿Estos estudiantes realmente están superando a sus compañeros? ¿O podría atribuirse esta diferencia al azar?