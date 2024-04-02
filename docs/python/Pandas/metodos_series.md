---
layout: default
title: Metodos Series
nav_order: 3
parent: Pandas
grand_parent: Python
---



# Series

## Constructor



```python
pd.series(
    data=None, # matriz, iterable, dict o escalar. Si los datos son un diccionario, se mantiene el orden de los argumentos.
    index=None, # Los valores deben ser hash y tener la misma longitud que los datos.
    dtype=None, # Tipo de datos para la serie de salida. Si no se especifica, esto se deducirá de los datos.
    name=None, # Hashable, predeterminado Ninguno. El nombre a darle a la Serie.
    copy=None, # booleano, predeterminado Falso. Copie los datos de entrada. Solo afecta la entrada Serie o ndarray 1d.
    fastpath=_NoDefault.no_default
)
```



`Ndarray` unidimensional con etiquetas de ejes (incluidas series temporales).


```python
import pandas as pd
d = {'a': 1, 'b': 2, 'c': 3}
serie = pd.Series(data=d, index=['a', 'b', 'c'])
serie
```




    a    1
    b    2
    c    3
    dtype: int64



## Atributos

- <code>.T</code> Devuelve la transpuesta, que por definición es el mismo objeto.
- <code>.array</code> El ExtensionArray de los datos que respaldan esta Serie o Índice.
- <code>.at</code> Accede a un valor único para un par de etiquetas de fila/columna.
- <code>.attrs</code> Diccionario de atributos globales de este conjunto de datos.
- <code>.axes</code> Devuelve una lista de las etiquetas del eje de fila.
- <code>.dtype</code> Devuelve el objeto dtype de los datos subyacentes.
- <code>.dtypes</code> Devuelve el objeto dtype de los datos subyacentes.
- <code>.empty</code> Indicador de si la Serie o DataFrame está vacío.
- <code>.flags</code> Obtiene las propiedades asociadas con este objeto de pandas.
- <code>.hasnans</code> Devuelve True si hay algún NaN.
- <code>.iat</code> Accede a un valor único para un par de fila/columna por posición entera.
- <code>.iloc</code> (OBSOLETO) Indexación basada puramente en la ubicación entera para la selección por posición.
- <code>.index</code> El índice (etiquetas de los ejes) de la Serie.
- <code>.is_monotonic_decreasing</code> Devuelve un booleano si los valores en el objeto disminuyen monótonamente.
- <code>.is_monotonic_increasing</code> Devuelve un booleano si los valores en el objeto aumentan monótonamente.
- <code>.is_unique</code> Devuelve un booleano si los valores en el objeto son únicos.
- <code>.loc</code> Accede a un grupo de filas y columnas por etiqueta(s) o un array booleano.
- <code>.name</code> Devuelve el nombre de la Serie.
- <code>.nbytes</code> Devuelve el número de bytes en los datos subyacentes.
- <code>.ndim</code> Número de dimensiones de los datos subyacentes, por definición 1.
- <code>.shape</code> Devuelve una tupla con la forma de los datos subyacentes.
- <code>.size</code> Devuelve el número de elementos en los datos subyacentes.
- <code>.values</code> Devuelve la Serie como ndarray o tipo similar a ndarray dependiendo del dtype.

## Metodos

### Conversion

- <code>.astypedtype[, copy, errors]</code> Convierte un objeto de pandas a un dtype especificado.
- <code>.convert_dtypes[infer_objects, ...]</code> Convierte columnas a los mejores dtypes posibles usando dtypes que soportan pd.NA.
- <code>.infer_objects[copy]</code> Intenta inferir mejores dtypes para columnas de objetos.
- <code>.copy[deep]</code> Hace una copia de los índices y datos de este objeto.
- <code>.bool</code> (OBSOLETO) Devuelve el valor booleano de una Serie o DataFrame de un solo elemento.
- <code>.to_numpy[dtype, copy, na_value]</code> Un ndarray de NumPy que representa los valores en esta Serie o Índice.
- <code>.to_period[freq, copy]</code> Convierte la Serie de un DatetimeIndex a un PeriodIndex.
- <code>.to_timestamp[freq, how, copy]</code> Convierte a un DatetimeIndex de Timestamps, al inicio del período.
- <code>.to_list</code> Devuelve una lista de los valores.
- <code>.array[dtype]</code> Devuelve los valores como un array de NumPy.

### Indexing, iteration

