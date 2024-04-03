---
layout: default
title: Summary Statistics
nav_order: 2
parent: Exploratory Data Analysis
---

# Summary Statistics

En el mundo del análisis de datos, trabajar con datos tabulares es una práctica común. Al analizar datos tabulares, a veces necesitamos obtener información rápida sobre los patrones y la distribución de los datos. Estos rápidos conocimientos suelen proporcionar la base para exploraciones y análisis adicionales. Nos referimos a estos conocimientos rápidos como estadísticas resumidas. Las estadísticas resumidas son muy útiles enproyectos de análisis de datos exploratorios porque nos ayudan a realizar una inspección rápida de los datos que estamos analizando.



## Analisis Univariado

Los resúmenes univariados se centran en la descripción y análisis de una sola variable a la vez. Este tipo de análisis es fundamental en estadística y análisis de datos, ya que proporciona una comprensión básica de las características y la distribución de los datos en una dimensión. Los resúmenes univariados son un paso inicial crucial en el análisis exploratorio de datos (EDA) para identificar patrones, tendencias, anomalías y posibles relaciones entre variables. A continuación, se detallan algunos de los conceptos y técnicas más importantes en los resúmenes univariados:

## Resumenes de Variables Cuantitativas 

### Medidas de Tendencia Central
La medida de tendencia central tiende a describir el valor promedio o medio de conjuntos de datos que se supone proporciona un resumen óptimo de todo el conjunto de mediciones. Este valor es un número que de alguna manera es central para el conjunto. Las medidas más comunes para analizar la frecuencia de distribución de los datos son la media, la mediana y la moda.

**Media (Promedio)**:   
Es la suma de todos los valores de la variable dividida por el número de observaciones. Proporciona el centro de gravedad de la distribución, pero es sensible a valores extremos (outliers).
```python
# Pandas
mean = df['column'].mean()
# Numpy
mean = np.mean(df['column'])
```

**Mediana:**  
Es el valor que divide al conjunto de datos en dos partes iguales cuando los datos están ordenados. La mediana es menos sensible a valores extremos y proporciona una mejor medida del centro para distribuciones sesgadas.

```python
# Pandas
median = df['column'].median()
# Numpy
median = np.median(df['column'])
```

**Media recortada:**  
Es una medida estadística de tendencia central que se asemeja a la media aritmética, pero con una diferencia clave: antes de calcular la media, se eliminan los valores extremos de ambos extremos de un conjunto de datos. El porcentaje exacto de datos a recortar depende del análisis, pero un enfoque común es eliminar el 5% de los valores más bajos y el 5% de los valores más altos.

```python
from scipy.stats import trim_mean
print(f'Media Recortada: Rs.{round(trim_mean(df.column, proportiontocut=0.1), 2)}')
```

**Moda:**  
Es el valor o valores que aparecen con mayor frecuencia en el conjunto de datos. Es útil para datos categóricos y para identificar picos en distribuciones multimodales.

```python
# Pandas
mode = df['column'].mode()
# Stats
from scipy import stats
node = stats.mode(df['column'])
```



### Medidas de Dispersión

El segundo tipo de estadística descriptiva es la medida de dispersión , también conocida como medida de variabilidad . Se utiliza para describir la variabilidad en un conjunto de datos, que puede ser una muestra o una población. Generalmente se utiliza junto con una medida de tendencia central para proporcionar una descripción general de un conjunto de datos. Una medida de dispersión/variabilidad/extensión nos da una idea de qué tan bien representa la tendencia central los datos. Si analizamos el conjunto de datos de cerca, a veces, la media/promedio puede no ser la mejor representación de los datos porque variará cuando haya grandes variaciones entre los datos. En tal caso, una medida de dispersión representará la variabilidad en un conjunto de datos con mucha más precisión.

Múltiples técnicas proporcionan medidas de dispersión en nuestro conjunto de datos. Algunos métodos comúnmente utilizados son la desviación estándar (o varianza), los valores mínimo y máximo de las variables, el rango, la curtosis y la asimetría

**Rango:** 
Es la diferencia entre el valor máximo y mínimo de la variable. Proporciona una idea de la amplitud de la distribución.

```python
# Pandas
max = df['column'].max()
min = df['column'].min()
# Numpy
max = np.max(df['column'])
min = np.min(df['column'])
# Para calcular el rango
range = max - min
```

