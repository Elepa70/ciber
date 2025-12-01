---
title: Derivabilidad
description: 
published: true
date: 2025-12-01T19:32:57.919Z
tags: 
editor: markdown
dateCreated: 2025-11-12T19:17:02.392Z
---

# Derivabilidad
La derivabilidad la definimos como:
- Una función es derivable en un punto a, si y solo si, existe el cociente incremental en a
- En forma matematica es: $f:I \rightarrow \mathbb{R},a \in I$, $f \text{ es derivable en }a \Leftrightarrow \exists \lim_{x\rightarrow a} \frac{f(x)-f(a)}{x-a}=f'(a)$.

Sin embargo, cuando hablamos de funciones, decimos que:
$\exists f'(a) \Leftrightarrow \exists f'(a_{-}) \text{ y }\exists f'(a_{+}) \text{ y son iguales}$.
Es decir, solo existe la función cuando en el intervalo dado, es definida, pero debemos tener en cuenta una condici´´on muy necesaria para que sea derivable, y es que sea continua, por eso podemos decir:
$\exists f'(a) \Rightarrow f$ es continua.

Pero esto no implica que si f es continua, exista derivada en ese punto.

## Interpretación geométrica de f'(a)
La derivada de la función la interpretaremos con la ecuación tangente que es: $y=mx+n$ o $y=f(a)+f'(a)(x-a)$. Donde $f'(a)$ es la pendiente de la recta tangente a la grafica de una función f en el punto protagonista dado "a".

## Reglas de derivación
Estas son de repaso.
### Suma
La derivada de la suma es la suma de las derivadas.
$(f+g)'(a)=f'(a)+g'(a)$.

### Producto
La derivada del producto es:
$(fg)'(a)=f'(a)*g(a)+f(a)*g'(a)$.

### Cociente.
La derivada del cociente es:
$(\frac{f}{g})'(a)=\frac{f'(a)+g(a)-f(a)+g'(a)}{(g(a))^{2}}$.

### Composición
La derivada de la suma es la suma de las derivadas.
$(fog)'(a)=g'(f(a))*f'(a)$.