- <code>.getkey[, default]</code> Obtiene un elemento del objeto para una clave dada (por ejemplo, columna de DataFrame).
- <code>.at</code>: Accede a un valor único para un par de etiquetas de fila/columna.
- <code>.iat</code>: Accede a un valor único para un par de fila/columna por posición entera.
- <code>.loc</code>: Accede a un grupo de filas y columnas por etiqueta(s) o un array booleano.
- <code>.iloc</code>: (OBSOLETO) Indexación basada puramente en la ubicación entera para la selección por posición.
- <code>.iter</code> Devuelve un iterador de los valores.
- <code>.items</code> Itera perezosamente sobre tuplas de (índice, valor).
- <code>.keys</code> Devuelve un alias para el índice.
- <code>.popitem</code> Devuelve un elemento y lo elimina de la serie.
- <code>.item</code> Devuelve el primer elemento de los datos subyacentes como un escalar de Python.
- <code>.xskey[, axis, level, drop_level]</code> Devuelve una sección transversal de la Serie/DataFrame.

### Function application, GroupBy & window

- <code>.applyfunc[, convert_dtype, args, by_row]</code> Invoca una función sobre los valores de la Serie.
- <code>.agg[func, axis]</code> Agrega utilizando una o más operaciones sobre el eje especificado.
- <code>.aggregate[func, axis]</code> Agrega utilizando una o más operaciones sobre el eje especificado.
- <code>.transformfunc[, axis]</code> Llama a func en sí misma produciendo una Serie con la misma forma de eje que ella misma.
- <code>.maparg[, na_action]</code> Mapea los valores de la Serie de acuerdo con un mapeo de entrada o función.
- <code>.groupby[by, axis, level, as_index, ...]</code> Agrupa la Serie utilizando un mapeador o por una Serie de columnas.
- <code>.rollingwindow[, min_periods, ...]</code> Proporciona cálculos de ventana rodante.
- <code>.expanding[min_periods, axis, method]</code> Proporciona cálculos de ventana expansiva.
- <code>.ewm[com, span, halflife, alpha, ...]</code> Proporciona cálculos ponderados exponencialmente (EW).
- <code>.pipefunc, *args, kwargs</code> Aplica funciones encadenables que esperan Series o DataFrames.

### Computations / descriptive statstistic

- <code>.abs()</code>: Devuelve una Serie/DataFrame con el valor numérico absoluto de cada elemento.
- <code>.all[axis, bool_only, skipna]</code> Devuelve si todos los elementos son Verdaderos, potencialmente sobre un eje.
- <code>.any[, axis, bool_only, skipna]</code> Devuelve si algún elemento es Verdadero, potencialmente sobre un eje.
- <code>.autocorr[lag]</code> Calcula la autocorrelación de lag-N.
- <code>.betweenleft, right[, inclusive]</code> Devuelve una Serie booleana equivalente a left <= serie <= right.
- <code>.clip[lower, upper, axis, inplace]</code> Recorta valores en los umbrales de entrada.
- <code>.corrother[, method, min_periods]</code> Calcula la correlación con otra Serie, excluyendo valores faltantes.
- <code>.count()</code>: Devuelve el número de observaciones no NA/nulas en la Serie.
- <code>.covother[, min_periods, ddof]</code> Calcula la covarianza con la Serie, excluyendo valores faltantes.
- <code>.cummax[axis, skipna]</code> Devuelve el máximo acumulativo sobre un eje de DataFrame o Serie.
- <code>.cummin[axis, skipna]</code> Devuelve el mínimo acumulativo sobre un eje de DataFrame o Serie.
- <code>.cumprod[axis, skipna]</code> Devuelve el producto acumulativo sobre un eje de DataFrame o Serie.
- <code>.cumsum[axis, skipna]</code> Devuelve la suma acumulativa sobre un eje de DataFrame o Serie.
- <code>.describe[percentiles, include, exclude]</code> Genera estadísticas descriptivas.
- <code>.diff[periods]</code> Primera diferencia discreta del elemento.
- <code>.factorize[sort, use_na_sentinel]</code> Codifica el objeto como un tipo enumerado o variable categórica.
- <code>.kurt[axis, skipna, numeric_only]</code> Devuelve la curtosis imparcial sobre el eje solicitado.
- <code>.max[axis, skipna, numeric_only]</code> Devuelve el máximo de los valores sobre el eje solicitado.
- <code>.mean[axis, skipna, numeric_only]</code> Devuelve la media de los valores sobre el eje solicitado.
- <code>.median[axis, skipna, numeric_only]</code> Devuelve la mediana de los valores sobre el eje solicitado.
- <code>.min[axis, skipna, numeric_only]</code> Devuelve el mínimo de los valores sobre el eje solicitado.
- <code>.mode[dropna]</code> Devuelve la(s) moda(s) de la Serie.
- <code>.nlargest[n, keep]</code> Devuelve los n elementos más grandes.
- <code>.nsmallest[n, keep]</code> Devuelve los n elementos más pequeños.
- <code>.pct_change[periods, fill_method, ...]</code> Cambio fraccional entre el elemento actual y un elemento anterior.
- <code>.prod[axis, skipna, numeric_only, ...]</code> Devuelve el producto de los valores sobre el eje solicitado.
- <code>.quantile[q, interpolation]</code> Devuelve el valor en el cuantil dado.
- <code>.rank([axis, method, numeric_only, ...])</code> Calcula los rangos de datos numéricos (1 a n) a lo largo del eje.
- <code>.sem[axis, skipna, ddof, numeric_only]</code> Devuelve el error estándar imparcial de la media sobre el eje solicitado.
- <code>.skew[axis, skipna, numeric_only]</code> Devuelve la asimetría imparcial sobre el eje solicitado.
- <code>.std[axis, skipna, ddof, numeric_only]</code> Devuelve la desviación estándar de la muestra sobre el eje solicitado.
- <code>.sum[axis, skipna, numeric_only, ...]</code> Devuelve la suma de los valores sobre el eje solicitado.
- <code>.var[axis, skipna, ddof, numeric_only]</code> Devuelve la varianza imparcial sobre el eje solicitado.
- <code>.kurtosis[axis, skipna, numeric_only]</code> Devuelve la curtosis imparcial sobre el eje solicitado.
- <code>.unique()</code>: Devuelve valores únicos del objeto Serie.
- <code>.nunique[dropna]</code> Devuelve el número de elementos únicos en el objeto.
- <code>.is_unique</code>: Devuelve un booleano si los valores en el objeto son únicos.
- <code>.is_monotonic_increasing</code>: Devuelve un booleano si los valores en el objeto están aumentando monótonamente.
- <code>.is_monotonic_decreasing</code>: Devuelve un booleano si los valores en el objeto están disminuyendo monótonamente.
- <code>.value_counts[normalize, sort, ...]</code> Devuelve una Serie que contiene recuentos de valores únicos.

