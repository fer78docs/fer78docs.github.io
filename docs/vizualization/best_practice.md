---
layout: default
title: Best Practices
nav_order: 4
parent: Data Visualization
---

# Mejores prácticas de visualización de datos

Una breve descripción general de qué considerar al realizar visualizaciones de datos.

## Introducción

Como científico de datos, una parte esencial de su función es presentar y comunicar eficazmente sus hallazgos tanto a sus pares como a las partes interesadas clave. Si bien algunas partes interesadas pueden estar bien versadas en las últimas técnicas de aprendizaje automático, la mayoría quedan fuera del ámbito de la ciencia de datos. Es por eso que una visualización clara de los datos es esencial para contar eficazmente la historia de sus datos.

Es importante tener en cuenta la pregunta de investigación al crear imágenes. En general, su análisis debe contar la historia completa de los datos y las imágenes deben ayudar en ese proceso. Al igual que los cuentos infantiles, las imágenes pueden brindarle al lector una enorme cantidad de información en una pequeña cantidad de espacio. Del mismo modo, las imágenes que cree deben decirle al lector la información que transmiten los datos .

## Que considerar

En general, sus imágenes deben incluir ejes claramente etiquetados y espaciados uniformemente. Se deben utilizar leyendas y colores al representar datos en varios grupos. Profundicemos en esto.

### Color

A la hora de elegir los colores, lo mejor es evitar los colores complementarios, como el rojo y el verde. Este tipo de combinaciones no dejan diferencias perceptibles entre los tonos para los lectores daltónicos. Hay paletas de colores integradas en las bibliotecas de visualización de Python que pueden facilitar un poco la elección de qué combinación de colores utilizar. Aquí hay algunas variedades de paletas de colores en la biblioteca seaborn.

### Gráfica de barras

Podemos utilizar gráficos de barras para ayudar al lector a comprender y visualizar mejor las diferencias relativas entre grupos (es decir, cuando el eje x está formado por datos categóricos). En el siguiente ejemplo, analizaremos datos hipotéticos sobre el valor influyente de diferentes tipos de medios entre los millennials y la generación X.

Vemos que la televisión tiene el mayor valor de influencia tanto para los millennials como para la generación X, los medios de comunicación en el cine tienen más impacto para los millennials en comparación con los de la generación X, y los medios impresos son los preferidos por la generación X, en comparación con los millennials.

![Serie temporal](https://fer78docs.github.io/assets/images/media_plot.webp)

Si quisiéramos utilizar gráficos de barras para observar los promedios entre grupos, podríamos agregar barras de error que incluyan los límites superior e inferior. Sin embargo, los promedios entre grupos podrían comunicarse mejor utilizando un diagrama de dispersión con barras de error porque los gráficos de barras muestran información agregada en lugar de un número.

## Gráficos de líneas

Los gráficos de líneas son útiles cuando el eje x refleja una variable cuantitativa, como el tiempo. Enfatizan la tasa de cambio. Algunos ejemplos de gráficos de líneas son los delitos que ocurren a lo largo del día, los cambios en el valor del dólar a lo largo de los años y las ventas de dulces a lo largo del año.

### Eje Y

Siempre es importante recordar lo que demuestran los datos y traducirlo en su visualización. Cuando trabajamos con gráficos de barras y gráficos de líneas, debemos considerar si incluimos o excluimos el cero en el eje y.

El siguiente ejemplo muestra dos gráficos de datos que analizan la inscripción en el primer año de la facultad de derecho desde 1974 hasta 2013 (fuente: Abhinav Agarwal )). El gráfico de la izquierda muestra que durante más de 30 años los avances en la matrícula de primer año en la facultad de derecho se eliminaron en un año. El gráfico de la derecha muestra los mismos datos escalados de manera diferente para incluir 0 en el eje y. Si bien se puede ver la caída en la matrícula de las facultades de derecho y los cambios en la matrícula a lo largo de los años, la información no es tan evidente ni sorprendente. Por eso el contexto es importante y los datos deben ser la fuerza guía en su proceso de visualización.

