---
layout: default
title: Mass Funtions
nav_order: 2
parent: Intro Probability Distributions
grand_parent: Probability
---

# Funciones de masa de probabilidad

Una función de masa de probabilidad (PMF) es un tipo de distribución de probabilidad que **define la probabilidad de observar un valor particular de una variable aleatoria discreta.** Por ejemplo, se puede utilizar un PMF para calcular la probabilidad de sacar un tres en un dado justo de seis caras.

Hay ciertos tipos de variables aleatorias (y distribuciones de probabilidad asociadas) que son relevantes para muchos tipos diferentes de problemas. Estas distribuciones de probabilidad de uso común tienen nombres y parámetros que las hacen adaptables a diferentes situaciones.

Por ejemplo, supongamos que lanzamos una moneda justa varias veces y contamos el número de caras. La función de masa de probabilidad que describe la probabilidad de cada resultado posible (p. ej., 0 caras, 1 cara, 2 caras, etc.) se denomina **distribución binomial**. Los parámetros para la distribución binomial son:

- `n` para el número de intentos (por ejemplo, `n=10` si lanzamos una moneda 10 veces)
- `p` para la probabilidad de éxito en cada prueba (probabilidad de observar un resultado particular en cada prueba. En este ejemplo, `p= 0,5` porque la probabilidad de observar caras en un lanzamiento de moneda justo es 0,5)

Si lanzamos una moneda normal 10 veces, decimos que el número de caras observadas sigue una distribución `Binomial(n=10, p=0.5)`. El siguiente gráfico muestra la función de masa de probabilidad para este experimento. Las alturas de las barras representan la probabilidad de observar cada resultado posible calculado por el PMF.

**Veamos cómo cambia la forma de la distribución binomial a medida que cambia el tamaño de la muestra.**

Utilice el control deslizante para cambiar el valor de `x` lanzamientos de moneda justos, entre uno y diez. Las alturas de las barras resultantes representan la probabilidad de observar diferentes valores de caras en x número de lanzamientos de moneda justos. Puede pasar el cursor sobre cada barra y ver el valor numérico real de la altura de la barra. Las barras más altas representan resultados más probables.

Observe que a medida que x aumenta, las barras se hacen más pequeñas. Esto se debe a que la suma de las alturas de todas las barras siempre será igual a 1. Entonces, cuando x es mayor, el número de caras que podemos observar aumenta y la probabilidad debe dividirse entre más valores.

[Binomial Distribution: Calculating Probability of a Given Number of Heads](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/binomial/binomial_single.html)


## Calcular probabilidades usando Python

El método `binom.pmf()` de la biblioteca `scipy.stats` se puede utilizar para **calcular el PMF de la distribución binomial en cualquier valor**. Este método toma 3 valores:

- `x`: el valor del interés
- `n`: el número de ensayos
- `p`: la probabilidad de éxito

Por ejemplo, supongamos que lanzamos una moneda normal 10 veces y contamos el número de caras. Podemos usar la función `binom.pmf()` para calcular la probabilidad de observar 6 cabezas de la siguiente manera:

```python
# import necessary library
import scipy.stats as stats

# st.binom.pmf(x, n, p)
print(stats.binom.pmf(6, 10, 0.5))
```
Output
```
0.205078
```

Observe que dos de los tres valores que entran en el método `stats.binomial.pmf()` son los parámetros que definen la distribución binomial: `n` representa el número de intentos y `p` representa la probabilidad de éxito.

Uso de la función de masa de probabilidad en un rango

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


## Función de masa de probabilidad en un rango usando Python

Podemos utilizar el mismo método `binom.pmf()` de la biblioteca `scipy.stats` para calcular la probabilidad de observar un rango de valores. Como se mencionó en un ejercicio anterior, el método `binom.pmf` toma 3 valores:

- `x`: el valor del interés
- `n`: el número de ensayos
- `p`: la probabilidad de éxito

Por ejemplo, podemos calcular la probabilidad de observar entre 2 y 4 caras en 10 lanzamientos de moneda de la siguiente manera:
```python
import scipy.stats as stats

# calculating P(2-4 heads) = P(2 heads) + P(3 heads) + P(4 heads) for flipping a coin 10 times
print(stats.binom.pmf(2, n=10, p=.5) 
    + stats.binom.pmf(3, n=10, p=.5) 
    + stats.binom.pmf(4, n=10, p=.5))
```
Output:
```
0.366211
```

También podemos calcular la probabilidad de observar menos de un cierto valor, digamos 3 caras, sumando las probabilidades de los valores debajo de él:

```python
import scipy.stats as stats

# calculating P(less than 3 heads) = P(0 heads) + P(1 head) + P(2 heads) for flipping a coin 10 times
print(stats.binom.pmf(0, n=10, p=.5) 
    + stats.binom.pmf(1, n=10, p=.5) 
    + stats.binom.pmf(2, n=10, p=.5))
```
Output
```
0.0546875
```

Tenga en cuenta que debido a que nuestro rango deseado es inferior a 3 cabezas, no incluimos ese valor en la suma.

Cuando hay muchos valores de interés posibles, esta tarea de sumar probabilidades puede resultar difícil. Si queremos saber la probabilidad de observar 8 o menos caras en 10 lanzamientos de moneda, debemos sumar los valores del 0 al 8:

```python
import scipy.stats as stats

var = stats.binom.pmf(0, n = 10, p = 0.5) 
    + stats.binom.pmf(1, n = 10, p = 0.5) 
    + stats.binom.pmf(2, n = 10, p = 0.5) 
    + stats.binom.pmf(3, n = 10, p = 0.5) 
    + stats.binom.pmf(4, n = 10, p = 0.5) 
    + stats.binom.pmf(5, n = 10, p = 0.5) 
    + stats.binom.pmf(6, n = 10, p = 0.5) 
    + stats.binom.pmf(7, n = 10, p = 0.5) 
    + stats.binom.pmf(8, n = 10, p = 0.5)
```
Output
```
0.98926
```
Esto implica una gran cantidad de código repetitivo. En su lugar, también podemos utilizar el hecho de que la suma de las probabilidades de todos los valores posibles es igual a 1:

```
P(0to8heads) + P(9to10heads) = P(0to10heads) = 1
P(0to8heads) = 1 − P(9to10heads)
```
Ahora, en lugar de sumar 9 valores para las probabilidades entre 0 y 8 caras, podemos hacer 1 menos la suma de dos valores y obtener el mismo resultado:

```python
import scipy.stats as stats
# less than or equal to 8
1 - (stats.binom.pmf(9, n=10, p=.5) + stats.binom.pmf(10, n=10, p=.5))
```
Output
```
0.98926
```

