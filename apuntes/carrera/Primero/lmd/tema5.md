---
title: Inducción y recurrencia
description: 
published: true
date: 2026-05-20T14:40:05.954Z
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
$a_0t_n+a_1t_{n-1}+a_2t_{n-2}+a_3t_{n-3}+a_kt_{n-k}=0$.

## Sucesión recurrente
### Primer metodo
Lo que podemos hacer es sustituir $t_n$ por $x^n$.
Algunos ejercicios que tenemos osn un sistema de ecuaciones dado y después en un punto de la expresión, tenemos que toma valores conforme a $tn_1$. Este tipo de ejercicios lo que buscamos es una expresión que sea capaz de simplifar esta sucesión.

### Segundo metodo
Si no es viable el primeor, cuando tenagmos los raices. Lo que podemos hacer es multilplicar las raices por polinomios de menor grado para ir modificandolo.

Matematicamente:
Si  suponemos que cada $\alpha_i$ tiene una multiplicidad $m_i$. Entonces son soluciones $\alpha^n_i p_i (n)$.

#### NO SE QUE ES
Lineales, no homogéneras y de coeficientes constantes.

Trataremos las de tipo:
$a_0t_n+a_1t_{n-1}+a_2t_{n-2}+a_3t_{n-3}+a_kt_{n-k}=b^n*q(n)$.
donde $b,a_0,...,a_k$ son constantes y $q(n)$ un polinomio de grado $d$.

Hay situaciones, donde un cambio de variable nos otorga mucha ventaja a la hora de buscar las soluciones.
