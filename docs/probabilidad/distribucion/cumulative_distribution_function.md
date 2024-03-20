---
layout: default
title: Cumulative Distribution Function
nav_order: 3
parent: Intro Probability Distributions
grand_parent: Probability
---

# Función de distribución acumulativa
La función de distribución acumulativa para una variable aleatoria discreta se puede derivar de la función de masa de probabilidad. Sin embargo, en lugar de la probabilidad de observar un valor específico, **la función de distribución acumulativa proporciona la probabilidad de observar un valor específico O MENOS.**

Como se analizó anteriormente, las probabilidades de todos los valores posibles en una distribución de probabilidad dada suman 1. **El valor de una función de distribución acumulativa en un valor dado es igual a la suma de las probabilidades menores que él, con un valor de 1 para la mayor número posible.**

Las funciones de distribución acumulativa aumentan constantemente, por lo que para dos números diferentes que podría tomar la variable aleatoria, el valor de la función siempre será mayor para el número mayor. 

```latex
If x1 < x2, --> CDF(x1) < CDF(x2)
```

Mostramos cómo se puede utilizar la función de masa de probabilidad para calcular la probabilidad de observar menos de 3 caras en 10 lanzamientos de moneda sumando las probabilidades de observar 0, 1 y 2 caras. La función de distribución acumulativa produce la misma respuesta al evaluar la función en CDF(X=2). En este caso, utilizar el CDF es más sencillo que el PMF porque requiere un cálculo en lugar de tres.

La animación del enlace muestra la relación entre la `función de masa de probabilidad` y la `función de distribución acumulativa`. El gráfico superior es el PMF, mientras que el gráfico inferior es el CDF correspondiente. Al observar la gráfica de una CDF, cada valor del eje y es la suma de las probabilidades menores o iguales que él en la PMF.

[Enlace a la animacion](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/cdf-vs-pmf/animated.html)

Podemos usar una función de distribución acumulativa para calcular la probabilidad de un rango específico tomando la diferencia entre dos valores de la función de distribución acumulativa. Por ejemplo, para encontrar la probabilidad de observar entre 3 y 6 caras, podemos tomar la probabilidad de observar 6 o menos cabezas y restar la probabilidad de observar 2 o menos caras. Esto deja un remanente de entre 3 y 6 cabezas.

La imagen de la derecha demuestra cómo funciona esto. Es importante tener en cuenta que para incluir el límite inferior en el rango, el valor que se resta debe ser uno menos que el límite inferior. En este ejemplo, queríamos saber la probabilidad de 3 a 6, que incluye 3. 

[Enlace a la animacion](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/cdf-animation/animation.html)

## Usando la función de distribución acumulativa en Python

Podemos utilizar el método `binom.cdf()` de la biblioteca `scipy.stats` para calcular la función de distribución acumulativa. Este método toma 3 valores:

- `x`: el valor de interés, buscando la probabilidad de este valor o menos
- `n`: el tamaño de la muestra
- `p`: la probabilidad de éxito

Calcular matemáticamente la probabilidad de observar 6 o menos caras en 10 lanzamientos de moneda justos (0 a 6 caras) se parece a lo siguiente:

```math
P(6 or fewer heads) = P(0 to 6 heads)
```
El codigo en Python es:
```python
import scipy.stats as stats

print(stats.binom.cdf(6, 10, 0.5))
```
Output
```
0.828125
```
Se puede pensar que calcular la probabilidad de observar entre 4 y 8 caras en 10 lanzamientos de moneda justos es tomar la diferencia del valor de la función de distribución acumulativa en 8 de la función de distribución acumulativa en 3:

```math
P(4 to 8 Heads) = P(0 to 8 Heads) − P(0 to 3 Heads)
```
En Python utilizamos el codigo:
```python
import scipy.stats as stats

print(stats.binom.cdf(8, 10, 0.5) - stats.binom.cdf(3, 10, 0.5))
```
Output
```
0.81738
```
Para calcular la probabilidad de observar más de 6 caras en 10 lanzamientos de moneda justos, restamos el valor de la función de distribución acumulativa en 6 de 1. Matemáticamente, esto se parece a lo siguiente:
```math
P(more than 6 Heads) = 1 - P(6 or fewer Heads)
```
Tenga en cuenta que "más de 6 cabezas" no incluye 6. En Python, calcularíamos esta probabilidad usando el siguiente código:
```python
import scipy.stats as stats
print(1 - stats.binom.cdf(6, 10, 0.5))
```
Output
```
0.171875
```
