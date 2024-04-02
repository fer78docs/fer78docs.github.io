---
layout: default
title: General functions
nav_order: 2
parent: Pandas
grand_parent: Python
---


# General functions

## Manipuladores de Datos de nivel superior

- [**melt**: - Convierte columnas en filas para pasar de un formato de datos de ancho a uno largo.](#melt)
- [**pivot**: - Transforma los datos de un formato ancho a uno largo.](#pivot)
- [**pivot_table**:-  Crea tablas de estilo excel, que ajecutan funciones: mean, sum, etc.](#pivot_table)
- [**crosstab**: - Crea tablas que resumen la relación entre dos o más variables categóricas.](#crosstab)
- [**cut**: - Segmentar y ordenar valores en contenedores, pasar de una variable continua a una variable categórica.](#cut)
- [**qcut**: - Se utiliza para dividir datos en bins basados en categorias](#qcut)
- [**merge**: - Crea tablas que resumen la relación entre dos o más variables categóricas.](#merge)
- [**merge_ordered**: - Combinar DataFrames con un enfoque en el orden secuencial de las observaciones.](#merge_ordered)
- [**merge_asof**: - Realizar fusiones aproximadas o asimétricas, útil en datos temporales o cronológicos.](#merge_asof)
- [**concat**: - Concatenar o unir objetos pandas a lo largo de un eje particular, ya sean Series o DataFrames.](#concat)
- [**get_dummies**: - Crea tablas que resumen la relación entre dos o más variables categóricas.](#get_dummies)
- [**from_dummies**: - Invierte la operación realizada por get_dummies().](#from_dummies)
- [**factorize**: - Obtener una representación numérica asignando a cada categoría única un valor entero.](#factorize)
- [**unique**: - Devuelve valores únicos en orden de aparición (Esto NO ordena).Incluye valores de NA..](#unique)
- [**lreshape**: - Transformar datos de un formato ancho a un formato largo, fundiendo varias columnas en una.](#lreshape)
- [**wide_to_long**: - Transformar DataFrames de un formato ancho a un formato largo..](#wide_to_long)

## Detect missing values a nivel superior

- [**isna**](#isna)
- [**isnull**](#isnull)
- [**notna**](#notna)
- [**notnull**](#notnull)

## Manejo de datos numericos a nivel superior

- [**to_numeric** - Convertir a tipo numerico](#to_numeric)

## Manejo de nivel superior con datos de tipo datetime

- [**to_datetime** - Convierte el argumento en fecha y hora](#to_datetime)
- [**to_timedelta** - Convierte el argumento a timedelta](#to_timedelta)
- [**date_range** - Devuelve un DatetimeIndex de frecuencia fija.](#date_range)
- [**bdate_range** - Convierte el argumento en fecha y hora](#bdate_range)
- [**period_range** - Devuelve un PeriodIndex de frecuencia fija.](#period_range)
- [**timedelta_range** - Devuelve un PeriodIndex de frecuencia fija.](#timedelta_range)
- [**infer_freq** - Devuelve un PeriodIndex de frecuencia fija.](#infer_freq)

## Manejo de datos de intervalo en un nivel superior.

- [**interval_range** - Crear un IntervalIndex con una frecuencia fija.](#interval_range)

## Evaluacion a nivel superior.

- [**eval** - Crear un IntervalIndex con una frecuencia fija.](#eval)

## Datetime formats.

- [**tseries.api.guess_datetime_format** - Adivina el formato de fecha y hora de una cadena de fecha y hora determinada.](#tseries.api.guess_datetime_format)

## Hash.

- [**util.hash_array** - Dada una matriz 1d, devuelve una matriz de números enteros deterministas.](#util.hash_array)

- [**util.hash_pandas_object** - Devuelve un hash de datos del índice/serie/marco de datos.](#util.hash_pandas_object)

## Importando DataFrames desde otras bibliotecas .

- [**api.interchange.from_dataframe** - Cree un pd.DataFramedesde cualquier DataFrame que admita el protocolo de intercambio.](#api.interchange.from_dataframe)



## melt

Lo que hace melt es "despivotar" o "fundir" el DataFrame, **convirtiendo columnas en filas**, lo cual es útil para pasar de un formato de datos de ancho a uno largo. Esto puede ser especialmente valioso en la preparación de datos para análisis y visualización.



```python
melt(frame: DataFrame, # El DataFrame que se va a transformar.
    id_vars=None, # Columna(s) que se mantendrán como identificadores.
    value_vars=None, # Columna(s) del DataFrame que se "fundirán", si se omite se funden todas menos las de id_vars.
    var_name=None, # Nombre columna que se creará y que contendrá los nombres de las columnas que se han fundido.
    value_name: Hashable = "value", #  Nombre columna que se creará y que contendrá los valores de las columnas fundidas.
    col_level=None, # Si las columnas son un MultiIndex, este parámetro se usa para determinar el nivel que se "fundirá".
    ignore_index: bool = True, # True se ignora el índice original. False, se conserva el índice original.
```



**Ejemplos**

Aquí tienes un ejemplo más ilustrativo con un tipo de dato común en análisis de datos: mediciones a lo largo del tiempo. Supongamos que tienes un DataFrame que registra temperaturas diarias máximas y mínimas en diferentes ciudades:


```python
import pandas as pd
df = pd.DataFrame({
    'Ciudad': ['Ciudad A', 'Ciudad B', 'Ciudad C'],
    'Temp_Max_Dia_1': [32, 30, 35],
    'Temp_Min_Dia_1': [24, 22, 23],
    'Temp_Max_Dia_2': [31, 29, 34],
    'Temp_Min_Dia_2': [23, 21, 22]
})
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ciudad</th>
      <th>Temp_Max_Dia_1</th>
      <th>Temp_Min_Dia_1</th>
      <th>Temp_Max_Dia_2</th>
      <th>Temp_Min_Dia_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ciudad A</td>
      <td>32</td>
      <td>24</td>
      <td>31</td>
      <td>23</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ciudad B</td>
      <td>30</td>
      <td>22</td>
      <td>29</td>
      <td>21</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ciudad C</td>
      <td>35</td>
      <td>23</td>
      <td>34</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



Si deseas realizar un análisis o una visualización de las temperaturas máximas y mínimas a lo largo del tiempo para cada ciudad, un formato largo puede ser más conveniente. Usando **pd.melt** puedes transformar el dataframe.


```python
df_largo = pd.melt(df, id_vars=['Ciudad'], var_name='Medición', value_name='Temperatura')
```


```python
df_largo
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ciudad</th>
      <th>Medición</th>
      <th>Temperatura</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ciudad A</td>
      <td>Temp_Max_Dia_1</td>
      <td>32</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ciudad B</td>
      <td>Temp_Max_Dia_1</td>
      <td>30</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ciudad C</td>
      <td>Temp_Max_Dia_1</td>
      <td>35</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Ciudad A</td>
      <td>Temp_Min_Dia_1</td>
      <td>24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ciudad B</td>
      <td>Temp_Min_Dia_1</td>
      <td>22</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Ciudad C</td>
      <td>Temp_Min_Dia_1</td>
      <td>23</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Ciudad A</td>
      <td>Temp_Max_Dia_2</td>
      <td>31</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ciudad B</td>
      <td>Temp_Max_Dia_2</td>
      <td>29</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Ciudad C</td>
      <td>Temp_Max_Dia_2</td>
      <td>34</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Ciudad A</td>
      <td>Temp_Min_Dia_2</td>
      <td>23</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ciudad B</td>
      <td>Temp_Min_Dia_2</td>
      <td>21</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Ciudad C</td>
      <td>Temp_Min_Dia_2</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



En este formato, cada fila representa una única observación de temperatura (ya sea máxima o mínima) para un día específico en una ciudad específica. Este formato es más manejable para realizar análisis como series temporales, gráficos de líneas o box plots, donde se quiere comparar los cambios en las temperaturas a lo largo del tiempo o entre diferentes ciudades.

## pivot

[**Subir**](#Indice)

A diferencia de melt que transforma los datos de un formato ancho a uno largo, pivot hace lo contrario: **transforma los datos de un formato largo a uno ancho**, lo cual es útil para crear tablas pivote, organizar datos para visualizaciones, o simplemente para hacer que el conjunto de datos sea más legible.



```python
df.pivot(
        columns = 'column_name', # Columna(s) a usar para hacer el nuevo índice del DataFrame.
        index= 'column_name', # Columna(s) cuyos valores únicos se convertirán en columnas en el nuevo DataFrame.
        values= 'column_name' # Columna(s) cuyos valores llenarán las celdas del nuevo DataFrame.
)
```



**Ejemplo:**

Conectemonos con un dataset de visitas a una web de ShoeFly.com una tienda online de zapatos.


```python
df = pd.read_csv('C:/Users/Fernando/Documents/GitHub/analytics_specialist/DATA/csv/page_visit_shoefly.csv')
df['month'] = df['month'].apply(lambda x: x.split(' - ')[1])
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>email</th>
      <th>month</th>
      <th>utm_source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10043</td>
      <td>Louis</td>
      <td>Koch</td>
      <td>LouisKoch43@gmail.com</td>
      <td>March</td>
      <td>yahoo</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10150</td>
      <td>Bruce</td>
      <td>Webb</td>
      <td>BruceWebb44@outlook.com</td>
      <td>March</td>
      <td>twitter</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10155</td>
      <td>Nicholas</td>
      <td>Hoffman</td>
      <td>Nicholas.Hoffman@gmail.com</td>
      <td>February</td>
      <td>google</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10178</td>
      <td>William</td>
      <td>Key</td>
      <td>William.Key@outlook.com</td>
      <td>March</td>
      <td>yahoo</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10208</td>
      <td>Karen</td>
      <td>Bass</td>
      <td>KB4971@gmail.com</td>
      <td>February</td>
      <td>google</td>
    </tr>
  </tbody>
</table>
</div>



Para crear un informe hacemos una agrupacion que cuente la cantidad de visitas por mes y por source


```python
click_source_by_month = df.groupby(['utm_source', 'month']).id.count().reset_index()
```


```python
click_source_by_month
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>utm_source</th>
      <th>month</th>
      <th>id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>email</td>
      <td>February</td>
      <td>147</td>
    </tr>
    <tr>
      <th>1</th>
      <td>email</td>
      <td>January</td>
      <td>43</td>
    </tr>
    <tr>
      <th>2</th>
      <td>email</td>
      <td>March</td>
      <td>272</td>
    </tr>
    <tr>
      <th>3</th>
      <td>facebook</td>
      <td>February</td>
      <td>263</td>
    </tr>
    <tr>
      <th>4</th>
      <td>facebook</td>
      <td>January</td>
      <td>404</td>
    </tr>
    <tr>
      <th>5</th>
      <td>facebook</td>
      <td>March</td>
      <td>156</td>
    </tr>
    <tr>
      <th>6</th>
      <td>google</td>
      <td>February</td>
      <td>196</td>
    </tr>
    <tr>
      <th>7</th>
      <td>google</td>
      <td>January</td>
      <td>127</td>
    </tr>
    <tr>
      <th>8</th>
      <td>google</td>
      <td>March</td>
      <td>220</td>
    </tr>
    <tr>
      <th>9</th>
      <td>twitter</td>
      <td>February</td>
      <td>154</td>
    </tr>
    <tr>
      <th>10</th>
      <td>twitter</td>
      <td>January</td>
      <td>164</td>
    </tr>
    <tr>
      <th>11</th>
      <td>twitter</td>
      <td>March</td>
      <td>97</td>
    </tr>
    <tr>
      <th>12</th>
      <td>yahoo</td>
      <td>February</td>
      <td>240</td>
    </tr>
    <tr>
      <th>13</th>
      <td>yahoo</td>
      <td>January</td>
      <td>262</td>
    </tr>
    <tr>
      <th>14</th>
      <td>yahoo</td>
      <td>March</td>
      <td>255</td>
    </tr>
  </tbody>
</table>
</div>



Esto nos muestra los datos de forma que se hace dificil vizualizar todo el conjunto. Con pivot podemos reordenar las columnas a un formato que sea una columna con las fuentes de visita y las columnas de cada mes a lo ancho. Esto hara mucho mas facil la comprension y presentacion de los datos


```python
pivot_view = click_source_by_month.pivot(
    columns='month',
    index='utm_source',
    values='id').reset_index()
```


```python
pivot_view
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>month</th>
      <th>utm_source</th>
      <th>February</th>
      <th>January</th>
      <th>March</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>email</td>
      <td>147</td>
      <td>43</td>
      <td>272</td>
    </tr>
    <tr>
      <th>1</th>
      <td>facebook</td>
      <td>263</td>
      <td>404</td>
      <td>156</td>
    </tr>
    <tr>
      <th>2</th>
      <td>google</td>
      <td>196</td>
      <td>127</td>
      <td>220</td>
    </tr>
    <tr>
      <th>3</th>
      <td>twitter</td>
      <td>154</td>
      <td>164</td>
      <td>97</td>
    </tr>
    <tr>
      <th>4</th>
      <td>yahoo</td>
      <td>240</td>
      <td>262</td>
      <td>255</td>
    </tr>
  </tbody>
</table>
</div>



## pivot_table

[**Subir**](#Indice)

Devuelve una tabla estilo excel del dataframe. A diferencia de la función pivot que se usa principalmente para reorganizar datos, pivot_table se utiliza para resumir y analizar datos. Es especialmente útil para agrupar y resumir conjuntos de datos complejos.



```python
pd.pivot_table(
    DataFrame,
    values=None,# Columna(s) cuyos valores se quieren resumir.
    index=None, # Columna(s) para hacer el índice de la tabla pivote.
    columns=None, # Columna(s) para hacer las columnas de la tabla pivote.
    aggfunc="mean", # Función de agregación. Puede ser una función o una lista de funciones.
    fill_value=None, # Valor para reemplazar los valores faltantes en el resultado.
    margins=False, # Si es True, agrega filas/columnas de totales o medias al final.
    dropna=True, # Si es True, omite las columnas con todos los valores NaN.
    margins_name="All", # Nombre para la fila/columna de totales cuando margins=True.
    sort=True, # Especifica si el resultado debe ordenarse.
)
```



Ejemplos:


```python
ventas = pd.DataFrame({
    'Producto': ['Producto A', 'Producto B', 'Producto A', 'Producto B'],
    'Ciudad': ['Ciudad 1', 'Ciudad 1', 'Ciudad 2', 'Ciudad 2'],
    'Ventas': [100, 200, 150, 300]
})
```


```python
ventas
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Producto</th>
      <th>Ciudad</th>
      <th>Ventas</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Producto A</td>
      <td>Ciudad 1</td>
      <td>100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Producto B</td>
      <td>Ciudad 1</td>
      <td>200</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Producto A</td>
      <td>Ciudad 2</td>
      <td>150</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Producto B</td>
      <td>Ciudad 2</td>
      <td>300</td>
    </tr>
  </tbody>
</table>
</div>




```python
ventas_pivot_table = pd.pivot_table(ventas, values='Ventas', index='Producto', columns='Ciudad', aggfunc='sum')
```


```python
ventas_pivot_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Ciudad</th>
      <th>Ciudad 1</th>
      <th>Ciudad 2</th>
    </tr>
    <tr>
      <th>Producto</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Producto A</th>
      <td>100</td>
      <td>150</td>
    </tr>
    <tr>
      <th>Producto B</th>
      <td>200</td>
      <td>300</td>
    </tr>
  </tbody>
</table>
</div>



Podemos retomar este ejemplo:


```python
click_source_by_month
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>utm_source</th>
      <th>month</th>
      <th>id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>email</td>
      <td>February</td>
      <td>147</td>
    </tr>
    <tr>
      <th>1</th>
      <td>email</td>
      <td>January</td>
      <td>43</td>
    </tr>
    <tr>
      <th>2</th>
      <td>email</td>
      <td>March</td>
      <td>272</td>
    </tr>
    <tr>
      <th>3</th>
      <td>facebook</td>
      <td>February</td>
      <td>263</td>
    </tr>
    <tr>
      <th>4</th>
      <td>facebook</td>
      <td>January</td>
      <td>404</td>
    </tr>
    <tr>
      <th>5</th>
      <td>facebook</td>
      <td>March</td>
      <td>156</td>
    </tr>
    <tr>
      <th>6</th>
      <td>google</td>
      <td>February</td>
      <td>196</td>
    </tr>
    <tr>
      <th>7</th>
      <td>google</td>
      <td>January</td>
      <td>127</td>
    </tr>
    <tr>
      <th>8</th>
      <td>google</td>
      <td>March</td>
      <td>220</td>
    </tr>
    <tr>
      <th>9</th>
      <td>twitter</td>
      <td>February</td>
      <td>154</td>
    </tr>
    <tr>
      <th>10</th>
      <td>twitter</td>
      <td>January</td>
      <td>164</td>
    </tr>
    <tr>
      <th>11</th>
      <td>twitter</td>
      <td>March</td>
      <td>97</td>
    </tr>
    <tr>
      <th>12</th>
      <td>yahoo</td>
      <td>February</td>
      <td>240</td>
    </tr>
    <tr>
      <th>13</th>
      <td>yahoo</td>
      <td>January</td>
      <td>262</td>
    </tr>
    <tr>
      <th>14</th>
      <td>yahoo</td>
      <td>March</td>
      <td>255</td>
    </tr>
  </tbody>
</table>
</div>




```python
pivot_table_source = pd.pivot_table(click_source_by_month,
                                    values='id',
                                    index='utm_source',
                                    columns='month',
                                    aggfunc="sum",
                                    margins=True,
                                    margins_name='Trimestre',
                                   )
```


```python
pivot_table_source
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>month</th>
      <th>February</th>
      <th>January</th>
      <th>March</th>
      <th>Trimestre</th>
    </tr>
    <tr>
      <th>utm_source</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>email</th>
      <td>147</td>
      <td>43</td>
      <td>272</td>
      <td>462</td>
    </tr>
    <tr>
      <th>facebook</th>
      <td>263</td>
      <td>404</td>
      <td>156</td>
      <td>823</td>
    </tr>
    <tr>
      <th>google</th>
      <td>196</td>
      <td>127</td>
      <td>220</td>
      <td>543</td>
    </tr>
    <tr>
      <th>twitter</th>
      <td>154</td>
      <td>164</td>
      <td>97</td>
      <td>415</td>
    </tr>
    <tr>
      <th>yahoo</th>
      <td>240</td>
      <td>262</td>
      <td>255</td>
      <td>757</td>
    </tr>
    <tr>
      <th>Trimestre</th>
      <td>1000</td>
      <td>1000</td>
      <td>1000</td>
      <td>3000</td>
    </tr>
  </tbody>
</table>
</div>



## crosstab

[**Subir**](#Indice)

Crea tablas que resumen la relación entre dos o más variables categóricas. Es especialmente útil para análisis estadísticos y de datos exploratorios. De forma predeterminada, calcula una tabla de frecuencia de los factores a menos que se pase una matriz de valores y una función de agregación.


```python
pd.crosstab(
    index, # Valores para agrupar en las filas tipo matriz, serie o lista de matrices/serie.
    columns, # Valores para agrupar en las columnas tipo matriz, serie o lista de matrices/serie.
    values=None, # Matriz de valores para agregar según los factores. Requiere que se especifique aggfunc .
    rownames=None, # nombres de fila, si se aprueba, debe coincidir con el número de matrices de filas aprobadas.
    colnames=None,  # nombres de columnas, si se aprueba, debe coincidir con el número de matrices de filas aprobadas.
    aggfunc=None, # Si se especifica, también requiere que se especifiquen valores.
    margins: bool = False, # Si es True, agrega filas/columnas de totales al final.
    margins_name="All", # Nombre de la fila/columna que contendrá los totales cuando 'margins' es True.
    dropna=True, # No incluya columnas cuyas entradas sean todas NaN.
    normalize=False # Normalice dividiendo todos los valores por la suma de valores.'all' o True , se normalizará en
                    # todos los valores.='index', se normalizará en cada fila,='columns': en cada columna.
)
```

**Ejemplos**

Insurance es una dataset sobre datos del seguro medico en una ciudad. Podemos utilizat crosstab para explorar algunos datos.  


```python
insurance = pd.read_csv('C:/Users/Fernando/Documents/GitHub/analytics_specialist/DATA/csv/insurance.csv')
```


```python
insurance.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
    </tr>
  </tbody>
</table>
</div>




```python
insurrance_smoker_region = pd.crosstab(index = insurance['region'],columns = insurance['smoker'])
```


```python
insurrance_smoker_region
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>smoker</th>
      <th>no</th>
      <th>yes</th>
    </tr>
    <tr>
      <th>region</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>northeast</th>
      <td>257</td>
      <td>67</td>
    </tr>
    <tr>
      <th>northwest</th>
      <td>267</td>
      <td>58</td>
    </tr>
    <tr>
      <th>southeast</th>
      <td>273</td>
      <td>91</td>
    </tr>
    <tr>
      <th>southwest</th>
      <td>267</td>
      <td>58</td>
    </tr>
  </tbody>
</table>
</div>



## cut

[**Subir**](#Indice)

Segmentar y ordenar valores de datos en contenedores. **Esta función también es útil para pasar de una variable continua a una variable categórica**. Cuando **pd.cut** devuelve una serie de categorías, básicamente está clasificando tus datos en grupos con una distribución uniforme. Cada elemento de tus datos originales se asigna a una de estas categorías en función de su valor.


```python
pd.cut(
    x, # matriz unidimensional
    bins, # Los criterios por los que se debe agrupar. Ver debajo
    right=True, # Si True, el intervalo incluirá el límite derecho. Si False, no lo incluirá.
    labels=None, #  Lista de etiquetas para asignar a los bins. Si None, se usan etiquetas numéricas.
    retbins=False, # Si True, retorna los bins además de los valores asignados.
    precision=3, # Precisión al representar los límites de los bins.
    include_lowest=False, # Si True, el primer intervalo incluirá el valor más bajo.
    duplicates="raise"|"drop", # Si los bordes del contenedor no son únicos, raise:ValueError o elimine los no únicos.
    ordered=True, # Etiquetas ordenadas o no. Se aplica a los tipos devueltos Categórico y Serie (con tipo Categórico)
)
```

**Los criterios por los que se debe agrupar.**

- **int:** Un entero que define el número de contenedores de igual ancho en el rango de x . El rango de x se amplía en un 0,1% en cada lado para incluir los valores mínimo y máximo de x .

- **secuencia de escalares:** define los bordes del contenedor permitiendo un ancho no uniforme. No se realiza ninguna extensión del rango de x .

- **IntervalIndex:** define los contenedores exactos que se utilizarán. Tenga en cuenta que IntervalIndex para contenedores no debe superponerse.

**Ejemplos**

Serie de edades que queremos segmentar para representar. Las serie insurance.age tiene 1338 valores de edades de los miembros de este estudio de Costes de Seguro Medico, para hacer un histograma.

Definir los **bins** y las **etiquetas** de cada uno. Esto establecera los rangos de 0 a 18 con la etiqueta '<18' y asi susecivamente.


```python
bins = [18, 25, 35, 45, 55, 65,]
etiquetas = ['18-25', '26-35', '36-45', '46-55', '56-65']
```


```python
insurance['age_categories'] = pd.cut(insurance.age, bins=bins, labels=etiquetas, ordered=True, include_lowest=True)
```


```python
insurance.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>age_categories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>18-25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>18-25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>26-35</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>26-35</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>26-35</td>
    </tr>
  </tbody>
</table>
</div>



Podemos hacer el histograma


```python
import matplotlib.pyplot as plt
insurance['age_categories'].hist(bins=9, grid=False, color='blue')

# Personalizar el gráfico
plt.title('Histograma de Edades')
plt.xlabel('Categorias')
plt.ylabel('Frecuencia')
plt.xticks(rotation=45)
plt.show()
```


    
![png](output_81_0.png)
    


## qcut

[**Subir**](#Indice)

Se utiliza para dividir datos en bins basados en categorias de cuantiles. Cuando pd.qcut devuelve una serie de categorías (por ejemplo, 'Q1', 'Q2', 'Q3', 'Q4'), básicamente está clasificando tus datos en grupos con una distribución uniforme. Cada elemento de tus datos originales se asigna a una de estas categorías en función de su cuantil. Aquí hay varias maneras en que puedes utilizar esta información:


```python
pd.qcut(
    x, # matriz unidimensional
    q, # Número de cuantiles. 10 para deciles, 4 para cuartiles, etc.
    labels=None, # Lista de etiquetas para asignar a los bins. Si None, se usan etiquetas numéricas.
    retbins=False, # Si devolver los (contenedores, etiquetas) o no
    precision=3, # Precisión al representar los límites de los bins.
    duplicates="raise"|"drop", # Si los bordes del contenedor no son únicos, raise:ValueError o elimine los no únicos.
)
```

Ejemplos:
    
Continuamos con el dataset sobre Costes del Seguro Medico


```python
qs = pd.qcut(insurance.age, 4, labels=['Q1', 'Q2', 'Q3', 'Q4'])
```


```python
qs.hist(bins=7, grid=False, color='blue')

# Personalizar el gráfico
plt.title('Histograma de Edades')
plt.xlabel('Categorias')
plt.ylabel('Frecuencia')
plt.show()
```


    
![png](output_88_0.png)
    


## merge

[**Subir**](#Indice)

Combinar dos DataFrames basándose en una o más claves comunes de manera similar a las operaciones de unión (joins) en las bases de datos SQL. Es una herramienta poderosa para combinar conjuntos de datos relacionados de una manera eficiente y flexible.


```python
pd.merge(
    left:df|sr, # DataFrame o Serie a la izquierda de la fusión.
    right:df|sr, # DataFrame o Serie a la derecha de la fusión.
    how="inner", # Tipo de fusión a realizar. Puede ser 'left', 'right', 'outer', 'inner'.
    on=None, # Columna o Index de union. Predeterminado es la intersección de las columnas en ambos DataFrames.
    left_on= None, # Columna o indice, matriz o lista para unirse en el marco de datos izquierdo, solo si on=None
    right_on=None, # Columna o indice, matriz o lista para unirse en el marco de datos derecho, solo si on=None
    left_index=False, #  Si es True, usa el índice (filas) del DataFrame izquierdo/derecho como clave(s) de unión.
    right_index=False, #  Si es True, usa el índice (filas) del DataFrame izquierdo/derecho como clave(s) de unión.
    sort=False, Ordena los datos resultantes según las columnas de unión.
    suffixes: Suffixes=("_x", "_y"), # una cadena que indica el sufijo que se agregará a los nombres de columnas
                                    #superpuestas en la izquierda y la derecha
    copy=None, # Evite la copia si= False,
    indicator=False # Si es Verdadero, agrega una columna llamada "_merge" con información sobre el origen de cada fila.
    validate=None,  # comprueba si la combinación es del tipo especificado (1:1, 1:m, m:1, m:m).
```

**Tipos de Merge:**

- **inner**: Combina solo las filas que tienen claves coincidentes en ambos DataFrames.
- **outer**: Combina todas las filas de ambos DataFrames, llenando con NaN donde no hay coincidencias.
- **left**: Incluye todas las filas del DataFrame izquierdo y las filas coincidentes del derecho.
- **right**: Incluye todas las filas del DataFrame derecho y las filas coincidentes del izquierdo.

**Tipos de combinaciones**

- **one_to_one** o **1:1**: compruebe si las claves de combinación son únicas en los conjuntos de datos izquierdo y derecho.
- **one_to_many** o **1:m**: compruebe si las claves de combinación son únicas en el conjunto de datos izquierdo.
- **many_to_one** o **m:1**: compruebe si las claves de combinación son únicas en el conjunto de datos correcto.
- **many_to_many** o **m:m**: permitido, pero no genera comprobaciones.

**Ejemplo**

Los datos de un Ecommerce estan en varias ficheros csv correspondientes a varias tablas de la base de dato, con el fin de presentar datos utilizamos **merge**.


```python
path ='C:/Users/Fernando/Documents/GitHub/analytics_specialist/DATA/csv/'
```


```python
visits = pd.read_csv(path + 'page_funnel_visits_visits.csv')
```


```python
cart = pd.read_csv(path + 'page_funnel_visits_cart.csv')
```


```python
checkout = pd.read_csv(path + 'page_funnel_visits_checkout.csv')
```


```python
purchase = pd.read_csv(path + 'page_funnel_visits_purchase.csv')
```

Los dataframes corresponden a un funnel de visitas a una web, tenemos las paginas de visita, carrito de compras, checkout y compra. Con merge podemos crear una vizualizacion completa de funnel. Puesto que merge solo une dos dataframes a la vez lo hacemos en varios pasos.


```python
step_1 = pd.merge(visits, cart, on = 'user_id', how = 'left')
```


```python
step_2 = pd.merge(step_1, checkout, on = 'user_id', how = 'left')
```


```python
all_data = pd.merge(step_2, purchase, on = 'user_id', how = 'left')
```


```python
all_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>visit_time</th>
      <th>cart_time</th>
      <th>checkout_time</th>
      <th>purchase_time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>943647ef-3682-4750-a2e1-918ba6f16188</td>
      <td>2017-04-07 15:14:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0c3a3dd0-fb64-4eac-bf84-ba069ce409f2</td>
      <td>2017-01-26 14:24:00</td>
      <td>2017-01-26 14:44:00</td>
      <td>2017-01-26 14:54:00</td>
      <td>2017-01-26 15:08:00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6e0b2d60-4027-4d9a-babd-0e7d40859fb1</td>
      <td>2017-08-20 08:23:00</td>
      <td>2017-08-20 08:31:00</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6879527e-c5a6-4d14-b2da-50b85212b0ab</td>
      <td>2017-11-04 18:15:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>a84327ff-5daa-4ba1-b789-d5b4caf81e96</td>
      <td>2017-02-27 11:25:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



## merge_ordered

[**Subir**](#Indice)

Se utiliza para combinar DataFrames de manera similar a la función merge, pero con un enfoque específico en el orden secuencial de las observaciones, típicamente para datos temporales. Es especialmente útil cuando se trabaja con series de tiempo o datos que requieren ser combinados de manera ordenada.


```python
pd.merge_ordered(
    left:df|sr, # DataFrame o Serie a la izquierda de la fusión.
    right:df|sr, # DataFrame o Serie a la derecha de la fusión.
    how="outer", # Tipo de fusión a realizar. Puede ser 'left', 'right', 'outer', 'inner'.
    on=None, # Columna o Index de union. Predeterminado es la intersección de las columnas en ambos DataFrames.
    left_on= None, # Columna o indice, matriz o lista para unirse en el marco de datos izquierdo, solo si on=None
    right_on=None, # Columna o indice, matriz o lista para unirse en el marco de datos derecho, solo si on=None
    left_by=None, #  Columnas para realizar agrupaciones separadas antes de realizar la fusión.
    right_by=None, #  Columnas para realizar agrupaciones separadas antes de realizar la fusión.
    fill_method=None, # Método para rellenar huecos (None o 'ffill', por ejemplo).
    suffixes=("_x", "_y"), # una cadena que indica el sufijo que se agregará a los nombres de columnas
                           #superpuestas en la izquierda y la derecha
)
```

**Ejemplo**


```python
# DataFrames de ejemplo
df1 = pd.DataFrame({'date': pd.to_datetime(['2021-01-01', '2021-01-03', '2021-01-05']),
                    'value_df1': [10, 20, 30]})
df2 = pd.DataFrame({'date': pd.to_datetime(['2021-01-01', '2021-01-02', '2021-01-03']),
                    'value_df2': [40, 50, 60]})

# Uso de merge_ordered
merged_df = pd.merge_ordered(df1, df2, on='date', fill_method='ffill')
merged_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>value_df1</th>
      <th>value_df2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-01-01</td>
      <td>10</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-01-02</td>
      <td>10</td>
      <td>50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-01-03</td>
      <td>20</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-01-05</td>
      <td>30</td>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>



## merge_asof

[**Subir**](#Indice)

Realizar fusiones aproximadas o asimétricas, especialmente útil en datos temporales o cronológicos. Esta función es particularmente adecuada para situaciones donde deseas combinar dos DataFrames basados en una columna de tiempo o clave, pero los tiempos no coinciden exactamente.

**Características Principales:**

- **Fusión por Proximidad:** A diferencia de un merge regular que busca coincidencias exactas, merge_asof une la fila más cercana en el tiempo, sin pasarse.

- **Uso en Datos Financieros y Económicos:** Muy útil en datos de mercados financieros, donde necesitas combinar series de tiempo con marcas de tiempo ligeramente diferentes (como precios de acciones y datos económicos).

- **Tolerancia de Tiempo:** Puedes especificar una tolerancia de tiempo para limitar la distancia máxima de coincidencia.

- **Dirección de Fusión:** Puedes especificar si deseas buscar hacia atrás o hacia adelante en el tiempo para encontrar la coincidencia más cercana.


```python
pd.merge_asof(
    left:df|sr, # DataFrame o Serie a la izquierda de la fusión.
    right:df|sr, # DataFrame o Serie a la derecha de la fusión.
    on=None, # Columna en la que unir (debe ser de tipo tiempo o numérica).
    left_on=None, # Columnas de tiempo en cada DataFrame si las columnas tienen nombres diferentes.
    right_on=None, # Columnas de tiempo en cada DataFrame si las columnas tienen nombres diferentes.
    left_index=False, # Utilice el índice del DataFrame izquierdo como clave de unión.
    right_index=False, # Utilice el índice del DataFrame derecho como clave de unión.
    by=None, # Haga coincidir estas columnas antes de realizar la operación de combinación.
    left_by=None, #Columnas adicionales para coincidir antes de realizar la fusión aproximada.
    right_by=None, #Columnas adicionales para coincidir antes de realizar la fusión aproximada.
    suffixes: Suffixes = ("_x", "_y"), # Sufijo que se aplicará a los nombres de columnas superpuestas
    tolerance=None, # Seleccione una tolerancia dentro de este rango; int o Timedelta
    allow_exact_matches=True, # Si es Verdadero, permite la coincidencia con el mismo valor 'on'
    direction="backward", # La dirección en la que buscar coincidencias. Puede ser 'backward', 'forward', o 'nearest'.
```

Ejemplo

Supongamos que tienes dos DataFrames con datos de acciones y quieres fusionarlos en base a una columna de tiempo:


```python
# DataFrames de ejemplo
trades = pd.DataFrame({
    'time': pd.to_datetime(['2021-01-01 09:30', '2021-01-01 09:31']),
    'ticker': ['AAPL', 'MSFT'],
    'price': [150, 220]
})

quotes = pd.DataFrame({
    'time': pd.to_datetime(['2021-01-01 09:30', '2021-01-01 09:31', '2021-01-01 09:32']),
    'ticker': ['AAPL', 'AAPL', 'MSFT'],
    'bid': [149.8, 150.2, 219.5],
    'ask': [150.2, 150.5, 220.5]
})

# Uso de merge_asof
merged_df = pd.merge_asof(trades, quotes, on='time', by='ticker')
merged_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>time</th>
      <th>ticker</th>
      <th>price</th>
      <th>bid</th>
      <th>ask</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-01-01 09:30:00</td>
      <td>AAPL</td>
      <td>150</td>
      <td>149.8</td>
      <td>150.2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-01-01 09:31:00</td>
      <td>MSFT</td>
      <td>220</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



En este ejemplo, **merge_asof** combina los DataFrames trades y quotes basándose en las marcas de tiempo más cercanas y los tickers coincidentes. La función toma la fila de quotes que tiene la marca de tiempo más cercana a cada fila en trades, siempre que la marca de tiempo de quotes no sea posterior a la de trades.

## concat

[**Subir**](#Indice)

Se utiliza para concatenar o unir objetos pandas a lo largo de un eje particular, ya sean Series o DataFrames. También puede agregar una capa de indexación jerárquica en el eje de concatenación, lo que puede resultar útil si las etiquetas son iguales (o se superponen) en el número de eje pasado.

**Características Principales:**

- Unión a lo Largo de un Eje: Puedes concatenar a lo largo de filas (eje 0) o columnas (eje 1).
- Manejo de Índices: Permite gestionar índices de diferentes maneras, como ignorarlos, crear un índice jerárquico (MultiIndex), o incluso conservar índices específicos de los objetos originales.
- Unión de Diferentes Tamaños: Puedes unir objetos de diferentes tamaños y elegir cómo manejar los valores faltantes (NaN).
- Combinación de Tipos de Datos: Permite concatenar Series o DataFrames que tienen diferentes tipos de columnas.


```python
concat(
    objs # Una lista o secuencia de Series/DataFrames,
    axis=0, # El eje para realizar la concatenación, 0 para filas y 1 para columnas.
    join="outer", # Tipo de unión, 'outer' (todas las filas/columnas) o 'inner' (solo filas/columnas comunes).
    ignore_index=False, # Si es True, no usa los índices de los objetos y en su lugar crea un nuevo rango de índices.
    keys=None, # Para crear un índice jerárquico basado en las claves proporcionadas.
    levels=None, # (valores únicos) para construir un MultiIndex. De lo contrario, se deducirán de las claves.
    names=None, # Nombres de los niveles en el índice jerárquico resultante.
    verify_integrity=False, # Compruebe si el nuevo eje concatenado contiene duplicados.
    sortFalse, # Ordene el eje sin concatenación si aún no está alineado.
    copy=None, # Si es falso, no copie datos innecesariamente.
```

Ejemplos


```python
df1 = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df2 = pd.DataFrame({'B': [7, 8, 9], 'C': [10, 11, 12]})

# Concatenar DataFrames
result = pd.concat([df1, df2], axis=0, ignore_index=True)
result
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>5</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>7</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>8</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>9</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
</div>



## get_dummies

[**Subir**](#Indice)

Se utiliza para convertir variables categóricas en variables dummy/indicadoras. Es especialmente útil en el procesamiento y análisis de datos para prepararlos para algoritmos de machine learning, donde a menudo es necesario convertir categorías en un formato que los modelos puedan entender fácilmente.

**Características Principales**

- **Conversión de Variables Categóricas:** Transforma variables categóricas en columnas de variables dummy/indicadoras, una por cada categoría única.
- **Binario por Defecto:** Por defecto, estas variables dummy toman valores de 0 y 1, indicando la ausencia o presencia de la categoría.
- **Manejo de Nulos:** Puedes elegir cómo manejar los valores nulos.
- **Prefijos para Nombres de Columnas:** Ofrece la opción de agregar un prefijo a los nombres de las nuevas columnas para una identificación más fácil.


```python
get_dummies(
    data, # DataFrame o Serie para convertir
    prefix=None, # String que se añadirá como prefijo al nombre de cada columna dummy.
    prefix_sep="_", # Separador entre el prefijo y el nombre de la categoría.
    dummy_na=False, # Si es True, añade una columna para representar los NaN.
    columns=None, # Columnas específicas para convertir. Si es None, convierte todas las columnas categóricas.
    sparse=False, # si True las columnas codificadas ficticiamente estar respaldadas por una SparseArraymatriz NumPy
    drop_first=False, # Si es True, descarta la primera columna y deja una columna que representa la variable binaria:
    dtype=None, # Tipo de datos para las nuevas columnas.
```

**Ejemplo**

En el dataframe insurance, sobre el costo del seguro medico existen varias variables categoricas como sex, smoker y region.


```python
insurance.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>age_categories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>18-25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>18-25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>26-35</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>26-35</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>26-35</td>
    </tr>
  </tbody>
</table>
</div>




```python
# convertimos la variable categorica sex en valores True(1) y False(0)
insurance = pd.get_dummies(insurance, columns=['sex'], drop_first=True, dtype=int)
```


```python
insurance.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>age_categories</th>
      <th>sex_male</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>18-25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>18-25</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## from_dummies

[**Subir**](#Indice)

Cree una categoría DataFramea partir de una DataFrameserie de variables ficticias. Invierte la operación realizada por get_dummies().


```python
pd.from_dummies(
    data: DataFrame,
    sep=None, # El separador utilizado en los nombres de las columnas de las categorías ficticias para eliminar
    default_category=None, # La categoría implícita si todas las variables ficticias de una fila son cero.
```

**Ejemplo**


```python
df = pd.DataFrame({"col1_a": [1, 0, 0], "col1_b": [0, 1, 0],
                   "col2_a": [0, 1, 0], "col2_b": [1, 0, 0],
                   "col2_c": [0, 0, 0]})
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>col1_a</th>
      <th>col1_b</th>
      <th>col2_a</th>
      <th>col2_b</th>
      <th>col2_c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.from_dummies(df, sep="_", default_category={"col1": "d", "col2": "e"})
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>col1</th>
      <th>col2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a</td>
      <td>b</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b</td>
      <td>a</td>
    </tr>
    <tr>
      <th>2</th>
      <td>d</td>
      <td>e</td>
    </tr>
  </tbody>
</table>
</div>



## factorize

[**Subir**](#Indice)

Se utiliza para obtener una representación numérica de una matriz categórica, asignando a cada categoría única un valor entero. Esta función es útil para convertir una columna de texto o categorías en una columna numérica, lo que facilita ciertas operaciones y análisis, y es especialmente útil en algoritmos de machine learning que requieren entradas numéricas.

**Características Principales:**
- **Asignación de Índices a Categorías Únicas:** Cada categoría única en la columna se asigna a un índice entero diferente.
- **Manejo de Valores Faltantes:** Los valores faltantes (NaN) se manejan automáticamente y se les asigna un índice único.
- **Devolución de Etiquetas y Uniques:** La función devuelve dos elementos: un arreglo de etiquetas y un arreglo con las categorías únicas.


```python
factorize(
    values, # Secuencia
    sort=False, # Si es True, las etiquetas únicas se ordenarán.
    use_na_sentinel=True, # Si es Verdadero, se utilizará el -1 para los valores de NaN. False: enteros no negativos
    size_hint:int= None, # Sugerencia sobre el medidor de tabla hash.
)
```

**Ejemplos**


```python
labels, unique = pd.factorize(insurance['region'])
```


```python
insurance['region'] = labels
```


```python
unique
```




    Index(['southwest', 'southeast', 'northwest', 'northeast'], dtype='object')




```python
insurance
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>age_categories</th>
      <th>sex_male</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>0</td>
      <td>16884.92400</td>
      <td>18-25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>1</td>
      <td>1725.55230</td>
      <td>18-25</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>1</td>
      <td>4449.46200</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>2</td>
      <td>21984.47061</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>2</td>
      <td>3866.85520</td>
      <td>26-35</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>30.970</td>
      <td>3</td>
      <td>no</td>
      <td>2</td>
      <td>10600.54830</td>
      <td>46-55</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>31.920</td>
      <td>0</td>
      <td>no</td>
      <td>3</td>
      <td>2205.98080</td>
      <td>18-25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>36.850</td>
      <td>0</td>
      <td>no</td>
      <td>1</td>
      <td>1629.83350</td>
      <td>18-25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>25.800</td>
      <td>0</td>
      <td>no</td>
      <td>0</td>
      <td>2007.94500</td>
      <td>18-25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>29.070</td>
      <td>0</td>
      <td>yes</td>
      <td>2</td>
      <td>29141.36030</td>
      <td>56-65</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 8 columns</p>
</div>



## unique

[**Subir**](#Indice)

Devuelve valores únicos en orden de aparición (Esto NO ordena).Incluye valores de NA.

**La devolución puede ser:**

- **Índice:** cuando la entrada es un índice
- **Categórico:** cuando la entrada es un tipo categórico
- **ndarray:** cuando la entrada es una serie/ndarray
- Devuelve numpy.ndarray o ExtensionArray.


```python
pd.unique(values)
```


```python
insurance.age_categories.unique()
```




    ['18-25', '26-35', '46-55', '36-45', '56-65']
    Categories (5, object): ['18-25' < '26-35' < '36-45' < '46-55' < '56-65']



## lreshape

[**Subir**](#Indice)

Se utiliza para transformar datos de un formato ancho a un formato largo. Esta función es útil cuando tienes múltiples columnas en un DataFrame y deseas "fundirlas" en una sola columna, manteniendo las demás columnas como identificadores.


```python
pd.lreshape(
    data: DataFrame,
    groups: dict, #  Un diccionario donde cada clave es un nuevo nombre de columna y cada valor es una lista de nombres
                  # de columnas antiguas que se "fundirán" bajo el nuevo nombre de columna como parte de la transformación.
    dropna=True # Si es True, no incluye columnas cuyas entradas sean todas NaN. Por defecto es True.
) -> DataFrame:
```

**Ejemplo**


```python
data = pd.DataFrame({
    'hr1': [514, 573],
    'hr2': [545, 526],
    'team': ['Red Sox', 'Yankees'],
    'year1': [2007, 2007],
    'year2': [2008, 2008]
})
```


```python
data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hr1</th>
      <th>hr2</th>
      <th>team</th>
      <th>year1</th>
      <th>year2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>514</td>
      <td>545</td>
      <td>Red Sox</td>
      <td>2007</td>
      <td>2008</td>
    </tr>
    <tr>
      <th>1</th>
      <td>573</td>
      <td>526</td>
      <td>Yankees</td>
      <td>2007</td>
      <td>2008</td>
    </tr>
  </tbody>
</table>
</div>




```python
result = pd.lreshape(data, {'year': ['year1', 'year2'], 'hr': ['hr1', 'hr2']})
```


```python
result
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>team</th>
      <th>year</th>
      <th>hr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Red Sox</td>
      <td>2007</td>
      <td>514</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Yankees</td>
      <td>2007</td>
      <td>573</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Red Sox</td>
      <td>2008</td>
      <td>545</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Yankees</td>
      <td>2008</td>
      <td>526</td>
    </tr>
  </tbody>
</table>
</div>



## pd.wide_to_long

[**Subir**](#Indice)

Se utiliza para transformar DataFrames de un formato ancho a un formato largo. Es menos flexible pero más amigable para el usuario que la función **melt**.

**Características Principales:**

- **Transformación de Formato Ancho a Largo:** Permite desagregar columnas en filas, agrupando por identificadores.
- **Uso de Stubnames:** wide_to_long funciona con columnas que tienen un formato común (stubname) seguido de un sufijo. Por ejemplo, con stubnames como 'A' y 'B', espera encontrar grupos de columnas como 'A_sufijo1', 'A_sufijo2', 'B_sufijo1', 'B_sufijo2', etc.


```python
pd.wide_to_long(
    df: DataFrame,
    stubnames, # Nombres base (stubs) de las columnas en el formato ancho.
    i, # Columna(s) que se usarán como identificadoras.
    j, # Nombre de la nueva columna que contendrá los sufijos.
    sep: str = "", suffix: str = r"\d+"  # Carácter que separa el stubname del sufijo en los nombres de columna.
) -> DataFrame:
```

**Ejemplo**

Estos datos de ventas anuales de varios productos, pero los datos están en un formato ancho y necesitas convertirlos a un formato largo para análisis y visualizaciones más eficientes.


```python
data = {
    'ProductoA_2016': [120, 130, 140],
    'ProductoA_2017': [150, 160, 170],
    'ProductoA_2018': [180, 190, 200],
    'ProductoA_2019': [210, 220, 230],
    'ProductoA_2020': [240, 250, 260],
    'ProductoB_2016': [80, 90, 100],
    'ProductoB_2017': [110, 120, 130],
    'ProductoB_2018': [140, 150, 160],
    'ProductoB_2019': [170, 180, 190],
    'ProductoB_2020': [200, 210, 220],
    'ProductoC_2016': [60, 70, 80],
    'ProductoC_2017': [90, 100, 110],
    'ProductoC_2018': [120, 130, 140],
    'ProductoC_2019': [150, 160, 170],
    'ProductoC_2020': [180, 190, 200],
    'Tienda': ['Tienda1', 'Tienda2', 'Tienda3']
}
df = pd.DataFrame(data)
```


```python
df_long = pd.wide_to_long(df, stubnames=['ProductoA', 'ProductoB', 'ProductoC'], i='Tienda', j='Año', sep='_', suffix='\d{4}')
```


```python
df_long.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>ProductoA</th>
      <th>ProductoB</th>
      <th>ProductoC</th>
    </tr>
    <tr>
      <th>Tienda</th>
      <th>Año</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda1</th>
      <th>2016</th>
      <td>120</td>
      <td>80</td>
      <td>60</td>
    </tr>
    <tr>
      <th>Tienda2</th>
      <th>2016</th>
      <td>130</td>
      <td>90</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Tienda3</th>
      <th>2016</th>
      <td>140</td>
      <td>100</td>
      <td>80</td>
    </tr>
    <tr>
      <th>Tienda1</th>
      <th>2017</th>
      <td>150</td>
      <td>110</td>
      <td>90</td>
    </tr>
    <tr>
      <th>Tienda2</th>
      <th>2017</th>
      <td>160</td>
      <td>120</td>
      <td>100</td>
    </tr>
  </tbody>
</table>
</div>



## isna

[**Subir**](#Indice)


```python
df.isna()
```

Identifica Valores Faltantes: isna retorna un DataFrame o Serie booleano del mismo tamaño que el original, **donde cada elemento es True si el valor correspondiente es NaN o faltante, y False en caso contrario**.

**Aplicaciones Comunes:**

- **Limpieza de Datos:** Antes de analizar datos, a menudo es necesario manejar los valores faltantes. isna te ayuda a identificar dónde están estos valores.
- **Rellenar o Eliminar Valores Faltantes:** Puedes usar isna en combinación con fillna() para reemplazar los NaN o con dropna() para eliminar filas/columnas con valores faltantes.
- **Análisis Condicional:** En análisis de datos, a veces necesitas seleccionar o filtrar datos basándote en la presencia de valores faltantes.

## isnull

[**Subir**](#Indice)


```python
pd.isnull(df)
```

Se utiliza para detectar valores faltantes en un  DataFrame o una Serie. Es una función esencial para la limpieza y el preprocesamiento de datos en el análisis de datos.

**Características Principales:**
- **Detecta Valores Faltantes:** Identifica si los valores en un objeto son NaN (en arrays numéricos), None o NaN (en arrays de objetos), o NaT (en arrays de tipo fecha/hora).
- **Aplicable a Diversos Tipos de Datos:** Funciona con escalares, arrays, Series, DataFrames e índices.

**Usos Comunes:**
- **Análisis de Datos Faltantes:** pandas.isnull es fundamental para identificar y contar valores faltantes en un conjunto de datos.
- **Limpieza de Datos:** Utilizado en combinación con funciones como dropna (para eliminar filas/columnas con valores faltantes) o fillna (para reemplazar valores faltantes con un valor específico).

## notna

[**Subir**](#Indice)


```python
pd.notna(df)
```

Se utiliza para detectar valores no faltantes en un DataFrame o una Serie. Esta función devuelve un resultado booleano, donde **True indica que el valor no es faltante** y **False indica que es un valor faltante**

**Características Principales:**

- **Detecta Valores No Faltantes:** pandas.notna es esencialmente el inverso booleano de pandas.isna o pandas.isnull.
- **Aplicable a Diversos Tipos de Datos:** Funciona con escalares, arrays, Series, DataFrames e índices.

## notnull

[**Subir**](#Indice)


```python
pd.notnull(obj)
```

Método para detectar valores no faltantes (es decir, valores válidos) en un DataFrame, Serie o array. Funciona de manera que  True indica que el valor no es faltante y False que sí lo es. Aplicable a Diversos Tipos de Datos: Funciona con escalares, arrays, Series, DataFrames e índices.

**Usos Comunes:**

- **Limpieza de Datos:** Utilizado para identificar y trabajar con datos no faltantes en un DataFrame o Serie.
- **Filtrado de Datos:** Se puede usar para seleccionar solo aquellas filas/columnas que tienen valores no faltantes.
- **Preparación de Datos para Análisis:** Es importante saber qué datos están presentes y cuáles no antes de realizar cualquier análisis estadístico o de datos.

## to_numeric

[**Subir**](#Indice)

Se utiliza para convertir argumentos a un tipo numérico. Esta función es útil cuando se trabaja con datos que pueden tener mezclas de tipos (como números y cadenas) y se necesita asegurar que todo el conjunto de datos sea numérico para análisis o procesamiento adicional. Es más robusta que el metodo .astype() por sus caracteristicas.

**Características Principales:**

- **Conversión a Tipo Numérico:** Convierte argumentos (escalares, listas, tuplas, arrays 1-d, o Series) a un tipo numérico.
- **Manejo de Errores:** Permite especificar cómo se deben manejar los errores de conversión con el parámetro errors.
- **Downcasting:** Permite convertir a un tipo numérico más pequeño (por ejemplo, de float64 a float32) si es posible.
- **Soporte para Back-Ends de Datos:** Permite especificar el back-end de datos (numpy_nullable o pyarrow) para el DataFrame resultante.

**Aplicaciones Comunes:**
- **Preprocesamiento de Datos:** Convertir datos de diferentes fuentes a un formato numérico uniforme.
- **Limpieza de Datos:** Manejar datos no numéricos o errores de formato en conjuntos de datos numéricos.
- **Optimización de Memoria:** Usar downcast para reducir el uso de memoria de grandes DataFrames.


```python
to_numeric(
    arg, # Argumento a ser convertido.
    errors="raise", # Manejo de errores: raise:Exepcion, coerce:Establecer comom NaN o ignore:devolver la entrada
    downcast: Literal["integer", "signed", "unsigned", "float"] | None = None, intentar downcast a un tipo más pequeño.
    dtype_backend=lib.no_default,
)
```

**Ejemplo**


```python
s = pd.Series(['1.0', '2', -3, 'cadena', 5.36])
```


```python
pd.to_numeric(s, errors='coerce')
```




    0    1.00
    1    2.00
    2   -3.00
    3     NaN
    4    5.36
    dtype: float64



## to_datetime

[**Subir**](#Indice)

Es utilizada para convertir argumentos a datetime. Esta función es esencial para trabajar con datos temporales, ya que permite la conversión eficiente de formatos de cadena y otros tipos de datos a un formato de fecha/hora estandarizado.

**Funcionalidades y Parámetros:**

- **Conversión Versátil:** Puede manejar una variedad de formatos de entrada, incluyendo enteros, flotantes, cadenas, objetos datetime, listas, tuplas, arrays 1-d, Series y DataFrame/diccionarios.
- **Manejo de Errores:** Ofrece varias opciones para manejar errores de conversión ('raise', 'coerce', 'ignore'), lo que permite controlar cómo se tratan los datos no convertibles.
- **Especificación del Orden de Fecha:** Los parámetros dayfirst y yearfirst permiten especificar el orden de interpretación de las fechas en las cadenas.
- **Soporte para Zonas Horarias:** El parámetro utc controla el manejo de zonas horarias, permitiendo convertir a una zona horaria consciente (UTC) o mantener la zona horaria original.
- **Formato Personalizado:** El parámetro format permite especificar una cadena de formato para analizar fechas y horas de manera más precisa.
- **Inferencia de Formato:** infer_datetime_format intenta inferir el formato de las cadenas de fecha/hora para acelerar la conversión.
- **Origen y Unidad:** origin y unit permiten especificar la referencia de fecha y la unidad de medida para la conversión de tiempos épicos.


```python
pd.to_datetime(
    arg: #objeto a convertir a una fecha y hora, si es dataframe minimo debe tener columnas: "year", "month", "day".
    errors="raise", # Manejo de errores: raise:Exepcion, coerce:Establecer comom NaN o ignore:devolver la entrada
    dayfirst=False, # Si es True analiza las fechas con el día primero, por ejemplo, "10/11/12" se analiza como 2012-11-10.
    yearfirst=False, # Si Trueanaliza las fechas con el año primero, por ejemplo, "10/11/12"se analiza como 2010-11-12.
    utc=False, # Si es True, siempre devuelve un objeto datetime consciente de la zona horaria UTC.
    format= None, # El strftime para analizar el tiempo, por ejemplo "%d/%m/%Y"
    exact=True, # True coincidencia exacta. False, permita que el formato coincida en cualquier parte de destino.
    unit:= None, # La unidad de tiempo si arg es un entero o un float. Las opciones son 'D', 's', 'ms', 'us', 'ns'.
    infer_datetime_format=False, # Si es True, intenta inferir el formato de fecha/hora a partir de los datos
    originz = "unix", # Define el punto de referencia para los tiempos épicos. Por defecto es 'unix' (1970-01-01).
    cache=True, # Si es True, cachea los resultados únicos de conversiones.
) -> DatetimeIndex | Series | DatetimeScalar | NaTType | None:
```

**Ejemplo**


```python
df = pd.DataFrame({'year': [2015, 2016], 'month': [2, 3], 'day': [4, 5]})
pd.to_datetime(df)
```




    0   2015-02-04
    1   2016-03-05
    dtype: datetime64[ns]




```python
pd.to_datetime(1490195805433502912, unit='ns')
```




    Timestamp('2017-03-22 15:16:45.433502912')




```python
pd.to_datetime(['2018-10-26 12:00 -0500', '2018-10-26 13:00 -0500'])
```




    DatetimeIndex(['2018-10-26 12:00:00-05:00', '2018-10-26 13:00:00-05:00'], dtype='datetime64[ns, UTC-05:00]', freq=None)




```python
pd.to_datetime(['2020-10-25 02:00 +0200', '2020-10-25 04:00 +0100'], utc=True)
```




    DatetimeIndex(['2020-10-25 00:00:00+00:00', '2020-10-25 03:00:00+00:00'], dtype='datetime64[ns, UTC]', freq=None)



## to_timedelta

[**Subir**](#Indice)

Se utiliza para convertir argumentos a timedelta, que son diferencias absolutas en tiempos, expresadas en distintas unidades (como días, horas, minutos, segundos). Esta función convierte un argumento de un formato o valor reconocido de timedelta a un tipo Timedelta.


```python
pd.to_timedelta(
    arg: str|int|float|timedelta|list|tuple|range|ArrayLike|Index|Series,
    unit="ns", # Denota la unidad del arg para argumentos numéricos.
    errors="raise", # Manejo de errores: raise:Exepcion, coerce:Establecer comom NaN o ignore:devolver la entrada
) -> Timedelta | TimedeltaIndex | Series:
```

**Valores posibles de unit:**

- **semanas:** ‘W’
- **dias:** ‘D’ / ‘days’ / ‘day’
- **horas:** ‘hours’ / ‘hour’ / ‘hr’ / ‘h’ / ‘H’
- **minutos:** ‘m’ / ‘minute’ / ‘min’ / ‘minutes’ / ‘T’
- **segundos:** ‘s’ / ‘seconds’ / ‘sec’ / ‘second’ / ‘S’
- **milisegundos:** ‘ms’ / ‘milliseconds’ / ‘millisecond’ / ‘milli’ / ‘millis’ / ‘L’
- **microsegundos:** ‘us’ / ‘microseconds’ / ‘microsecond’ / ‘micro’ / ‘micros’ / ‘U’
- **nanosegundos:** ‘ns’ / ‘nanoseconds’ / ‘nano’ / ‘nanos’ / ‘nanosecond’ / ‘N’

**Ejemplos**


```python
pd.to_timedelta('1 days 06:05:01.00003')
```




    Timedelta('1 days 06:05:01.000030')




```python
pd.to_timedelta(['1 days 06:05:01.00003', '15.5us', 'nan'])
```




    TimedeltaIndex(['1 days 06:05:01.000030', '0 days 00:00:00.000015500', NaT], dtype='timedelta64[ns]', freq=None)



## date_range

[**Subir**](#Indice)

Es una herramienta poderosa para crear rangos de fechas con frecuencia fija. Genera un rango de fechas con frecuencia fija, útil para crear índices de fecha/hora o para realizar operaciones con series temporales.

**Aplicaciones Comunes:**

- **Creación de Índices Temporales:** Ideal para crear índices para DataFrame o Series que trabajan con datos temporales.
- **Generación de Fechas para Análisis:** Produce secuencias de fechas para análisis de series temporales o simulaciones.
- **Operaciones Temporales en DataFrames:** Facilita la realización de operaciones basadas en fechas, como agrupación o filtrado.


```python
date_range(
    start=None, # El límite izquierdo para generar fechas. Puede ser una cadena o un objeto similar a datetime.
    end=None, # El límite derecho para generar fechas. Puede ser una cadena o un objeto similar a datetime.
    periods=None,#  El número de períodos a generar.
    freq='D', # La frecuencia de las fechas a generar. Puede ser una cadena, Timedelta, datetime.timedelta, o DateOffset.
    tz=None, # El nombre de la zona horaria para generar un DatetimeIndex localizado.
    normalize=False, #  Normaliza las fechas de inicio/final a medianoche antes de generar el rango de fechas.
    name=None, # El nombre del DatetimeIndex resultante.
    inclusive="both", # Incluye los límites. Puede ser "both", "neither", "left" o "right".,
    unit=None, # Especifica la resolución deseada del resultado.
) -> DatetimeIndex:
```

**Ejemplo**


```python
# Rango de Fechas Mensual - primer dia del mes
pd.date_range(start='1/1/2018', end='12/01/2018', freq='MS')
```




    DatetimeIndex(['2018-01-01', '2018-02-01', '2018-03-01', '2018-04-01',
                   '2018-05-01', '2018-06-01', '2018-07-01', '2018-08-01',
                   '2018-09-01', '2018-10-01', '2018-11-01', '2018-12-01'],
                  dtype='datetime64[ns]', freq='MS')




```python
# Rango de Fechas con Zona Horaria:
pd.date_range(start='1/1/2018', periods=5, tz='Asia/Tokyo')
```




    DatetimeIndex(['2018-01-01 00:00:00+09:00', '2018-01-02 00:00:00+09:00',
                   '2018-01-03 00:00:00+09:00', '2018-01-04 00:00:00+09:00',
                   '2018-01-05 00:00:00+09:00'],
                  dtype='datetime64[ns, Asia/Tokyo]', freq='D')




```python
# Rango de Fechas Mensual:
pd.date_range(start='1/1/2018', periods=5, freq='M')
```




    DatetimeIndex(['2018-01-31', '2018-02-28', '2018-03-31', '2018-04-30',
                   '2018-05-31'],
                  dtype='datetime64[ns]', freq='M')



## bdate_range

[**Subir**](#Indice)

Genera un rango de fechas con frecuencia fija, pero a diferencia de date_range, se enfoca en días laborables (excluyendo fines de semana y, opcionalmente, festivos).


```python
 pd.bdate_range(
    start=None, # Límite izquierdo para generar fechas, puede ser una cadena o un objeto similar a datetime.
    end=None, # Límite derecho para generar fechas.
    periods=None, # Número de períodos a generar.
    freq="B", # La frecuencia de las fechas, por defecto es 'B' (días laborables).
    tz=None, # Zona horaria para un DatetimeIndex localizado.
    normalize=True, # Normaliza las fechas de inicio/final a medianoche antes de generar el rango.
    name=None, # Nombre del DatetimeIndex resultante.
    weekmask=None, # Personalizan los días laborables válidos y los días festivos a excluir.
    holidays=None, # Personalizan los días laborables válidos y los días festivos a excluir.
    inclusive="both", # Incluir límites; establecer como cerrado o abierto. {“both”, “neither”, “left”, “right”}
) -> DatetimeIndex:
```

**Ejemplo**


```python
pd.bdate_range(start='1/1/2018', end='1/15/2018')
```




    DatetimeIndex(['2018-01-01', '2018-01-02', '2018-01-03', '2018-01-04',
                   '2018-01-05', '2018-01-08', '2018-01-09', '2018-01-10',
                   '2018-01-11', '2018-01-12', '2018-01-15'],
                  dtype='datetime64[ns]', freq='B')



## period_range

[**Subir**](#Indice)

Se utiliza para generar un rango de períodos con una frecuencia fija. Es útil para crear índices basados en períodos para series temporales.


```python
period_range(
    start=None, # El inicio del rango de períodos.
    end=None, # El final del rango de períodos.
    periods=None, # El número de períodos a generar.
    freq=None, # La frecuencia de los períodos, por ejemplo, 'D' para días o 'M' para meses.
    name=None, #  El nombre para el PeriodIndex resultante.
) -> PeriodIndex:
```


```python
pd.period_range(start='2023-01-01', end='2023-01-31', freq='D')
```




    PeriodIndex(['2023-01-01', '2023-01-02', '2023-01-03', '2023-01-04',
                 '2023-01-05', '2023-01-06', '2023-01-07', '2023-01-08',
                 '2023-01-09', '2023-01-10', '2023-01-11', '2023-01-12',
                 '2023-01-13', '2023-01-14', '2023-01-15', '2023-01-16',
                 '2023-01-17', '2023-01-18', '2023-01-19', '2023-01-20',
                 '2023-01-21', '2023-01-22', '2023-01-23', '2023-01-24',
                 '2023-01-25', '2023-01-26', '2023-01-27', '2023-01-28',
                 '2023-01-29', '2023-01-30', '2023-01-31'],
                dtype='period[D]')



## timedelta_range

[**Subir**](#Indice)

Es utilizada para generar un rango de diferencias de tiempo (timedeltas) con una frecuencia fija. Es útil para crear secuencias de datos basadas en diferencias de tiempo.


```python
pd.timedelta_range(
    start=None, # El inicio del rango de períodos.
    end=None, # El final del rango de períodos.
    periods=None, # El número de períodos a generar.
    freq=None, # Frecuencia de los timedeltas, como 'D' para días o 'H' para horas.
    name=None, # Nombre para el TimedeltaIndex resultante.
    closed=None, # Define qué extremo del intervalo incluir.
    unit=None, # Especifica la resolución deseada del resultado.
) -> TimedeltaIndex:
```

**Ejemplo**


```python
# Generar un rango de timedeltas diarios:
pd.timedelta_range(start='1 day', periods=4)
```




    TimedeltaIndex(['1 days', '2 days', '3 days', '4 days'], dtype='timedelta64[ns]', freq='D')




```python
# Generar un rango de timedeltas con frecuencia de 6 horas:
pd.timedelta_range(start='1 day', end='2 days', freq='6h')
```




    TimedeltaIndex(['1 days 00:00:00', '1 days 06:00:00', '1 days 12:00:00',
                    '1 days 18:00:00', '2 days 00:00:00'],
                   dtype='timedelta64[ns]', freq='6H')



## infer_freq

[**Subir**](#Indice)

Se utiliza para inferir la frecuencia más probable de un índice dado. Este índice puede ser de tipo DatetimeIndex, TimedeltaIndex, una Series o un arreglo similar. La función retorna una cadena que representa la frecuencia detectada, o None si no puede discernir una frecuencia.


```python
pd.infer_freq(
    index: DatetimeIndex | TimedeltaIndex | Series | DatetimeLikeArrayMixin,
) -> str | None:
```


```python
n = pd.date_range(start='2020/12/01', end='2020/12/30', periods=30)
```


```python
pd.infer_freq(n)
```




    'D'



## interval_range

[**Subir**](#Indice)

Se utiliza para crear un IntervalIndex con una frecuencia fija. Los datos de intervalo son aquellos que se expresan en términos de un rango entre dos puntos, como períodos de tiempo o rangos numéricos. En Pandas, esto suele implicar el uso de estructuras de datos especializadas y funciones que permiten trabajar eficientemente con este tipo de información, como crear, manipular y analizar intervalos de datos.

Esta función es útil para crear rangos de intervalos personalizados, ya sean numéricos o basados en fechas, para análisis y visualizaciones en series temporales.


```python
pd.interval_range(
    start=None, # El inicio del rango de períodos.
    end=None, # El final del rango de períodos.
    periods=None, # El número de períodos a generar.
    freq=None, # Frecuencia de los timedeltas, compatible con el tipo de start y end.
    name=None, # Nombre para el IntervalIndex resultante.
    closed="right", # Define si los intervalos están cerrados a la izquierda, derecha, ambos lados o ninguno.
) -> IntervalIndex:
```

**Ejemplos**


```python
# Intervalos numéricos
pd.interval_range(start=0, end=5)
```




    IntervalIndex([(0, 1], (1, 2], (2, 3], (3, 4], (4, 5]], dtype='interval[int64, right]')




```python
# Intervalos con fechas:
pd.interval_range(start=pd.Timestamp('2017-01-01'), end=pd.Timestamp('2017-01-04'))
```




    IntervalIndex([(2017-01-01, 2017-01-02], (2017-01-02, 2017-01-03], (2017-01-03, 2017-01-04]], dtype='interval[datetime64[ns], right]')




```python
# Especificar frecuencia en intervalos:
pd.interval_range(start=0, periods=4, freq=1.5)
```




    IntervalIndex([(0.0, 1.5], (1.5, 3.0], (3.0, 4.5], (4.5, 6.0]], dtype='interval[float64, right]')



## eval

[**Subir**](#Indice)

Es una función de Pandas que evalúa expresiones de Python expresadas como cadenas de texto. Utiliza varios backends para optimizar el rendimiento. Soporta operaciones aritméticas como +, -, *, /, **, %, // (solo en el motor de Python) y operaciones booleanas como | (or), & (and), y ~ (not). Además, el analizador de 'pandas' permite el uso de and, or, y not con la misma semántica que los operadores bitwise correspondientes. Es compatible con objetos Series y DataFrame, comportándose como en la evaluación estándar de Python.


```python
eval(
    expr: La expresión a evaluar. Esta cadena no puede contener ninguna declaración de Python , sólo expresiones de Python .
    parser="pandas", # El analizador que se utilizará para construir el árbol de sintaxis a partir de la expresión.
    engine='numexpr', # El analizador que se utilizará para construir el árbol de sintaxis a partir de la expresión.
    local_dict=None, # Un diccionario de variables locales, tomado de locals() por defecto.
    global_dict=None, # Un diccionario de variables globales, tomado de globals() por defecto.
    resolvers=(), # Una lista de objetos que implementan el método especial __getitem__.
    level: int = 0, # El número de marcos de pila anteriores que se van a atravesar y agregar al alcance actual.
    target=None, # Este es el objde destino para la asignación. Se usa cuando hay asignación de variables en la expresión.
    inplace: bool = False, # Si se proporciona el objetivo y la expresión muta el objetivo
```


```python
df = pd.DataFrame({"animal": ["dog", "pig"], "age": [10, 20]})
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>animal</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>dog</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>pig</td>
      <td>20</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.eval("double_age = df.age * 2", target=df)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>animal</th>
      <th>age</th>
      <th>double_age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>dog</td>
      <td>10</td>
      <td>20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>pig</td>
      <td>20</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>



## guess_datetime_format

Es una herramienta técnica usada internamente para inferir el formato de fecha y hora de una cadena de texto. Esta función intenta adivinar el formato más adecuado para una cadena de fecha y hora dada, lo que puede ser útil para optimizar la conversión de cadenas a objetos de fecha y hora en Pandas. Sin embargo, es importante tener en cuenta que guess_datetime_format es parte del módulo interno de Pandas y no está destinado para uso directo en aplicaciones comunes. En su lugar, funciones como **pandas.to_datetime** ofrecen una interfaz más amigable para convertir cadenas en fechas, utilizando, entre otras cosas, la capacidad de inferir formatos.


```python
from pandas.tseries.api import guess_datetime_format
```


```python
guess_datetime_format('09/13/2023')
```

## util.hash_array

En Pandas se utiliza para obtener un valor hash para cada elemento en un arreglo de datos. Esto es especialmente útil en operaciones que requieren comparaciones rápidas o identificación única de filas o elementos en un DataFrame o Serie, como en operaciones de agrupación, unión o eliminación de duplicados.


```python
pd.util.hash_array(
    vals: ArrayLike,
    encoding: str = "utf8", # Codificación de datos y clave cuando se trata de cadenas.
    hash_key: str = _default_hash_key, # Hash_key para la clave de cadena a codificar.
    categorize: bool = True, # Si se deben categorizar primero las matrices de objetos antes del hash.
) -> npt.NDArray[np.uint64]:
```

**Ejemplos**


```python
import numpy as np
pd.util.hash_array(np.array([1, 2, 3]))
```




    array([ 6238072747940578789, 15839785061582574730,  2185194620014831856],
          dtype=uint64)



## util.hash_pandas_object

Genera valores hash para cada elemento en un objeto de Pandas, lo que es útil para operaciones que requieren una comparación rápida o identificación única de elementos o filas. Es especialmente útil en operaciones como agrupaciones, uniones y detección de duplicados.  

La función toma un objeto de Pandas (como un DataFrame o una Serie) y devuelve una Serie de Pandas con valores hash correspondientes a cada elemento o fila. El hash de cada elemento es un número entero de 64 bits.


```python
hash_pandas_object(
    obj: Index | DataFrame | Series,
    index=True, # Indice en el hash (si es Serie/Marco de datos).
    encoding="utf8", # Codificación de datos y clave cuando se trata de cadenas.
    hash_key='0123456789123456', # Hash_key para la clave de cadena a codificar.
    categorize=True, # Si se deben categorizar primero las matrices de objetos antes del hash.
) -> Series:
```

**Ejemplos**


```python
pd.util.hash_pandas_object(pd.Series([1, 2, 3]))
```




    0    14639053686158035780
    1     3869563279212530728
    2      393322362522515241
    dtype: uint64



## pd.api.interchange.from_dataframe

Es una función en la biblioteca de Pandas en Python que forma parte de la API de intercambio de datos. Esta función es importante en el contexto de la interoperabilidad entre Pandas y otros sistemas de análisis de datos o bibliotecas.

Está diseñada para convertir un DataFrame de Pandas en un tipo de datos que es compatible con un sistema externo o una biblioteca. Esto es especialmente útil en situaciones donde necesitas trabajar con datos de Pandas en un entorno o biblioteca que no admite directamente los DataFrames de Pandas.


```python
from pandas.api.interchange import from_dataframe
```


```python
df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
```


```python
data_interchange_obj = from_dataframe(df)
```

En este ejemplo, df es un DataFrame de Pandas y from_dataframe(df) convierte este DataFrame en un objeto que sigue un estándar de intercambio de datos.
