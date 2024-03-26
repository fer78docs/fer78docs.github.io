---
layout: default
title: Variance Distribucion Binominal
nav_order: 7
parent: Intro Probability Distributions
grand_parent: Probability
---

# Varianza de la distribución binomial
La varianza de una distribución binomial es cuánto puede variar el valor esperado de éxito (del ejercicio anterior). En otras palabras, es una medida de la dispersión de las probabilidades con respecto al valor medio/esperado.

La varianza de la distribución binomial se calcula de manera similar al valor esperado utilizando los parámetros n (n.º de ensayos) y p (probabilidad de éxito). Usemos el ejemplo de los 10 lanzamientos justos de moneda para tratar de comprender cómo se calcula la varianza. Cada lanzamiento de moneda tiene una cierta probabilidad de salir cara o cruz: 0,5 y 0,5, respectivamente.

La varianza de un solo lanzamiento de moneda será la probabilidad de que se produzca el éxito multiplicada por la probabilidad de que no se produzca: p·(1-p) , o 0,5 x 0,5. Como tenemos n = 10 números de lanzamientos de moneda, la varianza de un único lanzamiento de moneda justo se multiplica por el número de lanzamientos. Así obtenemos la ecuación:

```
Variance(#ofHeads) = Var(X) = n × p × (1−p)
Variance(#ofHeads) = 10 × 0.5 × (1 − 0.5) = 2.5
```
Consideremos nuevamente nuestro cuestionario de 20 opciones múltiples. La varianza para responder correctamente una pregunta individual sería p·(1-p) , o 0,25 x 0,75. Luego multiplicamos esta variación por las 20 preguntas del cuestionario y obtenemos:
​
```
Variance(#ofCorrectAnswers)& = 20 × 0.25 × (1 − 0.25) = 3.75
```
Esperaríamos obtener 5 respuestas correctas, pero la varianza general de la distribución de probabilidad es 3,75.

