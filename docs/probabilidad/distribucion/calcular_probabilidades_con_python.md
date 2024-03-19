---
layout: default
title: Calcular Probabilidades con Python
nav_order: 4
parent: Intro Distribuciones de Probabilidad
grand_parent: Probabilidad
---

# Calcular probabilidades usando Python

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