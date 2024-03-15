---
layout: default
title: Ayudas visuales para EDA
nav_order: 1
parent: Exploratory Data Analysis
---
# Ayudas visuales para EDA

Presentar resultados a las partes interesadas es muy complejo en el sentido de que nuestra audiencia puede no tener suficientes conocimientos técnicos para comprender la jerga de programación y otros tecnicismos. Por tanto, las ayudas visuales son herramientas muy útiles. En este capítulo, nos centraremos en diferentes tipos de ayudas visuales que se pueden utilizar con nuestros conjuntos de datos. 

- [Line chart (Gráfico de Líneas)](#line)
- [Bar chart (Gráfico de Barras)](#bar)
- Scatter plot (Gráfico de Dispersión)
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