---
title: Apuntes rápidos para el segundo parcial de calculo
description: 
published: true
date: 2025-12-14T17:14:41.759Z
tags: 
editor: markdown
dateCreated: 2025-11-26T19:36:19.487Z
---

# Apuntes rápidos para el primer parcial de calculo
## Limites famosos
### Cuando tiende a infinito
$\lim_{x\rightarrow \infty}x^{\frac{1}{x}}=1$.

$\lim_{x\rightarrow 0?}x^{x}=1$.

$\lim_{x\rightarrow \infty}(1+x)^{\frac{1}{x}}=e$.

$\lim_{x\rightarrow \infty}\frac{log(1+x)}{x}=1$.

### Cuando tiende a cero
$\lim_{x\rightarrow 0}\frac{sen(x)}{x}=1$.

$\lim_{x\rightarrow 0}\frac{tg(x)}{x}=1$.

$\lim_{x\rightarrow 0}\frac{arctg(x)}{x}=1$.
## Ejercicios tipo
### Cálculo de la Imagen de la función
### Comprobar una desigualdad entre funciones 
$[f(x)\leq g(x),\forall\in I]$.
### determinar el nº de soluciones de una ecuación
$f(x)=g(x)\Leftrightarrow f(x)-g(x)=0$.
### Calculo de limites
Suele haber mucha "morralla", es por elloq ue se recomienda limpiar
### Optimización
# Teoremas obligatorios
## Teoremas sobre funciones
### Teroema de los ceros de Bolzano / Teorema de Bolzano
El teorema de bolzano nos dice que si una función definida en un intervalo cerrado y acotado ($f:[a,b]\rightarrow \mathbb{R}$), y en este intervalo se puede producir: $f(a)*f(b)<0$. Existe un valor $c$, perteneciente al intervalo $[a.b]$, tal que $f(c)=0$.

Matemáticamente se escribe como:
$f:[a,b] \rightarrow \mathbb{R}, \text{ siendo f continua y } f(a)*f(b)<0$, entonces $\exist c \in [a,b] \text{ t.q. } f(x)=0$.

Para poder usar mejor el teorema de Bolzano, describiremos su versión general que dice:

Una función continua, que puede estar definida en intervalo abierto, y cuyos $\lim_{x\rightarrow a}f(x)*\lim_{x\rightarrow b}f(x)<0$, entonces existe un punto $c$, que hace 0 la función. ($\exists \text{ c}\in \text{ }]a,b[ \text{ t.q. }f(c)=0$.

### Terorema del valor intermedio (T.V.I.)
El teorema del valor intermedio dice: "Toda función continua lleva intervalo en intervalos". Es decir, una función continua, dentro de un intervalo (Dominio), lleva otro intervalo (Imagen).
$f:I\rightarrow \mathbb{R} \text{ continua en }I \Rightarrow f(I)=\{f(x):x\in I\}\text{ es otro intervalo}$.

### Teorema de Weierstrass (Propiedad de compacidad)
Es primo hermano del anterior, sin embargo hay una diferencia. En este caso debemos tener si o si un intervalo cerrado y acotado inicial.

Por lo que el teorema de Weiestrass: Partiendo de una función con intervalo cerrado y acotado, el conjunto imagen debe ser también un intervalo cerrado y acotado.
$f:[a,b] \rightarrow \mathbb{R} \text{ continua} \Rightarrow f([a,b])$.

Como resultado podemos obtener que $f([a,b])=[m,M]$, donde m y M son mínimo y máximos absolutos respectivamente, y lo podemos obtener con $m=f(x_{o})$.

## Teoremas sobre derivadas
### Teorema del Valor Medio (T.V.M.)
Sea $f$ una función continua en un intervalo compacto, que es derivable según el teorema del valor medio, dice que existe un punto $c$ en el intervalor $a,b$ tal que cumple:$f'(c)=\frac{f(b)-f(a)}{b-a}$, esto representado geometricamente, decimos que calculamos un angúlo que en algún punto de la función "roza" la función.

Escrito lo anterior matematicamente es: $f:[a,b]\rightarrow \mathbb{R}, \text{f continua en }[a,b],\text{f derivable en }]a,b[ \Rightarrow \exists c \in ]a,b[ \text{ t.q. }f'(c)=\frac{f(b)-f(a)}{b-a}$.

### Teorema de Rolle
El teorema de rolle nos dice que:
Sea f una función en un intervalo compacto, derivable en el intervalo **y** siendo $f(a)=f(b)$, provocando que existe algún punto de la función es igual a cero.

Matematicamente es: $f:[a,b]\rightarrow \mathbb{R}, \text{f continua en }[a,b],\text{f derivable en }]a,b[, f(a)=f(b) \Rightarrow \exists c\in ]a,b[ \text{ t.q }f'(c)=0$.

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

### Polinomio de Taylor
El polinomio de taylor nos sirve para poder aproximar funciones, matematicamente lo escribimos de la siguiente manera:
$f:I\rightarrow \mathbb{R},a\in I,n\in \mathbb{N} (n\geq 2), \exists f^{n}(a)$.
Para el polinomio de taylor necesitamos 3 cosas:
- La función.
- Un valor.
- Hasta cuanto vamos a derivar, o también llamado orden de derivación.
Esto es devido a que el polinomio de taylor toma la siguiente forma:
$Tn(x)=f(a)+f'(a)(x-1)+\frac{f''(a)}{2!}(x-a)^{2}+\frac{f'''(a)}{3!}(x-a)^{3}+\frac{f^{n}(a)}{n!}(x-a)^{n}$.
### Teorema de Taylor
El teorema de Taylor, nos permite poder controlar el error que se comete cuando hacemos el polinomio de Taylor, para ello deberemos hacer:
$f(x)-Tn(x)$.
La diferencia entre la función y la expresión de Taylor nos dará el error.

Describimos el teorema de taylor como:
$f:I\rightarrow \mathbb{R},a\in I,n\in \mathbb{N}, \exists f^{n+1}(x)$.
Sea $x\in I$, entonces $\exists \text{c  t.q  }a\dots c\dots x$, (los puntos que hay entre a, c y x) nos dice que existe un valor c que está entre a y x, pero no sabemos en que orden.

El teorema de Taylor, ($Rn$), tiene la siguiente forma: $Rn=\frac{f^{n+1}(c)}{(n+1)!}(x-a)^{n+1}$, es básicamente buscar uno más que el n.


## Teorema Fundamental del Cálculo ($T.F.C.$)
Para definir el teorema fundamental del cálculo (y usarlo), debemos primero fijarnos en que la función sea continua en todo el intervalo, y además de aquello donde esté definido sea derivable. 

La fórmula es la siguiente:
$F(x)=\int_{h(x)}^{g(x)}f(t)dt=\int_{g(x)}^{a}f(t)dt - \int_{a}^{h(x)}f(t)dt$, donde $a$ es una constante.