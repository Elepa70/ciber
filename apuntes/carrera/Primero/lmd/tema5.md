---
title: Inducción y recurrencia
description: 
published: true
date: 2026-05-19T13:37:20.458Z
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
