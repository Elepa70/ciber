---
title: Introducción
description: 
published: false
date: 2026-09-28T09:25:44.295Z
tags: 
editor: markdown
dateCreated: 2026-09-14T17:25:49.207Z
---

# Introducción

Palabras claves:
- Arquitectura: COnsiste en el "manual" del procesador o la CPU.
- Organización: Compenetes y su interconexión.
- Computador: Lo definimos como un conjunto de Entrada/Salida, Memoria y CPU.

## Unidades funcionales
En las unidades funcionales tenemos 5 cosas:
- Entrada y Salida, donde entrada se encarga de codificar y lectura de transmitir o digitalizar
- Memoria, encargado de almacenar.
- CPU encargado de procesar la información y con ALU hace operaciones lógicas y la UC controla los circuitos.

Existen instrucciones para cada cosa y cada una de las unidades llevan una parte:
- Tranferencia: Como es *mov*, *in* o *out*, donde se encarga la Memoria y la Entrada/salida
- Operaciones: Como es *add* y *and*, encargandose la ALU.
- Control: Como es *jmp*, *call*, *ret*, y *set*, encargado por UC.

Hay un termino importante llamado programa almacenado, donde las instrucciones están almacenadas en memoria.


Dentro de la memoria solo hay datos, ya sea interpretado como programa o compilar y desamblar.

La entrada sirve para poder enviar información del ser humano al equipo o entre los propios equipos, por otro lado la salida emitir información al humano o también para comunicarse con otros equipos.

La memoria se encarga de almacenar información, con el valor de bits. 

En la CPU tenemos:
- ALU: Encargado de hacer operaciones ariméticas y lógicas.
- UC: Encargado de todos los demás circuitos. 

Lo habitual es tener memoria de posiciones de 1B, donde se generán los problemas de:
- Alineamiento: Las palabras de n bytes alineadas, comienza en dirección de múltiplo de n.
- Ordenamiento: DOnde tenemos que tener en cuenta que al escribir 2B, debemos saber como vamos a ocupar esos espacio de memorias, el más significativo primero (big-endian) o alreves (little-endian).


> Documentos con ayudas	
{.is-warning}

Existe una clasificación llamada m/n, que se encuentra en la ALU. Se necarga de admitir n operandos de un máximo de m en memoria. 

Existe una serie de combinaciones típicas creadas basadas en estas clasificación.
- Maquina pila 0/0: Las operaciones "suma" admiten 0 operandos, que admiten 0 cosas, es decir sumas el tope de la pila con el tope de la pila y lo dejas en el tope de la pila.
- Máquinas de acumulador 1/1: Se creo un registro acumulador, para no abusar de la pila, donde se usa los load y los store para poder hacer calculos. 
- Máquinas de RPG (Registros de Propósitos General): Se empezó a crear multiplos acumuladores para poder hacer calculos mucho más rapidos. Cuanto mas números tengas en el operador más te permite "sumar". 

Estás máquinas tienen a su vez aún más clasificación:
- Arquitecturas R/R (registro-registro): Este tipo no guarda nada, por lo tanto es 0/2, 0/3.
- Arquitecturas R/M (Registro-memorias): Es el más común, entre ellas 1/2 y 1/3 sobre todo. 
- Arquitecturas M/M (memoria-memoria): Es el tipo completo, opera directamente en memoria pero suele machacar y bastante más lento.

Por último veremos sobre los repertorios o arquitecturas:
- ISA: Arquitectura del Repertorio.
- RISC: Suelen ser las 0/2 o 0/3, pocas instrucciones y pocos modos.
- CISC: Es más complejo y se supone que es más proximo a lenguajes de alto nivel.

## Conceptos básicos de funcionamiento
La captación consiste en leer de una posición y traerlo al registro IR.

Volviendo a las arquitecturas tenemos que ir viendo:
- Arquitectura M/M: Varia en cuanto a las operaciones de captaciones.
- Arquitectura R/M: Hace usos de "Add" para acceder a memorias.
- Arquitectura R/R: Usado para varias instrucciones, y funciona mediante "Load".

Hablando sobre formatos de instrucciones:
- RISC: Sus caracteristicas son las de pocas instrucciones, pocos modos y muchos registros (0-2) y (0/3).
- CISC: Este es completamente alreves. 

> En casa
{.is-warning}

## Estructura de bus
La estructura del bus la vimos en en TOC, de todos modos también la hemos visto tanto en SO como parcialmente en SCD.

Debido a que E/S, memoria y CPU deben estar conectadas para pasar datos, existe los buses en paraletos que permiten una representación binaria de los datos para aumentar la velocidad de transferencia.

Los buses únicos por otro lado, la CPU escribe los buses de dirección y el control del R/W, la E/S y memoria comprueban si esta dirección es la suya. Tiene la ventaja de que es mas sencillo y tiene un coste bajo. Sin embargo los buses múltiples, suelen ser bastante más rapidos y funcionan en paralelo, donde se tiene una conexió entre Memoria y CPU, y otro con E/S y CPU.

En todos los buses, puede suceder que muchos quieran escribir a la vez para enviar mensajes, para evitar esto, un componente se convierte en dispositivo **activo** (Se encargad de escribir) y el resto en **pasivo** (Solo escuchan).

Tras esto se explican numerosos apartados que se ven en el primer tema de S.O. por ello no se repite.
## Rendimiento
En este aspecto vamos a ver aspectos muy similares a ED, es por ello que se omitirá algunos apartados.

Para poder medir el rendimiento, se acordo usar los benchmarks, estos rendimientos dependen tanto del diseño de CPU, versión del SO, compilador, librerias y muchas más cosas. En general los Benchmarks pueden ser especificios y probar el rendimiento de una de las partes del equipo, por ejemplo lo sbenchmarks de CPU ejercitan unicamente la PCU, están influidos por las prestaciones de la CPU, Memoria, Chache y buses.

Un benchmark requiere de 3 elementos para hacer las pruebas:
- T: Tiempo para ejecutar el programa.
- N: Número de instrucciones.
- S: Serían los ciclos o instrucciones que realiza.

Después esta la Frecuencia (R), que son aquellos ciclos de relojs que tarda un UC para ejecutar una instrucción.

La formula para saber el tiempo que tarda ejecutando un benchmark es el siguiente: $T=\frac{NxS}{R}$.
## Prespctiva histórica