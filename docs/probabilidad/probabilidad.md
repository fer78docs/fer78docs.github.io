---
layout: default
title: Probabilidad
nav_order: 3
has_children: true
---

# Probabilidad, teoría de conjuntos y ley de los grandes números

## Probabilidad
La probabilidad es una rama de las matemáticas que nos permite cuantificar la incertidumbre. En nuestra vida diaria, a menudo utilizamos la probabilidad para tomar decisiones, ¡incluso sin pensar en ello!

Por ejemplo, muchos informes meteorológicos dan un porcentaje de probabilidad de que llueva. Si escuchamos que hay un 80 por ciento de posibilidades de lluvia, probablemente no hagamos muchos planes afuera. Sin embargo, si solo hay un 5 por ciento de probabilidad de lluvia, podemos sentirnos cómodos planeando un picnic.

En este artículo, vamos a sentar las bases para comprender la probabilidad. Para ello, vamos a explorar un campo de las matemáticas llamado teoría de conjuntos .

## Teoría de conjuntos

La teoría de conjuntos es una rama de las matemáticas que se basa en el concepto de conjuntos . En términos simples, un conjunto es una colección de cosas. Por ejemplo, podemos usar un conjunto para representar elementos en una mochila. Podríamos tener:

*{ Libro ,​​​Papel ,​​​​carpeta ,​​​​​Sombrero ,​​Bolígrafo ,​​Bocadillo }​​​​*

En particular, los matemáticos suelen representar conjuntos con llaves. Los conjuntos también siguen dos reglas clave:
* Cada elemento de un conjunto es distinto.
* Los elementos de un conjunto no siguen ningún orden particular.

Por tanto, podemos decir:

* *{ 1 ,2 ,3 ,4 ,5 }={ 5 ,3 ,2 ,4 ,1 }*

Al definir un conjunto, solemos utilizar una letra mayúscula. Por ejemplo:

* *A={ 1 ,2 ,3 ,4 ,5 }*

Los conjuntos también pueden contener subconjuntos . El conjunto A es un subconjunto del conjunto B si todos los elementos de A existen dentro de B. Por ejemplo:

* *A={ 1 ,2 ,3 }*  
* *B={ 1 ,2 ,3 ,4 ,5 }*
​

Aquí, el conjunto A es un subconjunto de B porque todos los elementos de A están contenidos dentro de B.

### Experimentos y espacios muestrales

En probabilidad, un experimento es algo que produce observaciones con cierto nivel de incertidumbre. Un punto de muestra es un único resultado posible de un experimento. Finalmente, un espacio muestral es el conjunto de todos los puntos muestrales posibles para un experimento.

Por ejemplo, supongamos que realizamos un experimento en el que lanzamos una moneda dos veces y registramos si cada lanzamiento da como resultado cara o cruz. Hay cuatro puntos de muestra en este experimento: dos caras ( HH ), cruces y luego caras (TH), caras y luego cruces (HT), o dos cruces (TT). Podemos escribir el espacio muestral completo para este experimento de la siguiente manera:

* *S={ S.S ,​TT ,​HT ,​T H }*  

Supongamos que estamos interesados ​​en la probabilidad de un resultado específico: HH . Un resultado específico (o conjunto de resultados) se conoce como evento y es un subconjunto del espacio muestral. Tres eventos que podríamos observar en este espacio muestral son:

* Obtener dos cabezas: *A={ S.S }​*  
* Obtener dos colas: *B={ TT }​*
* Obtener cara y cruz: *C={ HT ,​T H }*

La definición frecuentista de probabilidad es la siguiente: si realizamos un experimento una cantidad infinita de veces, la probabilidad de cada evento es la proporción de veces que ocurre. Desafortunadamente, no tenemos la capacidad de lanzar dos monedas una cantidad infinita de veces, pero podemos estimar las probabilidades eligiendo algún otro número grande, como 1000. ¡Intentémoslo!

Bien, hemos lanzado dos monedas 1000 veces. ¿No fue DIVERTIDO? Aquí están cada uno de los resultados y la cantidad de veces que observamos cada uno:

* {HH} : 252
* {TT} : 247
* {HT} : 256
* {TH} : 245

Para calcular la probabilidad estimada de cualquier resultado, utilizamos la siguiente fórmula:
​
* P(evento)​​​​= Número de veces que ocurrió el evento / Número total de ensayos

​En este escenario, una prueba es una ejecución única de nuestro experimento (dos lanzamientos de moneda). Entonces, la probabilidad de obtener dos caras en dos lanzamientos de moneda es aproximadamente:

