---
title: Derivabilidad
description: 
published: true
date: 2025-11-13T20:25:58.222Z
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