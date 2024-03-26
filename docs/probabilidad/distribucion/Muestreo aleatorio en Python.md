---
layout: default
title: Muestreo aleatorio en Python
nav_order: 10
parent: Intro Probability Distributions
grand_parent: Probability
---

# Muestreo de una población


En estadística, a menudo queremos aprender sobre una población grande. Dado que a menudo es imposible recopilar datos para una población completa, los investigadores pueden utilizar una muestra más pequeña de datos para intentar responder sus preguntas.

Para hacer esto, un investigador podría calcular una estadística como la media o la mediana para una muestra de datos. Luego pueden usar esa estadística como una estimación del valor de la población que realmente les importa.

Por ejemplo, supongamos que un investigador quiere saber el peso promedio de todos los peces de salmón del Atlántico. Sería imposible capturar todos los peces. En cambio, los investigadores podrían recolectar una muestra de 50 peces frente a la costa de Nueva Escocia y determinar que el peso promedio de esos peces es x . Si los mismos investigadores recolectaran 50 peces nuevos y tomaran el nuevo peso promedio, ese promedio probablemente sería ligeramente diferente al promedio de la primera muestra.



## Muestreo aleatorio en Python

Ahora que hemos generado algunas muestras aleatorias de una población usando un subprograma, codifiquemos esto nosotros mismos en Python. El paquete `numpy.random` tiene varias funciones que podríamos usar para simular un muestreo aleatorio. En este ejercicio, usaremos la función `np.random.choice()`, que genera una muestra de cierto tamaño a partir de una matriz determinada.

En el código de ejemplo, haremos como que somos todopoderosos y en realidad tenemos una lista de todos los pesos de salmón del Atlántico que existen actualmente.

En el código de ejemplo, hemos hecho lo siguiente:

Cargado con los pesos de todos los salmones en un marco de datos llamado population.
Trazó la distribución populationy calculó la media.
Función utilizada `np.random.choice()` para generar una muestra llamada sample de tamaño 30 (la variable `samp_size` es igual a 30).

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import codecademylib3

population = pd.read_csv("salmon_population.csv")
population = np.array(population.Salmon_Weight)
pop_mean = round(np.mean(population),3)

## Plotting the Population Distribution
sns.histplot(population, stat='density')
plt.axvline(pop_mean,color='r',linestyle='dashed')
plt.title(f"Population Mean: {pop_mean}")
plt.xlabel("Weight (lbs)")
plt.show()
plt.clf() # close this plot
```

![Population](https://fer78docs.github.io/assets/images/population.png)


##Distribuciones de muestreo


Como vimos en el último ejemplo, cada vez que tomamos muestras de una población, obtendremos una media muestral ligeramente diferente. Para comprender cuánta variación podemos esperar en esas medias muestrales, podemos hacer lo siguiente:

- Tome un montón de muestras aleatorias de peces, cada una del mismo tamaño (50 peces en este ejemplo).
- Calcular la media muestral para cada uno.
- Trazar un histograma de todas las medias muestrales.

Este proceso nos da una estimación de la distribución muestral de la media para un tamaño de muestra de 50 peces.

El código para lograr esto se muestra a continuación:

```python
salmon_population = population['Salmon_Weight']

sample_size = 50
sample_means = []

# loop 500 times to get 500 random sample means
for i in range(500):
  # take a sample from the data:
  samp = np.random.choice(salmon_population, sample_size, replace = False)
  # calculate the mean of this sample:
  this_sample_mean = np.mean(samp)
  # append this sample mean to a list of sample means
  sample_means.append(this_sample_mean)

