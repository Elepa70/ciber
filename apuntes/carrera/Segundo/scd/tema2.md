---
title: Sincronización en memoria compartida
description: 
published: true
date: 2026-10-09T16:56:09.379Z
tags: 
editor: markdown
dateCreated: 2026-10-09T16:36:44.576Z
---

# Sincronización en memoria compartida
Las sincronizaciónes que vamos a ver en este tema, va a estar dividido en dos:
- Soluciones en bajo nivel con espera ocupada: Basadas en programa que contiene explícitamente instrucciones de bajo nivel de lectura y escritura.
- Soluciones en alto nivel: Se tiene una capa de software por encima con un interfaz para la aplicaciones.

Cuando un proceso tiene que esperar a algun evento por X condición, entra en un estado de espera infinita, a esto lo denominamos **espera ocupada**. Podemos encontrar dos tipos de soluciones:
- Solución software: Usan operaciones simple de lectura y escritura de datos simples.
- Solución hardware (cerrojos): Esta basado en instrucciones máquinas específicas, con varios procesadores involucrado.


## Soluciones software
> Resumir 8
{.is-error}

Este tipo de soluciones surgen basado en las soluciones 

### Secciones críticas
De momento tenemos definido las secciones críticas como una zona de código donde se debe realizar todo de seguido sin que afecten terminos estructura ajena.

Realmente se divide en tres partes:
- Protocolo de entrada (PE): Unas instrucciones donde puede haber espera hasta entrar.
- Sección crítica (SC): Las instrucciones que deben ser ejecutada por un único proceso.
- Protocolo de salida (PS): Instrucciones que permiten indicar al resto de procesos que se ha acabado la parte critica.

Algunas de las restricciones que vamos a definir en estas secciones criticas son:
- Cada proceso debe ejecutar únicamente una sección critica.
- La SC es un único bloque contiguo de instrucción.
- Se va a ejecutar un bucle infinito donde está, la sección critica (inclusive el PE de antes y el PS de después), y el resto de sentencias.


> Mientras que un proceso este en una sección crítica nunca deberá finalizar o abortar (propiamente o externamente), no puede haber bucles infinitos ni ser bloqueado o suspendido indefinidamente de manera externa.
{.is-warning}

### Propiedad de exclusión mutua
Tenemos tres propiedades mínimas a cumplir:
1. Exclusión mutua: Para que un algoritmo de exclusión mutua se efectue, se debe evitar que dos procesos se estén ejecutando una sección critica a la vez.
2. Progreso: Si hay dos procesos en el PE, uno de ellos deberá entrar si o si.
3. Espera limitada: Si hay un proceso que esta esperando una sección critica, eventualmente debe poder ser desbloqueado para hacerlo.

Además si se pueden cumplir dos propiedades, es mejor:
4. Equidad: No se perjudicar a un proceso de forma consistente.
5. Eficiencia: El algoritmo debe ser el más eficiente posible.