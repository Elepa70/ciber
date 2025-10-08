---
title: Tema 1 - Números Reales
description: 
published: true
date: 2025-10-08T14:29:30.765Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:32:19.213Z
---

# Tema 1 - Números Reales
Las funciones están definidas en un conjunto de números, usualmente reales. Pero debemos antes de tocar las funciones, saber que son los números reales y como se interpreta o escribe en formato matemático.

## Definición de los Números Reales $(\mathbb{R})$
Los números reales consisten en el conjunto de todos los números que pueden representarse en una recta numérica. **Incluyendo** los números racionales y irracionales.

Definiremos los números reales como la unión de los números racionales y los irracionales. Geométricamente, lo definiremos como una recta numérica, la conocida recta real. Que cumplen axiomáticamente las propiedades de un anillo conmutativo, es decir, un cuerpo, y que tienen una relación de orden.

## Propiedades de $\mathbb{R}$ y sus operaciones
Los números reales poseen dos operaciones fundamentales:
- Suma
- Producto

Cada una de estas tienen propiedades que las distinguen de las otras.

### Suma
La suma $a+b$, resulta en una operación "básica", las cuales tienen las siguientes propiedades:
- Conmutatividad: Da igual el orden de los valores, el resultado es el mismo.
$a+b=b+a\quad\forall a,b\in\mathbb{R}$.
- Asociativa: Da igual el orden de 3 valores, podemos reorganizarlo para que de el mismo resultado.
$(a + b) + c = a + (b + c), \forall a, b, c \in \mathbb{R}$.
- Elemento neutro: Para cualquier valor de *a*, siempre que le sumemos 0 es *a*.
$a + 0 = a, \forall a \in \mathbb{R}$.

- Elemento opuesto: Dado un valor *a*, existe un valor único, *-a*, tal que:
$a + (-a) = 0$.

### Producto
El producto (a . b), resulta en la operación de multiplicar valores:
- Conmutativa: Da igual el orden de los valores, el resultado es el mismo.
$a · b = b · a, \forall a, b \in \mathbb{R}$.
- Asociativa: Da igual el orden de 3 valores, podemos reorganizarlo para que de el mismo resultado.
$(a · b) · c = a · (b · c), \forall a, b, c \in \mathbb{R}$.
- Elemento neutro: Para cualquier valor de *a*, siempre que le multipliquemos 1 es *a*.
$a · 1 = a, \forall a \in \mathbb{R}$.

- Elemento inverso: Si a es un número real distinto de 0, existe el inverso que a por su inverso es 1.
$\frac{1}{a} = a^{−1}, \text{tal que } a{-1} · a = 1$.

- Propiedad distributiva: Un mismo valor puede afectar a ambos lados dentro de un parentesis (Explicación del alumno)
$a(b + c) = ab + ac, \forall a, b, c \in \mathbb{R}$.

### Orden
El orden nos sirve para poder determinar que valor es mayor que el otro.
- Propiedad reflexica: Un valor tiene el mismo orden que si mismo.
$a \leq a$.
- Propiedad antisimétrica: Un valor "a" que sea superior a "b", y el mismo valor "b" es superior a "a", podemos decir que ambos valores son iguales.
$a \leq b, b \leq a => a = b$.

- Propiedad transitiva: Siendo un valor "a", mayor que "b", y el mismo valor "b", mayor que "c". Podemos decir que el valor "a", también es mayor que "c".
$\{a \leq b\} \{b \leq c  \}=⇒ a \leq c$.

- Total: Dados dos valores "a" y "b" pertenecientes a los números reales, podemos decir que "a" es mayor que "b" o que "b" es mayor que "a".
- Orden y suma: Dado dos valores donde uno es mayor que el otro, si ambos son sumados por el mismo valor, se mantendrá el orden.
$a \leq b =⇒ a + c \leq b + c$.
- Orden y producto:Dado dos valores donde uno es mayor que el otro, si ambos son multiplicados por el mismo valor, se mantendrá el orden.
$a \leq b, c \geq 0 =⇒ ac \leq bc$.


Dados dos subconjuntos "A" y "B", y verificando que $a \leq b$, donde "a" es un valor perteneciente a "A", y "b" es un valor perteneciente a "B", existe un valor "c" perteneciente a los números reales que debe estar entre "a" y "b".

**Dados $A, B \in \mathbb{R}$ verificando que $a \leq b$ para cualquier $a \in A, b \in B$, existe $c \in \mathbb{R}$ tal que $a \leq c \leq b, \forall a \in A, \forall b \in B$.**

## Subconjuntos o conjuntos dentro de $(\mathbb{R})$
Hemos podido analizar algunas propiedades dentro de los números reales, sin embargo es esencial poder describir algunos de sus conjuntos para poder comprender la magnitud de los números reales. Vamos a describir a continuación los subconjuntos más notables de $\mathbb{R}$

### Importante
Durante el curso se verá el simbolo ℝ, acompañado de varios números o otros simbolos, para poder entenderlo:
$\mathbb{R}^{+} = \{x \in \mathbb{R} : x > 0\}$ : Todos los números reales mayor que 0.

$\mathbb{R}^{-} = \{x \in \mathbb{R} : x < 0\}$: Todos los números reales menores que 0.

$\mathbb{R}^{+} \cup \mathbb{R}^{-} \cup \{0\} = \mathbb{R}$: La unión de todos los números reales mayores que cero, menores que cero y cero, forman todos los números reales.

