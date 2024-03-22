---
layout: default
title: Poisson Distribution
nav_order: 5
parent: Intro Probability Distributions
grand_parent: Probability
---

# Introducción a la distribución de Poisson

Existen numerosas distribuciones de probabilidad que se utilizan para representar casi cualquier evento aleatorio. En la lección anterior, aprendimos sobre la distribución binomial para representar eventos como cualquier número de lanzamientos de moneda, así como la distribución normal para representar eventos como la altura de una mujer seleccionada al azar.

La distribución de Poisson es otra distribución común y se utiliza para describir la cantidad de veces que ocurre un determinado evento dentro de un intervalo de tiempo o espacio fijo. Por ejemplo, la distribución de Poisson se puede utilizar para describir la cantidad de automóviles que pasan por una intersección específica entre las 4 p.m. y las 5 p.m. de un día determinado. También se puede utilizar para describir la cantidad de llamadas recibidas en una oficina entre las 13:00 y las 15:00 horas de un día determinado.

La distribución de Poisson está definida por el parámetro de tasa, simbolizado por la letra griega lambda, **λ**.

Lambda representa el valor esperado (o el valor promedio) de la distribución. Por ejemplo, si nuestro número esperado de clientes entre la 1:00 p.m. y las 2:00 p.m. es 7, entonces estableceríamos el parámetro para la distribución de Poisson en 7. El PMF para la distribución de Poisson(7) es el siguiente:

![Distribucion de Poisson](https://fer78docs.github.io/assets/images/poisson.png)

¿Cómo se ve la PMF de la distribución de Poisson con diferentes valores en el parámetro lambda?

Utilice el control deslizante del subprograma para ver cómo cambia la distribución de la función de masa de probabilidad a medida que lambda cambia entre 1 y 10. La altura de las barras representa la probabilidad de observar el número a lo largo del eje x. Puede pasar el cursor sobre cualquier barra específica y ver la probabilidad específica de ese valor.

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/poisson-slider/index.html)


## Calcular probabilidades de valores exactos utilizando la función de masa de probabilidad

La distribución de Poisson es una distribución de probabilidad discreta, por lo que puede describirse mediante una función de masa de probabilidad y una función de distribución acumulativa.

Podemos usar el método `poisson.pmf()` en la biblioteca `scipy.stats` para evaluar la probabilidad de observar un número específico dado el parámetro (valor esperado) de una distribución. 

Por ejemplo, supongamos que esperamos que llueva 10 veces en los próximos 30 días. El número de veces que llueve en los próximos 30 días tiene “distribución de Poisson” con lambda = 10. Podemos calcular la probabilidad de que llueva exactamente 6 veces de la siguiente manera:

```python
import scipy.stats as stats
# expected value = 10, probability of observing 6
stats.poisson.pmf(6, 10)
```
Output
```
0.06305545800345125
```
Al igual que las funciones de masa de probabilidad anteriores de variables aleatorias discretas, las probabilidades individuales se pueden sumar para encontrar la probabilidad de observar un valor en un rango.

Por ejemplo, si esperamos que llueva 10 veces en los próximos 30 días, el número de veces que llueve en los próximos 30 días tiene una “distribución de Poisson” con lambda = 10. Podemos calcular la probabilidad de que llueva entre 12 y 14 veces. como sigue:

```python
import scipy.stats as stats
# expected value = 10, probability of observing 12-14
stats.poisson.pmf(12, 10) 
    + stats.poisson.pmf(13, 10) 
    + stats.poisson.pmf(14, 10)
```
Output
```
0.21976538076223123
```

## Calcular probabilidades de un rango usando la función de densidad acumulativa

Podemos usar el método `poisson.cdf()` en la biblioteca `scipy.stats` para evaluar la probabilidad de observar un número específico o menos dado el valor esperado de una distribución. Por ejemplo, si quisiéramos calcular la probabilidad de observar 6 o menos eventos de lluvia en los próximos 30 días cuando esperábamos 10, podríamos hacer lo siguiente:

```python
import scipy.stats as stats
# expected value = 10, probability of observing 6 or less
stats.poisson.cdf(6, 10)
```
Output
```
0.130141420882483
```

Esto significa que hay aproximadamente un 13% de posibilidades de que haya 6 lluvias o menos en el mes en cuestión.

También podemos utilizar este método para evaluar la probabilidad de observar un número específico o más dado el valor esperado de la distribución. Por ejemplo, si quisiéramos calcular la probabilidad de observar 12 o más eventos de lluvia en los próximos 30 días cuando esperábamos 10, podríamos hacer lo siguiente:

```python
import scipy.stats as stats
# expected value = 10, probability of observing 12 or more
1 - stats.poisson.cdf(11, 10)
```
Output
```
0.30322385369689386
```

Esto significa que hay aproximadamente un 30% de posibilidades de que haya 12 o más lluvias en el mes en cuestión.

Tenga en cuenta que utilizamos 11 en la declaración anterior a pesar de que 12 era el valor dado en el mensaje. Queríamos calcular la probabilidad de observar 12 o más lluvias, lo que incluye 12. `stats.poisson.cdf(11, 10)` Evalúa la probabilidad de observar 11 o menos lluvias, por lo que `1 - stats.poisson.cdf(11, 10)` sería igual a la probabilidad de observar 12 o más lluvias.

Sumar probabilidades individuales en un amplio rango puede resultar engorroso. A menudo es más fácil calcular la probabilidad de un rango utilizando la función de densidad acumulada en lugar de la función de masa de probabilidad. Podemos hacer esto tomando la diferencia entre la CDF del punto final más grande y la CDF de uno menos que el punto final más pequeño del rango.

