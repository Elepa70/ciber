---
title: Sucesiones y series
description: 
published: true
date: 2025-11-02T19:50:26.858Z
tags: 
editor: markdown
dateCreated: 2025-10-01T20:11:42.684Z
---

# Sucesiones y series
## Sucesiones
Una sucesión es una lista ordenadas de números reales, que de hecho es infinita.

Por ejemplo, una sucesión de números reales, es una aplicación del conjunto de los números naturales en el conjunto de los números reales.
$1,2,3,4\dots$.

Cuando queremos representar una sucesión pondremos:
$\{x_{n}\}_{n \in \mathbb{N}}$. 
> No es necesario poner que n pertenece a los números reales, sin embargo lo ponemos la primera vez para poder guiarnos.
{.is-warning}

Vamos a ver 5 ejemplos básicos de sucesiones que usaremos más adelante, para mayor entendimiento del temario.

### Ejemplos
Sucesión constante o número 1. Es aquella que nunca va a variar por ejemplo:
$\{7\}, x_{n} = 7, \forall n \in \mathbb{N}$. Si lo representamos gráficamente tenemos una recta donde todos los puntos están concentrados en el 7.

Sucesión número 2. Es aquella sucesión más trivial que podemos imaginarnos:
$\{n\}, x_{n} = n, \forall n \in \mathbb{N}$. En este caso obtenemos una lista de números que empieza en el $1$ y acabará en el $\infty$.

Sucesión número 3. Otra forma de ver una sucesión.
$\{\frac{1}{n}\}, x_{n} = \frac{1}{n}, \forall n \in \mathbb{N}$. Ahora si lo representamos empezaremos en el 1, sin embargo nos acercaremos lentamente al 0 sin llegar a tocarlo.

Sucesión alternada o número 4. Donde puede haber dos valores.
$\{-1^{n}\}, x_{n} = -1^{n}, \forall n \in \mathbb{N}$. Si lo representamos en una recta, los valores irán alternando entre $-1$ (Si es impar) y $1$ (Si es par).


Con estos ejemplos vamos poder explicar las sucesiones convergentes y acotadas.
### Sucesiones convergentes
Las podemos definir como, sea $\{x_{n}\}$ es convergente, si solo sí cuando exista un único número x, que verifica que la distancia entre la sucesión y el valor x sea cercano.

Es decir: Podemos decir que es convergente, cuando podemos encontrar valores que están entre medias de X.

En nuestros ejemplos diremos:
- Es convergente, ya que los valores están en el 7.
- No es convergente, ya que al ir hasta el infinito, no podemos encontrar un valor medio.
- Es convergente ya que todos se acercan al 0.
- No es convergente ya que o están en el -1 o están en el 1.

Una forma muy vulgar de definirlo, es decir que los valores se apelotonan en un único lugar.
> Es solo para explicarlo, por favor no lo definais asi en los ejercicios.
{.is-danger}

### Sucesiones acotadas
Como vimos en el anterior tema, las sucesiones acotadas suelen ser las que poseen un espacio limitado donde existen los valores.
> Definición del alumno.
{.is-warning}

Podemos decir que:
- $\{x_{n}\}$ está acotada superiormente $<=> \exist \text{ }M \in \mathbb{R} \text{ t.q. } x_{n}\leq M, \forall n\in \mathbb{N}$. Existe un valor M perteneciente a los números reales, tal que M sea más grande que la sucesión, para cualquier valor dentro de la sucesión.
- $\{x_{n}\}$ está acotada inferiormente $<=> \exist \text{ }m \in \mathbb{R} \text{ t.q. } m\leq x_{n}, \forall n\in \mathbb{N}$. Existe un valor m perteneciente a los números reales, tal que m sea más pequeño que la sucesión, para cualquier valor dentro de la sucesión.
- $\{x_{n}\}$ está acotada $<=> \exist \text{ }m,M \in \mathbb{R} \text{ t.q. } m\leq x_{n}\leq M, \forall n\in \mathbb{N}$. Cuando existe cota superior y cota inferior


En nuestros ejemplos diremos:
- Esta acotada, ya que todos los valores están en 7, así que podemos acotarlo en $[6,8]$.
- No está acotada superiormente ya que se aleja hacia el infinito. Por lo tanto no está acotada en general.
- Está acotada ya que los valores están entre el 0 y el 1, podemos acotarla en $[-1,2]$
- Está acotada ya que todos los valores están entre -1 y 1, por lo que podemos acotarla en $[-2,2]$


Con esto podemos decir que las sucesiones convergentes están acotadas, sin embargo las sucesiones acotadas pueden o no ser convergentes.

### Sucesiones monótonas
La podemos definir como en una sucesión, siempre encontramos un valor donde dependiendo del puesto que ocupe, tendrá un valor mayor que el anterior. Ejemplo de estas puede ser la 2º del ejemplo.

