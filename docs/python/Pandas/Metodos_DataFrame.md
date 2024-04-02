---
layout: default
title: Metodos Dataframe
nav_order: 4
parent: Pandas
grand_parent: Python
---



# DataFrame

## Constructor


```python
pd.DataFrame(
    data=None, # ndarray (estructurado u homogéneo), Iterable, dict, o DataFrame
    index=None, # Índice a utilizar para el marco resultante. 
    columns=None, # Etiquetas de columna a utilizar para el marco resultante si no tienen.  RangeIndex(0, 1, 2, ..., n). 
    dtype=None, # Tipo de datos a forzar. Solo se permite un único dtype. Si es None, se inferirá.
    copy=None # Copiar datos de las entradas. Para datos dict, el valor predeterminado de None se comporta como copy=True. 
)
```

### Atributos

- <code>T</code>: La transposición del DataFrame.
- <code>at</code>: Accede a un valor único para un par de etiquetas de fila/columna.
- <code>attrs</code>: Diccionario de atributos globales de este conjunto de datos.
- <code>axes</code>: Devuelve una lista que representa los ejes del DataFrame.
- <code>columns</code>: Las etiquetas de las columnas del DataFrame.
- <code>dtypes</code>: Devuelve los dtypes en el DataFrame.
- <code>empty</code>: Indicador de si la Serie/DataFrame está vacío.
- <code>flags</code>: Obtiene las propiedades asociadas con este objeto de pandas.
- <code>iat</code>: Accede a un valor único para un par de fila/columna por posición entera.
- <code>iloc</code>: (OBSOLETO) Indexación basada puramente en la ubicación entera para la selección por posición.
- <code>index</code>: El índice (etiquetas de fila) del DataFrame.
- <code>loc</code>: Accede a un grupo de filas y columnas por etiqueta(s) o un array booleano.
- <code>ndim</code>: Devuelve un entero que representa el número de ejes/dimensiones del array.
- <code>shape</code>: Devuelve una tupla que representa la dimensionalidad del DataFrame.
- <code>size</code>: Devuelve un entero que representa el número de elementos en este objeto.
- <code>style</code>: Devuelve un objeto Styler.
- <code>values</code>: Devuelve una representación de Numpy del DataFrame.

### Conversión

- <code>.astype(dtype[, copy, errors])</code> : Convierte un objeto de pandas a un tipo de datos especificado dtype.
- <code>.convert_dtypes[infer_objects, ...])</code> : Convierte columnas a los mejores tipos de datos posibles, utilizando tipos de datos que soportan pd.NA.
- <code>.infer_objects([copy])</code> : Intenta inferir mejores tipos de datos para columnas de tipo objeto.
- <code>.copy([deep])</code> : Hace una copia de los índices y datos de este objeto.
- <code>.bool()</code> : (DEPRECATED) Devuelve el valor booleano de una Serie o DataFrame de un solo elemento.

### Indexación e iteración

- <code>.head([n])</code> : Devuelve las primeras n filas.
- <code>.at</code>: Accede a un único valor para un par etiqueta de fila/columna.
- <code>.iat</code>: Accede a un único valor para un par de posición de fila/columna mediante un índice entero.
- <code>.loc</code>: Accede a un grupo de filas y columnas por etiqueta(s) o un array booleano.
- <code>.iloc</code>: (DEPRECATED) Indexación puramente basada en la ubicación entera para la selección por posición.
- <code>.insert(loc, column, value[, ...])</code> : Inserta una columna en el DataFrame en la ubicación especificada.
- <code>.__iter__()</code> : Itera sobre el eje de información.
- <code>.items()</code> : Itera sobre pares (nombre de columna, Serie).
- <code>.keys()</code> : Obtiene el 'eje de información' (ver Indexación para más detalles).
- <code>.iterrows()</code> : Itera sobre las filas del DataFrame como pares (índice, Serie).
- <code>.itertuples([index, name])</code> : Itera sobre las filas del DataFrame como namedtuples.
- <code>.pop(item)</code> : Devuelve el item y lo elimina del marco.
- <code>.tail([n])</code> : Devuelve las últimas n filas.
- <code>.xs(key[, axis, level, drop_level])</code> : Devuelve una sección cruzada de la Serie/DataFrame.
- <code>.get(key[, default])</code> : Obtiene un item del objeto para una clave dada (por ejemplo, una columna del DataFrame).
- <code>.isin(values)</code> : Determina si cada elemento en el DataFrame está contenido en values.
- <code>.where(cond[, other, inplace, ...])</code> : Reemplaza valores donde la condición es Falsa.
- <code>.mask(cond[, other, inplace, axis, ...])</code> : Reemplaza valores donde la condición es Verdadera.
- <code>.query(expr, *[, inplace])</code> : Consulta las columnas de un DataFrame con una expresión booleana.

