---
title: Gestión de Memoria
description: 
published: true
date: 2026-11-04T16:53:27.798Z
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
### Intercambio (Swapping)
## Memoria virtual. Organización
## Memoria virtual. Gestión
## Gestión de memoria en Linux