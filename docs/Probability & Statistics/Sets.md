---
layout: default
title: Sets
nav_order: 1
parent: Probability & Statistics
---

# Conjuntos (sets)

- [Definicion y creacion](#definicion)
- [Cardinalidad de un conjunto](#cardi)


La probabilidad hace un uso extensivo de operaciones de conjuntos. Por eso es importante introducir la notación y la terminología relevantes desde el principio. Entonces, comencemos por definir un conjunto. Hay muchas definiciones, con diferentes palabras y todas reflejan el mismo tipo de significado. La definición que he escrito aquí es de Nach Rosen quien trabajó en los laboratorios Bell y escribió libros sobre matemáticas. 

Uno de sus libros mas famoso, es *Matemáticas Discretas*. Definió el conjunto como: **una colección desordenada de objetos distintos**. En Python se define **como una colección no ordenada de elementos únicos e inmutables.**

Un conjunto es básicamente una colección, tiene muchos objetos dentro y eso es una colección, pero la colección tiene cierto tipo de propiedades. 

- **Desordenados**: Los elementos en un set no tienen un orden específico.
- **Elementos Únicos**: Cada elemento en un set debe ser único; no se permiten duplicados.
- **Inmutables**: Los elementos de un set deben ser de tipo inmutable, como números, cadenas y tuplas. No puedes incluir listas o diccionarios como elementos de un set debido a su mutabilidad.
- **Iterables**: Los sets en Python son iterables, lo que significa que puedes recorrer sus elementos utilizando un bucle for.
- Almacena cualquier tipo de objeto

Analicemos ahora qué es el objeto y cuáles son las propiedades de los objetos que deberían permanecer en la colección. Bueno, estos son cualquier objeto, puede ser un número, puede ser un libro, puede ser un curso completo, puede ser un sistema informático y sus accesorios. 

Para definir un conjunto, puedes usar llaves `{}` con elementos separados por comas dentro de ellas, o bien, puedes usar la función `set()` para crear un conjunto, opcionalmente pasando un iterable (como una lista o tupla) desde el cual se crearán los elementos del conjunto. Aquí tienes ejemplos de ambas maneras:
{: #definicion}
```python
# Crear un conjunto con llaves
mi_conjunto = {1, 2, 3, 4}
print(mi_conjunto)  # Salida: {1, 2, 3, 4}

# Crear un conjunto vacío (debes usar set(), no {})
conjunto_vacio = set()
print(conjunto_vacio)  # Salida: set()

# Crear un conjunto a partir de una lista
mi_conjunto = set([1, 2, 3, 4])
print(mi_conjunto)  # Salida: {1, 2, 3, 4}

# También puedes pasar una tupla o incluso una cadena de texto
mi_conjunto_desde_tupla = set((5, 6, 7))
print(mi_conjunto_desde_tupla)  # Salida: {5, 6, 7}

mi_conjunto_desde_cadena = set("hola")
print(mi_conjunto_desde_cadena)  # Salida: {'h', 'o', 'a', 'l'}
```
Además, los conjuntos automáticamente eliminarán los duplicados de los elementos proporcionados:
```python
# Los duplicados se eliminarán automáticamente
mi_conjunto_con_duplicados = {1, 2, 2, 3, 4, 4, 4}
print(mi_conjunto_con_duplicados)  # Salida: {1, 2, 3, 4}
```

## Cardinalidad de un conjunto
{: #cardi}

En cardinalidad, hablamos de un elemento de un conjunto o, a veces, de un miembro de un conjunto. Definamos algún conjunto de numeros como ejemplo. Aunque pueden ser cualquier tipo de objeto como ya lo definimos. 
```python
A = {1, 2, 5, 7}
```
Cada numero seria un elemento diferente en el conjunto. Puedes llamarlo elemento, o miembro. El símbolo griego `∈` se usa para denotar la relación de membresía a un conjunto. Se puede expresar que 1 es elemento de A de esta manera `1 ∈ A`. De forma contraria ∉ expresa que el elemento no pertenece al conjunto: `4 ∉ A`

**La cardinalidad de un conjunto se refiere al número de elementos que contiene el conjunto**. En matemáticas y teoría de conjuntos, la cardinalidad puede ser **finita** o **infinita**. Un conjunto con una cantidad limitada de elementos tiene una cardinalidad finita, mientras que un conjunto que contiene una cantidad infinita de elementos tiene una cardinalidad infinita.

Cardinalidad Finita
La cardinalidad de un conjunto finito se denota como 
∣
�
∣
∣A∣, donde 
�
A es el conjunto. Por ejemplo, si tenemos un conjunto 
�
=
{
2
,
4
,
6
,
8
}
A={2,4,6,8}, la cardinalidad de 
�
A es 4, porque hay cuatro elementos en el conjunto. Se escribe como 
∣
�
∣
=
4
∣A∣=4.

Cardinalidad Infinita
Los conjuntos infinitos pueden ser contablemente infinitos o incontablemente infinitos. Un conjunto es contablemente infinito si sus elementos pueden ser contados uno por uno y asignados a los números naturales, como el conjunto de todos los números enteros. Un conjunto es incontablemente infinito si su tamaño es mayor que el conjunto de todos los números naturales, como el conjunto de todos los números reales entre 0 y 1.

Cardinalidad en Python
En Python, la cardinalidad de un conjunto se puede obtener utilizando la función len(). Por ejemplo:

python
Copy code
mi_conjunto = {2, 4, 6, 8}
print(len(mi_conjunto))
Esto imprimirá 4, que es la cantidad de elementos en mi_conjunto.




solo quiero mencionar aquí que, aunque estos son los conjuntos finitos con los que trabajaremos principalmente en ciencia de datos, estos Los conjuntos finitos son en su mayoría muestras de una población más grande, que en sí misma es un conjunto infinito. Y a veces necesitamos inferir las propiedades de aquellas poblaciones que son básicamente, que se representan como conjuntos infinitos usando estos conjuntos finitos. Entonces es importante tener en cuenta ¿qué queremos decir con conjunto infinito? Es un conjunto con un número total de elementos que la cardinalidad del conjunto ya no es finita. También existen otras categorías de conjuntos finitos e infinitos. Uh, es posible que tengas un conjunto responsable. Por ejemplo, un conjunto responsable es un conjunto que es finito. Es un conjunto finito, contiene todos los , es decir, todos los objetos del conjunto. La cardinalidad del conjunto es finita, o es un conjunto finito o puede ser un conjunto infinito. Puede ser un conjunto infinito. Pero los elementos del conjunto se pueden ordenar, ordenar, enumerar. Entonces podemos decir que son objetos enumerables, enumerables, uh, enumerables. Puede definir un listado en particular o un anillo o arreglo. Matemáticamente, se llama secuencia. Puedes, puedes generar una secuencia de los elementos. Permítanme darles un ejemplo de lo que queremos decir con conjunto contable incluso si es un conjunto infinito, la forma muy, muy, quiero decir, casual de, quiero decir, recordar el conjunto contable, incluso si tiene infinitos elementos es el ¿De qué manera puedes idear una estrategia para contar el siguiente elemento? ¿ Si te dan un elemento en particular? ¿Se te ocurre una estrategia? Si puede idear una estrategia para indicar siempre el siguiente elemento dado el elemento actual, entonces los elementos del conjunto son responsables. Por ejemplo, digamos que tenemos un conjunto, un conjunto de todos los números enteros positivos, digamos cuatro o cinco. Ese conjunto es obviamente un conjunto infinito porque no hay un límite superior. El conjunto sigue y sigue y sigue. Uh hay uh quiero decir que el número de elementos en el conjunto ya no es finito, pero este conjunto, aunque tiene infinitos elementos, es contable.porque la definición de responsabilidad es que los objetos son enumerables. Y normalmente recuerdo esta responsabilidad o, o suelo enseñar a los estudiantes la responsabilidad a recordar, recordar la responsabilidad como si pudiera idear una estrategia. ¿Se te ocurre una estrategia? ¿Puedes construir una estrategia que cada vez que te dé un elemento del conjunto, puedas decirme el siguiente elemento? ¿Puedes ordenar los elementos? Entonces, por ejemplo, si te doy cuatro, ¿puedes decirme cuál es el siguiente entero positivo? Sí, puedes decir que son cinco. Y la estrategia es que si te doy X, representarás simplemente X más uno. Y eso es lo que, si les doy algún número. Por ejemplo, de este conjunto, ¿puedes decirme el siguiente elemento? Um Por ejemplo, si te doy 2 55 +61, ¿cuál es el siguiente elemento? Dirás, OK, +225562. Si eso es cierto, si puedes idear una estrategia de ordenamiento en la que siempre sea posible enumerar los objetos en una secuencia para ordenar los objetos en una secuencia, entonces ese conjunto se llama contable. Por otro lado, por ejemplo, si el conjunto es un conjunto de números reales, digamos 1.001 o quiero decir, el conjunto es el conjunto que contiene todos los números reales posibles en el mundo, todos los números reales con todos los decimales y cosas como Entonces, ¿ y si te pregunto cuál es el siguiente número? Entonces 1.01 ¿ cuál es el siguiente número que aparece después de este? ¿Puedes proponernos un listado? ¿Cuál es el siguiente número? Uh, puedes decir, OK, uh El siguiente número es 1.01001 tal vez o puede ser 1.0100001 tal vez este número sea el siguiente, quiero decir, puedes, pero no puedes encontrar el siguiente número. La propiedad del siguiente número debe ser que no debe haber ningún número intermedio. Y esto es imposible para este conjunto en particular. Um Ambos conjuntos, quiero decir, el conjunto de um positivo en profesores y el conjunto de números reales, ambos conjuntos son infinitos, pero este conjunto se llama contable y este conjunto se llama incontable. Así que sí, hay que tenerlo en cuenta y cuando hablemos de probabilidad, cuando hablemos de espacios muestrales y experimentos, deberíamos conocer la terminología subyacente. ¿Qué entendemos por conjunto finito? ¿Qué es un conjunto infinito? ¿Qué es el conjunto contable? Quiero decir, este es un nombre algo confuso, conjunto contable. Um Deberíamos llamar a un conjunto listable. Tal vez ese podría ser un mejor nombre, conjunto listable, un conjunto donde, donde el elemento se puede enumerar en un orden.Un conjunto incontable es un conjunto cuyos elementos no se pueden enumerar. Um Solo recuerda que el conjunto contable no tiene por qué ser finito. Si es finito, es contable, pero incluso conjuntos infinitos pueden ser contables. Sí, es posible. Mmm, sí. En el siguiente video, hablaré sobre más terminología relacionada con conjuntos uh, que son subconjuntos, conjuntos de potencia, conjuntos universales y muchos más. Entonces, espero verte en el próximo video.