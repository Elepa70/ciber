---
title: Unidades Funcionales
description: 
published: true
date: 2026-03-19T17:39:33.310Z
tags: 
editor: markdown
dateCreated: 2026-03-05T17:01:26.297Z
---

# Unidades Funcionales
## Introducción
Un equipo tiene las "unidades centrales", como la CPU y la memoria central. A su vez, tiene periféricos, como memorias externas o auqellos dispositivos de entrada y salida.

## Procesador
Los procesadores realmente son microprocesadores (Hoy en día) son lo que podemos ver en computadoras de forma normal.
También existe los microcontroladores, que son aquellas placas que tiene todo integrado.

Por último tenemos procesadores diseñados o especificos:
- DSP: Procesadores digitales de señales.
- Procesadores de red.
- Procesedores multimedia.

DEntro de un procesador tenemos:
- La unidad de procesamiento: Encargada de hacer calculos y parcialmente almacenar información
- Unidad de control: Encargada de controlar el resto de procesadores.

### Unidad de procesamiento
Dentro de la unidad de procesamiento tenemos:
- ALU: Unidad encargada de hacer suma aritmeticas y logicas.
- RF (Banco de registros): Sirve para almacenar números, estos números son sobretodo aquellos que se usarán en nuestros programas. Tiene un espacio muy pequeño. Este banco de registros suele ser temporal.

Cuando se hace el calculo, existe una serie de indicadores que nos indica si ha pasado algo o si tiene algo, las flags son: Acarreo, dindicador de signo, indicador de paridad, de cero y de desbordamiento.

Estos bits anteriores, se le llama palabras de estados o "flags".

### Unidad de control
Esta unidad ya hemos dicho que es la encargada de controlar, mediante señales diciendole a la ALU que sume, reste o haga lo que haga falta. Podríamos decir que es el director de la orquesta.

Dentro del procesador tenemos los siguientes elementos:
- Registro de dirección (AR): Dobde se debe ubicar la dirección del dato a leer.
- Registro de datos (DR): Donde se almacena el dato a leer o a escribir.
- Unidad de control: Circuitos que generan las señales de control.
- Registro de instrucción (IR): Memoriza temporalmente la instrucción del programa que la unidad de control está interpretando.
- Contador del programa (PC): Registro-Contador que contiene en todo momento la dirección de memoria.

Las instrucciones se realiza en dos fases:
- Fase de captación de instrucción: Cuando se inciia una instrucción, el procesador capta de la memoria la instrucción a ejecutar.
- Fase de ejecución: En este momento ya se realiza las operaciones específicas correspondientes a la operación.


Tamaño de la memoria= Nº de posiciones de la memoria * Nº de bits de cada palabra.

Dentro del proceso de captación tenemos que se realiza la siguiente operación.
- AR <- PC
- DR <- M[AR]
- IR <- DR
- PC <-PC+

Durante la fase de ejecución, cuando se carga la instrucción en IR se decodifica ejecuta bajo el control de la UC.

> Los ejercicios tipicos de este tema son aquellos del temporización en la ejecución de instrucciones
{.is-info}

Lo que hacemos en este caso son las siguientes operaciones:
- AR <- r7
- DR <- M[AR]
- r7 <- DR

Es decir el proceso completo de la ejecución de instrucciones es:
- AR <- PC
- DR <- M[AR]
- IR <- DR
- PC <- PC+1
- AR <- rD
- RD <- M[AR]
- r7 <- DR
## Memoria

ES la unidad asignada de almacenar tanto los datos como las instrucciones, existiendo:
## Memoria principal
Siendo muy rapida, encargada de tener encargada las instrucciones. Podemos encontrar la memoria RAM (Volatil, de lectura y escritura) y la memoria ROM (BIOS).

Dentro de la memoria RAM, tenemos los buses:
- Bus de dirección: m bits -> $2^m$ direcciones. Con entrada de datos y salidas.
- Señales de control: IO/M' -> Entrada salida / memoria, R/W -> Lectura/Escritura, MFC -> Memory Function Completed.

- Memoria interna
## Perifericos