### Aplicación de Funciones, GroupBy y Ventanas

- <code>.apply(func[, axis, raw, ...])</code> : Aplica una función a lo largo de un eje del DataFrame.
- <code>.map(func[, na_action])</code> : Aplica una función elemento a elemento a un DataFrame.
- <code>.applymap(func[, na_action])</code> : (DEPRECATED) Aplica una función elemento a elemento a un DataFrame.
- <code>.pipe(func, *args, <code>kwargs)</code> : Aplica funciones encadenables que esperan Series o DataFrames.
- <code>.agg([func, axis])</code> : Agrega utilizando una o más operaciones sobre el eje especificado.
- <code>.aggregate([func, axis])</code> : Agrega utilizando una o más operaciones sobre el eje especificado.
- <code>.transform(func[, axis])</code> : Llama a func en sí mismo, produciendo un DataFrame con la misma forma de eje que sí mismo.
- <code>.groupby([by, axis, level, ...])</code> : Agrupa el DataFrame usando un mapeador o por una Serie de columnas.
- <code>.rolling(window[, min_periods, ...])</code> : Proporciona cálculos de ventana deslizante.
- <code>.expanding([min_periods, axis, method])</code> : Proporciona cálculos de ventana expansiva.
- <code>.ewm([com, span, halflife, alpha, ...])</code> : Proporciona cálculos ponderados exponencialmente (EW).

### Cálculos / Estadísticas Descriptivas

