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

La deduplicación de datos, en el contexto de la ciencia de datos, es el proceso de identificar y eliminar registros duplicados dentro de un conjunto de datos. Los datos duplicados pueden surgir por diversas razones, como la integración de datos de múltiples fuentes, errores en la entrada de datos, o como resultado de procesos de recopilación de datos. 

![Data Deduplicaction](https://fer78docs.github.io/assets/images/data_deduplication.webp)

### Data Deduplication en SQL

La deduplicación de datos se puede lograr mediante varios métodos, como la palabra clave `DISTINCT`, `GROUP BY` o funciones de ventana como `ROW_NUMBER()`. Supongamos que tenemos un conjunto de datos con datos de ventas de una tienda online. El conjunto de datos puede contener registros duplicados debido a diversos motivos, como fallas del sistema, problemas de integración de datos o múltiples entradas para la misma transacción.

| transaction_id | product_id | sale_amount | sale_date  |
|----------------|------------|-------------|------------|
| 1              | ABC123     | 100         | 2023-07-01 |
| 2              | DEF456     | 50          | 2023-07-02 |
| 3              | GHI789     | 75          | 2023-07-03 |
| 4              | ABC123     | 100         | 2023-07-01 |
| 5              | XYZ999     | 200         | 2023-07-04 |


Creando una nueva tabla con registros deduplicados usando `DISTINCT`:

```sql
CREATE TABLE sales_data_dedup AS
SELECT DISTINCT transaction_id, product_id, sale_amount, sale_date
FROM sales_data;
```

Podemos usar `GROUP BY` para agrupar los registros según columnas específicas y luego aplicar funciones agregadas como `SUM`, `COUNT`, etc. En este caso, usaremos GROUP BY para eliminar duplicados.

Creando una nueva tabla con registros deduplicados usando `GROUP BY`:
```sql
CREATE TABLE sales_data_dedup AS
SELECT transaction_id, product_id, sale_amount, sale_date
FROM sales_data
GROUP BY transaction_id, product_id, sale_amount, sale_date;
```
Es importante tener en cuenta que cuando se utiliza `GROUP BY` para eliminar duplicados, no se garantiza el orden de las filas dentro de cada grupo. Si el orden de las filas es significativo, considere usar la función de ventana `ROW_NUMBER()` para eliminar duplicados manteniendo el orden deseado.

La función de ventana `ROW_NUMBER()` asigna un número entero único a cada fila según el orden especificado. Al usar esta función y seleccionar solo filas con `ROW_NUMBER() = 1`, podemos deduplicar los datos.

nueva tabla con registros deduplicados usando ROW_NUMBER(): 

```sql
CREATE TABLE sales_data_dedup AS
SELECT transaction_id, product_id, sale_amount, sale_date
FROM ( SELECT transaction_id, product_id, sale_amount, sale_date,
        ROW_NUMBER() OVER (PARTITION BY transaction_id, product_id, sale_amount, sale_date ORDER BY transaction_id) as row_num
FROM sales_data) t
WHERE row_num = 1;
```

En todos los métodos, deduplicamos con éxito los datos de ventas y creamos una nueva tabla sales_data_dedup que contiene registros únicos.

### Data Deduplication en Python

#### Estrategias de Deduplicación en la Práctica
- Análisis Exploratorio de Datos (EDA): Antes de eliminar duplicados, es importante realizar un EDA para entender por qué aparecen duplicados y asegurarse de que su eliminación no sesgará los análisis posteriores.
- Deduplicación basada en columnas específicas: En algunos casos, puede ser deseable eliminar duplicados basándose solo en algunas columnas que deben ser únicas, utilizando el argumento subset.
- Registros Completos vs. Incompletos: Al deduplicar, considera la posibilidad de mantener el registro más completo (por ejemplo, con menos valores NA) en cada conjunto de duplicados. 


### df.drop_duplicates()
Este es el método más directo para eliminar filas duplicadas de un DataFrame. Por defecto, `drop_duplicates()` elimina las filas que tienen todas sus columnas idénticas a otra fila, **manteniendo la primera ocurrencia** de cada conjunto de duplicados y descartando el resto.  
Puedes modificar su comportamiento con argumentos como `subset`, para especificar un subconjunto de columnas para considerar en la búsqueda de duplicados, y `keep`, para indicar cuál de los duplicados mantener (`'first'`, `'last'`, o `False` para eliminar todos los duplicados).

```python
df = df.drop_duplicates()
```

### df.duplicated()
Mientras que `.drop_duplicates()` se usa para eliminar duplicados, `.duplicated()` es útil para marcar los duplicados. Este método retorna una Serie booleana que indica si cada fila es un duplicado (basado en todas las columnas o un subconjunto especificado) de una fila anterior. Esto es especialmente útil para explorar los datos y entender la naturaleza de los duplicados antes de decidir cómo manejarlos.

```python
df = df.duplicates()
```

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

- [`concat()`](#concat): fusiona varias Series o DataFrames a lo largo de un índice o columna compartido.
- [`df.join()`](#join): fusiona varios DataFrame a lo largo de las columnas
- [`df.combine_first()`](#first): actualice los valores faltantes con valores no faltantes en la misma ubicación
- [`merge()`](#merge): Combina dos Series o DataFrames con unión estilo SQL
- [`compare()`](#compare): muestra las diferencias en valores entre dos Series o DataFrames.
- `merge_ordered()`: Combina dos Series o DataFrames a lo largo de un eje ordenado
- `merge_asof()`: Combina dos Series o DataFrames con keys coincidentes cercanas en lugar de exactas



### pd.concat()
{: #concat}
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

Al concatenar DataFramecon ejes con nombres, pandas intentará conservar estos nombres de índice/columna siempre que sea posible. En el caso de que todas las entradas compartan un nombre común, este nombre se asignará al resultado. Cuando los nombres de entrada no coinciden, el resultado no tendrá nombre.


### pd.merge()
{: #merge}
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

#### Integridad de los datos al realizar operaciones de fusión

El argumento `validate` permite al usuario especificar la expectativa sobre la relación entre las claves de unión en los DataFrames que se están combinando, ayudando a identificar problemas de datos antes de que la fusión se complete. Acepta una de las siguientes cadenas, cada una representando un tipo específico de relación entre las claves de los DataFrames a fusionar:

- `1:1`: Verifica que las claves sean únicas tanto en el DataFrame izquierdo como en el derecho. Esto asegura que cada clave se utiliza exactamente una vez en cada DataFrame. Es útil cuando quieres garantizar que no hay duplicados en ninguna de las tablas antes de la fusión.
- `1:m o m:1`: Verifica que todas las claves en el DataFrame del lado '1' sean únicas, pero permite duplicados en el lado 'm'. Esto es común en situaciones donde un DataFrame tiene una clave primaria y el otro tiene una clave foránea que puede repetirse.
- `m:m`: Permite duplicados en ambos DataFrames. Aunque este es el comportamiento predeterminado si no se especifica validate, utilizar este argumento explícitamente puede ser útil para documentar la naturaleza de la fusión y garantizar que la operación es intencional.


### df.join()
{: #join}
El método `.join()` permite unir DataFrames basándose en sus índices o en una clave (columna) común. Por defecto, realiza una unión izquierda (left join), manteniendo todas las filas del DataFrame sobre el cual se llama el método e incorporando las columnas del DataFrame pasado como argumento.

```python
df1.join(df2)
```
En este ejemplo, `df1` es el DataFrame "izquierdo" al cual se unirán las columnas de `df2` basándose en los índices de ambos DataFrames.

Parámetros Importantes
- `other`: Otro DataFrame o Serie o lista de DataFrames con los cuales se unirá el DataFrame original.
- `on`: Especifica la columna del DataFrame desde el cual se llama `.join()` que se utilizará como clave para la unión. Si se especifica, esta columna debe existir en el DataFrame "izquierdo".
- `how`: Define cómo se realiza la unión: 'left' (por defecto), 'right', 'inner', 'outer'.
- `lsuffix`, `rsuffix`: Sufijos a agregar a las columnas con el mismo nombre en ambos DataFrames para diferenciarlas en el DataFrame resultante.

### df.combine.first()
{: #first}
Actualice los valores faltantes de uno DataFrame con los valores no faltantes en otro DataFrameen la ubicación correspondiente. Es decir, se puede utilizar para rellenar valores faltantes en un DataFrame con valores de otro DataFrame. La idea es que, para cualquier elemento en el DataFrame original que sea NA (no disponible o `NaN`), si hay un valor correspondiente en el mismo lugar del otro DataFrame, este valor se usará para rellenar el NA en el DataFrame original. Si no hay NA, el valor del DataFrame original se mantiene. Este método no modifica ninguno de los DataFrames originales; en su lugar, crea un nuevo DataFrame como resultado.

```python
df1.combine_first(df2)
```
En este caso, df1 es el DataFrame principal cuyos valores NA se buscan rellenar con los valores de df2. Los índices y columnas de ambos DataFrames juegan un papel crucial aquí: combine_first intentará hacer la coincidencia basándose en estos índices y columnas. Si df2 tiene valores en posiciones donde df1 tiene NA, estos valores de df2 se utilizan en el DataFrame resultante.


### .compare()
{: #compare}
Comparar dos DataFrameo Series, respectivamente, y resumir sus diferencias. De forma predeterminada, si dos valores correspondientes son iguales, se mostrarán como NaN. Además, si todos los valores están en una fila/columna completa, la fila/columna se omitirá del resultado. Las diferencias restantes se alinearán en columnas.

```python
df1.compare(df2)
```