---
layout: default
title: Handling Missing Data
nav_order: 1
parent: Data Transformation
grand_parent: Exploratory Data Analysis
---


# Manejo de datos faltantes

Uno de los problemas más comunes en todo análisis de datos es la falta de datos y es casi omnipresente en todos los sistemas de datos. Los datos faltantes son lo que sucede cuando no hay valor para una variable determinada y pueden adoptar diversas formas. Si no manejamos adecuadamente estos datos faltantes, cualquier resultado o información que obtengamos podría ser significativamente incorrecto. ¡Pero no te preocupes! Existen muchas estrategias simples y confiables que pueden ayudarlo a lidiar con estos datos faltantes.

Para el resto de este artículo, supongamos que tenemos un conjunto de datos sobre las ventas en varias tiendas de ropa que somos responsables de limpiar y analizar. Nuestro trabajo es recopilar estos conjuntos de datos y asegurarnos de que estén completos (o que no les falte ningún dato). Cuando comenzamos a revisar cada conjunto de datos, notamos que algunas de nuestras variables tienen valores como `NULL`, `#N/A` o simplemente están vacías. ¿Qué podría estar pasando aquí?

### Por qué es importante gestionar los datos faltantes

Además de tener conjuntos de datos incompletos, ¿cuál es realmente el daño de tener datos faltantes? Como mencionamos anteriormente, un conjunto de datos solo es valioso si los datos son confiables y representan con precisión un conjunto de observaciones.

Los datos faltantes significan que existen lagunas potencialmente grandes en los datos y en lo que podemos aprender de ellos. Dado que los conjuntos de datos suelen describir una población (ya sea de sujetos o de eventos), el manejo de los datos faltantes dará como resultado una mejor comprensión de esa población. Desde una perspectiva estadística, manejar los datos faltantes significa que tendremos un mejor poder estadístico (la capacidad de aceptar o rechazar una hipótesis nula). Efectivamente, esto significa que podemos estar más seguros de que cualquier hallazgo de nuestros datos sea preciso.

Cuando tenemos datos completos, también minimizamos el riesgo de sacar conclusiones inexactas a partir de nuestro conjunto de datos. Por ejemplo, digamos que queremos analizar nuestras ventas de ropa en todas las tiendas y comprender qué colores de un producto en particular fueron nuestros más vendidos. Si una de nuestras tiendas no proporciona datos precisos sobre los colores de los productos vendidos, entonces podríamos llegar a una conclusión equivocada, lo que podría tener implicaciones en el presupuesto, adquisiciones, logística, etc.

## Por qué podrían faltar datos

Hay muchas razones por las que a un conjunto de datos le pueden faltar datos. Y si bien cada proceso de recopilación de datos tiene sus propias razones por las que pueden faltar datos, existen algunas explicaciones comunes.

### 1. Causas Sistemáticas

Una de las causas más simples de datos faltantes se debe a que nunca se proporcionaron en primer lugar. Aunque esto pueda parecer simple, en realidad es la razón más grande por la que pueden faltar datos en valores particulares. Si un proveedor de datos (ya sea una tecnología o un ser humano) nunca establece un valor para una variable dada, entonces el receptor de datos (conjunto de datos aguas abajo) no tendrá ningún dato que reportar.

Por ejemplo: Nuestras tiendas gestionadas deben reportar sobre las ventas de todos los productos, incluyendo el color específico del artículo vendido. Una de las tiendas no estaba al tanto de esta política y olvidó enviar esos detalles en su último informe. Por lo tanto, nuestro conjunto de datos consolidado se vería así:

| StoreID | ProductID | ProductColor | Price |
|---------|-----------|--------------|-------|
| A       | 1         | Red          | $20   |
| B       | 3         | Blue         | $18   |
| C       | 1         | NULL         | $20   |
| C       | 2         | NULL         | $25   |

### 2. Preocupaciones de Privacidad

La privacidad de los datos es un tema importante que muchos sistemas tecnológicos deben tener en cuenta. En algunas regiones o industrias, se da a los consumidores la opción de no proporcionar algunos o todos sus datos a las empresas. Esto puede llevar a la falta de datos para un subconjunto de usuarios.

Por ejemplo, nuestras tiendas de ropa dan a los clientes la opción de proporcionar su correo electrónico para mantenerse al día sobre las ventas actuales, o de optar por no recibir ese servicio si no quieren recibir correos electrónicos. Nuestros conjuntos de datos se parecerían a algo así:

| FirstName | LastName | Email                     | Phone          |
|-----------|----------|---------------------------|----------------|
| Rick      | Data     | rick.data@domain.com      | (555) 123-4321 |
| Ina       | Cognito  | #N/A                      | #N/A           |
| Selma     | Dealson  | selma.dealson@domain.com  | (555) 321-1234 |


### 3. Pérdida de Información

Aunque las tecnologías de datos modernas son bastante confiables, los problemas técnicos aún ocurren ocasionalmente. Si se produce una interrupción de conectividad en el momento equivocado, la entrada de datos podría ser interrumpida, lo que significa que los datos están incompletos, o los datos podrían corromperse.

Por ejemplo, nuestras tiendas de ropa tienen cámaras de seguridad cerca de las cajas registradoras y envían grabaciones de video a nuestro almacenamiento de datos. Si hay una interrupción de internet durante unos minutos, la transmisión de datos resultante tendrá un segmento de video faltante durante esos minutos.

## Identificar y verificar datos faltantes

Ahora que entendemos cómo se producen los datos faltantes y por qué son importantes, repasemos algunas estrategias de alto nivel sobre cómo identificar y verificar los datos faltantes.

1. En primer lugar, verifique que los datos se hayan cargado correctamente. ¡La forma más fácil de evitar la pérdida de datos es evitar que esto suceda en primer lugar! Dado que la mayoría de los casos de uso de datos faltantes se deben a un error sistemático, intente encontrar al culpable y corregir la fuente de datos defectuosa.

