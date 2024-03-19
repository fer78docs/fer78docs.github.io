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

```
- P ( A  o  B )
```

Podemos visualizar este cálculo de la siguiente manera:

![Line Chart](https://fer78docs.github.io/assets/images/addition-rule-independent-venndiagram.gif)

Esta animación ofrece una representación visual de la fórmula de la regla de suma, que es:

```
- P(A o B) = P(A) + P(B) − P(A y B)
```

Restamos la intersección de los eventos A y B porque se incluye dos veces en la suma de P(A) y P(B) .

¿Qué pasa si los eventos son mutuamente excluyentes? En una sola tirada de dado, si el evento A es que la tirada es menor o igual a 2 y el evento B es que la tirada es mayor o igual a 5, entonces los eventos A y B no pueden suceder ambos.

Para eventos mutuamente excluyentes, la fórmula de la regla de suma es:

```
-  P(A o B) = P(A) + P(B)
```

Esto se debe a que la intersección está vacía, por lo que no necesitamos eliminar ninguna superposición entre los dos eventos.

Ejemplo: 

función `prob_a_or_b()` que calcula la regla de la suma. Se necesita de tres argumentos:

- a: un evento con posibles resultados representados como un conjunto
- b: un evento con posibles resultados representados como un conjunto
- all_possible_outcomes: un conjunto que representa todos los resultados posibles de un espacio muestral

En `prob_a_or_b()`, se ha calculado la probabilidad de a y b así como la probabilidad de su intersección en las siguientes variables:

- `rob_a`
- `prob_b`
- `prob_inter`

```python
def prob_a_or_b(a, b, all_possible_outcomes):
  # probability of event a
  prob_a = len(a)/len(all_possible_outcomes)
	
	# probability of event b
  prob_b = len(b)/len(all_possible_outcomes)
	
	# intersection of events a and b
  inter = a.intersection(b)
	
	# probability of intersection of events a and b
  prob_inter = len(inter)/len(all_possible_outcomes)
	
	# add return statement here
  return (prob_a + prob_b) - prob_inter

# Conjuntos de variables para llamar: 

# rolling a die once and getting an even number or an odd number
evens = {2, 4, 6}
odds = {1, 3, 5}
all_possible_rolls = {1, 2, 3, 4, 5, 6}

# rolling a die once and getting an odd number or a number greater than 2
odds = {1, 3, 5}
greater_than_two = {3, 4, 5, 6}
all_possible_rolls = {1, 2, 3, 4, 5, 6}

# selecting a diamond card or a face card from a standard deck of cards
diamond_cards = {'ace_diamond', '2_diamond', '3_diamond', '4_diamond', '5_diamond', '6_diamond', '7_diamond', '8_diamond', '9_diamond', '10_diamond', 'jack_diamond', 'queen_diamond', 'king_diamond'}

face_cards = {'jack_diamond', 'jack_spade', 'jack_heart', 'jack_club', 'queen_diamond', 'queen_spade', 'queen_heart', 'queen_club', 'king_diamond', 'king_spade', 'king_heart', 'king_club'}

# all cards in a deck representing the entire sample space
all_possible_cards = {'ace_diamond', '2_diamond', '3_diamond', '4_diamond', '5_diamond', '6_diamond', '7_diamond', '8_diamond', '9_diamond', '10_diamond', 'jack_diamond', 'queen_diamond', 'king_diamond', 'ace_heart', '2_heart', '3_heart', '4_heart', '5_heart', '6_heart', '7_heart', '8_heart', '9_heart', '10_heart', 'jack_heart', 'queen_heart', 'king_heart', 'ace_spade', '2_spade', '3_spade', '4_spade', '5_spade', '6_spade', '7_spade', '8_spade', '9_spade', '10_spade', 'jack_spade', 'queen_spade', 'king_spade', 'ace_club', '2_club', '3_club', '4_club', '5_club', '6_club', '7_club', '8_club', '9_club', '10_club', 'jack_club', 'queen_club', 'king_club'}

```
