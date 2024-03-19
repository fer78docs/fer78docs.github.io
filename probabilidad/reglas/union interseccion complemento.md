---
layout: default
title: Union, Interseccion y complementos
nav_order: 1
parent: Reglas de la probabilidad
grand_parent: Probabilidad
---

# Unión, Intersección y Complemento

Profundicemos en algunos conceptos clave que usaremos a lo largo de esta lección: *unión* , *intersección* y *complemento* .

## Unión
La unión de dos conjuntos engloba cualquier elemento que exista en uno o en ambos. Podemos representar esto visualmente como un diagrama de Venn .

![Diagrama de Venn](https://fer78docs.github.io/assets/images/diagrama_venn.png)

Por ejemplo, digamos que tenemos dos conjuntos, A y B. 
* A representa lanzar un número impar con un dado de seis caras (el conjunto {1, 3, 5} ). 
* B representa sacar un número mayor que dos (el conjunto {3, 4, 5, 6}) . 

La unión de estos dos conjuntos sería todo en el conjunto A , el conjunto B o ambos: {1, 3, 4, 5, 6} . Podemos escribir la unión de dos eventos matemáticamente como (A o B) .

![Union de conjuntos](https://fer78docs.github.io/assets/images/union-ayb.png)

## Intersección
La intersección de dos conjuntos abarca cualquier elemento que exista en ambos conjuntos. Visualmente:

![interseccion de conjuntos](https://fer78docs.github.io/assets/images/interseccion_ayb.png)

La intersección de los conjuntos anteriores (A representa sacar un número impar en un dado de seis caras y B representa sacar un número mayor que dos) incluye cualquier valor que aparezca en ambos conjuntos: {3, 5} . Podemos escribir matemáticamente la intersección de dos eventos como (A y B).


## Complementar
Por último, el complemento de un conjunto consta de todos los resultados posibles fuera del conjunto. Visualmente:

![Complementos de A](https://fer78docs.github.io/assets/images/complemento_dea.png)

Considere el conjunto A del ejemplo anterior (lanzando un número impar en un dado de 6 caras). El complemento de este conjunto sería sacar un número par: {2, 4, 6} . Podemos escribir el complemento del conjunto A como A C . Una característica clave de los complementos es que un conjunto y su complemento cubren todo el espacio muestral. En este ejemplo de tirada de dado, el conjunto de números pares e impares cubriría todas las tiradas posibles: {1, 2, 3, 4, 5, 6} .

**Ejemplo 1:**

Interseccion y union de dos eventos:

```
A = {1, 2, 3}
B = {1, 2, 3, 4, 6}
```

Interseccion: 

![interseccion](https://fer78docs.github.io/assets/images/interseccion_evento_ejemplo.png)

Union: 

![union](https://fer78docs.github.io/assets/images/union_ejemplo_1.png)


Complemento de A:

![union](https://fer78docs.github.io/assets/images/complemento_A.png)

Complemento de B:

![union](https://fer78docs.github.io/assets/images/complemento_B.png)


**Ejemplo 2:**

Interseccion y union de dos eventos:

```
A = {5}
B = {2, 3, 4, 5, 6}
```

Interseccion: 

![interseccion](https://fer78docs.github.io/assets/images/interseccion_ejemplo2.png)

En el siguinete enlace hay un programa interactivo que muestra la union y la interseccion de dos eventos segun el resultado de lanzar dados: 

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/venn-diagram-draft-2/venn-diagram.html)