2. Intente mirar pequeños fragmentos de datos. A menudo, los datos faltantes pueden ser fáciles de detectar al observarlos directamente. Lo más común es que los científicos de datos, los analistas de datos y los profesionales de datos observen el principio o el final de un conjunto de datos, o recuperen una muestra aleatoria de datos para analizarlos. Si falta una cantidad significativa de datos, quedará evidente al hacerlo.

3. Mire las estadísticas de todo el conjunto de datos. A veces, sin embargo, los datos faltantes pueden ser difíciles de encontrar y pueden ser un pequeño subconjunto de datos. Un método rápido para descubrir si falta algún valor es recopilar algunas estadísticas resumidas básicas sobre nuestros datos. En particular, podemos contar cuántos valores hay en cada columna de su conjunto de datos y anotar cualquier discrepancia. Si una columna tiene un recuento inferior a nuestro número total de filas, ¡le faltan datos!

Si bien estas son sólo algunas técnicas, normalmente son suficientes para localizar cualquier dato faltante que tengamos. A partir de ahí, ahora tenemos que manejar esas entradas de datos, que cubriremos en secciones posteriores.

## Tipos de datos faltantes

Es una pregunta casi filosófica: ¿cómo podemos categorizar sistemáticamente tipos de nada? Pero identificar el tipo de falta es esencial para manejarla.

### ¿Por qué hay diferentes tipos de datos faltantes?

Así como los datos se pierden por diferentes motivos, también hay diferentes formas en que se pierden.

Durante el resto de este artículo, imaginaremos que tenemos un conjunto de datos de una campaña de encuestas de salud que realizamos en nuestra área local. Estas encuestas solicitaban información básica sobre cada persona y la participación era completamente voluntaria.

A la hora de intentar decidir qué tipo de datos faltantes tenemos, hay dos factores que debemos tener en cuenta:

### ¿Qué importancia tienen estos datos para el conjunto de datos más amplio?

Si bien cada variable en un conjunto de datos puede proporcionar cierta información que necesitamos, no todas las variables son iguales. Dependiendo de lo que estemos intentando aprender, algunos campos tienen más importancia que otros. Parece obvio que no podemos utilizar datos que no se ajusten a nuestras preguntas, pero te sorprendería la frecuencia con la que lo intentamos accidentalmente.

Por ejemplo, imaginemos que estamos recopilando datos para una encuesta de salud. Estamos recopilando el nivel de actividad (medido en minutos), la ubicación (ciudad) y la presión arterial. Si nos faltan muchos datos sobre la presión arterial, entonces no podemos utilizar ese conjunto de datos para responder preguntas sobre la presión arterial. Todavía podemos usarlo para comprender la relación entre ubicación y actividad, pero no la presión arterial.

### Diferentes tipos de datos faltantes

Pero los datos faltantes son más que faltas. Los datos faltantes se presentan en cuatro variedades:

- **Datos estructuralmente faltantes**: esperamos que estos datos falten por alguna razón 

- Falta completamente al azar (**MCAR**): la probabilidad de que cualquier punto de datos sea MCAR es la misma para todos los puntos de datos; este tipo de datos faltantes es en su mayoría hipotético.

- Falta al azar (**MAR**): la probabilidad de que cualquier punto de datos sea MAR es la misma dentro de los grupos de datos observados ; esto es mucho más realista que MCAR.

- Missing Not at Random (**MNAR**) hay alguna razón por la cual faltan datos
Profundicemos en algunos detalles más sobre este tipo de nada.



### Datos estructuralmente faltantes

"Un donut tiene un agujero, que es parte de lo que lo convierte en un donut." A veces, cuando nos faltan datos, no nos sorprende en absoluto. De hecho, en algunos escenarios, deberíamos tener datos faltantes, ¡porque tiene sentido! Esto es lo que son los Datos Estructuralmente Faltantes , y ocurre frecuentemente cuando hay uno o más campos que dependen de otro.

Digamos que una sección de nuestra encuesta de salud pregunta sobre afecciones respiratorias comunes y vemos una sección en nuestros datos que se parece a la siguiente:

| ID de participante | AsmaBandera | InhaladorFrecuencia | InhaladorMarca     |
|--------------------|-------------|---------------------|--------------------|
| 100                | VERDADERO   | Dos veces al día    | Rito de respiración|
| 101                | VERDADERO   | Una vez a la semana | Rito de respiración|
| 102                | FALSO       |                     |                    |
| 103                | VERDADERO   | Una vez al día      | Lejos del asma     |
| 104                | FALSO       |                     |                    |


Como podemos ver, dos filas no tienen ningún dato para la frecuencia y la marca. Esto es de esperarse ya que vemos en el AsthmaFlagcampo que estos participantes no usan ningún inhalador.

### Desaparecido completamente al azar (MCAR)

A veces simplemente faltan datos. Puede suceder por cualquier motivo, pero lo importante es que pudo haber sucedido ante cualquier observación. Para una variable dada, es igualmente probable que falten todas las observaciones. Más allá de eso, los datos del MCAR son realmente solo MCAR si es igualmente probable que a cada observación potencial le falte un valor para esa variable.

No hay lógica, ni fuerza externa ni comportamiento invisible. Es simplemente una casualidad completamente aleatoria que no haya datos. Los datos del MCAR exigen perfección estadística, lo cual es extremadamente raro porque, en la mayoría de los casos, existe alguna razón invisible por la que pueden faltar datos.

Pero volvamos a imaginar los datos de nuestra encuesta de salud. Los pasos son parte de los minutos de actividad y digamos que hay un error en el software que hace que el dispositivo no registre los pasos. Es completamente aleatorio si alguien tiene el error en su dispositivo o no, y sabemos por los desarrolladores que alrededor del 20% de los dispositivos están afectados. Por lo tanto, podríamos esperar que cualquier recuento de pasos faltantes sea MCAR. Los siguientes datos muestran una muestra de nuestros datos:


| ID de participante | Caminó    | Pasos (1000) |
|--------------------|-----------|--------------|
| 25                 | VERDADERO | 2.1          |
| 43                 | VERDADERO | 15           |
| 61                 | VERDADERO | 6            |
| 62                 | VERDADERO |              |
| 78                 | VERDADERO | 3            |
| 84                 | VERDADERO |              |
| 90                 | VERDADERO | 0.5          |
| 102                | VERDADERO | 1.5          |
| 110                | VERDADERO | 0.01         |
| 115                | VERDADERO | 4.1          |

