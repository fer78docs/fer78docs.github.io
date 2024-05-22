---
layout: default
title: Visualizing Categorical
nav_order: 2
parent: Data Visualization
---

# Visualizacion de datos categoricos

La visualización de datos categóricos implica principalmente el uso de gráficos circulares y gráficos de barras.

## Gráficos de barras

Los gráficos de barras se utilizan generalmente para **visualizar las frecuencias relativas de categorías dentro de una variable**. Por lo tanto, son principalmente útiles para resumir visualmente variables categóricas en lugar de variables cuantitativas. Si puede organizar su variable en categorías distintas, ¡un gráfico de barras suele ser una excelente opción! De lo contrario, es posible que deba recurrir a una imagen diferente.

Una vez que tenga sus distintas categorías, lo mejor es utilizar un gráfico de barras para mostrar los diferentes recuentos de valores de cada categoría. También podemos comparar medias, pero recomendamos usar un diagrama de caja de lado a lado porque brindan una imagen completa del resumen de cinco números.

**Gráficos de barras verticales versus horizontales**

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

Ahora que sabemos todo sobre los gráficos de barras, ¡creemos los nuestros propios en Python! Para ello, vamos a utilizar una biblioteca llamada `seaborn` . Crea imágenes potentes sin problemas de sintaxis y está construido a partir de la biblioteca `Matplotlib` .

Digamos que tenemos un conjunto de datos llamado flu.csv que indica si los pacientes dieron positivo o negativo en la prueba de gripe en una clínica durante la semana pasada. Los primeros cinco elementos de la columna Results se muestran a continuación.

**Resultados**
Positivo
Negativo
Negativo
Negativo
Positivo

Queremos crear un gráfico de barras que trace los recuentos de cada uno de los valores positive y negative dentro de la Results columna. Repasemos esto con la ayuda de la biblioteca pandas y la biblioteca seaborn con los siguientes pasos:

```python
#importe las bibliotecas necesarias.
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# importe el df
flu_results = pd.read_csv("flu.csv")
print(flu_results.head())

# recuentos de la categoría deseada con el método .countplot() 
sns.countplot(flu_results["Results"])
plt.show()
```

Esto crea un gráfico de barras básico. Podemos personalizar nuestro gráfico .countplot(), que cubriremos más adelante en esta lección.

También queremos señalar que el método `.countplot()` no es el único método que crea gráficos de barras en la biblioteca seaborn `.barplot()` También se puede usar para trazar un gráfico de barras en Python y es más flexible porque puede usar cualquier función para determinar la altura de las barras. Para esta lección, hemos elegido usar .countplot() porque la sintaxis es más simple y hace lo que necesitamos.

### Orden de gráficos de barras

A menudo verá gráficos de barras con barras configuradas en un orden determinado. Esto puede ayudar a comunicar características significativas sobre sus datos. El hecho de que nuestras etiquetas de categoría sean ordinales o nominales afectará cómo queremos ordenar nuestras barras y qué características podemos enfatizar. Investiguemos.

### Datos nominales

Los datos nominales tienen etiquetas sin orden específico. Por lo tanto, tenemos mucha libertad creativa a la hora de elegir dónde va cada barra en nuestro gráfico. Una forma de ordenar nuestros datos es en orden ascendente o descendente. 

```python
sns.countplot(df["victory_status"], order=df["victory_status"].value_counts(ascending=True).index)
```

