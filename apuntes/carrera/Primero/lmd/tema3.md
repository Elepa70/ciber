---
title: Lógica de Predicados
description: 
published: true
date: 2026-04-15T15:03:06.025Z
tags: 
editor: markdown
dateCreated: 2026-04-15T13:38:24.930Z
---

# Lógica de predicados

Los cuantificadores, es lo que ha provocado desarrollar está lógica.

La lógica detras del enunciado es:
$\text{ser\_persona}(x),\text{ser\_mortal}(x),\forall x (\text{ser\_persona(x)}\rightarrow \text{ser\_mortal(x)})$. Si $\text{ser\_persona(Sócrates)}$, entonces $\text{ser\_mortal(Sócrates)}$.
## Elementos del lenguaje de primer orden
Ahora vamos a ver los elementos que componen esta lógica.
### Alfabeto
El alfabeto es el lenguajd e primer orden en la sintaxis que vamos a usar, y tiene cuatro conjuntos finitos:
- C: Símbolos constantes.
- V: Variables.
- F: Símbolos de función.
- R: Símbolos de relación o de predicado.

Además:
- Tenemos los elementos conectores
- Símbolos de paréntesis y coma
- Cunatificador universal ($\forall$) y existencial ($\exist$).

A cada símbolo de una función o símbolo del predicado, se le asocia un número natural, que se llama **aridad**. 

### Términos y fórmulas atómicas
Sea $(C,V,F,R)$ un alfabeto de un lenguaje de primer orden. Podemos definir el conjunto de terminos T como:
- Los elementos de C y V son términos.
- Si $f\inF$ con aridad $n$ y $t_1...t_n$ son términos, entonces $f(t_1...t_n)$ son términos.
- Las palabars que no se hayan construido de esta manera NO son términos.

### Lenguaje de primer orden
Es aquel lenguaje que requiere un alfabeto de primer orden, construido por palabras con:
- Fórmula atómica es una palabra de F.
- Si $\alpha \text{ y } \beta$ están en F, y $x$ es una varibale, entonces su unión, disyunción... también lo estarán.

## Semántica del lenguaje de primer orden

La interpretaciones de la fórmulas de primer orden es más complicada. Dado un alfabeto de un lenguaje de primer orden, una estructura de este lenguaje tiene los siguientes elementos:
- Conjunto vacío, o dominio y universo.
- Aplicaciones $C\rightarrow D$.
## Equivalencia lógica
## Consecuencia lógica
## Formas normales