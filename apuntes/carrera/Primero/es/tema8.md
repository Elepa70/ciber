---
title: Optimización
description: 
published: true
date: 2026-06-05T14:33:30.272Z
tags: 
editor: markdown
dateCreated: 2026-06-05T14:33:30.272Z
---

# Optimización
## Introducción
El objetivo en la optimización sin restriccioens es optimizar una función **f** denominada objetivo. Esta optimización consiste en encontrar los máximos o mínimos de **f**.
> Recordamos que $f''(x)>0$ es un mínimo, y $f''(x)<0$ es un máximo.
{.is-info}

Antes debemos definir una serie de palabras:
- Gradiente de f: $\nabla f(x,y)$, es un vector formado por todas las dariables parciales de f.
- Hessiana de f: $H[f(x,y)]$, es la matriz formada por todas las derivadas parciales segundas de f. El teormea de Schwarz nos asegura la simetría de dicha matriz.
- Menor principal de orden i de la matriz Hessiana $(H_{ixi}[f(x,y)]$, es el determinante de la matriz Hessiana, que se obtiene al suprimir las $n-i$ últimas filas y $n-i$ últimas columnas.
### Caracteristicas de la Hessiana
1. H es definida positiva $\Leftrightarrow H_{ixi} > 0 \forall i$.
2. H es semidefinida positiva $\Leftrightarrow H_{ixi} \geq 0 \forall i$.
3. H es definida negativa $\Leftrightarrow H_{ixi}$ tiene el signo $(-1)^i$.
4. H es semidefnida negativa $\Leftrightarrow H_{ixi}$ tiene el signo $(-1)^i$ o son nulos.
5. H será indefinida en el resto de casos.
## Concavidad y convexidad
Es posible analizar la convexidad/concavidad de una fucnión f analuzando su Hessiana.

1. f es convexa $\Leftrightarrow$ H es semidefinida positiva.
2. f es cóncava $\Leftrightarrow$ H es semidefinida negativa.