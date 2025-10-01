---
title: Aritmética entera y modular
description: 
published: false
date: 2025-10-01T20:10:46.608Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:45:03.771Z
---

# Sistemas de numeración
## Definición de números naturales

Vamos a empezar, con la definición de las números naturales.


Podemos definir los números naturales, como aquellos que usamos para enumerar, incluyo en el 0. Tiene una serie de propiedades que son:
- Conmutividad
- Existe un número neutro 0, que cualquier número sumado a el es el mismo número. Con el producto es el 1.
- Está ordenado, desde el 0 hasta el infinito.

## Algoritmo de la división

El algoritmo de la división lo podemos definir como
Sean $a,b \in \mathbb{N} \text{ con } b \neq 0$. Entonces existen números $c, r \in \mathbb{ N }$ tales que cumplen:
- $a = b * c + r$.

## Sistema decimal
Es el sistema que conocemos, es decir el que está en base 10. $(0,1,2,3,4,5,6,7,8,9)$. Es decir el número 4853, podemos escribirlo como.

$a = 4853$
$a = 4 * 10^{3} + 2 * 10^{3} + 5 * 10^{3} + 7 * 10^{0}$

Así que podemos decir lo siguiente:
Sean $a,b \in \mathbb{N} \text{ con } a \neq 0 \text{ y } b \geq 2$. Entonces existen números $m \in \mathbb{N}, m \neq 0 \text{ y } a_{0},a_{1}, \dots ,a_{m} \in \mathbb{N}$  tales que cumplen:
- $a \leq a_{i} \leq b$.
- $a = \sum_{k=0}^{m} a_{k}*b^{m}+a_{m-1} *b ^{m-1} \dots +a_{1} *b + a_{0}$.
- $a_{m} \neq 0$.

## Operaciones
Las operaciones las podemos realizar en cualquier base de la misma manera, solo debemos tener en cuenta un detalle importante.
En base 10, la que conocemos, cuando llegamos al número 9, cambiamos el simbolo a 10. Si por ejemplo lo hacemos en base 6, cuando lleguemos a la cuenta 5+1, en vez de que sea 6, es 10.

## Cambios de base
Para hacer cambios de base, debemos tener en cuenta dos cosas.
1. Multiplicar si tenemos una base menor a la que queremos llegar. Ejemplo, $253)_{6} = 2*5^{3}+5*5^{2}+3*5^{1}$
2. Dividir si tenemos una base mayor a la que queremos llegar. Ejemplo, $450)_{10}$ deberemos dividir el número 

## Truco con Binarios
Con los números binarios, podemos hacer un cambio más sencillo al octal y al hexadecimal. Esto es debido a que el binario, al estar en base 2, las potencias de dos llegan a 8($2^{3}$) y a 16($2^{4}$).

Para hacer este truco, cuando tengamos un número binario y queramos pasarlo a octal, simplemente deberemos agrupar de 3 en 3 los números y leerlo como si fuera decimal. Al igual pasa con el hexadecimal.

# Representación en complementos




# Divisibilidad 