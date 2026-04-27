---
title: Interferencia estadística
description: 
published: true
date: 2026-04-27T16:34:25.522Z
tags: 
editor: markdown
dateCreated: 2026-04-27T15:37:10.907Z
---

# Inferencia estadística
## Introducción
No es posible el estudio de toda la población por motivos de destrución de la población, o por motivos economicos, entre otros.
Es por ello que tomamos la Muestra, que es un subconjunto de individuos de la población.

Sobre esta muestra:
- La describimos sus datos.
- Extraemos conclusiones sobre la población.

Con la inferencia estadística, lo que hacemos es estimar los valores que queremos sacar sobre esta muestra, mediante unas herramientas como:
- Estimación puntual: Estimación de un parámetro mediante un valor.
- Intervalos de confianza: Intervalo donde se encuentra el parámetro con cierta probabilidad.
- Constrastes de hipótesis: Verificar si una afirmación es plausible sobre la población.
## Muestreo aleatorio simple
Una muestra aleatoria simple $(m.a.s.)$, debe cumplir:
- Todos los individuos tienen la misma probabilidad de ser seleccionados.
- La selecciones son independientes.
- Todas las muestras de tamaño $n$ son equiprobables.

El plan es:
$Población \rightarrow \text{n individuos} \rightarrow muestra \rightarrow observaciones$.

## Estimación mediante interferencia estadística
Son parametros que no requieren que sean conocidos.
- Media muestral: $\overline{X}=\frac{1}{n}\sum x_i$. Ojo, $û=\overline{X}$, ya que û es la medía poblacional.
- Cuasivarianza muestral: $s²_{n-1}=\frac{\sum x^2_i-nx^2}{n-1}$, similar a $\widehat{\sigma²}=s^2_{n-1}$.
- Proporción muestral: $p = \frac{x}{n}$, siendo $x$ el número de éxistos y $n$ el tamaño de la muestra.

## Distribuciones en el muestreo de poblaciones Normales
A menos que la distribución del muestreo sea similar a la Normal, no podemos hacer una distrubicón de forma sencilla. Sin embargo gracias al Teorema Central del Dímite, nos permite el transformarlo o aproximarloa  una normal.

Ahora vamos a resumir las siguientes distribuciones estadísitcas muestrales:
- Media muestral
- Cuasivarianza muestral.
- Proporción muestral.
- Diferencia de medias muestrales.
- Cociente de varianza muestrales.
- Diferencia de proporciones muestrales.

Todas estas formulas se van a proporcionar en el examen.
## Intervalos de confianza mediante interferencia paramétrica
### Intervalos de confianza para una distribución Normal
### Intervalos de confianza para una distribución Normal