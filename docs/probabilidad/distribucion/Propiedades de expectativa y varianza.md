---
layout: default
title: Propiedades de expectativa y varianza
nav_order: 8
parent: Intro Probability Distributions
grand_parent: Probability
---

# Propiedades de expectativa y varianza

Hay varias propiedades de expectativa y varianza que son consistentes en todas las distribuciones:

## Propiedades de la expectativa
- El valor esperado de dos variables aleatorias independientes es la suma de cada valor esperado por separado:
```
E(X + Y) = E(X) + E(Y)
```
Por ejemplo, si quisiéramos contar el número total de caras entre 10 lanzamientos de monedas de veinticinco centavos y 6 lanzamientos de monedas de cinco centavos, el valor esperado combinado sería 5 caras (de las monedas de veinticinco centavos) y 3 caras (de las monedas de cinco centavos), es decir, 8 caras en total.

- Multiplicar una variable aleatoria por una constante a cambia el valor esperado a multiplicado por el valor esperado de la variable aleatoria:
```
E(aX) = aE(X)
```
Por ejemplo, el número esperado de caras de 10 lanzamientos de moneda justos es 5. Si quisiéramos calcular el número de caras de este evento ejecutado 4 veces (40 lanzamientos de moneda en total), el valor esperado ahora sería 4 veces el valor esperado original. , o 20.

- Agregar una constante a a la distribución cambia el valor esperado por el valor a :

```
E(X + a) = E(X) + a
```
Digamos que se hizo una prueba y se calificó, y la nota promedio fue de 78 sobre 100 puntos. Si el maestro decidiera curvar la calificación sumando 2 puntos a la calificación de todos, el promedio ahora sería de 80 puntos.

# Propiedades de la varianza
- Incrementar los valores en una distribución por una constante a no cambia la varianza:

Esto se debe a que la varianza de una constante es 0 (no existe un rango para un solo número). Agregar una constante a una variable aleatoria no agrega ninguna varianza adicional. Tomemos el ejemplo anterior con el profesor curvando las calificaciones: aunque el valor esperado (o promedio) de la prueba cambia de 78 a 80, la extensión y dispersión (o varianza) de las puntuaciones de la prueba permanece igual.

- Al escalar los valores de una variable aleatoria mediante una constante a, se escala la varianza mediante la constante al cuadrado:
```
Var(aX) = a2Var(X)
```
- La varianza de la suma de dos variables aleatorias es la suma de las varianzas individuales:
```
Var(X+Y) = Var(X) + Var(Y)
```
Este principio SÓLO se cumple si X e Y son variables aleatorias independientes. Digamos que X es el evento de obtener cara en un solo lanzamiento de moneda justo, e Y es el evento de obtener un 2 en un dado de seis caras justo:

```
Var(X)=0.5∗(1−0.5)=0.25
Var(Y)=0.167∗(1−0.167)=0.139
Var(X+Y)=Var(X)+Var(Y)=0.25+0.13
```
