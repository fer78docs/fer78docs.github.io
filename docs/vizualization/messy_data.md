---
layout: default
title: Messy Data
nav_order: 4
parent: Data Visualization
---


# Visualizaciones de datos para datos desordenados

Aprenda a solucionar problemas al visualizar datos confusos y faltantes.

Los tutoriales de visualización de datos generalmente utilizan datos preprocesados. Pero ¿qué pasa con los conjuntos de datos en la naturaleza? ¿Qué hacemos con los datos faltantes? ¿O valores atípicos que distorsionan en gran medida las visualizaciones? ¿Qué hacemos cuando hay demasiadas observaciones para poder interpretarlas en un diagrama de dispersión? Este artículo presentará algunos de los métodos que podemos utilizar para solucionar estos problemas.

Digamos que somos nuevos agentes inmobiliarios que queremos utilizar datos para comprender mejor la relación entre el precio y el número de dormitorios de una vivienda. Usaremos un conjunto de datos que hemos llamado housingdesde Kaggle sobre listados de viviendas de EE. UU.

## Datos perdidos

Las observaciones incompletas (o los datos faltantes) generalmente se ignoran al trazar funciones en bibliotecas de Python de uso común, como matplotlib y seaborn. Por lo tanto, es posible que deseemos eliminar esas filas o imputar los valores faltantes antes de trazar. Podemos verificar si faltan datos usando .info():

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 384977 entries, 0 to 384976
Data columns (total 17 columns):
 #   Column                   Non-Null Count   Dtype  
---  ------                   --------------   -----  
 0   region                   384977 non-null  object 
 1   price                    384977 non-null  int64  
 2   type                     384977 non-null  object 
 3   sqfeet                   384977 non-null  int64  
 4   beds                     384977 non-null  int64  
 5   baths                    384977 non-null  float64
 6   cats_allowed             384977 non-null  int64  
 7   dogs_allowed             384977 non-null  int64  
 8   smoking_allowed          384977 non-null  int64  
 9   wheelchair_access        384977 non-null  int64  
 10  electric_vehicle_charge  384977 non-null  int64  
 11  comes_furnished          384977 non-null  int64  
 12  laundry_options          305951 non-null  object 
 13  parking_options          244290 non-null  object 
 14  lat                      383059 non-null  float64
 15  long                     383059 non-null  float64
 16  state                    384977 non-null  object 
dtypes: float64(3), int64(9), object(5)
memory usage: 49.9+ MB
None
```

Según este resultado, es posible que nos preocupen las columnas laundry_optionsy parking_optionsporque tienen más valores faltantes que otras columnas.

## Vista preliminar

Echemos un primer vistazo a dos variables y veamos con qué problemas nos encontramos. Aquí hay un gráfico de precio versus área en pies cuadrados:

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_outliers.webp)

No parece que haya muchos puntos en esta trama, aunque debería haber más de 300.000 puntos. Los 1e6y 1e9en los ejes x e y, respectivamente, indican que la escala y el rango de ambas características son increíblemente grandes. Por ejemplo, tenemos al menos un anuncio de vivienda que cuesta casi 3.000.000.000 de dólares al mes. Lidiar con estos valores atípicos es lo primero que tendremos que hacer para visualizar los datos de manera más efectiva.

## Trazar con valores atípicos

Podemos reducir cada característica del gráfico para eliminar los valores atípicos hasta que tengamos una mejor idea de los datos. Puede ser necesario un poco de prueba y error para encontrar los valores correctos, así que comencemos limitando `price` a menos de $10 000 000 y `sqfeet` a menos de 2 000 000:

```python
housing2 = housing[(housing.price < 10000000) & (housing.price>0)]
housing2 = housing2[(housing2.sqfeet < 2000000) & (housing2.sqfeet>0)]

sns.scatterplot(housing2['sqfeet'], housing2['price'])
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_scaledown1.webp)

Este diagrama de dispersión es un poco mejor. Podemos ver más puntos en la parte inferior izquierda del gráfico. Acerquémonos a ese grupo de puntos: limitemos ambos `price` y `sqfeet` a valores inferiores a 20.000:

```python
housing2 = housing[(housing.price < 20000) & (housing.price>0)]
housing2 = housing2[(housing2.sqfeet < 20000) & (housing2.sqfeet>0)]

sns.scatterplot(housing2['sqfeet'], housing2['price'])
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_scaledown2.webp)

¡Ahora estamos empezando a ver todos los puntos! Todavía hay mucho espacio en blanco en el lado derecho, así que limitemos nuestros datos una vez más, esta vez limitando ambos `price` y `sqfeet` a valores inferiores a 3000:

```python
## limit price and sqfeet to < 3000
housing2 = housing[(housing.price < 3000) & (housing.price>0)]
housing2 = housing2[(housing2.sqfeet < 3000) & (housing2.sqfeet>0)]

sns.scatterplot(housing2['sqfeet'], housing2['price'])
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_toomany.webp)

Ahora realmente podemos ver la mayor parte de los puntos de nuestro conjunto de datos. Sin embargo, todavía hay tantos puntos aquí que están todos impresos uno encima del otro. Esto significa que no podemos visualizar la densidad de los puntos y por tanto la relación global entre precio y superficie.

## Visualizando muchos puntos de datos

