---
layout: default
title: Random Variables
nav_order: 4
parent: Probability & Statistics
---


## Variables Aleatorias

Las variables aleatorias son un concepto central en la teoría de la probabilidad y estadística, representando cantidades que resultan de un experimento aleatorio y cuyos valores no son predecibles con certeza antes de realizar el experimento. Estas variables pueden clasificarse en dos grandes categorías: variables aleatorias discretas y variables aleatorias continuas.

{: .highlight}
Una variable aleatoria puede ser entendida como una función que asigna un valor numérico a cada resultado de un espacio muestral asociado con un experimento aleatorio. Por ejemplo, si lanzas un dado, el resultado (número de puntos hacia arriba) es el valor que toma la variable aleatoria.

## Variables aleatorias discretas

{: .note}
Las **variables aleatorias discretas** son aquellas que toman un número finito o contablemente infinito de valores distintos. Cada uno de estos valores tiene una probabilidad asociada, y la suma de todas estas probabilidades debe ser igual a uno. Este tipo de variable es muy común en la estadística y la teoría de la probabilidad, y se utiliza frecuentemente para modelar situaciones donde los resultados son claramente separables y contables. Pueden adoptar valores que se pueden contar, como 0, 1, 2, ..., n, o una lista de valores específicos como {-3, -1, 0, 1, 5}.

### Variable Aleatoria de Bernoulli

{: .highlight}
Una variable aleatoria de Bernoulli **es un tipo específico de variable aleatoria discreta que sólo toma dos posibles valores, típicamente 0 y 1, para representar los resultados de un único ensayo de Bernoulli**. Este tipo de variable es fundamental en probabilidad y estadística para modelar el resultado de experimentos que tienen exactamente dos posibles resultados, comúnmente etiquetados como "éxito" y "fracaso".

### Definición

Una variable de Bernoulli $$X$$ se define de la siguiente manera:
- $$X = 1$$ con probabilidad $$p$$ (éxito).
- $$X = 0$$ con probabilidad $$1-p$$ (fracaso).


### Ejemplo con la Suma de Dos Dados

Si consideramos la variable $$S$$ como la suma de dos lanzamientos de un dado:
- $$P(S = 2) = \frac{1}{36}$$ porque solo hay una forma de obtener un 2: lanzando dos unos.
- $$P(S = 3) = \frac{2}{36}$$ porque hay dos combinaciones que dan un 3: (1,2) y (2,1).
- Y así sucesivamente hasta $$S = 12$$.

Estos cálculos asumen que todos los resultados son igualmente probables, lo cual es cierto para un dado justo.

### Aplicación Práctica: Variable Aleatoria Bernoulli

{: .highlight}
Una **variable aleatoria Bernoulli** es un tipo especial de variable aleatoria discreta que solo toma dos valores, generalmente 0 y 1. Es extremadamente útil para modelar experimentos binarios como el lanzamiento de una moneda.

#### Ejemplo con el Lanzamiento de una Moneda
- Si la moneda es justa, $$P(X = 1) = 0.5$$ y $$P(X = 0) = 0.5$$.
- Si la moneda no es justa y la probabilidad de cara es 0.7, entonces $$P(X = 1) = 0.7$$ y $$P(X = 0) = 0.3$$.

La **PMF** en este caso asignaría 0.7 a obtener cara y 0.3 a obtener cruz, reflejando la naturaleza sesgada de la moneda.

### Simulación en Python

Vamos a construir una función en Python que simule un experimento de Bernoulli, el cual podría representar, por ejemplo, el lanzamiento de una moneda:

```python
import numpy as np

def bernoulli_trial(p=0.5):
    """Simula un experimento de Bernoulli.
        Args:
    p (float): Probabilidad de éxito (por defecto 0.5).
        Returns:
    int: 1 si el experimento resulta en éxito, 0 en caso contrario.
    """
    return 1 if np.random.rand() <= p else 0
```

En esta función, `np.random.rand()` genera un número aleatorio entre 0 y 1, y compara este número con la probabilidad de éxito `p`. Si el número generado es menor o igual a `p`, el resultado es un éxito (1); de lo contrario, es un fracaso (0).

### Simulación y Análisis de Resultados

Podemos usar esta función para realizar múltiples ensayos y observar la frecuencia de éxitos, lo que nos permite estimar la probabilidad de éxito de la moneda:

```python
def simulate_bernoulli_trials(n, p=0.5):
    """Simula n ensayos de Bernoulli y reporta la frecuencia de éxitos.
        Args:
    n (int): Número de ensayos.
    p (float): Probabilidad de éxito.
    
    Returns:
    float: Frecuencia de éxitos.
    """
    results = [bernoulli_trial(p) for _ in range(n)]
    return sum(results) / n

# Simular 1000 lanzamientos de una moneda con p = 0.7
n_trials = 1000
success_prob = 0.612199
frequency_of_success = simulate_bernoulli_trials(n_trials, success_prob)

print(f"La frecuencia de éxito estimada es {frequency_of_success:.2f}")
```
Output:
```
La frecuencia de éxito estimada es 0.71
```

Este código simula 1000 lanzamientos de una moneda donde la probabilidad de obtener cara (éxito) es del 70%. La función simulate_bernoulli_trials devuelve la frecuencia de éxitos, que debería acercarse a 0.7 a medida que el número de ensayos aumenta.

### Visualización de la Convergencia

Para visualizar cómo la frecuencia de éxitos converge a la probabilidad real, podríamos realizar múltiples simulaciones aumentando progresivamente el número de ensayos y graficar los resultados:

```python
import matplotlib.pyplot as plt

trial_counts = [10, 50, 100, 500, 1000, 5000, 10000]
frequencies = [simulate_bernoulli_trials(count, success_prob) for count in trial_counts]

plt.figure(figsize=(10, 5))
plt.plot(trial_counts, frequencies, marker='o', linestyle='-')
plt.axhline(y=success_prob, color='r', linestyle='--')
plt.title('Convergencia de la Frecuencia de Éxitos a la Probabilidad Real')
plt.xlabel('Número de Ensayos')
plt.ylabel('Frecuencia de Éxitos')
plt.xscale('log')
plt.show()
```