Por ejemplo, aunque todavía esperamos 10 lluvias en los próximos 30 días, podríamos usar el siguiente código para calcular la probabilidad de observar entre 12 y 18 eventos de lluvia:

```python
import scipy.stats as stats
# expected value = 10, probability of observing between 12 and 18
stats.poisson.cdf(18, 10) - stats.poisson.cdf(11, 10)
```
Output
```
0.29603734909303947
```

## Expectativa de la distribución de Poisson

Anteriormente mencionamos que el parámetro lambda (λ) es el valor esperado (o valor promedio) de la distribución de Poisson. Pero ¿qué significa esto?

Pongamos esto en contexto: digamos que somos vendedores, y después de muchas semanas de trabajo, calculamos que nuestro promedio es de 10 ventas por semana. Si tomamos este valor como nuestro valor esperado de una distribución de Poisson, la función de masa de probabilidad tendrá el siguiente aspecto:

![Distribucion de Poisson](https://fer78docs.github.io/assets/images/funcion_de_pm.png)

La barra más alta representa el valor con mayor probabilidad de ocurrir. En este caso, la barra más alta está en 10. Sin embargo, esto no significa que realizaremos 10 ventas. Significa que, en promedio, en todas las semanas, esperamos que nuestro promedio sea de aproximadamente 10 ventas por semana.

Miremos esto de otra manera. Tomemos una muestra de 1000 valores aleatorios de la distribución de Poisson con el valor esperado de 10. Podemos usar el método `poisson.rvs()` en la biblioteca `scipy.stats` para generar valores aleatorios:

```python
import scipy.stats as stats

# generate random variable
# stats.poisson.rvs(lambda, size = num_values)
rvs = stats.poisson.rvs(10, size = 1000)
```
El histograma de este muestreo se parece al siguiente:

![Distribucion de Poisson](https://fer78docs.github.io/assets/images/poisson_rvs.png)

Podemos ver observaciones tan bajas como 2 pero tan altas como 20. Las barras más altas están en 9 y 10. Si tomáramos el promedio de las 1000 muestras aleatorias, obtendríamos:

```python
print(rvs.mean())
```
Output:
```
10.009
```

Este valor está muy cerca de 10, lo que confirma que sobre las 1000 observaciones, el valor esperado (o promedio) es 10.

Cuando hablamos del valor esperado, nos referimos al promedio de muchas observaciones. Esto se relaciona con la Ley de los Grandes Números: cuantas más muestras tengamos, es más probable que las muestras se parezcan a la población real y la media de las muestras se acerque al valor esperado. Entonces, aunque el vendedor pueda realizar 3 ventas una semana, puede realizar 16 la siguiente y 11 la semana siguiente. A largo plazo, después de muchas semanas, el valor esperado (o promedio) seguiría siendo 10.

## Propagación de la distribución de Poisson

Las distribuciones de probabilidad también tienen varianzas calculables. Las varianzas son una forma de medir la dispersión de valores y probabilidades en la distribución. Para la distribución de Poisson, la varianza es simplemente el valor de lambda (λ), lo que significa que el valor esperado y la varianza son equivalentes en las distribuciones de Poisson.

Sabemos que la distribución de Poisson tiene una variable aleatoria discreta y debe ser mayor que 0 (piense, un vendedor no puede tener menos de 0 ventas, una tienda no puede tener menos de 0 clientes), por lo que a medida que aumenta el valor esperado, el número de posibles Los valores que la distribución puede asumir también aumentarían.

El primer gráfico a continuación muestra una distribución de Poisson con lambda igual a tres, y el segundo gráfico muestra una distribución de Poisson con lambda igual a quince. Observe que en el segundo gráfico, la dispersión de la distribución aumenta. Además, tenga en cuenta que la altura de las barras en la segunda barra disminuye ya que hay más valores posibles en la distribución.

![Distribucion de Poisson 1 ](https://fer78docs.github.io/assets/images/distribucion_poisson_1.png)

![Distribucion de Poisson 2 ](https://fer78docs.github.io/assets/images/distribucion_poisson_2.png)

Como podemos ver, a medida que aumenta el parámetro lambda, también aumenta la varianza (o dispersión) de los valores posibles.

Podemos calcular la varianza de una muestra usando el método `numpy.var()`:

```python
import scipy.stats as stats
import numpy as np

rand_vars = stats.poisson.rvs(4, size = 1000)
print(np.var(rand_vars))
```
Output:
```
3.864559
```

Debido a que esto se calcula a partir de una muestra, es posible que la varianza no sea EXACTAMENTE igual a lambda. Sin embargo, esperamos que sea relativamente cercano cuando el tamaño de la muestra es grande, como en este ejemplo.

Otra forma de ver el aumento de los valores posibles es tomar el rango de una muestra (los valores mínimo y máximo de un conjunto). El siguiente código extraerá 1000 variables aleatorias de la distribución de Poisson con lambda = 4 y luego imprimirá los valores mínimo y máximo observados usando las funciones `.min()` y `.max()` de Python:

```python
import scipy.stats as stats

rand_vars = stats.poisson.rvs(4, size = 1000)

print(min(rand_vars), max(rand_vars))
```
Output:
```
0 12
```

Si aumentamos el valor de lambda a 10, veamos cómo cambian los valores mínimo y máximo:

```python
import scipy.stats as stats

rand_vars = stats.poisson.rvs(10, size = 1000)

print(min(rand_vars), max(rand_vars))
```
Output:
```
1 22
```

Estos valores están más distribuidos, lo que indica una variación mayor.