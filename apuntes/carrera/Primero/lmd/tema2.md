---
title: Lógica proposocional
description: 
published: true
date: 2026-04-07T14:07:29.022Z
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
## Consecuencia lógica
Un conjunto de formulas, peude ser satisfacible si existe una interpretación que valga 1. Por otro lado, si no se le llamaría insatisfacible.

Aunque cada fórmula se puede satisfacer por ella misma, el conjunto puede no serlo. 

Es hacer tablas de verdad separando en cada apartado los distintos conjuntos y si tenemos en todos un 1, entonces se cumple la consecuencia lógica.


A las fórmulas del conjunto se le llama hipótesis/premisas/antecendentes (El conjunto en sí), por otro lado a cada fórmula que pertenezca se le puede llamar conclusión/tesis/consecuente. Si el conjunto es vacío, y solo tenemos $/alpha$ en el conjunto, entonces $/alpha$ es una tautología.

No es recomendable hacer tablas de verdad, ya que no es una solución eficiente al problema.

Hay un teorema que es:
$\gamma \vDash \alpha$ si y sólo si $r \cup \{-\alpha\}$ es insatisfacible.

## Forma clausular
Un literal, es una proposición atómica o su negada, lo representamos con el simboló $\lambda$ y su negado es $\lambda^c$.
Si $\lamda=p$ entonces $\lambda^c = \neg p$.

Una cláusula es una distyuncion de literales, en la que no pueden estar un literal y su negado a la vez. Es decir un conjuntos de literales.

Los procesos que tenemos que hacer para resolver este tipo de ejericcios es reducir todo a and o or. Para ello debemos saber que:
$a \rightarrow b = \neg a \cup b$.
$a \leftrightarrow b = a \rightarrow b \cap b \rightarrow a$.

El SAT nos presenta un problema muy complejo, que es para obtener un algoritmo eficiente que dado un conjunto de cláusulas es satisfacible o no.


Cuando tengamos un problema de insatisfacibilidad, podemos separar los distintos $OR$ para poder saber si es o no insatisfacible un problema.

### Algoritmo de Davis-Putnam
Es necesario conocer algunos algunos conceptos:
- Una cláusula unit es aquella formada por un único literal por ejemplo $C=p$ o $C=\neg p$.
- Un literal puro $\lambda$ es un conjunto de cláusulas, donde $\lambda$ solo aparece de una unica manera, o siendo true o siendo false.
- Si $C$ es una cláusula y $\lambda$ un literal, denotamos por $C-\lamda$ a la cláusula $C$ sin el literal $\lambda$.

Una vez dado un conjunto de cláusulas y obtenido un literal, podemos descompener esas tres clausulas según el literal dado de la siguiente manera:
$A_\lambda$: Cláusulas que tienen a $\lambda$.
$A_\lambda^c$: Clausulas que tienen a $\lambda^c$.
$B_\lambda$: Las demás, es decir no tienen ni $\lambda$ ni $\lambda^c$.

Tras esto podemos obtener el nuevo conjunto de clausuras de la isguiente manera:
Unimos las clausuras de $B_\lambda$ con aquellas que son $A_\lambda^c$ - \lambda$.

Esto seguimos haciendo reduciendo el conjutno de clausuras hasta poder determinar si es o no satisfacible. (Llegar al conjunto vacío o no)