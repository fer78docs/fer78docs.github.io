---
layout: default
title: Random Variables 
nav_order: 1
parent: Intro Probability Distributions
grand_parent: Probability
---

## Variables aleatorias
Una variable aleatoria es, en su forma más simple, una función. En probabilidad, a menudo utilizamos variables aleatorias para representar eventos aleatorios. Por ejemplo, podríamos usar una variable aleatoria para representar el resultado de una tirada de dado: cualquier número entre uno y seis.

Las variables aleatorias deben ser numéricas, lo que significa que siempre toman un número en lugar de una característica o cualidad. Si queremos usar una variable aleatoria para representar un evento con resultados no numéricos, podemos elegir números para representar esos resultados. Por ejemplo, podríamos representar el lanzamiento de una moneda como una variable aleatoria asignando a “cara” un valor de 1 y a “cruz” un valor de 0.

En esta lección, usaremos `random.choice(a, size = size, replace = True/False)`de la biblioteca `numpy` para simular variables aleatorias en Python. En este método:

- `a` es una lista u otro objeto que tiene valores de los que estamos tomando muestras
- `size` es un número que representa cuántos valores elegir
- `replace` puede ser igual a `True` o `False` y determina si mantenemos un valor adespués de dibujarlo `(replace = True)` o lo eliminamos del grupo `(replace = False)`.

El siguiente código simula el resultado de lanzar un dado justo dos veces usando `np.random.choice()`:

```python
import numpy as np

# 7 is not included in the range function
die_6 = range(1, 7)

rolls = np.random.choice(die_6, size = 2, replace = True)

print(rolls)
```
output
```
[2, 5]
```

## Variables aleatorias discretas
Las variables aleatorias con un número contable de valores posibles se denominan variables aleatorias discretas. Por ejemplo, lanzar un dado normal de 6 caras se consideraría una variable aleatoria discreta porque las opciones de resultado se limitan a los números del dado.

Las variables aleatorias discretas también son comunes cuando se observan eventos de conteo, como cuántas personas ingresaron a una tienda en un día seleccionado al azar. En este caso, los valores son contables porque se limitan a números enteros (no se puede observar la mitad de una persona).

## Variables aleatorias continuas

Cuando los valores posibles de una variable aleatoria son incontables, se le llama variable aleatoria continua. Generalmente son variables de medición y no se pueden contar porque las mediciones siempre pueden ser más precisas: metros, centímetros, milímetros, etc.

Por ejemplo, la temperatura en Los Ángeles en un día elegido al azar es una variable aleatoria continua. Siempre podemos ser más precisos sobre la temperatura expandiendo a otro decimal (96 grados, 96,44 grados, 96,437 grados, etc.).