![Serie temporal](https://fer78docs.github.io/assets/images/twitter_image.webp)

## Que evitar

Si bien los elementos visuales pueden ser útiles para traducir sus datos, no todos los elementos visuales son informativos. Los diseños deficientes pueden confundir o desinformar al lector, en lugar de guiarlo a través de su historia de datos. Algunos tipos comunes de gráficos que se deben evitar son:

- Gráficos circulares
- Gráficos de barras apiladas
- Gráficos de áreas apiladas

## Gráficos circulares

Los gráficos circulares se encuentran con algunos errores comunes, como usar demasiadas categorías, falta de orden o que cada porción del pastel no sume el 100%. Los lectores se ven obligados a comparar áreas o ángulos en lugar de magnitudes relativas como lo harían con los gráficos de barras. En el siguiente ejemplo de un artículo de Business Insider sobre gráficos circulares, no podemos ordenar con confianza las partes del pastel según su magnitud. Podemos ver que el partido más grande del Parlamento Europeo es el PPE, pero ¿podemos distinguir el partido más pequeño?

La situación empeora cuando se convierte en un gráfico circular tridimensional. Cuando los gráficos circulares se hacen tridimensionales, se distorsiona la cantidad de área que ocupa una categoría, o en este caso, el Partido del Parlamento Europeo. Esto induciría al lector a pensar que los datos nos dicen algo que no es así.

## Gráficos de barras apiladas

Si bien los gráficos de barras apiladas intentan combinar información de una variedad de grupos en un solo gráfico, dificultan la comparación de categorías entre grupos. Esta imagen de la documentación de Google sobre gráficos contiene información sobre ventas hipotéticas de libros en todos los géneros a lo largo de tres décadas (décadas de 2010, 2020 y 2030). Es difícil identificar las claras diferencias en las ventas entre géneros que no son fantasía y ciencia ficción.

Tomando los mismos datos, podríamos considerar observar los cambios en las ventas de libros para cada década por género. En el gráfico de líneas a continuación, vemos un crecimiento en las ventas de libros cada década para los géneros de fantasía y ciencia ficción, misterio y literatura y disminuciones en las ventas cada década para los géneros románticos y occidentales. Si bien hubo una disminución en las ventas de 2010 a 2020 para el género general, todavía supera a todos los géneros en términos de ventas de libros.

## Gráficos de áreas apiladas

Al igual que los gráficos de barras apiladas, los gráficos de áreas apiladas también pueden resultar confusos de interpretar. En este ejemplo (El Cairo, 2016) (fuente: Truthful Art, The: Data, Charts, and Maps for Communication ), el gráfico de áreas apiladas de la izquierda muestra las contribuciones al PIB mundial de Asia, África, América y Europa a lo largo del tiempo. . Vemos que Asia en 1700 contribuía con más del 50% del PIB mundial, en comparación con Europa que aportaba un poco más del 25%. Sin embargo, en 2012, no podemos ver claramente si la contribución de Europa al PIB mundial es mayor o menor que la de América. El gráfico de áreas apiladas no comunica claramente los aumentos del PIB en Asia ni el estancamiento relativo de la participación del PIB mundial en África. En cambio, en el gráfico de la derecha podemos ver los tamaños relativos del PIB de todas las regiones y cómo han cambiado con el tiempo.

## Visualización en Python

Hay dos bibliotecas de trazado principales que utilizan la mayoría de los usuarios de Python: Matplotlib y seaborn. Ambas bibliotecas pueden crear hermosas imágenes: Matplotlib es versátil y personalizable, mientras que seaborn está construido sobre Matplotlib y sus características son un poco más fáciles de usar. ¡Veamos un ejemplo usando ambas bibliotecas!

En 1973, la Universidad de California Berkeley fue demandada por discriminación de género entre sus admisiones de posgrado. Exploraremos los argumentos del demandante y el demandado con los datos a continuación y crearemos algunas imágenes usando Matplotlib y seaborn. El demandante argumentó que UC Berkeley discriminó a las mujeres en sus admisiones de posgrado porque los hombres fueron aceptados en una tasa del 44% en comparación con el 30% de las mujeres. Sin embargo, cuando analizamos los datos y nos centramos en la tasa de aceptación entre departamentos, ese ya no es el caso. Vemos que en cuatro de los seis departamentos las mujeres tienen una tasa de aceptación mayor que los hombres. Nota: no se conocen los departamentos específicos, por lo que usaremos AF genérico como nuestras etiquetas.

