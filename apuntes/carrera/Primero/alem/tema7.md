---
title: Aplicaciones lineales
description: 
published: true
date: 2025-12-03T10:48:28.083Z
tags: 
editor: markdown
dateCreated: 2025-12-03T10:48:28.083Z
---

# Aplicaciones lineales
Dado que $K$ es un cuerpo, y $V$,$V'$dos espacios vectoriales, tenemos que:
$f:V \rightarrow V'$ es lineal siempre y cuando cumpla:
- f preserva sumas, para cualesquiera $u,v \in V$ se tiene que $f(u+v)=f(u)+f(v)$.
- f presenta producto por escalares. Para cualesquiera $u\in V$, y cualesquiera $\alpha \in K, f(\alpha*u)=\alpha*f(u)$.

Usaremos de momento, que para ser lineales deben ser de grado 1.
Al haber suma y prodcuto de combinaciones lineales, tenemos una aplicacion lineal.

## Operaciones
Podemos tanto sumar como hacer el producto de aplicaciones lineales y es exactamente igual que con los vectores. 

Sin embargo tenemos la composiciones lineales, que consiste en:
$g o f(u)=g(f(u))$, donde aplicaremos lo que hace $g$ a cada vector o parte del $f(u)$.
## Determinación
Lo podemos definir como auqellos datos concretos que nos permite conocer el resto de vectores.

## Matriz de una apliación lineal
Podemos obtener la información de una aplicación gracias a la matriz. Para poder hacer esta matriz vamos a usar este ejemplo:
Dada una aplicación $f(x,y)=(2x-y,-x+3y)$,  y hacerlo con $B=\{(1,2);(2,1)\}$ y $B'=\{(1,3);(1,2)\}$.
Lo que buscamos es $M_{B,B'}(f)$.
1. Usamos el primer vector $(1,2)$.
1. Calculamos su imagen con $f(x,y)$, que nos da $(0,5)$.
1. Ahora calculamos en B' con $(0,5)$, que lo haremos: $(0,5)=\alpha(1,3)+\beta(1,2)$, es decir obtenemos una sistema de ecuaciones del siguiente estilo: $\alpha+\beta=0 || 3\alpha+2\beta=5$. Obtenemos $\alpha=5 \text{ y }\beta=-5$, por lo que la primera columna de la matriz es $(5,-5)$.
### Obtención de valores
> Por entender.
{.is-warning}
## Cambio de base
El cambio de base lo haremos practicamente igual a como lo haciamos con los vectores. Debemos hacer multiplicaciones entre las matrices pero con el orden inverso.
## Composición de aplicaciones
Basicamente donde empieza una función comienza la otra. 
Ejemplo:

# Nucleo e imagen
## Nucleo
Definimos $N$ como $N(f)=\{u\in V:f(u)=0\}$ y la imagen como de f como $Im(f)=\{f(u):u\in V\}$.
