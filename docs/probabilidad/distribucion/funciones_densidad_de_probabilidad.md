---
layout: default
title: Probability Density Functions
nav_order: 4
parent: Intro Probability Distributions
grand_parent: Probability
---

# Funciones de densidad de probabilidad
De manera similar a cómo las variables aleatorias discretas se relacionan con las funciones de masa de probabilidad, las **variables aleatorias continuas** se relacionan con las funciones de densidad de probabilidad. Definen las distribuciones de probabilidad de variables aleatorias continuas y abarcan todos los valores posibles que puede adoptar la variable aleatoria dada.

Cuando se representa gráficamente, una función de densidad de probabilidad es una curva que atraviesa todos los valores posibles que puede tomar la variable aleatoria, y el área total bajo esta curva suma 1.

La siguiente imagen muestra una función de densidad de probabilidad. El área resaltada representa la probabilidad de observar un valor dentro del rango resaltado.

![Probability Density](https://fer78docs.github.io/assets/images/Adding-Area.gif)

En una función de densidad de probabilidad, no podemos calcular la probabilidad en un solo punto. Esto se debe a que el área de la curva debajo de un único punto es siempre cero. El siguiente gif muestra esto.

![Probability Density one point](https://fer78docs.github.io/assets/images/Normal-Distribution-Area-to-Zero.gif)

Como podemos ver en la imagen anterior, a medida que el intervalo se hace más pequeño, el ancho del área bajo la curva también se hace más pequeño. Al intentar evaluar el área bajo la curva en un punto específico, el ancho de esa área se vuelve 0 y, por lo tanto, la probabilidad es igual a 0.

Podemos calcular el área bajo la curva usando la función de distribución acumulativa para la distribución de probabilidad dada.

Por ejemplo, las alturas caen bajo un tipo de distribución de probabilidad llamada **distribución normal**. Los parámetros de la distribución normal son la media y la desviación estándar, y utilizamos la forma *Normal(media, desviación estándar)* como abreviatura.

Sabemos que la altura de las mujeres tiene una media de 167,64 cm con una desviación estándar de 8 cm, lo que las sitúa bajo la distribución Normal(167,64,8).

Digamos que queremos saber la probabilidad de que una mujer elegida al azar mida menos de 158 cm. Podemos usar la función de distribución acumulativa para calcular el área bajo la curva de la función de densidad de probabilidad de 0 a 158 para encontrar esa probabilidad.

![Area](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/norm_pdf_167_8_filled.svg)

Podemos calcular el área de la región azul en Python usando el método `norm.cdf()` de la biblioteca `scipy.stats`. Este método toma 3 valores:

- `x`: el valor del interés
- `loc:` la media de la distribución de probabilidad
- `scale`: la desviación estándar de la distribución de probabilidad

```python
import scipy.stats as stats

# stats.norm.cdf(x, loc, scale)
print(stats.norm.cdf(158, 167.64, 8))
```
Output
```
0.1141
```

## Funciones de densidad de probabilidad y función de distribución acumulativa

Podemos tomar la diferencia entre dos rangos superpuestos para calcular la probabilidad de que una selección aleatoria esté dentro de un rango de valores para distribuciones continuas. Este es esencialmente el mismo proceso que calcular la probabilidad de un rango de valores para distribuciones discretas.

![Rangos superpuestos](https://fer78docs.github.io/assets/images/Normal-PDF-Range.gif)

Digamos que queremos calcular la probabilidad de observar aleatoriamente a una mujer de entre 165 cm y 175 cm, suponiendo que las alturas todavía siguen la distribución Normal (167,74, 8). Podemos calcular la probabilidad de observar estos valores o menos. La diferencia entre estas dos probabilidades será la probabilidad de observar aleatoriamente a una mujer en este rango dado. Esto se puede hacer en Python usando el método `norm.cdf()` de la biblioteca `scipy.stats`. Como se mencionó anteriormente, este método adopta 3 valores:

```python
import scipy.stats as stats
# P(165 < X < 175) = P(X < 175) - P(X < 165)
# stats.norm.cdf(x, loc, scale) - stats.norm.cdf(x, loc, scale)
print(stats.norm.cdf(175, 167.74, 8) - stats.norm.cdf(165, 167.74, 8))
```
Output
```
0.45194
```

También podemos calcular la probabilidad de observar aleatoriamente un valor o mayor restando de 1 la probabilidad de observar menos que el valor dado. Esto es posible porque sabemos que el área total bajo la curva es 1, por lo que la probabilidad de observar algo mayor que un valor es 1 menos la probabilidad de observar algo menor que el valor dado.

Digamos que queremos calcular la probabilidad de observar a una mujer que mide más de 172 centímetros, suponiendo que las alturas todavía siguen la distribución Normal (167,74, 8). Podemos pensar en esto como lo opuesto a observar a una mujer que mide menos de 172 centímetros. Podemos visualizarlo de esta manera:

![Grafica](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/norm_pdf_167_8_filled2.svg)

Podemos usar el siguiente código para calcular el área azul tomando 1 menos el área roja:
```python
import scipy.stats as stats

# P(X > 172) = 1 - P(X < 172)
# 1 - stats.norm.cdf(x, loc, scale)
print(1 - stats.norm.cdf(172, 167.74, 8))
```
Output
```
0.45194
```
