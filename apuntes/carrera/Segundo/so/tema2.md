---
title: Procesos y Hebras
description: 
published: true
date: 2026-10-07T15:57:01.127Z
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
- El proceso puede crear otros procesos, dando la relación padre-hijo.

En el último caso, el hijo obtiene los recursos mediante:
- El SO sin que venga el padre intervenga.
- Compartir todo los recursos con el padre.
- Comparte algunos recursos del padre.

Este tipo de procesos pueden ejecutarse o bien concurrentemente o que el hijo termine y el padre este esperando a ello.

Respecto al espacio de direcciones, el hijo obtiene una copia del padre o se le da uno nuevo.


### UNIX-like OS
Los procesos UNIX-like OS, funciona de manera especial:
- Con llamadas al sistema "fork()" (También llamado retval que es el PID del hijo, donde si el pid == 0, es el hijo y en cualquier otro caso es el padre), podemos crear un nuevo hijo, que podrá heredear la memoria del padre o los registros de CPU del padre. Esta llamada devuelve un 
- La llamada "exec()", lo que hace es reemplazar un espacio de direcciones. Es decir eliminará la memoria copia creada para el hijo


> El PCB hijo obtiene: PID único, el registro del padre, el estado será nuevo **NO BLOQUEADO**, la memoria la cpia del padre. 
{.is-info}

En la creación de un proceso, lo hace "program loader" con los siguientes pasos:
- Creación de un PID único.
- Asignar espacio en memoria RAM o SWAP.
- Crear el PCB e inicializar campos de información.
- Insertar inforamción del PCB en la tabal de procesos (una lista donde estan todos los procesos).


Al finalizar un proceso, este llama al SO para solicitar un exit(), que provoca:
- Un aviso de finalización al padre, guardando su estado. (SIGCHLD)
- Los recursos son liberados
- El padre finaliza la ejecución de sus hijos mediante kill()
- El padre va a finalizar y por lo tanto el SO va terminando los procesos hijos evitando que continuen (Denominado terminación en cascada). En UNIX por otro lado, lo que se hace es dejar "colgados" los procesos, asociandolo al padre en init (systemd).
- También es posible que el SO termine un proceso por errores o condiciones de fallo.

- 
## Threads

## Conceptos fundamentales sobre planificación

## Políticas de planificación de la CPU

## Implementación de procesos/hebras en Linux: task

## Planificación de CPU en Linux