### Reindexing / selection / label manipulation

- <code>**.alignother[, join, axis, level, ...]</code>** Alinea dos objetos en sus ejes con el método de unión especificado.
- **<code>.case_whencaselist</code>** Reemplaza valores donde las condiciones son Verdaderas.
- **<code>.drop[labels, axis, index, columns, ...]</code>** Devuelve la Serie con etiquetas de índice especificadas eliminadas.
- **<code>.droplevellevel[, axis]</code>** Devuelve la Serie/DataFrame con el nivel de índice/columna solicitado eliminado.
- <code>.drop_duplicates*[, keep, inplace, ...]</code> Devuelve la Serie con valores duplicados eliminados.
- <code>.duplicated[keep]</code> Indica valores duplicados en la Serie.
- <code>.equalsother</code> Prueba si dos objetos contienen los mismos elementos.
- <code>.firstoffset</code> (OBSOLETO) Selecciona los períodos iniciales de datos de series temporales basados en un desplazamiento de fecha.
- <code>.head[n]</code> Devuelve las primeras n filas.
- <code>.idxmax[axis, skipna]</code> Devuelve la etiqueta de fila del valor máximo.
- <code>.idxmin[axis, skipna]</code> Devuelve la etiqueta de fila del valor mínimo.
- <code>.isinvalues</code> Si los elementos en la Serie están contenidos en values.
- <code>.lastoffset</code> (OBSOLETO) Selecciona los períodos finales de datos de series temporales basados en un desplazamiento de fecha.
- <code>.reindex[index, axis, method, copy, ...]</code> Conforma la Serie a un nuevo índice con lógica de relleno opcional.
- <code>.reindex_likeother[, method, copy, ...]</code> Devuelve un objeto con índices coincidentes como otro objeto.
- <code>.rename[index, axis, copy, inplace, ...]</code> Altera las etiquetas de índice o el nombre de la Serie.
- <code>.rename_axis[mapper, index, axis, ...]</code> Establece el nombre del eje para el índice o las columnas.
- <code>.reset_index[level, drop, name, ...]</code> Genera un nuevo DataFrame o Serie con el índice restablecido.
- <code>.sample[n, frac, replace, weights, ...]</code> Devuelve una muestra aleatoria de elementos de un eje del objeto.
- <code>.set_axislabels, *[, axis, copy]</code> Asigna el índice deseado al eje dado.
- <code>.takeindices[, axis]</code> Devuelve los elementos en los índices posicionales dados a lo largo de un eje.
- <code>.tail[n]</code> Devuelve las últimas n filas.
- <code>.truncate[before, after, axis, copy]</code> Trunca una Serie o DataFrame antes y después de cierto valor de índice.
- <code>.wherecond[, other, inplace, axis, level]</code> Reemplaza valores donde la condición es Falsa.
- <code>.maskcond[, other, inplace, axis, level]</code> Reemplaza valores donde la condición es Verdadera.
- <code>.add_prefixprefix[, axis]</code> Prefija las etiquetas con un prefijo de cadena.
- <code>.add_suffixsuffix[, axis]</code> Sufija las etiquetas con un sufijo de cadena.
- <code>.filter[items, like, regex, axis]</code> Subconjunto de filas o columnas del dataframe según las etiquetas de índice especificadas.

