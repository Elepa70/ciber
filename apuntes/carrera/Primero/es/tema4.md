---
title: Conceptos básicos de variables aleatorias
description: 
published: true
date: 2026-03-24T18:20:03.469Z
tags: 
editor: markdown
dateCreated: 2026-03-24T16:34:39.538Z
---

# Conceptos básicos de variables aleatorias
## Introducción
Las variables aleatorias representan un conjutno de valores que pueden observarse al realizar un experimento aleatorio, sy obre los cuales es posible establecer una medida de su probabilidad. El ejemplo más básico es cara o cruz al lanzar una moneda.
## Tipo de variables
Tenemos dos tipos de variables aleatorias.
- Variables aleatorias discretas: Es un número finito o entero de valores.
- Variable aleatoria continua: Donde se puede tomar cualqueir valor o intervalo.

## Distribución de probabilidad
La distribución de probabilidad de una variablea aleatoria, es una función matemática que asigna probabilidades a vavlores de dicha variable.
- Función de densidad: Depende del tipo e variable tenemos, función masa de probabilidad (para discretas) o función de densidad (continuas).
Para masa de probabilada la formula es: $p(x_i)=P[X=x]=p_i$.
Para función de densidad: $\int f(x)dx=1$.
- Función de distribución: Dependiendo del tipo de dato, solo cambia la forma de calcularlo, pero no el nombre.
En discreta: $F(x)=P[X\leq x]=\sum_{x_{i}\leq x}p(x_i)=\sum_{x_{i}\leq x}P[X=x]$.
En continuas: $F(x)=P[X\leq x]=\int f(t)dt$.

Para poder calcular las probabilidades con una variable aleatoria discreta X, lo que se hace es sumar las probabilidades correspondientes a valores de X comprendido entre A y B. POr otro lado con las continuas, lo que hayq ue hacer es calcular el área bajo la curva acotada entre a y b.

## Esperanza matemática
Sea $X$ una v.a. discreta con función masa de probabilidad $p(x)$, y sea $g(X)$ una función de dicha v.a. Definimos los valores esperados como:
$E[X]=\sum x_i *p(x_i)$.

Esto es para discretas para continua es casi igual:
$E[X]=\int x*f(x)dx$.

Las propiedades son:
- Siempre es constante.
- Si está actoada entre dos valores, la esperanza tambien lo estará.
- Si $X$ es simétrica respecto a un valor, entonces la esperanza es ese valor.

## Varianza
La varianza es la medida de dispersión que nos permite conocer el grado de dispersión de los valores.

La desviación tipica de una varianza viene con la siguiente formula:
$\sigma_X =+\sqrt{Var[X]}$.

Para calcular la Varianza, dependemos de si es discreta o continua, como siemmpre.
Discreta: $Var[X]=E[X-E[X]]^2=\sum (x_i - E[X])^2 *p(x_i)$.
Continuas: $Var[X]=[X-E[X]]^2=\int (x-E[X])^2 *f(x)dx$.