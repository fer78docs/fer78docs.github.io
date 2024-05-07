---
layout: default
title: Discrete Distributions
nav_order: 6
parent: Probability & Statistics
---

## Temas

 - [Distribucion Binomial](#distribucion-binomial)

Los tipos de variables aleatorias discretas se clasifican comúnmente según las distribuciones de probabilidad que describen cómo se comportan los datos asociados a estas variables. 

## Distribucion Binomial

{: .note}
La distribución binomial o distribución binómica es una distribución de probabilidad discreta que cuenta el número de éxitos en una secuencia de $$𝑛$$ ensayos de Bernoulli independientes entre sí con una probabilidad fija $$𝑝$$ de ocurrencia de éxito entre los ensayos.

La distribución binomial se utiliza con frecuencia para modelizar el número de aciertos en una muestra de tamaño $$𝑛$$ extraída con reemplazo de una población de tamaño N. 

Para cada experimento llamado **ensayo Bernoulli**, utilizamos una variable aleatoria que toma el valor 1 cuando se consigue un éxito y el valor 0 en caso contrario. La variable aleatoria, suma de todas estas variables aleatorias, cuenta el número de éxitos y sigue una distribución binomial. Es posible entonces obtener la probabilidad de k éxitos en una repetición de n experimentos:

La ley binomial se utiliza en diversos campos de estudio, especialmente a través de pruebas estadísticas que permiten interpretar datos y tomar decisiones en situaciones que dependen del azar. Debido a su sencilla definición, es una de las leyes de probabilidad que se estudian en los cursos introductorios de teoría de la probabilidad.

### Ejemplo Explicativo

Supongamos que lanzamos una moneda tres veces $$N = 3$$, y cada lanzamiento tiene una probabilidad de 0.7 de ser cara. Los posibles resultados (espacio muestral) y la distribución de $$X$$ serían:

- **0 caras (X = 0):** $$(Cruz, Cruz, Cruz)$$
  - Probabilidad: $$(1 - 0.7)^3 = 0.027 $$
- **1 cara (X = 1):** $$(Cara, Cruz, Cruz), (Cruz, Cara, Cruz), (Cruz, Cruz, Cara)$$
  - Probabilidad: $$ \binom{3}{1} \times 0.7^1 \times 0.3^2 = 0.189 $$
- **2 caras (X = 2):** $$(Cara, Cara, Cruz), (Cruz, Cara, Cara), (Cara, Cruz, Cara)$$
  - Probabilidad: $$ \binom{3}{2} \times 0.7^2 \times 0.3^1 = 0.441$$
- **3 caras (X = 3):** $$(Cara, Cara, Cara)$$
  - Probabilidad: $$ 0.7^3 = 0.343 $$

### Ejemplo de Código en Python

Para trabajar con la variable aleatoria binomial en Python, una de las herramientas más útiles y comunes es el módulo `numpy`, específicamente la función `numpy.random.binomial`. Este módulo facilita la simulación de ensayos binomiales, permitiendo generar datos que siguen una distribución binomial. 

Este código utiliza la función `np.random.binomial` para simular 1000 ensayos binomiales donde se lanzan 10 monedas por ensayo con una probabilidad de 0.7 de obtener cara en cada lanzamiento. Luego, genera un histograma para visualizar la distribución de los resultados.

```python
import numpy as np
import matplotlib.pyplot as plt

def simulate_binomial(n, p, trials):
    """Simula 'trials' ensayos binomiales de 'n' lanzamientos con probabilidad 'p'."""
    results = np.random.binomial(n, p, trials)
    return results

# Parámetros de la simulación
n = 10  # Número de lanzamientos
p = 0.7  # Probabilidad de cara
trials = 1000  # Número de simulaciones

# Realizar simulaciones
results = simulate_binomial(n, p, trials)

# Visualizar resultados
plt.hist(results, bins=np.arange(n+2)-0.5, edgecolor='black', density=True)
plt.title('Distribución Binomial de Caras en 10 Lanzamientos')
plt.xlabel('Número de Caras')
plt.ylabel('Frecuencia Relativa')
plt.xticks(range(n+1))
plt.show()
```

![Visualización de la Convergencia](https://fer78docs.github.io/assets/images/distribucion_binomial.png)


## Geometric Random Variable

### Ensayos Independientes de Bernoulli

{: .highlight}
Un ensayo independiente implica que el resultado de un ensayo no influye ni puede ser influenciado por los resultados de otros ensayos. En el contexto de lanzar una moneda, significa que el resultado de un lanzamiento no afecta el resultado del siguiente.

#### Ejemplo con Dos Lanzamientos
Si lanzamos una moneda dos veces con una probabilidad de 0.7 de sacar cara en cada lanzamiento, la probabilidad de obtener dos caras seguidas sería $$0.7 \times 0.7 = 0.49$$.

#### Explicación y Ejemplo
Supongamos que lanzamos una moneda hasta que salga cara por primera vez, y queremos saber cuántos lanzamientos se necesitan.

```python
def geometric_trial(p=0.7):
    """Simula una variable aleatoria geométrica.
    Args:
        p (float): Probabilidad de sacar cara. 
    Returns:
        int: Número de lanzamientos hasta el primer éxito.
    """
    count = 1
    while bernoulli_trial(p) == 0:
        count += 1
    return count
```

Esta función utiliza la función de Bernoulli definida anteriormente para simular lanzamientos sucesivos hasta que el primer lanzamiento resulte en éxito (cara).

### Función de Masa de Probabilidad (PMF) de la Variable Geométrica

{: .highlight}
La PMF de una variable aleatoria geométrica da la probabilidad de que se necesite un número específico de ensayos para alcanzar el primer éxito. 

#### Ejemplo

- $$P(X=1) = 0.7$$ (sacar cara en el primer lanzamiento).
- $$P(X=2) = 0.3 \times 0.7$$ (sacar cruz en el primero y cara en el segundo).
- $$P(X=n) = 0.3^{(n-1)} \times 0.7$$ (sacar cruz en los primeros $$n-1$$ lanzamientos y cara en el $$n$$-ésimo).

### Prueba de normalización de variable aleatoria geométrica opcional

Este segmento explica la variable aleatoria geométrica en detalle, destacando su importancia en el contexto de ensayos independientes de Bernoulli, como el lanzamiento repetido de una moneda hasta obtener el primer éxito (cara). Además, se aborda la propiedad de normalización de la distribución geométrica y se anticipa una demostración práctica utilizando Python. Vamos a desglosar y ampliar estos conceptos y ejemplos en español.

### Variable Aleatoria Geométrica

{: .highlight}
La variable aleatoria geométrica mide el número de intentos necesarios hasta obtener el primer éxito en una serie de ensayos independientes de Bernoulli. Por ejemplo, en el lanzamiento de una moneda, esta variable contaría cuántos lanzamientos se realizan hasta que aparece la primera cara, asumiendo que cada lanzamiento es independiente del anterior.

#### Propiedades de la Variable Geométrica

- **Espacio Muestral Infinito pero Contable:** La variable geométrica puede tomar una cantidad infinita de valores (1, 2, 3, ...), ya que teóricamente podrían requerirse infinitos lanzamientos para obtener una cara. Sin embargo, estos valores son contables, lo que clasifica a la variable como discreta.
- **Distribución de Probabilidad:** La probabilidad de que la variable aleatoria geométrica tome un valor específico $$k$$ es una función de la probabilidad de éxito $$p$$ y la probabilidad de fracaso $$q = 1-p$$. donde $$k$$ es el número de lanzamientos realizados hasta obtener el primer éxito.

$$P(X = k) = q^{k-1} \cdot p$$

### Aplicación Práctica en Python

Este código simula 1000 ensayos de una variable aleatoria geométrica y utiliza un histograma para visualizar cuántos lanzamientos se necesitan típicamente para obtener el primer éxito. Esta visualización ayuda a comprender la naturaleza de la distribución geométrica y la efectividad de los ensayos de Bernoulli independientes.

```python
import numpy as np
import matplotlib.pyplot as plt

def geometric_trial(p=0.7):
    count = 0
    while np.random.rand() >= p:
        count += 1
    return count + 1

# Simulación de 1000 ensayos geométricos
results = [geometric_trial(p=0.7) for _ in range(1000)]

# Visualización de la distribución
plt.hist(results, bins=max(results), edgecolor='black')
plt.title('Distribución de la Variable Aleatoria Geométrica')
plt.xlabel('Número de Lanzamientos hasta el Primer Éxito')
plt.ylabel('Frecuencia')
plt.show()
```
![Visualización de la Convergencia](https://fer78docs.github.io/assets/images/variable_aleatoria_geométrica.png)




## Cumulative Distribution Function 

La **Función de Distribución Acumulativa** (CDF, por sus siglas en inglés "Cumulative Distribution Function") es una herramienta fundamental en teoría de la probabilidad y estadística que describe la **acumulación de probabilidad hasta un cierto valor de una variable aleatoria**. Vamos a explorar en detalle qué es, cómo funciona, y sus aplicaciones principales.

{: .highlight}
Para una variable aleatoria $$X$$, la función de distribución acumulativa $$F_X(x)$$ se define como la probabilidad de que $$X$$ tome un valor menor o igual a $$x$$. Matemáticamente, esto se expresa como:
$$
F_X(x) = P(X \leq x)
$$
Esta función proporciona una descripción completa de la distribución de probabilidad de la variable aleatoria.

### Propiedades de la CDF

1. **No decreciente**: $$F_X(x)$$ es siempre una función no decreciente de $$x$$. Esto significa que si $$a \leq b $$, entonces $$F_X(a) \leq F_X(b)$$.
2. **Límites**: $$F_X(x)$$ tiene un límite de 0 cuando $$x$$ tiende a $$-\infty$$ y un límite de 1 cuando $$x$$ tiende a $$\infty$$).
3. **Continuidad por la derecha**: $$F_X(x)$$ es continua por la derecha en cada punto. Esto significa que $$\lim_{x \to x_0^+} F_X(x) = F_X(x_0)$$.
4. **Saltos en los valores de discontinuidad**: Los puntos donde $$F_X(x)$$ tiene saltos corresponden a los valores de $$x$$ donde la variable aleatoria $$X$$ puede tomar valores discretos con probabilidad positiva.

### Tipos de Variables Aleatorias y sus CDFs

- **Variables Discretas**: Para variables aleatorias discretas, la CDF es una función escalonada que aumenta en puntos donde la variable aleatoria tiene masa de probabilidad.
- **Variables Continuas**: Para variables continuas, la CDF es una función suave y continua. La derivada de la CDF, cuando existe, es la función de densidad de probabilidad (PDF).
- **Variables Mixtas**: Algunas variables aleatorias tienen componentes tanto continuos como discretos, lo que resulta en una CDF que es en parte suave y en parte escalonada.

### Ejemplo Práctico

Supongamos que tienes una variable aleatoria $$X$$ que sigue una distribución uniforme en el intervalo $$[0,1]$$. La CDF de $$X$$ es:
$$
F_X(x) = 
\begin{cases} 
0 & \text{si } x < 0 \\
x & \text{si } 0 \leq x \leq 1 \\
1 & \text{si } x > 1 
\end{cases}
$$
Este ejemplo muestra cómo la CDF describe de manera efectiva la distribución de $$X$$, indicando que cualquier valor dentro del intervalo [0,1] es igualmente probable.

En resumen, l**a función de distribución acumulativa es una herramienta esencial en probabilidad y estadística para entender cómo se distribuyen los valores de una variable aleatoria a lo largo del espectro de posibles valores**.

La animación del enlace muestra la relación entre la `función de masa de probabilidad` y la `función de distribución acumulativa`. El gráfico superior es el PMF, mientras que el gráfico inferior es el CDF correspondiente. Al observar la gráfica de una CDF, cada valor del eje y es la suma de las probabilidades menores o iguales que él en la PMF.

[Enlace a la animacion](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/cdf-vs-pmf/animated.html)

Podemos usar una función de distribución acumulativa para calcular la probabilidad de un rango específico tomando la diferencia entre dos valores de la función de distribución acumulativa. Por ejemplo, para encontrar la probabilidad de observar entre 3 y 6 caras, podemos tomar la probabilidad de observar 6 o menos cabezas y restar la probabilidad de observar 2 o menos caras. Esto deja un remanente de entre 3 y 6 cabezas.

La imagen de la derecha demuestra cómo funciona esto. Es importante tener en cuenta que para incluir el límite inferior en el rango, el valor que se resta debe ser uno menos que el límite inferior. En este ejemplo, queríamos saber la probabilidad de 3 a 6, que incluye 3. 

[Enlace a la animacion](https://static-assets.codecademy.com/skillpaths/master-stats-ii/probability-distributions/cdf-animation/animation.html)

### Usando la función de distribución acumulativa en Python

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

## Random Variables in Real Datasets

Para explorar cómo se utilizan las variables aleatorias en conjuntos de datos reales, se puede utilizar Python junto con bibliotecas como `Pandas` y `Seaborn` para cargar y analizar datos. Por ejemplo, el conjunto de datos de Iris es frecuentemente usado para este tipo de análisis:

```python
import pandas as pd
import seaborn as sns

# Cargar el conjunto de datos de Iris
iris = sns.load_dataset('iris')

# Mostrar las primeras cinco filas del conjunto de datos
print(iris.head())

# Explorar las categorías únicas de la variable 'species'
print(iris['species'].unique())
```

Este código carga el conjunto de datos de Iris, que incluye medidas como la longitud y el ancho del sépalo y del pétalo de diferentes especies de iris. Cada una de estas medidas se puede considerar como una variable aleatoria, donde los valores que toman son resultados de procesos aleatorios bajo condiciones controladas.

#### Tareas de Aprendizaje Automático
En el contexto del aprendizaje automático, las tareas comúnmente asociadas con variables aleatorias incluyen clasificación y regresión:
- **Clasificación:** Determinar a qué categoría (especies en el caso de Iris) pertenece una observación basada en sus características.
- **Regresión:** Predecir un valor continuo basado en otras variables (por ejemplo, predecir el largo del pétalo basado en otras medidas).

Estas tareas utilizan las propiedades de las variables aleatorias para entrenar modelos que puedan generalizar bien a partir de datos nuevos.

### Modelado de Variables Aleatorias en Python

Para modelar variables aleatorias y sus distribuciones en Python, se utilizan técnicas estadísticas y de aprendizaje automático para ajustar modelos a los datos. Esto puede implicar calcular la función de masa de probabilidad para variables discretas o la función de densidad de probabilidad para variables continuas.

#### Visualización y Análisis
Utilizar visualizaciones como histogramas o gráficos de dispersión ayuda a entender la distribución y la relación entre variables aleatorias. Por ejemplo:

```python
sns.pairplot(iris, hue='species')
plt.show()
```

Este gráfico muestra las relaciones entre todas las medidas en el conjunto de datos de Iris, coloreadas por especie, proporcionando una intuición visual de cómo las variables aleatorias se relacionan entre sí y cómo podrían influir en la clasificación de las especies.

Comprender cómo las variables aleatorias se aplican a datos reales permite a los científicos de datos y a los profesionales del aprendizaje automático construir modelos más precisos y efectivos. La teoría detrás de las variables aleatorias es fundamental, pero su aplicación práctica a través de herramientas como Python facilita la exploración y el modelado efectivo de datos complejos en situaciones del mundo real.