**Varianza:**  
Estas medidas indican cuánto tienden a dispersarse los valores alrededor de la media. La varianza es el promedio de las diferencias al cuadrado de la media, y la desviación estándar es la raíz cuadrada de la varianza.

```python
# Pandas
median = df['column'].var()
# Numpy
median = np.var(df['column'])
```

**Desviación Estándar**  
La desviación estándar esse deriva de la varianza y es simplemente la raíz cuadrada de la varianza. La desviación estándar suele ser más intuitiva porque se expresa en las mismas unidades que el conjunto de datos.

```python
desv_est = np.std(df['column'])
```
El método `std` en pandastambién se puede utilizar para calcular la desviación estándar de un conjunto de datos.

* **Desviación media absoluta (MAD):** el valor medio absoluto de la distancia entre cada punto de datos y la media.

```python
print(f'Max: Rs.{df.column.max()}')
print(f'Min: Rs.{df.column.min()}')
print(f'Rango: Rs.{df.column.max() - df.column.min()}')

print(f'Varianza: Rs.{df.column.var().round(2)}')
print(f'Desviación Estándar: Rs.{df.column.std().round(2)}')
print(f'Desviación Media Absoluta: Rs.{(df.column - df.column.mean()).abs().mean().round(2)}')
```

### Oblicuidad

En teoría de la probabilidad y estadística, la asimetría es una medida de la asimetría de la variable en el conjunto de datos con respecto a su media. El valor de asimetría puede ser positivo, negativo o indefinido. El valor de asimetría nos dice si los datos son asimétricos o simétricos. A continuación se muestra una ilustración de un conjunto de datos con sesgo positivo, datos simétricos y algunos datos con sesgo negativo:

* **Sesgo (Skewness):** Mide la asimetría de la distribución. Una distribución con sesgo positivo tiene una cola más larga hacia la derecha, mientras que un sesgo negativo indica una cola más larga hacia la izquierda.