### Manejo de Datos Faltantes

- <code>.backfill*[, axis, inplace, limit, ...]</code> (OBSOLETO) Rellena valores NA/NaN utilizando la siguiente observación válida para llenar el hueco.
- <code>.bfill*[, axis, inplace, limit, ...]</code> Rellena valores NA/NaN utilizando la siguiente observación válida para llenar el hueco.
- <code>.dropna*[, axis, inplace, how, ...]</code> Devuelve una nueva Serie con valores faltantes eliminados.
- <code>.ffill*[, axis, inplace, limit, ...]</code> Rellena valores NA/NaN propagando la última observación válida al siguiente válido.
- <code>.fillna[value, method, axis, ...]</code> Rellena valores NA/NaN utilizando el método especificado.
- <code>.interpolate[method, axis, limit, ...]</code> Rellena valores NaN utilizando un método de interpolación.
- <code>.isna</code> Detecta valores faltantes.
- <code>.isnull</code> Series.isnull es un alias para Series.isna.
- <code>.notna</code> Detecta valores existentes (no faltantes).
- <code>.notnull</code> Series.notnull es un alias para Series.notna.
- <code>.pad*[, axis, inplace, limit, downcast]</code> (OBSOLETO) Rellena valores NA/NaN propagando la última observación válida al siguiente válido.
- <code>.replace[to_replace, value, inplace, ...]</code> Reemplaza valores dados en to_replace con valor.

### Remodelado y Ordenación

- <code>.argsort[axis, kind, order]</code> Devuelve los índices enteros que ordenarían los valores de la Serie.
- <code>.argmin[axis, skipna]</code> Devuelve la posición entera del valor más pequeño en la Serie.
- <code>.argmax[axis, skipna]</code> Devuelve la posición entera del valor más grande en la Serie.
- <code>.reorder_levelsorder</code> Reorganiza los niveles de índice usando el orden de entrada.
- <code>.sort_values*[, axis, ascending, ...]</code> Ordena por los valores.
- <code>.sort_index*[, axis, level, ...]</code> Ordena la Serie por etiquetas de índice.
- <code>.swaplevel[i, j, copy]</code> Intercambia los niveles i y j en un MultiIndex.
- <code>.unstack[level, fill_value, sort]</code> Desapila, también conocido como pivotar, la Serie con MultiIndex para producir un DataFrame.
- <code>.explode[ignore_index]</code> Transforma cada elemento de tipo lista en una fila.
- <code>.searchsortedvalue[, side, sorter]</code> Encuentra índices donde los elementos deben ser insertados para mantener el orden.
- <code>.ravel[order]</code> (OBSOLETO) Devuelve los datos subyacentes aplanados como un ndarray o ExtensionArray.
- <code>.repeatrepeats[, axis]</code> Repite elementos de una Serie.
- <code>.squeeze[axis]</code> Convierte objetos de eje de 1 dimensión en escalares.
- <code>.view[dtype]</code> (OBSOLETO) Crea una nueva vista de la Serie.

### Combinación / Comparación / Unión / Fusión

- <code>.compareother[, align_axis, ...]</code> Compara con otra Serie y muestra las diferencias.
- <code>.updateother</code> Modifica la Serie en el lugar utilizando valores de la Serie pasada.

### Relacionado con Series Temporales

