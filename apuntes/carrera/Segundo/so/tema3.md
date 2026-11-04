---
title: Gestión de Memoria
description: 
published: true
date: 2026-11-04T17:05:46.884Z
tags: 
editor: markdown
dateCreated: 2026-11-04T16:34:14.381Z
---

# Gestión de Memoria
## Generalidades sobre gestión de memoria
### Jerarquía de memoria
La jerarquía de memoria viene de:
- CPU
- Cache (L1,L2,L3)
- RAM
- Los buses que comunican entre E/S
- HD



### Conceptos sobre cachés
La memoria chacé es una copia que puede ser accedida más rádiamente que la orgiinal, su objetivo es ser la más eficiente. Existen los terminos de aciertos de caché y fallo de caché (Si el dato se encuentra o no en la caché).

Esto funciona gracias al **principio de localidad**, los programas siguen un patrón y todos los accesos de memorias están contenidas en el mismo "lado".
### Espacios de direcciones y mapa de memoria
Debemos diferenciar entre espacios de direcciones lógicos y físicos:
- Espacios de direcciones lógico: Direcciones lógicas generadas por un programa.
- Espacios de direcciones físicos: Conjutno de direcciones físicas correspondientes a la direcciones lógicas en un instante dado de ejecución.

Cuando representamos un proceso en una imagen, debemos tener en cuenta que se dividen en tres partes principales:
- Tipo: Puede ser texto, código, datos etc etc
- Tamaño: Lo que ocupa cada apartado anterior.
- Offset: Donde empieza cada valor del tipo.
### Objetivos de la gestión de memoria
Vamos a ver varios apartados durante este tema:
- La organización de la memoria, como se divide, con un proceso o varios
- La gestión dada un esqueleto de organización. Ya que podemos tener varias estrategias a seguir para un mayor rendimiento.
- Protección y compartición, donde se busca la seguridad entre usuarios del mismo grupo.

Entrando en más detalle de organización podemos tener:
- Organización contigua (No existe o modelo antiguo): La asignación se hace en un único bloque de memmoria.
- Organización no contigua: Usado habitualmente donde se busca "dividir" el programa. Podemos encontrar paginación, segmentación y segmentación paginada.

La paginación y segmentación sin MV(Memoria Virtual) nos proporciona, que lso programas segmentados no tienen porque estar ubicado de forma contigua, los trozos deben residir en momoria principal durante su ejecución.
### Intercambio (Swapping)
La idea es intercambiar procesos entre memoria principal y auxiliar. Donde el proceso pasará a estado "Suspendido_bloqueado" (dentro del disea más simple) y lo que ocupa espacio en memoria principal, el programa, pasara a disco. 

El planificador (swapper), se encarga de:
- Retirar procesos de la memoria principal.
- Incorporar procesos a la memoria principal.
- Gestionar y asignar espacios de intercambio.
## Memoria virtual. Organización
## Memoria virtual. Gestión
## Gestión de memoria en Linux