![Oblicuidad](https://fer78docs.github.io/assets/images/oblicuidad.webp)

Tenga en cuenta las siguientes observaciones del diagrama anterior:

- El gráfico del lado derecho tiene una cola que es más larga que la cola del lado derecho. Esto indica que la distribución de los datos está sesgada hacia la izquierda. Si selecciona cualquier punto en la cola más larga de la izquierda, la media es menor que la moda. Esta condición se conoce como asimetría negativa.

- El gráfico del lado izquierdo tiene una cola que es más larga en el lado derecho. Si selecciona cualquier punto en la cola derecha, el valor medio es mayor que la moda. Esta condición se conoce como asimetría positiva.

- El gráfico del medio tiene una cola derecha que es igual que la cola izquierda. Esta condición se conoce como condición simétrica.

Diferentes bibliotecas de Python tienen funciones para obtener la asimetría del conjunto de datos. La biblioteca `SciPy` tiene la función `scipy.stats.skew(dataset)`. Usando la biblioteca `pandas` , podemos calcular la asimetría en nuestro marco de datos usando la función 
```python
df.skew()
```
Además, también podemos calcular la asimetría a nivel de columna. Por ejemplo, la inclinación de la altura de la columna se puede calcular utilizando el método . función.df.loc[:,"height"].skew()

### Curtosis:

La curtosis es una medida estadística que ilustra en qué medida las colas de la distribución difieren de las de una distribución normal. Esta técnica puede identificar si una distribución determinada contiene valores extremos.

Pero espera, ¿no es eso similar a lo que hacemos con la asimetría? No precisamente. La asimetría normalmente mide la simetría de la distribución dada. Por otro lado, la curtosis mide el peso de las colas de distribución.

La curtosis, a diferencia de la asimetría, no se trata de picos o planitud. Es la medida de la presencia de valores atípicos en una distribución determinada. Tanto la curtosis alta como la baja son un indicador de que los datos necesitan más investigación. Cuanto mayor es la curtosis, mayores son los valores atípicos.

#### Tipos de curtosis
Hay tres tipos de curtosis: mesocúrtica, leptocúrtica y platicúrtica. Veamos estos uno por uno:

- `Mesocúrtico` : si algún conjunto de datos sigue una distribución normal, sigue una distribución mesocúrtica. Tiene curtosis alrededor de 0.

- `Leptocúrtico` : en este caso, la distribución tiene curtosis mayor que 3 y las colas gruesas indican que la distribución produce más valores atípicos.

- `Platicúrtica`: En este caso, la distribución tiene curtosis negativa y las colas son muy delgadas en comparación con la distribución normal.

Los tres tipos de curtosis se muestran en el siguiente diagrama:

![Tipos de Curtosis](https://fer78docs.github.io/assets/images/tipos_curtuosis.webp)

Diferentes bibliotecas de Python tienen funciones para obtener la curtosis del conjunto de datos. La biblioteca `SciPy` tiene la función `scipy.stats.kurtosis(dataset)` . Usando la biblioteca pandas , calculamos la curtosis de nuestro marco de datos usando la función:
```python
# Kurtosis of data in data using skew() function
kurtosis =df.kurt()
print(kurtosis)

# Kurtosis of the specific column
sk_height=df.loc[:,"height"].kurt()
print(sk_height)
```

De manera similar, podemos calcular la curtosis de cualquier columna de datos en particular. Por ejemplo, podemos calcular la curtosis de la altura de la columna como df.loc[:,"height"].kurt().


### Calcular percentiles
Los percentiles miden el porcentaje de valores en cualquier conjunto de datos que se encuentran por debajo de un determinado valor. Para calcular percentiles, debemos asegurarnos de que nuestra lista esté ordenada. Un ejemplo sería si dijeras que el percentil 80 de los datos es 130: entonces, ¿qué significa eso? Bueno, simplemente significa que el 80% de los valores están por debajo de 130.
La formula es:

percentil de x = (numero de valores menores de x / total de numeros observados) * 100

Supongamos que tenemos los datos dados: 1, 2, 2, 3, 4, 5, 6, 7, 7, 8, 9, 10. Entonces el valor percentil de 4 = (4/12) * 100 = 33,33%. Esto simplemente significa que el 33,33% de los datos son menores que 4.

```python
# Pandas 0.5, 0.25, 0.75
percentil = df.quantile(0.5)
# Numpy - Calcular el percentil 50% 
percentil = np.percentile(df['column'], 50,)
```

**Comprobación de los cuartiles de un conjunto de datos**

El cuartil es como el percentil porque se puede utilizar para medir la dispersión e identificar el centro de unconjunto de datos. Los percentiles y cuartiles se llaman cuantiles. Mientras que el percentil divide el conjunto de datos en 100 porciones iguales, el cuartil divide el conjunto de datos en 4 porciones iguales. Normalmente, tres cuartiles dividirán su conjunto de datos en cuatro porciones iguales.

### Cuartiles

Dado un conjunto de datos ordenado en orden ascendente, los cuartiles son los valores que dividen el conjunto de datos dado en cuartos. Los cuartiles se refieren a los tres puntos de datos que dividen el conjunto de datos dado en cuatro partes iguales, de modo que cada división representa el 25% del conjunto de datos. En términos de percentiles, el percentil 25 se denomina primer cuartil (Q1), el percentil 50 se denomina segundo cuartil (Q2) y el percentil 75 se denomina tercer cuartil (Q3).

**Rango Intercuartílico (IQR):**   
Es la diferencia entre el tercer cuartil (Q3) y el primer cuartil (Q1). Ofrece una medida de la dispersión central y es menos sensible a outliers.

El IQR es una estadística muy útil, especialmente cuando necesitamos identificar dónde se encuentra el 50% central de los valores de un conjunto de datos. A diferencia del rango, que puede verse sesgado por números muy altos o bajos (valores atípicos), el IQR no se ve afectado por los valores atípicos ya que se centra en el medio 50. También es útil cuando necesitamos calcular valores atípicos en un conjunto de datos.

Según el cuartil, existe otra medida llamada rango intercuartil que también mide la variabilidad en el conjunto de datos. Se define de la siguiente manera:

IQR = Q3 - Q1

El IQR no se ve afectado por la presencia de valores atípicos. 


```python
column = df.column.sort_values()

# Pandas
Q1 = df.column.quantile(q=0.25)
Q1 = df.column.quantile(q=0.50)
Q1 = df.column.quantile(q=0.75)

# Numpy
Q1 = np.percentile(column, 25)
Q2 = np.percentile(column, 50)
Q3 = np.percentile(column, 75)

# rango intercuartilico
IQR = Q3 - Q1


from scipy import stats
IQR = stats.iqr(df['colum'])

```


#### Visualizar cuartiles

Si queremos trazar el diagrama de caja para un solo sujeto, podemos hacerlo usando la función `plt.boxplot()`

```python
plt.boxplot(serie, showmeans=True, whis = 99)
```
![Diagrama de Caja](https://fer78docs.github.io/assets/images/diagrama_caja.webp)

El diagrama anterior ilustra el hecho de que la caja va del cuartil superior al inferior (alrededor de 62 y 73), mientras que los bigotes (las barras que se extienden desde la caja) van hasta un mínimo de 56 y un máximo de 90. La línea roja es la mediana (alrededor de 67), mientras que el pequeño triángulo (color verde) es la media.

Ahora, agreguemos también diagramas de caja para otros temas. Podemos hacer esto fácilmente combinando todas las puntuaciones en una sola variable:

```python
box = plt.boxplot(scores, showmeans=True, whis=99)

plt.setp(box['boxes'][0], color='blue')
plt.setp(box['caps'][0], color='blue')
plt.setp(box['caps'][1], color='blue')
plt.setp(box['whiskers'][0], color='blue')
plt.setp(box['whiskers'][1], color='blue')

plt.setp(box['boxes'][1], color='red')
plt.setp(box['caps'][2], color='red')
plt.setp(box['caps'][3], color='red')
plt.setp(box['whiskers'][2], color='red')
plt.setp(box['whiskers'][3], color='red')

plt.ylim([20, 95]) 
plt.grid(True, axis='y') 
plt.title('Distribution of the scores in three subjects', fontsize=18) 
plt.ylabel('Total score in that subject') 
plt.xticks([1,2,3], ['Physics','Literature','Computer'])

plt.show()
```

![Diagrama de Caja](https://fer78docs.github.io/assets/images/digrama_varios_variables.webp)

Del gráfico se desprende que la puntuación mínima obtenida por los estudiantes rondaba el 32, mientras que la puntuación máxima obtenida era 90, que fue en la asignatura de informática.

### Agrupación de conjuntos de datos

Durante el análisis de datos, a menudo es esencial agrupar o agrupar datos según ciertos criterios. Por ejemplo, una tienda de comercio electrónico podría querer agrupar todas las ventas que se realizaron durante el período navideño o los pedidos que se recibieron el Black Friday. Estos conceptos de agrupación ocurren en varias partes del análisis de datos.

La funcion `goupby()` proporciona funcionalidades que nos permiten dividir, aplicar y combinar en todo el marco de datos.

#### Mecánica grupal

Mientras trabajamos con los pandasmarcos de datos, nuestro análisis puede requerir que dividamos nuestros datos según ciertos criterios. Los mecánicos de Groupby acumulan nuestro conjunto de datos en varias clases en las que podemos realizar ejercicios y realizar cambios, como los siguientes:

- Agrupar por características, jerárquicamente
- Agregar un conjunto de datos por grupos
- Aplicar funciones de agregación personalizadas a grupos
- Transformar un conjunto de datos en grupo

El método pandas groupby realiza dos funciones esenciales:

- Divide los datos en grupos según algunos criterios.
- Aplica una función a cada grupo de forma independiente.

```python
# Group the dataset by the column body-style
style = df.groupby('body-style')

# Get values items from group with value convertible 
style.get_group("convertible")

# formar grupos basados ​​en múltiples categorías
df.groupby(["body-style","drive-wheels"])
```

No solo podemos agrupar el conjunto de datos con criterios específicos, sino que también podemos realizar operaciones aritméticas directamente en todo el grupo al mismo tiempo e imprimir el resultado como una serie o marco de datos. Existen funciones como `max()`, `min()`, `mean()`, `first()` y `last()` que se pueden aplicar directamente al objeto GroupBy para obtener estadísticas resumidas para cada grupo.

```python
# max() will print the maximum entry of each group 
style['normalized-losses'].max()

# min() will print the minimum entry of each group 
style['normalized-losses'].min()

# calcular la media de todas las variables cuantitativas
style.mean()
```

Tenga en cuenta que podemos obtener el promedio de las variables de un dataframe agrupando solo por uno de los valores de una columna categorica, de la siguiente manera:

```python
# La varibale style tiene como valor el dataframe agrupado por body-style
style.get_group("convertible").mean()
```

También podemos aplicar `count()` a variables del dataframe agrupado:

```python
style['column'].count()
```

## Data agregation

La agregación es el proceso de implementar cualquier operación matemática en un conjunto de datos o un subconjunto del mismo. La agregación es una de las muchas técnicas de pandas que se utiliza para manipular los datos en el marco de datos para el análisis de datos.

La función `df.aggregate()` se utiliza para aplicar agregación en una o más columnas. Algunas de las agregaciones más utilizadas son las siguientes:

- `sum`: Devuelve la suma de los valores del eje solicitado
- `min`: Devuelve el mínimo de los valores para el eje solicitado
- `max`: Devuelve el máximo de los valores para el eje solicitado

Dado que la agregación solo funciona con columnas de tipo numérico, se debe agrupar por  columnas numéricas del conjunto de datos y les apliquemos algunas funciones de agregación:

```python
# filtrar el dataset agrupado por colummnas numericas
new_dataset = df.filter(["length","width","height","curb-weight","price"],axis=1)

# applying single aggregation for mean over the columns
new_dataset.agg("mean", axis="rows")

# encontrar la suma y el mínimo de todas las columnas a la vez  
new_dataset.agg(['sum', 'min']) 
```

El resultado es un marco de datos con filas que contienen el resultado de la agregación respectiva que se aplicó a las columnas. Para aplicar funciones de agregación en diferentes columnas, puede pasar un diccionario con una clave que contenga los nombres de las columnas y los valores que contengan la lista de funciones de agregación para cualquier columna específica:

```python
# find aggregation for these columns 
new_dataset.aggregate({"length":['sum', 'min'], 
              "width":['max', 'min'], 
              "height":['min', 'sum'], 
              "curb-weight":['sum']}) 
# if any specific aggregation is not applied on a column
# then it has NaN value corresponding to it
```

El resultado del código anterior es el siguiente:

|      | length   | width | height | curb-weight |
|------|----------|-------|--------|-------------|
| max  | NaN      | 1.0000| NaN    | NaN         |
| min  | 0.678039 | 0.8375| 47.8   | NaN         |
| sum  | 168.257568 | NaN | 10807.1| 513689.0    |

#### Operaciones grupales

Las operaciones más importantes implementadas por groupBy son agregar, filtrar, transformar y aplicar. Una forma eficaz de implementar funciones de agregación en el conjunto de datos es hacerlo después de agrupar las columnas requeridas. La función agregada devolverá un único valor agregado para cada grupo. Una vez creados estos grupos, podemos aplicar varias operaciones de agregación a esos datos agrupados.

```python
# Group the data frame df by body-style and drive-wheels and extract stats from each group
df.groupby(["body-style","drive-wheels"]).agg(
    {
         'height':min, # minimum height of car in each group
         'length': max, # maximum length of car in each group
         'price': 'mean', # average price of car in each group
        
    }
)
# Podemos crear un diccionario de agregación de funciones que queremos realizar en grupos y luego usarlo más tarde:
aggregations=(
    {
         'height':min, # minimum height of car in each group
         'length': max, # maximum length of car in each group
         'price': 'mean', # average price of car in each group
        
    }
)
# implementing aggregations in groups
df.groupby(
   ["body-style","drive-wheels"]
).agg(aggregations) 
```
`numpy` tambien tiene funciones de agregacion que podemos utilizar con `groupby`:

```python
import numpy as np

df.groupby(
   ["body-style","drive-wheels"])["price"].agg([np.sum, np.mean, np.std])
```



## Visualización de variables cuantitativas
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

Pandas ofrece el método `.value_counts()` para generar los recuentos de todos los valores en una columna de DataFrame. Tambien podemos ver los primeros 30 valores mas grandes usando la funcion `nlargest()`

### Proporciones de valor para datos categóricos

Una tabla de recuentos es un enfoque para explorar variables categóricas , pero a veces es útil observar también la proporción de valores en cada categoría. Por ejemplo, saber que hay 3.539 listados de alquileres en Manhattan es difícil de interpretar sin ningún contexto sobre los recuentos en las otras categorías. Por otro lado, saber que los listados de Manhattan representan el 71% de todos los listados de la ciudad de Nueva York nos dice mucho más sobre la frecuencia relativa de esta categoría.

Podemos calcular la proporción de cada categoría dividiendo su recuento por el número total de valores de esa variable:

```python
dataframe.column.value_counts() / len(dataframe.column)
```

### Visualización de variables categóricas
Para las variables categóricas , los gráficos de barras y los gráficos circulares son opciones comunes para visualizar el recuento (o proporción) de valores en cada categoría. También pueden transmitir las frecuencias relativas de cada categoría.

La biblioteca de Python seaborn ofrece varias funciones que pueden crear gráficos de barras. La forma más sencilla de trazar los recuentos es `countplot()`: