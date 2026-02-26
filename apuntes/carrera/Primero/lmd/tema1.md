---
title: Álgebra de Boole
description: 
published: true
date: 2026-02-26T12:47:59.017Z
tags: 
editor: markdown
dateCreated: 2026-02-25T11:10:30.264Z
---

# Álgebra de Boole
El primer tema que vamos a tratar, consiste en el Álgebra de Boole.
## Definición
Un Álgebra de Boole es un conjunto $B$ con dos operaciones binarias internas:
- Suma ($+$ o $\cup$)
- Producto ($*$ o $\cap$)

Con estas operaciones se cumplen las propiedades de:
- Asociatividad.
- Conmutatividad
- Elemento neutro (Para la suma es el 0 y para el producto es el 1)
- Existencia de un elemento complementario, es decir, que para $A$ existe un $\overline{A}$ .

### Propiedades
De las anteriores definiciones podemos obtener una serie de propiedades.
- Idempotencia: $x+x=x$ y $x*x=x$.
- Dominación: $x+1=1$ y $x*0=0$.
- Absorción: $x+(x*y)=x$ y $x*(x+y)=x$.
- Propiedad cancelativa: $x+y=x+z$ y cumpliendo $x*y=x*z$, entonces $y=z$.
- Doble complementario: $\overline{\overline{x}}=x$.
- $x+(\overline{x}*y)=x+y$ y $x(\overline{x}+y)=x*y$.
- Leyes De Morgan: $\overline{X*Y}=\overline{X}+\overline{Y}$ y $\overline{X+Y}=\overline{X}*\overline{Y}$.

> Los más importantes a aprender son: Idempotencia, Dominación, Doble Complementario y las Leyes De Morgan, ya que el resto es posible que lo obtengamos de las anteriores.
{.is-info}

Cuando tengamos una propiedad, tenemos que tener en cuenta la **propiedad dual**, donde se hace un intercambio de $+$ y $*$, y también los $0$ y $1$.

> Si una propiedad es cierta, también lo es su propiedad dual.
{.is-success}

### Teorema
> El teorema puede ser confuso, con un ejemplo es más guiado.
{.is-warning}

Si $(B,+,*,0,1,\overline{ })$ y $(T,+,*,0,1,\overline{ })$ son algebras de Boole, entonces $BxT$ es álgebra de Boole.
Entonces podemos hacer:
- Operaciones: $(b_{1},t_{1})*(b_{2},t_{2})=(b_{1}*t_{1},b_{2}*t_{2})$ y $(b_{1},b_{2})+(t_{1},t_{2})=(b_{1}+b_{2},t_{1}+t_{2})$.
- Elemento neutro: $(1,1)$ es elemento neutro para el $*$ y el $(0,0)$ es elemento neutro para $+$.
- Elemento complementario: $\overline{(b,t)}=(\overline{B},\overline{T})$.


#### Ejemplo del teorema
> Puede dar a confusión ya que ha sido copiado y interpretado.
{.is-danger}

Definimos a $B$ como $(B,+,*)$, es decir tenemos verdadero o falso (1 o 0).
Definimos a $B^{2}$ como: $B^{2}=B*B=\{(0,0),(0,1),(1,0),(1,1)\}$.

Esto son todos las posibles combinaciones que podemos hacer con los elementos dados.

Si hacemos las operaciones anteriores, debemos ir con cada elemento con el que ocupa la posición.

> Siempre trabajaremos con un $B^{n}$ donde $n\geq1$.
{.is-info}


## Órdenes
Debemos recordar lo dado en Algebra Lineal.

Un orden parcial en un conjunto P es una relación binaria ($\leq$), que cumple:
- Propiedad reflexiva: Para cualquier $a \in P, a\leq a$.
- Propiedad antisimétrica: Si $a\leq b$ y $b\leq a$ entonces $a=b$.
- Propiedad transitiva: Si $a\leq b$ y $b \leq c$ entonces $a \leq c$.

> Tras esto vemos los diagramas de Hasse, debido a la falta de medios para representarlos, recomiendo acudir a fuentes fiables de Internet.
{.is-info}

## Expresión booleana
Antes de definirlas, vamos a explicar sus caracteristicas:
- Literales: Aquellos elementos que toman como valor true or false (1 o 0), pudiendo ser variables, o complementario de variables.
- Recurrente: Definimos la recurrencia como, si $E_{1}$ y $E_{2}$ son expresiones booleanas, la suma o "or" también lo sera, el producto o "and" también, y el complementario de estos también.

Dada las anteriores definiciones, tenemos entonces que una expresión booleana la construimos en base de las anteriores reglas.

Ejemplo:
Dado $X=\{a,b\}$, entonces $1,a+b,\overline{AB}+b+0$ son expresiones booleanas, donde los literales son $a,\overline{A},b,\overline{B},0 \text{ y }1$.

La tabla de verdad, nos sirve para poder evaluar las expresiones. Aunque puede ser un proceso lento o tedioso, es el mejor metodo existente hasta el momento, ya que si pudieramos encontrar un algoritmo mejor, entonces habríamos resuelto uno de los problemas del millón.

A un conjunto de funciones booleanas en $n$ variables. (Escrito: $F^{n}=\{f:B^{n}\rightarrow B\text{ es función booleana}\}$. Tambiésn es un álgebra de Boole.

Con la particularidad de $F^{n}$ tiene $2^{2^{n}}$ elementos.

