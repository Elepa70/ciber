---
title: Matrices, sistemas de ecuaciones y detememinantes
description: 
published: true
date: 2025-11-10T20:29:14.627Z
tags: 
editor: markdown
dateCreated: 2025-11-10T14:15:40.092Z
---

# Matrices
> Vamos a ver un repaso de matrices, similar a lo estudiado en Bachillerato
{.is-warning}

## Definición
Definimos una matriz como:
- Dado un cuerpo, y dos números naturales distintos de cero. Considerando un conjunto $M =\{1,2,\dots,m\}$ y $N =\{1,2,\dots,n\}$, el producto cartesiano de $MxN$, dará la matriz A.

O una lista de $m*n$ elementos del cuerpo distribuidos por filas y columnas donde $A(i,j)=a_{ij}$.

## Conceptos generales
- Las filas, constituyen el primer "número", en el caso anterior el i.
- Las columnas, es el segundo valor "j".
- Cuando tenemos igual valores de $i=j$, decimos que tenemos una matriz cuadrada. La escribiremos como $A_{n}$.
- Si la matriz solo tiene fila, la llamaremos matriz fila, al igual pasa con la matriz columna cuando solo posee una columna.
- La diagonal principal está construida por los valors $a_{11},a_{22},a_{33}...a_{mn}$, el contrarío será la diagonal secundaría.

## Operaciones con matrices
Las operaciones que veremos son las básicas:
### La suma
En esta operación debemos sumar los elementos que hayan en la matriz que estén el la misma posición
### El producto
El producto de matrices debemos realizarlo de manera que el número de columnas de la primera matriz, sea igual al número de filas de la segunda matriz.

Por ejemplo $A_{2x5} * B_{5x6}$, en este caso si se puede realizar.

### Transpuesta
La transpuesta de una matriz no es más que la matriz es intercambiando los valores de fila en columna, es decir $a_{1,2}$ pasa a $a_{2,1}$.

### Matriz regulares
Son aquellas matrices que cuando se le multiplica una matriz especifica, se consigué la matriz identidad.
- La matriz identidad es una matriz donde solo tiene en su diagonal principal 1, y en el resto 0.

# Forma escalonada reducida
## Operaciones elementales
A las matrices ademas de estas operaciones normales entre ellas, podemos hacerle transformaciones nosotros mismos para ir obteniendo otras cosas, tenemos.
### Transformaciónes elementales por fila

En esta vamos a ver:
- El intercambio de filas. Lo expresaremos como $E_{1,n}$
- Multiplicación de una fila por un escalar distinto de 0. Expresado como $E_{2}(Valor)$
- Sumarle una fila y multiplicarla por algo. Expresado como $E_{3,n}(valor)$

En todas estas transformaciones siempre vamos a obtener una manera de revertirlo, pero debemos hacerlo en orden, ya que si no, vmaos a obtener una matriz completamente distinta a la que partimos.

## Matrices elementales
Las matrices elementales son aquellas matrices que obtenemos a la hora de modificar una matriz identidad con las operaciones elementales. 
> Se recomienda tener especial cuidado ya que puede llegar a la confusión si estamos operando tanto con estas matrices como con las cuadradas.
{.is-warning}

Cuando multiplicamos una matriz A por una elemental por la izquierda, lo que amos a obtener es una transformación por filas, sin embargo por la derecha por columnas.
## Matriz escalonada reducida
Una matriz escalonada reducia, por filas es una matriz que cumple:
- Si debajo de una fila nula (hay todos ceros), todas las demás son nulas.
- El pivote (Aquel primer elemento distinto de 0), tiene un valor de 1.
- El pivote está más a la derecha que el de la anterior fila.
- En las columnas donde hay un pivote, todo valor debajo del pivote es 0.
## Forma escalonada reducida
> Si no se entiende esto, por palabra del profesor. Hay poca posibilidad de poder aprobar la asignatura.
{.is-danger}

Dada cualquier matriz, solo existe una única matriz escalonada reducida por filas, que obtenemos a partir de transformaciones elementales por filas. Esto nos permite también ver el rango de la matriz, ya que el rango es aquél número de filas distinto de cero de la forma escaolnada reducida de una matriz.

Una vez tengamos las transformaciones realizadas, si usamos los mismos metodos pero en una matriz identidad, podemos obtener la matriz $P$, que nos dá la siguiente regla: $P*A=H_{A}$. Donde:
- $P$: Matriz obtenida mediante la multiplicación de transformaciones elementales en una matriz identidad.
- $A$: Matriz que estamos usando para obtener su matriz escalonada.
- $H_{A}$: Matriz escaolnada resultante.

Se pueden usar varios metodos para realizar este tipo de ejercicios:
1. Podemos ir paso a paso y ir apuntando las transformaciones que le estamos haciendo a la matriz, para después operar con la matriz $Id$.
2. Podemos "añadirle" o ampliar la matriz $A$, con la matriz $Id$ correspondiente, para poder obtener como resultado directamente $H_{A}$ y $P$, respectivamente.