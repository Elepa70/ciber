---
title: Modelos de distribuciones discretas y continuas
description: 
published: true
date: 2026-04-21T10:04:00.988Z
tags: 
editor: markdown
dateCreated: 2026-04-20T15:45:04.104Z
---

# Modelos de distribuciones discretas y continuas
## Modelos de distribuciones de probabilidad

Estos modelos son encargados de representar el comportamiento de fenómenos diversos. En este apartado 
## Distribución Binomial
Este modelo se usa bastante en la vida real, ya que presenta dos situaciones "éxito" si ocurre el suceso, y "fracaso" si no ocurre.

Cuando usamos esta distribución, debemos tener en cuenta que la porbabilidad de exito no puede alterarse ni modificarse. $X ->B(n,o)$, se define la función masa de probabilidad de una esta manera:
$P[X=x]=(nx)p^x (1-p)^{n-x}$, y su función de distribución:
- $F(x)=P[X\leq x]= \ 0 si x<0 || \sum(ni)p^i(1-p)^{n-i} si 0\leq x< n || 1 si x\geq n$.
- La esperazna es: $E[X]=np$, y su varianza $Var[X]=np(1-p)=npq$.

## DIstribución de Poisson
Mide la probabilidad de un suceso aleatorio a lo largo de un intervalo temporal o espacial. Esto puede ser por ejemplo "Nº de vehículos que llegan a una gasolinera en una hora".

En este caso tenemos que la probabilidad es:
$P[X=x]=\frac{\lambda^x e^-\lambda}{x!}$.
- La esperanza es $E[X]=\lambda$ y su varianza es $Var[X]=\lambda$.
## Distribución Normal
La distribución Normal es la más importante y la más usada. 

Este tipo de distribución se usa normalmente con datos con poca dispersión de datos, ya que tiene una función de densidad sencilla gracias a su derivada es facil.

La función de densidad de la distribución Normal es, on parametros u y $\sigma$:
$f(x)=\frac{1}{\sigma \sqrt{2 \pi}}e^{-\frac{(x-u)^2}{2\sigma ^2}}$.

La esperanza es: $E[X]=u$.
La Varianza es: $Var[X]=\sigma^2$.

La gráfica de la función de densidad de la Normal, tiene una forma peculiar acampanada (por eso se le llama campana de Gauss), que varía según los valores de sigma o de u.

Una curiosidad de esta distribución es que la Media, la Moda y la Mediana está en el mismo punto, es decir en $u$.

Una de los problemas que trae la normal, es que trae infinitos números de distribuciones normales, por ello se ha hecho la Normal estándar o tipificada, para poder operar con todas.

La tipificación normalmente la hacemos mediante la siguiente expresión:
$Z=\frac{X-u}{\sigma}\leadsto N(0,1)$.

Por lo tanto, entonces:
$Fx(x)=P[X\leq x]=P[\frac{X-u}{\sigma} \leq \frac{x-u}{\sigma}]=P[Z\leq \frac{x-u}{\sigma}]=Fz(\frac{x-u}{\sigma})$.


## Aproximaciones entre las distribuciones
## Distribuciones asociadas a la ley Normal