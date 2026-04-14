---
title: Modelos de distribuciones discretas y continuas
description: 
published: true
date: 2026-04-14T16:45:33.453Z
tags: 
editor: markdown
dateCreated: 2026-04-14T15:35:45.347Z
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
$P[X=x]=\frac{\lambda^x e^-\lambda}{x!}.
- La esperanza es $E[X]=\lambda$ y su varianza es $Var[X]=\lambda$.
## Distribución de la Normal
