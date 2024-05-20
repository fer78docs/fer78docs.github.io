---
layout: default
title: Line Graphs
nav_order: 1
parent: Data Visualization
---

# Graficos de Linea

`Matplotlib` es una biblioteca de Python que se utiliza para crear cuadros y gráficos.

```python
from matplotlib import pyplot as plt
```

Esto importará las funciones de trazado de `matplotlib` y las hará accesibles usando el nombre más corto `plt`. 

### Trazado de líneas básicas

Los gráficos de líneas son útiles para visualizar cómo cambia una variable con el tiempo. Algunos datos posibles que se mostrarían con un gráfico de líneas:

- Precios medios de la gasolina en la última década.
- Peso de un individuo durante los últimos meses
- Temperatura promedio a lo largo de una línea de longitud en diferentes latitudes.

Usando los métodos de `Matplotlib`, el siguiente código creará un gráfico de líneas simple `.plot()` y lo mostrará usando `.show()`:

```python
x_values = [0, 1, 2, 3, 4]
y_values = [0, 1, 4, 9, 16]
plt.plot(x_values, y_values)
plt.show()
```

- `x_values` es una variable que contiene una lista de valores de `x` para cada punto en nuestro gráfico lineal
- `y_values` es una variable que contiene una lista de valores de `y` para cada punto en nuestro gráfico lineal
- `plt` es el nombre que le hemos dado al módulo Matplotlib que hemos importado en la parte superior del código
- `plt.plot(x_values, y_values)` creará el gráfico de líneas
- `plt.show()` realmente mostrará el gráfico

El gráfico quedaría así:

![Line Graph](https://fer78docs.github.io/assets/images/parabola.webp)

También podemos mostrar varios gráficos de líneas en el mismo conjunto de ejes. Esto puede resultar muy útil si queremos comparar dos conjuntos de datos con la misma escala y categorías de eje.

Matplotlib colocará automáticamente las dos líneas en los mismos ejes y les dará colores diferentes si llama `plt.plot()` dos veces. 

El siguinte ejemplo combina el gasto de almuerzo de dos personas. 

```python
# Days of the week:
days = [0, 1, 2, 3, 4, 5, 6]
# Your Money:
money_spent = [10, 12, 12, 10, 14, 22, 24]
# Your Friend's Money:
money_spent_2 = [11, 14, 15, 15, 22, 21, 12]
# Plot your money:
plt.plot(days, money_spent)
# Plot your friend's money:
plt.plot(days, money_spent_2)
# Display the result:
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/money_spent_2.webp)

De forma predeterminada, la primera línea siempre es azul y la segunda línea siempre es naranja. En el siguiente ejercicio, aprenderemos cómo personalizar estas líneas nosotros mismos.

### Estilos de línea

Podemos especificar un color diferente para una línea usando la palabra clave color con un nombre de color HTML o un código HEX :

```python
plt.plot(days, money_spent, color='green')
plt.plot(days, money_spent_2, color='#AAAAAA')
```

También podemos hacer una línea de puntos o de trazos usando la palabra clave linestyle.

```python
# Dashed:
plt.plot(x_values, y_values, linestyle='--')
# Dotted:
plt.plot(x_values, y_values, linestyle=':')
# No line:
plt.plot(x_values, y_values, linestyle='')
```

También podemos agregar un marcador usando la palabra clave marker:

```python
# A circle:
plt.plot(x_values, y_values, marker='o')
# A square:
plt.plot(x_values, y_values, marker='s')
# A star:
plt.plot(x_values, y_values, marker='*')
```

Para ver todas las opciones posibles, consulte la documentación de Matplotlib . A continuación se muestran algunos de esos valores aplicados a nuestros gráficos sobre el gasto en almuerzos:

```python
plt.plot(days, money_spent, color='green', linestyle='--')
plt.plot(days, money_spent_2, color='#AAAAAA',  marker='o')
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/linestyles.webp)

**Ejemplo**

