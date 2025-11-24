---
title: Espacios vectoriales
description: 
published: true
date: 2025-11-24T11:12:38.681Z
tags: 
editor: markdown
dateCreated: 2025-11-18T19:29:56.655Z
---

# Espacios vectoriales
## Definición y explicación
### Definición
Dado un cuerpo $K$ y un conjunto $V$, decimos que $V$ tiene estructura de espacio vectorial sobre $K$ (tambiñen se puede decir K-espacio vectorial), si en $V$ podemos hacer dos operaciones.
1. La suma: $VxV\rightarrow V$, que es lo mismo que $(u,v) \rightarrow u+v$.
1. El producto: $KxV\rightarrow V$, que es lo mismo que $(\alpha ,u) \rightarrow \alpha *u$.

SI $K$ es un cuerpo, consideramos el conjunto $K^{n}=\{(x_{1},x_{2},\dots , _{n}) : x_{i} \in K\}$. Donde la suma y el producto por escalares se realiza:
$(x_{1},x_{2},\dots , x_{n})+(y_{1},y_{2},\dots , y_{n}) = (x_{1}+y_{1},x_{2}+y_{2},\dots , x_{n}+y{n})$.
$a*(x_{1},x_{2},\dots , x_{n})= (a*x_{1},a*x_{2},\dots , a* x_{n})$.

Todo polinomio, como las matrices, son espacios vectoriales.

Una serie de propiedades que tenemos de los espacios vectoriales es que:
- $0*u=0$.
- $\alpha *u=0$.
- $\alpha *u=0$ implica que $\alpha = 0 \text{ o }u=0$. 
- Si $\alpha*u=\beta *u$ y $u \neq 0$ entonces $\alpha = \beta$.
- Si $\alpha*u=\alpha *v$ y $\alpha \neq 0$ entonces $u = v$.

### Combinaciones lineales
Con lo declarado anteriormente, y siendo $u_{1},u_{2},u_{n},v \in V$, decims que $v$ es combinación lineal de los vectores $u_{1},u_{2},u_{n}$, si existen $\alpha_{1},\alpha_{2},\alpha_{n} \in K$, tal que $v=\alpha_{1} * u_{1}+ \alpha_{2} * u_{2}+ \dots + \alpha_{n} * u_{n}$.

Si $S=\{\u_{1},u_{2},\dots ,u_{n}}$, denotaremos $L(S)$ o por $L[u_{1},u_{2}, \dots , u_{n}]$.

El conjunto $\{u,v\}$ es linealmente dependeinte si y solo si, uno de los vectores es multiplo del otro.

## Sistemas de generadores
Decimos que los vectores $S$, forman un sistema de generadores de $V$, o que $S$ es un sistema de generadores de $V$, si todo vector de $V$ es combinación lineal de los vectores de $S$. Es decir si $L[S]=V$.

Basicamente, es un conjunto a partir del cual nos permite ir obteniendo los demás vectores, mediante suma y producto. No es necesario que estos vectores sean dependientes entre ellos.

### El rango
El rango nos permite saber dos cosas:
- Si el sistema es linealmente independiente entre si, si el $rg(A)=m$, siendo m, el número de filas.
- Si el sistema es generador de $K^{n}$, si $rg(A)=n$

Con las columnas pasa exactamente lo mismo.

Si al añadir una fila, el rango es el mismo, decimos que hay una combinación lineal.

Para tener un sistema de generadores, necistamos como mínimo $K^{n}$, $n$ vectores, por otro lado para un sistema linealmente independiente debemos tener como máximo $n$.

## Base
Una base es aquello es aquello que cumple independencia linealmente y a su vez que sea un generador, todo espacio vectorial tiene una base.
## Dimensión
Podemos definirlo como cuantos datos necesitamos para determinar un elemento.
El nº de vectores debe tener el mismo nº de vectores, es decir cumplir consigo mismo. Ya que dependiendo del conjunto obtenemos una u otra dimensión.
## Coordenadas de un vector
Un vector se escribe de fomra unica, respecto a los vectores de una base. 

Los vectores, los podemos escribir como base canonica de otro $\{(1,0,0),(0,0,1),(0,0,1)\}$, o respecto a otra base, lo cual nos daría algo como $v=x*(1,1,1),y(2,1,2),z(3,1,3)$, siendo la base que teniamos= $\{(1,1,1),(2,1,2),(3,1,3)\}$.

## Cambio de base
> Por resumir, es confuso todavía.
{.is-warning}

Basicamente son unas operaciones que realizmaos cuando deseamos cambiar la base de una matriz.

## Subespacios vectoriales
Decimos que es un subespacio vectorial, cuando tenemos un espacio cerrado de suma o productos, donde podemos obtener vectores ya definidos.