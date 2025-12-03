---
title: Integración
description: 
published: true
date: 2025-12-03T19:49:31.175Z
tags: 
editor: markdown
dateCreated: 2025-12-03T19:49:31.175Z
---

# Integración
Antes de ver la integración, vamos a explicar la integral de Riemann para entender la necesidad de integrar.
## Integración de Riemann
La integración de Riemann es una forma antigua que se tenia para poder calcular el area de una superficie. Este area se hacia creando distintos rectangulos de la misma anchura debajo de la función, y calculando el area del rectangulo formado. La suma de todos los rectangulos era el area total.

Sin embargo, esto traia un problema, y es que cuanto mas finos sean los rectangulos, más sumas hay que hacer, pero más preciso es el area.

Se definia de la siguiente manera $lim\sum (J,P)=\int_{a}^{b}f(x)dx$.

## Condición de integral
Debe cumplirse lo siguiente:
- Si hay continuidad, hay integral
o
- Si hay monotonia, hay integral.

## Propiedades
Algunas propiedades básicas.
1. $\int_{a}^{b}(f+g)(x)dx=\int_{a}^{b}f(x)dx+\int_{a}^{b}g(x)dx$.
2. $a \in \mathbb{R} \int_{a}^{b}af(x)dx= a\int_{a}^{b}f(x)dx$.
3. Si $f\leq g$ entonces $\int_{a}^{b}f(x)dx \leq \int_{a}^{b}g(x)dx$.
4. Si $f\geq 0$ entonces $\int_{a}^{b}f(x)dx \geq 0$.
5. Propiedad de adictividad.  $\int_{a}^{b}f(x)dx= \int_{a}^{c}f(x)dx+\int_{c}^{b}f(x)dx$.

## Reglas de Barrow
Antes, vamos a definir la primitiva de una función.
- G es una primita de f $\Leftrightarrow \exist G'(x)=f(x),\forall x \in I$.

### Teorema (Regla de Barrow)
Lo definimos de la siguiente manera.
$f:[a,b]\rightarrow \mathbb{R}$ intervalo y $G$ es una primitiva de $f$.
Entonces: $\int_{a}^{b}f(x)dx=G(b)-G(a)=G(x)]^{b}_{a}$.
### Versión general
Lo definimos de la siguiente manera.
$f:]a,b[\rightarrow \mathbb{R}$ intervalo y $G$ es una primitiva de $f$, y $\exists \lim_{x\rightarrow a} G(x) \text{ y } \exists \lim_{x\rightarrow b} G(x)$.

Entonces: $\int_{a}^{b}f(x)dx=\lim_{x\rightarrow b} G(x) - \lim_{x\rightarrow a} G(x)$.

También se le puede decir Integrales impropias.