Es decir, diremos que $\{X_{n}\}$ es creciente si $x_{n}\leq x_{n+1}, \forall \text{ }n \in \mathbb{N}$.
Pasa de forma similar cuando decimos que $\{X_{n}\}$ es decreciente, solo que $x_{n}\leq x_{n-1}, \forall \text{ }n \in \mathbb{N}$.


## Propiedades de los limites / Proposición
Vamos a ver una serie de propiedades de los limites.

Primero vamos a definir, Sean $\{x_{n}\}$ y $\{y_{n}\}$ dos sucesiones convergentes. Tenemos las siguientes propiedades:

1. $\lim (x_{n}+y_{n}) =\lim x_{n}+\lim y_{n}$,
2. $\lim (x_{n}*y_{n}) =\lim x_{n}*\lim y_{n}$,
3. Si $\lim y_{n} \neq 0$ entonces  $\lim\frac{x_{n}}{y_{n}} =\frac{\lim(x_{n})}{\lim(y_{n})}$,
4. Si $x_{n} \leq y_{n} \forall n$ entonces  $\lim(x_{n}) \leq \lim( y_{n})$
5. Si $x_{n}\leq y_{n} \leq z_{n}, \forall \text{ }n \in \mathbb{N}$ y $\lim x_{n}=\lim z_{n}$. Entonces $\lim x_{n} = \lim y_{n} = \lim z_{n}$. Esta se conoce como regla del sándwich, donde dado los limites que tienen al mismo lado, entonces cualquier numero intermedio también tiende al mismo limite.
6. Si $\{x_{n}\}$ esta acotada y $\lim y_{n} = 0$ entonces: $\lim x_{n} * y_{n} = 0$. O lo que es lo mismo, una sucesión acotada multiplicada por un límite que tiende a 0, es 0.


## Principio de inducción

El uso que le vamos a dar al principio de inducción es demostrar una propiedad en $\mathbb{N}$. Para hacer una demostración por inducción, vamos a hacer lo siguiente:
1. Debemos demostrar que suceda el primer caso. $(n=1)$
2. Suponemos que se cumplen los n primeros casos. Asumir la hipótesis de la inducción.
3. Demostrar que a partir del n-ésimo caso, demostrar el siguiente caso. $(n+1)$

Por ejemplo, cuando queremos demostrar que los elementos de una sucesión cumplen una propiedad, demostramos que el elemento $x_{1}$ se cumple, después, suponemos que se cumplen en $x_{1},\dots,x_{n}$ y tenemos que demostrar que si la propiedad se cumple en $x_{n}$, se cumple también en $x_{n+1}$.

Al final, de forma intuitiva, podemos ver que una inducción es esencialmente ir probando de manera iterada una propiedad. Vemos que se cumple un caso y a partir de ese, se pueden demostrar los siguientes pasos.

Curiosidad matemática: La inducción se basa fuertemente en la inductividad  de $\mathbb{N}$. Si tenemos que hacer un número infinito no numerable, entonces, la inducción no se puede realizar. En esos casos, tenemos que recurrir a lo que se denomina una inducción transfinita que usa fuertemente el axioma de elección.

## Sucesos divergentes
Los sucesos divergentes son aquellos donde se encuentra que el limite tiende a $+\infty$ o a $-\infty$. 
> SE DEBE CUMPLIR UNO DE LOS DOS, NO LOS DOS.
{.is-danger}

Cuando $\{x_{n}\}\Rightarrow +\infty \text{  ó } \lim x_{n}= +\infty \Leftrightarrow [\forall M \in \mathbb{R}, \exists n_{0} \in \mathbb{N}, n\geq n_{0} \Rightarrow x_{n} \geq M]$.

Esta es la definición matemática, pero esencialmente debemos quedarnos con que si tiende a infinito **positivo** podemos decir que es divergente positivamente. Sin embargo si tiende al infinito **negativo**, diremos que es divergente negativamente.


### Límites que tienden al infinito
Bien una sucesión divergente, tenemos que uno de sus límites tiende al infinito. Vamos a ver algunas operaciones básicas con infinitos.
#### Suma
No voy a describirla, únicamente se van a escribir las propiedades.
$L \in \mathbb{R}$.
$\infty + L = +\infty$.
$\infty - L = +\infty$.
$- \infty + L = -\infty$.
$-\infty - L = -\infty$.


$\infty + \infty = \infty$.
$-\infty - \infty = -\infty$.
$\infty - \infty = Error!$. Ojo esto es una indeterminación, no sabemos si puede ser finito o infinito.
> Recordamos que una indeterminación es algo que no está determinado.
{.is-info}

