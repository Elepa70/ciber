---
title: Limites Funcional y Continuidad
description: 
published: true
date: 2025-11-10T19:49:29.996Z
tags: 
editor: markdown
dateCreated: 2025-10-30T19:10:41.192Z
---

# Limite Funcional y Continuidad
## Definición de limite funcional o en un punto

Para definir un limite funcional, no es mas que decir, que un limite existe en una función $f(x)$, cuando le damos valores a la $x$, que sean proximos a $a$, sin que sean $a$. El valor que le damos, debe ser el mismo en ambos lados del punto. 

Es decir, si tenemos una función a trozos donde por un lado vale 12, y por el otro 129548, podemos decir que no se cumple.

> Ojo, si tenemos el caso donde una función en un punto vale otra cosa, pero sin embargo cuando nos acercamos por los limites tenemos el mismo valor. Ejemplo: Una función a trozos, donde si vale $a$, toma un valor de $2$, pero cuando es no $a$, tiene un valor de $213$. Su limite sigue siendo $213$.
{.is-info}


Siempre debe ser el mismo valor al que tienden.

## Limites laterales
Los limites laterales, nos harán falta en aquellos casos donde en una función a trozos, tomamos valores completamnete distintos, y debemos comprobar si efectivamente es el mismo.

Para ello le daremos valores proximos a $a$, por ambos lados (izquierda y derecha), y debe tomar el mismo valor para cumplirlo.
## Limites infinitos
Estos limites también lso conocemos como Asintotas verticales. No es más que cuando un valor toma, un cierto valor en un punto, la función toma un valor proximo al infinito. El mejor ejemplo puede ser $\frac{1}{x}$.

## Limites en el infinito
También conocido como asintotas horizontales, es similar a las verticales pero suceden a lo largo de la función, es decir, el comportamiento de la función cuando toma un valor proximo al infinito.

### Limites en el infinito del infinito
Es una subrama de las asintotas horizontales, donde en vez de que la función tome un valor determinado (como puede ser 0), toma un valor de infinito. El mejor ejemplo puede ser $x$.

## Cálculo de limites
Antes de hacer los calculos de los limites, vamos a tener en cuenta las indeterminaciones:
### Calculo con escala de infinitos
- "$\infty -\infty$"
- "$0-\infty$"
- "$\frac{\infty}{\infty}$"
- "$\frac{0}{0}$"
### Calculo con la regla del número e
- "$1^{\infty}$"

Recordamos que la regla del número e, es:
$(\frac{x+1}{x})^{x}=x((\frac{x+1}{x}-1)$., el resultado es $L$, que es $e^{L}$.
### Calculo con el teorema del número e (O Formula)
- "$0^{0}$"
- "$\infty^{0}$"

Recordamos que el teorema del número e, dice:
$x^{\frac{1}{x}}=e^{\frac{1}{x}*\log(x)}$
## Operaciones con funciones continuas
Al igual que con las series convergentes, podemos operar con funciones continuas siguiendo lo siguiente:
- La suma de funciones continuas, es una función continua.
- El producto de funciones continuas, es una función continua.
- El cociente de funciones es continuo, siempre y cuando el denominador no se anule.
- La composición de funciones es continua, si ambas lo son.

### Ejemplos:
- Podemos encontrar como ejemplos que toda las funciones elementales son continuas.
- La suma de funciones son continuas (funciones = polinomios).
- Toda función racional es continua en su dominio.
- La función $f(x)=|\log(1+e^{x})|, \forall x \in \mathbb{R}$ es continua ya que la composición de funciones lo es.

## Teoremas
Ahora vamos a ver una serie de teoremas importantes.
### Teoremas de los ceros de Bolzano / Teorema de Bolzano
El teorema de bolzano nos dice que si una función definida en un intervalo cerrado y acotado ($f:[a,b]\rightarrow \mathbb{R}$), y en este intervalo se puede producir: $f(a)*f(b)<0$. Existe un valor $c$, perteneciente al intervalo $[a.b]$, tal que $f(c)=0$.

Matemáticamente se escribe como:
$f:[a,b] \rightarrow \mathbb{R}, \text{ siendo f continua y } f(a)*f(b)<0$, entonces $\exist c \in [a,b] \text{ t.q. } f(x)=0$.

Para poder usar mejor el teorema de Bolzano, describiremos su versión general que dice:

Una función continua, que puede estar definida en intervalo abierto, y cuyos $\lim_{x\rightarrow a}f(x)*\lim_{x\rightarrow b}f(x)<0$, entonces existe un punto $c$, que hace 0 la función. ($\exists \text{ c}\in \text{ }]a,b[ \text{ t.q. }f(c)=0$.

### Terorema del valor intermedio (T.V.I.)
El teorema del valor intermedio dice: "Toda función continua lleva intervalo en intervalos". Es decir, una función continua, dentro de un intervalo (Dominio), lleva otro intervalo (Imagen).

$f:I\rightarrow \mathbb{R} \text{ continua en }I \Rightarrow f(I)=\{f(x):x\in I\}\text{ es otro intervalo}$.