Dado que todas estas personas han identificado que caminaron ese día, podemos suponer que Stepsno debería faltar el valor de. También conocemos este error y vemos que alrededor del 20% de nuestros encuestados no registran ningún paso. Por lo tanto, podemos suponer que los valores faltantes simplemente faltan por casualidad y que no hay una razón subyacente para la falta (en realidad, esta es una suposición muy grande, pero conocemos el error, por lo que parece estar bien).

Este tipo de datos faltantes tiene menos impacto en nuestros análisis que otros tipos, ya que existe una variedad de técnicas que podemos utilizar para aumentar la precisión de nuestro análisis. Podríamos imputar los datos tomando el número promedio de pasos. Podríamos interpolar los datos generando valores basados ​​en la distribución de los datos existentes. O podríamos eliminarlo sin invalidar nuestro análisis.

### Desaparecido al azar (MAR)

Missing at Random podría ser el más complejo de los tipos de datos que faltan. Si la probabilidad de que falten datos es diferente para diferentes grupos, pero es igualmente probable dentro de un grupo, entonces esos datos faltan al azar. Es una especie de híbrido entre perderse por una razón y perderse completamente al azar.

Por ejemplo, varios estudios científicos han demostrado que a las personas no les gusta informar su peso, especialmente cuando tienen un índice de masa corporal (IMC) fuera del rango “normal” (lo normal está entre comillas porque el IMC es una estadística cuestionable y “normal”). "está mal definido, pero es la etiqueta que suelen utilizar las básculas de IMC). En nuestro estudio, pedimos a los participantes que informaran sobre sus heighty weight.

Este es un ejemplo de datos faltantes al azar porque podemos suponer que algunos grupos no informan su peso por algún motivo, pero que cualquier persona dentro de ese grupo (es decir, alguien con un IMC no “normal”) tiene la misma probabilidad de no hacerlo. informando su peso. Veamos una muestra de los datos de nuestra encuesta.

| ID de participante | Altura (cm) | Peso (kg) |
|--------------------|-------------|-----------|
| 1                  | 176         | 84        |
| 2                  | 190         |           |
| 3                  | 160         | 61        |
| 4                  | 180         |           |
| 5                  | 184         |           |
| 6                  | 158         | 72        |
| 7                  | 152         | 50        |
| 8                  | 156         |           |
| 9                  | 194         | 104       |
| 10                 | 180         | 79        |

Como podemos ver, faltan algunos datos. Como sabemos que a algunas personas no les gusta informar su peso, y también sabemos que no todos sienten lo mismo, y no se aplica a toda nuestra población, estos datos faltan al azar (sabemos que esto no es lo que "aleatorio" generalmente significa, pero es la definición estadística).

Esto afectará nuestro análisis y limitará las afirmaciones que podemos hacer, pero todavía hay varias técnicas que podemos emplear y que nos permitirán utilizar los datos que se informaron.

### Desaparecido no al azar (MNAR)

Tres cajas de frutas: manzanas, naranjas y plátanos. Las cajas de naranjas y manzanas están llenas, pero la caja de plátanos está vacía. A un lado, hay una papelera con un folleto difícil de leer que muestra que los plátanos tienen un 50% de descuento.

Finalmente, a veces faltan datos por una buena razón que se aplica a todos los datos. Este puede ser el tipo más interesante porque es cuando la falta realmente cuenta su propia historia. ¡Aquí es cuando el valor de la variable que falta está relacionado con la razón por la que falta en primer lugar!

Veamos un ejemplo para comprender mejor MNAR. Los participantes de nuestro estudio fueron asignados a una clínica local para obtener una lectura de salud. Se les medirá la presión arterial, la altura y el peso, y el médico tomará notas después de una entrevista. Pero falta una parte de las medidas de peso. Los participantes no fueron responsables de sus propios informes, por lo que esto es inesperado. Podríamos suponer que no querían ser pesados, pero si profundizamos en los datos, podríamos obtener una imagen diferente. Probamos las siguientes agrupaciones:

- último peso informado para ver si faltan datos de grupos de IMC más altos o más bajos
- datos demográficos como edad, raza y género para ver si hay un patrón aquí
- fecha de recogida de datos

Digamos que descubrimos que todos los datos faltantes se recopilaron el mismo día. En nuestra clínica, las básculas funcionan con pilas. Si la báscula se queda sin pilas, alguien tendrá que comprar más. Los datos faltan por una razón, aunque esa razón no tiene ninguna relación con nuestro estudio.

Es una buena práctica asumir siempre que los datos son MNAR e intentar descubrir pistas sobre ese motivo. Como analista, probablemente nunca sabrá realmente por qué faltan datos, pero encontrar un patrón a menudo puede indicar si los datos MNAR son importantes para su estudio o no. Y saber eso puede ayudarle a decidir qué hacer con los datos que faltan.

### Datos sobre datos

Al intentar diagnosticar el tipo de falta, los datos sobre los datos (también conocidos como metadatos) pueden ser invaluables. La fecha y hora en que se recopilaron los datos, cómo se recopilaron, quién los recopiló, dónde se recopilaron, etc., pueden brindar pistas invaluables para resolver el problema de los datos faltantes.

Al final, gran parte del trabajo de análisis de datos resuelve misterios, y The Mystery of the Missing Data es uno de los más vendidos.

## Manejo de datos faltantes con eliminación

**Cómo eliminar datos de forma segura**

Ahora sabemos por qué los datos faltantes son importantes y entendemos las diferencias entre los diferentes tipos de datos faltantes. Ahora estamos listos para abordar algunos datos faltantes. Un método que podemos utilizar para combatir los datos faltantes es la eliminación.

