---
layout: default
title: Time Series Analysis
nav_order: 5
parent: Exploratory Data Analysis
---

# Analisis de Series Temporales

Los datos de series de tiempo incluyen marcas de tiempo y, a menudo, se generan mientras se monitorea el proceso industrial o se rastrea cualquier métrica comercial. Una secuencia ordenada de valores de marca de tiempo a intervalos igualmente espaciados se denomina serie de tiempo . El análisis de dichas series temporales se utiliza en muchas aplicaciones, como pronósticos de ventas, estudios de servicios públicos, análisis presupuestario, pronósticos económicos, estudios de inventario, etc. Existe una gran cantidad de métodos que se pueden utilizar para modelar y pronosticar series de tiempo.

## Comprender el conjunto de datos de series temporales

La pregunta más esencial sería: ¿qué entendemos por datos de series temporales? Por supuesto, hemos oído hablar de ello en varias ocasiones. ¿Quizás podamos definirlo? Seguro que podemos. Básicamente, una serie de tiempo es una colección de observaciones realizadas de forma secuencial en el tiempo. Tenga en cuenta que aquí hay dos frases clave importantes: **una colección de observaciones** y **secuencialmente en el tiempo**. Como es una serie, tiene que ser una colección de observaciones y, como trata con el tiempo, tiene que hacerlo de forma secuencial.

