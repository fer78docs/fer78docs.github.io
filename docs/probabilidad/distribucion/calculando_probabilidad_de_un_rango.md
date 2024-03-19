---
layout: default
title: Calcular Probabilidades de un rango
nav_order: 5
parent: Intro Distribuciones de Probabilidad
grand_parent: Probabilidad
---

# Uso de la función de masa de probabilidad en un rango

Hemos visto que podemos calcular la probabilidad de observar un valor específico usando una función de masa de probabilidad. ¿Qué pasa si queremos encontrar la probabilidad de observar un rango de valores para una variable aleatoria discreta? Una forma de hacer esto es sumando la probabilidad de cada valor.

Por ejemplo, digamos que lanzamos una moneda justa 5 veces y queremos saber la probabilidad de obtener entre 1 y 3 caras. Podemos visualizar este escenario con la función de masa de probabilidad:

![Binomial Distribution: Calculating Probability of a Range](https://fer78docs.github.io/assets/images/Binomial-Distribution-PMF-Probability-over-a-Range.webp)

Podemos calcular esto usando la siguiente ecuación donde `P(x)` es la probabilidad de observar el número `x` de éxitos (cara en este caso):

```
P(1 to 3 heads) = P(1<= X <=3)
P(1 to 3 heads) = P(X=1) + P(X=2) + P(X=3)
P(1 to 3 heads) = 0.1562 + 0.3125 + 0.3125
P(1 to 3 heads) = 0.7812
```



Visualicemos lo que significa tomar la probabilidad de un rango. Utilice los controles deslizantes para seleccionar un rango de valores que representen el número de caras que podríamos observar en 10 lanzamientos de moneda justos.

Pruebe diferentes rangos para ver cómo cambian las probabilidades para diferentes valores. Pase el cursor sobre una barra individual para ver la altura de la barra (que corresponde a la probabilidad de que ocurra el valor).

​[Binomial Distribution: Calculating Probability of a Range](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/binomial-range_v2/index.html)
