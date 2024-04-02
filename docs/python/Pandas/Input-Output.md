---
layout: default
title: Input - Output
nav_order: 1
parent: Pandas
grand_parent: Python
---

# Input Output

**Indice**

- [**PICKING**](#id1)
- [**CSV**](#id2)
- [**CLIPBOARD**](#id3)
- [**EXCEL**](#id4)
- [**JSON**](#id5)
- [**HTML**](#id6)
- [**XML**](#id7)
- [**LATEX**](#id8)
- [**HDF**](#id9)
- [**FEATHER**](#id10)
- [**PARQUET**](#id11)
- [**ORC**](#id12)
- [**SAS**](#id13)
- [**SPSS**](#id14)
- [**SQL**](#id15)
- [**STATA**](#id17)

## Pickling<a name="id1"></a>

El término **"pickling"** en Python se refiere al proceso de **serialización** de objetos. Serializar un objeto implica convertirlo en un flujo de bytes que puede ser guardado en un archivo o transmitido a través de una red. Este flujo de bytes puede luego ser deserializado ("unpickled") para reconstruir el objeto original. En el contexto de Pandas, el pickling es útil para guardar DataFrames o Series de manera eficiente.

Pandas ofrece una forma fácil de serializar (pickle) sus estructuras de datos como DataFrames y Series.
Puedes guardar un DataFrame o Serie en un archivo binario utilizando el método **.to_pickle()** y luego cargar este archivo utilizando la función **pd.read_pickle()**.

```python
df.to_pickle('mi_dataframe.pkl)
df = pd.read_pickle('mi_dataframe.pkl')
```

**Consideraciones de Seguridad**

- El pickling no es seguro contra datos erróneos o maliciosos. Nunca debes unpickle datos recibidos de una fuente no confiable.
- El formato pickle es específico de Python y puede no ser compatible con otros lenguajes de programación.

**Ventajas y Desventajas:**

- **Ventajas:** Rápido y fácil de usar; mantiene la integridad de los tipos de datos; útil para estructuras de datos grandes.
- **Desventajas:** No es un formato legible por humanos; no es seguro contra datos maliciosos; no es ideal para compartir datos entre diferentes lenguajes de programación.

## Ficheros de Texto: csv, tables<a name="id2"></a>

Un "flat file" o archivo plano, en el contexto de Pandas y procesamiento de datos en Python, se refiere a un archivo de texto que contiene datos tabulares en un formato simple.

**Tipos Comunes:**

- **CSV** (Valores Separados por Comas): Es probablemente el tipo más común de archivo plano. Los valores en cada fila están separados por comas.
- **TSV** (Valores Separados por Tabulaciones): Similar a los CSV, pero usando tabulaciones como separadores.
- **Archivos de Texto:** Pueden tener otros delimitadores o ser de ancho fijo.

**Lectura**



```python
pd.read_table(path_or_buf, [sep='\t'])
```



- Está diseñada para leer archivos de datos tabulares.
- Por defecto, espera que los campos estén delimitados por tabulaciones (\t).
- Puedes cambiar el delimitador para leer archivos con otros separadores utilizando el argumento **sep**, por defecto es (\t).



```python
pd.read_csv(path_or_buf, [sep=','])
```



- Diseñada específicamente para leer archivos en formato CSV (Valores Separados por Comas).
- Por defecto, espera que los campos estén delimitados por comas.



```python
pd.read_fwf(path_or_buf)
```



- Diseñada para leer archivos con campos de ancho fijo, donde las columnas tienen un ancho especificado y no están separadas por delimitadores. "fwf" significa "fixed width formatted".
- Útil para leer datos de archivos donde las columnas están alineadas en cada línea sin un delimitador común como una coma o una tabulación.

**Escritura**



```python
df.to_csv(path_or_buf, sep=',', index=True, header=True,  ...)
```



## Clipboard<a name="id3"></a>

Pandas proporciona funcionalidades para leer y escribir datos desde y hacia el portapapeles (clipboard). Esto puede ser útil si estás trabajando con datos que necesitas copiar de una aplicación (como una hoja de cálculo) y pegar en un DataFrame de Pandas, o viceversa.


```python
pd.read_clipboard()
```

Esta función intenta interpretar el contenido del clipboard como un DataFrame, lo cual es útil si has copiado datos tabulares


```python
df.to_clipboard()
```

Esto copiará los datos del DataFrame en el formato adecuado para pegar en aplicaciones como Excel.

Es importante tener en cuenta que el manejo del clipboard puede variar según el sistema operativo y el entorno en el que estés trabajando. Además, la eficiencia de esta funcionalidad puede depender del tamaño de los datos: es práctica para datos pequeños, pero puede no ser ideal para conjuntos de datos muy grandes.

## Exel<a name="id4"></a>

Pandas ofrece un conjunto de herramientas que facilitan la lectura y escritura de datos en formato Excel

**Lectura**


```python
pd.read_excel('archivo.xlsx')
```

Lee un archivo Excel y lo convierte en un DataFrame de Pandas.

Asegúrate de que el paquete **openpyxl** esté instalado en tu entorno, ya que Pandas lo utiliza para leer archivos Excel. Si el archivo Excel es grande, la lectura puede llevar tiempo. Además, ten en cuenta el uso de memoria, especialmente con archivos muy grandes.


```python
pd.ExcelFile('myfile.xlsx')
```

Se utiliza para crear un objeto ExcelFile, el cual sirve como una especie de manejador o punto de acceso para trabajar con archivos Excel en Pandas. Este método es especialmente útil cuando necesitas trabajar con múltiples hojas de un mismo archivo Excel.

Metodos


```python
# Lee una hoja específica del archivo Excel como un DataFrame.
pd.ExcelFile.parse('sheet_name')

# Devuelve una lista con los nombres de todas las hojas en el archivo Excel.
pd.ExcelFile.sheet_names('myfile.xlsx')

# Cierra el archivo Excel.
ExcelFile.close()
```

Ejemplo:


```python
# Otro metodo con with
with pd.ExcelFile("myfile.xls") as xls:
    df1 = pd.read_excel(xls, "Sheet1")

# Leyendo hojas individuales
hoja1 = xlsx.parse('Hoja1')
# Extrayendo los nombres de todas las hojas
hojas = xlsx.sheet_names
# Cerrando el archivo
xlsx.close()
```

**Escritura**


```python
df1.to_excel('output1.xlsx')
```

Es utilizado para escribir un DataFrame en un archivo Excel. Este método es muy útil cuando necesitas exportar datos de Pandas a un formato que es ampliamente utilizado en aplicaciones de hojas de cálculo como Microsoft Excel.


```python
pd.ExcelWriter('mi_archivo.xlsx')
```


```python
writer = pd.ExcelWriter('mi_archivo.xlsx', engine='openpyxl')

# escribe al fichero excel
df1.to_excel(writer, sheet_name='Hoja1')
df2.to_excel(writer, sheet_name='Hoja2')

# guarda el archivo
writer.save()

# usando en un contexto with, que asegura que el archivo se cierra completamente
with pd.ExcelWriter('mi_archivo.xlsx', engine='openpyxl') as writer:
    df1.to_excel(writer, sheet_name='Hoja1')
    df2.to_excel(writer, sheet_name='Hoja2')

```

ExcelWriter en Pandas es una clase que se utiliza para escribir en archivos Excel con múltiples hojas de datos. Es especialmente útil cuando quieres exportar diferentes DataFrames a diferentes hojas en un mismo archivo Excel.

- Para crear un objeto ExcelWriter, simplemente especifica la ruta del archivo Excel donde quieres escribir.
- También puedes especificar el motor que se utilizará para escribir el archivo (por ejemplo, openpyxl para archivos .xlsx o xlwt para archivos .xls).
- Utiliza el método to_excel de un DataFrame y pasa el objeto ExcelWriter, especificando la hoja a la que deseas escribir.
- Puedes escribir en varias hojas añadiendo diferentes DataFrames.

## Json<a name="id5"></a>

**Lectura**


```python
pd.read_json('path', ...)
```

Es una función utilizada para leer una cadena de texto en formato JSON (JavaScript Object Notation) y convertirla en un DataFrame de Pandas.


```python
pd.json_normalize(data: dict | list[dict], ...)
```

Es una función en Pandas que se utiliza para aplanar estructuras de datos JSON en tablas planas. Es particularmente útil cuando trabajas con JSON que tiene estructuras anidadas y complejas, y deseas convertirlas en un DataFrame para análisis más sencillo.

**Escritura**


```python
df.to_json('path', ...)
```

Se utiliza para convertir un DataFrame en una cadena JSON (JavaScript Object Notation).

**Metadatos Json**


```python
pd.io.json.build_table_schema(df, ...)
```

Genera un diccionario que describe el formato y la estructura del DataFrame, incluyendo los nombres de las columnas y sus tipos de datos. Este esquema puede ser utilizado para validar datos o para intercambiar metadatos sobre la estructura del DataFrame con otras aplicaciones o sistemas.

## Html <a name="id6"></a>

**Lectura**


```python
pd.read_html('path', ...)
```

Lee tablas HTML en una lista de objetos DataFrame.  
Extraer datos tabulares de páginas web o documentos HTML. Útil para web scraping y para trabajar con datos almacenados en formato de tabla en HTML.

**Escritura**


```python
df.to_html('path', ...)
```

Crear una representación HTML de un DataFrame para incrustar en páginas web, informes HTML o para visualizaciones de datos en entornos que soportan HTML.


```python
df.style.to_html()
```

Exportar un DataFrame con estilos aplicados (como colores, fuentes, etc.) a HTML, lo que es útil para presentaciones de datos más atractivas y detalladas, especialmente en informes web y dashboards.

## XML <a name="id7"></a>


```python
df = pd.read_xml('path', ...)
```

Leer un documento XML como un DataFrame


```python
df.to_xml('path', ...)
```


```python
Renderice un DataFrame en un documento XML.
```

## Látex <a name="id8"></a>


```python
df.to_latex('ruta', ...)
```

Permite convertir un DataFrame de Pandas en una cadena de texto formateada en LaTeX. Esto es útil para incluir tablas de Pandas en documentos LaTeX. El modulo **jinja2** es un requisito y debe instalarse para que este método funcione.


```python
df.style.to_html()
```

Exportar un DataFrame con estilos aplicados (como colores, fuentes, etc.) a Látex, lo que es útil para presentaciones de datos más atractivas y detalladas, especialmente en informes web y dashboards. Este método puede convertir un Styler construido con HTML-CSS a LaTeX utilizando las conversiones limitadas.

## HDFStore <a name="id9"></a>

Es una estructura de almacenamiento de datos en Pandas que utiliza PyTables para leer y escribir datos usando el formato HDF5 (Hierarchical Data Format versión 5). HDF5 es un formato de archivo y una biblioteca de software diseñada para almacenar y gestionar datos grandes y complejos. Es ampliamente utilizado en campos científicos y de ingeniería para el almacenamiento eficiente de grandes volúmenes de datos.

**Ventajas de Usar HDF5 con Pandas:**

- Eficiencia en Espacio y Tiempo: HDF5 es altamente eficiente en términos de almacenamiento y velocidad de acceso, especialmente para grandes conjuntos de datos.
- Acceso a Datos Parciales: Puedes leer y escribir subconjuntos de datos sin necesidad de cargar todo el conjunto de datos en la memoria.
- Almacenamiento de Datos Complejos: Soporta una amplia gama de datos, desde simples arrays hasta tablas complejas y jerárquicas.
- Integridad de Datos: Soporta metadatos y ofrece opciones para la compresión de datos y la gestión de errores.

**Lectura**


```python
pd.read_hdf('path', key='name'..)
# key: El identificador del grupo. Se puede omitir si el archivo HDF contiene un único objeto pandas.
```

Lee datos del almacenamiento HDF5 y lo cierra si fue abierto por esta función. Utilizado para leer datos directamente de un archivo HDF5.


```python
HDFStore.put(key, value, ...)
```

Almacena un objeto en HDFStore. Útil para guardar DataFrames o Series en un archivo HDF5 con una clave específica


```python
HDFStore.append(key, df, ...)
```

Añade datos a una tabla existente en el archivo.Ideal para agregar datos incrementalmente a un conjunto de datos existente en un archivo HDF5.


```python
HDFStore.get(key)
```

Recupera un objeto de Pandas almacenado en el archivo.Permite acceder a datos específicos mediante una clave.


```python
HDFStore.select(key[, where, start, stop, ...]):
```

Recupera un objeto de Pandas almacenado en el archivo, opcionalmente basado en criterios where. Uso: Facilita la extracción de subconjuntos de datos basándose en condiciones específicas.


```python
HDFStore.info()[source]
```

 Imprime información detallada sobre el almacenamiento.


```python
HDFStore.keys()
```

Devuelve una lista de claves correspondientes a objetos almacenados en HDFStore.


```python
HDFStore.groups()
```

Devuelve una lista de todos los nodos de nivel superior.


```python
HDFStore.walk(where='/grupo_donde_empezar')
```

Recorre la jerarquía de grupos de PyTables para objetos de Pandas.Ideal para explorar en detalle la estructura interna del archivo HDF5 y los objetos de Pandas almacenados.


```python
Ejemplo
```


```python
df1 = pd.DataFrame([[1, 2], [3, 4]], columns=['A', 'B'])
store = pd.HDFStore("store.h5", 'w')
store.put('data', df1, format='table')
df2 = pd.DataFrame([[5, 6], [7, 8]], columns=['A', 'B'])
store.append('data', df2)
store.close()
for group in store.walk():
    print(group)
store.close()
```

## Feather <a name="id10"></a>

Feather es un formato de archivo binario liviano y eficiente para almacenar DataFrames que es especialmente útil para la lectura y escritura rápida de datos. Feather proporciona un puente entre el análisis de datos en **Python** (usando Pandas) y **R**, permitiendo un intercambio eficiente de datos entre estos dos entornos. Para usar Feather en Pandas, necesitarás instalar la biblioteca **pyarrow**, que incluye soporte para Feather.

**Lectura**


```python
pd.read_feather('path')
```

**Escritura**


```python
df.to_feather('path')
```

## Parquet <a name="id11"></a>

El formato Parquet es un formato de archivo columnar eficiente y comprimido, optimizado para trabajar con conjuntos de datos grandes. En Pandas, la integración con Parquet permite leer y escribir DataFrames de manera eficiente, aprovechando las ventajas de este formato. Parquet es ampliamente utilizado en ecosistemas de procesamiento de datos como Hadoop y Spark. Para trabajar con archivos Parquet en Pandas, necesitas instalar la biblioteca **pyarrow** o **fastparquet**, que proporcionan soporte para el formato Parquet.

**Lectura**


```python
df = pd.read_parquet('path', ...)
```

Esto carga los datos del archivo 'mi_dataframe.parquet' en el DataFrame df.

**Escritura**


```python
df.to_parquet('path/file.parquet', engine='pyarrow')
```


```python
Guarda el DataFrame 'df' en un archivo parquet.
```

## ORC <a name="id12"></a>

El formato ORC es un formato de archivo columnar que es comúnmente utilizado en el ecosistema Hadoop, particularmente con herramientas como Hive y Spark. Está optimizado para almacenamiento eficiente y procesamiento rápido de grandes conjuntos de datos.

**Lectura**


```python
pd.read_orc('path', ...)
```

**Escritura**


```python
df.to_orc('path', ...)
```

## SAS <a name="id13"></a>

SAS (Statistical Analysis System) es un sistema de software para análisis de datos, y sus archivos son comúnmente utilizados en el campo de la estadística y análisis de datos empresariales. Los archivos de SAS suelen tener extensiones .sas7bdat para los archivos de datos y .sas7bcat para los archivos de catálogo.

**Lectura**


```python
pd.read_sas('path', ...)
```

## SPSS <a name="id14"></a>

Funcionalidades para trabajar con archivos SPSS, un formato de archivo utilizado por el software de análisis estadístico SPSS. Estas funcionalidades se centran principalmente en la lectura de archivos SPSS.

**Lectura**


```python
pd.read_spss('path', ...)
```

## SQL <a name="id15"></a>

La funcionalidad para interactuar con bases de datos SQL es una parte esencial para el manejo de datos, especialmente en aplicaciones que requieren interacción con sistemas de gestión de bases de datos relacionales. Pandas proporciona herramientas para leer datos desde y escribir datos en bases de datos SQL de manera eficiente y sencilla.

**Lectura**


```python
pd.read_sql_table ('table_name', connection, ...)
```

Lea la tabla de la base de datos SQL en un DataFrame. Dado un nombre de tabla y un SQLAlchemy conectable, devuelve un DataFrame. Esta función no admite conexiones DBAPI.


```python
pd.read_sql_query('sql_query', connection, index_col=None, ...)
```

Devuelve un DataFrame correspondiente al conjunto de resultados de la cadena de consulta. Opcionalmente, proporcione un parámetro index_col para usar una de las columnas como índice; de ​​lo contrario, se usará el índice entero predeterminado.


```python
pd.read_sql('table_name' o 'sql_query', con, ...)
```

Lea una consulta SQL o una tabla de base de datos en un DataFrame. Esta función es un contenedor conveniente para read_sql_tabley read_sql_query(para compatibilidad con versiones anteriores). Delegará a la función específica dependiendo de la entrada proporcionada. Una consulta SQL se enrutará a read_sql_query, mientras que el nombre de una tabla de base de datos se enrutará a read_sql_table


```python
df.to_sql('name', con, ...)
```

Escriba registros almacenados en un DataFrame en una base de datos SQL. Se admiten bases de datos compatibles con SQLAlchemy  . Las tablas se pueden crear, agregar o sobrescribir nuevas.

## STATA <a name="id17"></a>

Pandas proporciona funcionalidades para interactuar con archivos de datos Stata, un formato de archivo utilizado por el software estadístico Stata. Estas funcionalidades incluyen leer archivos Stata en DataFrames de Pandas y exportar DataFrames a archivos Stata. Además, Pandas ofrece herramientas para acceder a metadatos específicos de archivos Stata.


```python
pd.read_stata('path')
```

Cargar datos de un archivo Stata (.dta) en un DataFrame de Pandas. Permite especificar cómo se deben manejar fechas, categorías y otros tipos de datos durante la importación.


```python
pd.to_stata('path')
```

Exporta un DataFrame de Pandas a un archivo Stata. Permite especificar cómo se deben convertir las fechas, si incluir el índice del DataFrame y cómo manejar las etiquetas de las variables.

Acceso a Metadatos de Archivos Stata:


```python
StataReader.data_label() # Devuelve la etiqueta de los datos del archivo Stata.
StataReader.value_labels() #  Devuelve un dict anidado que asocia cada nombre de variable con sus valores y etiquetas.
StataReader.variable_labels() # Devuelve un diccionario que asocia cada nombre de variable con su etiqueta correspondiente.
```
