---
layout: default
title: Regla de Multiplicacion
nav_order: 6
parent: Probability Rules
grand_parent: Probability
---

# Regla de multiplicación

Hemos analizado la regla de la suma, que describe la probabilidad de que ocurra un evento U otro evento (o ambos). ¿Qué pasa si queremos calcular la probabilidad de que dos eventos sucedan simultáneamente? Para dos eventos, A y B , esto es P ( A y B) o la probabilidad de la intersección de A y B.

## Formula general
La fórmula general para la probabilidad de que dos eventos ocurran simultáneamente es:

```
P ( A y B ) = P ( A ) * PAG ( B∣A )
```

Sin embargo, para eventos independientes, podemos simplificar ligeramente esta fórmula.

### Eventos dependientes

Volvamos a nuestro ejemplo de la bolsa de canicas. Tenemos cinco canicas: dos son azules y tres son rojas. Escogemos dos canicas sin reposición. ¿Qué pasa si queremos saber la probabilidad de elegir una canica azul primero Y una canica azul después?

Teniendo en cuenta la probabilidad condicional, la regla de multiplicación para estos dos eventos dependientes es:

```
P( Azul 1.º y Azul 2.º ) = P( azul 1º ) * P( azul 2.º ∣ Azul 1º )
P( Azul 1.º y Azul 2.º ) = 2/5 * 1/4
P( Azul 1.º y Azul 2.º ) = 1/10
```
Este es un resultado potencial al sacar dos canicas de la bolsa. Una forma de visualizar todos los resultados posibles de un par de eventos es un diagrama de árbol .

Los diagramas de árbol tienen las siguientes propiedades:

- Cada rama representa un conjunto específico de eventos.
- Las probabilidades de que las ramas terminales (todos los conjuntos posibles de resultados) sumen uno.
- Multiplicamos entre ramas (¡usando la regla de la multiplicación!) para calcular la probabilidad de que ocurra cada rama (conjunto de resultados).

¡En el navegador de la derecha podrás jugar con uno en este enlace: 

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/tree-diagram/tree.html)

## Eventos independientes

Para dos eventos independientes, la regla de la multiplicación se vuelve menos complicada. La probabilidad de que ocurran dos eventos independientes es:

```
P(A y B) = P(A) * P(B)
```
Esto se debe a que lo siguiente es cierto para eventos independientes:
```
P(B ∣ A ) = P(B)
```
Veamos el ejemplo más sencillo: lanzar dos veces una moneda justa. El evento A es que obtenemos cruz en el primer lanzamiento, y el evento B es que obtenemos cruz en el segundo lanzamiento. P(A) = P(B) = 0.5 , entonces según nuestra fórmula, la probabilidad de obtener cruz en ambos lanzamientos sería:

```
P(B y A ) = 0.5 * 0.5 = 0.25
```


<hr>

El subprograma del enlace hay un diagrama de árbol y diez canicas azules y naranjas debajo del diagrama de árbol (es posible que deba desplazarse hacia abajo para ver las canicas). Si haces clic en una de las canicas, el diagrama de árbol se completará según lo que hayas seleccionado. 

Después de seleccionar dos canicas, aparecerá una ecuación para la regla del producto encima de las canicas. 

El número de canicas naranjas y azules se aleatoriza cada vez que golpeas Reset, por lo que verás muchos valores diferentes para prob1 , prob2 y final_prob .

Pruebe todos los resultados posibles y observe el diagrama de árbol en consecuencia:

[Enlace al programa](https://static-assets.codecademy.com/skillpaths/master-stats-ii/intro-probability/tree-diagram/tree.html)

<hr>

Hemos introducido la probabilidad condicional como parte de la regla de multiplicación para eventos dependientes. Sin embargo, profundicemos un poco más en él, ya que es una poderosa herramienta de probabilidad que tiene aplicaciones en el mundo real.

Para este problema, seguiremos el diagrama de árbol de la derecha.

Supongamos que lo siguiente es cierto (esto se muestra en el primer conjunto de ramas del diagrama):

- El 20 por ciento de la población tiene faringitis estreptocócica.
- El 80 por ciento de la población no tiene faringitis estreptocócica.

Ahora supongamos que hacemos pruebas a un grupo de personas para detectar faringitis estreptocócica. Los posibles resultados de estas pruebas se muestran en el siguiente conjunto de ramas:

- Si una persona tiene faringitis estreptocócica, hay un 85% de posibilidades de que su prueba sea positiva y un 15% de posibilidades de que sea negativa. Esto está etiquetado como:

```
P(+|ST) = 0.85
P(-|ST) = 0.15
```

- Si una persona no tiene faringitis estreptocócica, hay un 98% de posibilidades de que su prueba sea negativa y un 2% de posibilidades de que sea positiva. Esto se puede etiquetar como:

```
P(+|NO ST) = 0.98
P(-|NO ST) = 0.02
```

Finalmente, veamos los cuatro posibles pares de resultados que forman las ramas terminales de nuestro diagrama:

```
P (ST and + ) = 0.1 7
P (ST and - ) = 0.0 3
P (NO ST and + ) = 0.0 1 6
P (NO ST and - ) = 0.7 8 4
```


En conjunto, estos suman uno, ya que capturan todos los resultados potenciales después de que se realizan las pruebas a los pacientes.

Es genial que tengamos toda esta información. Sin embargo, nos falta algo. Si alguien obtiene un resultado positivo, ¿cuál es la probabilidad de que tenga faringitis estreptocócica? Notacionalmente, podemos escribir esta probabilidad como:


```
P (ST ∣ +)
```

En el siguiente ejercicio, exploraremos cómo podemos usar nuestro diagrama de árbol para calcular esta probabilidad.