- <code>.asfreqfreq[, method, how, ...]</code> Convierte series temporales a la frecuencia especificada.
- <code>.asofwhere[, subset]</code> Devuelve la(s) última(s) fila(s) sin ningún NaN antes de where.
- <code>.shift[periods, freq, axis, ...]</code> Desplaza el índice por el número deseado de períodos con una frecuencia de tiempo opcional.
- <code>.first_valid_index</code> Devuelve el índice para el primer valor no NA o None, si no se encuentra ningún valor no NA.
- <code>.last_valid_index</code> Devuelve el índice para el último valor no NA o None, si no se encuentra ningún valor no NA.
- <code>.resamplerule[, axis, closed, label, ...]</code> Re-muestrea datos de series temporales.
- <code>.tz_converttz[, axis, level, copy]</code> Convierte el eje consciente de la zona horaria a la zona horaria objetivo.
- <code>.tz_localizetz[, axis, level, copy, ...]</code> Localiza el índice ingenuo de la zona horaria de una Serie o DataFrame a la zona horaria objetivo.
- <code>.at_timetime[, asof, axis]</code> Selecciona valores en un momento específico del día (por ejemplo, 9:30 AM).
- <code>.between_timestart_time, end_time[, ...]</code> Selecciona valores entre tiempos específicos del día (por ejemplo, 9:00-9:30 AM).

### Accesores

Los "accesores", que son propiedades de los objetos `DataFrame` y `Series` que exponen métodos especializados para tipos de datos específicos. Los accesores en pandas facilitan el manejo de ciertos tipos de datos sin necesidad de aplicar funciones externas o realizar conversiones de tipo manualmente.

- <code>.str</code> alias de StringMethods
- <code>.cat</code> alias de CategoricalAccessor
- <code>.dt</code> alias de CombinedDatetimelikeProperties
- <code>.sparse</code> alias de SparseAccessor
<code>DataFrame.sparse</code> alias de SparseFrameAccessor
<code>Index.str</code> alias de StringMethods

### Propiedades de Fechas y Horas

- <code>.dt.date</code>: Devuelve un array de numpy de objetos python datetime.date.
- <code>.dt.time</code>: Devuelve un array de numpy de objetos datetime.time.
- <code>.dt.timetz</code>: Devuelve un array de numpy de objetos datetime.time con zonas horarias.
- <code>.dt.year</code>: El año del datetime.
- <code>.dt.month</code>: El mes como enero=1, diciembre=12.
- <code>.dt.day</code>: El día del datetime.
- <code>.dt.hour</code>: Las horas del datetime.
- <code>.dt.minute</code>: Los minutos del datetime.
- <code>.dt.second</code>: Los segundos del datetime.
- <code>.dt.microsecond</code>: Los microsegundos del datetime.
- <code>.dt.nanosecond</code>: Los nanosegundos del datetime.
- <code>.dt.dayofweek</code>: El día de la semana con lunes=0, domingo=6.
- <code>.dt.day_of_week</code>: El día de la semana con lunes=0, domingo=6.
- <code>.dt.weekday</code>: El día de la semana con lunes=0, domingo=6.
- <code>.dt.dayofyear</code>: El día ordinal del año.
- <code>.dt.day_of_year</code>: El día ordinal del año.
- <code>.dt.days_in_month</code>: El número de días en el mes.
- <code>.dt.quarter</code>: El trimestre de la fecha.
- <code>.dt.is_month_start</code>: Indica si la fecha es el primer día del mes.
- <code>.dt.is_month_end</code>: Indica si la fecha es el último día del mes.
- <code>.dt.is_quarter_start</code>: Indicador de si la fecha es el primer día de un trimestre.
- <code>.dt.is_quarter_end</code>: Indicador de si la fecha es el último día de un trimestre.
- <code>.dt.is_year_start</code>: Indica si la fecha es el primer día de un año.
- <code>.dt.is_year_end</code>: Indica si la fecha es el último día de un año.
- <code>.dt.is_leap_year</code>: Indicador booleano si la fecha pertenece a un año bisiesto.
- <code>.dt.daysinmonth</code>: El número de días en el mes.
- <code>.dt.days_in_month</code>: El número de días en el mes.
- <code>.dt.tz</code>: Devuelve la zona horaria.
- <code>.dt.freq</code>: Devuelve el objeto de frecuencia para este PeriodArray.
- <code>.dt.unit</code>:
- <code>.dt.normalize*args, kwargs</code> Convierte las horas a medianoche.

### Métodos de Fecha y Hora