La eliminación es, simplemente, cuando eliminamos algún aspecto de los datos que faltan para que el conjunto de datos resultante sea lo más completo posible, lo que lleva a análisis precisos. Dado que los datos faltantes no proporcionan una imagen completa de lo que sucedió en nuestras observaciones, no podemos confiar en ellos para el análisis, por lo que eliminar datos puede ser una buena solución.

### ¿Cuándo es seguro utilizar la eliminación?

¿Es realmente seguro eliminar datos?

Parece que eliminar datos podría causar más problemas que faltar datos en primer lugar. ¡Y en algunas situaciones, ese podría ser el caso! Hay algunos escenarios en los que eliminar datos es seguro y otros en los que no se recomienda.

El gran riesgo de la eliminación es que podríamos introducir sesgos o datos no representativos en el conjunto de datos. Si eliminamos demasiados datos, o el tipo de datos incorrecto, entonces el conjunto de datos resultante ya no describe con precisión lo que realmente sucedió. En general, es seguro eliminar datos cuando:

1. Son datos faltantes de MAR o MCAR. Podemos eliminar datos que caen en cualquiera de estas categorías sin afectar el resto de los datos, ya que asumimos que los datos faltan al azar. Sin embargo, si el porcentaje de datos faltantes es demasiado alto, entonces no podemos eliminar los datos; estaríamos reduciendo demasiado el tamaño de nuestra muestra. Tenga en cuenta que cada caso de uso de conjunto de datos o análisis tendrá una definición diferente de cuántos datos faltantes son "demasiados". Por ejemplo, los datos utilizados para predecir el fraude con tarjetas de crédito tendrían una menor tolerancia a la falta de datos que los datos de las encuestas de salud.

2. Los datos faltantes tienen una baja correlación con otras características de los datos. Si los datos que faltan no son importantes para lo que estamos haciendo, entonces podemos eliminarlos de forma segura.


## Tipos de eliminación

Dependiendo del tipo de análisis que estemos realizando, tenemos a nuestra disposición dos tipos de borrado:

- Listado
- Por parejas

Cada tipo de eliminación tiene sus ventajas y desventajas. Profundicemos para comprender las diferencias entre ellos. En los ejemplos siguientes, exploraremos cómo abordar algunos datos faltantes de encuestas de salud utilizando Python y el popular marco de manipulación de datos pandas.

### Eliminación por lista

La eliminación por lista , también conocida como análisis de caso completo, es una técnica en la que eliminamos toda la observación cuando faltan datos. Esta técnica particular generalmente se emplea cuando las variables faltantes afectarán directamente el análisis que intentamos realizar, generalmente con respecto a los datos faltantes de MAR o MCAR.

Echemos un vistazo a algunos datos de encuestas de salud, almacenados en un DataFrame llamado data.

Aquí tienes los datos formateados en Markdown:

| Número de participante | Sexo | Altura (cm) | Peso (kg) | Educación   |
|------------------------|------|-------------|-----------|-------------|
| 1                      | F    | 176         | 84        | Primario    |
| 2                      | M    | 190         |           | Secundario  |
| 3                      | F    | 160         | 61        |             |
| 4                      | F    | 180         | 78        | Primario    |
| 5                      | M    | 184         |           | Primario    |
| 6                      | F    | 158         | 72        |             |
| 7                      | M    | 152         | 50        | No graduado |
| 8                      | M    | 156         |           | Secundario  |
| 9                      | M    | 194         | 104       | Primario    |
| 10                     | F    | 180         | 79        | No graduado |

En nuestro conjunto de datos, notamos que a algunas filas les falta un valor para las variables Weighty Education. Si estamos estudiando la correlación entre Heighty Weight, no podemos usar esas filas como están actualmente. Para remediar esto, podemos eliminar cualquier fila a la que le falten datos de esta manera:

```python
# Drop rows that have any missing data
data.dropna(inplace=True) 
```

Al ejecutar el código anterior, nuestro conjunto de datos cambiará para que se vea como el siguiente, sin más valores faltantes:

| Número de participante | Sexo | Altura (cm) | Peso (kg) | Educación   |
|------------------------|------|-------------|-----------|-------------|
| 1                      | F    | 176         | 84        | Primario    |
| 4                      | F    | 180         | 78        | Primario    |
| 7                      | M    | 152         | 50        | No graduado |
| 9                      | M    | 194         | 104       | Primario    |
| 10                     | F    | 180         | 79        | No graduado |

En general, debemos tener cuidado al utilizar la eliminación por lista, ya que perdemos mucha información cuando eliminamos una fila completa. Cuando eliminamos filas como esta, disminuimos la cantidad de datos que podemos usar para el análisis. Esto significa que tendríamos menos confianza en la exactitud de las conclusiones que extraigamos del conjunto de datos resultante.

Como práctica recomendada, solo debemos utilizar la eliminación por lista cuando el número de filas con datos faltantes es relativamente pequeño para evitar un sesgo significativo. Cada conjunto de datos tendrá un contexto diferente sobre la cantidad de datos que es seguro eliminar. Un lugar seguro para comenzar es asumir que si faltan menos del 5% de los datos, entonces podemos utilizar la eliminación por lista de forma segura.

### Eliminación por pares

La eliminación por pares es una alternativa a la eliminación por listas y busca el contexto de lo que intentamos analizar. En la eliminación por pares, solo eliminamos filas cuando faltan valores en las variables que estamos analizando directamente. A diferencia de la eliminación por lista, no nos importa si faltan otras variables y podemos conservar esas filas.

Volvamos a nuestro conjunto de datos de ejemplo:


| Número de participante | Sexo | Altura (cm) | Peso (kg) | Educación   |
|------------------------|------|-------------|-----------|-------------|
| 1                      | F    | 176         | 84        | Primario    |
| 2                      | M    | 190         |           | Secundario  |
| 3                      | F    | 160         | 61        |             |
| 4                      | F    | 180         | 78        | Primario    |
| 5                      | M    | 184         |           | Primario    |
| 6                      | F    | 158         | 72        |             |
| 7                      | M    | 152         | 50        | No graduado |
| 8                      | M    | 156         |           | Secundario  |
| 9                      | M    | 194         | 104       | Primario    |
| 10                     | F    | 180         | 79        | No graduado |