- <code>.abs()</code> : Devuelve una Serie/DataFrame con el valor numérico absoluto de cada elemento.
- <code>.all([axis, bool_only, skipna])</code> : Devuelve si todos los elementos son Verdaderos, potencialmente sobre un eje.
- <code>.any(*[, axis, bool_only, skipna])</code> : Devuelve si algún elemento es Verdadero, potencialmente sobre un eje.
- <code>.clip([lower, upper, axis, inplace])</code> : Recorta valores en los umbrales de entrada.
- <code>.corr([method, min_periods, ...])</code> : Calcula la correlación par a par de columnas, excluyendo valores NA/nulos.
- <code>.corrwith(other[, axis, drop, ...])</code> : Calcula la correlación par a par.
- <code>.count([axis, numeric_only])</code> : Cuenta celdas no-NA para cada columna o fila.
- <code>.cov([min_periods, ddof, numeric_only])</code> : Calcula la covarianza par a par de columnas, excluyendo valores NA/nulos.
- <code>.cummax([axis, skipna])</code> : Devuelve el máximo acumulativo sobre un eje de Serie o DataFrame.
- <code>.cummin([axis, skipna])</code> : Devuelve el mínimo acumulativo sobre un eje de Serie o DataFrame.
- <code>.cumprod([axis, skipna])</code> : Devuelve el producto acumulativo sobre un eje de Serie o DataFrame.
- <code>.cumsum([axis, skipna])</code> : Devuelve la suma acumulativa sobre un eje de Serie o DataFrame.
- <code>.describe([percentiles, include, ...])</code> : Genera estadísticas descriptivas.
- <code>.diff([periods, axis])</code> : Primera diferencia discreta de elemento.
- <code>.eval(expr, *[, inplace])</code> : Evalúa una cadena que describe operaciones en columnas de DataFrame.
- <code>.kurt([axis, skipna, numeric_only])</code> : Devuelve la curtosis imparcial solicitada sobre el eje.
- <code>.kurtosis([axis, skipna, numeric_only])</code> : Devuelve la curtosis imparcial sobre el eje solicitado.
- <code>.max([axis, skipna, numeric_only])</code> : Devuelve el máximo de los valores sobre el eje solicitado.
- <code>.mean([axis, skipna, numeric_only])</code> : Devuelve la media de los valores sobre el eje solicitado.
- <code>.median([axis, skipna, numeric_only])</code> : Devuelve la mediana de los valores sobre el eje solicitado.
- <code>.min([axis, skipna, numeric_only])</code> : Devuelve el mínimo de los valores sobre el eje solicitado.
- <code>.mode([axis, numeric_only, dropna])</code> : Obtiene la(s) moda(s) de cada elemento a lo largo del eje seleccionado.
- <code>.pct_change([periods, fill_method, ...])</code> : Cambio fraccional entre el elemento actual y uno anterior.
- <code>.prod([axis, skipna, numeric_only, ...])</code> : Devuelve el producto de los valores sobre el eje solicitado.
- <code>.product([axis, skipna, ...])</code> : Devuelve el producto de los valores sobre el eje solicitado.
- <code>.quantile([q, axis, numeric_only, ...])</code> : Devuelve valores en el cuantil dado sobre el eje solicitado.
- <code>.rank([axis, method, numeric_only, ...])</code> : Calcula los rangos de datos numéricos (1 a n) a lo largo del eje.
- <code>.round([decimals])</code> : Redondea un DataFrame a un número variable de lugares decimales.
- <code>.sem([axis, skipna, ddof, numeric_only])</code> : Devuelve el error estándar no sesgado de la media sobre el eje solicitado.
- <code>.skew([axis, skipna, numeric_only])</code> : Devuelve la asimetría no sesgada sobre el eje solicitado.
- <code>.sum([axis, skipna, numeric_only, ...])</code> : Devuelve la suma de los valores sobre el eje solicitado.
- <code>.std([axis, skipna, ddof, numeric_only])</code> : Devuelve la desviación estándar de la muestra sobre el eje solicitado.
- <code>.var([axis, skipna, ddof, numeric_only])</code> : Devuelve la varianza imparcial sobre el eje solicitado.
- <code>.nunique([axis, dropna])</code> : Cuenta el número de elementos distintos en el eje especificado.
- <code>.value_counts([subset, normalize, ...])</code> : Devuelve una Serie que contiene la frecuencia de cada fila distinta en el DataFrame.

### Reindexación / Selección / Manipulación de Etiquetas

- <code>.add_prefix(prefix[, axis])</code> : Prefija las etiquetas con el prefijo de cadena.
- <code>.add_suffix(suffix[, axis])</code> : Sufija las etiquetas con el sufijo de cadena.
- <code>.align(other[, join, axis, level, ...])</code> : Alinea dos objetos en sus ejes con el método de unión especificado.
- <code>.at_time(time[, asof, axis])</code> : Selecciona valores en un momento particular del día.
- <code>.between_time(start_time, end_time)</code> : Selecciona valores entre momentos particulares del día.
- <code>.drop([labels, axis, index, ...])</code> : Elimina las etiquetas especificadas de filas o columnas.
- <code>.drop_duplicates([subset, keep, ...])</code> : Devuelve DataFrame con filas duplicadas eliminadas.
- <code>.duplicated([subset, keep])</code> : Devuelve Serie booleana que denota filas duplicadas.
- <code>.equals(other)</code> : Prueba si dos objetos contienen los mismos elementos.
- <code>.filter([items, like, regex, axis])</code> : Subconjunto de filas o columnas del dataframe según las etiquetas de índice especificadas.
- <code>.first(offset)</code> : (DEPRECATED) Selecciona periodos iniciales de datos de series temporales basados en un desplazamiento de fecha.
- <code>.head([n])</code> : Devuelve las primeras n filas.
- <code>.idxmax([axis, skipna, numeric_only])</code> : Devuelve el índice de la primera ocurrencia del máximo sobre el eje solicitado.
- <code>.idxmin([axis, skipna, numeric_only])</code> : Devuelve el índice de la primera ocurrencia del mínimo sobre el eje solicitado.
- <code>.last(offset)</code> : (DEPRECATED) Selecciona periodos finales de datos de series temporales basados en un desplazamiento de fecha.
- <code>.reindex([labels, index, columns, ...])</code> : Conforma DataFrame a nuevo índice con lógica de llenado opcional.
- <code>.reindex_like(other[, method, ...])</code> : Devuelve un objeto con índices coincidentes como otro objeto.
- <code>.rename([mapper, index, columns, ...])</code> : Renombra columnas o etiquetas de índice.
- <code>.rename_axis([mapper, index, ...])</code> : Establece el nombre del eje para el índice o las columnas.
- <code>.reset_index([level, drop, ...])</code> : Restablece el índice, o un nivel de este.
- <code>.sample([n, frac, replace, ...])</code> : Devuelve una muestra aleatoria de elementos de un eje del objeto.
- <code>.set_axis(labels, *[, axis, copy])</code> : Asigna el índice deseado al eje dado.
- <code>.set_index(keys, *[, drop, append, ...])</code> : Establece el índice del DataFrame usando columnas existentes.
- <code>.tail([n])</code> : Devuelve las últimas n filas.
- <code>.take(indices[, axis])</code> : Devuelve los elementos en los índices posicionales dados a lo largo de un eje.
- <code>.truncate([before, after, axis, copy])</code> : Trunca una Serie o DataFrame antes y después de algún valor de índice.

