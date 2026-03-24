---
title: Lógica proposocional
description: 
published: true
date: 2026-03-24T15:21:36.389Z
tags: 
editor: markdown
dateCreated: 2026-03-18T15:17:06.592Z
---

# Lógica proposicional
La lógica de proposcional sirve para elementos sencillos es decir, verdadero o falso.

La definición es:
- Partiendo de un alfabeto como conjunto finito.
- Una palabra sobre el alfabeto, es una concatenación de letras.
- Un lenguaje sobre el alfabeto elegido, un conjunto de palabras.

En nuestro caso, el alfabeto que vamos a usar será $X$ con operadores $\cap \cup \rightarrow \leftrightarrow \text{ buscando el simbolo...}$.

Por ejemplo, considernado que $X=\{p,q\}$ entonces algunas palabras pueden ser: 
- $p$.
- $p \cup q$.
- $p \rightarrow q\cup p$.

### Simbolos:
- Disyunción $\cap$, se lee como $\alpha$ o $\beta$. Ambas deben ser verdad.
- Conjunción $\cup$, se lee como $\alpha$ y $\beta$. Una debe ser verdad.
- Negación $\text{simbolo por descubirr...}$, se lee como no $\alpha$. 
- Implicación $\rightarrow$, se lee como $\alpha$ implica a $\beta$. Es vedad siempre y cuando no pase que alpha sea verdad y beta no.
- Equivalencia $\leftrightarrow$, se lee como $\alpha$ equivale a $\beta$. Es verdad cuando ambos valores se cumplen o es verdad o es negación.

En cuanto a la prioridad de los simbolos, es la siguiente:
- Primero va la negación ().
- Segundos va $\cup$ y $\cap$, teniendo la misma prioridad.
- Después van $\rightarrow$ y $\leftrightarrow$, tienen siempre la misma prioridad, dependiendo parentesis.

Cuando haya más de un $\rightarrow$, va de derecha a izquierda.

### Subfórmulas
Las subformulas son aquellas formulas que intervienen en otra.
Por ejemplo:
- Si $\alpha = \beta_{1} \cup \beta_{2}$, entonces $Sub(\alpha)=\{\alpha\}\cup Sub(\beta_{1}) \cup Sub(\beta_{2}$.

### Interpretraciones
Una interpretación es dar un valor de verdad, a cada una de las proposiciones atómicas que hay. Lo hacemos descomponiendo las premisas que nos dan mediante:
- Ponemos los valores de cada lado de la unión mediante sumas y después ponemos la multiplicación de todo junto.
- Para separar la intersección, simplemente lo dividimos en sus interpretacioens.
- Los negativos lo que hacemos es interpretarlo como 1- algo.

Ejemplo:
$a\cup (b\cap -c = I(a)+I(b\cap -c) + I(a)I(b\cap -c) = I(a) + I(b)I(-c) + I(a)I(b)I(c)=I(a) + I(b)(1-I(c)) + I(a)I(b)(1-I(c))$.

Dentro de las interpreatciones tenemos:
- Tautología: Si $I(\alpha)=1$ para TODA interpretación, siempre es cierto.
- Contradicción: Si $I(\alpha)=0$ para TODA interpretación, nunca es cierto.
- Satisface: Si $I(\alpha)=1$ para ALGUNA interpretación, puede o no ser cierto.
- Refutable: Si $I(\alpha)=0$ para ALGUNA interpretación, puede no ser cierto.
- Contingente: Se satisface y es refutable.