---
layout: default
title: La probabilidad condicional
nav_order: 5
parent: Probability Rules
grand_parent: Probability

# La probabilidad condicional

Si queremos calcular la probabilidad de que ocurran un par de eventos dependientes, debemos definir la **probabilidad condicional**. Usando una bolsa de canicas como ejemplo, recordemos la definición de eventos dependientes:

Si sacamos dos canicas de una bolsa de cinco canicas sin reemplazo, la probabilidad de que la segunda canica sea roja depende del color de la primera. Tenemos un nombre especial para esto: probabilidad condicional. En resumen, la probabilidad condicional mide la probabilidad de que ocurra un evento, dado que ya ha ocurrido otro.

Notacionalmente, denotamos la palabra "dado" con una línea vertical. Por ejemplo, si queremos representar la probabilidad de que elijamos una canica roja dado que la primera canica es azul, podemos escribir:

```
P (Rojo Segundo ∣ Azul primero)
```

Del diagrama anterior sabemos que:

```
P (Rojo Segundo ∣ Azul primero )= 3/4
```
​
¿Qué pasaría si escogiéramos dos canicas con reemplazo? ¿Cómo es la probabilidad condicional? Bueno, pensemos en esto. Independientemente de qué canica escojamos primero, se devolverá a la bolsa. Por lo tanto, la probabilidad de sacar una canica roja o una canica azul en segundo lugar no se ve afectada por el primer resultado.

Por tanto, para eventos independientes, podemos decir lo siguiente:

```
P(A ∣ B) = P(A)
PAG(B ∣ A) = P(B)
```

En el enlace: 

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/marble-count/index.html) 

Hay un subprograma que contiene una bolsa de canicas azules y naranjas. Cuando haces clic en cualquier canica, se retira de la bolsa y se actualiza la probabilidad de seleccionar cualquiera de los colores.

Saca dos canicas azules de la bolsa. ¿Cuál es la probabilidad de seleccionar al azar una canica naranja ahora? ¿Aumentó o disminuyó?

Restablezca el subprograma haciendo clic en el Resetbotón. Retire una canica azul y una canica naranja ahora. ¿Aumentó o disminuyó aleatoriamente la probabilidad de seleccionar una canica azul? ¿Aumentó o disminuyó aleatoriamente la probabilidad de seleccionar una canica naranja?