# plot all the sample means to show the sampling distribution
sns.histplot(sample_means, stat='density')
plt.title("Sampling Distribution of the Mean")
plt.show()
```

La distribución del sample_meansluce así:

![Sampling Distribution](https://fer78docs.github.io/assets/images/sample_meansluce.png)

Tenga en cuenta que podemos observar una distribución muestral para cualquier estadística. Por ejemplo, podríamos estimar la distribución muestral del máximo calculando el máximo de cada muestra, en lugar de la media (como se muestra arriba).

## Teorema del límite central

Hasta ahora, hemos definido el término distribución muestral y hemos mostrado cómo podemos simular una distribución muestral aproximada para algunas estadísticas diferentes (media, máximo, varianza, etc.). El teorema del límite central (CLT) nos permite describir específicamente la distribución muestral de la media.

El CLT establece que la distribución muestral de la media se distribuye normalmente siempre que la población no esté demasiado sesgada o el tamaño de la muestra sea lo suficientemente grande. Usar un tamaño de muestra de n > 30 suele ser una buena regla general, independientemente de cómo sea la distribución de la población. Si la distribución de la población es normal, el tamaño de la muestra puede ser menor.

Echemos otro vistazo al peso del salmón para ver cómo se aplica aquí el CLT. El primer gráfico a continuación muestra la distribución de la población. El peso del salmón está sesgado hacia la derecha, lo que significa que la cola de la distribución es más larga a la derecha que a la izquierda.

![CTL](https://fer78docs.github.io/assets/images/salmon_weigth.png)

A continuación, simulamos una distribución muestral de la media (utilizando un tamaño de muestra de 100) y superpusimos una distribución normal encima. Observe cómo la distribución muestral estimada sigue la curva normal casi a la perfección.

![CTL](https://fer78docs.github.io/assets/images/muestral_media.png)

Tenga en cuenta que el CLT solo se aplica a la distribución muestral de la media y no a otras estadísticas como máximo, mínimo y varianza.

**Ahora que hemos examinado el CLT desde un nivel alto, entremos en detalles.**

El CLT no sólo establece que la distribución muestral será normalmente distribuida, sino que también nos permite describir esa distribución normal cuantitativamente. Las distribuciones normales se describen por su media μ(mu) y desviación estándar σ(sigma).

Dividamos esto:

- Tomamos muestras de tamaño n de una población (que tiene una media poblacional verdadera μy una desviación estándar de σ) y calculamos la media muestral x.
- Dado que n es suficientemente grande (n > 30), la distribución muestral de las medias se distribuirá normalmente con:
    - media xaproximadamente igual a la media poblacionalμ
    - desviación estándar igual a la desviación estándar de la población dividida por la raíz cuadrada del tamaño de la muestra. Podemos escribir esto como:

![formula CTL](https://fer78docs.github.io/assets/images/formula ctl.png)

Nos centraremos en el primer punto de este ejercicio y en el segundo punto del siguiente ejercicio.

Como ejemplo de esto, echemos un vistazo nuevamente a nuestra población de salmón. En el último ejercicio vimos que la distribución muestral de la media tenía una distribución normal. En el gráfico siguiente, podemos ver que la media de la distribución muestral simulada es aproximadamente igual a la media poblacional.

![Graficos CTL](https://fer78docs.github.io/assets/images/ctl.png)

En el espacio de trabajo, hemos simulado una distribución muestral de la media utilizando un tamaño de muestra de 50.

Ejemplo: 

En el espacio de trabajo, configuramos una simulación de una población que tiene una media de 10 y una desviación estándar de 10. Configuramos un tamaño de muestra de 50.

Según el CLT, deberíamos tener una distribución muestral de la media que tenga una distribución normal y una media cercana a la media poblacional.

```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats as stats
import seaborn as sns

# Set the population mean & standard deviation:
population_mean = 10
population_std_dev = 10
# Set the sample size:
samp_size = 50

# Create the population
population = np.random.normal(population_mean, population_std_dev, size = 100000)

# Simulate the samples and calculate the sampling distribution
sample_means = []
for i in range(500):
    samp = np.random.choice(population, samp_size, replace = False)
    sample_means.append(np.mean(samp))

mean_sampling_distribution = round(np.mean(sample_means),3)

# Plot the original population
sns.histplot(population, stat = 'density')
plt.title(f"Population Mean: {population_mean} ")
plt.xlabel("")
plt.show()
plt.clf()

