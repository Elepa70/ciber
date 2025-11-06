---
title: Combinatoria
description: 
published: true
date: 2025-11-06T13:32:48.951Z
tags: 
editor: markdown
dateCreated: 2025-10-30T20:43:18.172Z
---

# Combinatoria
## Conteo
En este tema, vamos a ir hacia atras. Es decir, vamos a partir como si estuvieramos aprendiendo de buenas a primeras lo que son las matematicas, para ello empezamos contando.

El conteo, no es más que dado un conjunto, poder enumerarlos. Tiene una cardinalidad, osea que llega hasta cierto número.

Esto debe es biyectivo (recordamos el primer tema).

### Suma
Tras aprender a contar, aprendimos a sumar y lo mismo vamos a hacer.

La suma no es mas que dado dos conjuntos, sin elementos en común, la unión de ambos elementos. Sería como juntar dos conjuntos.

Una forma de explicarlo según el profesor es: "Si una primera tarea es puede realizar de $n_{1}$ formas, y una segunda tarea se puede realizar de $n_{2}$ formas, ambas tareas son incompatibles, por lo que debe haber una tarea que sea $n_{1}+n_{2}$, que unan ambas."

### Principio Inclusión-Expulsión
Este principio, nos permite la resta, que es lo siguiente que aprendimos.

Pongamos un caso donde tenemos dos conjuntos y queremos sumarlos, sin embargo en estos conjuntos existen elementos que están en ambos lugares al mismo tiempo, es decir que son intersección. Esto nos genera un problema a la hora de sumar.

Cuando intentamos hacer la unión de ambas, nos damos cuenta de que el elemento extra, se suma dos veces, por lo que debemos excluirlo o expulsarlo.

Por ello la unión de dos conjuntos es: $|U \cup Y| = |X|+|Y| - |X\cap Y|$, donde $X\text{ e }Y$, son conjuntos.

Si lo vemos con dos conjuntos es facil pero cuando tenemos más de uno se puede hacer algo dificil, es por ello que existe la siguiente regla que nos permitirá facilitar las sumas, si la cantidad de valores que vamos a juntar es impar (Es decir, $|X|$ o $|X\cup Y \cup Z|$), en caso contrario deberemos restar.

### Principio del producto
Podemos definir el principio del producto, como el producto cartersiano de dos conjuntos.

Sin embargo, hay veces que nos preguntan sobre cuantas aplicaciones distintas podemos definir dos conjutnos dados. Esto no es más que poner $Y^{X}$, según que nos piden, en el caso anterior: definir X en Y.

### Principio de palomar

El principio de palomar, nos dice que si queremos introducir un elemento (m), donde tenemos un número inferior de capacidad (n), va a haber por lo menos un lugar donde haya dos elementos.

El generalizado, simplemente nos dice que puede haber más de dos elementos.

## Variaciones
> A partir de este punto, es cuando se empieza a complicar el temario.
{.is-warning}

Las variaciones es un metodo que poseemos para poder elegir el número total de elecciones dentro de un conjunto dado, esto puede ser con o sin repetición. El orden de eleccion tiene importancia.
### Sin repetición
En este caso, podemos verlo como una carrera y se debe dar 3 medallas, bronce, plata y oro.

El problema, es que dentro de todos los atletas, pongamos 10, se pueden producir una gran cantidad de variaciones para quien puede poseer estas medallas. Sin embargo tenemos una formula que nos lo permite.

La denotación que le daremos a la variaciones es la siguiente $V^{m}_{n}$, donde $m$ nuestras medallas o elementos a elegir, y $n$, nuestros atletas o el espacio que imponemos.

Para calcularlo, no es que usar la siguiente formula: $V^{m}_{n}=\frac{n!}{(n-m)!}$. Puede existir el caso donde $m$ y $n$, tengan el mismo valor, entonces lo podemos representar como $P_{n}$.


### Con repetición
En este caso, nos queda una situación mucho más simple, ya que al no tener que excluir nada no debemos dividir entre nada, solo debemos jugar entre nuestro espacio muestral.

Se denota de la siguiente manera: $VR^{m}_{n}$, y simplemente debemos hacer $n^{m}$.


