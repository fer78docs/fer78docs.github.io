---
layout: default
title: Exploratory Data Analysis
nav_order: 2
has_children: true
---

# Exploratory Data Analysis

El objetivo principal de esta sección es cubrir los fundamentos del Análisis de Datos Exploratorios (**EDA**) y comprender las diferentes etapas del proceso. 

{: .note }
EDA es un proceso de examen del conjunto de datos disponible para descubrir patrones, detectar anomalías, probar hipótesis y verificar suposiciones utilizando medidas estadísticas.

John Tuckey promovió la EDA entre los estadísticos para examinar y descubrir los datos y crear hipótesis más nuevas que podrían usarse para el desarrollo de un enfoque más nuevo en la recopilación y experimentación de datos.

### Etapas de EDA
- **Requisitos de Datos:** puede haber varias fuentes de datos para una organización. Es importante comprender qué tipo de datos se requieren para que la organización pueda recopilarlos, conservarlos y almacenarlos. Además de esto, se requiere categorizar los datos, numéricos o categóricos, y el formato de almacenamiento y difusión. 
- **Recopilación de datos:** los datos recopilados de varias fuentes deben almacenarse en el formato correcto y transferirse al personal de tecnología de la información adecuado dentro de una empresa. Como se mencionó anteriormente, se pueden recopilar datos de varios objetos sobre varios eventos utilizando diferentes tipos de sensores y herramientas de almacenamiento.
- **Procesamiento de datos:** el preprocesamiento implica el proceso de precurar el conjunto de datos antes del análisis real. Las tareas comunes implican exportar correctamente el conjunto de datos, colocarlos debajo de las tablas correctas, estructurarlos y exportarlos en el formato correcto.
- **Limpieza de datos:** los datos preprocesados ​​aún no están listos para un análisis detallado. Debe transformarse correctamente para una verificación de datos incompletos, verificación de duplicados, verificación de errores y verificación de valores faltantes. Estas tareas se realizan en la etapa de limpieza de datos, que implica responsabilidades como hacer coincidir el registro correcto, encontrar imprecisiones en el conjunto de datos, comprender la calidad general de los datos, eliminar elementos duplicados y completar los valores faltantes. 
- **EDA:** El análisis de datos exploratorio, como se mencionó anteriormente, es la etapa en la que realmente comenzamos a comprender el mensaje contenido en los datos. Cabe señalar que pueden ser necesarios varios tipos de técnicas de transformación de datos durante el proceso de exploración. 
- **Modelado y algoritmo:** desde la perspectiva de la ciencia de datos, los modelos generalizados o fórmulas matemáticas pueden representar o exhibir relaciones entre diferentes variables, como correlación o causalidad. Estos modelos o ecuaciones involucran una o más variables que dependen de otras variables para causar un evento. En general, un modelo siempre describe la relación entre variables independientes y dependientes. La estadística inferencial se ocupa de cuantificar las relaciones entre variables particulares.
- **Producto de datos:** cualquier software informático que utilice datos como entradas, produzca resultados y proporcione retroalimentación basada en los resultados para controlar el entorno se denomina producto de datos. Un producto de datos generalmente se basa en un modelo desarrollado durante el análisis de datos.
- **Comunicación:** Esta etapa se ocupa de difundir los resultados para que las partes interesadas finales utilicen el resultado para la inteligencia de negocios . Uno de los pasos más notables en esta etapa es la **visualización de datos**. La visualización se ocupa de técnicas de transmisión de información, como tablas, gráficos, diagramas de resumen y gráficos de barras para mostrar el resultado analizado.

### La importancia de la EDA

Diferentes campos de la ciencia, la economía, la ingeniería y el marketing acumulan y almacenan datos principalmente en bases de datos electrónicas. Se deben tomar decisiones apropiadas y bien establecidas utilizando los datos recopilados. Es prácticamente imposible dar sentido a conjuntos de datos que contienen más de un puñado de puntos de datos sin la ayuda de programas informáticos. Para estar seguro de los conocimientos que proporcionan los datos recopilados y tomar decisiones adicionales, se realiza minería de datos donde pasamos por procesos de análisis distintivos. El análisis de datos exploratorio es clave y, por lo general, es el primer ejercicio en la minería de datos. Nos permite visualizar datos para comprenderlos así como crear hipótesis para su posterior análisis. El análisis exploratorio se centra en la creación de una sinopsis de datos o conocimientos para los próximos pasos en un proyecto de minería de datos.

### Pasos en EDA

- **Definición del problema:** antes de intentar extraer información útil de los datos, es fundamental definir el problema empresarial a resolver. La definición del problema funciona como fuerza impulsora para la ejecución de un plan de análisis de datos. Las principales tareas involucradas en la definición del problema son definir el objetivo principal del análisis, definir los principales entregables, delinear las principales funciones y responsabilidades, obtener el estado actual de los datos, definir el cronograma y realizar un análisis de costo/beneficio. A partir de dicha definición del problema, se puede crear un plan de ejecución.
- **Preparación de datos:** este paso implica métodos para preparar el conjunto de datos antes del análisis real. En este paso, definimos las fuentes de datos, definimos esquemas y tablas de datos, comprendemos las características principales de los datos, limpiamos el conjunto de datos, eliminamos conjuntos de datos no relevantes, transformamos los datos y dividimos los datos en los fragmentos necesarios para el análisis.
- **Análisis de datos:** este es uno de los pasos más cruciales que se ocupa de las estadísticas descriptivas y el análisis de los datos. Las tareas principales implican resumir los datos, encontrar la correlación oculta y las relaciones entre los datos, desarrollar modelos predictivos, evaluar los modelos y calcular las precisiones. Algunas de las técnicas utilizadas para el resumen de datos son tablas de resumen, gráficos, estadísticas descriptivas, estadísticas inferenciales, estadísticas de correlación, búsqueda, agrupación y modelos matemáticos.
- **Desarrollo y representación de los resultados:** este paso implica presentar el conjunto de datos al público objetivo en forma de gráficos, tablas resumen, mapas y diagramas. Este también es un paso esencial ya que el resultado analizado del conjunto de datos debe ser interpretable por las partes interesadas del negocio, que es uno de los principales objetivos de EDA. La mayoría de las técnicas de análisis gráfico incluyen diagramas de dispersión, diagramas de caracteres, histogramas, diagramas de caja, diagramas de residuos, diagramas de medias y otros.

### Tipos de Datos

**Datos numéricos**

Estos datos tienen un sentido de medición involucrado; por ejemplo, la edad, la altura, el peso, la presión arterial, la frecuencia cardíaca, la temperatura, la cantidad de dientes, la cantidad de huesos y la cantidad de miembros de la familia de una persona. Estos datos a menudo se denominan datos **cuantitativos** en estadística. El conjunto de datos numéricos puede ser de tipo discreto o continuo.

- **Discretos:** Estos son datos que son contables y sus valores se pueden enumerar. Por ejemplo, si lanzamos una moneda, el número de caras en 200 lanzamientos de moneda puede tomar valores de 0 a 200 casos (finitos). Una variable que representa un conjunto de datos discreto se denomina `variable discreta`. La variable discreta toma un número fijo de valores distintos.
- **Datos Continuos:** Una variable que puede tener un número infinito de valores numéricos dentro de un rango específico se clasifica como dato continuo. Una variable que describe datos continuos es una `variable continua`. 

**Datos Categoricos**

Este tipo de datos representa las características de un objeto; por ejemplo, género, estado civil, tipo de dirección o categorías de las películas. Estos datos a menudo se denominan conjuntos de datos cualitativos en estadística. Una variable que describe datos categóricos se denomina `variable categórica`. Este tipo de variables pueden tener uno de un número limitado de valores. Es más fácil para los estudiantes de informática comprender los valores categóricos como tipos enumerados o enumeraciones de variables. Hay diferentes tipos de variables categóricas:

- Una variable categórica binaria puede tomar exactamente dos valores y también se la conoce como `variable dicotómica`. Por ejemplo, cuando creas un experimento, el resultado es éxito o fracaso. Por tanto, los resultados pueden entenderse como una variable categórica binaria .
- Las `variables politómicas` son variables categóricas que pueden tomar más de dos valores posibles. Por ejemplo, el estado civil puede tener varios valores, como anulado, divorciado, interlocutorio , legalmente separado, casado, polígamo, nunca casado, pareja de hecho, soltero, viudo, pareja de hecho y desconocido. Dado que el estado civil puede tomar más de dos valores posibles, es una variable politómica.

La mayor parte del conjunto de datos categóricos sigue escalas de medición `nominales` u `ordinales`. Hay cuatro tipos diferentes de escalas de medición descritas en estadística: nominal, ordinal, de intervalo y de razón. Estas escalas se utilizan más en las industrias académicas. Entendamos cada uno de ellos con algunos ejemplos.

**Nominal**  
Estos se practican para etiquetar variables sin ningún valor cuantitativo. Las escalas generalmente se denominan `etiquetas` . Y estas escalas son mutuamente excluyentes y no tienen ninguna importancia numérica. Por ejemplo: genero, idiomas, especicies, partes de algo, rangos taxonomicos, etc.

Las escalas nominales se consideran `escalas cualitativas` y las mediciones que se toman mediante escalas cualitativas se consideran `datos cualitativos` . Sin embargo, el avance de la investigación cualitativa ha creado confusión para ser considerada definitivamente como cualitativa. Si, por ejemplo, alguien usa números como etiquetas en el sentido de medición nominal, no tienen ningún valor o significado numérico concreto. No se puede realizar ningún tipo de cálculo aritmético sobre medidas nominales.

En el caso de un conjunto de datos nominal, ciertamente puedes saber lo siguiente:

- La **frecuencia** es la velocidad a la que aparece una etiqueta durante un período de tiempo dentro del conjunto de datos.
- La **proporción** se puede calcular dividiendo la frecuencia por el número total de eventos. Luego, podrías calcular el porcentaje de cada proporción.
- Y para visualizar el conjunto de datos nominal, puede utilizar un gráfico circular o un gráfico de barras.

