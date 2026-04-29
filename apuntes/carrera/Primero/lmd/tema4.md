---
title: Unificación y resolución
description: 
published: true
date: 2026-04-29T15:06:57.355Z
tags: 
editor: markdown
dateCreated: 2026-04-29T14:32:55.294Z
---

# Unificación y reoslución
## Consecuecia lógica
EL mayor problema que tenemos es que: Dado un conjutno de fórmulas $R$, y una fórmula $\alpha$, como sabemos si $R\vDash \alpha$?.

## Sustitución
Sea $\alpha$ un literal, $x$ una variable y $t$ un término. La sustitución elemental de $x$ por $t$ es la transofrmación que cambia cada ocurrencia de $x$ por $t$. Denotado con $\sigma = (x|t)$.

Debemos tener en cuenta que la sustitución se debe aplicar a ambos literales.
La sustitución que hacemos la aplicamos a todos los lados.

## Unificación
Una vez sustituido los literales necesarios, podemos unfiicar estos literales mediante la unfiicación.

## Resolución
> Parte dificil
{.is-danger}

La resolución consiste en partiendo de $\alpha \cup \beta, \not \alpha \cup \gammma$, como resolución es $\beta \cup \gamma$. A menos que lleguemos a una contradicción, ya que en tal caso significa que las clausulas de las que hemos partidos no es resoluble o insatisfacible.


La segunda dificultad, consiste en saber que pasa en una clausula donde aparece un literal dos veces.
