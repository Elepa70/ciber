---
title: Cuerpos finitos
description: 
published: true
date: 2025-10-27T20:35:18.726Z
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

El algoritmo de Horner, es un metodo que tenemos para poder dividir polinomios y funciona de la siguiente manera:
- Escribimos todos los coeficientes del polinomio dividendo, en una fila.
- En el lateral de la tabla, escribiremos de forma descendiente los valores del divisor. (Aunque el primero de todo no lo usaremos).
- Tras esto haremos "Ruffini", es decir, bajamos el priver valor y lo multiplicamos por ambos números del latera. Importante: Cuando multipliquemos, usaremos todos los valores del dividendo excluyendo el del mayor grado, y después lo colocaremos según cuando lo hayamos multiplicado, es decir si ha sido el primero lo colocaremos justo para el siguiente, si es el segundo, pues hacia el segundo etc etc
- Tras esto, los úlltimos valores según nuestro dividendo (Si estamos multiplicando con dos valores, los últimos dos valores), será considerando nuestro resto y lo que sobre será nuestro cociente.

Es importante, cuandoe stemos en $\mathbb{Z}_{n}$, deberemos tener en cuenta que los valores que ponemos a la izquierda son negativos, así que deberemos buscar primero su inverso (Algoritmo extendido de euclides). 

Si el dividendo **NO** es mónico, deberemos dividir todos los valores finales entre $\frac{1}{n}$, siendo $n$, el valor que acompaña a la incognita con mayor grado. Se debe tener especial cuidado si estamos en otra base.

## Polinomios - Divisibilidad
Cuando hablamos de la divisibilidad, usamos los mismos conceptos que aprendimos con los números enteros, es decir $a|b$. Sin embargo aquí debemos tener en cuenta que usamos cuerpos y que estamos con polinomios.

Los mayores cambios son con algunas propiedades como:
- Si $a(x)|1$ entonces $a(x) \in K$.
- Si $a(x)|b(x)$ y $b(x)|a(x)$ entonces $a(x)= \lambda b(x)$ para algún $\lambda \in K$.
- Si $a(x)|b(x)$ y $a(x)|c(x)$ entonces $a(x)|(b(x)+c(x))$ y $a(x)|(b(x)-c(x)$.
- Si $a(x)|b(x)$  entonces $a(x)|b(x)  *c(x)$ para cualquier $c(x) \in K$.

Dicho esto vamos a ver el Máximo común divisor.
### Máximo común divisor
> Esto puede ser muy confuso, se recomienda enormemente practicarlo.
{.is-warning}

El máximo común divisor en polinomios, funciona similar que en los enteros, sin embargo puede llegar a ser confuso.

Debemos tener en cuenta una cosa:
- Vamos a considerar los polinomios mónicos como unica solución.

Esto es debidoa que podemos tener multiplos "máximos común divisor". 

### Mínimo común múltiplo
Si el máximo es similar, el mínimo no se queda corto, por ello no hay nada que explicar.

## Polinomios irreducibles
Los polinomios irreducible, son como los números primos. Aquellos polinomios cuyo mcd es $1$ y el mismo polinomio. Estos polinomios no tienen porque ser monicos, sin embargo todos lo mónicos son irreducibles.

Por ende, los polinomios reducibles, son aquellos polinomios que están conformado por varios irreducbiles (Ejemplo: $4=2^{2}$)

### Factorización de polinomios
La factorización de polinomios es lo mismo que en los números reales (como se ha dicho antes $9=3^{2}$. Sin embargo aquí jugamos una serie de reglas:
- Un polinomio $q(x)$ se considera irreducible si tiene un divisir grado $1$, y solo tiene una raíz.

Con estas reglas debemos **sabernos** los siguientes polinomios irreducibles en $\mathbb{Z}_{2}$:
- $x$.
- $x+1$.
- $x^2+x+1$.
- $x^3+x+1$.
- $x^2+x^{2}+1$.

El resto como $x^{2}$ se escribe como composición de los anteriores, por ejemplo $x^{2}=x*x$ o $x^3+1 = (x+1)(x^2+x+1)$, o $x^{4}+x^{2}+1 = (x^{2}+x+1)^{2}$.

Para poder deducir si es o no irreducible, dependiendo de la base que tengamos, debemos sustituir todas las "$x$", con los valores de esa $Z_{n}$. Por ejemplo si tenemos $Z_{3}$, lo comprobamos sustituyendo cada x por $\{0,1,2\}$, y comprobar si son o no raíz.

### Raices multiples
Cuando tenemos raices multiples, nos referimos a que es posible que un polinomio, en vez de estar expresado con una raiz irreducible, la expresemos como esa raiz irreducible, elevada a algo. No es mas que decir que $8=2^3$.

### Raices racionales
Es una forma de poder resolver raices donde el grado es superior a 4, ya que no existe formula para poder resolverlo. Pero antes debe cumplir una serie de cuestiones.

Si $\frac{a}{b}$ es raíz, entonces $a$, puede tomar todos los valores que son $mcd(a,b)$
 Sea $q(x)=a_{n}x^{n}+\dots+a_{1}x+a_{0}$, tenemos que debe cumplir:
 - $a|a_{0}$, es decir que el valor a, debe ser los multiplos del $a_{0}$.
 - $b|a_{n}$, es decir que el valor de b, debe ser los multiplos de $a_{n}$.
 - $(b-a)|q(1)$, de todas las raices que tengamos formadas por $\frac{a}{b}$, la cumplen aquellas que sea divisor de $(b-a)$.
 - $(a+b)|q(-1)$, de todas las raices que tengamos formadas por $\frac{a}{b}$, la cumplen aquellas que sea divisor de $(a+b)$.
 
## Algoritmo de euclides extendido
Esta parte no tiene mucho cambio con respecto a lo estudiado anteriormente, ya que es lo mismo. Sin embargo debemos tener en cuenta que la solución final siempre debe ser monica (o al menos intentarlo), por ello debemos multiplicarlo (En caso de que no salga 