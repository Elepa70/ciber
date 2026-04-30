---
title: Estudio de sistemas sencuenciales
description: 
published: true
date: 2026-04-30T16:06:34.840Z
tags: 
editor: markdown
dateCreated: 2026-04-30T15:36:58.212Z
---

# Estudio de sistemas sencuenciales
## Concepto de sistemas secuenciales
La salida de un instante, dado depende de la secuencia de entradas recibida hasta dicho instante. (Historia del sistema). Los sistemas con **memoria**, son aquellos que recuerdan algo.

Vamos a tener tres variables:
- Entradas
- Salidas
- Estados


## Elementos básicos secuenciales
Los elementos básicos de almacenamiento, que se pueden memorizar en un bit de información, son:
- Cerrojos (latches)
- Biestables (flip-flops)

Los elementos básicos de almacenamiento coincide la salida con el estados.

- Sistemas secuenciales síncronos: Es aquel en el que los cambios de estado en el sistema se producen únicamente cuando se producen cambios en una señal especial de entrada.
- Sistemas secuenciales asíncronos: Es aquel en el que los cambios de estado se producen cuando cambia alguna entrada.


LLos elementos de las puertas asíncronos, son en realidad dos puertas NOR o NAND retroalimentadas.

Vamos a usar sobretodos dos tipos de tablas:
- Tablas de estados: Salidas que se producen para cualquier combinación de entrada.
- Tablas de excitación: Entradas que hay que proporcionar para obtener un cambio de estado.

Una señal de reloj, es una señal cuadrada periódica que se suele utilizar para sincronizar el comportamiento de la mayoría de los sistemas digitales. Estas señales las implementamos con un Biestable SR sincronizado, añadiendo una tercera entrada "Clk", que habilita o inhabilita la actualización del valor Q.

A su vez es importante distinguir entre entradas:
- Sincronas: Dependientes del reloj
- Asincronas: Dependiente de otros factores, como puede ser el botón de resteo del equipo.