## Combinaciones
### Combinaciones sin repetición
Consiste en una seleccion de elementos donde a diferencia de variaciones no tiene importancia el orden, y no se puede repetir elementos.


Ejemplo: Elegir a 3 personas de un grupo de clase para ir a Benidor.

Lo vamos a denotar como $C^{m}_{n}$, donde $m$ es la cantidad de elementos y $n$ son las cantidad de benficiarios.

#### Propiedades
Para poder calcular las posibilidades podemos calcularlo de la siguiente manera:
- Podemos calcular los elementos seleccionados.
- Restante de aquellos elementos no seleccionados menos los que iban a serlo.

Es decir: $C^{m}_{n}=C^{n-m}_{n}$

Ojo $C^{n}_{n}=1$ y $C^{1}_{n}=n$.


Otra propiedades más dificil, es verlo de manera:
- Esta $x$ elemento involucrado.
- No está $x$ elemento involucrado.

$C^{m}_{n}=C^{m-1}_{n-1}+C^{m}_{n-1}$.

#### Como realizarlo
Si tomamos en cuenta las variaciones, podemos ver que que sería las combinaciones multiplicado por las permutaciones que podemos realizar, entonces nuestra formula tiene que ver con estos calculos, es decir:

$V^{m}_{n} = C^{m}_{n}/P_{m}$, que despenjando y escribiendo los valores nos sale: $C^{m}_{n}= \frac{n!}{(n-m)!}$, que podemos escribir como $\binom{n}{m}$

### Permutacion con repetición
Esto consiste en sasber en cuantas formas queremos ordenar algo, pero hay objetos que se repiten.

Por ejemplo, cuando queremos ordeanr letras A A A A B B B C C, tenemos que elegir donde poner las A, donde tenemos $\binom{9}{4}$, con las B tenemos en cuenta la perdida de las posiciones por A, entonnces son $\binom{5}{3}$, y el resto es C $\binom{2}{2}$.

Multiplicariamos estos valores de forma:
$\binom{9}{4} * \binom{5}{3} * \binom{2}{2} = \frac{9! * 5! * 2!}{4! * 3! * 2!}$

$P^{n_{1}...n{r}}_{n}= \frac{n!}{n_{1}!... n_{r}!}$

### Combinacion con repeticion

En estas combinaciones, tenemos en cuenta que hay distintos montones de un mismo elementos, como por ejemplo bolas de colores, donde solo tenemos rojas, amarillas o verdes.

Se denota de la siguiente manera $CR^{m}_{n}$. 

Por ejemplo en las bolas, tenemos que sacar 4 bolas y son de 3 montones de colores, $CR^{4}_{3}$. Teniendo en cuenta esto, debemos aplicar las reglas anteriores para poder calcularlo, es decir:
$CR^{m}_{n}=C^{n-1}_{m+n-1}$, una vez tengamos esto, podemos calcularlo con las reglas de antes.


## Triángulo de Pascal
> En espera de que se suban los apuntes para poder comparar y corregir.
{.is-warning}

El triangulo de Pascal, no es mñas que una sucesión de elementos ordenados, que nos pueden ayudar a comprender algúnas cosas de las matématicas, como puede ser $(a+b)^{b}$.

Ese triangulo lo formaremos con los elementos $\binom{n}{m}$, partimos desde $\binom{0}{0}$, y continuaremos hasta la que queramos.

### Propiedades
Este triángulo respeta las propiedades que vimos anteriormente como:
- $\binom{0}{n}=1$.
- $\binom{n}{n}=1$.

Y podemos operar con ellos también, de una forma especial. Para cada elemento que creamos nuevo por ejemplo:
$\binom{1}{0}=1$ $\binom{1}{1}=1$, podemos hacer una suma de ellos para que nos de uno posterior:
$\binom{2}{1}=1+1 = 2$.

Es decir tenemos la regla de que: $\binom{n-1}{m-1}+ \binom{n-1}{m} = \binom{n}{m}$.

COn esto podemos deducir las propiedades de $(a+b)^{n}$, con la siguiente formula:
$(a+b)^{n}=\varSigma\binom{n}{0} a^{k-k+b^{n}}$.