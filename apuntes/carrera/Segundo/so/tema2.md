---
title: Procesos y Hebras
description: 
published: true
date: 2026-09-30T17:20:14.140Z
tags: 
editor: markdown
dateCreated: 2026-09-30T16:41:57.893Z
---

# Procesos y Hebras
## Conceptos fundamentales sobre procesos
Un proceso se define como un programa que esta en ejecución y la ejecución de este programa debe realizarse sin interferencias. Debido a la ejecución de otros programas.
- Un programa es un fichero estático que se puede ejecutar.
- Un proceso es lo mismo que un programa que se esta ejecutando, o un programa y su estado de ejecución.

Toda ejecución de programa es caracterizada por su traza de ejecución. Los distintos procesos peuden ejecutarse el mismo programa.


Todo proceso requiere de recursos que el SO se encarga de controlar, como puede ser memoria, CPU... Dentro del apartado de ejecución de la CPU, se debe diferenciar entre la ejecución de usuario y la ejecución de kernel, similar pasa a la memoria que este en estado protegido del kernel (Donde solo opera el kernel por logica, el codigo de este espacio es llamado reentrante) y la de continuo o usuario (Donde cada proceso tiene un espacio de direcciones protegido).

Vamos a diferenciar:
- Un usuario puede acceder a los procesos mediante su codigo de usuario, pero JAMÁS podra acceder al contexto de kernel.
- El kernel puede acceder a los procesos mediante llamadas al sistema y excepción, y también puede acceder al Kernel mediante tratamiento de interrpciones y tareas del sistema.

El SO se ejecuta de la siguiente manera:
- Núcleo fuera de todo proceso, es decir, se ejecuta el núcleo como si fuera un proceso normal y el código del sistema operativo se opera de forma separa al modo kernel.
- La ejecución de los proceoss d eusuario, donde los software del SO tienen el contexto del proceso de usuario, y un proceso se ejecuta en modo kernel cuando es algo del SO.

A la hora de pensar en proceso, debemos pensar en, una unidad de acividad caracterizada por la ejecución de una secuencia de instrucciones (traza), un esatdo de computación actual (contexto) y un conjunto de recursos (dado por el SO). El SO puede decidir que un proceso se termine, guardando sus datos en el PCB (mas adelante), esta acción se denmonia context_switch (Cambio de contexto).


Tenemos que definir PCB ( Process Control Block), es una estrucutra de datos que contiene información relativa al concepto del proceso, ya que es algo creado gestionado y destruido unicamente por el kernel, conteniendo la siguiente información:
- PID (Process IDentifier)
- Process State (State diagram)
- Contexto de registro
- Información de memoria
- Lista de recursos utilizados

Por lo tanto un proceso tiene texto y datos asociados, a su vez tiene una pila asociada, y el SO almacena toda esta inforamción en el PCB, es por ello que podemos definir PCB como metadatos en la memoria de los procesos.



Todos los cambios que se realizan en el proceso, incluso sus datos guardados por detención se salvan en el PCB. 

### Cambio de proceso
Es un apartado importante, ya que nos permite entender el "multitasking OS" o SO multitareas, esto sucede:
- Cuando un proceso en ejecución acaba su tiempo en de ejecución (timeout o se acabo su timeslice)
- Como consecuencia de una llamada que bloqueante del sistema.
- Debido a una interrupción.
- El proceso abandona por si mismo la CPU.

Los cambios de contexto lo podemos resumir en el "dispatch" del tema anterior:
- Dejar en suspenso la ejecución de un proceso, almacenando los datos en el PCB
- Restaurar el contexto de registro del proceso que se va a ejecutar en CPU.
- Continuar con el ciclo de captación-ejecución de instrucciones utilizando el nuevo valor de registro PC.

## Operaciones sobre procesos
La creación del proceso, consiste en la asignación de espacio de direcciones que se utilizará, y la creación de estructuras de datos para que se administre.

Un proceso se crea:
- Por sistema batch: Respuesta a la recepción y admisión de un trabajo.
- "logon" interactivo: Un usuario se autentifica en un terminal, y el SO crea el proceso de intérprete.
- El SO crea un proceso para llevar a cabo el servicio solicitado por el usuario (El más habitual).
- El proceso puede crear otros procesos, dando la relación padre-hijo,
## Threads

## Conceptos fundamentales sobre planificación

## Políticas de planificación de la CPU

## Implementación de procesos/hebras en Linux: task

## Planificación de CPU en Linux