### Manejo de Datos Faltantes

- <code>.backfill(*[, axis, inplace, ...])</code> : (DEPRECATED) Llena valores NA/NaN usando la siguiente observación válida para llenar el hueco.
- <code>.bfill(*[, axis, inplace, limit, ...])</code> : Llena valores NA/NaN usando la siguiente observación válida para llenar el hueco.
- <code>.dropna(*[, axis, how, thresh, ...])</code> : Elimina valores faltantes.
- <code>.ffill(*[, axis, inplace, limit, ...])</code> : Llena valores NA/NaN propagando la última observación válida al siguiente válido.
- <code>.fillna([value, method, axis, ...])</code> : Llena valores NA/NaN usando el método especificado.
- <code>.interpolate([method, axis, limit, ...])</code> : Llena valores NaN usando un método de interpolación.
- <code>.isna()</code> : Detecta valores faltantes.
- <code>.isnull()</code> : DataFrame.isnull es un alias de DataFrame.isna.
- <code>.notna()</code> : Detecta valores existentes (no faltantes).
- <code>.notnull()</code> : DataFrame.notnull es un alias de DataFrame.notna.
- <code>.pad(*[, axis, inplace, limit, ...])</code> : (DEPRECATED) Llena valores NA/NaN propagando la última observación válida al siguiente válido.
- <code>.replace([to_replace, value, ...])</code> : Reemplaza valores dados en to_replace con value.

### Reestructuración, Ordenación, Transposición

- <code>.droplevel(level[, axis])</code> : Devuelve Series/DataFrame con nivel(es) de índice/columna solicitados eliminados.
- <code>.pivot(*, columns[, index, values])</code> : Devuelve DataFrame reorganizado por los valores de índice/columna dados.
- <code>.pivot_table([values, index, ...])</code> : Crea una tabla dinámica al estilo de una hoja de cálculo como un DataFrame.
- <code>.reorder_levels(order[, axis])</code> : Reorganiza niveles de índice usando el orden de entrada.
- <code>.sort_values(by, *[, axis, ...])</code> : Ordena por los valores a lo largo de cualquiera de los ejes.
- <code>.sort_index(*[, axis, level, ...])</code> : Ordena el objeto por etiquetas (a lo largo de un eje).
- <code>.nlargest(n, columns[, keep])</code> : Devuelve las primeras n filas ordenadas por columnas en orden descendente.
- <code>.nsmallest(n, columns[, keep])</code> : Devuelve las primeras n filas ordenadas por columnas en orden ascendente.
- <code>.swaplevel([i, j, axis])</code> : Intercambia niveles i y j en un MultiIndex.
- <code>.stack([level, dropna, sort, ...])</code> : Apila los niveles prescritos de columnas a índice.
- <code>.unstack([level, fill_value, sort])</code> : Desapila un nivel de las etiquetas de índice (necesariamente jerárquicas).
- <code>.swapaxes(axis1, axis2[, copy])</code> : (DEPRECATED) Intercambia ejes e intercambia los valores de los ejes apropiadamente.
- <code>.melt([id_vars, value_vars, ...])</code> : Desanida un DataFrame de formato ancho a largo, dejando opcionalmente identificadores establecidos.
- <code>.explode(column[, ignore_index])</code> : Transforma cada elemento de un tipo lista en una fila, replicando los valores de índice.
- <code>.squeeze([axis])</code> : Convierte objetos de eje unidimensional en escalares.
- <code>.to_xarray()</code> : Devuelve un objeto xarray del objeto pandas.
- <code>.T</code>: La transposición del DataFrame.
- <code>.transpose(*args[, copy])</code> : Transpone índice y columnas.

