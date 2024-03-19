---
layout: default
title: Teorema de Bayes
nav_order: 7
parent: Reglas de la probabilidad
grand_parent: Probabilidad
---

## Teorema de Bayes

Imagine que es un paciente que recientemente dio positivo por faringitis estreptocócica. Es posible que desee saber la probabilidad de que TIENE faringitis estreptocócica, dado que su prueba dio positivo:

![Ejercicio](https://fer78docs.github.io/assets/images/ejercicio de bayes.png)


```
P(ST|+)
```

o calculate this probability, we will use something called Bayes Theorem, which states the following:
```
P(B ∣ A)= P(A ∣ B) * P(B) / P(A)
```

Usando el teorema de Bayes la formula quedaria:

```
P(ST ∣ +)= P(+ ∣ ST) * P(ST) / P(+)
```

Sabemos que: 
```
P(+∣ST)=0.85
P(ST)=0.20
```

¿Qué pasa con P(+)? ¿Es esto algo que sabemos? Bueno, pensemos en esto. Hay cuatro resultados posibles:

- Tener faringitis estreptocócica y dar positivo
- Tener faringitis estreptocócica y dar negativo
- No tener faringitis estreptocócica y dar positivo
- No tener faringitis estreptocócica y dar negativo

Solo nos importan los dos resultados en los que un paciente da positivo en P(+) . Por tanto, podemos decir:

```
P(+) = P(ST and + ) + P(NO ST and + )
P(+) = 0.17 + 0.016
P(+) = 0.186
```

​Finalmente, si integramos todo esto en la fórmula del teorema de Bayes, obtenemos:
```
P(ST ∣ +) = (0.85 * 0.20) / 0.186 = 0.914
```
Existe un 91,4% de posibilidades de que realmente tenga faringitis estreptocócica si su prueba da positivo. Esto no es obvio a partir de la información descrita en nuestro diagrama de árbol, pero con el poder del teorema de Bayes, pudimos calcularlo.

Otros calculos: 

Probabilidad de resultado negativo:

![Probabilidad de Resultado negativo](https://fer78docs.github.io/assets/images/probabilidad_negativo.webp)

Probabilidad de Resultado positivo y no tiene ST: 

![Probabilidad de Resultado positivo y no tiene ST](https://fer78docs.github.io/assets/images/probability_nost_y_positivo.webp)


Probabilidad de no tener ST y dar negetivo

![Probabilidad de Resultado negativo](https://fer78docs.github.io/assets/images/nost_negativo.webp)


