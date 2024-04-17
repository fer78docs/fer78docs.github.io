---
layout: default
title: Expectation
nav_order: 6
parent: Probability & Statistics
---

## Expectativa

El concepto de **expectativa** (o valor esperado) es fundamental en el campo de la probabilidad y estadísticas. **La expectativa proporciona un resumen numérico central de una variable aleatoria, ofreciendo una medida de la "tendencia central" o el promedio a largo plazo que uno puede esperar en una serie de experimentos** donde la variable aleatoria se observa repetidamente.

{: .highlight}
La expectativa de una variable aleatoria $$X$$, denotada como $$E[X]$$ o $$\mu$$, es el promedio ponderado de todos los posibles valores que $$X$$ puede tomar, ponderados por la probabilidad de cada valor. Matemáticamente se define de diferentes maneras dependiendo de si la variable aleatoria es discreta o continua:

- **Variable Discreta**: Si $$X$$ es una variable aleatoria discreta que toma valores $$(x_1, x_2, x_3, \dots)$$ con probabilidades $$(p_1, p_2, p_3, \dots)$$, entonces el valor esperado de $$X$$ se calcula como:

  $$
  E[X] = \sum_{i} x_i p_i
  $$

  donde la suma se extiende sobre todos los valores posibles de $$X$$.

Ejemplo: Calcularemos la expectativa de una variable aleatoria que sigue una distribución binomial, donde 
$$𝑛 = 10$$ (número de ensayos) y $$𝑝 = 0.5$$ (probabilidad de éxito en cada ensayo).

```python
import scipy.stats as stats

# Parámetros de la distribución binomial
n = 10  # número de ensayos
p = 0.5  # probabilidad de éxito

# Crear una variable aleatoria binomial
binomial_var = stats.binom(n, p)

# Calcular la expectativa
expected_value = binomial_var.mean()
print("Expectativa de la variable binomial:", expected_value)
```

- **Variable Continua**: Si $$X$$ es una variable aleatoria continua con una función de densidad de probabilidad (PDF) $$f(x)$$, el valor esperado se define como:

  $$
  E[X] = \int_{-\infty}^{\infty} x f(x) \, dx
  $$

  donde la integral se evalúa sobre todo el rango de $$X$$.

Ejemplo: Calcular la expectativa de una variable aleatoria que sigue una distribución normal, con media $$𝜇 = 0$$ y desviación estándar $$𝜎 = 1$$.

```python
# Parámetros de la distribución normal
mu = 0  # media
sigma = 1  # desviación estándar

# Crear una variable aleatoria normal
normal_var = stats.norm(mu, sigma)

# Calcular la expectativa
expected_value = normal_var.mean()
print("Expectativa de la variable normal:", expected_value)
```

### Generalizando el Cálculo de la Expectativa

Para otras distribuciones, puedes seguir un procedimiento similar utilizando las funciones proporcionadas por SciPy para esa distribución específica. Aquí está cómo se haría de forma general:

```python
# Para una distribución general, reemplazar 'dist' con el nombre de la distribución
# y configurar sus parámetros específicos.
dist_var = stats.dist(param1, param2, ...)

# Calcular la expectativa
expected_value = dist_var.mean()
print("Expectativa de la distribución:", expected_value)
```

## Ley de los Grandes Numeros

{: .note}
La Ley de los Grandes Números (LLN) es un teorema fundamental en teoría de la probabilidad que describe el resultado de realizar el mismo experimento un gran número de veces. Según la LLN, **el promedio de los resultados obtenidos de un gran número de pruebas se acercará al valor esperado a medida que se incremente el número de pruebas**. Esto implica que las frecuencias relativas de los resultados convergen a las probabilidades teóricas.

### LLN Débil vs. LLN Fuerte

- **LLN Débil**: Asegura que, para cualquier tolerancia $$\epsilon > 0$$, la probabilidad de que el promedio de las muestras difiera del valor esperado por más de $$\epsilon$$ tiende a cero conforme el tamaño de la muestra se hace infinitamente grande.

- **LLN Fuerte**: Establece que con probabilidad 1, el promedio de las muestras converge al valor esperado cuando el tamaño de la muestra tiende a infinito.

### Simulaciones Estadísticas en Python

#### Generación de Datos

Usaremos Python para simular datos utilizando módulos como `numpy` y `scipy`. Por ejemplo, para simular una variable aleatoria binomial, podemos usar el siguiente código:

```python
import numpy as np
# Simular 1000 ensayos de una distribución binomial con n=10 y p=0.5
data = np.random.binomial(10, 0.5, 1000)
```

#### Cálculo de Promedios

Para calcular el promedio de los datos simulados y compararlos con el valor esperado:

```python
average = np.mean(data)
print("Promedio calculado:", average)
```

#### Análisis de Datos y Estimación de Parámetros

- Interpretación de Resultados: Los resultados de las simulaciones deben interpretarse en el contexto de la LLN. Por ejemplo, si el promedio calculado de los ensayos binomiales difiere significativamente del valor esperado (5 en este caso), se debería aumentar el número de ensayos.

- Estimación de Parámetros: La estimación de parámetros puede mejorar utilizando métodos como el de Máxima Verosimilitud o los Métodos de Momentos. Esto permite ajustar los parámetros de la distribución a partir de los datos observados para que coincidan más estrechamente con el valor teórico esperado.

```python
import matplotlib.pyplot as plt
import numpy as np

# Simular progresivamente mayores cantidades de ensayos
sample_sizes = np.arange(100, 10000, 10)
averages = [np.mean(np.random.binomial(10, 0.5, size)) for size in sample_sizes]

# Graficar los resultados
plt.plot(sample_sizes, averages, label="Promedio de Ensayos Binomiales")
plt.axhline(y=5, color='r', linestyle='--', label="Valor Esperado")
plt.xlabel("Tamaño de la Muestra")
plt.ylabel("Promedio Calculado")
plt.legend()
plt.show()
```

![Grandes Numeros](https://fer78docs.github.io/assets/images/grandes_numeros.png)