Cuando hay demasiados puntos de datos para visualizar, una cosa que podemos hacer es tomar un subconjunto aleatorio de datos. Esto significará menos puntos y, debido a que es un subconjunto aleatorio, aún debería poder generalizarse aproximadamente al conjunto de datos completo. Intentemos usar un 5% aleatorio de los datos:

```python
perc = 0.05
housing_sub = housing2.sample(n = int(housing2.shape[0]*perc))

sns.scatterplot(housing_sub['sqfeet'], housing_sub['price'])
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_subplot.webp)

Todavía hay mucha superposición, pero en realidad podemos ver la asociación lineal positiva entre área y precio que era difícil de visualizar originalmente.

Todavía podemos mejorar esto. Podemos intentar hacer cada punto más pequeño para ver mejor los lugares con mayor concentración de puntos trazados:

```python
sns.scatterplot(housing_sub['sqfeet'], housing_sub['price'], s = 5)
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_subplot_smaller.webp)

Este gráfico es mejor que el anterior porque, de un vistazo, podemos ver la mayor concentración de puntos en el sqfeetrango de 500 a 1500 y en el rango de 500 a 2000 price. Sin embargo, esto todavía no nos da una idea clara de cuántos puntos hay en este grupo intermedio. En lugar de trazar los puntos más pequeños, es posible que deseemos hacerlos más transparentes. De esta forma, podemos interpretar la intensidad del color para comprender la superposición:

```python
sns.scatterplot(housing_sub['sqfeet'], housing_sub['price'], alpha = 0.2)
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_subplot_alpha.webp)

Podemos ver que la sección inferior del gráfico es más oscura que la sección superior. Esto se debe a que muchos más puntos se superponen entre sí en los priceniveles inferiores y a menos puntos en general a medida que priceaumentan.

También podríamos considerar trazar un LOWESS (Suavizado de diagrama de dispersión ponderado localmente) más suave sobre nuestros puntos de datos. Esto dibujará una línea a través del precio promedio aproximado para cada valor de sqfeet:

```python
sns.lmplot(x='sqfeet', y='price', data = housing_sub, line_kws={'color': 'black'}, lowess=True)
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_subplot_lm.webp)

Aunque los puntos individuales son más difíciles de leer, la línea nos brinda información sobre la relación entre estas dos características.

## Visualización de variables discretas

Digamos que queremos observar la relación entre bedsy bathsen nuestro conjunto de datos. Podemos trazar fácilmente el diagrama de dispersión:

```python
sns.scatterplot('beds', 'baths', data = housing_sub)
```

![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_discrete.webp)


Si bien este gráfico nos indica cada combinación de número de camas y baños en nuestro conjunto de datos, no nos dice cuántas observaciones hay. Esto se debe a que ambas características son valores discretos , lo que en este caso significa que están limitados a números enteros bedsy medios números para bath. Entonces, cada punto de datos que representa 3 dormitorios y 2 baños se traza exactamente en el mismo lugar que los demás, superponiéndose perfectamente para que parezca un solo punto.

Agregar un jitter ajusta la distribución de puntos a lo largo de uno (o ambos) ejes para ver más fácilmente algunos puntos que hay en cada grupo:

sns.lmplot('beds', 'baths', data = housing_sub, x_jitter = .15, y_jitter = .15, fit_reg = False)


![Serie temporal](https://fer78docs.github.io/assets/images/scatterplot_discrete_jitter.webp)


Podemos mirar esta trama y aprender mucho más que la anterior. Por ejemplo, sabemos que hay menos puntos en cada bathnivel cuando bedses igual a 6 que a 5.

## Transformación de registros

A veces, cuando los datos están en una escala logarítmica , puede resultar difícil visualizar la distribución de los valores. Las características con valores positivos que están muy sesgados a la derecha son los principales candidatos para la transformación logarítmica. Veamos la distribución de pricenuestro conjunto de datos:

```python
sns.displot(housing.price)
```

![Serie temporal](https://fer78docs.github.io/assets/images/distribution.webp)

Aquí podemos ver un pico alto en el lado izquierdo y una cola derecha muy larga a lo largo del eje x. Si bien podríamos intentar reducir los pricevalores como antes, podría ser beneficioso intentar trazar la distribución del precio de los troncos:

```python
log_price = housing.price[housing.price>0]
log_price = np.log(log_price)
sns.displot(log_price)
plt.xlabel('log price')
```

![Serie temporal](https://fer78docs.github.io/assets/images/distribution_log.webp)

Este histograma proporciona mucha más información que los datos en el formato original. Incluso podemos limitar el gráfico a entre 5 y 10 para ver la distribución más claramente:

```python
sns.displot(log_price)
plt.xlabel('log price')
plt.xlim(5,10)
```

![Serie temporal](https://fer78docs.github.io/assets/images/distribution_log_limited.webp)

Este gráfico indica que el precio de los troncos es unimodal y tiene una distribución aproximadamente normal. Este es un conocimiento útil si queremos construir un modelo para predecir precios en el futuro.

Conclusión
Hacer visualizaciones de datos interpretables no siempre es tan fácil como simplemente trazar todos los datos. A menudo, las visualizaciones requieren algunos pasos adicionales, como agitar, hacer que los puntos sean más pequeños o más opacos o transformar los datos. Seguir estos pasos le ayudará a realizar visualizaciones más dinámicas e interpretables en el futuro.

