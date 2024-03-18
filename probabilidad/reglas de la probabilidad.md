---
layout: default
title: Reglas de la probabilidad
nav_order: 1
parent: Probabilidad
---

# Introduccion

La probabilidad es una forma de cuantificar la incertidumbre. Cuando lanzamos una moneda justa, decimos que hay un 50 por ciento de posibilidades (probabilidad = 0,5) de que salga cruz. Esto significa que si lanzamos INFINITAMENTE muchas monedas justas, la mitad de ellas saldrá cruz. De manera similar, cuando lanzamos un dado de seis caras, decimos que hay una probabilidad de 1 entre 6 de sacar un cinco.

¿Qué pasa si lanzamos una moneda con una mano y un dado con la otra al mismo tiempo? ¿Cuál es la probabilidad de que en la moneda salga cruz Y en el dado salga cinco? ¿Hay alguna manera de cuantificar la probabilidad de que AMBOS ocurran estos dos eventos diferentes? En esta lección, analizaremos diferentes reglas de probabilidad que nos ayudan a cuantificar la probabilidad de múltiples eventos aleatorios.

## Unión, Intersección y Complemento

Profundicemos en algunos conceptos clave que usaremos a lo largo de esta lección: *unión* , *intersección* y *complemento* .

### Unión
La unión de dos conjuntos engloba cualquier elemento que exista en uno o en ambos. Podemos representar esto visualmente como un diagrama de Venn .

![Diagrama de Venn](https://fer78docs.github.io/assets/images/union.png)

Por ejemplo, digamos que tenemos dos conjuntos, A y B. 
* A representa lanzar un número impar con un dado de seis caras (el conjunto {1, 3, 5} ). 
* B representa sacar un número mayor que dos (el conjunto {3, 4, 5, 6}) . 

La unión de estos dos conjuntos sería todo en el conjunto A , el conjunto B o ambos: {1, 3, 4, 5, 6} . Podemos escribir la unión de dos eventos matemáticamente como (A o B) .

![Diagrama de Venn](https://fer78docs.github.io/assets/images/union.png)

### Intersección
La intersección de dos conjuntos abarca cualquier elemento que exista en ambos conjuntos. Visualmente:

![Diagrama de Venn](https://fer78docs.github.io/assets/images/interseccion.png)

La intersección de los conjuntos anteriores (A representa sacar un número impar en un dado de seis caras y B representa sacar un número mayor que dos) incluye cualquier valor que aparezca en ambos conjuntos: {3, 5} . Podemos escribir matemáticamente la intersección de dos eventos como (A y B).


### Complementar
Por último, el complemento de un conjunto consta de todos los resultados posibles fuera del conjunto. Visualmente:

![Diagrama de Venn](https://fer78docs.github.io/assets/images/complemento.png)

Considere el conjunto A del ejemplo anterior (lanzando un número impar en un dado de 6 caras). El complemento de este conjunto sería sacar un número par: {2, 4, 6} . Podemos escribir el complemento del conjunto A como A C . Una característica clave de los complementos es que un conjunto y su complemento cubren todo el espacio muestral. En este ejemplo de tirada de dado, el conjunto de números pares e impares cubriría todas las tiradas posibles: {1, 2, 3, 4, 5, 6} .