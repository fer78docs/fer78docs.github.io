---
layout: default
title: Continuous Random Variables
nav_order: 5
parent: Probability & Statistics
---




## Zero Probability to Individual Values

¿Podemos realmente decir que es imposible que ocurran eventos de probabilidad cero? No se puede encontrar ningún ejemplo mientras se permanece en el ámbito de los espacios muestrales finitos. Por otro lado, **en  espacios muestrales infinitos , abundan los posibles resultados de probabilidad cero.** Las variables aleatorias continuas pueden tomar cualquier valor dentro de un intervalo continuo, y estos valores son no numerables.

### Experimento del Círculo Unitario

![Experimento del Circulo Unitario](https://fer78docs.github.io/assets/images/circulo_unitario.png)

Consideremos un experimento ilustrativo para entender mejor las variables aleatorias continuas. Imaginemos un círculo unitario, es decir, un círculo de radio uno, centrado en el origen de un sistema de coordenadas. En este experimento, el acto aleatorio consiste en colocar puntos dentro del círculo. La variable de interés en este caso es la distancia desde el origen hasta el punto donde cada punto es colocado aleatoriamente.

En este experimento, la variable aleatoria que define la distancia desde el origen hasta el punto puede tomar cualquier valor entre 0 y 1. El valor 0 se alcanzaría si el punto cae exactamente en el centro del círculo (el origen), mientras que el valor 1 se alcanza si el punto cae en cualquier parte del perímetro del círculo. Entre estos dos extremos, hay infinitos valores posibles que la distancia podría tomar, como 0.1, 0.001, 0.7213, etc. Estos valores forman un continuo y son ejemplos de una variable aleatoria continua.

Si consideramos anillos concéntricos dentro del círculo, cada anillo podría representar un intervalo específico para $$X$$, y la probabilidad de que $$X$$ tome un valor dentro de un anillo sería proporcional al área de ese anillo.

### Asignación de Probabilidades

En el caso de variables continuas, la asignación de probabilidades presenta desafíos únicos. En teoría, la probabilidad de que la variable aleatoria tome un valor específico exacto dentro del intervalo es cero. Esto se debe a que la cantidad de posibles valores en un intervalo continuo es infinita, y asignar una probabilidad positiva a cada posible valor individual resultaría en una suma de probabilidades que excedería 1, violando la propiedad de normalización de probabilidades.

Para manejar probabilidades en el caso de variables continuas, utilizamos lo que se conoce como**Funciones de Densidad de Probabilidad (PDF)** . Estas funciones no asignan probabilidades a valores individuales sino que describen la densidad de probabilidad en diferentes regiones del espacio de valores de la variable.

Por ejemplo, en lugar de preguntar cuál es la probabilidad de que la variable aleatoria sea exactamente 0.5, utilizamos la PDF para determinar la probabilidad de que la variable esté dentro de un intervalo, como entre 0.3 y 0.7.

## Probability Density Functions

{: .note}
En el estudio de las variables aleatorias continuas, las **Funciones de Densidad de Probabilidad** (PDFs, por sus siglas en inglés) son esenciales para modelar y comprender la distribución de probabilidad de estas variables. A diferencia de las Funciones de Masa de Probabilidad (PMFs), que asignan probabilidades a valores específicos de variables discretas, las PDFs se utilizan para construir modelos de probabilidad sobre intervalos de variables continuas.

### Conceptos Básicos de PDFs

{: .highlight}
Una Funcion de Densidad de Probabilidad de  no proporciona directamente la probabilidad de un valor específico; en cambio, describe cómo se distribuye la probabilidad a lo largo de un intervalo de posibles valores. En el contexto de las variables continuas, una PDF es útil para calcular la probabilidad de que la variable caiga dentro de un rango específico.

#### Modelado de Probabilidades:

- Para construir una PDF, se puede comenzar definiendo la función en todo su rango posible, asegurando que el área bajo la curva de la función sea igual a uno.
- Por ejemplo, para una variable $$X$$ uniforme que varía de 0 a 1, una PDF simple podría ser una función constante donde el valor de la función (altura) es siempre 1 en el intervalo [0,1].

#### Cálculo de Probabilidades:

- Para calcular la probabilidad de que $$X$$ esté en un intervalo específico, como entre 0.2 y 0.4, calculamos el área bajo la PDF en ese intervalo.
- Esta área se obtiene integrando la función de densidad de probabilidad desde 0.2 hasta 0.4, y el resultado representa la probabilidad de que $$X$$ caiga dentro de ese rango.

### Propiedades Clave de las PDFs

1. **Positividad:** Todos los valores de una PDF deben ser **no negativos**, una propiedad compartida con las PMFs.

2. **Integración a Uno:** A diferencia de las PMFs, donde cada valor individual puede tener una probabilidad directamente asignada (y sumar todas las probabilidades da uno), en las PDFs el total del área bajo la curva debe ser igual a uno para que el modelo de probabilidad sea válido.

3. **Diferencias con PMFs:** Mientras que los valores de una PMF siempre deben ser menores o iguales a uno, los valores de una PDF pueden ser mayores que uno, siempre que el área bajo la curva se mantenga en uno. Esto es importante porque los valores de la PDF no representan probabilidades directas sino densidades de probabilidad, que ayudan a calcular probabilidades sobre intervalos.

## Continuos Uniform Distribution

La **distribución uniforme continua es un modelo estadístico esencial que se utiliza para describir situaciones donde todos los eventos en un intervalo específico son igualmente probables**. Esta distribución es particularmente útil para simular y modelar fenómenos en los cuales no hay preferencia por ningún valor dentro del rango establecido.

{: .note}
Una variable aleatoria $$X$$ se dice que sigue una distribución uniforme continua sobre un intervalo $$[a, b]$$ si cada valor dentro de este intervalo es igualmente probable. Esto implica que la función de densidad de probabilidad (PDF) para $$X$$ es constante dentro de $$[a, b]$$ y cero fuera de este rango.

Para una variable aleatoria $$X$$ que es uniforme sobre el intervalo $$[10, 30]$$

![variable_continuous](https://fer78docs.github.io/assets/images/pdf_continuous.png)

$$
f(x) = \begin{cases} 
\frac{1}{20} & \text{si } 10 \leq x \leq 30 \\
0 & \text{de lo contrario}
\end{cases}
$$

Esta forma de la función garantiza que la probabilidad de cualquier subintervalo dentro de $$[10, 30]$$ sea proporcional a su longitud. La constante $$\frac{1}{20}$$ se deriva de la inversa de la longitud del intervalo $$(30 - 10 = 20)$$, asegurando que el área total bajo la curva de la PDF sea 1, cumpliendo así con una propiedad fundamental de las distribuciones de probabilidad.

### Ejemplo Práctico de la Distribución Uniforme

Supongamos que queremos calcular la probabilidad de que $$X$$ caiga entre 15 y 20. Dado que la altura de la función de densidad es $$\frac{1}{20}$$ en todo el intervalo $$[10, 30]$$, el cálculo de esta probabilidad se reduce a evaluar el área de un rectángulo definido por el intervalo $$[15, 20]$$:

$$
P(15 \leq X \leq 20) = \frac{1}{20} \times (20 - 15) = \frac{1}{20} \times 5 = \frac{1}{4}
$$

Esto indica que hay una probabilidad del 25% de que $$X$$ esté entre 15 y 20.

#### Aplicación en Simulaciones

La distribución uniforme es ampliamente utilizada en la generación de números aleatorios, especialmente en simulaciones computacionales. Por ejemplo, la función `np.random.rand()` en Python genera números aleatorios uniformemente distribuidos en el intervalo $$[0, 1]$$. Estos valores pueden ser escalados a cualquier otro intervalo $$[a, b]$$ mediante la transformación:

$$
X = a + (b - a) \times \text{np.random.rand()}
$$

Esto es particularmente útil en estudios de simulación donde se requieren entradas aleatorias que sean equitativas en términos de probabilidad a lo largo de un intervalo dado.

### Implementar Uniform Distributions con Python

```python
import matplotlib.pyplot as plt
import seaborn as sns

X = 100 * np.random.rand(100000)+20
plt.hist(X, density=True, bins=50)
sns.kdeplot(X)
```

![Uniform Distribution](https://fer78docs.github.io/assets/images/hist_random_continious.png)

## Exponential Random Variables

Las variables aleatorias exponenciales son un tipo importante de distribución de probabilidad continua que se utiliza **para modelar el tiempo entre eventos en procesos que son continuos** y sin memoria. Esta distribución es especialmente útil en el ámbito de la teoría de colas, la fiabilidad de sistemas y en la modelación de procesos de llegada en sistemas de comunicaciones.

Una variable aleatoria exponencial, denotada como $$X$$, **describe el tiempo entre eventos en un proceso de Poisson, donde los eventos ocurren de manera continua e independiente a una tasa constante**. Matemáticamente, la función de densidad de probabilidad (PDF) de una variable aleatoria exponencial está dada por:

$$
f(x; \lambda) = \lambda e^{-\lambda x} \quad \text{para } x \geq 0
$$

Donde:
- $$\lambda$$ es la tasa de llegada o tasa de fallo, también conocida como parámetro de tasa, que indica el número promedio de eventos por unidad de tiempo.
- $$e$$ es la base del logaritmo natural.
- $$x$$ representa el tiempo.

Las principales características de esta distribución incluyen:
- **Sin memoria**: La distribución exponencial es la única distribución continua que tiene la propiedad de falta de memoria, lo que significa que la probabilidad de que ocurra un evento en el futuro es independiente de cualquier historia pasada.
  
$$
P(X > s + t | X > s) = P(X > t) \quad \text{para todo } s, t \geq 0
$$

- **Media y Varianza**:
  - La media (esperanza) de $$X$$ es $$\frac{1}{\lambda}$$.
  - La varianza de $$X$$ es $$\frac{1}{\lambda^2}$$.

#### Ejemplos de Aplicación

1. **Teoría de Colas**: En el análisis de colas, la distribución exponencial se utiliza para modelar los tiempos de llegada de clientes a un servicio o los tiempos de servicio necesarios en puntos de atención.
  
2. **Fiabilidad de Sistemas**: En ingeniería de fiabilidad, se utiliza para modelar el tiempo hasta el fallo de componentes electrónicos o mecánicos. Por ejemplo, si un componente tiene una tasa de fallo constante de \( \lambda \) fallos por hora, el tiempo hasta el fallo del componente puede modelarse como una variable aleatoria exponencial.

3. **Procesos de Llegada en Redes de Comunicación**: En telecomunicaciones, los tiempos entre llegadas de paquetes de datos pueden modelarse utilizando distribuciones exponenciales.

### Simulación en Python

Aquí se presenta un ejemplo básico de cómo generar y visualizar variables aleatorias exponenciales utilizando Python y NumPy:

```python
import numpy as np
import matplotlib.pyplot as plt

# Parámetro de tasa
lambda_param = 1.0

# Generar 1000 variables aleatorias exponenciales
data = np.random.exponential(1/lambda_param, 1000)

# Visualizar los datos
plt.hist(data, bins=50, density=True, alpha=0.75, label='Datos simulados')
plt.title('Histograma de Variables Aleatorias Exponenciales')
plt.xlabel('Tiempo')
plt.ylabel('Densidad')
plt.legend()
plt.show()
```

![Probability density funtion](https://fer78docs.github.io/assets/images/pdf_histogram.png)

El código siguiente utiliza NumPy y Matplotlib para visualizar la función de densidad de probabilidad (PDF) de varias distribuciones exponenciales con diferentes parámetros de tasa.

```python
# Importar las bibliotecas necesarias para el manejo de arrays y visualización
import numpy as np
import matplotlib.pyplot as plt

# Generar 1000 puntos equidistantes en el rango de 0 a 10
x = np.linspace(0, 10, 1000)

# Crear diferentes valores del parámetro de tasa 'lambda', desde 0.1 hasta 2, en total 4 valores
lmdaz = np.linspace(0.1, 2, 4)

# Iterar sobre cada valor de lambda
for i in lmdaz:
    # Calcular la función de densidad de probabilidad exponencial para cada valor de x y lambda
    fx = i * np.exp(-i * x)  # f(x) = lambda * exp(-lambda * x)
    
    # Graficar la función calculada, etiquetando con el valor de lambda correspondiente
    plt.plot(x, fx, label=str(i))

# Añadir una leyenda al gráfico, que muestra las etiquetas de los valores de lambda
plt.legend()

# Mostrar el gráfico resultante
plt.show()
```

![Probability density funtion](https://fer78docs.github.io/assets/images/pdfuntions.png)
