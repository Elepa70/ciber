---
title: Vectores, Matrices y Registros
description: 
published: true
date: 2025-10-21T17:00:06.294Z
tags: 
editor: markdown
dateCreated: 2025-10-21T17:00:06.294Z
---

# Vectores, Matrices y Registros

Los lenguajes de programación tienen datos primitivo, **SIN LIBRERIAS**, es decir: char, int, long, bool...

Sin embargo, si solo podemos usar, no seriamos capaces de crear infraestructuras como las de hoy en dia. Esto se verá más adelante en la asignatura Estructuras de Datos.

Existen tipos d edatos estructurados, que nacen de los datos primitivos, estos tipos de datos son:
- Estáticos: Consiste en un tipo de dato, donde el tipo de dato lo defines cuando lo compilas.
- Dinámicos: Conforme se vaya ejecutando el programa, el tipo de dato crece o decrece. Usualmente es más usado, sin embargo actualmente solo veremos estáticos.


Los tipos de datos simples, representan un único valor, una variable de tipo entero representa un único número entero.

Los tipos de datos estructurados pueden representar una colección de valores, las variables representan un conjunto de valores. 

## Vectores

Un array, es un conjunto finito y ordenado de elementos homogéneos. Es decir sabemos la cantidad de elementos que hay, con un orden impuesto y tiene el miso tipo de datos.

Un array, consiste en una estructura general, y pueden ser: vectores (Unidimensional), matrices (Bidimensionales, o tabla) o cubos (Mayor a 2 dimensiones).



Los vectores consiste en el array más simple, y se representan como un conjunto de elementos consecutivos de un mismo tipo a los que se pueden acceder mediante un índice. 
- Los índices: Empiezan con el 0, aunque esto no tiene porque ser siempre cierto debemos comprobar según donde estemos trabajando. 
- Rango: Conssite en la cantidad de elemetos que hay.

Podemos expresarlo como
```C++
v[0]
v[3]
v[i+i] \\ Ojo debemos primero haber declarado i, y debe ser entero.
```

> Ojo, si ponemos v[N], teniendo un array de tamaño N, esto fallará. Este error se llama violación de segmento.
{.is-danger}


