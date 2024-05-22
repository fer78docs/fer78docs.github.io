---
layout: default
title: Visualizing Categorical
nav_order: 2
parent: Data Visualization
---

# Visualizacion de datos categoricos

La visualización de datos categóricos implica principalmente el uso de gráficos circulares y gráficos de barras.

## Gráficos de barras

Los gráficos de barras se utilizan generalmente para visualizar las frecuencias relativas de categorías dentro de una variable. Por lo tanto, son principalmente útiles para resumir visualmente variables categóricas en lugar de variables cuantitativas. Si puede organizar su variable en categorías distintas, ¡un gráfico de barras suele ser una excelente opción! De lo contrario, es posible que deba recurrir a una imagen diferente.

Una vez que tenga sus distintas categorías, lo mejor es utilizar un gráfico de barras para mostrar los diferentes recuentos de valores de cada categoría. También podemos comparar medias, pero recomendamos usar un diagrama de caja de lado a lado porque brindan una imagen completa del resumen de cinco números .

Gráficos de barras verticales versus horizontales
Dentro de un gráfico de barras, tenemos dos ejes. Un eje representa los valores discretos dentro de una variable categórica que estamos comparando, mientras que el otro eje mide los recuentos de cada uno de estos valores. Dependiendo de cómo orientemos estos ejes, podemos tener un gráfico de barras horizontales o un gráfico de barras verticales . 

### Gráficos de barras versus histogramas 

Finalmente, tenemos una última cosa que repasar antes de comenzar a codificar nuestros propios gráficos. Si alguna vez se ha topado con histogramas, puede notar que los gráficos de barras y los histogramas parecen casi idénticos. Sin embargo, estas son las diferencias clave entre ellos:

Los gráficos de barras se utilizan para variables categóricas, mientras que los histogramas se utilizan para datos cuantitativos.
Los histogramas siempre deben organizarse en un orden específico porque representan un rango de valores numéricos. En un gráfico de barras, cada barra representa frecuencias de variables de categoría dentro de una categoría. A menos que la variable sea ordinal, las barras se pueden ordenar en cualquier orden.

![Line Graph](https://fer78docs.github.io/assets/images/graficos_categoricals.png)


[Simumacion](https://static-assets.codecademy.com/Paths/data-analyst-career-path/barcharts_piecharts_lesson/bar_gif_final/index.html)


## Área del gráfico de barras

Repasemos uno de los conceptos más importantes sobre los gráficos de barras; tan importante que le asignamos su propio ejercicio.

Las barras de un gráfico de barras tienen un par de características clave:

- Tienen longitudes que son proporcionales a los conteos que representan.
- El ancho de cada barra en el gráfico de barras es el mismo, lo que significa que el área de cada barra también es proporcional a los recuentos que representan.

Estas características hacen que un gráfico de barras sea muy confiable para representar datos categóricos.

Para cualquier gráfico como un gráfico de barras, las áreas que utilizamos para representar los valores siempre deben ser equivalentes a los tamaños relativos de los valores que representan. De lo contrario, los lectores podrían ser engañados y potencialmente identificar patrones que en realidad no existen.

## Trazado de gráficos de barras con Seaborn

Ahora que sabemos todo sobre los gráficos de barras, ¡creemos los nuestros propios en Python! Para ello, vamos a utilizar una biblioteca llamada seaborn . Crea imágenes potentes sin problemas de sintaxis y está construido a partir de la biblioteca Matplotlib .

Digamos que tenemos un conjunto de datos llamado flu.csv que indica si los pacientes dieron positivo o negativo en la prueba de gripe en una clínica durante la semana pasada. Los primeros cinco elementos de la columna Results se muestran a continuación.

Resultados
Positivo
Negativo
Negativo
Negativo
Positivo

Queremos crear un gráfico de barras que trace los recuentos de cada uno de los valores positive y negative dentro de la Results columna. Repasemos esto con la ayuda de la biblioteca pandas y la biblioteca seaborn con los siguientes pasos:

1) Importe las bibliotecas necesarias.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

2) Importe flu.csv usando el .read_csv()método. Puede inspeccionar las primeras cinco filas de datos con el .head()método en pandas.

```python
flu_results = pd.read_csv("flu.csv")
print(flu_results.head())
```

3) Trace los recuentos de la categoría deseada con el método .countplot() en seaborn. El único argumento requerido de este método es el xparámetro, que toma la columna de datos que estamos trazando. En nuestro caso, esta es la Resultscolumna.

```python
sns.countplot(flu_results["Results"])
```

4) Muestra la trama.

```python
plt.show()
```

Esto crea un gráfico de barras básico. Podemos personalizar nuestro gráfico .countplot(), que cubriremos más adelante en esta lección.

También queremos señalar que el método .countplot() no es el único método que crea gráficos de barras en la biblioteca seaborn. barplot()También se puede usar para trazar un gráfico de barras en Python y es más flexible porque puede usar cualquier función para determinar la altura de las barras. Para esta lección, hemos elegido usar .countplot()porque la sintaxis es más simple y hace lo que necesitamos.

### Orden de gráficos de barras

A menudo verá gráficos de barras con barras configuradas en un orden determinado. Esto puede ayudar a comunicar características significativas sobre sus datos. El hecho de que nuestras etiquetas de categoría sean ordinales o nominales afectará cómo queremos ordenar nuestras barras y qué características podemos enfatizar. Investiguemos.

### Datos nominales

Los datos nominales tienen etiquetas sin orden específico. Por lo tanto, tenemos mucha libertad creativa a la hora de elegir dónde va cada barra en nuestro gráfico. Una forma de ordenar nuestros datos es en orden ascendente o descendente. Apliquemos este orden a nuestros datos games.csv usando el .value_counts()método pandas en el orderparámetro.

```python
sns.countplot(df["victory_status"], order=df["victory_status"].value_counts(ascending=True).index)
```

Por la forma en que ordenamos los gráficos, queda inmediatamente claro cuál resignes el resultado del juego más común y el modo de nuestra victory_statuscolumna, mientras que drawes el menos común.

En el ejemplo anterior tenemos value_counts(ascending=True). Si queremos que las barras estén en orden inverso, podemos eliminarlas ascending=Truedel .value_counts()método (el orden descendente es el predeterminado). La indexllamada especifica las etiquetas de fila del DataFrame.

c