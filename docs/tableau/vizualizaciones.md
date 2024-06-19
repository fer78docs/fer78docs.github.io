---
layout: default
title: How-to
nav_order: 1
parent: Tableau's
---

# Realizar Vizualizaciones en Tableau

## Trabajar primero en papel

Con tantas opciones de visualización en Tableau, puede ser más fácil crear tonterías que crear una visualización significativa. Y con la cantidad de campos de datos y marcas disponibles para nosotros, es fácil que el lienzo se sature o se vuelva incoherente. Entonces, antes de saltar a Tableau, demos un paso atrás y primero esbocemos nuestra visualización en una hoja de papel.

Al crear una visualización, tenga en cuenta su propósito o pregunta de investigación, quiénes son los espectadores y qué acciones pueden realizar los usuarios a partir de estos conocimientos. La cuestión no es predecir cómo será la visualización final, aunque eso puede sucederle a investigadores que ya están muy familiarizados con sus datos. En cambio, estamos tratando de tener una idea de cómo nuestras variables pueden funcionar juntas colocándolas en ejes diferentes.

### Veamos un ejemplo:

**Situación:** Leslie es especialista en programas universitarios y quiere comprender mejor el desempeño en los exámenes en todo el departamento de Biología. Tienen datos sobre puntuaciones de exámenes, instructor, especialidad del estudiante, tamaño de la clase y año de estudio.

**Propósito:** Determinar qué factores pueden afectar los puntajes de los exámenes de los estudiantes.

**Preguntas de investigación:**

- ¿Las puntuaciones de los exámenes difieren entre las especialidades?
- ¿Las puntuaciones de los exámenes difieren entre los niveles de grado?
- ¿Existe una relación entre el tamaño de la clase y la puntuación del examen?
- ¿Qué instructores tienen el puntaje promedio más alto en los exámenes?
- Visores: administradores de departamento

**Ideas prácticas:** ¿Qué puede proponer Leslie al departamento si se encuentran diferencias en las puntuaciones de los exámenes? Podría sugerir cambiar la capacidad de las clases, limitar cursos específicos a estudiantes de último año, evaluaciones de programas de estudios o exigir requisitos previos.

Con estos factores en mente, Leslie puede decidir qué gráficos son los más apropiados. Un diagrama de dispersión podría funcionar mejor para el punto 3 porque el objetivo es ilustrar una relación entre dos medidas numéricas. Mientras que un gráfico de barras podría funcionar para mostrar diferencias entre categorías en el n.º 1 o n.º 2. y el número 4 podría representarse con una tabla simple. (¡Siéntete libre de hacer un boceto de cada uno para ver lo que queremos decir! Podemos hacer esto con los datos imaginarios de Leslie, porque recuerda que estamos pensando en cómo interactúan los diferentes campos entre sí en lugar de tratar de predecir con precisión cómo se verán los gráficos resultantes. .) Debido a que tendrán múltiples visualizaciones para abordar múltiples preguntas, un panel puede ser la mejor opción.

Comenzar en papel es útil para formular las preguntas que su visualización busca responder y reducir las piezas necesarias para elaborar su historia.

Más sobre la narración
Obtenga más información sobre cómo utilizar Tableau para contar una historia visual de forma eficaz.

Una imagen de alguien dibujando un gráfico simple en una pizarra para intentar hacer coincidir el gráfico más complejo en una burbuja de pensamiento sobre su cabeza.

Tableau es una herramienta fantástica con muchas opciones para visualizar datos. Con tantas opciones a nuestra disposición, es útil seguir los pasos para diseñar una historia y revisar las mejores prácticas.

Parte I: Diseñar una historia
Muchas visualizaciones de datos y paneles de control exitosos comienzan trabajando primero en papel. Aquí es donde comienza el proceso de narración.

Piensa en lo siguiente y escribe o dibuja lo que te viene a la mente:

¿Cuál es el objetivo o las preguntas centrales de la visualización? En otras palabras, ¿Qué pregunta quieres responder?
¿Quién es el público objetivo?
¿Qué datos se utilizarán y qué ideas se pueden extraer de ellos?
Con estas preguntas en mente, podemos empezar a delinear el viaje del espectador. Si estamos presentando un argumento, es posible que deseemos identificar datos de respaldo y pensar en la mejor secuencia para presentarlos. Para una narrativa, es posible que deseemos darles a los espectadores la opción de explorar los datos para llegar a su propia conclusión. o podemos optar por llevar al espectador a una conclusión específica.

Generalmente, la mejor manera de presentar una historia en Tableau es mediante un panel, que es una combinación de varias visualizaciones que se pueden organizar en una sola presentación, como un póster interactivo. También podemos optar por utilizar una historia de Tableau, que es una serie de visualizaciones o paneles. Las historias nos permiten usar botones para navegar por las vistas, como pasar las páginas de un libro.

Tableau ofrece algunos enfoques de uso común para contar historias con datos que pueden ayudarnos a encontrar el enfoque en una visualización o panel.

