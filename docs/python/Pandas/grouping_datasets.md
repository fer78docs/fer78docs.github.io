---
layout: default
title: Grouping Datasets
nav_order: 3
parent: Pandas
grand_parent: Python
---

# Agrupación de conjuntos de datos

Durante el análisis de datos, a menudo es esencial agrupar o agrupar datos según ciertos criterios. Por ejemplo, una tienda de comercio electrónico podría querer agrupar todas las ventas que se realizaron durante el período navideño o los pedidos que se recibieron el Black Friday. Estos conceptos de agrupación ocurren en varias partes del análisis de datos. En este capítulo, cubriremos los fundamentos de las técnicas de agrupación y cómo hacerlo puede mejorar el análisis de datos. 

## Entendiendo groupby()

Durante la fase de análisis de datos, suele ser esencial categorizar un conjunto de datos en múltiples categorías o grupos. Podemos hacer dicha categorización usando la biblioteca pandas. La función groupby es una de las funciones más eficientes y que ahorra tiempo para hacer esto. Proporciona funcionalidades que nos permiten dividir, aplicar y combinar en todo el marco de datos; es decir, esta función se puede utilizar para dividir, aplicar y combinar marcos de datos.

De manera similar al lenguaje de consulta estructurado ( SQL ), podemos usar pandas y Python para ejecutar operaciones de grupo más complejas.

### Mecánica grupal

Mientras trabajamos con los marcos de datos en pandas, nuestro análisis puede requerir que dividamos nuestros datos según ciertos criterios. Los mecánismos de Groupby acumulan nuestro conjunto de datos en varias clases en las que podemos realizar ejercicios y realizar cambios, como los siguientes:

- Agrupar por características, jerárquicamente
- Agregar un conjunto de datos por grupos
- Aplicar funciones de agregación personalizadas a grupos
- Transformar un conjunto de datos en grupo

El método groupby realiza dos funciones esenciales:

- Divide los datos en grupos según algunos criterios.
- Aplica una función a cada grupo de forma independiente.

Para trabajar con las funcionalidades de groupby, necesitamos un conjunto de datos que tenga múltiples registros numéricos y categóricos para que podamos agruparlos por diferentes categorías y rangos.

Podemos agrupar el dataframe por la columna `body-style`, primero conocer los valores de la variable:

```python
# Group the dataset by the column body-style
style = df.groupby('body-style')

# Get values items from group with value convertible 
style.get_group("convertible")
```
Esto nos devuelve una tabla con los valores de los automobiles 


## Tablas dinámicas y tabulaciones cruzadas
Pandas ofrece varias opciones para agrupar y resumir datos. Ya hemos hablado de groupby, agregación y transformación, pero hay otras opciones disponibles, como `pivot_table` y `crosstab`. Primero, comprendamos las tablas dinámicas.

### Tablas dinamicas
La función pandas.pivot_table()función crea una tabla dinámica estilo hoja de cálculo como marco de datos. Los niveles de la tabla dinámica se almacenarán en objetos MultiIndex (índices jerárquicos) en el índice y las columnas del marco de datos resultante.

Las tablas dinámicas más simples deben tener un marco de datos y un índice/lista del índice. 

Hagamos una tabla dinámica de un nuevo marco de datos que consta de body-style las columnas ,,,,,, y :drive-wheels length width height curb-weight price

```python
new_dataset1 = df.filter(["body-style","drive-wheels",
                          "length","width","height","curb-weight","price"],axis=1)
#simplest pivot table with dataframe df and index body-style
table = pd.pivot_table(new_dataset1, index =["body-style"]) 
table
```

El resultado es una tabla dinámica agrupada por body-styley drive-wheels. Contiene el promedio de los valores numéricos de las columnas correspondientes.

La sintaxis de la tabla dinámica toma algunos argumentos, como c, valores, índice, columna y función de agregación. Podemos aplicar la función de agregación a una tabla dinámica al mismo tiempo. Podemos pasar la función de agregación, los valores y las columnas a las que se aplicará la agregación para crear una tabla dinámica de un subconjunto resumido de un marco de datos:

```python
# import numpy for aggregation function
import numpy as np

# new data set with few columns
new_dataset3 = df.filter(["body-style","drive-wheels","price"],axis=1)

table = pd.pivot_table(new_dataset3, values='price', index=["body-style"],
                       columns=["drive-wheels"],aggfunc=np.mean,fill_value=0)
table
```
En términos de sintaxis, el código anterior representa lo siguiente:

- Una tabla dinámica con un conjunto de datos llamado `new_dataset3`.
- Los valores son las columnas a las que se aplicará la función de agregación.
- El índice es una columna para agrupar datos.
- Columnas para especificar la categoría de datos.
- `aggfunc` es la función de agregación que se aplicará.
- `fill_valuese` utiliza para completar los valores faltantes.

También podemos aplicar una función de agregación diferente a diferentes columnas:
```python
table = pd.pivot_table(new_dataset1, values=['price','height','width'],
                       index =["body-style","drive-wheels"],
                       aggfunc={'price': np.mean,'height': [min, max],'width': [min, max]},
                       fill_value=0)
table
```

### Tabulaciones cruzadas
Podemos personalizar el pandas marco de datos con otra técnica llamada tabulación cruzada . Esto nos permite hacer frente groupbyy agregar para un mejor análisis de datos. pandas tiene la función, que ayuda a la hora de crear una tabla de tabulación cruzada. La tabla de tabulación cruzada muestra la frecuencia con la que aparecen ciertos grupos de datos. Vamos a ver: crosstab

Vamos pd.crosstab() a ver cuántos estilos de carrocería diferentes fabrican los diferentes fabricantes:

```python
pd.crosstab(df["make"], df["body-style"])
```

Apliquemos márgenes y el margins_nameatributo para mostrar la suma por filas y columnas de las tablas cruzadas, como se muestra en el siguiente código:

```python
# apply margins and margins_name attribute to displays the row wise 
# and column wise sum of the cross table
pd.crosstab(df["make"], df["body-style"],margins=True,margins_name="Total Made")
```

