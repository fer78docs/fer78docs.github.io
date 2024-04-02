---
layout: default
title: Simpson's paradox
nav_order: 4
parent: Exploratory Data Analysis
---

# Esbozando la paradoja de Simpson
Por lo general, las decisiones que tomamos a partir de nuestro conjunto de datos están influenciadas por el resultado de las medidas estadísticas que les aplicamos. Esos resultados nos informan sobre el tipo de correlación y las visualizaciones básicas del conjunto de datos. Sin embargo, a veces, las decisiones difieren cuando segregamos los datos en grupos y aplicamos medidas estadísticas, o cuando los agregamos y luego aplicamos medidas estadísticas. Este tipo de comportamiento anómalo en los resultados de un mismo conjunto de datos generalmente se denomina paradoja de Simpson . En pocas palabras, la paradoja de Simpson es la diferencia que aparece en una tendencia de análisis cuando un conjunto de datos se analiza en dos situaciones diferentes: primero, cuando los datos se separan en grupos y, segundo, cuando se agregan.

Aquí hay una tabla que representa la tasa de recomendación para dos consolas de juegos diferentes por hombres y mujeres individualmente y también combinadas:

|             | PS4          | Xbox Uno     |
|-------------|--------------|--------------|
| Masculino   | 50/150 = 30% | 180/360 = 50%|
| Femenino    | 200/250 = 80%| 36/40 = 90%  |
| Conjunto    | 250/400 = 62.5% | 216/400 = 54% |

La tabla anterior presenta la tasa de recomendación de dos videoconsolas diferentes: PS4 y Xbox One por hombres y mujeres, tanto de forma individual como combinada.

Supongamos que vas a comprar una videoconsola que tiene una recomendación máxima. Como se muestra en la tabla anterior, Xbox One es recomendada por un porcentaje mayor de hombres y mujeres que la PS4. Sin embargo, utilizando los mismos datos combinados, la PS4 tiene un porcentaje recomendado más alto (62,5%) según todos los usuarios. Entonces, ¿cómo decidirías cuál elegir? Los cálculos parecen bien pero, lógicamente, la toma de decisiones no parece acertada. Ésta es la paradoja de Simpson. El mismo conjunto de datos demuestra aquí dos argumentos opuestos.

Bueno, el problema principal, en este caso, es que cuando solo vemos los porcentajes de los datos separados, no considera el tamaño de la muestra. Dado que cada fracción muestra el número de usuarios que recomendarían la consola de juegos según el número solicitado, es relevante considerar el tamaño completo de la muestra. El tamaño de la muestra en los datos separados de hombres y mujeres difiere en gran medida. Por ejemplo, la recomendación masculina para PS4 es 50, mientras que la recomendación para Xbox One es 180. Hay una diferencia enorme en estos números. Xbox One tiene muchas más respuestas de hombres que de mujeres, mientras que en PS4 ocurre lo contrario. Debido a que menos hombres recomiendan la PlayStation, lo que da como resultado una calificación promedio más baja para la PS4 cuando se combinan los datos, se llega a la paradoja.

Para tomar una decisión única sobre qué consola elegir, debemos decidir si los datos se pueden combinar o si debemos mirarlos por separado. En este caso, tenemos que averiguar qué consola tiene más probabilidades de satisfacer tanto a hombres como a mujeres . Puede haber otros factores que influyan en estas revisiones, pero no tenemos estos datos, por lo que buscamos el número máximo de buenas críticas independientemente del sesgo de género. Aquí, agregar los datos tiene más sentido. Combinaremos la revisión e iremos con el promedio general. Dado que nuestro objetivo es combinar las revisiones y ver el promedio total, la agregación de datos tiene más sentido.

Parece que la paradoja de Simpson es un problema inverosímil que es teóricamente posible pero que nunca ocurre en la práctica porque nuestro análisis estadístico de los datos generales disponibles es preciso. Sin embargo, existen muchos estudios bien conocidos sobre la paradoja de Simpson en el mundo real.

Un ejemplo del mundo real son los tratamientos de salud mental como la depresión. La siguiente es una tabla sobre la efectividad de dos tipos de terapias administradas a los pacientes:

|                 | Terapia A      | Terapia B      |
|-----------------|----------------|----------------|
| Depresión ligera| 81/87 = 93%    | 234/270 = 87%  |
| Depresión severa| 192/263 = 73%  | 55/80 = 69%    |
| Ambos           | 273/350 = 78%  | 289/350 = 83%  |


Como puede ver, en la tabla anterior, existen dos tipos de terapias: Terapia A y Terapia B. La terapia A parece funcionar mejor tanto para la depresión leve como para la grave, pero la suma de los datos revela que el tratamiento B funciona mejor en ambos casos. ¿Cómo es esto posible? Bueno, no podemos concluir que los resultados después de la agregación de datos sean correctos, porque el tamaño de la muestra difiere en cada tipo de terapia. Para tomar una decisión única sobre qué terapias debemos seguir, debemos pensar de manera práctica: ¿cómo se generaron los datos? ¿Y qué factores influyen en los resultados que no se ven en absoluto?

En realidad, los médicos consideran que la depresión leve es un caso menos grave y la terapia A es más barata que la terapia B. Por lo tanto, los médicos recomiendan la terapia más simple, A, para la depresión leve.

Los detalles y hechos de los dos tipos de terapia no se mencionan en nuestro conjunto de datos. El tipo de depresión y la gravedad del caso conducen a variables de confusión (las variables de confusión son algo que no vemos en la tabla de datos, pero pueden determinarse mediante el análisis de antecedentes de los datos) porque afecta la decisión sobre qué tratamiento y método de recuperación. para seleccionar. Entonces, el factor que decide qué tratamiento funciona mejor para el paciente depende de la variable de confusión, que es la gravedad del caso. Para determinar qué terapia funciona mejor, necesitamos un informe de la gravedad de los casos y luego comparar las tasas de recuperación con ambas terapias en lugar de datos agregados entre grupos.

Responder las preguntas que queremos a partir de un conjunto de datos a veces requiere más análisis que simplemente mirar los datos disponibles. La lección que se desprende de la paradoja de Simpson es que los datos por sí solos son insuficientes. Los datos nunca son puramente objetivos y tampoco lo es la trama final. Por lo tanto, debemos considerar si estamos entendiendo la historia completa cuando manejamos un conjunto de datos.

Otro hecho que debe considerarse antes de concluir el análisis basado en el resultado que obtenemos es que correlación no implica causalidad . Esto es tan importante en el campo de la estadística que Wikipedia tiene un artículo aparte sobre esta afirmación.