#### Producto
$\infty * \infty = \infty$.
$\infty * -\infty = -\infty$.
$\infty + L = \infty$ Si $L > 0$
$\infty + L = -\infty$ Si $L < 0$

#### Inversión
Una inversión la escribimos como $\frac{x_{n}}{y_{n}}=x_{n}*\frac{1}{y_{n}}$

$\{y_{n}\} \rightarrow L \neq 0 \Rightarrow \{\frac{1}{y_{n}}\} \rightarrow \frac{1}{L}$.


$\{y_{n}\} \rightarrow \infty \Rightarrow \{\frac{1}{y_{n}}\} \rightarrow 0$.


$\{y_{n}\} \rightarrow 0  \Rightarrow \{\frac{1}{y_{n}}\} \rightarrow \infty \text{ o } -\infty$.


#### Escala de infinitos
Hay veces que llegamos aun cociente entre polinomios y debemos saber cuál de los dos tiende más a infinito con respecto al otro, ya que si no tendríamos un $\frac{\infty}{\infty}$, que es una indeterminación.

El orden de menor a mayor tendencia a infinito es:
$\log(n) \propto n^{b} \propto a^{n} \propto n^{n}$, con $b > 0$ y $a > 0$


### Indeterminaciones con sucesiones $\{X_{n}^{y_{n}}\}$.
Con este tipo sucesiones podemos encontrar una serie de indeterminaciones.

Estas sucesiones usualmente vamos a usar la formula de la $e$, recordamos que es: $X_{n}^{y_{n}}=e^{y_{n}*log(x_{n})}$.
- "$\infty^{0}$": Este tipo de indeterminación, usaremos la formula de la $e$.
- "$0^{0}$": En este tipo de indeterminación, también usaremos la formula de la $e$.
- "$1^{\infty}$" En este tipo de indeterminación usaremos el **teorema** del número $e$, que se va  explicar a continuación.

El teorema del número $e$, nos da las siguiente "propiedad":
1. El estudio de estos límites son el mismo: $\lim y_{n}(x_{n}-1)= L \Leftrightarrow \lim x_{n}^{y_{n}} = e^{L}$.

Con esta propiedad, según el valor de L, podemos sacar que:
- Si L, toma el valor de $\infty$, entonces nos vamos hacia el infinito.
- Si L, toma el valor de $-\infty$, entonces el valor que tomaremos es 0.

## Series de $\mathbb{N}$.
Antes de explicar que son las series, es importante saber como funciona el $\varSigma$, o sumatorio.

Cuando tenemos $\varSigma^{n}_{n=1}a_{n} = a_{1}+a_{2}+\dots a_{n}$, tenemos un sumatorio que va desde $n=1$ hasta $n$. Por lo tanto sea la sucesión $\{a_{n}\}$, $S_{1}=a_{1},S_{2}=a_{1}+a_{2},S_{3}=a_{1}+a_{2}+a_{3}\dots S_{n}=\varSigma a_{n}$, esto último lo llamaremos termino general de $a_{n} \text{ o }\varSigma a_{n}$.
> Las indicaciones en $\varSigma^{n}_{n=1}a_{n}$, n debe estar encima del sumatorio y $n=1$, debe estar debajo del sumatorio. Debido al software que uso, no puedo implementar esto último.
{.is-warning}

Cuando tenemos una serie, dada por un sumatorio (Lo normal), podemos diferenciar dos partes:
- Termino general: Lo que está en el sumatorio
- Sucesión de sumas parciales: Aquello que da el resultado sus sumas parciales, lo veremos con ejemplos.

#### Ejemplos
1. $\varSigma \text{ }7$, tenemos el termino general $7$ y la sucesión de sumas parciales $7+7+7+7+7+\dots$. Esta serie se llama **serie constante**.

2. $\varSigma \text{ } \frac{1}{n}$, tenemos el termino general $\frac{1}{n}$ y la sucesión de sumas parciales $1+\frac{1}{2}+\frac{1}{3}+\frac{1}{4}+\dots + \frac{1}{n}$. Esta serie se llama **serie armónica**. Existe una variante de serie armónica, llamada **serie armónica generalizada**, que es escribe de la siguiente manera$\varSigma \text{ } \frac{1}{n^{\alpha}}$.

3. $\varSigma \text{ }x^{n}$, tenemos el termino general $x^{n}$ y la sucesión de sumas parciales $1+x+x^{2}+x^{3}+x^{4}+\dots +x^{n}$. Esta serie se llama **serie geométrica de razón x**. Donde $x$ es un valor constante. 

### Serie convergente
Decimos que una serie como $\varSigma a$ es convergente si y solo si, existe un limite en la sucesión. De forma matemática $\varSigma a \text{ es convergente} \Leftrightarrow \exists \lim(a_{1}+a_{2}+a_{3}+\dots a_{n}) \in \mathbb{R}$.

