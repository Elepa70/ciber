---
title: Procesos y Hebras
description: 
published: true
date: 2026-09-30T16:59:10.566Z
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
## Operaciones sobre procesos

## Threads

## Conceptos fundamentales sobre planificación

## Políticas de planificación de la CPU

## Implementación de procesos/hebras en Linux: task

## Planificación de CPU en Linux