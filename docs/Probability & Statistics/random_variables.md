---
layout: default
title: Random Variables
nav_order: 4
parent: Probability & Statistics
---

## Indice

- [Variables Aleatorias](#variables-aleatorias)
- [Bernoulli Random Variables](#bernoulli-random-variables)


## Variables Aleatorias

{: .note}
Una **variable aleatoria** se define técnicamente como una función de valor real que asigna un número real a cada resultado posible de un experimento aleatorio. Aunque se llama "variable", en realidad es una función que mapea resultados a números.

### Ejemplo Práctico: Lanzamiento de Dos Dados

Consideremos el experimento de lanzar dos dados de seis caras. El espacio muestral de este experimento, es decir, todos los posibles resultados de lanzar dos dados, contiene 36 posibles combinaciones (desde $$(1,1)$$ hasta $$(6,6)$$).

#### Definición de la Función

Definimos una función $$F$$ que toma como entrada un resultado del experimento (en este caso, una pareja de números que representan el resultado de cada dado) y devuelve la suma de estos dos números. Esta función $$F$$ es un ejemplo de una variable aleatoria porque asigna un valor numérico real (la suma) a cada posible resultado del experimento (cada pareja de números). Imaginemos cómo se vería esta función en Python:

```python
def suma_dados(a, b):
    return a + b
```

Esta función, `suma_dados`, acepta dos entradas (los resultados de cada dado) y devuelve su suma.

### Variables Aleatorias Basadas en el Mismo Experimento

Podemos definir múltiples variables aleatorias basadas en el mismo experimento de lanzamiento de dos dados:

1. **Suma de los resultados** ($$S$$): Como ya definimos con la función `suma_dados`.
2. **Máximo de los resultados** ($$M$$): Una variable aleatoria que devuelve el máximo de los dos números obtenidos.
3. **Indicador de número primo** ($$I$$): Una variable aleatoria que devuelve 1 si la suma es un número primo, y 0 en caso contrario.

Visualización de los Valores de $$S$$

Para cada posible valor de la suma $$S$$, podemos identificar qué resultados del lanzamiento corresponden a ese valor específico. Por ejemplo:

- Si $$S = 2$$, el único resultado posible es $$(1,1)$$.
- Si $$S = 3$$, los resultados posibles son $$(1,2)$$ y $$(2,1)$$.
- Si $$S = 4$$, los resultados posibles son $$(1,3), (2,2)$$, y $$(3,1)$$.

Y así sucesivamente para los demás valores posibles de `S`.

### Probabilidades Asociadas a las Variables Aleatorias

La probabilidad de que una variable aleatoria tome un valor específico es la probabilidad del evento que genera ese valor. Por ejemplo:

- La probabilidad de que $$S = 2$$ es la probabilidad de obtener $$(1,1)$$ en el lanzamiento, que es $$\frac{1}{36}$$.
- La probabilidad de que $$S = 4$$s sería la suma de las probabilidades de obtener $$(1,3), (2,2), y (3,1)$$, que sería $$\frac{3}{36} = \frac{1}{12}$$.

Las variables aleatorias deben ser numéricas, lo que significa que siempre toman un número en lugar de una característica o cualidad. Si queremos usar una variable aleatoria para representar un evento con resultados no numéricos, podemos elegir números para representar esos resultados. Por ejemplo, podríamos representar el lanzamiento de una moneda como una variable aleatoria asignando a “cara” un valor de 1 y a “cruz” un valor de 0.

Usaremos `random.choice(a, size = size, replace = True/False)`de la biblioteca `numpy` para simular variables aleatorias en Python. En este método:

- `a` es una lista u otro objeto que tiene valores de los que estamos tomando muestras
- `size` es un número que representa cuántos valores elegir
- `replace` puede ser igual a `True` o `False` y determina si mantenemos un valor adespués de dibujarlo `(replace = True)` o lo eliminamos del grupo `(replace = False)`.

El siguiente código simula el resultado de lanzar un dado justo dos veces usando `np.random.choice()`:

```python
import numpy as np

# 7 is not included in the range function
die_6 = range(1, 7)

rolls = np.random.choice(die_6, size = 2, replace = True)

print(rolls)
```
output
```
[2, 5]
```

### Aplicación de las Variables Aleatorias

La utilidad de estas variables aleatorias radica en su capacidad para simplificar el análisis del experimento:

- **Probabilidad de Eventos Específicos:** Por ejemplo, la probabilidad de que $$A$$ tome el valor 4 se calcula sumando las probabilidades de todos los eventos que producen un máximo de 4 en los lanzamientos, tales como (1,4), (2,4), (3,4), (4,1), (4,2), (4,3), y (4,4).
- **Modelado de la Distribución:** La distribución de probabilidad para cada variable aleatoria discreta se puede describir utilizando **funciones de masa de probabilidad**, las cuales asignan a cada valor de la variable aleatoria la probabilidad del evento correspondiente.

### Variables aleatorias discretas

{: .highlight}
Las **variables aleatorias con un número contable de valores posibles** se denominan variables aleatorias discretas. Por ejemplo, lanzar un dado normal de 6 caras se consideraría una variable aleatoria discreta porque las opciones de resultado se limitan a los números del dado.

Las variables aleatorias discretas también son comunes cuando se observan eventos de conteo, como cuántas personas ingresaron a una tienda en un día seleccionado al azar. En este caso, los valores son contables porque se limitan a números enteros (no se puede observar la mitad de una persona).

### Variables aleatorias continuas

{: .highlight}
Cuando **los valores posibles de una variable aleatoria son incontables, se le llama variable aleatoria continua**. Generalmente son variables de medición y no se pueden contar porque las mediciones siempre pueden ser más precisas: metros, centímetros, milímetros, etc.

Por ejemplo, la temperatura en Los Ángeles en un día elegido al azar es una variable aleatoria continua. Siempre podemos ser más precisos sobre la temperatura expandiendo a otro decimal (96 grados, 96,44 grados, 96,437 grados, etc.).

## Bernoulli Random Variables

### Función de Masa de Probabilidad (PMF)

{: .note}
La **función de masa de probabilidad** asigna probabilidades a los posibles valores discretos de una variable aleatoria. La **PMF** cumple con los axiomas de la probabilidad:

- La probabilidad de cada valor es no negativa.
- La suma de las probabilidades de todos los posibles valores es igual a 1.

### Ejemplo con la Suma de Dos Dados

Si consideramos la variable $$S$$ como la suma de dos lanzamientos de un dado:
- $$P(S = 2) = \frac{1}{36}$$ porque solo hay una forma de obtener un 2: lanzando dos unos.
- $$P(S = 3) = \frac{2}{36}$$ porque hay dos combinaciones que dan un 3: (1,2) y (2,1).
- Y así sucesivamente hasta $$S = 12$$.

Estos cálculos asumen que todos los resultados son igualmente probables, lo cual es cierto para un dado justo.

### Aplicación Práctica: Variable Aleatoria Bernoulli

{: .highlight}
Una **variable aleatoria Bernoulli** es un tipo especial de variable aleatoria discreta que solo toma dos valores, generalmente 0 y 1. Es extremadamente útil para modelar experimentos binarios como el lanzamiento de una moneda.

#### Ejemplo con el Lanzamiento de una Moneda
- Si la moneda es justa, $$P(X = 1) = 0.5$$ y $$P(X = 0) = 0.5$$.
- Si la moneda no es justa y la probabilidad de cara es 0.7, entonces $$P(X = 1) = 0.7$$ y $$P(X = 0) = 0.3$$.

La **PMF** en este caso asignaría 0.7 a obtener cara y 0.3 a obtener cruz, reflejando la naturaleza sesgada de la moneda.

### Simulación en Python

Vamos a construir una función en Python que simule un experimento de Bernoulli, el cual podría representar, por ejemplo, el lanzamiento de una moneda:

```python
import numpy as np

def bernoulli_trial(p=0.5):
    """Simula un experimento de Bernoulli.
        Args:
    p (float): Probabilidad de éxito (por defecto 0.5).
        Returns:
    int: 1 si el experimento resulta en éxito, 0 en caso contrario.
    """
    return 1 if np.random.rand() <= p else 0
```

En esta función, `np.random.rand()` genera un número aleatorio entre 0 y 1, y compara este número con la probabilidad de éxito `p`. Si el número generado es menor o igual a `p`, el resultado es un éxito (1); de lo contrario, es un fracaso (0).

### Simulación y Análisis de Resultados

Podemos usar esta función para realizar múltiples ensayos y observar la frecuencia de éxitos, lo que nos permite estimar la probabilidad de éxito de la moneda:

```python
def simulate_bernoulli_trials(n, p=0.5):
    """Simula n ensayos de Bernoulli y reporta la frecuencia de éxitos.
        Args:
    n (int): Número de ensayos.
    p (float): Probabilidad de éxito.
    
    Returns:
    float: Frecuencia de éxitos.
    """
    results = [bernoulli_trial(p) for _ in range(n)]
    return sum(results) / n

# Simular 1000 lanzamientos de una moneda con p = 0.7
n_trials = 1000
success_prob = 0.612199
frequency_of_success = simulate_bernoulli_trials(n_trials, success_prob)

print(f"La frecuencia de éxito estimada es {frequency_of_success:.2f}")
```
Output:
```
La frecuencia de éxito estimada es 0.71
```

Este código simula 1000 lanzamientos de una moneda donde la probabilidad de obtener cara (éxito) es del 70%. La función simulate_bernoulli_trials devuelve la frecuencia de éxitos, que debería acercarse a 0.7 a medida que el número de ensayos aumenta.

### Visualización de la Convergencia

Para visualizar cómo la frecuencia de éxitos converge a la probabilidad real, podríamos realizar múltiples simulaciones aumentando progresivamente el número de ensayos y graficar los resultados:

```python
import matplotlib.pyplot as plt

trial_counts = [10, 50, 100, 500, 1000, 5000, 10000]
frequencies = [simulate_bernoulli_trials(count, success_prob) for count in trial_counts]

plt.figure(figsize=(10, 5))
plt.plot(trial_counts, frequencies, marker='o', linestyle='-')
plt.axhline(y=success_prob, color='r', linestyle='--')
plt.title('Convergencia de la Frecuencia de Éxitos a la Probabilidad Real')
plt.xlabel('Número de Ensayos')
plt.ylabel('Frecuencia de Éxitos')
plt.xscale('log')
plt.show()
```

![Visualización de la Convergencia](https://fer78docs.github.io/assets/images/Visualización de la Convergencia.png)

Este gráfico mostrará cómo la frecuencia de éxitos se estabiliza y converge hacia la probabilidad real de éxito (0.612199 en este caso) a medida que aumenta el número de ensayos, ilustrando la ley de los grandes números.

## Geometric Random Variable

### Ensayos Independientes de Bernoulli

{: .highlight}
Un ensayo independiente implica que el resultado de un ensayo no influye ni puede ser influenciado por los resultados de otros ensayos. En el contexto de lanzar una moneda, significa que el resultado de un lanzamiento no afecta el resultado del siguiente.

#### Ejemplo con Dos Lanzamientos
Si lanzamos una moneda dos veces con una probabilidad de 0.7 de sacar cara en cada lanzamiento, la probabilidad de obtener dos caras seguidas sería $$0.7 \times 0.7 = 0.49$$.

#### Explicación y Ejemplo
Supongamos que lanzamos una moneda hasta que salga cara por primera vez, y queremos saber cuántos lanzamientos se necesitan.

```python
def geometric_trial(p=0.7):
    """Simula una variable aleatoria geométrica.
    Args:
        p (float): Probabilidad de sacar cara. 
    Returns:
        int: Número de lanzamientos hasta el primer éxito.
    """
    count = 1
    while bernoulli_trial(p) == 0:
        count += 1
    return count
```

Esta función utiliza la función de Bernoulli definida anteriormente para simular lanzamientos sucesivos hasta que el primer lanzamiento resulte en éxito (cara).

### Función de Masa de Probabilidad (PMF) de la Variable Geométrica

{: .highlight}
La PMF de una variable aleatoria geométrica da la probabilidad de que se necesite un número específico de ensayos para alcanzar el primer éxito. 

#### Ejemplo

- $$P(X=1) = 0.7$$ (sacar cara en el primer lanzamiento).
- $$P(X=2) = 0.3 \times 0.7$$ (sacar cruz en el primero y cara en el segundo).
- $$P(X=n) = 0.3^{(n-1)} \times 0.7$$ (sacar cruz en los primeros $$n-1$$ lanzamientos y cara en el $$n$$-ésimo).

### Prueba de normalización de variable aleatoria geométrica opcional

Este segmento explica la variable aleatoria geométrica en detalle, destacando su importancia en el contexto de ensayos independientes de Bernoulli, como el lanzamiento repetido de una moneda hasta obtener el primer éxito (cara). Además, se aborda la propiedad de normalización de la distribución geométrica y se anticipa una demostración práctica utilizando Python. Vamos a desglosar y ampliar estos conceptos y ejemplos en español.

### Variable Aleatoria Geométrica

{: .highlight}
La variable aleatoria geométrica mide el número de intentos necesarios hasta obtener el primer éxito en una serie de ensayos independientes de Bernoulli. Por ejemplo, en el lanzamiento de una moneda, esta variable contaría cuántos lanzamientos se realizan hasta que aparece la primera cara, asumiendo que cada lanzamiento es independiente del anterior.

#### Propiedades de la Variable Geométrica

- **Espacio Muestral Infinito pero Contable:** La variable geométrica puede tomar una cantidad infinita de valores (1, 2, 3, ...), ya que teóricamente podrían requerirse infinitos lanzamientos para obtener una cara. Sin embargo, estos valores son contables, lo que clasifica a la variable como discreta.
- **Distribución de Probabilidad:** La probabilidad de que la variable aleatoria geométrica tome un valor específico $$k$$ es una función de la probabilidad de éxito $$p$$ y la probabilidad de fracaso $$q = 1-p$$. donde $$k$$ es el número de lanzamientos realizados hasta obtener el primer éxito.

$$P(X = k) = q^{k-1} \cdot p$$

### Demostración de la Propiedad de Normalización

{: .highlight}
Para cualquier variable aleatoria discreta, la suma de las probabilidades de todos los posibles valores debe ser igual a 1. Esto asegura que la distribución de probabilidad esté correctamente definida.

#### Demostración para la Variable Geométrica
Se puede demostrar que la suma de las probabilidades para todos los posibles valores de una variable geométrica es 1 utilizando la serie geométrica:

$$
\sum_{k=1}^{\infty} P(X = k) = \sum_{k=1}^{\infty} q^{k-1} \cdot p = p \sum_{k=0}^{\infty} q^k = p \cdot \frac{1}{1-q} = 1
$$

donde la suma de una serie geométrica $$\sum_{k=0}^{\infty} q^k$$ es $$\frac{1}{1-q}$$, y dado que $$q = 1-p$$, la expresión se simplifica a 1, confirmando que la distribución está bien definida.

### Aplicación Práctica en Python

Este código simula 1000 ensayos de una variable aleatoria geométrica y utiliza un histograma para visualizar cuántos lanzamientos se necesitan típicamente para obtener el primer éxito. Esta visualización ayuda a comprender la naturaleza de la distribución geométrica y la efectividad de los ensayos de Bernoulli independientes.

```python
import numpy as np
import matplotlib.pyplot as plt

def geometric_trial(p=0.7):
    count = 0
    while np.random.rand() >= p:
        count += 1
    return count + 1

# Simulación de 1000 ensayos geométricos
results = [geometric_trial(p=0.7) for _ in range(1000)]

# Visualización de la distribución
plt.hist(results, bins=max(results), edgecolor='black')
plt.title('Distribución de la Variable Aleatoria Geométrica')
plt.xlabel('Número de Lanzamientos hasta el Primer Éxito')
plt.ylabel('Frecuencia')
plt.show()
```
![Visualización de la Convergencia](https://fer78docs.github.io/assets/images/variable_aleatoria_geométrica.png)

