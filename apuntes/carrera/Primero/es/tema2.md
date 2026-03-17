---
title: Estadística descriptiva bidimensional
description: 
published: true
date: 2026-03-17T16:57:57.489Z
tags: 
editor: markdown
dateCreated: 2026-03-09T16:40:14.952Z
---

# Estadística descriptiva bidimensional
Hay situaciones donde la información a medir no depende de una única variable, si no que es de un conjunto de ellas. Por ejemplo, cuando hablamos de un producto, podemos mas o menos entender la varíación del precio debido a la venta de ese producto.

## Definición
Cuando tenemos dos variables, debemos tener en cuenta:
- Existencia o no de asociación.
- Fuerza de la asociación.
- DIrección de la asociación.
- Naturaleza de la asociación.

Para hacer las tablas de frecuencias lo que hacemos es exponer un caso X y uno Y y sacar su frecuencia n. Así con cada aspecto.

## Distribución marginales
Las distribuciones marginales son las obtenidas al estudiar por separado cada una de las variables que componen la variable bidimensional.
ç
La marginal de X es la distribución de todas las observaciones que hay en X independientemente de las de Y.

## Distribuciones condicionadas
Las distribuciones condicionadas corresponden al estudio de una variable cuando la otra está presente. Cada distribución condicionada será, por tanto, una distribución unidimensional.

Todo lo tipo de calculos son iguales que los que se han hecho en unidimensional.

## Independencia estadística
Diremos que $X$ e $Y$ son independientes, si no existe ningún tipo de relación entre ambas variables.
Para que sean independientes se debe cumpler el **teorema de caracterización de la Independencia**. 
$X\text{ e }Y \text{ son independientes }\Leftrightarrow n_{ij}=\frac{n_{i}*n_{j}}{n}\text{, para todo }i\text{ y para todo }j$.

Lo que hacemos basicamente es multiplicar cada valor que está en los extremos de filas y columnas y lo dividimos netre n. El valor debe ser el mismo que está antes.

## Covarianza
La covarianza es un numero que nos permite saber is existe o no una relación lineal entre las variables. En caso de que si exista, no sindica para que crecen o decrecen.

La formula es:
$\sigma XY=\frac{1}{n}\sum_{i=1} \sum{j=1} x_{i}*yi_{i}*n_{ij}-\overline{X}*\overline{Y}$.

Dependiendo el valor podemos saber lo siguiente:
- Si $\sigma XY>0$ exite relación lineal o positiva. Las dos crecen o decrecen a la vez.
- Si $\sigma XY <0$, existe relación lineal inversa o negativa. Van en sentido contrario el crecimiento.
- Si $\sigma XY =0$, entonces no hay relación lineal entre ellas. Puede o no haber relación pero no está incorreladas. 

Propiedades:
- $\sigma XX=\sigma^{2}$ la covarianza de una variable y de sí misma es igual a la varianza de la variable.
- $\sigma XY = \sigma YX$ Es la misma covarianza dando igual el orden.
- Si la variable son independientes entonces $\sigma XY = 0$.
- Si $\sigma XY \neq 0$ entonces $X$ e $Y$ no son independientes.
- $\text{Independencia }\Rightarrow \text{ Incorrelación}$.
- $\text{Incorrelación }\Nrightarrow \text{ Independencia}$.

## Coeficiente de correlación lineal simple
Este coeficiente nos sirve para medir el sentido y el grado de intensidad, de la relación dada entre dos variables.
$r_{XY}=\frac{\sigma XY}{\sigma X * \sigma Y}$.

Interpretación del signo:
- $-1$: Relación lineal perfecta negativa.
- $-1<r_{XY}<0$: Relación negativa, cuanto más proximo sea al -1 más perfecta será.
- $0$: Ausenscia de relación lineal.
- $0<r_{XY}<1$: Relación positiva, más fuerte cuanto más proximo esté al 1.
- $1$: Relación lineal perfecta positiva.

Cuando hagamos este coeficiente, debemos escribir lo siguiente:
"Grado de asociación lineal entre las dos variables <grado>, además la relaciçon es <simbolo>."
  
Para saber el grado debemos tener en cuenta si está en estos valores:
-	Perfecta: $+-0.96 , +-1.0$.
-	Fuerte: $+-0.85 , +-0.95$.
-	Significativa: $+-0.70 , +-0.84$.
-	Moderada: $+-0.50 , +-0.69$.
-	Perfecta: $+-0.20 , +-0.49$.
-	Perfecta: $+-0.10 , +-0.19$.
-	Perfecta: $+-0.09 , +-0.0$.
  
  