```python
time = [0, 1, 2, 3, 4]
revenue = [200, 400, 650, 800, 850]
costs = [150, 500, 550, 550, 560]
plt.plot(time, revenue, color = 'purple', linestyle = '--')
plt.plot(time, costs, color = '#82edc9', marker = 's')
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/ejemplo_plt.png)

### Ejes y etiquetas

A veces, puede resultar útil acercar o alejar la trama, especialmente si hay algún detalle que queremos abordar. Para hacer zoom podemos usar `plt.axis()`. Lo usamos plt.axis() alimentándolo con una lista como entrada. Esta lista debe contener:

- El valor x mínimo mostrado
- El valor x máximo mostrado
- El valor y mínimo mostrado
- El valor y máximo mostrado

Por ejemplo, si queremos mostrar un gráfico desde `x=0` hasta `x=3` y desde `y=2` hasta `y=5`, llamaríamos `plt.axis([0, 3, 2, 5])`.

```python
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
plt.plot(x, y)
plt.axis([0, 3, 2, 5])
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/axis_zoom.webp)

### Etiquetar los ejes

Podemos etiquetar los ejes `x` e `y` usando `plt.xlabel()` y `plt.ylabel()`. El título de la trama se puede configurar usando `plt.title()`.Todos estos comandos requieren una cadena, que es un conjunto de caracteres entre comillas simples (') o dobles (").

Por ejemplo, si alguien ha estado realizando un seguimiento de su felicidad (en una escala de 10) a lo largo del día y quiere mostrar esta información con ejes etiquetados, podemos usar los siguientes comandos:

```python
hours = [9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
happiness = [9.8, 9.9, 9.2, 8.6, 8.3, 9.0, 8.7, 9.1, 7.0, 6.4, 6.9, 7.5]
plt.plot(hours, happiness)
plt.xlabel('Time of day')
plt.ylabel('Happiness Rating (out of 10)')
plt.title('My Self-Reported Happiness While Awake')
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/axis_labels.png)


### Subtramas

A veces, queremos mostrar dos líneas una al lado de la otra, en lugar de en el mismo conjunto de ejes x e y. Cuando tenemos varios ejes en la misma imagen, llamamos a cada conjunto de ejes subtrama . La imagen u objeto que contiene todas las subtramas se llama figura .

Podemos tener muchas subtramas diferentes en la misma figura y podemos distribuirlas de muchas maneras diferentes. Podemos pensar que nuestros diseños tienen filas y columnas de subtramas. Por ejemplo, la siguiente figura tiene seis subtramas divididas en 2 filas y 3 columnas:

![Line Graph](https://fer78docs.github.io/assets/images/six_subplots.svg)

Podemos crear subtramas usando `.subplot()`. El comando `plt.subplot()` necesita que se le pasen tres argumentos:

- El número de filas de subtramas.
- El número de columnas de subtramas.
- El índice de la subtrama que queremos crear.

Por ejemplo, el comando `plt.subplot(2, 3, 4)` crearía la "Subtrama 4" a partir de la figura anterior. Cualquiera `plt.plot()` que venga después `plt.subplot()` creará un gráfico lineal en la trama secundaria especificada. Por ejemplo:

```python
# Data sets
x = [1, 2, 3, 4]
y = [1, 2, 3, 4]

# First Subplot
plt.subplot(1, 2, 1)
plt.plot(x, y, color='green')
plt.title('First Subplot')

# Second Subplot
plt.subplot(1, 2, 2)
plt.plot(x, y, color='steelblue')
plt.title('Second Subplot')

# Display both subplots
plt.show()
```

Esto daría como resultado una figura con los dos gráficos organizados así:

![Line Graph](https://fer78docs.github.io/assets/images/two_subplots.svg)

A veces, cuando juntamos varias subtramas, algunos elementos pueden superponerse y hacer que la figura sea ilegible:

Podemos personalizar el espacio entre nuestras subtramas para asegurarnos de que la figura que creamos sea visible y fácil de entender. Para hacer esto, usamos el comando `plt.subplots_adjust()`, este tiene algunos argumentos de palabras clave que pueden mover sus gráficos dentro de la figura:

- `left`: el margen del lado izquierdo, con un valor predeterminado de 0,125. Puede aumentar este número para dejar espacio para una etiqueta del eje `y`
- `right` el margen derecho, con un valor predeterminado de 0,9. Puedes aumentarlo para dejar más espacio para la figura o disminuirlo para dejar espacio para una leyenda.
- `bottom` el margen inferior, con un valor predeterminado de 0,1. Puede aumentar esto para dejar espacio para etiquetas de marcas o una etiqueta del eje x
- `top` el margen superior, con un valor predeterminado de 0,9
- `wspace` el espacio horizontal entre subtramas adyacentes, con un valor predeterminado de 0,2
- `hspace` el espacio vertical entre subtramas adyacentes, con un valor predeterminado de 0,2

Por ejemplo, si estuviéramos agregando espacio al final de un gráfico cambiando el margen inferior a 0,2 (en lugar del valor predeterminado de 0,1), usaríamos el comando:

```python
plt.subplots_adjust(bottom=0.2)
```

También podemos usar múltiples argumentos de palabras clave, si necesitamos ajustar múltiples márgenes. Por ejemplo, podríamos ajustar tanto el topcomo el hspace:

```python
plt.subplots_adjust(top=0.95, hspace=0.25)
```

Usemos `wspace` para arreglar la figura de arriba:

```python
# Left Plot
plt.subplot(1, 2, 1)
plt.plot([-2, -1, 0, 1, 2], [4, 1, 0, 1, 4])

# Right Plot
plt.subplot(1, 2, 2)
plt.plot([-2, -1, 0, 1, 2], [4, 1, 0, 1, 4])

# Subplot Adjust
plt.subplots_adjust(wspace=0.35)

plt.show()
```

Esto nos daría una figura con un mejor diseño:

![Line Graph](https://fer78docs.github.io/assets/images/fixed_subplots.webp)


**Ejemplo**

Vamos a crear una figura que tenga dos filas de subtramas. Deberia tener:

- una subtrama en la fila superior
- dos subtramas en la fila inferior
- subplot_adjust_ckpt

```python
x = range(7)
straight_line = [0, 1, 2, 3, 4, 5, 6]
parabola = [0, 1, 4, 9, 16, 25, 36]
cubic = [0, 1, 8, 27, 64, 125, 216]

plt.subplot(2,1,1)
plt.plot(x,straight_line)

plt.subplot(2, 2, 3)
plt.plot(x, parabola)

plt.subplot(2, 2, 4)
plt.plot(x, cubic)

plt.subplots_adjust(bottom = 0.2, wspace = 0.35)

plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/subplot-ejemplo.png)

