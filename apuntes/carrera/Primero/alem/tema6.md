---
title: Espacios vectoriales
description: 
published: true
date: 2025-11-27T20:08:30.271Z
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
Podemos decir que un subespacio vectorial no es mas que un espacio vectorial dentro de otro, que nos permite sumar y hacer el producto, sin necesidad de salir a otro.
### Ecuaciones del subespacio vectorial
Las ecuaciones del subespacio vectorial la haremos siguiento el siguiente orden:
- Dado un vector como generador de vectores, es decir $u=L\{(2,1,-1,3),(1,-1,2,1)\}$, lo primero que haremos será encontrar el rango o que son independientes para poder hacer base.
- Tras calcular el rango, lo que haremos será llamarlo formalmente como base, es decir: $B_{u}=L\{(2,1,-1,3),(1,-1,2,1)\}$.
- Podemos decir que: $(x,y,z,t)\in u$, si y solo si $rg\{(2,1,-1,3),(1,-1,2,1),(x,y,z,t)\}=2$, y para que esto se cumpla, se debe cumplir que $det\{(2,1,-1),(1,-1,2),(x,y,z)\}=0$ y $det\{(2,1,3),(1,-1,1),(x,y,t)\}=0$, según nuestro determinante anterior para calcular el rango, añadimos los terminos independientes para poder formar un sistema de ecuaciones.

Una vez hayamos desarrollado el determinante, tenemos:
$(x,y,z,t)\in u$, si y solo si $\{4x-5y-3z=0||4x+y-3t=0\}$, un sistema de ecuaciones.

Para comprobar que es correcto, simplemente sustituimos los vectores que teniamos al principio en el sistema y debe salir 0.
### Formar nuevos subespacios vectoriales
Para poder formar nuevos subespacios vectoriales, debemos operar con la suma y la intersección, similar a los conjuntos con la unión y los intersección.

### Intersección
Para poder hacer una intersección entre dos subespacios vectoriales, lo que vamos a buscar es hacer los sistemas cartesiano de ambas y unirlas. Ejemplo:

Dado $u_{1}=[(1,1,1),(0,1,2)]$ y $u_{2}=[(1,2,1),(1,0,2)]$ en $(\mathbb{Z}_{3})^{3}$, tenemos primero que pasa sistemas cartesianos, es decir con $u_{1}$, le hacemos forma escalonada reducida $u_{1}=[(1,0,2),(0,1,2)]$, que en un sistema es igual que poner $u_{1}=\{x=\alpha || y=\beta || z=2\alpha + 2 \beta\}$.
Si resolvemos esto nos sal que $u_{1}=x+y+z$, y si hacemos lo mismo con $u_{2}$ obtenemos:$u_{2}=x+2y+z$.

La intersección será entonces:
$u_{1}\cap u_{2}=\{x+y+z=0 || x+2y+z=0\}$, si resolvemos (Forma escalonada) nos saldrá que es $u_{1}\cap u_{2}=\{x+z=0 || y=0\}$, es decir cualquier elemento formado por $x=2\alpha,y=0,z=\alpha$, va a estar en la intersección.

### Suma
Para poder hacer una suma entre dos subespacios vectoriales, lo que vamos a buscar es hacer los sistemas generadores de ambos y unirlos. Ejemplo:

Dado $u_{1}=\{x+z+t=0 || x+y+t+z=0 || y+t=0\}$ y $u_{2}=L[(1,0,1,0,0),(1,1,1,0,1)]$ en $(\mathbb{Z}_{2})^{5}$.
Debemos pasar $u_{1}$ a sistema de generadores, para ello hacemos la forma escalonada y resolvermos el sistema, como hicimos anteriormente. La unica diferencia es que le daremos valores.

Una vez tengamos ambos como generadores de vectores, lo que haremos será unirnos para poder formar una nueva matriz. $B_{u_{1}+u_{2}}=\{(1,0,0,1,0),(0,1,0,0,0),(0,0,1,1,0),(0,0,0,0,1)\}$, pasamos esta matriz, la resolvemos y obtenemos que $B_{u_{1}+u_{2}}=x+y+t=0$.

## Suma directa $\oplus$
La suma directa surge cuando unicamente podemos hacer 1 unica forma de obtener cada valor. Se puede resumir en que $u_{1}\cap u_{2}=\{0\}$.

Y si recordamos los conjuntos, tenemos: $dim(u_{1}+u_{2})=dim(u_{1})+dim(u_{2})-dim(u_{1}\cap u_{2})$, por lo tanto sabiendo la dimensiones de los conjuntos y la unión, podemos dar con el de la diferencia.
## Subespacio complementario
Lo podemos definir como aquello que le falta a un espacio. Es decir para formar un subespacio necesitamos $V=u\oplus w$. Donde $w$ es el espacio complementario de $u$.

Para calcularlo, normalmente lo haremos usando generadores de vectores, y le calcularemos aquellos vectores que le faltán para hallar la base del espacio dado.

## Aplicaciones lineales
Dado que $K$ es un cuerpo, y $V$,$V'$dos espacios vectoriales, tenemos que:
$f:V \rightarrow V'$ es lineal siempre y cuando cumpla:
- f preserva sumas, para cualesquiera $u,v \in V$ se tiene que $f(u+v)=f(u)+f(v)$.
- f presenta producto por escalares. Para cualesquiera $u\in V$, y cualesquiera $\alpha \in K, f(\alpha*u)=\alpha*f(u)$.

Usaremos de momento, que para ser lineales deben ser de grado 1.
Al haber suma y prodcuto de combinaciones lineales, tenemos una aplicacion lineal.

### Operaciones
Podemos tanto sumar como hacer el producto de aplicaciones lineales y es exactamente igual que con los vectores. 

Sin embargo tenemos la composiciones lineales, que consiste en:
$g o f(u)=g(f(u))$, donde aplicaremos lo que hace $g$ a cada vector o parte del $f(u)$.
### Determinación
Lo podemos definir como auqellos datos concretos que nos permite conocer el resto de vectores.