Tomemos un ejemplo de datos de series de tiempo:
![Serie temporal](https://fer78docs.github.io/assets/images/time_series.webp)

La captura de pantalla anterior ilustra la producción de energía solar (medida en gigavatios hora ( GWh )) durante los primeros seis meses de 2016. También muestra el consumo de electricidad tanto a diario como a semana.

## Fundamentos de la TSA
Para comprender el conjunto de datos de series temporales, generemos aleatoriamente un conjunto de datos normalizado:

Podemos utilizar numpy para generar conjuntos de datos aleatorios:
```python
zero_mean_series = np.random.normal(loc=0.0, scale=1., size=50)
```
Podemos realizar una suma acumulativa sobre la lista anterior: 
```python
random_walk = np.cumsum(zero_mean_series)
random_walk
```

### Serie temporal univariada
Cuando capturamos una secuencia de observaciones para la misma variable durante un período de tiempo particular, la serie se denomina **serie de tiempo univariada**. En general, en una serie temporal univariante, las observaciones se toman durante períodos de tiempo regulares, como el cambio de temperatura a lo largo del tiempo a lo largo de un día.

### Características de los datos de series temporales.
Cuando se trabaja con datos de series temporales, se pueden observar varias características únicas. En general, las series temporales tienden a presentar las siguientes características:

- Al observar datos de series temporales, es fundamental ver si hay alguna tendencia . Observar una tendencia significa que los valores de medición promedio parecen disminuir o aumentar con el tiempo.
- Los datos de series temporales pueden contener una cantidad notable de valores atípicos . Estos valores atípicos se pueden observar cuando se representan en un gráfico.
- Algunos datos de series temporales tienden a repetirse durante un determinado intervalo en algunos patrones. Nos referimos a estos patrones repetitivos como estacionalidad .
- A veces, hay un cambio desigual en los datos de las series temporales. Nos referimos a estos cambios desiguales como cambios abruptos . Observar cambios abruptos en las series temporales es esencial ya que revela fenómenos subyacentes esenciales.
- Algunas series tienden a seguir una variación constante a lo largo del tiempo. Por lo tanto, es esencial observar los datos de las series de tiempo y ver si los datos exhiben una variación constante a lo largo del tiempo.


## Trabajo con Series Temporales

Open Power System Data para comprender la TSA
Jupyter Noteboook:


### Convertir Date en el Indice del Dataframe: 
Cambiar el índice de tu DataFrame a la columna "Date" significa que utilizarás los valores de esta columna como índices de las filas en lugar de los índices numéricos predeterminados de Pandas. Esto es especialmente útil cuando estás trabajando con series temporales, ya que facilita el acceso y la manipulación de los datos basados en fechas específicas:

Como resultado de esta accion:

- **Acceso basado en fecha**: Puedes acceder a las filas utilizando valores de fecha directamente. Por ejemplo, `df.loc['2023-03-15']` te daría los datos para el 15 de marzo de 2023.
- **Operaciones de series temporales:** Facilita realizar operaciones específicas de series temporales, como re-muestreo (`resample`), interpolaciones y desplazamientos de tiempo (`shift`), entre otros.
- **Visualización:** Al hacer gráficos, Pandas automáticamente reconocerá que el índice es una serie temporal, lo cual puede hacer que la generación de gráficos de series de tiempo sea más directa y con etiquetas de fecha bien formateadas.

Puede hacerse con el codigo:
```python
df.set_index('Date', inplace=True)
```

### Indexación basada en el tiempo
La indexación basada en el tiempo es un método muy poderoso de la biblioteca pandas cuando se trata de datos de series de tiempo. Tener una indexación basada en el tiempo permite utilizar una cadena formateada para seleccionar datos.    
Vea el siguiente código, por ejemplo:
```python
# seleccionar datos de un año
df_power.loc['2015']
# Seleccionar datos de un mes
df_power.loc['2015-10']
# seleccionar datos de un dia
df_power.loc['2015-10-02']
# O una serie personalizada
df.loc['2017-01-01':'2017-02-15']
```

Tenga en cuenta que utilizamos el descriptor de acceso `loc` del marco de datos pandas. En el ejemplo anterior, utilizamos una fecha como cadena para seleccionar una fila. Podemos usar todo tipo de técnicas para acceder a filas tal como lo podemos hacer con un índice de marco de datos normal.

## Visualización de datos de series temporales con Python

Una introducción a la exploración y visualización de datos de series temporales con Python.

### Introducción

Los datos representados en un único punto en el tiempo se conocen como datos transversales. Como científico o analista de datos, a veces puede encontrarse con datos recopilados durante períodos de tiempo, conocidos como datos de series temporales .

Los datos de series temporales aparecen en el mundo real con bastante frecuencia. Por ejemplo, las lecturas meteorológicas, los precios de las acciones de las empresas y los datos de ventas son ejemplos de datos que se pueden rastrear a lo largo del tiempo. Por lo tanto, es importante que pueda explorar y visualizar datos con un componente de tiempo.

En este artículo, aprenderá cómo explorar datos de series temporales con Python usando lo siguiente:

- Gráficos de líneas
- Diagramas de caja
- Mapas de calor
- Gráficos de retraso
- Gráficos de autocorrelación

## Trama lineal

Un gráfico de líneas se utiliza comúnmente para visualizar datos de series de tiempo. En un gráfico de líneas, el tiempo suele estar en el eje x y los valores de observación están en el eje y. Mostremos un ejemplo de este gráfico utilizando un archivo CSV de datos de ventas de una pequeña empresa durante un período de cinco años.

```python
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns

# load in data
sales_data = pd.read_csv("sales_data.csv")

# peek at first few rows of data
sales_data.head()
```

Aquí están las primeras filas de los datos de ventas:

| fecha | ventas
— | — | — 0 | 2016-01-01 | 2000,0 1 | 2016-01-02 | 1700,0 2 | 2016-01-03 | 1800,0 3 | 2016-01-04 | 1400,0 4 | 2016-01-05 | 1500.0

Creemos un gráfico lineal de los datos, con la fecha en el eje x y las ventas en el eje y:

```python
# convert string to datetime64
sales_data["date"] = sales_data["date"].apply(pd.to_datetime)
sales_data.set_index("date", inplace=True)

# create line plot of sales data
plt.plot(sales_data["date"], sales_data["sales"])
plt.xlabel("Date")
plt.ylabel("Sales (USD)")
plt.show()
```
![Serie temporal](https://fer78docs.github.io/assets/images/lineplot.svg)

Observe cómo podemos ver la tendencia de los datos a lo largo del tiempo. Mirando el gráfico, parece que:

- Las ventas son estacionales, alcanzan su punto máximo al principio y al final de cada año y disminuyen a mediados de cada año.
- Las ventas no parecen mostrar signos de crecimiento con el tiempo. Este parece ser un negocio estancado.

## Diagrama de caja

Cuando se trabaja con datos de series temporales, los diagramas de caja pueden resultar útiles para ver la distribución de valores agrupados por intervalo de tiempo.

Por ejemplo, creemos un diagrama de caja para cada año de ventas y colóquelos de lado a lado para compararlos:

```python
# extract year from date column
sales_data["year"] = sales_data["date"].dt.year

# box plot grouped by year
sns.boxplot(data=sales_data, x="year", y="sales")
plt.show()
```

![Serie temporal](https://fer78docs.github.io/assets/images/boxplot.svg)

Para cada año de los datos de ventas, podemos ver fácilmente información útil, como la mediana de las ventas, las ventas más altas y más bajas, el rango intercuartílico de nuestros datos y cualquier valor atípico.

Las ventas medianas de cada año (representadas por la línea horizontal en cada cuadro) son bastante estables, lo que sugiere que las ventas no crecen con el tiempo.

### Mapa de calor

También podemos utilizar un mapa de calor para comparar observaciones entre intervalos de tiempo en datos de series de tiempo.

Por ejemplo, creemos un mapa de calor de densidad con el año en el eje y y el mes en el eje x. Esto se puede hacer invocando la función `heatmap()` de Seaborn:

```python
# calculate total sales for each month
sales = sales_data.groupby(["year", "month"]).sum()

# re-format the data for the heat-map
sales_month_year = sales.reset_index().pivot(index="year", columns="month", values="sales")

# create heatmap
sns.heatmap(sales_month_year, cbar_kws={"label": "Total Sales"})
plt.title("Sales Over Time")
plt.xlabel("Month")
plt.ylabel("Year")
plt.show()
```

![Serie temporal](https://fer78docs.github.io/assets/images/heatmap_mnth_year_sales.svg)

Recuerde que en un mapa de calor, a medida que el color se vuelve más brillante y pasa del violeta oscuro al amarillo, las ventas totales en la celda correspondiente son mayores.

Aquí vemos una vez más que las ventas son bastante consistentes año tras año y también muestran estacionalidad.

### Diagrama de dispersión retrasado

Podemos utilizar un diagrama de dispersión de retardo para explorar la relación entre una observación y el retardo de esa observación.

En una serie de tiempo, un desfase es una observación previa:

- La observación en un paso de tiempo anterior (el intervalo de tiempo más pequeño para el cual tenemos mediciones distintas) se llama retraso 1.
- La observación hace dos momentos se llama retardo 2, etc.

En el conjunto de datos de ventas, tenemos un valor de ventas diferente para cada día. Por lo tanto, el valor del retraso 1 para cualquier día en particular es igual a las ventas del día anterior. El valor del retraso 2 son las ventas de hace dos días, etc.

El módulo plotting  de la biblioteca pandas tiene una función incorporada lag_plot que traza la observación en el tiempo t en el eje x y la observación de retraso 1 (t+1) en el eje y:

```python
# import lag_plot function
from pandas.plotting import lag_plot

# lag scatter plot
lag_plot(sales_data)
plt.show()
```

![Serie temporal](https://fer78docs.github.io/assets/images/lagplot.svg)

¿Cómo podemos interpretar un diagrama de dispersión retrasado?

- Si los puntos se mueven desde la parte inferior izquierda hasta la parte superior derecha, esto indica una correlación positiva entre las observaciones y sus valores de retraso 1. Por ejemplo, las altas ventas de un día se asocian con las altas ventas del día anterior.
- Si los puntos se mueven desde la parte superior izquierda a la parte inferior derecha, esto indica una correlación negativa entre las observaciones y sus valores de retraso 1. Por ejemplo, las ventas elevadas en un día se asocian con ventas bajas el día anterior y viceversa.
- Si no hay una estructura identificable en el gráfico de retraso, esto indica que los datos son aleatorios y no hay asociación entre valores en puntos de tiempo consecutivos. Por ejemplo, las ventas de un día no proporcionan información sobre las ventas esperadas del día siguiente.

Explorar la relación entre una observación y un retraso de esa observación es útil para ayudarnos a determinar si un conjunto de datos es aleatorio.

Dado que los puntos en los datos de ventas se mueven a lo largo de una línea diagonal desde la parte inferior izquierda hasta la parte superior derecha, esto indica que nuestros datos no son aleatorios y existe una correlación positiva entre las observaciones y sus valores de retraso 1.

### Gráfico de autocorrelación

Se utiliza un gráfico de autocorrelación para mostrar si los elementos de una serie temporal están correlacionados positivamente, negativamente o son independientes entre sí.

Esto se puede trazar con lafunción `autocorrelation_plot()` del módulo `pandas.plotting`:

```python
# import autocorrelation function
from pandas.plotting import autocorrelation_plot

# autocorrelation plot
autocorrelation_plot(sales_data)
plt.show()
```

![Serie temporal](https://fer78docs.github.io/assets/images/autocorrelation.webp)

En el gráfico de autocorrelación anterior, el retraso está en el eje x y el valor de la autocorrelación, que oscila entre -1 y 1, está en el eje y. Un valor cercano a 0 indica una correlación débil, mientras que los valores más cercanos a -1 y 1 indican una correlación fuerte.

Observe cómo el gráfico de autocorrelación de los datos de ventas forma ondas que oscilan entre una fuerte correlación negativa y positiva. Estas ondas sugieren que nuestro conjunto de datos muestra estacionalidad.

Observe también cómo la autocorrelación disminuye con el tiempo. Esto indica que las ventas tienden a ser similares en días consecutivos, pero las ventas de hace tres años están menos asociadas con las ventas de hoy que las ventas de hace un año.

**Resumen:** 

En este artículo, recibió una breve introducción a la exploración y visualización de datos de series temporales utilizando:

- Gráficos de líneas
- Diagramas de caja
- Mapas de calor
- Gráficos de retraso
- Gráficos de autocorrelación

Como científico o analista de datos, a menudo trabajará con datos que cambian con el tiempo. En el futuro, ahora estará mejor equipado para explorar y visualizar datos con un componente de tiempo.

Ejemplo. 

[Notebook Time Series](https://fer78docs.github.io/docs/ejemplos/Analisis%20de%20Series%20Temporales%20Open%20PSystem/Series_temporales.html)


