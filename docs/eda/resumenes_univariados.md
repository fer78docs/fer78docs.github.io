---
layout: default
title: Resumenes Univariados
nav_order: 1
parent: Exploratory Data Analysis
---

# Resumenes Univariados

Los resúmenes univariados se centran en la descripción y análisis de una sola variable a la vez. Este tipo de análisis es fundamental en estadística y análisis de datos, ya que proporciona una comprensión básica de las características y la distribución de los datos en una dimensión. Los resúmenes univariados son un paso inicial crucial en el análisis exploratorio de datos (EDA) para identificar patrones, tendencias, anomalías y posibles relaciones entre variables. A continuación, se detallan algunos de los conceptos y técnicas más importantes en los resúmenes univariados:

## Resumenes de Variables Cuantitativas 
### Medidas de Tendencia Central
* **Media (Promedio)**: Es la suma de todos los valores de la variable dividida por el número de observaciones. Proporciona el centro de gravedad de la distribución, pero es sensible a valores extremos (outliers).
* **Mediana:**Es el valor que divide al conjunto de datos en dos partes iguales cuando los datos están ordenados. La mediana es menos sensible a valores extremos y proporciona una mejor medida del centro para distribuciones sesgadas.
* **Media recortada:**  es una medida estadística de tendencia central que se asemeja a la media aritmética, pero con una diferencia clave: antes de calcular la media, se eliminan los valores extremos de ambos extremos de un conjunto de datos. El porcentaje exacto de datos a recortar depende del análisis, pero un enfoque común es eliminar el 5% de los valores más bajos y el 5% de los valores más altos.
* **Moda:** Es el valor o valores que aparecen con mayor frecuencia en el conjunto de datos. Es útil para datos categóricos y para identificar picos en distribuciones multimodales.

```python
print(f'Media: Rs.{df.column.mean().round()}')
print(f'Mediana: Rs.{df.column.median().round()}')
print(f'Moda: Rs.{df.column.mode().round()}')

# Calcular la media recortada
from scipy.stats import trim_mean
print(f'Media Recortada: Rs.{round(trim_mean(df.column, proportiontocut=0.1), 2)}')
```

### Medidas de Dispersión

* **Rango:** Es la diferencia entre el valor máximo y mínimo de la variable. Proporciona una idea de la amplitud de la distribución.
* **Desviación Estándar y Varianza:** Estas medidas indican cuánto tienden a dispersarse los valores alrededor de la media. La varianza es el promedio de las diferencias al cuadrado de la media, y la desviación estándar es la raíz cuadrada de la varianza.
* **Rango Intercuartílico (IQR):** Es la diferencia entre el tercer cuartil (Q3) y el primer cuartil (Q1). Ofrece una medida de la dispersión central y es menos sensible a outliers.
* **Desviación media absoluta (MAD):** el valor medio absoluto de la distancia entre cada punto de datos y la media.

```python
print(f'Max: Rs.{df.column.max()}')
print(f'Min: Rs.{df.column.min()}')
print(f'Rango: Rs.{df.column.max() - df.column.min()}')
print(f'Rango Intercuartil: Rs.{df.column.quantile(q=0.75) - df.column.quantile(q=0.25)}')
print(f'Varianza: Rs.{df.column.var().round(2)}')
print(f'Desviación Estándar: Rs.{df.column.std().round(2)}')
print(f'Desviación Media Absoluta: Rs.{(df.column - df.column.mean()).abs().mean().round(2)}')
```

### Forma de la Distribución
* **Sesgo (Skewness):** Mide la asimetría de la distribución. Una distribución con sesgo positivo tiene una cola más larga hacia la derecha, mientras que un sesgo negativo indica una cola más larga hacia la izquierda.
* **Curtosis:** Indica el grado de concentración de valores alrededor de la media, comparando la forma de la distribución con una distribución normal. Las distribuciones con alta curtosis tienen colas más pesadas y un pico más agudo.

### Visualización de variables cuantitativas
Si bien las estadísticas resumidas son ciertamente útiles para explorar y cuantificar una característica, puede que nos resulte difícil concentrarnos en un montón de números. Es por eso que la visualización de datos es un elemento tan poderoso de EDA.

Para variables cuantitativas, los diagramas de caja y los histogramas son dos visualizaciones comunes. Estos gráficos son útiles porque comunican simultáneamente información sobre los valores mínimos y máximos, la ubicación central y la dispersión. Los histogramas también pueden iluminar patrones que pueden afectar un análisis (por ejemplo, sesgo o multimodalidad).

La biblioteca de Python `seaborn`, construida sobre `matplotlib`, ofrece las funciones `boxplot()` y `histplot()` para trazar fácilmente datos desde un DataFrame de pandas:

* **Histogramas:** Permiten visualizar la distribución de frecuencias de una variable continua, identificando modas, asimetrías y la forma general de la distribución.
* **Diagramas de caja (Boxplots):** Ofrecen una representación visual de la mediana, los cuartiles y los valores atípicos, y son útiles para comparar distribuciones y detectar outliers.
* **Gráficos de barras:** Son útiles para datos categóricos, mostrando la frecuencia o proporción de cada categoría.

Los resúmenes univariados son esenciales para cualquier análisis de datos, ya que proporcionan los fundamentos para entender cada variable individualmente antes de explorar las relaciones entre múltiples variables.

## Variables categoricas

### Value Counts para Datos Categoricos
Cuando se trata de variables categóricas, las medidas de tendencia central y dispersión que funcionaron para describir variables numéricas, como la media y la desviación estándar, generalmente se vuelven inadecuadas cuando se trata de valores discretos. A diferencia de los números, los valores categóricos no son continuos y muchas veces no tienen un orden intrínseco.

En cambio, una buena manera de resumir las variables categóricas es generar una tabla de frecuencia que contenga el recuento de cada valor distinto. Por ejemplo, puede que nos interese saber cuántos de los listados de alquileres de la ciudad de Nueva York pertenecen a cada distrito. Relacionado, también podemos encontrar qué municipio tiene más listados.

Pandas ofrece el método `.value_counts()` para generar los recuentos de todos los valores en una columna de DataFrame:

### Proporciones de valor para datos categóricos

Una tabla de recuentos es un enfoque para explorar variables categóricas , pero a veces es útil observar también la proporción de valores en cada categoría. Por ejemplo, saber que hay 3.539 listados de alquileres en Manhattan es difícil de interpretar sin ningún contexto sobre los recuentos en las otras categorías. Por otro lado, saber que los listados de Manhattan representan el 71% de todos los listados de la ciudad de Nueva York nos dice mucho más sobre la frecuencia relativa de esta categoría.

Podemos calcular la proporción de cada categoría dividiendo su recuento por el número total de valores de esa variable:

```python
dataframe.column.value_counts() / len(dataframe.column)
```

### Visualización de variables categóricas
Para las variables categóricas , los gráficos de barras y los gráficos circulares son opciones comunes para visualizar el recuento (o proporción) de valores en cada categoría. También pueden transmitir las frecuencias relativas de cada categoría.

La biblioteca de Python seaborn ofrece varias funciones que pueden crear gráficos de barras. La forma más sencilla de trazar los recuentos es `countplot()`: