---
layout: default
title: Communicating Findings
nav_order: 6
has_children: true
---

#Comunicación de los hallazgos de la ciencia de datos
Aprenda a comunicar eficazmente análisis de ciencia de datos.

La ciencia de datos se trata tanto de contar historias como de codificar y discutir datos. La razón por la que los científicos de datos tienen tanta demanda recientemente es por su capacidad para traducir el desempeño y la salud de una empresa mediante la recopilación de información que antes no estaba disponible a partir de sus datos. Puede parecer algo fácil y obvio en este momento, pero en realidad, los datos de una empresa pueden estar tan confusos y desestructurados que los simples mortales no puedan encontrarles sentido.

Mejores prácticas para comunicar los hallazgos de la ciencia de datos
Un científico de datos que explica a un grupo de gerentes de producto que la covarianza entre dos variables no muestra una relación lineal visible es como si Dumbledore le enseñara a un grupo de Jedi cómo conjurar un Patronus. Dos mundos diferentes. No computa.

La transformación de los resultados del análisis de datos por parte de los científicos de datos en medios fácilmente accesibles y comprensibles para que todos los entiendan es en realidad una de las habilidades más importantes en el trabajo.

Después de que un científico de datos completa una investigación en profundidad sobre algún conjunto de datos, los resultados de esta investigación deben convertirse de alguna manera en un resumen simplificado para que otros lo observen y comprendan. Por lo general, este tipo de resúmenes se escriben como comentarios a uno de los tickets asignados o, más a menudo, como diapositivas en una presentación que luego se analiza verbalmente con más detalle.

## Conozca a su audiencia

Antes de comenzar el proceso de comunicar sus hallazgos, es importante poner en perspectiva quién es realmente su audiencia. Todo el tono de su presentación depende y cambia según cómo la perciban las personas.

Imagine que está presentando información sobre propinas y transacciones de facturación de restaurantes a un grupo de propietarios de restaurantes. ¿Cómo sería tu presentación? Ahora imagina que estás mostrando los mismos datos a un grupo de desarrolladores que están creando una aplicación de entrega de comida. ¿En qué se diferenciaría su presentación para esta audiencia de la primera?

Si pone demasiada jerga matemática/estadística en un informe o presentación para personas sin conocimientos técnicos, le pedirán que les defina cosas o que les aclare ciertos conceptos. Sin embargo, entréguelo de forma demasiado simplificada a una audiencia técnica y le preguntarán cómo obtuvo los resultados.

Necesitas encontrar la combinación perfecta entre estos dos para adaptar correctamente tu comunicación.

### Estructura la secuencia de tu historia

Una estructura define en qué secuencia usted revela los resultados de su análisis. Durante este proceso, también desea determinar en qué profundidad analítica desea profundizar. Esta es una oportunidad para resaltar solo las observaciones más importantes que usted obtuvo de los datos a través de su exploración.

El tipo de observaciones que desea incluir es el que más se relaciona con el objetivo final de la investigación. Si, por ejemplo, nota una tendencia completamente ajena en el comportamiento del usuario en relación con su análisis, guárdela como un punto de discusión adicional dentro de un apéndice al final en algún lugar de sus diapositivas o informe. A veces, un miembro de la audiencia también puede captar este detalle adicional y preguntarle durante una sesión de preguntas y respuestas. Este tipo de estructura le permite ir rápidamente a su apéndice y seleccionar una diapositiva que profundiza en un detalle aludido anteriormente.

### Encuentre y seleccione datos relevantes

¿Es absolutamente necesario discutir todos los conocimientos que recopiló a partir de sus datos? ¿Le ayuda a transmitir su punto final o es simplemente una tontería adicional que cree que es interesante como científico de datos?

A veces, las estadísticas adicionales que ayudan a un científico de datos a tomar un camino de investigación particular pueden no ser los conocimientos ideales para compartir con la audiencia. Si una serie de características son vagas en su representación inmediata y no explican algún tipo de resultado solicitado, es mejor pasarlas por alto.

El siguiente es un ejemplo de visualización de los datos de transacciones de restaurante y propinas. La visualización no ha tenido ajustes ni argumentos añadidos. En el eje X tenemos el monto total de la factura y en el eje Y tenemos el monto de la propina. Las etiquetas son pequeñas, no hay título y lo único que se puede extraer inmediatamente es que cuanto más alto es el billete, mayor es la propina, lo que parece obvio.

Este es un error de novato en el campo de la ciencia de datos cuando se intenta comunicar hallazgos a través de visualizaciones. No deberíamos mirar un gráfico y pensar ¿Cuál es el propósito de este gráfico?

![scatter](https://fer78docs.github.com/assets/images/plain_scatter.webp)

Un poco soso, ¿no? Más adelante en el artículo nos centraremos en hacerlo parecer un poco más útil y más fácil de entender.

Elija métodos adecuados de visualización.
Contrariamente a la creencia popular, sus datos generalmente tienen un conjunto finito de tipos de visualización que probablemente debería aplicarles. Algunos ejemplos incluyen gráficos de barras y diagramas de recuento para datos categóricos, gráficos de series temporales para datos de tipo fecha y hora y diagramas de líneas/diagramas de caja o histogramas para datos de tipo continuo y numérico.

Por ejemplo:

![scatter](https://fer78docs.github.com/assets/images/bubble-graph.webp)

¿Qué intenta decirnos esta visualización?

Usar la combinación incorrecta aquí no sólo terminará confundiendo a la audiencia, sino que también podría sacrificar la confianza de la audiencia en usted y su capacidad para realizar análisis confiables. Por ejemplo, ver una visualización del tipo diagrama de burbujas en un sitio web o en una revista puede parecer interesante al principio, pero escribir tanto código para poner círculos detrás de 7 números es simplemente una tontería. La visualización anterior podría haberse puesto fácilmente en una tabla sin ningún esfuerzo y mucho más rápida de leer.

### Complejidad y propósito

No dejes que tus visualizaciones se vuelvan demasiado ruidosas. No es necesario mostrar un gráfico de cada combinación posible de correlaciones para cada variable.

Concéntrese solo en las características importantes dentro de su conjunto de datos para evitar presentar demasiada información a su audiencia a la vez. Esto incluye definir umbrales máximos para cuántas tendencias segmentadas o agrupadas se deben representar en una visualización.

Otro error que se comete al intentar comunicar una gran cantidad de datos es intentar incluirlos todos en una sola visualización. En los casos en los que desee trazar múltiples tendencias en sus datos, a veces puede ser una mejor idea dividirlos en gráficos separados.

El siguiente gráfico de líneas muestra la relación lineal entre el monto de la factura y las propinas en diferentes días. En realidad, solo se incluyen cuatro días en este conjunto de datos, pero si eliminamos la leyenda y preguntamos qué ve, la única respuesta que esperaríamos escuchar es espagueti :

![scatter](https://fer78docs.github.com/assets/images/spaghetti.webp)

Dado que la tendencia del monto de la propina parece permanecer relativamente similar en diferentes días, no hay ninguna razón real para visualizar cada día por separado. La única razón por la que el viernes parece un comportamiento más estable es que hay menos datos. Si este conjunto de datos contuviera algún tipo de variable de fecha y hora y fuera mucho más grande, otro enfoque sería promediar o sumar las transacciones por cada fecha contenida en el eje X. En este caso, tendría que agregar marcas adicionales en el eje X para ayudar a indicar los días de la semana, pero se vería mucho más limpio.

### Conclusión

Los datos siempre empiezan siendo confusos, feos y confusos. La forma más sencilla de lograr que la audiencia se familiarice con un concepto centrado en datos es a través de la visualización. Cuando utilice la visualización para presentar sus hallazgos, recuerde lo siguiente:

- Las visualizaciones son como chistes, si no las entiendes inmediatamente… probablemente no sean muy buenas.
- Sepa quién es su audiencia.
- Asegúrese de que su visualización tenga un propósito y esté de alguna manera vinculada a la conclusión final de sus hallazgos porque los temas irrelevantes a veces hacen que su audiencia pierda el interés.
- Asegúrese de utilizar datos relevantes.
- Elija un método adecuado de visualización.
- Utilice etiquetas grandes y cortas en sus gráficos para que las personas puedan entender rápidamente lo que realmente significan los marcadores o las líneas en un gráfico.
- Intente simplificar los conceptos sin utilizar jerga técnica que haga que los datos vuelvan a parecer confusos.

A medida que se aventure fuera del análisis y se adentre en otras partes del espectro de la ciencia de datos, habrá factores adicionales que entrarán en juego para comunicar mejor sus hallazgos; sin embargo, no importa en qué área de la ciencia de datos se centre, las prácticas mencionadas aquí siempre seguirán siendo relevantes.


