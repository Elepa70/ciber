---
title: Recursividad
description: 
published: true
date: 2025-12-09T16:51:13.828Z
tags: 
editor: markdown
dateCreated: 2025-12-09T16:51:13.828Z
---

# Recurisividad
## Definición
*Se dice que un objeto es recursivo si forma parte de sí mismo o se define en función de sí mismo.*

Los algoritmos repulsivos son útiles cuando el problema a resolver, o la forma de llegar a la solución, están ya definimos en formas recursiva.

Ejemplos:
Cuando tenemos un descendiente de una persona, pues lo definimos como hijo de X, o es hijo de hijo de X, etc...

La recursividad es la propiedad que tiene una función por la cual puede llamarse a si misma. Usualmente menos eficiente que una iterativa.


Tenemos dos tipos de recursividad:
- Recursividad directa: Una función se hace referencia a si misma.
- Recursividad indirecta: Tenemos dos o más funciones que se llaman mutuamente.

## Funcionamiento
Para resolver un problema, el primer paso será descomponer el problema de forma que su solución quede definida en función de ella misma, pero de un tamaño menor.

- Caso base: Casos del problema que se resuelve con un segmento de código sin recursividad.
- Casos generales: Se hace llama a si mismo con un subproblema m