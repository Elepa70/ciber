---
title: Cuerpos finitos
description: 
published: true
date: 2025-10-22T19:11:08.623Z
tags: 
editor: markdown
dateCreated: 2025-10-22T19:11:08.623Z
---

# Polinomios
Empezamos el tema 3, con los polinomios. Sin embargo, todavía no vamos a definirlo.

## Definición de anillo
Un anillo consiste en un conjunto que cumple, que hay suma, resta y multiplicación. Como pueden ser los conjuntos $\mathbb{Z},\mathbb{Q},\mathbb{R},\mathbb{C} \text{ y } \mathbb{Z}_{n}:n\geq 2$.

Como poseen la suma y la multiplicación, también cumplira las propiedades que tienen como es:
1. Para cualesquiera $a,b,c \in A$ se tiene que $(a+b)+c =a +(b+c)$.
1. Para cualesquiera $a,b \in A$ se tiene que $a+b =b+a$.
1. Existe un elemento $0 \in A$, que nos permite $a+0 = a$.
1. Para cualquier elemento $a\in A$, existe un elemento $b \in A$ tal que $a+b=0$.
1. Existe un elemento $1 \in A$, que nos permite $a*1 = a$.
1. Para cualesquiera $a,b,c \in A$ se tiene que $a* (b+c) =a*b +a*c$.

## Definición de cuerpo
Un cuerpo por otro lado, tiene que cumplir lo anterior y que tenga inverso. Un cuerpo puede ser los conjuntos: $\mathbb{Q},\mathbb{R},\mathbb{C} \text{ y } \mathbb{Z}_{p}: \text{p número primo}$.

Debemos añadir a las anteriores propiedades, dos propiedades más.
1. Para cualesquiera $a,b\in A$ se tiene que $a*b =b*a$.
1. Para cualquier elemento $a\in A, a\neq 0$, existe un elemento $b \in A$ tal que $a*b=1$.

## Polinomios
Definimos los polinomios (de una variable) con coefecientes en K, como: $a_{n}x^{n}+\dots+a_{1}x+a_{0}$. Donde $n\in\mathbb{N},a_{i} \in K,x\notin K$.

Podemos llamar al conjunto del polinomio como $K[x]$.

Realmente esta definición no es del todo formal, ya que vamos a trabajar con algunos polinomios que no se riguen por esta norma. Sin embargo como ha dicho el profesor, vamos a continuar como si esta definición fuera la idonea.

Una vez definido más o menos, vamos a ver sus propiedades. Estas propiedades son básicas pero se dejarán escritas.
1. Si $a_{n}\neq 0$, entonces se dice que el polinomio dado tiene un grado según el valor del coeficiente más alto.
2. Al elemento $a_{k}\in K$ se le llama coeficiente de grado k, y a la expresión $a_{k}x^{k}$, termino de grado k.
3. El coeficiente más alto del polinimo lo podemos llamar coeficiente líder.
4. El coeficiente de grado 0 de un polinomio se le llama término independiente.
5. Un polinomio cuyo coeficiente lider tenga un valor de $1$, se le llama polinomio mónico.
6. Un polinomio que tiene grado 0, se le llama polinomio constante.

### Operaciones de Polinomios
Las operaciones en polinomios son básicas, las sumas y las restas se hacen respecto al grado del coeficiente que tengamos. No podemos sumar un valro cuyo coeficiente sea $3$ a otro con coeficiente $2$.

Por otro lado las multiplicaciones y las divisiones son más complejas, las divisiones las veremos más adelante.

Las multiplicaciones las hacemos de cada elemento de un polinomio, hacia el otro polinomio, nos podemos valer de varios metodos para resolverlo, pero usualmente es recomendable separar las multiplicaciones que realicemos y después sumarla. Es importante el grado.
#### División de polinomios
Sea $K$ un cuerpo, y sean $p(x),q(x) \in K[x]$ con $q(x) \neq 0$. Entonces existen unos valores $c(x),r(x) \in K[x]$ tales que:
- $p(x)=q(x)*c(x)+r(x)$.
- $gr(r(x)) < gr(q(x)) \text{ o }r(x) = 0$.

Es decir, dados dos polinomios en un cuerpo. Debe existe un polinomio "cociente" y otro "resto" que cumple:
- El polinomio del divisor debe ser igual al polinomio del dividendo por el polinomio del cociente + el polinomio del resto.
- El grado del polinomio resto, debe ser más pequeño que el polinomio del divisor, o puede ser 0.
### Evaluación
Es lo que conmumente hemos llamado, darle valores. Es cuando asignamos un valor a nuestra "$x$", para saber que valor nos dará.

### Raíz
Consiste en una evaluación, donde el valor resultante es 0, o buscamos que sea 0. Lo que decimos normalmente como resolver una ecuación.

## Algoritmo de Horner
El algoritmo de horner es un metodo que tenemos para poder dividir polinomios, recordamos la definición anteriormente.
