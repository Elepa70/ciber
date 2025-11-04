---
title: Apuntes para el primer parcial de Calculo
description: 
published: true
date: 2025-11-04T10:26:06.565Z
tags: 
editor: markdown
dateCreated: 2025-11-04T10:19:52.029Z
---

# Apuntes rápidos para el primer parcial de calculo
Estos apuntes son para hacer una pasada rapida, no es nada recomendable estudiar de aquí.

## Valores en en $\mathbb{R}$.

$\mathbb{R}^{+} = \{x \in \mathbb{R} : x > 0\}$ : Todos los números reales mayor que 0.

$\mathbb{R}^{-} = \{x \in \mathbb{R} : x < 0\}$: Todos los números reales menores que 0.

$\mathbb{R}^{+} \cup \mathbb{R}^{-} \cup \{0\} = \mathbb{R}$: La unión de todos los números reales mayores que cero, menores que cero y cero, forman todos los números reales.

$\mathbb{R}^{*} = \{x \in \mathbb{R} : x \neq 0\}$: Todos los números reales distintos de 0.

$\mathbb{R}^{+}_{0} = \{x \in \mathbb{R} : x \geq 0\}$: Todos los números reales mayores que 0, incluyendo el 0.

$\mathbb{R}^{-}_{0} = \{x \in \mathbb{R} : x \leq 0\}$:Todos los números reales menores que 0, incluyendo el 0.

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