![Line Graph](https://fer78docs.github.io/assets/images/ordered_graph1.webp)

Por la forma en que ordenamos los gráficos, queda inmediatamente claro cuál resignes el resultado del juego más común y el modo de nuestra victory_statuscolumna, mientras que drawes el menos común.

En el ejemplo anterior tenemos `value_counts(ascending=True)`. Si queremos que las barras estén en orden inverso, podemos eliminar a`scending=True` .La llamada index especifica las etiquetas de fila del DataFrame.

### Datos ordinales

Si estamos trabajando con datos ordinales, debemos trazar los datos de acuerdo con nuestras variables categóricas. Por ejemplo, digamos que queremos trazar el número de estudiantes por nivel de grado en una universidad. Tenemos una tabla a continuación, que es una vista previa de los datos de un archivo Students.csv .

Nivel de grado
Segundo año
Segundo año
Primer año
Tercer año
Cuarto año

Podemos ordenar los valores categóricos como `First Year`, `Second Year`, `Third Year` y `Fourth Year` ya que son ordinales. Usando `.countplot()`, podemos ingresarlos como una lista en el orderparámetro.

```python
sns.countplot(df["Grade Level"], order=["First Year", "Second Year", "Third Year", "Fourth Year"])
```

![Line Graph](https://fer78docs.github.io/assets/images/student_data_2.webp)

De este gráfico, obtenemos conclusiones que no podríamos obtener simplemente mirando la columna de datos. Podemos ver que la universidad tuvo una afluencia de estudiantes para la clase de segundo año, al igual Second Yearque la moda (valor más observado) de la Grade Levelcolumna de datos. Todos los demás años tienen aproximadamente el mismo número de estudiantes. Ordenar las barras de acuerdo con los datos ordinales nos ayuda a ver estos patrones y hacer que nuestras imágenes sean informativas para los lectores.

### Gráficos circulares

Hasta ahora, en esta lección, hemos analizado los gráficos de barras como una forma de trazar datos categóricos. Sin embargo, los gráficos de barras no son la única opción. A menudo, se encontrará con gráficos circulares como una forma de mostrar datos categóricos. Mientras que los gráficos de barras se utilizan normalmente para visualizar una tabla de frecuencias, los gráficos circulares son una alternativa cuando se desea visualizar una tabla de proporciones.

Los gráficos circulares se componen de sectores que se combinan para formar un círculo completo. Cada porción representa una proporción y la suma de cada proporción (porción) suma 1 (o 100%).

Estos sectores están destinados a brindar a los espectadores un tamaño relativo de los datos, similar a cómo actúan las barras en un gráfico de barras. La longitud del arco (tamaño del ángulo del corte) de cada corte es proporcional a la cantidad que representa. Esto también significa que el área de cada rebanada también es proporcional a esta cantidad.

Antes de profundizar en los casos de uso de los gráficos circulares y cómo trazarlos, queremos abordar el hecho de que los gráficos circulares son los elementos visuales más problemáticos. Exploraremos por qué más adelante en esta lección. Siguen siendo una de las herramientas de visualización más utilizadas, por lo que aprender todo sobre ellas resultará vital como analista de datos.

La razón principal por la que uno usaría un gráfico circular es para representar una relación de parte a todo en sus datos. Si desea comparar tamaños relativos de sus datos y ver cómo todos ellos son parte de una suma mayor sin preocuparse menos por sus tamaños precisos, un gráfico circular puede ser una buena opción.

Echa un vistazo a la animación. Esto muestra los sectores del gráfico circular. Observe algunas cosas:

Tanto la longitud del arco como el área de cada sector son proporcionales al porcentaje del círculo que constituye.

- La suma de cada sector suma el 100 por ciento.
- Es fundamental que cualquier gráfico circular que vea o cree siga estas dos reglas.

[Grafico de pastel](https://static-assets.codecademy.com/Paths/data-analyst-career-path/barcharts_piecharts_lesson/pie_gif/index.html)


### Trazar gráficos circulares con Matplotlib

Creamos nuestro propio gráfico circular usando Matplotlib. La biblioteca Seaborn actualmente no tiene bibliotecas de gráficos circulares. Digamos que tenemos la siguiente tabla que representa la proporción de calificaciones que obtiene un estudiante en los exámenes durante su año escolar:

|Los grados|Dimensiones
|A	|.09
|B	|.28
|C	|.41
|D	|.18
|F	|.04

Para crear un gráfico circular en Matplotlib, seguimos algunos pasos (estos pueden variar según el formato de sus datos). Imaginemos que la tabla de valores está en un archivo csv llamado Student_grades.csv , por lo que podemos usar pandas para acceder a ellos.

```python
student_grades = pd.read_csv("student_grades.csv")

# cree dos variables: una que represente los tamaños de cuña y otra que represente las etiquetas que corresponden a cada cuña. 
wedge_sizes = student_grades["Proportions"]
grade_labels = student_grades["Grades"]

# Traza los tamaños y etiquetas de las cuñas. 
plt.pie(wedge_sizes, labels = grade_labels)

#Configure el gráfico circular para que sea un círculo perfecto.
plt.axis('equal')

# Ponle un título a la trama y muéstrala.
plt.title(“Student Grade Distribution”)
plt.show()
```

### Errores de los gráficos circulares

Hemos aprendido sobre gráficos circulares y sus casos de uso, así como también sobre cómo trazarlos en Python. Sin embargo, si bien los gráficos circulares se utilizan comúnmente en los medios y las revistas, pueden surgir varios problemas. Profundicemos en los casos de uso de los gráficos circulares y de barras para comprender mejor cuándo es mejor usar uno u otro.

**Comparación de tamaños de categorías**

Uno de los puntos principales de la visualización de datos es facilitar al lector la comparación de diferentes conjuntos de información. Los sectores de un gráfico circular son difíciles de comparar ya que el ojo humano tiene dificultades para comparar áreas. Veamos el siguiente ejemplo:

![Line Graph](https://fer78docs.github.io/assets/images/bad_pie_charts.webp)

Al observar cualquiera de estos gráficos circulares, le resultará difícil percibir los tamaños relativos de cada sector. Si nuestra audiencia necesita esta comprensión matizada de los datos, un gráfico de barras es mucho más eficaz. 

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import codecademylib3

pie_data = pd.read_csv("pie_data.csv")
graph_counts = pie_data["values"]
graph_labels = pie_data["labels"]

plt.subplot(1,2,1)
plt.pie(graph_counts, labels = graph_labels)
plt.axis('Equal')
plt.title("Tough to Compare")

plt.subplot(1,2,2)
sns.barplot(graph_labels, graph_counts)
plt.title("Easy to Compare")

plt.show()
```

### Mejorando su gráfico circular

Un lema de buena vida suele ser cuantos más trozos de pastel, mejor. Desafortunadamente, esto no es cierto con los gráficos circulares. Con demasiadas porciones, intentar descifrar lo visual se vuelve engorroso, a veces incluso más engorroso que leer datos de una tabla. Eche un vistazo al ejemplo siguiente. Hay veinte cuñas en el gráfico. Tratar de hacer coincidir cada pieza con su etiqueta es demasiado esfuerzo cuando se supone que una imagen debe simplificar la legibilidad para el espectador.

![Line Graph](https://fer78docs.github.io/assets/images/college_major.webp)

Cuando te encuentras en una situación como esta, tienes un par de opciones.

- Puede agregar sus porciones de pastel para crear menos y al mismo tiempo representar una historia informativa.
- Puede ver si un gráfico de barras representa más eficazmente la información. Los gráficos de barras no sufren tanto como los gráficos circulares cuando se trata de visualizar numerosas categorías. Esto se debe a que no están restringidos a un círculo, sino a numerosas barras.