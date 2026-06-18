---
title: Resumen para Examen
description: 
published: true
date: 2026-06-18T11:02:32.705Z
tags: 
editor: markdown
dateCreated: 2026-06-18T10:37:37.720Z
---

Aquí puedes tener una zona de apuntes rapidos para distintos temas.
# Álgebras de Boole
De este apartado debemos saber hacer:

## Boole y caracteristicas
La álgebra de boole es una conjunto $B$ que tiene operaciones binarias suma y producto.
Propiedades importantes:
- Idempotencia: $x+x=x$ y $x*x=x$.
- Dominación: $x+1=1$ y $x*0=0$.
- Doble complementario: $\overline{\overline{x}}=x$.
- Leyes De Morgan: $\overline{X*Y}=\overline{X}+\overline{Y}$ y $\overline{X+Y}=\overline{X}*\overline{Y}$.

## Expresión booleana
Las expresiones booleanas las construimos en base a literales (1 o 0) y recurrentes (+ *). Estas expresiones pueden ser dadas en:
- Minterms: Conjunto de valores de una expresión que recopila información en función de $F^n$ que hace que la cumpla. Con los minterms podemos escribir la Forma Normal Disyuntiva ($xy+\overline{X}y$).
- Maxterms: Es el contrario de los minterms, con esto podemos hacer la Forma Normal Conjuntiva ($(x+y)(\overline{X}y)$).

## Simplificación de circuitos

- Mapas de Karnaugh: "Tabla donde marcamos aquellos valores que cumplen con la función dada" obtenemos los minterms.
- Quine-McCluskey: Método dedicado a la optimización de funciones booleanas para sacar minterms. "Colocamos todos los valores en una columna agrupados según cuantos 1 tengamos, a la derecha de esta fila, iremos comprobando en grupos de mayor a menor cantidad de 1 si lo hay una diferencia de 1 valor, en caso de que existe esta diferencia la pondremos a la derecha escribiendo "-", en el posición donde difiere. Tras todo esto obtenemos una serie de valores, tras esto hacemos una tabla, donde por columna está los minters y por fila estará los valores obtenidos. 
> Recomendable mirar en los apuntes si se tiene mucha duda, no es viable representarlo en estos apuntes.
{.is-info}

# Lógica proposicional
En este apartado, ya hemos deberiamos haber entendido como funciona la Álgebra de Boole, ahora nos toca jugar con ellas para llegar a los que nos pide.

En este apartado, nos suelen pedir:
- Dada X cantidad de formulas, demostrar que es tautología.
- Dada X cantidad de formula, demostrar que Y es consecuencia lógica.
- Nos dan un texto y debemos traducirlo a lenguaje proposicional.

## Interpretaciones
Es vital saber esta parte:
- Tautología, si $I(\alpha)=1$ para **TODA** interpretación.
- Contradición, si $I(\alpha)=0$ para **TODA** interpretación.
- Satisfacible, si $I(\alpha)=1$ para alguna interpretación.
- Refutable, si $I(\alpha)=0$ para alguna interpretación.
- Contigente, es tanto satisfacible como refutable.

## Simbolos
- Disyunción $\wedge$, se lee como $\alpha$ y $\beta$.
- Conjunción $\vee$, se lee como $\alpha$ o $\beta$.
- Negación $\neg$, se lee como no $\alpha$.
- Implicación $\rightarrow$, se lee como $\alpha$ implia a $\beta$. Se puede traducir a $\alpha \rightarrow \beta = \neg \alpha \vee \beta$.
# Lógica de Predicados
# Unificación y Resolución
# Inducción y Recurrencia
# Grafos
