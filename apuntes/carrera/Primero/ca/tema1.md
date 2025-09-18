---
title: Tema 1 - Números Reales
description: 
published: true
date: 2025-09-18T17:55:39.244Z
tags: 
editor: markdown
dateCreated: 2025-09-18T09:14:28.603Z
---

# Tema 1 - Números Reales
Las funciones están definidas en un conjunto de números, usualmente reales. Pero debemos antes de tocar las funciones, saber que son los números reales y como se interpreta o escribe en formato matématico.

## Definición de los Números Reales (ℝ)
Los números reales consisnten en el conjunto de todos los números que pueden representarse en una recta númerica. **Incluyendo** los números racionales y irracionales.

## Propiedades de ℝ y sus operaciones
Los números reales poseen dos operaciones fundamentales:
- Suma
- Producto

Cada una de estas tienen propiedades que las distinguen de las otras.

### Suma
La suma ( a + b ), resulta en una operación "básica", las cuales tienen las siguientes propiedades:
- Conmutativa: Da igual el orden de los valores, el resultado es el mismo.
a + b = b + a, ∀ a, b ∈ R
- Asociativa: Da igual el orden de 3 valores, podemos reorganizarlo para que de el mismo resultado.
 (a + b) + c = a + (b + c), ∀ a, b, c ∈ R
- Elemento neutro: Para cualquier valor de *a*, siempre que le sumemos 0 es *a*.
a + 0 = a, ∀ a ∈ R

- Elemento opuesto: Dado un valor *a*, existe un valor único, *-a*, tal que:
a + (-a) = 0

### Producto
El producto (a . b), resulta en la operación de multiplicar valores:
- Conmutativa: Da igual el orden de los valores, el resultado es el mismo.
a · b = b · a, ∀ a, b ∈ R
- Asociativa: Da igual el orden de 3 valores, podemos reorganizarlo para que de el mismo resultado.
 (a · b) · c = a · (b · c), ∀ a, b, c ∈ R
- Elemento neutro: Para cualquier valor de *a*, siempre que le multipliquemos 1 es *a*.
a · 1 = a, ∀ a ∈ R

- Elemento inverso: Si a es un número real distinto de 0, existe el inverso que a por su inverso es 1.
1/a = a −1, tal que a ·1 a = 1. (MODIFICAR)

- Propiedad distributiva: Un mismo valor puede afectar a ambos lados dentro de un parentesis (Explicación del alumno)
a(b + c) = ab + ac, ∀ a, b, c ∈ R

### Orden
El orden nos sirve para poder determinar que valor es mayor que el otro.
- Propiedad reflexica: Un valor tiene el mismo orden que si mismo.
a ⩽ a
- Propiedad antisimétrica: Un valor "a" que sea superior a "b", y el mismo valor "b" es superior a "a", podemos decir que ambos valores son iguales.
a ⩽ b, b ⩽ a =⇒ a = b

- Propiedad transitiva: Siendo un valor "a", mayor que "b", y el mismo valor "b", mayor que "c". Podemos decir que el valor "a", también es mayor que "c".
{a ⩽ b} {b ⩽ c1  }=⇒ a ⩽ c

- Total: Dados dos valores "a" y "b" pertenecientes a los números reales, podemos decir que "a" es mayor que "b" o que "b" es mayor que "a".
- Orden y suma: Dado dos valores donde uno es mayor que el otro, si ambos son sumados por el mismo valor, se mantendrá el orden.
a ⩽ b =⇒ a + c ⩽ b + c
- Orden y producto:Dado dos valores donde uno es mayor que el otro, si ambos son multiplicados por el mismo valor, se mantendrá el orden.
a ⩽ b, c ⩾ 0 =⇒ ac ⩽ bc


Dados dos subconjuntos "A" y "B", y verificando que a ⩽ b, donde "a" es un valor perteneciente a "A", y "b" es un valor perteneciente a "B", existe un valor "c" perteneciente a los números reales que debe estar entre "a" y "b".

