---
title: Diagonalización
description: 
published: true
date: 2025-12-05T11:14:47.910Z
tags: 
editor: markdown
dateCreated: 2025-12-05T11:14:47.910Z
---

# Diagonalización

> Faltan diapositivas, información incompleta.
{.is-warning}

La diagonalización es una nueva manera para ver los cambios de base, donde en vez de:
$M_{B'}(f)=M_{B \rightarrow B'}*M_{B}*M_{B' \rightarrow B}$, tendremos lo siguiente:
$C=P^{-1}*A*P$.

Nuestro objetivo es encontrar como resultado, esa $C$, que tiene forma de matriz identidad. Es decir, solo tiene la primera diagonal con valores.

Para ello hay dos metodos, mediante vectores o mendiante matrices.

Ejemplo:
$f(\mathbb{Z}_{5})^{3}\rightarrow(\mathbb{Z}_{5})^{3}$.
$f(x,y,z)=(2x+3z,2y+4z,4x+y+2z)$.
$B=\{(2,1,1;(1,1,0);(1,3,2)\}$.
¿$M_{B}(f)$?
## Ejemplo - Vectores
Bien, lo primero que haremos será declarar $u_{n}$, para ello diremos que:
$u_{1}=(2,1,1)$.
$u_{1}=(1,1,0)$.
$u_{1}=(1,3,2)$.

Y ahora lo calcularemos en su $f(u_{1})$.
$f(u_{1})=(2*2+3*1||2*1+4*1||2*4+1+2*1) = (2,1,1)$, (hemos puesto el valor del vector en la aplicación).
Como nos podemso fijar, obtenemos el propio $u_{1}$, por lo que podemos decir que es: $1*u_{1}+0*u_{2}+0*u_{3}$.

Si hacemos esto con los demas encontramos lo siguiente:
$f(u_{2})=(2,2,0)$ que es lo mismo que $1*u_{1}+2*u_{2}+0*u_{3}$.
$f(u_{3})=(3,4,1)$ que es lo mismo que $0*u_{1}+0*u_{2}+3*u_{3}$.

Por lo tanto la matriz $M_{B}(f)= 1 ,0 ,0 || 0,2,0 || 0,0,3$, pensarlo en forma de matriz.

## Ejemplo - Matriz
No me queda claro.
> Por rellenar.
{.is-danger}

## Definición
Decimos que f es diagonalizable si existe una base B de forma que $M_{B}$ es una matriz diagonal.
## Valor propio
Llamaremos a $a$ un valor propio, si existe un valorq eu nos ayuda a $f(u)=a*u$.
### Polinomio caracteristico
Para encontrar los valores propios. Tenemos los siguientes metodos:
#### Por vectores
Usaremos que $N(f-a*Id)\neq{0}$, y esto se traduce a que $Pf(a)=det(f-a*Id)$, calcular el indeterminante formado entre la resta de la función y la identidad con el valor propio a calcular.

#### Por matrices
$P_{A}(a)=det(A-a*Id)$, es similar.

> Los valores propios son las raizes obtenidas, es decir igualar a 0.
{.is-success}