Cambio a lo largo del tiempo: utiliza datos temporales para ilustrar tendencias o cambios.
Profundizar: comienza con el panorama más amplio y luego entra en detalles más finos.
Alejar: comienza con un detalle más pequeño y luego pasa a una imagen amplia y de alto nivel.
Contraste: representa diferencias entre más de 2 sujetos
Intersecciones: explora cómo pueden converger 2 dimensiones inicialmente separadas
Factores: toma un tema más amplio y lo divide en factores (tipos/categorías)
Valores atípicos: aspectos destacados y perfiles atípicos en los datos
Cualquiera que sea el enfoque adecuado para sus datos, recuerde verificarlo mientras crea y modifica visualizaciones. Intente adoptar una mentalidad de principiante e imagine que está viendo su panel de control por primera vez. ¿Responde a las preguntas que esperaba abordar? Si hay un argumento central, ¿está claro para el espectador? Si el panel está diseñado para la exploración, ¿es fácil de navegar?

Parte II: Mejores prácticas
Ahora que tenemos una dirección más centrada en la narración de historias, cubramos algunas de las mejores prácticas para comunicarnos a través de visualizaciones de datos.

Elija el gráfico correcto
Esto puede parecer básico, pero es una parte crucial del diseño general y la legibilidad del proyecto final. Tableau nos brinda la flexibilidad de representar nuestros datos de numerosas maneras. A continuación se muestran algunas de las opciones de gráficos de ejemplo de Tableau basadas en la relación de los datos.

Cambios temporales: gráfico de líneas, gráficos de áreas
Partes de un todo: gráfico circular, mapa de árbol
Relación entre variables: diagrama de dispersión
Distribución: histograma, diagrama de caja
Clasificación o magnitud: gráfico de barras, burbujas empaquetadas
Con el gráfico adecuado, todo lo demás resulta más fácil. (En ese sentido, si siente que está luchando contra su visualización en cada paso... considere probar un nuevo tipo de gráfico o sacar el lápiz y el papel viejos para ver si puede hacerlo funcionar lejos de los desafíos tecnológicos).

No lo compliques demasiado
Al crear paneles e historias, casi siempre es mejor mantener las cosas simples. Limite la cantidad de visualizaciones en un panel y trate de no saturar una vista, manteniendo las cosas simples para que los espectadores las entiendan. Puede resultar útil limitarse a 3 o 4 visualizaciones en un panel y eliminar cualquier elemento que no contribuya a la historia.

Equilibrio visual
En arte y diseño, el equilibrio visual es la sensación de "claridad ponderada en una composición". En otras palabras, la forma en que se organizan las visualizaciones debería ayudar a que tengan sentido, no hacer que las cosas parezcan confusas, desordenadas o abarrotadas. Las cosas más importantes deben resaltarse visualmente a través del tamaño y la posición, y otros elementos deben apoyar sin distraer ni competir.

Como diseñadores, debemos intentar mantener una sensación de equilibrio en nuestras visualizaciones mediante la utilización de elementos como la posición, el tamaño, el color, las formas y las texturas. Hay una cantidad infinita de información sobre el buen diseño, pero si está buscando algo básico, lea más sobre las formas básicas de equilibrio visual en la fuente vinculada al final del artículo.

Uso de propiedades estéticas para transmitir el tema de una historia
Otro paso para una narración eficaz es fortalecer nuestra historia reforzando un tema visual en todo momento. Por ejemplo, si analizamos datos de medallas de los Juegos Olímpicos, es posible que deseemos utilizar los colores de las medallas e incorporar el logotipo de los Juegos Olímpicos en el título. También podemos considerar nuestro tema al elegir fuentes y gráficos. Estas opciones pueden (sutil o contundentemente) ayudar al espectador a comprender rápidamente de qué se trata el panel.

Tomemos como ejemplo las visualizaciones del conjunto de datos de erupciones volcánicas. Cuando pensamos en volcanes, podemos evocar imágenes de flujos de lava caliente, cenizas espesas, formas montañosas y colores ardientes. Siguiendo la línea de estas imágenes, elegimos utilizar gris carbón, rojos y naranjas en la combinación de colores. Las fuentes utilizadas fueron atrevidas y llamativas. Hicimos un juego con una señal de peligro y una forma parecida a un fuego en el título. El uso de un mapa de áreas con picos y valles fue intencionado y sirvió para imitar la silueta del terreno volcánico.

Para practicar más, consulte este panel que utiliza datos de Rotten Tomatoes sobre la rentabilidad de las películas. Vea si puede identificar qué elementos visuales ayudan a transmitir el tema en estos datos.

Uniéndolo todo junto
Una vez que haya terminado de crear su visualización, vuelva a visitarla y hágase estas preguntas:

¿Cumple la visualización su propósito, es decir, responder a la pregunta central planteada?
¿Mi enfoque narrativo y mis elecciones de gráficos son apropiados y fáciles de seguir?
¿Estoy siguiendo las mejores prácticas de visualización?
¿He utilizado propiedades estéticas para realzar mi historia?
Cuanto más practiques la narración a través de visualizaciones, más fácil e intuitivo te resultará. Te animamos a que sigas haciendo visualizaciones y sigas preguntándote "¿Por qué se ve tan bien ?" (¡o algo así como " no tan bueno "!) cuando vea visualizaciones de datos sorprendentes en la naturaleza y siga participando en nuestros foros de Codecademy y la comunidad de Tableau Public, que son recursos fantásticos de inspiración, comentarios y motivación.

Fuentes :

Mejores prácticas de narración: https://help.tableau.com/current/pro/desktop/en-us/story_best_practices.htm

Elegir el gráfico correcto: https://help.tableau.com/current/pro/desktop/en-us/what_chart_example.htm

Equilibrio visual: https://wikieducator.org/Artistic_principles/Visual_balance