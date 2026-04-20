---
title: Modelos de distribuciones discretas y continuas
description: 
published: true
date: 2026-04-20T16:06:33.017Z
tags: 
editor: markdown
dateCreated: 2026-04-20T15:45:04.104Z
---

# Modelos de distribuciones discretas y continuas
## Distribución Binomial

Este tipo de distribución analiza gran parte de fenomenos aleatorios en la vida real, donde se mide normalmente con la probabilidad de éxito y la probabilidad de fracaso. (Siendo exito $P[éxito]=p$ y la de fracaso $P[fracas]=1-p$. Aquí suele entrar experminetos que se realizan n veces cada una siendo independiente a la anterior.

Sea $X \leadsto B(n,p)$ tenemos que se define como:
$P[X=x] = \frac{n}{m}p^x (1-p)^{n-x}= \frac{n!}{x!(n-x)!}p^x(1-p)^{n-x}$.
## Distribución de Poisson
La distribución de Poisson, es similar a la binomial, sin embargo la diferencia viene dada enq ue imponemos un límite de tiempo.
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
## Aproximaciones entre las distribuciones
## Distribuciones asociadas a la ley Normal