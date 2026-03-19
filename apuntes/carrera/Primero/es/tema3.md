---
title: Teoría de la probabilidad
description: 
published: true
date: 2026-03-19T18:50:06.801Z
tags: 
editor: markdown
dateCreated: 2026-03-17T18:08:55.097Z
---

# Teoría de la probabilidad
## Introducción
Recordemos que hablamos de fenómenos donde están los:
- Determinísticos: Repetido indefinidas veces, siempre da lo mismo.
- Aleatorios: Repetido indefinidas veces, da resultados diferentes y no previsibles.

Para esto último se encarga el cálculo de probabilidades con definición: Aborda el estudio de los experimentos aleatorios a través de la asignación de un modelo matemáico que resuma la esencia aleatoria de dichoe experimento.

## Espacio muestral $\mathbb{E}$.
Es aquel conjunto de todos los posible resultados de un experimento aleatorio.

Según sea el conjunto de resultados de experimento aleatorio, puede ser:
- Discreto: Conjunto finito o infinito numerable.
- Continuo: Conjunto no numerable.

## Sucesos
Los sucesos son los subconjuntos del espacio muestral cuyos elementos tienen alguna característica común. Se denota como letras mayúsculas.

Existe:
- Suceso elemental: Es cada uno de los resultados indivisibles de un experimento aleatorio.
- Suceso seguro: Siempre ocurre, es el propio espacio muestral.
- Suceso imposible: No contiene ningún suceso elemental del experimento.

## Operaciones con sucesos.
- Inclusión $(A\subseteq B)$ A está incluido en B. Es decir al pasar A entonces ocurre B.
- Unión $(A\cup B)$: Formado por sucesos que pertenecen a ambos.
- Intersección $(A \cap B)$: Formado por aquellos elementos que están simultaneamente en ambos sucesos.
- Complementario $(\bar{A})$: Formado por aquellos elementos de $\mathbb{E}$ que no están en A.
- Diferencia $(A-B)$: Formado por aquellos elementos que cumple $A\cap \bar{B}$.
- Incompatible: No puede ocurirr a la vez

## Propiedades de las operaciones
- Asociativa: $(A\cup B) \cup C = A \cup (B \cup C)$, con intersección: $(A\cap B) \cap C = A \cap (B \cap C)$.
- Comutativa: $A\cup B = B \cup A$, con intersección: $A\cap B = B \cap A$.
- Elemento neutro: $A \cup 0 = A$, con intersección: $A \cap E = A$.
- Distributiva: $A \cup (B \cap C) = (A\cup B) \cap (A\cup C)$ y $A \cap (B \cup C) = (A\cap B) \cup (A\cap C)$
- Leyes de Morgan: $\overline{(A\cup B)}= \overline{A}\cap \overline{B}$, con intersección $\overline{(A\cap B)}= \overline{A}\cup \overline{B}$