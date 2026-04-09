---
title: Estudio de Sistemas combinacionales
description: 
published: true
date: 2026-04-09T15:56:24.977Z
tags: 
editor: markdown
dateCreated: 2026-04-09T15:47:00.614Z
---

# Estudio de sistemas combinacionales
## Concepto de sistema combinacionales
Un sistema combinacional, es una función booleana (con entrada 0 y 1). En la vida real, debemos tener en cuenta que los valores pueden cambiar entre el 0 y 1, provocando así que haya un pequeño delay o que funcione en cuestión del tiempo.
## Analisis de sistemas combinacionales
El analisis lo hacemos de dos manera:
- Funcional: mediante mapas de Karnaugh, tablas de verdad o expresiones booleanas.
- Temporal: Donde también conocemos el retardo de reprogramación, es decir, el tiempo que tarda en cambiar de estado.

En los analisis funcional podemos obtener la expresión algebraica mediante una grafica o una tabla de verdad, o alreves.

Sin embargo con el analisis temporal, debemos tener en cuenta también el tiempo, por lo tanto en vez de tener una expresión algebraica completa, podemos representarlo mediante una pequña grafica donde se muestre los cambios de estado y en que momento se hacen.

## Diseño de sistemas combinacionales
Podemos diseñar un circuito a partir de:
1. Tabla de verdad
2. Expresión analítica (Mediante el teorema shannon)
3. La minimilización de la expresión anteriores.
4. Implementación de expresión minima.

Gracias a lo anterior podemos implementar un circuito lógico dependiendo de las expresiones disponibles:
- Cualquier tipo de expresión.
- Expresión mínima de suma de productos (AND/OR o NAND/NAND)
- Expresión mínima del producto de sumas (OR/AND o NOR/NOR)

## Componentes combinacionales estándar
