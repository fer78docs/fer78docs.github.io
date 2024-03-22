---
layout: default
title: Ayudas visuales para EDA
nav_order: 2
parent: Exploratory Data Analysis
---
# Ayudas visuales para EDA

Presentar resultados a las partes interesadas es muy complejo en el sentido de que nuestra audiencia puede no tener suficientes conocimientos técnicos para comprender la jerga de programación y otros tecnicismos. Por tanto, las ayudas visuales son herramientas muy útiles. En este capítulo, nos centraremos en diferentes tipos de ayudas visuales que se pueden utilizar con nuestros conjuntos de datos. 

- [Line chart (Gráfico de Líneas)](#line)
- [Bar chart (Gráfico de Barras)](#bar)
- [Scatter plot (Gráfico de Dispersión)](#scatter)
- Area plot and stacked plot (Parcela de área y parcela apilada)
- Pie chart (Gráfico Circular)
- Table chart (Gráfico de Tabla)
- Polar chart (Gráfico de Radar o Polar)
- Histogram (Histograma)
- Lollipop chart (Gráfico de Piruletas)


### Line chart (Gráfico de Líneas)
{: #line}
Se utiliza un gráfico de líneas para ilustrar la relación entre dos o más variables continuas. Estas pueden ser por ejemplo fechas y precios. 

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10,5))
plt.plot(df['Fecha'], df['Precio'], marker='', color='blue', linewidth=2, label="Precio")
plt.title('Evolución del Precio a lo Largo del Tiempo')
plt.xlabel('Fecha')
plt.ylabel('Precio')
plt.legend()
plt.show()
```
![Line Chart](https://fer78docs.github.io/assets/images/line_chart.jpg)


### Bar chart (Gráfico de Barras) 
{: #bar}
Las barras se pueden dibujar horizontal o verticalmente para representar variables categóricas. se utilizan con frecuencia para distinguir objetos entre distintas colecciones con el fin de realizar un seguimiento de las variaciones a lo largo del tiempo.

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6)) # Cambia el tamaño según tus necesidades
plt.bar(months, values, color='blue') # Usa el color que prefieras

# Añadir valores en la parte superior de las barras
for i, value in enumerate(values):
    plt.text(i, value + 3, str(value), ha='center')

# Etiquetas y título
plt.xlabel('Month')
plt.ylabel('Value') # Reemplaza 'Value' con la variable correspondiente
plt.title('Monthly Values') # Reemplaza 'Monthly Values' con un título apropiado
plt.xticks(rotation=45) # Rota las etiquetas si es necesario
plt.tight_layout() # Ajusta automáticamente los parámetros de la subtrama

# Muestra el gráfico
plt.show()
```

![Bar Chart](https://fer78docs.github.io/assets/images/bar_chart.webp)


Para crear un grafico de barras horizontales se mantiene el codigo, exepto `plt.xticks` lo cambiamos por `plt.yticks()` y `plt.bar()` los cambiamos por `plt.barh()`.

![Bar Chart](https://fer78docs.github.io/assets/images/bar_chart_horizontal.webp)




### Scatter plot (Gráfico de Dispersión)
{: #scatter}

Los diagramas de dispersión también se denominan gráficos de dispersión, scatter graphs, scatter charts, scattergrams, and scatter diagrams. Utilizan un sistema de coordenadas cartesianas para mostrar valores de normalmente dos variables para un conjunto de datos.

¿Cuándo deberíamos utilizar un diagrama de dispersión? Los diagramas de dispersión se pueden construir en las dos situaciones siguientes:

- Cuando una variable continua depende de otra variable, que está bajo el control del observador.
- Cuando ambas variables continuas son independientes

Hay dos conceptos importantes: variable independiente y variable dependiente. En el modelado estadístico o el modelado matemático, los valores de las variables dependientes dependen de los valores de las variables independientes. La variable dependiente es la variable de resultado que se estudia. Las variables independientes también se denominan regresores. La conclusión aquí es que **los diagramas de dispersión se utilizan cuando necesitamos mostrar la relación entre dos variables y, por lo tanto, a veces se los denomina diagramas de correlación.** 

O eres un científico de datos experto o un estudiante principiante en informática, y sin duda te has encontrado antes con una forma de diagrama de dispersión. Estos gráficos son poderosas herramientas de visualización, a pesar de su simplicidad. Las razones principales son que tienen muchas opciones, poderes de representación y opciones de diseño, y son lo suficientemente flexibles como para representar un gráfico de manera atractiva.

Algunos ejemplos en los que los diagramas de dispersión son adecuados son los siguientes:

- Los estudios de investigación han establecido con éxito que la cantidad de horas de sueño que necesita una persona depende de su edad.
- El ingreso promedio de los adultos se basa en el número de años de educación.

```python
import seaborn as sns 
import matplotlib.pyplot as plt 
sns.set() 

# Un diagrama de dispersión normal 
plt.scatter(x=sleepDf["age"]/12., y=sleepDf["min_recommended"]) 
plt.scatter(x =sleepDf["edad"]/12., y=sleepDf['max_recommended']) 
plt.xlabel('Edad de la persona en años') 
plt.ylabel('Total de horas de sueño requeridas') 
plt.show()
```
![diagrama de dispersion](https://fer78docs.github.io/assets/images/diagrama_de_dispersion.webp)