## Plot the sampling distribution
sns.histplot(sample_means, stat='density')
# calculate the mean and SE for the probability distribution
mu = np.mean(population)
sigma = np.std(population)/(samp_size**.5)
# plot the normal distribution with mu=popmean, sd=sd(pop)/sqrt(samp_size) on top
x = np.linspace(mu - 3*sigma, mu + 3*sigma, 100)

plt.plot(x, stats.norm.pdf(x, mu, sigma), color='k', label = 'normal PDF')
plt.title(f"Sampling Dist Mean: {mean_sampling_distribution}")
plt.xlabel("")
plt.show()
```
![Graficos CTL](https://fer78docs.github.io/assets/images/ejemplo ctl.png)

### Error estándar

La segunda parte del teorema del límite central es:

La distribución muestral de la media tiene una distribución normal, con una desviación estándar igual a la desviación estándar de la población (a menudo indicada como la letra griega, sigma) dividida por la raíz cuadrada del tamaño de la muestra (a menudo indicada como n):
```
σ / √x
​```

La desviación estándar de una distribución muestral también se conoce como error estándar de la estimación de la media . En muchos casos, no podemos conocer la desviación estándar de la población, por lo que estimamos el error estándar utilizando la desviación estándar de la muestra:
```
standard deviation of our sample / √ sample size
​```
Dos cosas importantes a tener en cuenta sobre esta fórmula son que:

- A medida que aumenta el tamaño de la muestra, el error estándar disminuirá.
- A medida que aumenta la desviación estándar de la población, también lo hará el error estándar.

Ejemplo: 
puede ver una distribución de población y una distribución de muestreo (desplácese hacia abajo para ver la distribución de muestreo, Un error estándar más pequeño significa que la distribución será más alta y más delgada. ¿Es ese el caso?

Manten eso en mente:
- A medida que aumenta el tamaño de la muestra, el error estándar disminuirá.
- A medida que aumenta la desviación estándar de la población, también lo hará el error estándar.

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import scipy.stats as stats
import codecademylib3

population_mean = 36
population_std_dev = 10
# Set the sample size:
samp_size = 50

### Below is code to create simulated dataset and calculate Standard Error

# Create the population
population = np.random.normal(population_mean, population_std_dev, size = 100000)

## Simulate the sampling distribution
sample_means = []
for i in range(500):
    samp = np.random.choice(population, samp_size, replace = False)
    sample_means.append(np.mean(samp))

mean_sampling_distribution = round(np.mean(sample_means),3)
std_sampling_distribution = round(np.std(sample_means),3)

std_error = population_std_dev / (samp_size **0.5)

sns.histplot(population, stat = 'density')
plt.title(f"Population Mean: {population_mean} \n Population Std Dev: {population_std_dev} \n Standard Error = {population_std_dev} / sq rt({samp_size}) \n Standard Error = {std_error} ")
plt.xlim(-50,125)
plt.ylim(0,0.045)
plt.show()
plt.clf()

## Plot the sampling distribution
sns.histplot(sample_means, stat = 'density')
# calculate the mean and SE for the probability distribution
mu = np.mean(population)
sigma = np.std(population)/(samp_size**.5)

# plot the normal distribution with mu=popmean, sd=sd(pop)/sqrt(samp_size) on top
x = np.linspace(mu - 3*sigma, mu + 3*sigma, 100)
plt.plot(x, stats.norm.pdf(x, mu, sigma), color='k', label = 'normal PDF')
# plt.axvline(mean_sampling_distribution,color='r',linestyle='dashed')
plt.title(f"Sampling Dist Mean: {mean_sampling_distribution} \n Sampling Dist Standard Deviation: {std_sampling_distribution}")
plt.xlim(20,50)
plt.ylim(0,0.3)
plt.show()
```