$\mathbb{R}^{*} = \{x \in \mathbb{R} : x \neq 0\}$: Todos los números reales distintos de 0.

$\mathbb{R}^{+}_{0} = \{x \in \mathbb{R} : x \geq 0\}$: Todos los números reales mayores que 0, incluyendo el 0.

$\mathbb{R}^{-}_{0} = \{x \in \mathbb{R} : x \leq 0\}$:Todos los números reales menores que 0, incluyendo el 0

Con esto explicado podemos dar paso a los subconjuntos de ℝ
### Naturales $(\mathbb{N})$
De forma intuitiva definimos los números naturales como aquellos que usamos para contar. Cabe destacar que el cero NO está incluido en los naturales. Sin embargo, los algebristas consideran el cero como natural por conveniencia.

$\mathbb{N}=\{1,2,3,4,\dots\}$.

### Enteros $(\mathbb{Z})$
Diremos que los números enteros son los naturales, los opuestos y el cero.
$\mathbb{Z}=\{\dots,-2,-1,0,1,2,\dots\}$.
### Racionales $(\mathbb{Q})$
Podemos decir que los numeros racionales son aquellos valores decimales que podemos expresar en forma de fracción.
$\mathbb{Q} = \{\frac{p}{q} : p \in \mathbb{Z}, q \in \mathbb{N}\}$.
### Irracionales $(\frac{\mathbb{R}}{\mathbb{Q}})$
Podemos decir que son aquellos números que no son racionales.
Estos números pueden ser: pi (π), raiz de 2 (√2), euler (e) o el número de oro (φ) o (Ø).


## Intervalo y acotar
Un intervalo con extremos $a$, $b$, con $a\leq b$, es el conjunto de todos los números comprendidos entre ambos valores

Para poder definir los tipos de intervalos, vamos a establecer la siguiente regla:
- Sean $a, b \in \mathbb{R}, a < b$. (Sean a y b, dos valores pertenecientes a los números reales y siendo b mayor que a)

Con la regla mencionada anteriormente podemos ver los dos tipos de intervalos:
### Segmento

En este intervalo encontramos aquellos que están definidos entre dos valores fijos, es decir a y b.

Un ejemplo puede ser [1,3], en este intervalo tenemos a 1 y 3, y todos los números intermedios.

Vamos a poner los distintos intervalos que podemos encontrar en la recta.
$[a, b] = \{x \in \mathbb{R}: a \leq b\}$.
$(a, b] \text{ o } ]a, b] = \{x \in \mathbb{ℝ}: a < x \leq b\}$.
$[a, b) \text{ o } [a, b[ = \{x \in \mathbb{R} : a \leq x < b\}$.
$(a, b) \text{ o } ]a, b[ = \{x \in \mathbb{R} : a < x < b\}$.


### Semirrectas
Sin embargo en este tipo de intervalos, encontraremos aquellos que no tienen porque están definidos en un valor fijo.

Esto pueden ser por ejemplo:
Un intervalo entre [1, ∞), ya que el valor infinito, no podemos definirlo exactamente.

Podemos encontrar los siguientes intervalos:
$[a, +∞) = \{x \in \mathbb{R} : a \leq x}$.
$(a, +∞) = \{x \in \mathbb{R}: a < x}$.
$(−∞, b] = \{x \in \mathbb{R} : x \leq b\}$.
$(−∞, b) = \{x \in \mathbb{R}: x < b\}$.

### Acotación
Ahora en vez de decir "definido", vamos a usar la palabra matematica ideal. Acotado.

Cuando un intervalo está acotado superiormente, significa que existe un valor que siempre está debajo de todo el intervalo. Al igual, decimos que un valor está acotado inferiormente, cuando encontramos un valor que siempre está por debajo del intervalo.

*A* tiene una cota superior en $\mathbb{R}$, si y solo si,existe un valor *M*, que pertenece a los números reales que es mayor que *a* para todo el conjunto de *A*.

En lenguaje matemático: $A \subset \mathbb{R}, \exist M \in \mathbb{R}, a\leq M, \forall a\in A$.

> Ojo también existe la cota inferior, simplemente debemos encontrar un valor que sea siempre menor al conjunto dado.
{.is-info}


Al igual, decimos que un intervalo está acotado, si esté está acotado superiormente **y** inferiormente.


Por último, podemos decir, que en un intervalo existe un máximo de un conjunto, cuando un valor perteneciente al conjunto definido es superior a todo los valores del conjunto dado. 
> Similar a la cota inferior, existe un mínimo del conjunto, debemos dijarnos que está definido.
{.is-info}

## Valor absoluto

El valor absoluto de un número real x es su distancia al cero. Algebraicamente es una función a trozos.

$|x| = dist(x,0) = \{ x, si x\geq 0, -x, si x<0\}$.

> Ojito, la raíz de x, es el valor absoluto de x: √x = |x\|
{.is-warning}

### Propiedades del valor absoluto
Tenemos 6 propiedades:
- $|x| \geq 0$.
- $|x| = 0 ⇔ x = 0$.
- $|x| \leq y ⇔ -y \leq x \leq y$.
- $|x + y| \leq |x| + |y|$.
- $|x - y| \leq ||x| - |y||$.
- $|xy| = |x| · |y|, \frac{|x|}{|y|} = \frac{|x|}{|y|}$.
> Según la profesora, ni la 4 ni la 5, se le debería tomar importancia para lo que daremos en el curso. NO SIGNIFICA QUE NO SEAN IMPORTANTES PARA EL APRENDIZAJE!!!
>{.is-danger}


