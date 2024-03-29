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

Echemos un vistazo a un conjunto de datos de automóviles que enumera las diferentes características y atributos de los automóviles que podemos encontrar en https://www.kaggle.com/toramky/automobile-dataset. 

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 205 entries, 0 to 204
Data columns (total 26 columns):
 #   Column             Non-Null Count  Dtype  
---  ------             --------------  -----  
 0   symboling          205 non-null    int64  
 1   normalized-losses  205 non-null    object 
 2   make               205 non-null    object 
 3   fuel-type          205 non-null    object 
 4   aspiration         205 non-null    object 
 5   num-of-doors       205 non-null    object 
 6   body-style         205 non-null    object 
 7   drive-wheels       205 non-null    object 
 8   engine-location    205 non-null    object 
 9   wheel-base         205 non-null    float64
 10  length             205 non-null    float64
 11  width              205 non-null    float64
 12  height             205 non-null    float64
 13  curb-weight        205 non-null    int64  
 14  engine-type        205 non-null    object 
 15  num-of-cylinders   205 non-null    object 
 16  engine-size        205 non-null    int64  
 17  fuel-system        205 non-null    object 
 18  bore               205 non-null    object 
 19  stroke             205 non-null    object 
 20  compression-ratio  205 non-null    float64
 21  horsepower         205 non-null    object 
 22  peak-rpm           205 non-null    object 
 23  city-mpg           205 non-null    int64  
 24  highway-mpg        205 non-null    int64  
 25  price              205 non-null    object 
dtypes: float64(5), int64(5), object(16)
memory usage: 41.8+ KB
```

Podemos agrupar el dataframe por la columna `body-style`, primero conocer los valores de la variable:

```python
# Group the dataset by the column body-style
style = df.groupby('body-style')

# Get values items from group with value convertible 
style.get_group("convertible")
```
Esto nos devuelve una tabla con los valores de los automobiles 