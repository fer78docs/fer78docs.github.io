---
layout: default
title: Mass Funtions
nav_order: 3
parent: Intro Distribuciones de Probabilidad
grand_parent: Probabilidad
---


# Funciones de masa de probabilidad

Una función de masa de probabilidad (PMF) es un tipo de distribución de probabilidad que **define la probabilidad de observar un valor particular de una variable aleatoria discreta.** Por ejemplo, se puede utilizar un PMF para calcular la probabilidad de sacar un tres en un dado justo de seis caras.

Hay ciertos tipos de variables aleatorias (y distribuciones de probabilidad asociadas) que son relevantes para muchos tipos diferentes de problemas. Estas distribuciones de probabilidad de uso común tienen nombres y parámetros que las hacen adaptables a diferentes situaciones.

Por ejemplo, supongamos que lanzamos una moneda justa varias veces y contamos el número de caras. La función de masa de probabilidad que describe la probabilidad de cada resultado posible (p. ej., 0 caras, 1 cara, 2 caras, etc.) se denomina **distribución binomial**. Los parámetros para la distribución binomial son:

- `n` para el número de intentos (por ejemplo, `n=10` si lanzamos una moneda 10 veces)
- `p` para la probabilidad de éxito en cada prueba (probabilidad de observar un resultado particular en cada prueba. En este ejemplo, `p= 0,5` porque la probabilidad de observar caras en un lanzamiento de moneda justo es 0,5)

Si lanzamos una moneda normal 10 veces, decimos que el número de caras observadas sigue una distribución `Binomial(n=10, p=0.5)`. El siguiente gráfico muestra la función de masa de probabilidad para este experimento. Las alturas de las barras representan la probabilidad de observar cada resultado posible calculado por el PMF.

**Veamos cómo cambia la forma de la distribución binomial a medida que cambia el tamaño de la muestra.**

Utilice el control deslizante para cambiar el valor de x lanzamientos de moneda justos, entre uno y diez. Las alturas de las barras resultantes representan la probabilidad de observar diferentes valores de caras en x número de lanzamientos de moneda justos. Puede pasar el cursor sobre cada barra y ver el valor numérico real de la altura de la barra. Las barras más altas representan resultados más probables.

Observe que a medida que x aumenta, las barras se hacen más pequeñas. Esto se debe a que la suma de las alturas de todas las barras siempre será igual a 1. Entonces, cuando x es mayor, el número de caras que podemos observar aumenta y la probabilidad debe dividirse entre más valores.

[Binomial Distribution: Calculating Probability of a Given Number of Heads](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/binomial/binomial_single.html)