## Extremos absolutos de relativos
Decimos que la función $f$ alcanza en $a$ un máximo relativo cuando:
- $a$ es un punto interior, $a \in I \Leftrightarrow \exists S>0,]a-S,a+S[$.
- $f(a)\geq f(x), \forall x \in ]a-S,a+S[$.

Con los mínimos relativos es al contrario, es decir $f(a)\leq f(x)$.

### Condición necesaria
$f$ alcanza en $a$ un extremo relativo $\Rightarrow f'(a)=0$, o cuando existe un punto a en la derivada que es critico.
> La existencia de extremos relativos no implica extremos absolutos ni viceversa. Sin embargo un extremo absoluto en $a\in I$ si implica un extremo relativo en $a$.
{.is-danger}

## Teorema del Valor Medio (T.V.M.)
Sea $f$ una función continua en un intervalo compacto, que es derivable según el teorema del valor medio, dice que existe un punto $c$ en el intervalor $a,b$ tal que cumple:$f'(c)=\frac{f(b)-f(a)}{b-a}$, esto representado geometricamente, decimos que calculamos un angúlo que en algún punto de la función "roza" la función.

Escrito lo anterior matematicamente es: $f:[a,b]\rightarrow \mathbb{R}, \text{f continua en }[a,b],\text{f derivable en }]a,b[ \Rightarrow \exists c \in ]a,b[ \text{ t.q. }f'(c)=\frac{f(b)-f(a)}{b-a}$.

## Teorema de Rolle
El teorema de rolle nos dice que:
Sea f una función en un intervalo compacto, derivable en el intervalo **y** siendo $f(a)=f(b)$, provocando que existe algún punto de la función es igual a cero.

Matematicamente es: $f:[a,b]\rightarrow \mathbb{R}, \text{f continua en }[a,b],\text{f derivable en }]a,b[, f(a)=f(b) \Rightarrow \exists c\in ]a,b[ \text{ t.q }f'(c)=0$.

## Caracterización de monotonía
$f:I\rightarrow \mathbb{R}$ es una función derivable en el intervalo $I$.
Tenemos lo siguiente:
- $f$ es creciente $\Leftrightarrow f'(x)\geq 0$.
- $f$ es decreciente $\Leftrightarrow f'(x)\leq 0$.
- $f$ es constante $\Leftrightarrow f'(x)= 0$.
- $f'(x)>0, \forall x \in I \Leftrightarrow$ f es estrictamente creciente.
- $f'(x)<0, \forall x \in I \Leftrightarrow$ f es estrictamente decreciente.

En el caso que tengamos que  $f'(x)\neq 0, \forall x \in I$, entonces f es estrictamente monotona.

## Concavidad y Convexida
Convexa es "cara feliz" y concava al reves.

Si tenemos una función que es dos veces derivable y $f'(a)=0$:
- Si $f''(a)>0 \Rightarrow$ f tiene un mínimo relativo en a.
- Si $f''(a)<0 \Rightarrow$ f tiene un máximo relativo en a.
## Regla de L' Hôpital
La regla de L'Hôpital se divide según la indeterminación que tengamos.
### 1º Regla de L' Hôpital
La usaremos para resolver la indeterminación del tipo ["$\frac{0}{0}$"], para se debe cumplir:
Dado un intervalo $I$, y sean $f,g: I/\{a\}\rightarrow \mathbb{R}$.
- $f\text{ y }g$ son derivables.
- $\lim_{x\rightarrow a}f(x)=\lim_{x\rightarrow a}g(x)=0$.
- $g'(x)\neq 0$, cerca de a.
### 2º Regla de L' Hôpital
La usaremos para resolver la indeterminación del tipo ["$\frac{\infty}{\infty}$"] o ["$\frac{?}{\infty}$"], donde $?$ es un valor no determinado o dificil de hacerlo, para se debe cumplir:
Dado un intervalo $I$, y sean $f,g: I/\{a\}\rightarrow \mathbb{R}$.
- $f\text{ y }g$ son derivables.
- $\lim_{x\rightarrow a}g(x)=\infty$.
- $g'(x)\neq 0$, cerca de a.
## Polinomio de Taylor
El polinomio de taylor nos sirve para poder aproximar funciones, matematicamente lo escribimos de la siguiente manera:
$f:I\rightarrow \mathbb{R},a\in I,n\in \mathbb{N} (n\geq 2), \exists f^{n}(a)$.
Para el polinomio de taylor necesitamos 3 cosas:
- La función.
- Un valor.
- Hasta cuanto vamos a derivar, o también llamado orden de derivación.
Esto es devido a que el polinomio de taylor toma la siguiente forma:
$Tn(x)=f(a)+f'(a)(x-1)+\frac{f''(a)}{2!}(x-a)^{2}+\frac{f'''(a)}{3!}(x-a)^{3}+\frac{f^{n}(a)}{n!}(x-a)^{n}$.

Por otro lado tenemos el teorema de taylor
### Teorema de Taylor
El teorema de Taylor, nos permite poder controlar el error qu ese comete cuando hacemos el polinomio de Taylor, para ello deberemos hacer:
$f(x)-Tn(x)$.
La diferencia entre la función y la expresión de Taylor nos dará el error.

Describimos el teorema de taylor como:
$f:I\rightarrow \mathbb{R},a\in I,n\in \mathbb{N}, \exists f^{n+1}(x)$.
Sea $x\in I$, entonces $\exists \text{c  t.q  }a\dots c\dots x$, (los puntos que hay entre a, c y x) nos dice que existe un valor c que está entre a y x, pero no sabemos en que orden.

El teorema de Taylor, ($Rn$), tiene la siguiente forma: $Rn=\frac{f^{n+1}(c)}{(n+1)!}(x-a)^{n+1}$, es básicamente buscar uno más que el n.