---
layout: default
title: Asociaciones dos categoricas
nav_order: 4
parent: Exploratory Data Analysis
---

# Asociaciones: dos variables categoricas

Para tradajar este tema exploraremos una muestra de datos del Inventario de Personalidad Narcisista (NPI-40), una prueba de personalidad con 40 preguntas sobre preferencias personales y visión de uno mismo. Hay dos posibles respuestas a cada pregunta. El ejemplo con el que trabajaremos contiene respuestas a lo siguiente:

* `influence:` yes= Tengo un talento natural para influir en las personas; no= No soy bueno para influir en las personas.
* `blend_in:` yes= Prefiero mezclarme con la multitud; no= Me gusta ser el centro de atención.
* `special:` yes= Creo que soy una persona especial; no= No soy mejor ni peor que la mayoría de las personas.
* `leader:` yes= Me veo como un buen líder; no= No estoy seguro de ser un buen líder.
* `authority:` yes= Me gusta tener autoridad sobre otras personas; no= No me importa seguir órdenes.

Como puedes imaginar, las respuestas a algunas de estas preguntas están asociadas. Por ejemplo, si sabemos si alguien se considera un buen líder, también podemos descubrir que es más probable que le guste tener autoridad. En esta lección aprenderemos cómo evaluar si existe una asociación entre dos de estas variables.

## Tablas de Contingencia de Frecuencias

Las tablas de contingencia, también conocidas como tablas de doble entrada o tabulaciones cruzadas, son útiles para resumir dos variables al mismo tiempo. Por ejemplo, supongamos que estamos interesados ​​en comprender si existe una asociación entre influence(si una persona cree que tiene talento para influir en las personas) y leader(si se ve a sí misma como un líder). Podemos usar la función crosstab de pandas para crear una tabla de contingencia:

```python
influence_leader_freq = pd.crosstab(npi.influence, npi.leader)
influence_leader_freq
# output
leader	no	yes
influence		
no	3015	1293
yes	2360	4429
```

Esta tabla nos indica el número de personas que dieron cada combinación posible de respuestas a estas dos preguntas. Por ejemplo, 2360 personas dijeron que no se ven a sí mismas como líderes pero tienen talento para influir en las personas.

Para evaluar si existe una asociación entre estas dos variables, debemos preguntarnos si la información sobre una variable nos proporciona información sobre la otra. En este ejemplo, vemos que entre las personas que no se ven a sí mismas como líderes (la primera columna), un número mayor (3015) no cree que tenga talento para influir en las personas. Mientras tanto, entre las personas que se ven a sí mismas como líderes (la segunda columna), un número mayor (4429) cree que tienen talento para influir en las personas.

Entonces, si sabemos cómo respondió alguien a la pregunta sobre liderazgo, tenemos cierta información sobre cómo es probable que responda a la pregunta sobre influencia. Esto sugiere que las variables están asociadas.

## Tablas de contingencia de proporciones

En el ejercicio anterior, analizamos una asociación entre las preguntas influence y leader utilizando una tabla de contingencia de frecuencias. Sin embargo, a veces resulta útil convertir esas frecuencias en proporciones. Podemos lograr esto simplemente dividiendo todas las frecuencias en una tabla de contingencia por el número total de observaciones (la suma de las frecuencias):

```python
influence_leader_freq = pd.crosstab(npi.influence, npi.leader)
influence_leader_prop = influence_leader_freq/len(npi)
influence_leader_prop
# output
leader	no	yes
influence		
no	0.271695	0.116518
yes	0.212670	0.399117
```

La tabla de contingencia resultante facilita un poco la comparación de la proporción de personas en cada categoría. Por ejemplo, vemos que las dos proporciones más grandes de la tabla (0,399 y 0,271) están en las celdas sí/sí y no/no de la tabla. También podemos ver que casi el 40% de la población encuestada (con mucho, la proporción más grande) se ven a sí mismos como líderes y piensan que tienen talento para influir en las personas.

## Proporciones marginales

En los ejercicios anteriores, analizamos una asociación entre las influencepreguntas leadery usando una tabla de contingencia. Vimos alguna evidencia de una asociación entre estas preguntas.

Ahora, tomemos un momento para pensar en cómo se verían las tablas si no hubiera asociación entre las variables . Nuestro primer instinto puede ser que habría 0,25 (25%) de los datos en cada una de las cuatro celdas de la tabla, pero ese no es el caso. 

Podríamos notar que la fila inferior, que corresponde a las personas que creen que tienen talento para influir en las personas, representa 0,213 + 0,399 = 0,612 (o 61,2%) de las personas encuestadas: ¡más de la mitad! Esto significa que podemos esperar proporciones más altas en la fila inferior, independientemente de si las preguntas están asociadas.