Ahora supongamos que estamos estudiando la correlación entre Heighty Educationcon estos datos. Si empleáramos la eliminación por lista, terminaríamos eliminando 5 filas, ¡lo que representa el 50% de los datos en esta selección! Sin embargo, con la eliminación por pares mantenemos nuestro enfoque en los datos de los campos Educationy Height, ya que ese es el alcance de nuestro estudio. Podemos hacer esto con el siguiente código:

```python
data.dropna(subset=['Height','Education'], #only looks at these two columns
            inplace=True, #removes the rows and keeps the data variable
            how='any') #removes data with missing data in either 
```

Después de ejecutar el código anterior, solo terminamos eliminando dos filas de datos, en lugar de cinco.

| Número de participante | Sexo | Altura (cm) | Peso (kg) | Educación   |
|------------------------|------|-------------|-----------|-------------|
| 1                      | F    | 176         | 84        | Primario    |
| 2                      | M    | 190         |           | Secundario  |
| 4                      | F    | 180         | 78        | Primario    |
| 5                      | M    | 184         |           | Primario    |
| 7                      | M    | 152         | 50        | No graduado |
| 8                      | M    | 156         |           | Secundario  |
| 9                      | M    | 194         | 104       | Primario    |
| 10                     | F    | 180         | 79        | No graduado |

La eliminación por pares tiene la ventaja de retener la mayor cantidad de datos posible y, al mismo tiempo, permitirnos manejar los datos faltantes para nuestras variables clave. En general, la eliminación por pares es la técnica preferida a utilizar.

### Eliminación de variables

Hay otra táctica que podríamos emplear: eliminar una variable por completo. Si a una variable le faltan suficientes datos, entonces realmente no sabemos lo suficiente sobre esa variable para usarla en nuestro análisis, por lo que no podemos confiar en las conclusiones que extraigamos de ella.

Si bien esto puede parecer más fácil que las otras soluciones mencionadas y posiblemente efectiva, generalmente no queremos descartar variables enteras. ¿Por qué? En la mayoría de los contextos, tener más datos siempre es una buena idea y deberíamos trabajar para conservarlos si es posible. Cuantos más datos tengamos, más confianza podremos tener en que nuestras conclusiones realmente se están produciendo y no se deben al azar. Sólo deberíamos eliminar una variable como último recurso, y si a esa variable le falta una cantidad muy significativa de datos (al menos el 60%).


## Imputación única

Llenando los espacios en blanco uno a la vez. Imagínese: está viendo el ticker bursátil de su empresa favorita, esperando que baje de precio para poder aprovechar la oportunidad de invertir. Cada minuto pasa y va bajando más y más, casi hasta donde queremos. Entonces, de repente, ¡los datos desaparecen! Luego, tan rápido como desapareció, el precio volvió y ¡ha vuelto a subir! ¿Qué pudo haber pasado aquí?

**¿Qué son los datos de series de tiempo?**

Los datos bursátiles que estábamos observando se denominan conjunto de datos de series de tiempo . Estos conjuntos de datos tienen propiedades y capacidades analíticas interesantes porque rastrean datos durante (generalmente) períodos de tiempo establecidos. Si nos faltan datos en uno de estos períodos, tenemos una variedad de enfoques únicos para manejar estos datos faltantes.

Cuando faltan datos en las series de tiempo, tenemos la ventaja del contexto. Es decir, debido a que los datos muestran observaciones del mismo evento a lo largo del tiempo, podemos aprender sobre lo que está sucediendo y hacer una conjetura fundamentada sobre lo que podría haber sucedido en los datos faltantes. Los métodos de los que hablaremos en este artículo son específicos de datos de series temporales debido a esta propiedad.

**¿Es MNAR?**

Antes de que podamos comenzar a describir técnicas, debemos verificar que los datos que faltan puedan clasificarse como MNAR; estas técnicas suponen que ese es el caso. Puede resultar complicado comprender que los datos faltan de forma no aleatoria. ¿Cómo podemos verificar esto exactamente? Hay dos aspectos clave para poder describir con precisión los datos faltantes como MNAR:

1. **Utilice el conocimiento del dominio** : probablemente la forma más rápida de identificar MNAR es tener un amplio conocimiento de los datos y la industria en la que estamos trabajando. Los datos faltantes que caen en MNAR se verán y se sentirán diferentes de los datos "normales" en nuestro conjunto de datos. Con conocimiento del dominio, ya sea de nosotros mismos o de alguien de nuestro equipo, podríamos identificar la causa de la falta de datos. Por ejemplo, alguien podría saber que en una encuesta faltan datos en una columna en particular porque el participante estaba demasiado avergonzado para responder o no sabía la respuesta. Esto nos permitiría saber que los datos son MNAR.
2. **Analizar el conjunto de datos para encontrar patrones**: a medida que exploramos, filtramos y separamos nuestros datos, en última instancia deberíamos poder identificar algo en los datos faltantes que no se alinea con todo lo demás. Por ejemplo, si tenemos algunos datos de una encuesta, podríamos encontrar que los datos que faltan provienen casi exclusivamente de hombres mayores de 55 años. Si vemos surgir un patrón como este, podemos decir con confianza que es MNAR.

### ¿Qué podemos hacer?.

Ahora que hemos identificado los datos faltantes como MNAR, ¿qué podemos hacer para manejar los datos faltantes? Veamos un ejemplo de datos faltantes en una serie de tiempo:

| Marca de tiempo      | Valor     |
|----------------------|-----------|
| 10/01/2021 08:01     | 12        |
| 10/01/2021 08:02     | 13        |
| 10/01/2021 08:03     |           |
| 10/01/2021 08:04     | dieciséis |
| 10/01/2021 08:05     | 15        |

En este caso, nuestro conjunto de datos tiene un valor para cada minuto y nos falta un valor. La mejor manera de manejar estos datos faltantes es utilizar los datos que los rodean para "completar los espacios en blanco". Esto se llama imputación única y hay muchas maneras de abordar este problema.

## LOCF