![Visualización de la Convergencia](https://fer78docs.github.io/assets/images/Visualización de la Convergencia.png)

Este gráfico mostrará cómo la frecuencia de éxitos se estabiliza y converge hacia la probabilidad real de éxito (0.612199 en este caso) a medida que aumenta el número de ensayos, ilustrando la ley de los grandes números.

### Función de Masa de Probabilidad (PMF)  

{: .highlight}
La Función de Masa de Probabilidad (PMF) es una función que **describe la probabilidad de que una variable aleatoria discreta tome un valor específico**. Es una función que devuelve la probabilidad de que una variable aleatoria discreta sea exactamente igual a algún valor.​ Es una función que asocia a cada punto de su espacio muestral X la probabilidad de que esta lo asuma. La función de probabilidad suele ser el medio principal para definir una distribución de probabilidad discreta, y tales funciones existen para variables aleatorias escalares o multivariantes, cuyo dominio es discreto.

La función de masa de probabilidad de un dado. Todos los números tienen la misma probabilidad de aparecer cuando este es tirado.
![pmf_dado](https://fer78docs.github.io/assets/images/funcion_de_masa_probabilidad.png)

### Tipos de Variables Aleatorias Discretas

Los tipos de variables aleatorias discretas se clasifican comúnmente según las distribuciones de probabilidad que describen cómo se comportan los datos asociados a estas variables. Aquí describo algunas de las distribuciones más comunes y utilizadas para variables aleatorias discretas.
En Python, la librería `scipy.stats` proporciona implementaciones de las PMFs para muchas distribuciones discretas comunes, lo que facilita su cálculo en la práctica. Estas funciones son extremadamente útiles para simulaciones, modelado estadístico y análisis probabilístico en una amplia gama de aplicaciones.

1. **Distribución Binomial**:  
   Usada cuando se están observando el número de éxitos en un número fijo de ensayos independientes y cada ensayo tiene solo dos posibles resultados (éxito o fracaso).  
   La PMF de una distribución binomial describe la probabilidad de obtener un número específico de éxitos en un número fijo de ensayos independientes, cada uno con dos posibles resultados y una misma probabilidad de éxito.

    ```python
    from scipy.stats import binom
    import numpy

    # Parámetros
    n = 10  # número de ensayos
    p = 0.5  # probabilidad de éxito
    size = 100 # muestras a generar

    # Generar Variables
    numpy.random.binomial(n, p, size)

    # Calcular PMF para un valor específico
    k = 5  # número de éxitos
    prob = binom.pmf(k, n, p)
    print(f"Probabilidad de {k} éxitos en {n} ensayos: {prob:.4f}")
    ```


2. **Distribución de Poisson**:
    Aplica para modelar el número de eventos en un intervalo de tiempo o espacio fijo cuando estos eventos ocurren con una tasa media conocida y de manera independiente entre sí.
    La PMF de una distribución de Poisson mide la probabilidad de un número determinado de eventos ocurriendo en un intervalo fijo, dado que estos eventos ocurren con una tasa media conocida y de manera independiente.

    ```python
    from scipy.stats import poisson
    import numpy

    lambda_ = 3  # tasa media de eventos por intervalo
    zize = 10 # número de muestras a generar.

    # Generar variables
    numpy.random.poisson(lambda_, size)

    # Calcular PMF
    k = 4  # número de eventos
    prob = poisson.pmf(k, lambda_)
    print(f"Probabilidad de {k} eventos: {prob:.4f}")
    ```


3. **Distribución Geométrica**:
    Describe el número de ensayos necesarios para obtener el primer éxito en una secuencia de ensayos independientes, cada uno con dos posibles resultados.
    La PMF de una distribución geométrica describe la probabilidad de que el primer éxito ocurra en el ensayo $$𝑘$$

    ```python
    from scipy.stats import geom
    import numpy
    
    p = 0.2  # probabilidad de éxito en cada ensayo
    zize = 10 # número de muestras a generar.

    # generar variable
    numpy.random.geometric(p, size)

    # Calcular PMF
    k = 5  # ensayo en el que ocurre el primer éxito
    prob = geom.pmf(k, p)
    print(f"Probabilidad de primer éxito en el intento {k}: {prob:.4f}")
    ```

4. **Distribución Binomial Negativa**:
    Generaliza la distribución geométrica para contar el número de ensayos requeridos para obtener un número fijo de éxitos.
    Esta distribución cuenta cuántos ensayos son necesarios para lograr un número especificado de éxitos.

    ```python
    from scipy.stats import nbinom
    import numpy

    r = 5  # número de éxitos deseados
    p = 0.5  # probabilidad de éxito en cada ensayo
    zize = 10 # número de muestras a generar.

    # generar variable
    numpy.random.negative_binomial(n, p, size)

    # Calcular PMF
    k = 10  # total de ensayos
    prob = nbinom.pmf(k-r, r, p)
    print(f"Probabilidad de alcanzar {r} éxitos en {k} ensayos: {prob:.4f}")
    ```

5. **Distribución Hipergeométrica**:
    Modela el número de éxitos en una muestra de tamaño fijo tomada sin reemplazo de una población que consta de dos tipos de objetos (éxitos y fracasos).  
    La PMF de la distribución hipergeométrica describe la probabilidad de obtener un número determinado de éxitos en una muestra extraída sin reemplazo de una población finita que consta de dos tipos de objetos.

    ```python
    from scipy.stats import hypergeom
    import numpy
    
    M = 20  # tamaño total de la población
    n = 7   # número de éxitos en la población
    N = 12  # tamaño de la muestra

    # Calcular PMF
    k = 3  # número de éxitos observados en la muestra
    prob = hypergeom.pmf(k, M, n, N)
    print(f"Probabilidad de {k} éxitos en una muestra de {N}: {prob:.4f}")

    # generar variable
    ngood   # número de elementos "buenos" en la población.
    nbad    # número de elementos "malos" en la población.
    nsample # número de elementos a muestrear (sin reemplazo).
    size    # número de muestras a generar.

    numpy.random.hypergeometric(ngood, nbad, nsample, size=None)
   ```

6. **Distribución Uniforme Discreta**:
   - Todos los valores posibles de la variable tienen la misma probabilidad de ocurrir.
   - Parámetros: el mínimo y máximo valor que puede tomar la variable.

7. **Distribución de Bernoulli**:
   - Un caso especial de la distribución binomial con un solo ensayo $$n = 1$$.
   - Parámetro: probabilidad de éxito $$p$$.

8. **Distribución Multinomial**:
   - Extensión de la distribución binomial para situaciones en las que cada ensayo puede resultar en más de dos categorías.
   - Parámetros: número de ensayos $$n$$ y vector de probabilidades $$p$$ para cada categoría.

Estas distribuciones permiten modelar una gran variedad de procesos y fenómenos en diversos campos como la biología, ingeniería, economía, ciencias sociales, y más. Cada tipo de distribución proporciona un modelo estadístico que se adapta a las características específicas de los datos y la naturaleza del experimento o la observación realizada.


## Variables aleatorias continuas

{: .note}
Las **variables aleatorias continuas** son aquellas que pueden tomar cualquier valor numérico dentro de un intervalo o conjunto de intervalos, a diferencia de las variables aleatorias discretas que tienen valores contables y separados. Este tipo de variables es fundamental en estadística y probabilidad para modelar fenómenos que requieren una escala de medida infinita y continua.

### Características Principales

1. **Valores no Contables**: Las variables aleatorias continuas pueden adoptar cualquier valor dentro de un rango específico, que puede ser finito o infinito.
2. **Función de Densidad de Probabilidad (PDF)**: A diferencia de las variables discretas que usan una función de probabilidad de masa, las continuas se describen mediante una función de densidad de probabilidad. Esta función no proporciona probabilidades directamente, sino que el área bajo la curva de la función entre dos puntos corresponde a la probabilidad de que la variable aleatoria caiga dentro de ese intervalo.

### Ejemplos de Variables Aleatorias Continuas

- **Altura de los estudiantes en una clase**: La altura puede variar continuamente y puede ser cualquier valor dentro de un rango razonable, por ejemplo, entre 1.50 metros y 2.00 metros.
- **Tiempo necesario para completar una tarea**: Este tiempo puede ser cualquier número no negativo, medido con precisión hasta fracciones de segundo.
- **Presión en un tanque de gas**: La presión puede fluctuar y tomar cualquier valor dentro de los límites de seguridad del tanque.

### Distribuciones Comunes de Variables Aleatorias Continuas

- **Distribución Normal (Gaussiana)**: Una de las distribuciones más importantes y comunes en estadística. Es simétrica y describe fenómenos naturales, sociales y de medición donde los valores tienden a agruparse alrededor de un promedio.
- **Distribución Exponencial**: Usada para modelar el tiempo entre eventos en un proceso de Poisson, como el tiempo entre llamadas telefónicas en un call center.
- **Distribución Uniforme**: Describe una situación donde todos los valores dentro de un cierto intervalo son igualmente probables, como elegir un número al azar entre 0 y 1.




### Variables Aleatorias Continuas

1. **Normal (Gaussiana)**:

   - `loc`: media de la distribución (mu).
   - `scale`: desviación estándar de la distribución (sigma).
   - `size`: número de muestras a generar.

   ```python
   numpy.random.normal(loc=0.0, scale=1.0, size=None)
   ```
   Genera números a partir de una distribución normal con media `loc` y desviación estándar `scale`.

2. **Exponencial**:

   - `scale`: inverso de la tasa (lambda), a veces llamado parámetro de escala.
   - `size`: número de muestras a generar.

   ```python
   numpy.random.exponential(scale=1.0, size=None)
   ```
   Genera números a partir de una distribución exponencial con un parámetro de escala.

3. **Uniforme**:

   - `low`: límite inferior del rango de los valores.
   - `high`: límite superior del rango de los valores.
   - `size`: número de muestras a generar.

   ```python
   numpy.random.uniform(low=0.0, high=1.0, size=None)
   ```
   Genera números a partir de una distribución uniforme entre `low` y `high`.

4. **Beta**:

   - `a`: parámetro de forma alpha.
   - `b`: parámetro de forma beta.
   - `size`: número de muestras a generar.

   ```python
   numpy.random.beta(a, b, size=None)
   ```
   Genera números a partir de una distribución beta con parámetros `a` y `b`.

5. **Gamma**:

   - `shape`: parámetro de forma (k).
   - `scale`: parámetro de escala (theta).
   - `size`: número de muestras a generar.

   ```python
   numpy.random.gamma(shape, scale=1.0, size=None)
   ```
   Genera números a partir de una distribución gamma con un parámetro de forma y escala.

Estos métodos permiten simular datos que siguen estas distribuciones, lo que es útil en simulaciones, pruebas de hipótesis, y para entender mejor el comportamiento estadístico de fenómenos modelados por estas distribuciones.