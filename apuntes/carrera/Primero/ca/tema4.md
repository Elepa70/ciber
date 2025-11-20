---
title: Derivabilidad
description: 
published: true
date: 2025-11-20T19:31:38.626Z
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