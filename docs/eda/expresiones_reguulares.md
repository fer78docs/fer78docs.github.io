---
layout: default
title: Regular Expressions
nav_order: 8
parent: Exploratory Data Analysis
---


Referencia:

**Clases de Caracteres**

- `[ABC]`: Conjunto de caracteres
- `[^ABC]`: Combina cualquier personaje que no esté en el conjunto.
- `[A-Z]`: Coincide con un carácter incluido entre caracteres especificados (inclusive).
- `.`: Coincide con cualquier carácter excepto los saltos de línea. Equivalente a `[^\n\r]`.
- `\w`: Coincide con carácter de palabra (alfanumérico y guión bajo). Equivalente a `[A-Za-z0-9_]`.
- `\W`: Coincide con carácter que no sea de palabra (alfanumérico y guión bajo). Equivalente a `[^A-Za-z0-9_]`.
- `\d`: Coincide con cualquier carácter de dígito (0-9). Equivalente a `[0-9]`.
- `\D`: Coincide con cualquier carácter que no sea un dígito (0-9). Equivalente a `[^0-9]`.
- `\s`: Coincide con cualquier carácter de espacio en blanco (espacios, tabulaciones, saltos de línea).
- `\S`: Coincide con cualquier carácter que no sea un espacio en blanco (espacios, tabulaciones, saltos de línea).
- `\p{L}`: Coincide con un carácter en la categoría Unicode especificada. Por ejemplo, \p{Ll} coincidirá con cualquier letra minúscula. Para obtener una lista de valores, consulte esta página de MDN. `\P{L}` lo niega. `\p{Han}` se utiliza para secuencias Unicode. 

**Anclas**

- `^`: Coincide con el comienzo de la cadena o con el comienzo de una línea si el indicador multilínea (m) está habilitado. Esto coincide con una posición, no con un caracter.
- `$`: Coincide con el final de la cadena o con el final de una línea si el indicador multilínea (m) está habilitado. Esto coincide con una posición, no con un caracter.
- `\b`: Coincide con una posición de límite de palabra (fin de cadena). 

**Grupos de Captura**

- `(ABC)`: Agrupa varios tokens y crea un grupo de captura para extraer una subcadena o utilizar una referencia inversa.
- `(?<nombre>ABC)`: Crea un grupo de captura al que se puede hacer referencia mediante el nombre especificado.
- `\1` : Coincide con los resultados de un grupo de captura. Por ejemplo, \1 coincide con los resultados del primer grupo de captura y \3 coincide con el tercero.
- `(?:ABC)`: Agrupa varios tokens sin crear un grupo de captura.


**Lookaround**

- `(?=ABC)`: Coincide con un grupo después de la expresión principal sin incluirlo en el resultado.
- `(?!ABC)`: Especifica un grupo que no puede coincidir después de la expresión principal (si coincide, el resultado se descarta).
- `(?<=ABC)`: Coincide con un grupo antes de la expresión principal sin incluirlo en el resultado.
- `(?<!=ABC)`: Especifica un grupo que no puede coincidir antes de la expresión principal (si coincide, el resultado se descarta).


**Cuantificadores y Alternancia**

- `+`: Coincide con 1 o más de los tokens anteriores.
- `*`: Coincide con 0 o más del token anterior.
- `{1,3}`: Coincide con la cantidad especificada del token anterior. {1,3}coincidirá con 1 y 3. {3}coincidirá exactamente con 3. {3,}coincidirá con 3 o más.
- `?`: Coincide con 0 o 1 del token anterior, lo que lo convierte efectivamente en opcional.
- `?`: Hace que el cuantificador anterior sea vago, lo que hace que coincida con la menor cantidad de caracteres posible. De forma predeterminada, los cuantificadores son codiciosos y coincidirán con tantos caracteres como sea posible.
- `|`: Actúa como un OR booleano. Coincide con la expresión antes o después de \|.


**Sustitucion**

- `$&`: Inserta el texto coincidente.
- `$1`: Inserta los resultados del grupo de captura especificado. Por ejemplo, $3 insertaría el tercer grupo de captura.
- `$\``: Inserta la parte de la cadena de origen que precede a la coincidencia.
- `$'`: Inserta la parte de la cadena de origen que sigue a la coincidencia.
- `$$`: Escapa: Inserta un carácter de signo de dólar ($).
- `\n`: Para mayor comodidad, estos caracteres de escape se admiten en la cadena Reemplazar en RegExr: `\n`, `\r`, `\t`, `\\y` escapes Unicode `\uFFFF`. Esto puede variar en su entorno de implementación.


**Banderas**

- `i`: Los indicadores de expresión cambian la forma en que se interpreta la expresión. Las banderas siguen a la barra diagonal de cierre de la expresión (ej. /.+/igm).
- `g`: Conserva el índice de la última coincidencia, permitiendo que las búsquedas posteriores comiencen desde el final de la coincidencia anterior.
- `m`: Cuando el indicador multilínea está habilitado, los anclajes iniciales y finales `( ^y $)` coincidirán con el inicio y el final de una línea, en lugar del inicio y el final de toda la cadena. Tenga en cuenta que patrones como `/^[\s\S]+$/m` pueden devolver coincidencias que abarquen varias líneas porque los anclajes coincidirán con el inicio/final de cualquier línea.
- `u`: Cuando la bandera Unicode está habilitada, puede usar escapes Unicode extendidos en el formulario `\x{FFFFF}`. También hace que otros escapes sean más estrictos, lo que provoca que los escapes no reconocidos (por ejemplo, \j) arrojen un error.
- `y`: La expresión solo coincidirá desde su posición lastIndex e ignora el gindicador global ( ) si está configurado. Debido a que cada búsqueda en RegExr es discreta, este indicador no tiene más impacto en los resultados mostrados.
- `s`: El punto ( .) coincidirá con cualquier carácter, incluida la nueva línea.


En el siguiente sitio puede consultar, crear y practicar expresiones regulares:

[Regex](https://regexr.com/)