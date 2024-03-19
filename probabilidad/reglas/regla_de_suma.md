---
layout: default
title: Regla de suma
nav_order: 4
parent: Reglas de la probabilidad
grand_parent: Probabilidad
---

# Regla de suma

Ahora es el momento de aplicar estos conceptos para calcular probabilidades.

Volvamos a uno de nuestros primeros ejemplos: el evento A es lanzar un número impar en un dado de seis caras y el evento B es lanzar un número mayor que dos. ¿Qué pasa si queremos encontrar la probabilidad de que ocurran uno o ambos eventos? Esta es la probabilidad de la unión de A y B :

- P ( A  o  B )

Podemos visualizar este cálculo de la siguiente manera:

![Line Chart](https://fer78docs.github.io/assets/images/addition-rule-independent-venndiagram.gif)

Esta animación ofrece una representación visual de la fórmula de la regla de suma, que es:

- P(A o B)=P ( A ) + P(B) − P(A y B)

Restamos la intersección de los eventos A y B porque se incluye dos veces en la suma de P(A) y P(B) .

¿Qué pasa si los eventos son mutuamente excluyentes? En una sola tirada de dado, si el evento A es que la tirada es menor o igual a 2 y el evento B es que la tirada es mayor o igual a 5, entonces los eventos A y B no pueden suceder ambos.

Para eventos mutuamente excluyentes, la fórmula de la regla de suma es:

-  P(A o B) = P(A) + P(B)

Esto se debe a que la intersección está vacía, por lo que no necesitamos eliminar ninguna superposición entre los dos eventos.