* P(HH) = 250 / 1000 = 0.252

Con base en estas 1000 pruebas, estimaríamos que hay un 25,2 por ciento de posibilidades de obtener dos caras en dos lanzamientos de moneda. ¡Esto es genial! Sin embargo, si hacemos este mismo procedimiento una y otra vez, es posible que obtengamos resultados ligeramente diferentes. Por ejemplo, si repetimos el experimento otras 1.000 veces, es posible que obtengamos dos cabezas sólo el 24,2 por ciento de las veces.

Si queremos sentirnos seguros de que estamos cerca de la probabilidad real de un evento en particular, podemos aprovechar la ley de los grandes números .

## Ley de los grandes números

No podemos repetir nuestro experimento aleatorio una cantidad infinita de veces (¡por más DIVERTIDO que sería!). Sin embargo, todavía podemos lanzar ambas monedas un gran número de veces. A medida que lanzamos ambas monedas más y más, la proporción observada de veces que ocurre cada evento convergerá a su verdadera probabilidad. Esto se llama ley de los grandes números .

Observemos la ley de los grandes números en tiempo real. Usaremos Python para simular lanzar ambas monedas tantas veces como queramos y veremos cómo la proporción de dos caras converge a su verdadera probabilidad.

Repasemos cada parte del código a continuación, paso a paso. No necesita preocuparse por cada línea de código, pero comprender el objetivo general le ayudará a comprender mejor la probabilidad.

*Pregunta de codificacion*

En el editor de código a continuación, hemos escrito una función llamada `coin_flip_experiment()` que simula lanzar dos monedas justas. Usando un bucle for,  ejecutamos `coin_flip_experiment()` un número específico de veces. A medida que este ciclo se repite, rastreamos la frecuencia con la que ambas monedas salen cara. Finalmente, usando `matplotlib`, trazamos la proporción de experimentos que resultan en dos cabezas después de cada prueba.

El número de veces `coin_flip_experiment()` que se ejecuta está determinado por la `num_trials` variable en la línea 21. Actualmente, esta variable está configurada en 5. Ejecute el programa varias veces. En el gráfico resultante, la línea horizontal naranja es la probabilidad real de observar dos cabezas (0,25). La línea azul es la proporción de cabezas que vemos a lo largo de nuestras pruebas. ¿Qué notas sobre la línea azul después de cada carrera?

Deberías ver que la proporción de dos caras después de cinco intentos es inconsistente. En algunos experimentos, es posible que veamos cero observaciones de dos cabezas, mientras que en otros, podemos ver que casi las cinco observaciones son dos cabezas. Para simular la ley de los grandes números, necesitamos hacer más pruebas. Establezca la variable `num_trials`  en diferentes valores, como los siguientes:

100
1000
100000

Toma nota de lo que observas. ¿A dónde converge la línea azul en el gráfico después de muchas pruebas?

```python
import matplotlib.pyplot as plt
import numpy as np
import codecademylib3

def coin_flip_experiment():
  # defining our two coins as lists
  coin1 = ['Heads', 'Tails']
  coin2 = ['Heads', 'Tails']
 
  # "flipping" both coins randomly
  coin1_result = np.random.choice(coin1)
  coin2_result = np.random.choice(coin2)
 
  # checking if both flips are heads
  if coin1_result == 'Heads' and coin2_result == 'Heads':
    return 1
  else:
    return 0
 
# how many times we run the experiment
num_trials = 5
prop = []
flips = []
# keep track of the number of times heads pops up twice
two_heads_counter = 0
 
# perform the experiment five times
for flip in range(num_trials):
  # if both coins are heads add 1 to the counter
  two_heads_counter += coin_flip_experiment()
  # keep track of the proportion of two heads at each flip 
  prop.append(two_heads_counter/(flip+1))
  # keep a list for number of flips
  flips.append(flip+1)
 
# plot all flips and proportion of two heads
plt.plot(flips, prop, label='Experimental Probability')
plt.xlabel('Number of Flips')
plt.ylabel('Proportion of Two Heads')

plt.hlines(0.25, 0, num_trials, colors='orange', label='True Probability')
plt.legend()
plt.show()
```

Después de establecer la variable `num_trials` con números grandes, vemos que la proporción de ensayos que resultan en dos caras converge a 0,25. La línea horizontal en y=0,25 queda completamente cubierta después de unos cien mil giros. Al simular una gran cantidad de lanzamientos en Python, hemos demostrado que la probabilidad real de ver dos caras en dos lanzamientos de monedas separados es igual a 0,25.