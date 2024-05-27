---
layout: default
title: Regular Expressions
nav_order: 8
parent: Exploratory Data Analysis
---


## Literales

El texto más simple que podemos relacionar con expresiones regulares son los literales. Aquí es donde nuestra expresión regular contiene el texto exacto que queremos hacer coincidir. La expresión regular a, por ejemplo, coincidirá con el texto a, y la expresión regular bananas coincidirá con el texto bananas.

Además, podemos hacer coincidir solo una parte de un fragmento de texto. Quizás estemos buscando algún documento para ver si aparece la palabra monkey, ya que amamos a los monos. Podríamos usar la expresión regular monkey para hacer coincidir con el fragmento de texto The monkeys like to eat bananas.

No solo podemos unir caracteres alfabéticos: ¡los dígitos también funcionan! ¡La expresión regular 3 coincidirá con 3 el fragmento de texto 34 y la expresión regular 5 gibbons coincidirá completamente con el texto 5 gibbons!

Las expresiones regulares funcionan moviendo carácter por carácter, de izquierda a derecha, a través de un fragmento de texto. Cuando la expresión regular encuentra un carácter que coincide con la primera parte de la expresión, busca una secuencia continua de caracteres coincidentes.

## Alternancia

¿Te encantan los babuinos y los gorilas? ¡Puedes encontrar cualquiera de ellos con la misma expresión regular usando alternancia! La alternancia, realizada en expresiones regulares con el símbolo de barra vertical, \|nos permite hacer coincidir los caracteres que preceden \|O los caracteres posteriores a \|. La expresión regular baboons \|gorillas coincidirá baboons en el texto `I love baboons`, pero también coincidirá gorillas en el texto `I love gorillas`.

¿Estás pensando en cómo hacer coincidir todo el texto I love baboons o I love gorillas? ¡Llegaremos a eso más adelante!

## Conjuntos de caracteres

Los exámenes de ortografía pueden parecer un recuerdo lejano de la escuela primaria, pero en última instancia los realizamos todos los días mientras escribimos. Es fácil cometer errores en palabras comúnmente mal escritas como consensus y, además, a veces hay grafías alternativas para la misma palabra.

Los conjuntos de caracteres , indicados por un par de corchetes [], nos permiten hacer coincidir un carácter de una serie de caracteres, lo que permite coincidencias con ortografía incorrecta o diferente.

La expresión regular con[sc]en[sc]us coincidirá con consensusla ortografía correcta de la palabra, pero también coincidirá con las siguientes tres ortografías incorrectas: concensus, consencus y concencus. Las letras dentro de los primeros corchetes, sy c, son las diferentes posibilidades para el carácter que viene después cony antes en. Lo mismo ocurre con los segundos corchetes, sy cson las diferentes posibilidades de personajes que vendrán después eny antes us.

Por lo tanto, la expresión regular [cat]coincidirá con los caracteres c, oa , pero no con el texto . tcat

La belleza de los conjuntos de caracteres (y la alternancia) es que permiten que nuestras expresiones regulares se vuelvan más flexibles y menos rígidas que simplemente haciendo coincidir con literales.

Podemos hacer que nuestros conjuntos de caracteres sean aún más poderosos con la ayuda del ^símbolo de intercalación. Colocado al frente de un conjunto de caracteres, ^niega el conjunto y coincide con cualquier carácter que no esté indicado. Estos se denominan conjuntos de caracteres negados . Por lo tanto, la expresión regular [^cat]coincidirá con cualquier carácter que no sea c, a, o t y coincidirá completamente con cada carácter d, o o g .

¿Tenemos consenso en que las expresiones regulares son geniales?