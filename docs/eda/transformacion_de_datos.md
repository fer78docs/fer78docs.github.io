---
layout: default
title: Data Transformation
nav_order: 4
parent: Exploratory Data Analysis
---

# Transformación de datos
Uno de los pasos fundamentales del Análisis Exploratorio de Datos (EDA) es el `Data Wrangling`. La trasnformacion de datos es un conjunto de técnicas utilizadas para convertir datos de un formato o estructura a otro formato o estructura. Los siguientes son algunos ejemplos de actividades de transformación de datos en data analisys:

- **[Data deduplication](#deduplication)** (*deduplicación de datos*) Implica la identificación y eliminación de registros duplicados dentro de un conjunto de datos para mejorar la calidad y la precisión de los datos. Ejemplo: Eliminar entradas duplicadas en una base de datos de clientes.
- La **[Key restructuring](#Keyrest)** (*reestructuración de claves*) Consiste en transformar claves con significados específicos en claves genéricas para facilitar su uso y análisis. Ejemplo: Cambiar un identificador de producto específico del proveedor a un identificador universal.
- La **Data Cleansing** (*limpieza de datos*)  Implica la eliminación o corrección de datos inexactos, incompletos, obsoletos o irrelevantes para mejorar la calidad general de los datos. Ejemplo: Eliminar espacios en blanco adicionales alrededor de los valores en una columna de datos.
- La **Data Validation** (*validación de datos*) Es el proceso de aplicar reglas o algoritmos para verificar la precisión y la integridad de los datos en relación con ciertos criterios o estándares. Ejemplo: Verificar si los números de teléfono en una base de datos siguen un formato específico.
- La **Format revisioning** (*revisión de formato*) Consiste en convertir datos de un formato a otro para facilitar su análisis o integración con otros sistemas. Ejemplo: Convertir una fecha de formato de texto a formato de fecha y hora estándar.
- La **Data derivation** (*derivación de datos*) Implica la creación de nuevas variables o atributos a partir de datos existentes utilizando reglas o algoritmos definidos. Ejemplo: Calcular la edad de los clientes a partir de su fecha de nacimiento.
- La **Data aggregation** (*agregación de datos*) Consiste en buscar, extraer, resumir y preservar información importante en diferentes sistemas de informes para facilitar el análisis. Ejemplo: Sumar las ventas mensuales para obtener ventas anuales totales.
- La **Data integration** (*integración de datos*) Involucra combinar datos de múltiples fuentes y formatos en un único esquema o estructura para análisis coherente. Ejemplo: Integrar datos de ventas de diferentes sucursales en una sola base de datos.
- El **Data filtering** (*filtrado de datos*) Implica identificar y seleccionar solo los datos relevantes para un análisis específico, descartando datos irrelevantes o no deseados. Ejemplo: Filtrar registros de ventas para mostrar solo transacciones realizadas en un período de tiempo específico.
- La **[Data joining](#joining)** (*unión de datos*) Consiste en combinar dos o más conjuntos de datos relacionados mediante una clave común para realizar análisis conjunto. Ejemplo: Unir datos de clientes con datos de pedidos utilizando un identificador único de cliente.

La razón principal para transformar los datos es obtener una mejor representación de modo que los datos transformados sean compatibles con otros datos. Además de esto, la interoperabilidad en un sistema se puede lograr siguiendo una estructura y un formato de datos comunes.


## Data Deduplication
{: #deduplication}


## Key restructuring
{: #Keyrest}



## Data Deduplication
{: #deduplication}



## Data Deduplication
{: #deduplication}




## Data Deduplication
{: #deduplication}




## Data Deduplication
{: #deduplication}



## Data Deduplication
{: #deduplication}



## Data Deduplication
{: #deduplication}


## Data joining
{: #joining}

"Data Joining" se refiere al proceso de combinar dos o más conjuntos de datos basándose en una columna común o índice para crear un único conjunto de datos integrado. Los métodos utilizados para el data joining en ciencia de datos se inspiran en gran medida en las operaciones de unión de bases de datos relacionales. 

### Pandas
Pandas proporciona varios métodos para combinar y comparar Series o DataFrames.Los metodos para unir marcos de datos con Pandas son:  `append()`, `concat()`, `merge()` o `join()`. El metodo `compare()` muestra las diferencias en valores entre dos Series o DataFrame.

- `concat()`: fusiona varias Series o DataFrames a lo largo de un índice o columna compartido.
- `DataFrame.join()`: fusiona varios DataFrame a lo largo de las columnas
- `DataFrame.combine_first()`: actualice los valores faltantes con valores no faltantes en la misma ubicación
- `merge()`: Combina dos Series o DataFrames con unión estilo SQL
- `merge_ordered()`: Combina dos Series o DataFrames a lo largo de un eje ordenado
- `merge_asof()`: Combina dos Series o DataFrames con keys coincidentes cercanas en lugar de exactas
- `compare()`: muestra las diferencias en valores entre dos Series o DataFrames.


### .concat()
Toma como entrada una lista, diccionario , Series o DataFrames y los une a lo largo de un eje específico:

- `Axis 0`: Concatenación vertical (por defecto), donde los DataFrames o Series se apilan uno encima del otro. Esto es equivalente a añadir filas.
- `Axis 1`: Concatenación horizontal, donde los DataFrames o Series se unen lado a lado. Esto es equivalente a añadir columnas.

#### Lógica de Conjunto en los Índices

Una característica clave de `concat()` es su capacidad para manejar índices al concatenar:

- **Unión** (por defecto): Todos los índices únicos de cada objeto se incluyen en el índice del DataFrame resultante, lo que puede resultar en índices duplicados si estos no son únicos a través de los objetos concatenados.
- **Intersección**: Solo los índices compartidos por todos los objetos se incluyen en el DataFrame resultante, eliminando así cualquier índice que no esté presente en todos los objetos.

#### Manejo de Ejes no Concatenados

Para los ejes que no están siendo concatenados, puedes especificar cómo manejar los índices que no coinciden entre los objetos:

- `ignore_index=True:` Ignora los índices de los objetos y crea un nuevo índice entero para el DataFrame resultante. Esto es útil cuando no te interesan los índices originales.
- `keys=[...]`: Permite especificar un conjunto de etiquetas para los objetos concatenados. Esto es útil para distinguir entre los datos de diferentes fuentes después de la concatenación, creando un MultiIndex.

```python
# Concatenación vertical
result_vertical = pd.concat([df1, df2])

# Concatenación horizontal
result_horizontal = pd.concat([df1, df2], axis=1)

# Concatenación con intersección de índices
result_intersection = pd.concat([df1, df2], join='inner')

# Concatenación con un nuevo índice
result_ignore_index = pd.concat([df1, df2], ignore_index=True)

# Concatenación con claves específicas para cada DataFrame
result_keys = pd.concat([df1, df2], keys=['x', 'y'])
```

{:nota}
Al concatenar DataFramecon ejes con nombres, pandas intentará conservar estos nombres de índice/columna siempre que sea posible. En el caso de que todas las entradas compartan un nombre común, este nombre se asignará al resultado. Cuando los nombres de entrada no coinciden, el resultado no tendrá nombre.


### .merge()
Realiza operaciones de unión similares a bases de datos relacionales como SQL. Los usuarios que estén familiarizados con SQL pero que sean nuevos en Pandas pueden hacer referencia a una comparación con SQL .

#### Tipos de fusión 
Operaciones comunes de unión de estilo SQL.

- `uno a uno` : unir dos DataFrames en sus índices que deben contener valores únicos.
- `muchos a uno` : unir un índice único a una o más columnas en un archivo DataFrame.
- `muchos a muchos` : unir columnas sobre columnas.

Nota  
Al unir columnas sobre columnas, potencialmente una unión de muchos a muchos, se descartarán todos los índices de los objetos pasados del DataFrame.

Para una combinación de muchos a muchos, si una combinación de llaves aparece más de una vez en ambas tablas, el DataFrame resultante tendrá el producto cartesiano de los datos asociados.

```python
result = pd.merge(df_left, df_right, on="key")
```

#### Claves en Uniones 
El argumento `how` de `merge()` especifica qué claves se incluyen en la tabla resultante. Si una combinación de keys no aparece en las tablas izquierda o derecha, los valores en la tabla unida serán `NA`. A continuación se muestra un resumen de las opciones y sus nombres equivalentes en SQL:

| Nombre de unión | SQL             | Descripción                                     |
|-----------------|-----------------|-------------------------------------------------|
| left            | LEFT OUTER JOIN | Utilice únicamente las teclas del marco izquierdo |
| right           | RIGHT OUTER JOIN| Utilice únicamente las teclas del marco derecho  |
| outer           | FULL OUTER JOIN | Utilice la unión de claves de ambos marcos.     |
| inner           | INNER JOIN      | Utilice la intersección de claves de ambos fotogramas. |
| cross           | CROSS JOIN      | Crea el producto cartesiano de filas de ambos marcos. |


- `left`: Utiliza las claves del marco (DataFrame o tabla) izquierdo para encontrar coincidencias en el marco derecho. Si no hay coincidencias en el derecho para una clave del izquierdo, aún se incluirán las filas del izquierdo, rellenando las columnas del derecho con NULL.

- `right`: Opera de manera inversa al LEFT JOIN, utilizando las claves del marco derecho para encontrar coincidencias en el marco izquierdo. Las filas del derecho sin coincidencias en el izquierdo se incluirán, con NULL en las columnas del izquierdo.

- `outer`: Combina las estrategias de LEFT y RIGHT JOIN, utilizando las claves de ambos marcos para la unión. Incluirá todas las filas de ambos marcos, rellenando con NULL las columnas del marco opuesto cuando no haya coincidencias.

- `inner`: Utiliza la intersección de las claves de ambos marcos, es decir, solo incluye las filas con claves que tienen coincidencias en ambos marcos. Las filas sin coincidencias en cualquiera de los marcos se excluyen del resultado final.

- `cross`: No se basa en claves para realizar la unión. En lugar de eso, crea un producto cartesiano, combinando cada fila del marco izquierdo con cada fila del marco derecho, resultando en un número de filas igual al producto del número de filas de ambos marcos.

