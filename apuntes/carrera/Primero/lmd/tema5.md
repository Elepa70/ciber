---
title: Inducción y recurrencia
description: 
published: true
date: 2026-05-19T14:18:54.147Z
tags: 
editor: markdown
dateCreated: 2026-05-13T13:35:32.770Z
---

# Inducción y recurrencia
## Principio de inducción
Si $A$ es un subconjunto de $\mathbb{N}$ verificando:
- $0 \in A$.
- $\text{Si }n \in A \text{ entonces }n+1\in A$.
Entonces $A=\mathbb{N}$.

Se peude enunciar de forma más general que:
- El mínimo de $A$ es $k$.
- Si $n \in A$ entonces $n+1 \in A$.
Por lo tanto $A=\{k,k+1,k+2,\dots\}
> Lo mismo que en calculo.
{.is-info}

Demostrar que una propiedad es cierta haciendo:
- Caso base: DEmostrando que se cumple en P(k).
- Hipotesis de induccion: Suponer que P(k), P(k+1) es cierto.
- Paso inductivo: Debemos demostrar que P(k), P(k+1).

## Recurrencia
Una función reccurrente ( recursiva) es aquella que se llama a si misma.

Continuamos con el esquema de:
- Caso base, es el caso número uno.
- Caso general, a partir de casos más pequeños.

Una recurrencia lineal, homogénea y de coeficientes constantes es una del tipo:
$a_0t_n+a_1t_{n-1}+a_2t_{n-2}+a_3t_{n-3}+a_kt_{n-k}=0$