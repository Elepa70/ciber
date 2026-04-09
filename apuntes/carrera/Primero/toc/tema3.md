---
title: Estudio de Sistemas combinacionales
description: 
published: true
date: 2026-04-09T16:11:52.404Z
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
Vamos a ver otro tipo de componentes que también sirve para circuitos pero con un nivel más complejos. 

Cuando intentamos introducir este tipo de circuitos lógicos con los que tenemos, llegamos a que todo es inmanejable, para ello es necesario describir el comportamiento mediante:
- Procesamiento de datos.
- Enturatmiento de datos.
- Almacenamiento de datos.


Un ejemplo de estos componentes puede ser la ALU del tema anterior, donde las tabla de verdad pueden llegar a tener 16.384 filas, con 8 ecuaciones booleanas y 14 variables.

Existe unos bloques funcionales que relaizan distintas tareas y pueden ser primitivas según su nivel de registro:
- Componentes combinacionales: No tienen memoria y son lo que vamosa  ver en este tema.
- Componentes secuenciales: Registro, contadores. Se dará en el tema siguiente.
### Sumadores
Consiste en un circuito lógico que nos permite llevarnos acarreos si hiciera falta cuando tenemos que una suma es 2.

El circuito completo lo que hace es sumar 3 cosas:
- Un primer bit A
- Un segundo bit B
- Un tercer bit Acarreo entrante

Esto nos permite hacer usarlo tantas veces como lo necesitemos, sin ningún problema.

Si intentaramos hacer este tipo de sumadores con mapas de karnaugh, tenemos el problema de que no contemplamos correctamente el XOR.