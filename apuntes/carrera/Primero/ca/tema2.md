---
title: Sucesiones y series
description: 
published: true
date: 2025-10-08T20:01:50.725Z
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
$\{n\}, x_{n} = n, \forall n \in \mathbb{N}$. En este caso obtenemos una lista de números que empieza en el $1$ y acabará en el $\infty$

Sucesión número 3. Otra forma de ver una sucesión.
$\{\frac{1}{n}\}, x_{n} = \frac{1}{n}, \forall n \in \mathbb{N}$. Ahora si lo representamos empezaremos en el 1, sin embargo nos acercaremos lentamente al 0 sin llegar a tocarlo.

Sucesión alternada o número 4. Donde puede haber dos valores.
$\{-1^{n}\}, x_{n} = -1^{n}, \forall n \in \mathbb{N}$. Si lo representamos en una recta, los valores irán alternando entre $-1$ (Si es impar) y $1$ (Si es par).


Con estos ejemplos vamos poder explicar las sucesiones convergentes y acotadas.
### Sucesiones convergentes
Las podemos definir como, sea $\{x_{n}\}$ es convergente, si solo sí cuando exista un único número x, que verifica que la distancia entre la sucesión y el varlo x sea cercano.

Es decir: Podemos decir que es convergente, cuando podemos encontrar valores que están entre medias de X.

En nuestros ejemplos diremos:
- Es convergente, ya que los valores están en el 7.
- No es convergente, ya que al ir hasta el infinito, no podemos encontrar un valor medio.
- Es convergente ya que todos se acercan al 0.
- No es convergente ya que o están en el -1 o están en el 1.

Una forma muy bulgar de definirlo, es decir que los valores se aperotonan en un unico lugar.
> Es solo para explicarlo, por favor no lo definais asi en los ejercicios.
{.is-danger}

### Sucesiones acotadas
Como vimos en el anterior tema, las sucesiones acotadas suelen ser las que poseen un espacio limitado donde existen los valores.
> Definición del alumno.
{.is-warning}

Podemos decir que:
- $\{x_{n}\}$ está acotada superiormente $<=> \exist \text{ }M \in \mathbb{R} \text{ t.q. } x_{n}\leq M, \forall n\in \mathbb{N}$. Existe un valor M perteneciente a los números reales, tal que M sea más grande que la sucesión, para cualquier valor dentro de la sucesión.
- $\{x_{n}\}$ está acotada inferiormente $<=> \exist \text{ }m \in \mathbb{R} \text{ t.q. } m\leq x_{n}, \forall n\in \mathbb{N}$. Existe un valor m perteneciente a los números reales, tal que m sea más pequeño que la sucesión, para cualquier valor dentro de la sucesión.
- $\{x_{n}\}$ está acotada $<=> \exist \text{ }m,M \in \mathbb{R} \text{ t.q. } m\leq x_{n}\leq M, \forall n\in \mathbb{N}$. Cuando existe cota superior y cota ínferior


En nuestros ejemplos diremos:
- Esta acotada, ya que todos los valores están en 7, así que podemos acotarlo en $[6,8]$.
- No está acotada superiormente ya que se aleja hacia el infinito. Por lo tanto no está acotada en general.
- Está acotada ya que los valores están entre el 0 y el 1, podemos acotarla en $[-1,2]$
- Está acotada ya que todos los valores están entre -1 y 1, por lo que podemos acotarla en $[-2,2]$


Con esto podemos decir que las sucesiones convergentes están acotadas, sin embargo las sucesiones acotadas pueden o no ser convergentes.

### Sucesiones monotomas
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
5. Si $x_{n}\leq y_{n} \leq z_{n}, \forall \text{ }n \in \mathbb{N}$ y $\lim x_{n}=\lim z_{n}$. Entonces $\lim x_{n} = \lim y_{n} = \lim z_{n}$. Esta se conoce como regla del sandwich, donde dado los limites que tienen al mismo lado, entonces cualquier numero intermedio también tiende al mismo limite.
6. Si $\{x_{n}\}$ esta acotada y $\lim y_{n} = 0$ entonces: $\lim x_{n} * y_{n} = 0$. O lo que es lo mismo, una sucesión acotada multiplicada por un límite que tiende a 0, es 0.


## Principio de inducción
Este principio lo utilizamos para demostrar que se cumplen propiedades para todo $\mathbb{N}$.

Definimos los números naturales como $\mathbb{N} = \{1,2,3,\dots\}$ verificando:
1. $1\in \mathbb{N}$.
2. Si $n \in \mathbb{N} \Rightarrow n+1 \in \mathbb{N}$.

Con los dos primeros elementos de una sucesión cumplan estas propiedades, podemos decir que todos los elementos de la sucesión pertenecen al conjunto $\mathbb{N}$.

> Susceptible a error, se actualizá.
{.is-warning}
