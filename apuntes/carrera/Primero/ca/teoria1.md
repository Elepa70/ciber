---
title: Apuntes para el primer parcial de Calculo
description: 
published: true
date: 2025-11-12T09:43:13.222Z
tags: 
editor: markdown
dateCreated: 2025-11-04T10:19:52.029Z
---

# Apuntes rápidos para el primer parcial de calculo
Estos apuntes son para hacer una pasada rapida, no es nada recomendable estudiar de aquí.

> Aprenderse las funciones y comportamientos de las trigonometricas y sus arcos. 
{.is-warning}

## Valores en en $\mathbb{R}$.

$\mathbb{R}^{+} = \{x \in \mathbb{R} : x > 0\}$ : Todos los números reales mayor que 0.

$\mathbb{R}^{-} = \{x \in \mathbb{R} : x < 0\}$: Todos los números reales menores que 0.

$\mathbb{R}^{+} \cup \mathbb{R}^{-} \cup \{0\} = \mathbb{R}$: La unión de todos los números reales mayores que cero, menores que cero y cero, forman todos los números reales.

$\mathbb{R}^{*} = \{x \in \mathbb{R} : x \neq 0\}$: Todos los números reales distintos de 0.

$\mathbb{R}^{+}_{0} = \{x \in \mathbb{R} : x \geq 0\}$: Todos los números reales mayores que 0, incluyendo el 0.

$\mathbb{R}^{-}_{0} = \{x \in \mathbb{R} : x \leq 0\}$:Todos los números reales menores que 0, incluyendo el 0.

## Otro formato (No principio de inducción)
### Cálculo de la monotonía
Lo podemos hacer la interpretación de valores conforme a otro termino ($y$), ejemplo. Imponemos que $x<y$, entonces en la función $f(x)>f(y)$, pero esto no podemos hacerlo directametne, debemos ir paso a paso como si fuera un principio de inducción, ejemplo:

$f(x)= \frac{1}{x+e^{x}}$.

Pues hacemos: $x>y \Rightarrow x+e^{x} > y+e^{y}$, sin embargo al invertirlo, como es una división nos sale que es decreciente. Osea es monotona y decreciente.



## Principio de inducción
Tiene tres principios:
1. Se debe cumplir para $x_{1}$.
2. Nos cuestionamos que es lo que queremos hacer.
3. Lo haremos con uno más que el anterior $x_{n+1}$.

Lo que vamos haciendo es ir añadiendo los valores de la sucesión de forma que lleguemos al mismo punto o valor.

Ejemplo:
$x_{1}=1,x_{n+1}=\sqrt{3x_{n}},\forall n \geq 1$. Vamos a ver si es monotona.

Lo primero que haremos será mirar el valor en $x_{2}$ que nos dá (Hacer los cálculos) $\sqrt{3}$.

Y ahora empezamos con el principio de inducción.
1. ¿Se cumple en $x_{1}$? Sí $x_{1}<x_{2}$.
2. ¿Qué queremos demostrar? Qué $x_{n}<x_{n+1}$.
3. Por lo tanto comprobamos que $x_{n+1}<x_{n+2}$.

Ejercicio resuelto en: [Principio de inudcción](/apuntes/carrera/Primero/ca/induccion)
## Fórmula o reglas con sucesiones famosas
### Regla del número e
Cuando tenemos una indeterminación del tipo "$1^{\infty}$", usamos la regla del número e.
$x_{n}^{y_{n}}=y_{n}(x_{n}-1) = L$, y para acabarlo: $e^{L}$.

Sucesión famosa:
$(\frac{x+1}{x})^{x}=x((\frac{x+1}{x}-1)=1$, el resultado es $L$, que es $e^{1}=e$.
### Calculo con el teorema del número e (O Formula)
En caso de tener una indeterminación del tipo "$0^{0}$" o "$\infty^{0}$", tendremos que usar el teorema del número e (también llamado la formula del número e).

$x_{n}^{y_{n}}= e^{y_{n}*\log(x_{n})}$, una vez puesto, normalmente empezamos a resolver unicamente:
$y_{n}*\log(x_{n})$.

Sucesión famosa:
$\lim[(\frac{n+1}{n})^{n}]=\lim[e^{n*\log(\frac{n+1}{n})}]$, que nos dá como resultado final del límite $e$.
## Criterios de convergencia
En todos los criterios vamos a tener en cuenta que $\varSigma a_{n} (a_{n} \geq 0, \forall n)$.
1. Criterio de la Raíz n-esima (También conocido como criterio de Couchy): En este método lo que hacemos es: Sea $\varSigma a_{n}$, $\lim \sqrt[n]{a_{n}} = L$.

1. Criterio del cociente (También conocido como criterio de D'Alembert): En este método lo que hacemos es: Sea $\varSigma a_{n}$, $\lim \frac{a_{n+1}}{a_{n}} = L$.


En los métodos anteriores vamos a tener solución o no dependiendo de $L$, podemos obtener que:
- $L < 1$: Por lo tanto es convergente.
- $L = 1$: No podemos determinar nada, el criterio ha fallado.
- $L > 1$: No es convergente.




3. Criterio de comparación (por paso al limite): Este método es algo distinto a los anteriores, ya que lo que haremos será fundamentalmente comparar con otras sucesiones que tengamos. Primero lo que haremos será determinar quienes son nuestras sucesiones, sea  $\varSigma a_{n}$ y $\varSigma b_{n}$, donde $\varSigma a_{n}$ solemos usarla como aquella a la que vamos a analizar.

	a) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = L \neq 0 \Rightarrow$ ambas sucesiones hacen lo mismo, es decir convergen o no convergen, dependiendo de con cuál sucesión estemos comparando.
b) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = 0 \Rightarrow$ tenemos dos opciones, la primera es que $\varSigma b_{n} \text{ conv} \Rightarrow \varSigma a_{n} \text{ conv}$ |||| $\varSigma a_{n}\text{ no conv} \Rightarrow \varSigma b_{n} \text{ no conv}$.
c) Si $\lim \frac{\varSigma a_{n}}{\varSigma b_{n}} = \infty \Rightarrow$ tenemos dos opciones, la primera es que $\varSigma a_{n} \text{ conv} \Rightarrow \varSigma b_{n} \text{ conv}$ |||| $\varSigma b_{n}\text{ no conv} \Rightarrow \varSigma a_{n} \text{ no conv}$.
  
Cualquier otra cuestión del criterio de comparación, cuenta como invalido o desconocido.
  
Las sucesiones que usaremos para compararlas son:
- Genérica de razón $\varSigma x^{n} \text{ conv}\Leftrightarrow |x|<1$.
- Armónica genérica $\varSigma \frac{1}{x^{\alpha}} \text{ conv}\Leftrightarrow \alpha>1$.

## Suma de Series

Recordamos las propiedades de las series:
- $\varSigma (a_{n}+b_{n}) = \varSigma a_{n} +\varSigma b_{n}$.
- $\varSigma \alpha a_{n} = \alpha \varSigma a_{n}$, siendo $\alpha$ una constante.

Y las sumas tenemos una formula que es:
$\varSigma_{n=1} x^{n}=\frac{1}{1-x} - 1$. El (-1), lo obtenemos de $x^{0}$, es decir el primer n.

Ejemplo:
$\varSigma_{n\geq2} (-\frac{1}{3})^{n}=\varSigma_{n=0}(\frac{-1}{3})^{n}-[(\frac{-1}{3})^{0}+(\frac{-1}{3})^{1}]=\frac{1}{1+\frac{1}{3}}-(1-\frac{1}{3})=\frac{1}{12}$.
