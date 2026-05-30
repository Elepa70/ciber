---
title: Contrastes de hipótesis
description: 
published: true
date: 2026-05-30T10:35:18.810Z
tags: 
editor: markdown
dateCreated: 2026-05-30T09:45:07.342Z
---

# Constraste de hipótesis
## Constraste de hipótesis paramétricos
Debemos definir algunos datos:
Formulación del problema:
- Hipótesis nula $(H_o)$. Es la hipótesis que planteamos sobre el parámetro o característica de la población. Representa la situación de referencia o ausencia de efecto.
- Hipótesis alternativa $(H_1)$. Es la hipótesis opuesta a la nula. Contiene los posibles valores del parámetro no incluiods en $H_0$. 

Estadístico experimental (o de contraste): Nos permite tomar la decisión sobre la hipótesis planteada.

Región de **NO** rechazo. Consjunto de valores del estadístico de contraste en el que **NO** se rechazará la hipótesis nula.

Región crítica. Conjunto de valores del estadístico de contraste en el que se rechazará la hipótesis nula.


### Errores de hipotesis
- Error tipo I. Rechazar la hipótesis nula siendo esta cierta, se denota con $\alpha$.
- Error tipo II. No rechazar la hipótesis nula siendo esta falsa, se denota con $\beta$.

### Regla de decisión
La decisión se basa en el valor del estadístico de contraste, denorada por $S$ el conjutno de valores que puede tomar el estadístico de contraste.
Este conjunto se divide en dos regiones disjuntas:
$S= R\cup \neg{R}$.
$R\cap \neg{R}=0$.
Donde: 
- $R$ es la región crítica.
- $neg R$ es la región de no rechazo.

> Existe una "regla" que dice "no se puede rechazar $H_0$, ya que un contraste de hipótesis se buscan evidencias en contra de $H_0$, no para demostrar su veracidad.
{.is-info}
## P-Valor
El **p-valor** es el **menor nivel de significación $\alpha$**, donde se rechazaría la hipótesis nula $H_o$. Se mide:
- $p-valor=P[\text{resultado tan extremo como el observado} | H_0 \text{ cierta}]$, es decir:
- $p-valor=P[estadístico de contrastes \geq valor observado | H_0 \text{ cierta}]$
## Constraste de hipótesis no paramétricos