LOCF significa Última observación realizada . Con esta técnica vamos a completar los datos que faltan con el valor anterior. LOCF se utiliza a menudo cuando vemos un patrón relativamente consistente que ha seguido aumentando o disminuyendo con el tiempo.

Veamos el siguiente conjunto de datos con datos sobre qué tan cómoda es la ubicación de una oficina, de un conjunto de empleados que usan relojes inteligentes. Estos datos se han adaptado de este conjunto de datos de Kaggle “Preferencias longitudinales de comodidad personal en interiores” para los fines de este artículo.


| tiempo                     | id_espacio | comodidad   |
|----------------------------|------------|-------------|
| 2021-03-16 08:22:00+08:00  | 125        | Confortable |
| 2021-03-16 09:37:00+08:00  | 125        | No cómodo   |
| 2021-03-18 08:11:00+08:00  | 125        | No cómodo   |
| 2021-03-18 09:48:00+08:00  | 125        | Confortable |
| 2021-03-18 13:35:00+08:00  | 125        | Confortable |
| 2021-03-18 15:23:00+08:00  | 125        | Confortable |
| 2021-03-18 15:53:00+08:00  | 125        |             |
| 2021-03-18 18:58:00+08:00  | 125        | Confortable |
| 2021-03-19 08:05:00+08:00  | 125        | No cómodo   |
| 2021-03-19 09:53:00+08:00  | 125        | Confortable |

Vemos que falta un valor en la séptima fila 2021-03-18 15:53:00+08:00 para la comodidad general de la oficina en este espacio en particular. Dado que estamos analizando datos de un espacio de oficina, podemos suponer que no habría un gran cambio en la comodidad general en el lapso de treinta minutos. Esto hace que el conjunto de datos sea un buen candidato para LOCF.

En Python, hay una variedad de métodos que podemos emplear:

Si sus datos están en un **DataFrame de pandas**, podemos usar el método `.ffil()` en una columna en particular:

```python
df['comfort'].ffill(axis=0, inplace=True)
# Applying Forward Fill (another name for LOCF) on the comfort column
```

Si nuestros datos están en una **matriz NumPy**, existe una biblioteca de uso común llamada `impyute` que tiene una variedad de funciones de series de tiempo. Para usar LOCF, podemos escribir el siguiente código:

```python
impyute.imputation.ts.locf(data, axis=0)
# Applying LOCF to the dataset
```

Con ambos métodos, buscamos llevar los datos de la comfortcolumna hacia adelante para completar los datos faltantes. En este caso, queremos mover nuestro Comfyvalor de la marca de tiempo anterior para completar los datos que faltan. Por lo tanto, nuestro conjunto de datos ahora se vería así:


| tiempo                     | id_espacio | comodidad   |
|----------------------------|------------|-------------|
| 2021-03-16 08:22:00+08:00  | 125        | Confortable |
| 2021-03-16 09:37:00+08:00  | 125        | No cómodo   |
| 2021-03-18 08:11:00+08:00  | 125        | No cómodo   |
| 2021-03-18 09:48:00+08:00  | 125        | Confortable |
| 2021-03-18 13:35:00+08:00  | 125        | Confortable |
| 2021-03-18 15:23:00+08:00  | 125        | Confortable |
| 2021-03-18 15:53:00+08:00  | 125        | Confortable |
| 2021-03-18 18:58:00+08:00  | 125        | Confortable |
| 2021-03-19 08:05:00+08:00  | 125        | No cómodo   |
| 2021-03-19 09:53:00+08:00  | 125        | Confortable |

Este conjunto de datos es un buen candidato para LOCF, ya que los datos anteriores a nuestros datos faltantes tienen una tendencia constante (la oficina está Comfyseis horas antes de nuestros datos faltantes). LOCF es un gran método cuando podemos asumir que los datos pasados ​​se trasladarán.

## NOCB

NOCB significa Próxima observación llevada hacia atrás y resuelve la imputación en la dirección opuesta a LOCF. NOCB generalmente se usa cuando tenemos datos más recientes y sabemos lo suficiente sobre el pasado para completar los espacios en blanco de esa manera. Veamos nuevamente nuestro conjunto de datos de comodidad de oficina para otro espacio de la oficina:

| tiempo                     | id_espacio | comodidad   |
|----------------------------|------------|-------------|
| 2021-03-12 14:49:00+08:00  | 2          | Confortable |
| 2021-03-17 15:30:00+08:00  | 2          | Confortable |
| 2021-03-17 15:33:00+08:00  | 2          | Confortable |
| 2021-03-17 15:53:00+08:00  | 2          | No cómodo   |
| 2021-03-18 11:23:00+08:00  | 2          |             |
| 2021-03-18 11:38:00+08:00  | 2          | Confortable |
| 2021-03-18 12:01:00+08:00  | 2          | Confortable |
| 2021-03-18 13:49:00+08:00  | 2          | Confortable |
| 2021-03-18 14:22:00+08:00  | 2          | Confortable |
| 2021-03-18 15:24:00+08:00  | 2          | Confortable |
| 2021-03-18 15:59:00+08:00  | 2          | Confortable |

Para este espacio en particular, nos falta el primer valor para el comfortnivel del 18 de marzo de 2021. Dado que podemos ver que el resto de los datos de todos los datos 2021-03-18 11:23:00+08:00comparten el mismo valor, este conjunto de datos sería un buen candidato para NOCB. .

De manera similar a LOCF, existen un par de técnicas comunes que podemos utilizar:

Si sus datos están en un **DataFrame de pandas**, podemos usar  método `.bfil()` en una columna en particular. Al “rellenar” (otro nombre para NOCB) nuestros datos, tomaremos datos del siguiente punto de datos de la serie temporal y los trasladaremos hacia atrás.

```python
df['comfort'].bfill(axis=0, inplace=True)
```

Para utilizar `impyute` para realizar NOCB, podemos escribir el siguiente código

```python
impyute.imputation.ts.nocb(data, axis=0)
```

En ambos bloques de código, estamos intentando tomar los datos.

