---
layout: default
title: Distribucion Binominal valor esperado
nav_order: 6
parent: Intro Probability Distributions
grand_parent: Probability
---

# Valor esperado en la Distribucion Binominal


Otros tipos de distribuciones tienen valores esperados y varianzas basadas en los parámetros dados, al igual que la distribución de Poisson. Recuerde que la distribución binomial tiene parámetros n, que representan el número de eventos y p, que representa la probabilidad de "éxito" (o el resultado específico que estamos buscando).

Considere el siguiente escenario: lanzamos una moneda justa 10 veces y contamos el número de caras que observamos. ¿Cuántas cabezas esperarías ver? Naturalmente, podrías pensar en 5, ¡y estarías en lo cierto! Lo que estamos haciendo es calcular el valor esperado sin siquiera darnos cuenta. Tomamos los 10 lanzamientos de moneda y lo multiplicamos por la probabilidad de obtener cara, o la mitad, obteniendo la respuesta de 5 caras. Y esa es exactamente la ecuación para el valor esperado de la distribución binomial:

```
Expected(#ofHeads) = E(X) = n×p
```
Tenga en cuenta que si estuviéramos contando el número de caras de 5 lanzamientos de moneda justos, el valor esperado sería:
```
5 × 0.5 = 2.5
```
Está bien que el valor esperado sea una fracción o tenga valores decimales, aunque sería imposible observar 2,5 caras.

Veamos un ejemplo diferente. Digamos que nos olvidamos de estudiar y vamos a adivinar **B** en las 20 preguntas de un cuestionario de opción múltiple. Si asumimos que cada opción de letra (A, B, C y D) tiene la misma probabilidad de ser la respuesta correcta para cada pregunta, ¿cuántas preguntas esperaríamos acertar? `n` equivaldría a 20, porque hay 20 preguntas, y `p` equivaldría a 0,25, porque hay una probabilidad de 1 entre 4 de que B sea la respuesta correcta. Usando la ecuación, podemos calcular:

``` 
Expected( #​​​​​​​​​​respuestas ​bien)​​​​​ ​= E(X)​​= 20 × 0.25 = 5
```
