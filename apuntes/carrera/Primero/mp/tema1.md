---
title: Punteros y memoria dinámica
description: 
published: true
date: 2026-03-02T17:40:48.533Z
tags: 
editor: markdown
dateCreated: 2026-03-02T17:37:25.989Z
---

# Punteros y memoria din
Vamos a hablar sobre un nuevo tipo de dato llamado puntero.

Solemos tener un problema a la hora de conocer el tiempo de compilación la cantidad de memoria que se va a necesitar para almacenar los datos. El uso de arrays grandes supone un desgato de memoria enorme.

Para ello, existe el tipo de dato puntero, donde nos permite definir los espacios de reserva para el tiempo de ejecución y crear variables en tiempo de ejecución, eso si es responsabilidad del programador.

## Tipo de punteros
Los punteros contiene la dirección de memoria de otro lado, donde existe un tipo de puntero especial llamado dirección nula con valor 0.

La declaración consiste:
```C++
int * ptri; //Declaracion de puntero a entero.
```