| tiempo                     | id_espacio | comodidad   |
|----------------------------|------------|-------------|
| 2021-03-12 14:49:00+08:00  | 2          | Confortable |
| 2021-03-17 15:30:00+08:00  | 2          | Confortable |
| 2021-03-17 15:33:00+08:00  | 2          | Confortable |
| 2021-03-17 15:53:00+08:00  | 2          | No cómodo   |
| 2021-03-18 11:23:00+08:00  | 2          | Confortable |
| 2021-03-18 11:38:00+08:00  | 2          | Confortable |
| 2021-03-18 12:01:00+08:00  | 2          | Confortable |
| 2021-03-18 13:49:00+08:00  | 2          | Confortable |
| 2021-03-18 14:22:00+08:00  | 2          | Confortable |
| 2021-03-18 15:24:00+08:00  | 2          | Confortable |
| 2021-03-18 15:59:00+08:00  | 2          | Confortable |


## Otras 

Con LOCF y NOCB, asumimos que los datos directamente antes o después son lo suficientemente precisos como para completar cualquier dato faltante circundante. Sin embargo, existen otros enfoques que podemos probar dependiendo de nuestros datos. Al igual que con los métodos anteriores de imputación única, decidir qué método utilizar requiere conocimiento del dominio para completar correctamente los valores faltantes.

Una de esas alternativas es BOCF, o Baseline Observation Carryed Forward . En este enfoque, los valores iniciales de una variable determinada se aplican a los valores faltantes. Este es un enfoque común en los estudios médicos, particularmente en los estudios de fármacos. Por ejemplo, podríamos suponer que los datos faltantes para un nivel de dolor informado podrían volver al valor inicial. Esto sucedería si un medicamento no funcionara tan bien, por lo que podría ser una suposición segura si los datos tienen una tendencia en esa dirección.

Veamos un conjunto de datos de ejemplo. En estos datos, estamos tratando de estudiar alguna medida de bacterias en el cuerpo de un paciente después de que el paciente recibe un medicamento que se supone que las reduce. Aquí hay un conjunto de datos ficticios que podrían representar esto:

| marca de tiempo          | concentración |
|--------------------------|---------------|
| 2021-09-01 08:00:00      | 100           |
| 2021-09-01 08:15:00      | 98            |
| 2021-09-01 08:30:00      | 97            |
| 2021-09-01 08:45:00      | 98            |
| 2021-09-01 09:00:00      | N / A          |
| 2021-09-01 09:15:00      | 96            |
| 2021-09-01 09:30:00      | 94            |
| 2021-09-01 09:45:00      | 93            |
| 2021-09-01 10:00:00      | 90            |

Dado que estamos tratando de medir el efecto de un fármaco sobre algo en el cuerpo, no queremos asumir que LOCF o NOCB se aplicarán aquí, ya que eso podría introducir un error significativo en nuestro análisis. En su lugar, podríamos emplear BOCF, que podría verse así:

```python
# Isolate the first (baseline) value for our data
baseline = df['concentration'][0]

# Replace missing values with our baseline value
df['concentration'].fillna(value=baseline, inplace=True)
```

Otra alternativa de imputación única es WOCF, o Worst Observation Carried Forward . Con este tipo de imputación, queremos asumir que los datos son el peor valor posible. Esto sería útil si el propósito de nuestro análisis fuera registrar una mejora en algún valor (por ejemplo, si quisiéramos estudiar si un tratamiento está ayudando a la condición de un paciente en particular). Al completar los datos con el peor valor, podemos reducir los resultados potencialmente sesgados que en realidad no sucedieron.

Veamos otro conjunto de datos de ejemplo. En este conjunto de datos, rastreamos el nivel de dolor de un paciente durante el transcurso de un programa de terapia. El paciente califica su dolor en una escala del 1 al 10, siendo 10 el más alto.

| fecha       | dolor |
|-------------|-------|
| 2021-09-01  | 8     |
| 2021-09-02  | 8     |
| 2021-09-03  | 9     |
| 2021-09-04  | 7     |
| 2021-09-05  | N / A |
| 2021-09-06  | 6     |
| 2021-09-07  | 7     |
| 2021-09-08  | 5     |
| 2021-09-09  | 5     |

Este es un gran caso de uso para WOCF. Dado que realizamos un seguimiento del nivel de dolor de un paciente, con el objetivo de reducirlo, no queremos asumir que el paciente se siente mejor de lo que se siente, ya que eso podría afectar su recuperación a largo plazo. Por lo tanto, siempre querríamos asumir un nivel de dolor más alto que el real, para poder curarlos más. Esto se parecería al siguiente bloque de código:

```python
# Isolate worst pain value (in this case, the highest)
worst = df['pain'].max()

# Replace all missing values with the worst value
df['pain'].fillna(value=worst, inplace=True)
```

### ¿Cuales son las desventajas?

Los métodos de imputación única son muy útiles cuando nos faltan datos. Al utilizar estos métodos, podemos completar fácil y rápidamente los datos faltantes a partir de información contextual en el conjunto de datos. Sin embargo, existen algunas desventajas al utilizar métodos de imputación única.

La mayor desventaja de estos métodos es la posibilidad de agregar sesgos a un conjunto de datos. Cuando utilizamos la imputación única, asumimos que los datos que utilizamos para completar los espacios en blanco son confiables y precisos para esa observación. Sin embargo, este no es siempre el caso. Los datos a menudo cambiarán de maneras inesperadas. La imputación única ignorará estos cambios potenciales y "suavizará" nuestros datos, lo que podría conducir a resultados inexactos.

En general, la imputación única puede ser una técnica eficaz para manejar los datos faltantes en nuestros conjuntos de datos de series temporales. Si bien puede que no sea el enfoque más sofisticado, puede ser una solución rápida y útil en las circunstancias adecuadas.

## Imputación múltiple

Imagínese que está realizando un examen final para una clase de ciencias. A medida que avanzas en el examen, encuentras algunas preguntas cuyas respuestas no recuerdas, así que decides adivinar. Más adelante en el examen, habrá refrescado un poco su memoria porque algunas de las preguntas posteriores tienen pistas sobre las respuestas anteriores. Afortunadamente, puedes usar este nuevo conocimiento para regresar y completar las conjeturas anteriores. ¡Con suerte, obtendrás una mejor puntuación en el examen!

