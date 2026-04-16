---
title: Estudio de Sistemas combinacionales
description: 
published: true
date: 2026-04-16T16:46:28.803Z
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
#### Sumadores
Consiste en un circuito lógico que nos permite llevarnos acarreos si hiciera falta cuando tenemos que una suma es 2.

El circuito completo lo que hace es sumar 3 cosas:
- Un primer bit A
- Un segundo bit B
- Un tercer bit Acarreo entrante

Esto nos permite hacer usarlo tantas veces como lo necesitemos, sin ningún problema.

Si intentaramos hacer este tipo de sumadores con mapas de karnaugh, tenemos el problema de que no contemplamos correctamente el XOR.

El problema de este sistema es que es bastante lento a la hora de encadenar distintos accareos.
#### Resta
Lo vamos a hacer mediante Complemento a 2, recordemos del tema 1. Esto lo haremos porque la facilidad que nos otorga es que podemos sumar valores negativos sin necesidad de hacerlos negativos.

Para ello haremos:
- Invertir los valores A y B
- Activar el acarreo 1.

Con esto podemos hacer las sumas de acarreo 
#### Comparadores
Los comparadores podemos hacerlo de varias maneras con:
- 1 Salidas: Usadas para comparar directamente dos valores sabiendo que queremos obtener.
- 3 Salidas: Donde podemos obtener si son iguales o mayores o menos uno respecto al otro.

Sin embargo el problema real viene cuando queremos comprobar valores enteros

### ALU
Como ya sabemos, la ALU es la Unidad Aritmético Lógica, donde la serie mas conocida es la 74XXX. Por ejemplo las ALU 74181 puede llegar a hacer 16 operaciones lógicas, dependiendo de los bits de selección.

Toda operación airmético-lógica se basan en la suma así que se podría diseñar una ALU modificando entradas al sumador.
- Un ampliador aritmetico: Lógica de modificación utilizadas en las operaciones aritméticas.
- Un ampliador lógico: Logica utilizada en las operaciones.
### Codificador / Decodificador
Un codificador, consiste en un circuito combinacional con varias entradas y salidas, dodne generalmente en un instante.
Este tipo de codificadores pueden ser:
- Con prioridad, donde puede haber mas de una entrada activada existiendo prioridad entre ellas.
- Sin prioridad, donde solo admite una entrada activada.


Por otro lado los decodificadores, lo que hace es según la salida que queramos activar, dejará el resto a 0. Es como si estuvieramos haciendo mapas de karnaugh pero alreves. Este tipo de componentes suele traer una salida llamada Enable, para habilitar el uso del componente.

### Multiplexores/Demultiplexores
Los multiplexor(MUX) consiste en un bloque combinacional con $p$ entradas de control, $2^p$ entrada de datos y solo una salida. Lo que hace realmente es de toda las entradas que da, elegir una unica salida. Hace como un control.

Los multiplexores lo usamos para aplicar una función de complemementación (como los mapas de Karnaugh).

Por otro lado los demultiplexores, son auqellos componentes que hacen lo contrario.

### Dispositivos lógicos programables
Estos dispoitivos, sustituyen aplicaciones a circuitos como SSI (Pequeños) o MSI (Medianos), ya que ocupan incluso menos, necesitan menos unidades y su coste es menor.

Estos dispositivos nos permite hacer funciones de computación, hay tres tipos:
- SPLD: Los más antiguos que nos permiten funciones sencillas.
- CPLD: Nos habilita a complementar funciones más complejas.
- FPGA: Son los más complejos, que nos permite incluso complementar un procesador entero.

Algunas dispositivos lógicos porgramables pueden ser:
- La memoria: Con una capacidad de $n$ entradas de dirección, $m$ salidas de datos y $mx2^n$ celdas de memoria (bits). Si estas memorias no se modifican se llaman memorias $ROM$.