**Dados A, B ⊂ ℝ verificando que a ⩽ b para cualquier a ∈ A, b ∈ B, existe c ∈ ℝ tal que a ⩽ c ⩽ b, ∀a ∈ A, ∀b ∈ B.**

## Subconjuntos o conjuntos dentro de ℝ
Hemos podido analizar algunas propiedades dentro de los números reales, sin embargo es esencial poder describir algunos de sus conjuntos para poder comprender la magnitud de los números reales.

### Importante
Durante el curso se verá el simbolo ℝ, acompañado de varios números o otros simbolos, para poder entenderlo:
ℝ^+^ = {x ∈ ℝ : x > 0} : Todos los números reales mayor que 0.
ℝ^-^ = {x ∈ ℝ : x < 0} : Todos los números reales menores que 0.
ℝ^*^ U ℝ^-^ U {0}= ℝ     : La unión de todos los números reales mayores que cero, menores que cero y cero, forman todos los números reales.
ℝ^*^ = {x ∈ ℝ : x ≠ 0} : Todos los números reales distintos de 0.
ℝ^+^~0~ = {x ∈ ℝ : x ≥ 0} : Todos los números reales mayores que 0, incluyendo el 0.
ℝ^-^~0~ = {x ∈ ℝ : x ≤ 0} : Todos los números reales menores que 0, incluyendo el 0

Con esto explicado podemos dar paso a los subconjuntos de ℝ
### Naturales ℕ
Podemos decir que son aquellos números que son positivos y no tienen decimales. OJO: No está el 0
ℕ = {1,2,3,4...,n,n+1}.
### Enteros ℤ
Podemos decir que son aquellos números que son positivos y negativos, que no tienen decimales. Sin embargo aquí incluimos el 0.
ℤ = {-4,-3,-2,-1,0,1,2,3,4...}.
### Racionales ℚ
Podemos decir que los numeros racionales son aquellos valores decimales que podemos expresar en forma de fracción.
ℚ = {p/q : p ∈ ℤ, q ∈ ℕ}.
### Irracionales ℝ\ℚ
Podemos decir que son aquellos números que no son racionales.
Estos números pueden ser: pi (π), raiz de 2 (√2), euler (e) o el número de oro (φ) o (Ø).


## Intervalo y acotar
Un intervalo es aquel consiste en aquel espacio que contiene una series de números. (Explicación alumno).

"Un conjunto A ⊂ R es un intervalo si dados x e y ∈ A, se cumple que (x, y) ⊂ A "

Para poder definir los tipos de intervalos, vamos a establecer la siguiente regla:
- Sean a, b ∈ ℝ, a < b. (Sean a y b, dos valores pertenecientes a los números reales y siendo b mayor que a)

Con la regla mencioanda anteriormente podemos ver los dos tipos de intervalos:
### Recta

En este intervalo encontramos aquellos que están definidos entre dos valores fijos, es decir a y b.

Un ejemplo puede ser [1,3], en este intervalo tenemos a 1 y 3, y todos los números intermedios.

Vamos a poner los distintos intervalos que podemos encontrar en la recta.
[a, b] = {x ∈ R : a ⩽ x ⩽ b}.
(a, b] o ]a, b] = {x ∈ R : a ⩽ x ⩽ b}.
[a, b) o [a, b[ = {x ∈ R : a ⩽ x ⩽ b}.
(a, b) o ]a, b[ = {x ∈ R : a ⩽ x ⩽ b}.


### Semirrectas
Sin embargo en este tipo de intervalos, encontraremos aquellos que no tienen porque están definidos en un valor fijo.

Esto pueden ser por ejemplo:
Un intervalo entre [1, ∞), ya que el valor infinito, no podemos definirlo exactamente.

Podemos encontrar los siguientes intervalos:
[a, +∞) = {x ∈ R : a ⩽ x}.
(a, +∞) = {x ∈ R : a < x}.
(−∞, b] = {x ∈ R : x ⩽ b}.
(−∞, b) = {x ∈ R : x < b}.

### Acotación