Este tipo de proceso iterativo ocurre todo el tiempo en varios sistemas analíticos y de datos, y es algo que también podemos aplicar a los datos faltantes. Este tipo de técnica se conoce como imputación múltiple .

### ¿Qué es la imputación múltiple?

La imputación múltiple es una técnica para completar datos faltantes, en la que reemplazamos los datos faltantes varias veces. La imputación múltiple, en particular, se utiliza cuando faltan datos en varias columnas categóricas de nuestro conjunto de datos. Después de haber probado diferentes valores, utilizamos un algoritmo para elegir los mejores valores para reemplazar los datos faltantes. Al hacer esto, con el tiempo podremos encontrar el valor correcto para los datos que faltan.

Existen numerosos algoritmos que podemos utilizar, todos con sus propias ventajas y desventajas. En general, el proceso general para la imputación múltiple sigue el siguiente diagrama de flujo.

![Imputacion Multiple](https://fer78docs.github.com/assets/images/imputacion_multiple.png)

Después de cada iteración, nuestros valores predichos para cada variable deberían volverse cada vez más precisos, ya que los modelos continúan refinándose para adaptarse mejor a nuestro conjunto de datos. El objetivo de la imputación múltiple es completar los datos faltantes para poder encontrar un modelo (generalmente normal o chi-cuadrado) que se ajuste mejor al conjunto de datos.

### Cuando 

La imputación múltiple es una técnica poderosa para reemplazar datos faltantes, pero existen algunos requisitos y consideraciones que se deben tener en cuenta antes de utilizar la imputación múltiple.

La imputación múltiple es mejor para los datos MAR, por lo que debemos asegurarnos de que nuestros datos se ajusten a esa descripción. Con los datos faltantes del MAR, se supone que existe una razón subyacente para que falten datos, y tenemos una buena comprensión de por qué faltan esos datos. Dado que no es completamente aleatorio, usar datos aleatorios para completar los espacios en blanco no es suficiente, por lo que debemos usar el contexto del resto de los datos como ayuda.

Suponiendo que cumplimos con los criterios para utilizar la imputación múltiple, nuestro conjunto de datos recibirá un par de beneficios clave.

1. Podemos asumir con seguridad que nuestros datos no estarán sesgados, ya que comenzamos el proceso con una asignación aleatoria de valores para los datos faltantes.

2. Debido a que el objetivo de la imputación múltiple es tener un modelo que se ajuste a los datos, podemos estar bastante seguros de que los datos resultantes serán una aproximación cercana a los datos reales. Esto incluiría cálculos como el error estándar y estadísticas generales.

### Cómo usarlo

Ahora que entendemos lo que intenta hacer la imputación múltiple, ¡continuemos y probémoslo! No tenemos que crear nuestro propio algoritmo para completar nuestros datos, ya que existen muchos enfoques diferentes y bibliotecas prediseñadas que pueden ayudarnos.

Un lugar para comenzar sería con el IterativeImputermódulo interno sklearn. Este módulo proporciona una biblioteca para realizar imputación múltiple, aprovechando los marcos existentes con sklearnDataFrames pandas. Supongamos que tenemos el siguiente conjunto de datos:


| X    | Y    | z   |
|------|------|-----|
| 5.4  | 18.0 | 7.6 |
| 13.8 | 27.4 | 4.6 |
| 14.7 |      | 4.2 |
| 17.6 | 18.3 |     |
| 49.6 | 4.7  |     |
| 1.1  | 48.9 | 8.5 |
| 12.9 |      | 3.5 |
| 3.4  | 13.6 |     |
| 16.1 | 1.8  |     |
| 10.2 | 42.7 | 4.7 |

Si quisiéramos utilizar el módulo `IterativeImputer` aquí, nuestro código se vería así:

```python
import numpy as np
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer
import pandas as pd

# Create the dataset as a Python dictionary
d = {
    'X': [5.4,13.8,14.7,17.6,np.nan,1.1,12.9,3.4,np.nan,10.2],
    'Y': [18,27.4,np.nan,18.3,49.6,48.9,np.nan,13.6,16.1,42.7],
    'Z': [7.6,4.6,4.2,np.nan,4.7,8.5,3.5,np.nan,1.8,4.7]
}

dTest = {
    'X': [13.1, 10.8, np.nan, 9.7, 11.2],
    'Y': [18.3, np.nan, 14.1, 19.8, 17.5],
    'Z': [4.2, 3.1, 5.7,np.nan, 9.6]
}

# Create the pandas DataFrame from our dictionary
df = pd.DataFrame(data=d)
dfTest = pd.DataFrame(data=dTest)

# Create the IterativeImputer model to predict missing values
imp = IterativeImputer(max_iter=10, random_state=0)

# Fit the model to the test dataset
imp.fit(dfTest)

# Transform the model on the entire dataset
dfComplete = pd.DataFrame(np.round(imp.transform(df),1), columns=['X','Y','Z'])

print(dfComplete.head(10))
```

Después de ejecutar nuestro código, nuestro conjunto de datos ahora se ve así (los valores imputados están en negrita ):


| X    | Y    | z   |
|------|------|-----|
| 5.4  | 18.0 | 7.6 |
| 13.8 | 27.4 | 4.6 |
| 14.7 | 17.4 | 4.2 |
| 17.6 | 18.3 | 5.6 |
| 11.2 | 49.6 | 4.7 |
| 1.1  | 48.9 | 8.5 |
| 12.9 | 17.4 | 3.5 |
| 3.4  | 13.6 | 5.7 |
| 11.2 | 16.1 | 1.8 |
| 10.2 | 42.7 | 4.7 |

Como podemos ver, los datos imputados se ven y se comportan de manera muy similar al resto del conjunto de datos. Con solo unas pocas líneas de código, podemos usar una biblioteca como esta para completar los datos faltantes lo mejor que podamos.