### Combinación / Comparación / Unión / Fusión

- <code>.assign(<code>kwargs)</code> : Asigna nuevas columnas a un DataFrame.
- <code>.compare(other[, align_axis, ...])</code> : Compara con otro DataFrame y muestra las diferencias.
- <code>.join(other[, on, how, lsuffix, ...])</code> : Une columnas de otro DataFrame.
- <code>.merge(right[, how, on, left_on, ...])</code> : Fusiona objetos DataFrame o Series nombradas con una unión al estilo de bases de datos.
- <code>.update(other[, join, overwrite, ...])</code> : Modifica en el lugar usando valores no NA de otro DataFrame.

### Relacionado con Series Temporales

- <code>.asfreq(freq[, method, how, ...])</code> : Convierte series temporales a la frecuencia especificada.
- <code>.asof(where[, subset])</code> : Devuelve la(s) última(s) fila(s) sin ningún NaN antes de where.
- <code>.shift([periods, freq, axis, ...])</code> : Desplaza el índice por el número deseado de períodos con una frecuencia de tiempo opcional.
- <code>.first_valid_index()</code> : Devuelve el índice del primer valor no NA o None, si no se encuentra ningún valor no NA.
- <code>.last_valid_index()</code> : Devuelve el índice del último valor no NA o None, si no se encuentra ningún valor no NA.
- <code>.resample(rule[, axis, closed, ...])</code> : Reorganiza los datos de series temporales.
- <code>.to_period([freq, axis, copy])</code> : Convierte DataFrame de DatetimeIndex a PeriodIndex.
- <code>.to_timestamp<code>[freq, how, axis, copy])</code> : Convierte a DatetimeIndex de marcas de tiempo, al comienzo del período.
- <code>.tz_convert(tz[, axis, level, copy])</code> : Convierte el eje consciente de tz a la zona horaria objetivo.
- <code>.tz_localize(tz[, axis, level, ...])</code> : Localiza el índice tz-naive de una Serie o DataFrame a la zona horaria objetivo.

### Flags

Flags refer to attributes of the pandas object: Las propiedades del conjunto de datos (como la fecha en que se registró, la URL desde la que se accedió, etc.) deben almacenarse en DataFrame.attrs.
- <code>Flags(obj, *, allows_duplicate_labels)</code> : Flags que se aplican a objetos pandas.

### Metadatos

- <code>DataFrame<code>.attrs: DataFrame.attrs es un diccionario para almacenar metadatos globales para este DataFrame.
- <code>Warning</code>: DataFrame.attrs se considera experimental y puede cambiar sin previo aviso.
- <code>DataFrame<code>.attrs: Diccionario de atributos globales de este conjunto de datos.

### Plotting