El apartado de $\lim(a_{1}+a_{2}+a_{3}+\dots a_{n})$, lo podemos llamar suma de la serie. 

Para que una serie sea convergente, es necesario que su termino general deba tender a 0. $\varSigma a_{n} \text{ convergente} \Rightarrow \{a_{n}\}\rightarrow 0$, sin embargo esto no puede ser inverso, es decir. Si el termino general tiende a 0, no tiene porque ser convergente.

De los ejemplos que tenemos:
- Las series constantes nunca serán convergentes.
- Las series armónicas no convergen, sin embargo las series que sean armónica generalizadas **SI**, convergen, siempre y cuando $\alpha$ tengo un valor mayor a 1, es decir $\alpha > 1$.
- Las series geométricas de razón, si convergen, pero solo si el termino general, tiene un valor positivo menor a 1. Es decir $|x|<1$.

### Serie cola
Las series cola consiste en unas series donde partimos desde "otro punto" que no le corresponde a una serie normal. Es decir es nacida de otra.

> Si una serie cola, es parte de una serie convergente, entonces la serie cola también lo será.
{.is-info}

#### Ejemplo
$\varSigma^{\infty}_{n\geq 7}a_{n} \Rightarrow \varSigma^{\infty}_{n = 7}a_{n} = \varSigma^{\infty}_{n =1}a_{n} - (a_{1}+a_{2}+a_{3}+a_{4}+a_{5}+a_{6})$. 

> Importante fijarse como están puestas las flechas y los iguales debajo del sumatorio.
{.is-warning}

### Propiedades de las series / Operaciones de las series
Las propiedades de las series, o las operaciones que podemos realizar con ellas son dos, y siempre debemos tener una serie convergente, para este ejemplo vamos a tener $\varSigma a_{n} \text { y }\varSigma \text{ }b_{n}$, ambas convergentes.

- $\varSigma (a_{n}+b_{n}) = \varSigma a_{n} +\varSigma b_{n}$.
- $\varSigma \alpha a_{n} = \alpha \varSigma a_{n}$, siendo $\alpha$ una constante.

### Criterios de convergencia en series
Aunque hayamos dicho que aquellas series que son convergente, debe tender su termino general a 0. Sin embargo, no nos es fácil evaluar las series dadas, por ello vamos a prender 3 criterios de convergencias más.

En todos los criterios vamos a tener en cuenta que $\varSigma a_{n} (a_{n} \geq 0, \forall n)$.
1. Criterio de la Raíz n-esima (También conocido como criterio de Couchy): En este método lo que hacemos es: Sea $\varSigma a_{n}$, $\lim \sqrt[n]{a_{n}} = L$, y dependiendo de $L$, tenemos uno o varios resultados.

1. Criterio del cociente (También conocido como criterio de D'Alembert): En este método lo que hacemos es: Sea $\varSigma a_{n}$, $\lim \frac{a_{n+1}}{a_{n}} = L$, lo que es lo mismo y  $\lim (a_{n+1})*(\frac{1}{a_{n}}) = L$ dependiendo de $L$, tenemos uno o varios resultados.


1. Criterio de comparación (por paso al limite): Este método es algo distinto a los anteriores, ya que lo que haremos será fundamentalmente comparar con otras sucesiones que tengamos. Primero lo que haremos será determinar quienes son nuestras sucesiones, sea  $\varSigma a_{n}$ y $\varSigma b_{n}$, donde $\varSigma a_{n}$ solemos usarla como aquella a la que vamos a analizar.
	a) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = L \neq 0 \Rightarrow$ ambas sucesiones hacen lo mismo, es decir convergen o no convergen, dependiendo de con cuál sucesión estemos comparando.
  b) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = 0 \Rightarrow$ tenemos dos opciones, la primera es que $\varSigma b_{n} \text{ conv} \Rightarrow \varSigma a_{n} \text{ conv}$ |||| $\varSigma a_{n}\text{ no conv} \Rightarrow \varSigma b_{n} \text{ no conv}$.
  c) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = \infty \Rightarrow$ tenemos dos opciones, la primera es que $\varSigma a_{n} \text{ conv} \Rightarrow \varSigma b_{n} \text{ conv}$ |||| $\varSigma b_{n}\text{ no conv} \Rightarrow \varSigma a_{n} \text{ no conv}$.
  
Cualquier otra cuestión del criterio de comparación, cuenta como invalido o desconocido.
  
Las sucesiones que usaremos para compararlas son:
- Genérica de razón $\varSigma x^{n} \text{ conv}\Leftrightarrow |x|<1$
- Armónica genérica $\varSigma \frac{1}{x^{\alpha}} \text{ conv}\Leftrightarrow \alpha>1$