La proporción de encuestados en cada categoría de una sola pregunta se denomina proporción marginal . Por ejemplo, la proporción marginal de la población que tiene talento para influir en las personas es 0,612. Podemos calcular todas las proporciones marginales de la tabla de contingencia de proporciones usando sumas de filas y columnas de la siguiente manera:

```python
leader_marginals = influence_leader_prop.sum(axis=0)
print(leader_marginals)
print('\n')
influence_marginals =  influence_leader_prop.sum(axis=1)
print(influence_marginals)

# output
leader
no     0.484365
yes    0.515635
dtype: float64

influence
no     0.388213
yes    0.611787
dtype: float64
```

## Tablas de contingencia esperadas

En el ejercicio anterior calculamos las proporciones marginales para las preguntas leader y influence

Para entender si estas preguntas están asociadas, podemos usar las proporciones marginales para crear una tabla de contingencia de proporciones esperadas si no hubiera asociación entre estas variables . Para calcular estas proporciones esperadas, necesitamos multiplicar las proporciones marginales para cada combinación de categorías:


|               | líder = no                       | líder = sí                       |
|---------------|----------------------------------|----------------------------------|
| influencia = no | 0,484 * 0,388 = 0,188          | 0,516 * 0,388 = 0,200          |
| influencia = sí | 0,484 * 0,612 = 0,296          | 0,516 * 0,612 = 0,315          |

Estas proporciones luego se pueden convertir a frecuencias multiplicando cada una por el tamaño de la muestra (11097 para estos datos):

|               | líder = no                 | líder = sí                 |
|---------------|----------------------------|----------------------------|
| influencia = no | 0,188 * 11097 = 2087    | 0,200 * 11097 = 2221    |
| influencia = sí | 0,296 * 11097 = 3288    | 0,315 * 11097 = 3501    |

Esta tabla nos dice que si no hubiera asociación entre las preguntas leadery influence, esperaríamos que 2087 personas respondieran no a ambas.

En Python, podemos calcular esta tabla usando la función `chi2_contingency()` de `SciPy`, pasando la tabla de frecuencia observada. En realidad, hay cuatro resultados de esta función, pero por ahora, solo veremos el cuarto:

```python
from scipy.stats import chi2_contingency

chi2, pval, dof, expected = chi2_contingency(influence_leader_freq)
print(np.round(expected))
# output
[[2087. 2221.]
 [3288. 3501.]]
 ```

Tenga en cuenta que la función `ScyPy` arrojó las mismas frecuencias esperadas que calculamos "a mano" anteriormente. Ahora que tenemos la tabla de contingencia esperada, si no hay asociación, podemos compararla con nuestra tabla de contingencia observada:

leader       no   yes
influence            
no         3015  1293
yes        2360  4429

Cuanto más difieran las tablas esperadas y observadas, más seguros podremos estar de que las variables están asociadas. En este ejemplo, vemos algunas diferencias bastante grandes (por ejemplo, 3015 en la tabla observada en comparación con 2087 en la tabla esperada). Esto proporciona evidencia adicional de que estas variables están asociadas.

## La estadística de chi-cuadrado

En el ejercicio anterior, calculamos una tabla de contingencia de frecuencias esperadas si no hubiera asociación entre las preguntas leader y influence. Luego comparamos esto con la tabla de contingencia observada. Debido a que las tablas parecían algo diferentes, llegamos a la conclusión de que las respuestas a estas preguntas probablemente estén asociadas.

Si bien podemos inspeccionar estas tablas visualmente, muchos científicos de datos utilizan la estadística Chi-Cuadrado para resumir cuán diferentes son estas dos tablas. Para calcular la estadística de Chi Cuadrado, simplemente encontramos la diferencia al cuadrado entre cada valor en la tabla observada y su valor correspondiente en la tabla esperada, y luego dividimos ese número por el valor de la tabla esperada; Finalmente suma esos números. La estadística Chi-Cuadrado también es el primer resultado de la función SciPy chi2_contingency():

```python
chi2, pval, dof, expected = chi2_contingency(influence_leader_freq)
print(chi2)
# output
1307.8836807573769
```

La interpretación del estadístico Chi-Cuadrado depende del tamaño de la tabla de contingencia. Para una tabla de 2x2 (como la que hemos estado investigando), una estadística de Chi-cuadrado mayor que alrededor de 4 sugeriría fuertemente una asociación entre las variables . En este ejemplo, nuestra estadística Chi-Cuadrado es mucho mayor que eso: ¡1307,88! Esto se suma a nuestra evidencia de que las variables están altamente asociadas.