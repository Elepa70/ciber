---
title: Unificación y resolución
description: 
published: true
date: 2026-05-05T14:39:37.767Z
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

### Dificultad 1
TOda sustitución se aplica a todos los lados.

### Dificultad 2
Cuando tengamos el mismo literal ambos predicados, debemos tener en cuenta que podemos sustituir cosas.

Por ejemplo:
$Q(f(a),y) \cup Q(y,y) \cup \neg R(x,y)$, si aplicamos $(y|f(a)$ obtenemos, $Q(f(a),f(a))\cup \neg R(x,f(a))$.

Sin embargo, es importante recordar. Para unificar dos literales de distintas cláusulas y calcular una resolvente, se debe renombrar las variables.



### Pasos a resolver
Debemos considerar que tenemos dos formas de resolver:
- Resolvente mediante clasuuslas distintas: Buscamos poder unificarla mediante la sustitución.
- Resolvente mediante misma clausula: Unfiicamos dos clausulas que estén en la misma clausula.

Las estrategias que tenemos para resolver estos ejercicios son:
### Fuerza Bruta
Calcular todas las posibilidades una a una en fuerza bruta.
### Estrategia lineal
Cada resolvente se obtiene de una cláusula obtenida en el paso anterior y otrá cláusula.
### Estrategia lineal-input
Las clausulas que se implementa siempre pertenece al conjunto incial. Aunque este metood es el mas sencillo, no es completo y puede o no encontrarse.
