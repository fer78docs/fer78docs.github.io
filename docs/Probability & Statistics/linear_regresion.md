---
layout: default
title: Linear Regression
nav_order: 9
parent: Probability & Statistics
---

# Regresión lineal

### Introduccion

La regresión lineal es una poderosa técnica de modelado que se puede utilizar para comprender la relación entre una variable cuantitativa y una o más variables, a veces con el objetivo de hacer predicciones. Por ejemplo, la regresión lineal puede ayudarnos a responder preguntas como:

- *¿Cuál es la relación entre el tamaño de los apartamentos y el precio de alquiler de los apartamentos en Nueva York?*
- *¿Es la altura de una madre un buen predictor de la altura adulta de su hijo?*

El primer paso antes de ajustar un modelo de regresión lineal es el análisis exploratorio de datos y la visualización de datos: ¿existe alguna relación que podamos modelar? Por ejemplo, supongamos que recopilamos las alturas (en cm) y los pesos (en kg) de 9 adultos e inspeccionamos un gráfico de altura versus peso:

```python
plt.scatter(data.height, data.weight)
plt.xlabel('height (cm)')
plt.ylabel('weight (kg)')
plt.show()
```

![Correlacion](https://fer78docs.github.io/assets/images/correlation_for.png)

Cuando miramos este gráfico, vemos que hay cierta evidencia de una relación entre la altura y el peso: las personas más altas tienden a pesar más. En los siguientes ejercicios, aprenderemos cómo modelar esta relación con una línea. Si tuvieras que trazar una línea que pasara por estos puntos para describir la relación entre altura y peso, ¿qué línea trazarías?


### Ecuación de una recta


Como su nombre lo indica, la regresión LINEar implica ajustar una línea a un conjunto de puntos de datos. Para ajustar una línea, es útil comprender la ecuación de una línea, que a menudo se escribe como $$y=mx+b$$ . En esta ecuación:

- $$x$$ e $$y$$ representan variables, como altura y peso u horas de estudio y puntuaciones de exámenes .
- $$b$$ representa la intersección y de la línea. Aquí es donde la línea se cruza con el eje y (una línea vertical ubicada en $$x = 0$$ ).
$$m$$ representa la pendiente. Esto controla qué tan pronunciada es la línea. Si elegimos dos puntos cualesquiera en una recta, la pendiente es la relación entre la distancia vertical y horizontal entre esos puntos; Esto a menudo se escribe como subir/correr.

El siguiente gráfico muestra una recta con la ecuación $$y = 2x + 12$$ :

Tenga en cuenta que también podemos tener una recta con pendiente negativa. Por ejemplo, el siguiente gráfico muestra la recta con la ecuación $$y = -2x + 8$$ :

![Ecuacion 2](https://fer78docs.github.io/assets/images/ecuacion2.png)


### Encontrar la "mejor" línea

En el último ejercicio, intentamos imaginar cómo sería la línea que mejor se ajustaría. Para elegir realmente una línea, debemos idear algunos criterios sobre lo que realmente significa "mejor".

Dependiendo de nuestros objetivos y datos finales, podríamos elegir diferentes criterios; sin embargo, una opción común para la regresión lineal son los mínimos cuadrados ordinarios (OLS). En una regresión MCO simple, asumimos que la relación entre dos variables $$x$$ e $$y$$ se puede modelar como:

$$y=mx​+b+error​​​​$$

Definimos "mejor" como la línea que minimiza el error cuadrático total para todos los puntos de datos. Este error cuadrático total se denomina función de pérdida en el aprendizaje automático. Por ejemplo, considere la siguiente trama:

![Error Cuadratico](https://fer78docs.github.io/assets/images/error_cuadratico.png)

En este gráfico, vemos dos puntos a cada lado de una línea. Uno de los puntos está una unidad debajo de la línea (etiquetada -1). El otro punto está tres unidades por encima de la línea (etiquetado como 3). El error cuadrático total (pérdida) es:

$$\text{pérdida} = (-1)^2 + (3)^2 = 1 + 9 = 10$$

Observe que elevamos al cuadrado cada distancia individual de modo que los puntos por debajo y por encima de la línea contribuyan igualmente a la pérdida (cuando elevamos al cuadrado un número negativo, el resultado es positivo). Para encontrar la línea que mejor se ajusta, necesitamos encontrar la pendiente y la intersección de la línea que minimiza la pérdida.

La visualización interactiva en el navegador le permite intentar encontrar la línea que mejor se ajuste a un conjunto aleatorio de puntos de datos:

- El control deslizante de la izquierda controla la m(pendiente)
- El control deslizante de la derecha controla la b(intercepción)

Puede ver la pérdida total en el lado derecho de la visualización. Para obtener la línea de mejor ajuste, queremos que esta pérdida sea lo más pequeña posible.

Para comprobar si obtuvo la mejor línea, marque la casilla "Trazar mejor ajuste".

Aleatoriza un nuevo conjunto de puntos e intenta ajustar una nueva línea ingresando la cantidad de puntos que deseas (¡pruébalo 8!) en el cuadro de texto y presionando Randomize Points.

Juegue con el subprograma y vea si puede encontrar la línea que mejor se ajuste a los puntos que ha aleatorizado.

[](https://content.codecademy.com/programs/data-science-path/line-fitter/line-fitter.html)

## Ajuste de un modelo de regresión lineal en Python

Hay varias bibliotecas de Python que se pueden usar para ajustar una regresión lineal, pero en este curso usaremos la función `OLS.from_formula()` de `statsmodels.api` porque usa una sintaxis simple y proporciona resúmenes completos del modelo.

Supongamos que tenemos un conjunto de datos nombrado `body_measurements` con columnas `height` y `weight`. Si queremos ajustar un modelo que pueda predecir el peso en función de la altura, podemos crear el modelo de la siguiente manera:

```python
model = sm.OLS.from_formula('weight ~ height', data = body_measurements)
```

Usamos la fórmula 'weight ~ height' porque queremos predecir `weight` (es la variable de resultado) usándo `height` como predictor. Entonces, podemos ajustar el modelo usando `.fit()`:

```python
results = model.fit()
```

Finalmente, podemos inspeccionar un resumen de los resultados usando `print(results.summary())`. Por ahora, solo veremos los coeficientes usando results.params, pero la tabla de resumen completa es útil porque contiene otra información de diagnóstico importante.

```python
print(results.params)
```

Salida:
```
Intercept   -21.67
height        0.50
dtype: float64
```

Esto nos dice que la intersección de mejor ajuste es -21.67 y la pendiente de mejor ajuste es 0.50.

**Ejemplo**:
Utilizando el conjunto de datos `students`, cree un modelo de regresión lineal que prediga el `score` del estudiante utilizando `hours_studied` como predictor y guarde el resultado en una variable denominada `model`.

```python
import pandas as pd
import statsmodels.api as sm

# Read in the data
students = pd.read_csv('test_data.csv')

# Create the model here:
model = sm.OLS.from_formula('score ~ hours_studied', data = students)
# Fit the model here:
results = model.fit()
# Print the coefficients here:
print(results.params)
```
Salida
```
Intercept        43.016014
hours_studied     9.848111
dtype: float64
```

## Usar un modelo de regresión para la predicción

Supongamos que tenemos un conjunto de datos de alturas y pesos de 100 adultos. Ajustamos una regresión lineal e imprimimos los coeficientes:

```python
model = sm.OLS.from_formula('weight ~ height', data = body_measurements)
results = model.fit()
print(results.params)
```
Salida:
```
Intercept   -21.67
height        0.50
dtype: float64
```

Esta regresión nos permite predecir el peso de un adulto si conocemos su altura. Para hacer una predicción, necesitamos reemplazar la intersección y la pendiente en nuestra ecuación de una línea. La ecuación es:

$$ peso = 0.50 * altura - 21.67$$

Para hacer una predicción, podemos introducir cualquier altura. Por ejemplo, podemos calcular que el peso esperado para una persona de 160cm de altura es de 58,33kg:

$$ peso = 0.50 * 160 - 21.67$$
$$ peso = 58.33$$

También podemos hacer este cálculo utilizando el método `.predict()` del modelo ajustado. Para predecir el peso de una persona de 160 cm de altura, primero debemos crear un nuevo conjunto de datos height igual al 160 que se muestra a continuación:

```python
newdata = {"height":[160]}
print(results.predict(newdata))
```
Salida:
```python
0      58.33
dtype: float64
```

Tenga en cuenta que obtenemos el mismo resultado (58.33) que con los otros métodos; sin embargo, se devuelve como un marco de datos.

**Ejemplo**
Continuando con el ejemplo anterior teniamos los coeficientes: 
```python
print(results.params)
```
Salida
```
Intercept        43.016014
hours_studied     9.848111
dtype: float64
```

Utilizando este modelo, ¿cuál es la puntuación prevista para un estudiante que pasó 3 horas estudiando? Podemos calcular la probabilidad utilizando la formula de la linea y el metodo `predict()`.

pred_3hr = results.params[1]*3 + results.params[0]
print(pred_3hr)

# Calculate and print `pred_5hr` here:
newdata = {"hours_studied":[5]}
pred_5hr = results.predict(newdata)
print(pred_5hr)