- <code>.plot([x, y, kind, ax, ....])</code> : Accesor y método de plotting de DataFrame.
- <code>.plot.area([x, y, stacked])</code> : Dibuja un gráfico de área apilada.
- <code>.plot.bar([x, y])</code> : Gráfico de barras vertical.
- <code>.plot.barh([x, y])</code> : Crea un gráfico de barras horizontal.
- <code>.plot.box([by])</code> : Crea un diagrama de caja de las columnas del DataFrame.
- <code>.plot.density([bw_method, ind])</code> : Genera un gráfico de Estimación de Densidad Kernel usando kernels gaussianos.
- <code>.plot.hexbin(x, y[, C, ...])</code> : Genera un gráfico de agrupación hexagonal.
- <code>.plot.hist([by, bins])</code> : Dibuja un histograma de las columnas del DataFrame.
- <code>.plot.kde([bw_method, ind])</code> : Genera un gráfico de Estimación de Densidad Kernel usando kernels gaussianos.
- <code>.plot.line([x, y])</code> : Grafica Series o DataFrame como líneas.
- <code>.plot.pie(<code>kwargs)</code> : Genera un gráfico de tarta.
- <code>.plot.scatter(x, y[, s, c])</code> : Crea un gráfico de dispersión con tamaño y color de marcador variable.
- <code>.boxplot([column, by, ax, ...])</code> : Crea un diagrama de caja de las columnas del DataFrame.
- <code>.hist([column, by, grid, ...])</code> : Crea un histograma de las columnas del DataFrame.

### Sparse accessor

Métodos específicos y atributos de dtype sparse se proporcionan bajo el accesor DataFrame.sparse.
- <code>.sparse.density</code>: Razón de puntos no dispersos a puntos de datos totales (densos).
- <code>.sparse.from_spmatrix(data[, ...])</code> : Crea un nuevo DataFrame a partir de una matriz dispersa de scipy.
- <code>.sparse.to_coo()</code> : Devuelve el contenido del marco como una matriz COO dispersa de SciPy.
- <code>.sparse.to_dense()</code> : Convierte un DataFrame con valores dispersos a denso.

### Serialización / IO / Conversión

- <code>.from_dict(data[, orient, dtype, ...])</code> : Construye DataFrame a partir de un diccionario de elementos tipo array o diccionarios.
- <code>.from_records(data[, index, ...])</code> : Convierte ndarray estructurado o de registros a DataFrame.
- <code>.to_orc([path, engine, index, ...])</code> : Escribe un DataFrame en formato ORC.
- <code>.to_parquet([path, engine, ...])</code> : Escribe un DataFrame al formato binario parquet.
- <code>.to_pickle(path, *[, compression, ...])</code> : Serializa (pickle) el objeto a archivo.
- <code>.to_csv([path_or_buf, sep, na_rep, ...])</code> : Escribe el objeto a un archivo de valores separados por comas (csv).
- <code>.to_hdf(path_or_buf, *, key[, ...])</code> : Escribe los datos contenidos en un archivo HDF5 usando HDFStore.
- <code>.to_sql(name, con, *[, schema, ...])</code> : Escribe registros almacenados en un DataFrame a una base de datos SQL.
- <code>.to_dict([orient, into, index])</code> : Convierte el DataFrame a un diccionario.
- <code>.to_excel(excel_writer, *[, ...])</code> : Escribe el objeto a una hoja de Excel.
- <code>.to_json([path_or_buf, orient, ...])</code> : Convierte el objeto a una cadena JSON.
- <code>.to_html([buf, columns, col_space, ...])</code> : Renderiza un DataFrame como una tabla HTML.
- <code>.to_feather(path, <code>kwargs)</code> : Escribe un DataFrame al formato binario Feather.
- <code>.to_latex([buf, columns, header, ...])</code> : Renderiza el objeto a una tabulación LaTeX, longtable o tabla anidada.
- <code>.to_stata(path, *[, convert_dates, ...])</code> : Exporta el objeto DataFrame al formato dta de Stata.
- <code>.to_gbq(destination_table, *[, ...])</code> : (DEPRECATED) Escribe un DataFrame en una tabla de Google BigQuery.
- <code>.to_records([index, column_dtypes, ...])</code> : Convierte DataFrame a un arreglo de registros NumPy.
- <code>.to_string([buf, columns, ...])</code> : Renderiza un DataFrame a una salida tabular amigable para la consola.
- <code>.to_clipboard(*[, excel, sep])</code> : Copia el objeto al portapapeles del sistema.
- <code>.to_markdown([buf, mode, index, ...])</code> : Imprime DataFrame en formato amigable con Markdown.
- <code>.style</code>: Devuelve un objeto Styler.
- <code>.\__dataframe\__([nan_as_null, ...])</code> : Devuelve el objeto de intercambio de dataframe que implementa el protocolo de intercambio.


```python

```
