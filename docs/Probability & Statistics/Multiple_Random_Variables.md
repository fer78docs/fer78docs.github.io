---
layout: default
title: Multiple Random Variables
nav_order: 7
parent: Probability & Statistics
---

## Variables Aleatorias Múltiples y Distribuciones Conjuntas

### Distribuciones Conjuntas

1. **Distribuciones Conjuntas**:
   - **Variables Discretas**: Para dos variables aleatorias discretas $$X$$ y $$Y$$, la función de masa de probabilidad conjunta (joint PMF) $$p(x, y)$$ define la probabilidad de que $$X$$ tome el valor $$x$$ y $$Y$$ tome el valor $$y$$ simultáneamente.
   - **Variables Continuas**: En el caso de variables continuas, la función de densidad conjunta (joint PDF) describe cómo se distribuye la densidad sobre combinaciones de valores de $$X$$ y $$Y$$.

2. **Distribuciones Marginales**:
   - Las distribuciones marginales se obtienen sumando (en el caso discreto) o integrando (en el caso continuo) la distribución conjunta sobre el rango de todas las posibles valores de las otras variables. Por ejemplo, la distribución marginal de $$X$$ se obtiene como $$p(x) = \sum_y p(x, y)$$ para variables discretas, o $$p(x) = \int p(x, y) \, dy$$ para variables continuas.

### Trabajar con Múltiples Variables Aleatorias

1. **Extension a Más de Dos Variables**:
   - El concepto de distribuciones conjuntas se extiende naturalmente a más de dos variables. Para $$n$$ variables $$X_1, X_2, \dots, X_n$$, la distribución conjunta nos permite describir y analizar eventos que involucran todas estas variables simultáneamente.

2. **Cálculo de Expectativas y Varianzas**:
   - La expectativa de una función de múltiples variables aleatorias, como $$W = X + Y + Z$$, se puede calcular utilizando la distribución conjunta y sumando (o integrando) sobre todos los posibles valores de las variables involucradas.

### Aplicaciones Prácticas y Modelado

1. **Modelos de Regresión y Clasificación**:
   - En contextos reales, frecuentemente enfrentamos situaciones donde debemos predecir o clasificar resultados basados en múltiples características o atributos. Las distribuciones conjuntas son fundamentales para desarrollar modelos estadísticos que tomen en cuenta las relaciones entre diferentes variables.

2. **Desafíos del Modelado Conjunto**:
   - Cuando el número de variables aumenta, modelar la distribución conjunta completa se vuelve computacionalmente difícil, lo que nos lleva al problema conocido como la "maldición de la dimensionalidad". En la práctica, se utilizan heurísticas y aproximaciones para manejar grandes dimensiones.

### Temas Avanzados

1. **Distribución Multivariante Gaussiana**:
   - Un caso particularmente importante de distribuciones conjuntas es la distribución gaussiana multivariante, donde cada conjunto de variables sigue una distribución gaussiana. Exploraremos las propiedades y aplicaciones de este tipo de distribución en profundidad.

2. **Independencia y Variables Condicionadas**:
   - Discutiremos conceptos como la independencia entre variables aleatorias múltiples y cómo las probabilidades condicionales se modifican en presencia de múltiples variables.


## Distribución Gaussiana Multivariante

La Distribución Gaussiana Multivariante es esencial para entender y modelar relaciones complejas entre múltiples variables aleatorias, y es ampliamente utilizada en técnicas avanzadas de modelado estadístico y predicción.

### Conceptos Básicos de la Distribución Gaussiana Multivariante

1. **Vectores Aleatorios**:
   - En el contexto de múltiples variables aleatorias, es conveniente utilizar vectores aleatorios para describir conjuntos de variables. Un vector aleatorio $$\mathbf{X}$$ agrupa varias variables aleatorias, como $$X_1, X_2, \ldots, X_D$$, facilitando la descripción y manipulación de sus distribuciones conjuntas.

2. **Función de Densidad Conjunta**:
   - La función de densidad de la distribución gaussiana multivariante para un vector aleatorio \( \mathbf{X} \) se expresa en términos matriciales y vectoriales, lo que simplifica muchas de las operaciones estadísticas involucradas.

#### Fórmula de la Distribución Gaussiana Multivariante

1. **Parámetros de la Distribución**:
   - **Media Vectorial (\(\boldsymbol{\mu}\))**: Es un vector que contiene las medias de cada variable aleatoria en el vector \( \mathbf{X} \).
   - **Matriz de Covarianza (\(\mathbf{\Sigma}\))**: Es una matriz \( D \times D \) que no solo captura las varianzas de cada variable individual, sino también las covarianzas entre cada par de variables. Esta matriz debe ser definida positiva para asegurar una distribución válida.

2. **Función de Densidad**:
   - La función de densidad para un vector aleatorio \( \mathbf{X} \) en la distribución gaussiana multivariante se define como:
     \[
     f(\mathbf{x}) = \frac{1}{\sqrt{(2\pi)^D \det(\mathbf{\Sigma})}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^\top \mathbf{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right)
     \]
   - Esta fórmula incorpora el determinante de la matriz de covarianza \( \mathbf{\Sigma} \) y su inversa, mostrando cómo las interrelaciones entre las variables afectan la distribución global.

#### Aplicaciones en Ciencia de Datos y Aprendizaje Automático

1. **Modelos de Regresión y Clasificación**:
   - La distribución gaussiana multivariante es fundamental en técnicas como la regresión lineal y la regresión ridge, donde las relaciones entre múltiples predictores necesitan ser modeladas conjuntamente.

2. **Teorema del Límite Central**:
   - Esta distribución juega un papel crucial en la justificación del uso de normales en la modelación de errores y ruidos en modelos estadísticos, debido al Teorema del Límite Central que indica que bajo ciertas condiciones, la suma de variables aleatorias independientes tiende a una distribución normal.

3. **Justificación de Ruido Gaussiano**:
   - En muchos modelos prácticos, el ruido se modela como una variable aleatoria gaussiana, lo cual se justifica mediante el Teorema del Límite Central, demostrando que muchos procesos aleatorios pequeños e independientes contribuyen al efecto observado.

#### Conclusión y Perspectivas Futuras

La Distribución Gaussiana Multivariante no solo es una herramienta matemática elegante, sino también una base esencial para el análisis estadístico en múltiples campos aplicados. Al entender esta distribución, los estudiantes y profesionales pueden aplicar estos conceptos a problemas complejos en ciencia de datos, ingeniería y economía, mejorando la precisión y eficacia de sus modelos. En las siguientes lecciones, exploraremos más a fondo las propiedades y aplicaciones de esta distribución, así como otras distribuciones multivariantes relevantes en el análisis estadístico moderno.