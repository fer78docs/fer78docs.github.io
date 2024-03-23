---
layout: default
title: Choise the Best Graphics
nav_order: 3
parent: Exploratory Data Analysis
---

Elegir el mejor gráfico
No existe un estándar que defina qué gráfico debe elegir para visualizar sus datos. Sin embargo, existen algunas pautas que pueden ayudarte. Éstos son algunos de ellos:

Como se mencionó con cada uno de los cuadros anteriores que hemos visto, es importante comprender qué tipo de datos tiene. Si tiene variables continuas, un histograma sería una buena opción. De manera similar, si desea mostrar la clasificación, un gráfico de barras ordenado sería una buena opción.
Elija el gráfico que transmita efectivamente el significado correcto y relevante de los datos sin distorsionar los hechos.
La simplicidad es lo mejor. Se considera mejor dibujar un gráfico simple y comprensible que dibujar gráficos sofisticados que requieren varios informes y textos para comprenderlos.
Elija un diagrama que no sobrecargue a la audiencia con información. Nuestro propósito debe ser ilustrar la información abstracta de una manera clara.
Dicho esto, veamos si podemos generalizar algunas categorías de gráficos según diversos propósitos.

Tipos de gráficos según los propósitos:

- **Correlacion:** 
    - Scatter plot
    - Correlogram
    - Pairwise plot
    - Jittering with strip plot
    - Counts plot
    - Marginal histogram
    - Scatter plot with a line of best fit
    - Bubble plot with circling
- **Show deviation:**
    - Area chart
    - Diverging bars
    - Diverging texts
    - Diverging dot plot
    - Diverging lollipop plot with markers
- **Show distribution:**
    - Histogram for continuous variable
    - Histogram for categorical variable
    - Density plot
    - Categorical plots
    - Density curves with histogram
    - Population pyramid
    - Violin plot
    - Joy plot
    - Distributed dot plot 
    - Box plot
- **Show composition**
    - Waffle chart
    - Pie chart
    - Treemap
    - Bar chart
- **Show change**
    - Time series plot
    - Time series with peaks and troughs annotated
    - Autocorrelation plot
    - Cross-correlation plot
    - Multiple time series
    - Plotting with different scales using the secondary y axis
    - Stacked area chart
    - Seasonal plot
    - Calendar heat map
    - Area chart unstacked
- **show groups**
    - Dendrogram
    - Cluster plot
    - Andrews curve
    - Parallel coordinates
- **Show ranking**
    - Ordered bar chart
    - Lollipop chart
    - Dot plot
    - Slope plot
    - Dumbbell plot

Tenga en cuenta que analizar todos y cada uno de los tipos de trama mencionados en la tabla está fuera del alcance de este libro. Sin embargo, hemos intentado cubrir la mayoría de ellos en este capítulo. Algunos de ellos se utilizarán en los próximos capítulos; Usaremos estos gráficos de maneras más contextuales y con configuraciones avanzadas.

### Otras bibliotecas para explorar
Hasta ahora hemos visto diferentes tipos de técnicas de visualización 2D y 3D utilizando `matplotlib` y `seaborn`. Además de estas bibliotecas de Python ampliamente utilizadas, existen otras bibliotecas que puede explorar:

- **Ploty**( https://plot.ly/python/ ): este es un conjunto de herramientas de visualización basado en una aplicación web. Su API para Jupyter Notebook y otras aplicaciones lo hace muy poderoso para representar gráficos 2D y 3D.
- **Ggplot**( http://ggplot.yhathq.com/ ): Esta es una implementación de Python basada en la biblioteca Gramática de gráficos del lenguaje de programación R.
- **Altair**( https://altair-viz.github.io/ ): está construido sobre la poderosa gramática de visualización Vega-Lite y sigue técnicas de biblioteca de visualización estadística muy declarativas. Además de eso, tiene una API muy descriptiva y sencilla.

### Otras lecturas
- Matplotlib 3.0 Cookbook, Srinivasa Rao Poladi, Packt Publishing, October 22, 2018
- Matplotlib Plotting Cookbook, Alexandre Devert, Packt Publishing, March 26, 2014
- Data Visualization with Python, Mario Döbler, Tim Großmann, Packt Publishing, February 28, 2019
- No Humble Pie: The Origins and Usage of a Statistical Chart, Ian Spence, University of Toronto, 2005.