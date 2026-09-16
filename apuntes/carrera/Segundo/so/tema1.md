---
title: Estructuras de sistemas operativos
description: 
published: true
date: 2026-09-16T16:36:24.970Z
tags: 
editor: markdown
dateCreated: 2026-09-16T15:49:04.526Z
---

# Estructuras de sistemas operativos
## Recordatorio de TOC y FS
En este primer apartado, nos dedicamos a recordar lo que hemos dado el año pasado.

Durante esta asignatura vamos a también usar la abstracción como hemos visto en PDOO. 
Esto es importante ya que en SO y en HW, hay bastante poca abstracción y vamos a ir viendo porque se da esto.

Los módulos de Entrada y Salida, se comunican el controlador de dispositivos (Device controller), que este a su vez se comunica con el dispositivo.

Por otro lado la CPU usa varios registros, en los que tenemos PC (programa counter, que usa las siglas del siguiente programa) y IR (Es aquel que esta siendo ejecutado en ese momento). Los registros de memorias de la CPU, tenemos:
- MAR: Contiene la dirección de la siguiente R/W. 
- MBR: Contiene los datos que van a escribirse en memoria.
- I/O AR: Son los registro de dirección de E/S.
- I/O BR: Son los registros de buffer de E/S
> Importante los dos primeros.
{.is-info}

Dentro de los registros de la CPU tenemos:
### Registros de CPU de propósito general
Se acceden por programas y clasificarlo en registros de datos. Los más importantes son registros índice, puntero a segmento y puntero a la pila (Este último tiene el BP que es el principio de la PIla y el SP que es el fin de la pila).
### Otros registros de CPU
Tenemos:
- Programa Counter (PC): Dirección de la siguiente ejecución.
- Instruction Register (IR): Última instrucción que se fué a usar.
- Program Status Word (PSW): Información de códigos de condición. Tenemos el modo de ejecución OO (Kernel, unicamente por el SO), 01 (Modo User). También tenemos los entry points que existe las: Interrupciones, excepciones y Llamadas al sistema (Provocadas por el SO o por nosotros).

> El concepto de máquina desnuda es aquel que se define como: Todo repertorio por instrucción microprocesador (NO SIRVE ENSAMBLADOR), puede acceder a toda la memoria y solo permite E/S a bajo nivel.

Tras esto tenemos la memoria principal o la RAM.

Todos estos modulos estan conectadas entre ellas mediante buses donde destacamos:
- Control Bus
- Address bus
- Data bus
## Componentes de un SO

## Estructuras/Arquitecturas de los SOs

## SOs de propósito específico