![Error Estandar](https://fer78docs.github.io/assets/images/ejemplo_error_estandar.png)

### Estimadores sesgados

Según el teorema del límite central, la media de la distribución muestral de la media es igual a la media poblacional. Este es el caso de algunas distribuciones muestrales, pero no de todas. Recuerde, puede tener una distribución muestral para cualquier estadística muestral, incluyendo:

- significar
- mediana
- máximo minimo
- diferencia

Debido a que la media de la distribución muestral de la media es igual a la media de la población, lo llamamos estimador insesgado. Una estadística se denomina estimador insesgado de un parámetro poblacional si la media de la distribución muestral de la estadística es igual al valor de la estadística para la población.

El máximo es un ejemplo de estimador sesgado , lo que significa que la media de la distribución muestral del máximo no está centrada en el máximo de la población.

Ejemplo:
En el espacio de trabajo, puede ver la distribución muestral del máximo. La media de la distribución no es igual al máximo de la población, lo que demuestra que es un estimador sesgado.

Veamos otro ejemplo. Edite la función app_statistic()para que devuelva la varianza usando la función NumPy np.var(), np.mean()

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
import codecademylib3

app_stat_text = "Maximum"
def app_statistic(x):
    return np.mean(x)

### Below calculates the statistic for this population:
### You don't need to change anything below to pass the checkpoints
mean, std_dev = 50, 15
population = np.random.normal(mean, std_dev, 1000)

pop_statistic = round(app_statistic(population),2)

sns.histplot(population, stat = 'density')
plt.axvline(pop_statistic,color='r',linestyle='dashed')
plt.title(f"Population {app_stat_text}: {pop_statistic}")
plt.xlabel("")
plt.show()
plt.clf()

sample_stats = []
samp_size = 5
for i in range(500):
    samp = np.random.choice(population, samp_size, replace = False)
    this_sample_stat = app_statistic(samp)
    sample_stats.append(this_sample_stat)

sns.histplot(sample_stats, stat = 'density')
plt.title(f"Sampling Dist of the {app_stat_text} \nMean: {round(np.mean(sample_stats),2)}")
plt.axvline(np.mean(sample_stats),color='r',linestyle='dashed')
plt.xlabel(f"Sample {app_stat_text}")
plt.show()
plt.clf()
```

## Calcular probabilidades
Una vez que conocemos la distribución muestral de la media, también podemos usarla para estimar la probabilidad de observar un rango particular de medias muestrales, dada alguna información (conocida o supuesta) sobre la población. Para ello, podemos utilizar la Función de Distribución Acumulada, o (CDF) de la distribución normal.

Resolvamos esto con nuestro ejemplo del salmón. Digamos que estamos transportando el salmón y queremos asegurarnos de que la caja en la que transportamos el pescado sea lo suficientemente fuerte para soportar el peso.

Supongamos que estimamos que la población de salmón tiene un peso promedio de 60 libras con una desviación estándar de 40 libras.
Tenemos una caja que soporta 750 libras y queremos poder transportar 10 peces a la vez.
Queremos calcular la probabilidad de que el peso medio de esos 10 peces sea menor o igual a 75 (750/10).
Utilizando el CLT, primero estimamos que el peso medio de 10 salmones muestreados al azar de esta población se distribuye normalmente con media = 60 y error estándar = 40/10^.5. Luego, podemos usar esta distribución de probabilidad para calcular la probabilidad de que 10 peces muestreados al azar tengan un peso medio menor o igual a 75.

```python
x = 75
mean = 60
std_dev = 40
samp_size = 10
standard_error = std_dev / (samp_size**.5)
# remember that **.5 is raising to the power of one half, or taking the square root

stats.norm.cdf(x,mean,standard_error)
```

Esto arroja 0,882, o una probabilidad del 88,2% de que el peso promedio de nuestra muestra de 10 peces sea menor o igual a 75.


Ejemplo:

Calculemos la misma probabilidad para nuestra población de bacalao.

Sabemos que el bacalao tiene un peso promedio de 36 libras con una desviación estándar de 20. Queremos intentar meter 25 bacalaos en nuestra misma caja que puede contener hasta 750 libras.

Nuestro primer paso es calcular el error estándar para un tamaño de muestra de 25. Usando la información anterior, calcule el error estándar y asígnelo a una variable llamada standard_error.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

## Setting up our parameters
std_dev = 20
samp_size = 25

standard_error = std_dev / (samp_size**.5)
```

Ahora que tenemos nuestro error estándar, podemos usar la CDF normal para calcular la probabilidad de que una muestra de 25 peces tenga un peso medio de 30 libras. Usando la función `stats.norm.cdf()`, calcula esta probabilidad y asígnala a una variable `cod_cdf`.

```python
x = 30
mean = 36
cod_cdf = stats.norm.cdf(x,mean,standard_error)
```

**Recapitulemos lo que hemos aprendido en esta lección:**

- Una distribución muestral se obtiene tomando una muestra aleatoria de un cierto tamaño varias veces, tomando una estadística muestral y trazando la distribución de esta estadística muestral.
- El Teorema del Límite Central establece que la distribución muestral de la media estará distribuida normalmente (incluso si la población original no estaba distribuida normalmente).
- Una estadística se denomina estimador insesgado de un parámetro poblacional si la media de la distribución muestral de la estadística es igual al valor de la estadística para la población. La media es un estimador insesgado.
- Podemos utilizar el error estándar de nuestra distribución media muestral para calcular las probabilidades de obtener una muestra con una determinada estadística utilizando el CDF.

**Ejercicio:**

Para repasar, consideremos un ejemplo de un restaurante que sirve hamburguesas de un cuarto de libra. Sus cuartos de libra pesan un promedio de 0,25 libras con una desviación estándar de 0,2 libras.

1. Digamos que pesamos todas las hamburguesas que cocinan para la cena en una noche determinada. 64 personas piden cuartos de libra. ¿Cuál es la probabilidad de que la media sea 0,24 libras o menos?

2. Configure los parámetros en la parte superior del código completando los valores para x, population_mean, population_std_devy samp_size.

3. Presiona Ejecutar. El CDF está impreso en el título del segundo gráfico. Tome nota mental de la probabilidad de que 64 hamburguesas tengan una media de 0,24 libras o menos.

La noche siguiente, hay un delicioso especial y menos personas piden la hamburguesa. Nuestro tamaño de muestra es ahora 10.

1. Establezca el tamaño de la muestra en el simulador en 10 y considere el error estándar. ¿Ha cambiado en la dirección que esperabas?

2. Digamos que su familia fue al restaurante y los cinco pidieron la hamburguesa. ¿Cuál es la probabilidad de que reciba hamburguesas con un peso promedio de 0,24 libras o menos?

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
import codecademylib3

# Set up parameters here:
x = None
population_mean = None
population_std_dev = None
samp_size = None

### Below is code to create simulated dataset and calculate Standard Error
standard_error = population_std_dev / (samp_size**.5)

this_cdf = round(stats.norm.cdf(x,population_mean,standard_error),3)

# Create the population
population = np.random.normal(population_mean, population_std_dev, size = 100000)

# Simulate the sampling distribution
sample_means = []
for i in range(500):
    samp = np.random.choice(population, samp_size, replace = False)
    sample_means.append(np.mean(samp))

mean_sampling_distribution = round(np.mean(sample_means),3)
std_sampling_distribution = round(np.std(sample_means),3)

std_error = population_std_dev / (samp_size **0.5)

sns.histplot(population, stat = 'density')
plt.title(f"Population Mean: {population_mean} \n Population Std Dev: {population_std_dev} \n Standard Error = {population_std_dev} / sq rt({samp_size}) \n Standard Error = {std_error} ")
plt.xlabel("")
plt.show()
plt.clf()

# Plot the sampling distribution
sns.histplot(sample_means, stat = 'density')
plt.axvline(x,color='r',linestyle='dashed')
plt.title(f"Sampling Dist Mean: {mean_sampling_distribution} \n Sampling Dist Standard Deviation: {std_sampling_distribution}\n CDF for x={x}: {this_cdf}")
plt.xlabel("")
plt.show()
```