### Leyendas

Cuando tenemos varias líneas en un solo gráfico, podemos etiquetarlas usando el comando `plt.legend()`.

El método `legend` toma una lista con las etiquetas a mostrar. Así, por ejemplo, podemos llamar:

```python
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16])
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64])
plt.legend(['parabola', 'cubic'])
plt.show()
``` 

que mostraría una leyenda en nuestro gráfico, etiquetando cada línea:

![Line Graph](https://fer78docs.github.io/assets/images/legend.webp)

`plt.legend()` También puede tomar un argumento de palabra clave `loc`, que posicionará la leyenda en la figura.

Estos son los valores de posición `loc` que acepta:

|**Código numérico**	|**Cadena**|
|0	|mejor|
|1	|superior derecha|
|2	|arriba a la izquierda|
|3	|abajo a la izquierda|
|4	|inferior derecha|
|5	|bien|
|6	|centro izquierda|
|7	|centro derecha|
|8	|centro inferior|
|9	|centro superior|
|10	|centro|

Nota: Si decide no establecer un valor para loc, se elegirá de forma predeterminada la "mejor" ubicación.

A veces, es más fácil etiquetar cada línea a medida que la creamos. Si queremos, podemos usar la palabra clave `label` dentro de `plt.plot()`. Si elegimos hacer esto, no pasamos ninguna etiqueta a `plt.legend()`. Por ejemplo:

```python
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16], label="parabola")
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64], label="cubic")
plt.legend() # Still need this command!
plt.show()
```

**Ejemplo**

```python
months = range(12)
hyrule = [63, 65, 68, 70, 72, 72, 73, 74, 71, 70, 68, 64]
kakariko = [52, 52, 53, 68, 73, 74, 74, 76, 71, 62, 58, 54]
gerudo = [98, 99, 99, 100, 99, 100, 98, 101, 101, 97, 98, 99]

plt.plot(months, hyrule)
plt.plot(months, kakariko)
plt.plot(months, gerudo)

#create your legend here
legend_labels = ["Hyrule", "Kakariko", "Gerudo Valley"]
plt.legend(legend_labels, loc = 8)
plt.show()
```
![Line Graph](https://fer78docs.github.io/assets/images/ejemplo_legend.png)


### Modificar ticks

En todos nuestros ejercicios anteriores, nuestros comandos comenzaron con plt.. Para modificar las marcas, tendremos que probar algo un poco diferente.

Debido a que nuestras tramas pueden tener múltiples subtramas, debemos especificar cuál queremos modificar. Para ello llamamos `plt.subplot()` de otra forma.

```python
ax = plt.subplot(1, 1, 1)
```

`ax` es un objeto de ejes y nos permite modificar los ejes que pertenecen a una subtrama específica. Incluso si solo tenemos una subtrama, cuando queramos modificar los ticks, necesitaremos comenzar llamando a `ax = plt.subplot(1, 1, 1)` o `ax = plt.subplot()` para obtener nuestro objeto de ejes.

Supongamos que queremos configurar nuestras marcas x en 1, 2 y 4. Usaríamos el siguiente código:

```python
ax = plt.subplot()
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16])
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64])
ax.set_xticks([1, 2, 4])
```
El resultado se vería así:

![Line Graph](https://fer78docs.github.io/assets/images/tick_marks.png)

También podemos modificar las marcas y usando `ax.set_yticks()`.

Cuando cambiamos las marcas `x`, sus etiquetas cambian automáticamente para coincidir. Pero, si queremos etiquetas especiales (como cadenas), podemos usar el comando `ax.set_xticklabels()` o `ax.set_yticklabels()`. Por ejemplo, es posible que deseemos tener un eje y con marcas en 0,1, 0,6 y 0,8, pero etiquetarlas como 10 %, 60 % y 80 %, respectivamente. Para ello utilizamos los siguientes comandos:

```python
ax = plt.subplot()
plt.plot([1, 3, 3.5], [0.1, 0.6, 0.8], 'o')
ax.set_yticks([0.1, 0.6, 0.8])
ax.set_yticklabels(['10%', '60%', '80%'])
```
Esto daría como resultado este etiquetado del eje y:

![Line Graph](https://fer78docs.github.io/assets/images/y_ticks.webp)


### Cifras

Cuando creamos muchos gráficos, es fácil terminar con líneas que se han trazado y no se muestran. Si no tenemos cuidado, estas líneas "olvidadas" aparecerán en sus nuevos gráficos. Para asegurarse de que no tenga líneas perdidas, puede usar el comando `plt.close('all')` para borrar todos los trazados existentes antes de trazar uno nuevo.

Anteriormente aprendimos cómo colocar dos conjuntos de ejes en la misma figura. A veces preferimos tener dos figuras separadas. Podemos usar el comando `plt.figure()` para crear nuevas figuras y dimensionarlas como queramos. Podemos agregar la palabra clave `figsize=(width, height)` para establecer el tamaño de la figura, en pulgadas. Usamos paréntesis ((y)) para pasar el ancho y el alto, que están separados por una coma.

Para crear una figura con un ancho de 4 pulgadas y una altura de 10 pulgadas, usaríamos:

```python
plt.figure(figsize=(4, 10))
```

Se vería alto y delgado, así:

![Line Graph](https://fer78docs.github.io/assets/images/tall_fig.webp)


Una vez que hayamos creado una figura, es posible que queramos guardarla para poder usarla en una presentación o en un sitio web. Podemos usar el comando `plt.savefig()` para guardar en muchos formatos de archivo diferentes, como png, svg o pdf. Después de trazar, podemos llamar `plt.savefig('name_of_graph.png')`:

```python
# Figure 2
plt.figure(figsize=(4, 10)) 
plt.plot(x, parabola)
plt.savefig('tall_and_narrow.png')
```

### Ejemplo de Resumen

```python
x = [1, 2, 3, 4, 5, 6]
y1 = [15, 17, 20, 25, 30, 37]
y2 = [16, 18, 21, 24, 31, 40]

plt.plot(x, y1, color = 'pink', marker='o', label="y1")
plt.plot(x, y2, color = 'gray', marker='o', label="y2")
plt.xlabel('Amazing X-axis')
plt.ylabel('Incredible Y-axis')
plt.title("Two Lines on One Graph")
plt.legend(loc = 4)
plt.show()
```

![Line Graph](https://fer78docs.github.io/assets/images/ejemplo_lines.png)
