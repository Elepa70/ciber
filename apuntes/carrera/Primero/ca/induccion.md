---
title: Principio de Inducción - Ejercicio práctico
description: 
published: true
date: 2025-10-09T16:31:14.998Z
tags: 
editor: markdown
dateCreated: 2025-10-08T20:03:21.415Z
---

# En esta página vamos a resolver un ejercicio de inducción para complementar la teoría del tema 2.
Ejercicio en cuestión:

Demuestra que la sucesión $x_{1}=1,x_{n+1}=\sqrt{3x_{n}},\forall n \geq 1$ es convergente y calcula su límite.

Como bien sabemos, una sucesión es convergente, si los valores se "apelotonan" en un mismo lugar, o sí la sucesión es monotona y acotada.

Vamos a hacer el segundo paso, vamos a demostrar que es monotona y acotada para poder decir que es convergente.

## Monotonia
Bien vamos tenemos el valor de $x_{1}$, así que vamos a obtener $x_{2}$, para poder comparar si la función podría seguir una monotonia o no.

$x_{2}= \sqrt{3x_{1}} = \sqrt{3}$. Con este resultado podemos decir: $x_{1}\leq x_{2}$. Sin embargo, esto nos permite decir que: ¿$x_{n}\leq x_{n+1}, \forall n \in \mathbb{N}$?.

Para ello vamos a hacer uso del principio de la induccion.

### Principio de la inducción para la monotonia.
Como sabemos de los apuntes, debemos comprobar que suceden tres cosas:
1. Se debe cumplir el orden con n=1. En este caso ya hemos demostrado que $x_{1}\leq x{2}$, por lo que no hace falta hacer nada.
2. La hipotesis de la inducción nos dice que entonces, $x_{n}$ debe ser menor a $x_{n+1}$.
3. Vamos a comprobar si lo anterior es cierto. Es decir ¿$x_{n}\leq x_{n+1}$?.

Para ello lo que se recomienda es seguir un orden, en este caso vamos a partir desde los valores de $x$, y vamos a ir añadiendo a izquierda y a derecha para poder llegar a la sucesión.
> Siguiendo los pasos se entenderá lo anterior.
{.is-success}

$x_{n}\leq x_{n+1} \Rightarrow 3x_{n} \leq 3x_{n+1} \Rightarrow \sqrt{3x_{n}} \leq \sqrt{3x_{n+1}}$.

¿Que hemos hecho?
Primero hemos añadido a ambos lados del igual un 3, esto es debido a que en la sucesión que tenemos al principio, lo primero que acompaña a $x_{n}$ es una multiplicación por 3. Y comprobamos la igualdad, en este caso por principios del conjunto de los naturales, una constante multplicando a ambos lados de una desigualdad, mantendrá la desigualdad.

Una vez tengamos $3x_{n}$, añadimos lo que nos falta que es la raíz cuadrada. Y volvemos a comprobar que la desigualdad se mantenga, en este caso si pensamos en la función raíz, nos acordaremos que es estrictamente creciente, por lo que lo va a alterar la soluciones en este caso.

Bien con esto hemos llegado que $\sqrt{3x_{n}} \leq \sqrt{3x_{n+1}}$ es decir $x_{n} \leq x_{n+1}$. Por lo tanto podemos dejar escrito que es una sucesión, monotona y estrictamente creciente.


## Acotada
Bien una vez finalizado la monotonia, ahora nos toca saber si es o no acotada, como es un sucesión monotona y estrictamente creciente, podemos decir con seguridad que tenemos una cota inferior en $x_{1}$. ¿Pero cuál es la cota superior?

Esto ahora mismo para nosotroso no es posible calcularlo, así que vamos a "dejarlo estar", para continuar con la convergencia.

## Convergente
Bien, si recordamos, que sea convergente, es que los valores se aproximen mucho a un elemento, pero nunca llegar y sobre todo, nunca pasarse de ese elemento. 

Para hacer esta parte debemos **suponer** que existe un limite de $x_{n}$, y lo vamos a llamar $l$.
> En la explicación original de la profesora, se llamaba $x$, sin embargo se va a llamar $l$, para un mayor entendimiento.
{.is-info}

Una vez **supuesto**, ese límite, vamos a calcularlo y añarlo. Escribiremos:
Supongamos que $\exists \lim x_{n} = l$.

$x_{n}=\sqrt{3x_{n}}$. Tenemos esto, sin embargo nos parece incomodo calcular un límite con una raíz cuadrada, así que elevamos al cuadrado a ambos lados para poder quitarlo.

$x_{n}^{2}=3x_{n}$, esto lo podemos escribir como: $x_{n}*x_{n}=x_{n}^{2}=3x_{n}$.

Ahora vamos a hacer susupuestos limites con $x_{n}*x_{n}$ y $3x_{n}$.
> En el papel, deberíamos escribri una línea hacia abajo con: ($n \rightarrow \infty$).
{.is-info}

Vale, ahora aplicaremos las propiedades que nos sabemos sobre las sucesiones. La primera es que, una multplicación entre limites convergentes, da como resultado un límite convergente, y la segunda es que una multiplicación de una constante y un limite convergente, resulta en un limite convergente.

Es decir, cuando buscalos los limites de $x_{n}*x_{n}=3x_{n}$, encontraremos que: $l*l=3l$.

Resolvemos esta operación y nos da como resultados: $l=0$ y $l=3$. Sin embargo $l \neq 0$, ya que es menor al infimo que tenemos en la sucesión $x_{1}=1$, dicho en otras palabras, se salé de nuestro rango de trabajo, ya que estamos por encima de 1.

## Vuelta a acotada

Por lo tanto ahora **seguimos asumiendo**, que si $l=3$, entonces ¿$1\leq x_{n} \leq 3$? y también que ¿$x_{n}\leq 3, \forall n \in \mathbb{N}$?.

Ahora lo que haremos será de nuevo, aplicar el princpio de inducción, para comprobar que esto es correcto.

### Principio de inducción en acotado.
Bien como se ha dicho, vamos a comprobar efectivamente que el límite es correcto o no. Para ello empezamosa  aplicar los tres pasos del princpio de inducción.
1. Se debe cumplir el orden con n=1. Es correcto ya que $x_{1}=1 \leq 3$.
2. La hipotesis de la inducción nos dice que entonces, $x_{n}$ debe ser menor a $3$.
3. Vamos a comprobar ahora que, también se cumple para valores a $n$, es decir $n+1$. Es decir ¿$x_{n+1}\leq 3$?.

$x_{n+1} \leq 3 \Leftrightarrow 3x_{n+1} \leq 3*3 \Leftrightarrow \sqrt{3x_{n+1}} \leq \sqrt{3*3} \Leftrightarrow \sqrt{3x_{n+1}}\leq \sqrt{9} \Leftrightarrow \sqrt{3x_{n+1}} \leq 3$. Por lo tanto, podemos decir que: $x_{n+1} \leq 3$.

Esto implica que efectivamente hay un límite superior en 3, por lo tanto estamos ante una sucesión acotada.

## Conclusión y finalización del ejercicio.
Debido a que estamos ante una sucesión que es acotada y monotona, podemos decir que estamos ante una sucesión convergente, con limites $\{1,3\}$.

> Hasta que no sea revisado el ejercicio, tenga en cuenta que puede tener faltas ortograficas, erratas o conclusiones/explicaciones poco coherentes matematicamente hablando.
{.is-danger}