- <code>.dt.isocalendar</code> Calcula el año, la semana y el día según el estándar ISO 8601.
- <code>.dt.to_period*args, kwargs</code> Convierte a PeriodArray/PeriodIndex en una frecuencia particular.
- <code>.dt.to_pydatetime</code> (OBSOLETO) Devuelve los datos como un array de objetos datetime.datetime.
- <code>.dt.tz_localize*args, kwargs</code> Localiza un Array/Index de Datetime de la zona horaria a un Array/Index de Datetime consciente de la zona horaria.
- <code>.dt.tz_convert*args, kwargs</code> Convierte un Array/Index de Datetime consciente de la zona horaria de una zona horaria a otra.
- <code>.dt.normalize*args, kwargs</code> Convierte las horas a medianoche.
- <code>.dt.strftime*args, kwargs</code> Convierte a Index utilizando el formato de fecha especificado.
- <code>.dt.round*args, kwargs</code> Realiza una operación de redondeo en los datos a la frecuencia especificada.
- <code>.dt.floor*args, kwargs</code> Realiza una operación de piso en los datos a la frecuencia especificada.
- <code>.dt.ceil*args, kwargs</code> Realiza una operación de techo en los datos a la frecuencia especificada.
- <code>.dt.month_name*args, kwargs</code> Devuelve los nombres de los meses con el locale especificado.
- <code>.dt.day_name*args, kwargs</code> Devuelve los nombres de los días con el locale especificado.
- <code>.dt.as_unit*args, kwargs</code>

### Propiedades del Período

- <code>.dt.qyear</code>:
- <code>.dt.start_time</code>: Obtiene el Timestamp para el inicio del período.
- <code>.dt.end_time</code>: Obtiene el Timestamp para el final del período.

### Propiedades de Timedelta

- <code>.dt.days</code>: Número de días para cada elemento.
- <code>.dt.seconds</code>: Número de segundos (>= 0 y menos de 1 día) para cada elemento.
- <code>.dt.microseconds</code>: Número de microsegundos (>= 0 y menos de 1 segundo) para cada elemento.
- <code>.dt.nanoseconds</code>: Número de nanosegundos (>= 0 y menos de 1 microsegundo) para cada elemento.
- <code>.dt.components</code>: Devuelve un DataFrame de los componentes de los Timedeltas.
- <code>.dt.unit</code>:

### Métodos de Timedelta

- <code>.dt.to_pytimedelta()</code>: Devuelve un array de objetos nativos datetime.timedelta.
- <code>.dt.total_seconds*args, kwargs</code> Devuelve la duración total de cada elemento expresada en segundos.
- <code>.dt.as_unit*args, kwargs</code>

### Manejo de Cadenas