**Ordinal**

La principal diferencia entre la escala ordinal y nominal es el orden. En escalas ordinales, el orden de los valores es un factor significativo. Un consejo fácil para recordar la escala ordinal es que suena como un orden . ¿Has oído hablar de la escala Likert , que utiliza una variación de una escala ordinal? Veamos un ejemplo de escala ordinal usando la escala Likert

- Totalmente de acuerdo
- De acuerdo
- Neutral
- En desacuerdo
- Totalmente en desacuerdo

Como se puede ver se reduce a cinco valores ordinales diferentes. Para hacerlo más fácil, considere las escalas ordinales como un orden de clasificación (1º, 2º, 3º, 4º, etc.). **Se permite el ítem de la mediana como medida de tendencia central; sin embargo, el promedio no está permitido.**


**Intervalo**

En las escalas de intervalo, **tanto el orden como las diferencias exactas entre los valores son significativos**. Las escalas de intervalo se utilizan ampliamente en estadística, por ejemplo, para medir tendencias centrales: `media`, `mediana`, `moda` y `desviaciones estándar`. Los ejemplos incluyen la ubicación en coordenadas cartesianas y la dirección medida en grados desde el norte magnético. La media, la mediana y la moda están permitidas en los datos de intervalo.


**Relación**

Las escalas de razones contienen orden, valores exactos y cero absoluto, lo que permite su uso en estadística descriptiva e inferencial. Estas escalas ofrecen numerosas posibilidades de análisis estadístico. Las operaciones matemáticas, la medida de tendencias centrales y la medida de dispersión y coeficiente de variación también se pueden calcular a partir de dichas escalas.

La siguiente tabla ofrece un resumen de los tipos de datos y medidas de escala:

| Provides:                                 | Nominal | Ordinal | Interval | Ratio |
|-------------------------------------------|:-------:|:-------:|:--------:|:-----:|
| The “order” of values is known            |         |    ✓     |    ✓     |   ✓   |
| “Counts,” aka “Frequency of Distribution” |    ✓    |    ✓     |    ✓     |   ✓   |
| Mode                                      |    ✓    |    ✓     |    ✓     |   ✓   |
| Median                                    |         |    ✓     |    ✓     |   ✓   |
| Mean                                      |         |         |    ✓     |   ✓   |
| Can quantify the difference between each value |   |         |    ✓     |   ✓   |
| Can add or subtract values                |         |         |    ✓     |   ✓   |
| Can multiply and divide values            |         |         |          |   ✓   |
| Has “true zero”                           |         |         |          |   ✓   |


### Comparación de EDA con el análisis clásico y bayesiano

Existen varios enfoques para el análisis de datos. Los más populares que son relevantes para este libro son los siguientes:

- **Análisis de datos clásico:** para el enfoque de análisis de datos clásico, a la definición del problema y al paso de recopilación de datos le sigue el desarrollo del modelo, al que sigue el análisis y la comunicación de resultados.
- **Enfoque de análisis de datos exploratorio:** para el enfoque EDA, sigue el mismo enfoque que el análisis de datos clásico, excepto que se intercambian la imposición del modelo y los pasos del análisis de datos. La atención se centra principalmente en los datos, su estructura, valores atípicos, modelos y visualizaciones. Generalmente, en EDA, no imponemos ningún modelo determinista o probabilístico a los datos.
- **Enfoque de análisis de datos bayesiano:** el enfoque bayesiano incorpora conocimientos previos sobre distribución de probabilidad en los pasos del análisis, como se muestra en el siguiente diagrama. Bueno, en pocas palabras, la distribución de probabilidad previa de cualquier cantidad expresa la creencia sobre esa cantidad en particular antes de considerar alguna evidencia. 

El siguiente diagrama muestra tres enfoques diferentes para el análisis de datos que ilustran la diferencia en sus pasos de ejecución:

graph TD
    classDef green fill:#9f6,stroke:#333,stroke-width:2px;
    subgraph "Classical Data Analysis"
        A[Problem Definition] --> B[Data Collection]
        B --> C[Model Development]
        C --> D[Data Analysis]
        D --> E[Results Communication]
    end
    subgraph "Exploratory Data Analysis"
        F[Problem Definition] --> G[Data Collection]
        G --> H[Data Analysis]
        H --> I[Model Development]
        I --> J[Results Communication]
    end
    subgraph "Bayesian Data Analysis"
        K[Problem Definition] --> L[Data Collection]
        L --> M[Model Development]
        M --> N[Prior Distribution]
        N --> O[Data Analysis]
        O --> P[Results Communication]
    end
    class D,H,O green


Los analistas y científicos de datos combinan libremente los pasos mencionados en los enfoques anteriores para obtener información significativa de los datos. Además de eso, es esencialmente difícil juzgar o estimar qué modelo es mejor para el análisis de datos. Todos ellos tienen sus paradigmas y son aptos para diferentes tipos de análisis de datos.