- <code>.str.capitalize()</code>: Convierte las cadenas en la Serie/Índice a mayúsculas.
- <code>.str.casefold()</code>: Convierte las cadenas en la Serie/Índice a minúsculas flexibles.
- <code>.str.cat[others, sep, na_rep, join]</code> Concatena cadenas en la Serie/Índice con un separador dado.
- <code>.str.centerwidth[, fillchar]</code> Rellena los lados izquierdo y derecho de las cadenas en la Serie/Índice.
- <code>.str.contains(path[, case, flags, na, ...])</code> Prueba si un patrón o regex está contenido dentro de una cadena de la Serie o Índice.
- <code>.str.countpat[, flags]</code> Cuenta las ocurrencias de un patrón en cada cadena de la Serie/Índice.
- <code>.str.decodeencoding[, errors]</code> Decodifica la cadena de caracteres en la Serie/Índice usando la codificación indicada.
- <code>.str.encodeencoding[, errors]</code> Codifica la cadena de caracteres en la Serie/Índice usando la codificación indicada.
- <code>.str.endswith([, na])</code> Prueba si el final de cada elemento de la cadena coincide con un patrón.
- <code>.str.extractpat[, flags, expand]</code> Extrae grupos de captura en el regex pat como columnas en un DataFrame.
- <code>.str.extractallpat[, flags]</code> Extrae grupos de captura en el regex pat como columnas en DataFrame.
- <code>.str.findsub[, start, end]</code> Devuelve los índices más bajos en cada cadena en la Serie/Índice.
- <code>.str.findallpat[, flags]</code> Encuentra todas las ocurrencias de un patrón o expresión regular en la Serie/Índice.
- <code>.str.fullmatchpat[, case, flags, na]</code> Determina si cada cadena coincide completamente con una expresión regular.
- <code>.str.geti</code> Extrae el elemento de cada componente en la posición especificada o con la clave especificada.
- <code>.str.indexsub([, start, end])</code> Devuelve los índices más bajos en cada cadena en la Serie/Índice.
- <code>.str.joinsep</code> Une listas contenidas como elementos en la Serie/Índice con el delimitador pasado.
- <code>.str.len</code> Calcula la longitud de cada elemento en la Serie/Índice.
- <code>.str.ljustwidth[, fillchar]</code> Rellena el lado derecho de las cadenas en la Serie/Índice.
- <code>.str.lower</code> Convierte las cadenas en la Serie/Índice a minúsculas.
- <code>.str.lstrip[to_strip]</code> Elimina los caracteres iniciales.
- <code>.str.matchpat[, case, flags, na]</code> Determina si cada cadena comienza con una coincidencia de una expresión regular.
- <code>.str.normalizeform</code> Devuelve la forma normal Unicode para las cadenas en la Serie/Índice.
- <code>.str.padwidth[, side, fillchar]</code> Rellena las cadenas en la Serie/Índice hasta el ancho.
- <code>.str.partition[sep, expand]</code> Divide la cadena en la primera ocurrencia de sep.
- <code>.str.removeprefixprefix</code> Elimina un prefijo de una serie de objetos.
- <code>.str.removesuffixsuffix</code> Elimina un sufijo de una serie de objetos.
- <code>.str.repeatrepeats</code> Duplica cada cadena en la Serie o Índice.
- <code>.str.replacepat, repl[, n, case, ...]</code> Reemplaza cada ocurrencia de patrón/regex en la Serie/Índice.
- <code>.str.rfindsub[, start, end]</code> Devuelve los índices más altos en cada cadena en la Serie/Índice.
- <code>.str.rindexsub[, start, end]</code> Devuelve los índices más altos en cada cadena en la Serie/Índice.
- <code>.str.rjustwidth[, fillchar]</code> Rellena el lado izquierdo de las cadenas en la Serie/Índice.
- <code>.str.rpartition[sep, expand]</code> Divide la cadena en la última ocurrencia de sep.
- <code>.str.rstrip[to_strip]</code> Elimina los caracteres finales.
- <code>.str.slice[start, stop, step]</code> Corta subcadenas de cada elemento en la Serie o Índice.
- <code>.str.slice_replace[start, stop, repl]</code> Reemplaza una porción posicional de una cadena con otro valor.
- <code>.str.split[pat, n, expand, regex]</code> Divide las cadenas alrededor del separador/delimitador dado.
- <code>.str.rsplit[pat, n, expand]</code> Divide las cadenas alrededor del separador/delimitador dado.
- <code>.str.startswithpat[, na]</code> Prueba si el inicio de cada elemento de la cadena coincide con un patrón.
- <code>.str.strip[to_strip]</code> Elimina los caracteres iniciales y finales.
- <code>.str.swapcase</code> Convierte las cadenas en la Serie/Índice a mayúsculas y minúsculas intercambiadas.
- <code>.str.title</code> Convierte las cadenas en la Serie/Índice a formato de título.
- <code>.str.translatetable</code> Mapea todos los caracteres en la cadena a través de la tabla de mapeo dada.
- <code>.str.upper</code> Convierte las cadenas en la Serie/Índice a mayúsculas.
- <code>.str.wrapwidth, kwargs</code> Envuelve las cadenas en la Serie/Índice en el ancho de línea especificado.
- <code>.str.zfillwidth</code> Rellena las cadenas en la Serie/Índice anteponiendo caracteres '0'.
- <code>.str.isalnum</code> Verifica si todos los caracteres en cada cadena son alfanuméricos.
- <code>.str.isalpha</code> Verifica si todos los caracteres en cada cadena son alfabéticos.
- <code>.str.isdigit</code> Verifica si todos los caracteres en cada cadena son dígitos.
- <code>.str.isspace</code> Verifica si todos los caracteres en cada cadena son espacios en blanco.
- <code>.str.islower</code> Verifica si todos los caracteres en cada cadena son minúsculas.
- <code>.str.isupper</code> Verifica si todos los caracteres en cada cadena son mayúsculas.
- <code>.str.istitle</code> Verifica si todos los caracteres en cada cadena están en formato de título.
- <code>.str.isnumeric</code> Verifica si todos los caracteres en cada cadena son numéricos.
- <code>.str.isdecimal</code> Verifica si todos los caracteres en cada cadena son decimales.
- <code>.str.get_dummies[sep]</code> Devuelve un DataFrame de variables dummy/indicadoras para la Serie.

### Accesor Categórico

- <code>.cat.categories</code>: Las categorías de este categórico.
- <code>.cat.ordered</code>: Si las categorías tienen una relación ordenada.
- <code>.cat.codes</code>: Devuelve una Serie de códigos así como el índice.
- <code>.cat.rename_categories*args, kwargs</code> Renombra categorías.
- <code>.cat.reorder_categories*args, kwargs</code> Reordena las categorías según lo especificado en new_categories.
- <code>.cat.add_categories*args, kwargs</code> Añade nuevas categorías.
- <code>.cat.remove_categories*args, kwargs</code> Elimina las categorías especificadas.
- <code>.cat.remove_unused_categories*args, ...</code> Elimina categorías que no se usan.
- <code>.cat.set_categories*args, kwargs</code> Establece las categorías a las nuevas categorías especificadas.
- <code>.cat.as_ordered*args, kwargs</code> Establece el Categórico como ordenado.
- <code>.cat.as_unordered*args, kwargs</code> Establece el Categórico como no ordenado.

### Accesor Sparse

- <code>.sparse.npoints</code>: El número de puntos no fill_value.
- <code>.sparse.density</code>: El porcentaje de puntos no fill_value, como decimal.
- <code>.sparse.fill_value</code>: Los elementos en los datos que son fill_value no se almacenan.
- <code>.sparse.sp_values</code>: Un ndarray que contiene los valores no fill_value.
- <code>.sparse.from_cooA[, dense_index]</code> Crea una Serie con valores dispersos a partir de una scipy.sparse.coo_matrix.
- <code>.sparse.to_coo[row_levels, ...]</code> Crea una scipy.sparse.coo_matrix a partir de una Serie con MultiIndex.

### Accesor de Lista

- <code>.list.flatten</code> Aplana los valores de la lista.
- <code>.list.len</code> Devuelve la longitud de cada lista en la Serie.
- <code>.list.getitemkey</code> Indiza o corta listas en la Serie.

### Accesor de Estructura

- <code>.struct.dtypes</code>: Devuelve el objeto dtype de cada campo hijo de la estructura.
- <code>.struct.fieldname_or_index</code> Extrae un campo hijo de una estructura como una Serie.
- <code>.struct.explode</code> Extrae todos los campos hijos de una estructura como un DataFrame.

### Banderas

- <code>Flagsobj, *, allows_duplicate_labels</code> Banderas que se aplican a los objetos de pandas.

### Metadatos

- <code>.attrs</code>: Es un diccionario para almacenar metadatos globales para esta Serie.
<code>Advertencia</code>: Series.attrs se considera experimental y puede cambiar sin previo aviso.
- <code>.attrs</code>: Diccionario de atributos globales de este conjunto de datos.

### Gráficos

- <code>.plot[kind, ax, figsize, ....]</code> Accesor y método de trazado de Series.
- <code>.plot.area[x, y, stacked]</code> Dibuja un gráfico de área apilada.
- <code>.plot.bar[x, y]</code> Gráfico de barras vertical.
- <code>.plot.barh[x, y]</code> Hace un gráfico de barras horizontal.
- <code>.plot.box[by]</code> Hace un gráfico de caja de las columnas del DataFrame.
- <code>.plot.density[bw_method, ind]</code> Genera un gráfico de Estimación de Densidad Kernel utilizando núcleos gaussianos.
- <code>.plot.hist[by, bins]</code> Dibuja un histograma de las columnas del DataFrame.
- <code>.plot.kde[bw_method, ind]</code> Genera un gráfico de Estimación de Densidad Kernel utilizando núcleos gaussianos.
- <code>.plot.line[x, y]</code> Trazar Series o DataFrame como líneas.
- <code>.plot.piekwargs</code> Genera un gráfico circular.
- <code>.hist[by, ax, grid, xlabelsize, ...]</code> Dibuja un histograma de la serie de entrada utilizando matplotlib.

### Serialización / Entrada-Salida / Conversión

- <code>.to_picklepath, *[, compression, ...]</code> Serializa (pickle) el objeto a archivo.
- <code>.to_csv[path_or_buf, sep, na_rep, ...]</code> Escribe el objeto a un archivo de valores separados por comas (csv).
- <code>.to_dict*[, into]</code> Convierte Series a un diccionario {etiqueta -> valor} o un objeto similar a un diccionario.
- <code>.to_excelexcel_writer, *[, ...]</code> Escribe el objeto en una hoja de Excel.
- <code>.to_frame[name]</code> Convierte Series a DataFrame.
- <code>.to_xarray</code> Devuelve un objeto xarray del objeto pandas.
- <code>.to_hdfpath_or_buf, *, key[, mode, ...]</code> Escribe los datos contenidos en un archivo HDF5 utilizando HDFStore.
- <code>.to_sqlname, con, *[, schema, ...]</code> Escribe registros almacenados en un DataFrame en una base de datos SQL.
- <code>.to_json[path_or_buf, orient, ...]</code> Convierte el objeto en una cadena JSON.
- <code>.to_string[buf, na_rep, ...]</code> Renderiza una representación de cadena de la Serie.
- <code>.to_clipboard*[, excel, sep]</code> Copia el objeto al portapapeles del sistema.
- <code>.to_latex[buf, columns, header, ...]</code> Renderiza el objeto en una tabla LaTeX, longtable o tabla anidada.
- <code>.to_markdown[buf, mode, index, ...]</code> Imprime la Serie en un formato amigable para Markdown.


```python

```
