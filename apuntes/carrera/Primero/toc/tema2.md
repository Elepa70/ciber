---
title: Unidades Funcionales
description: 
published: true
date: 2026-03-19T18:41:07.702Z
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

Dentro de la memoria interna tenemos el tiempo de acceso a la memoria o latencia, que es lo que tarda en responder la memoria. Y el ancho de banda, que es el número máximo de bytes que se puede transmitir por segundo entre memoria y procesador.

### Modos de dirección
Tenemos metodos de direccionamiento:
- Implícito: El código de operación indica sí mismo donde se encuentra operando.
- Inmediato: El operadno forma parte de la misma instrucción.
- Direco o absluto: L ainstrucción contiene la dirección del dato.
- Indirecto: La instrucción contiene un puntero a un registro o posición de memoria que contiene la dirección del dato a operar.
- Indexado: Registro índice y registro de referencia.
- Relativo:  Tenemos a la base, al contador de programa y al segmento.
### Memoria caché
La memoria caché suele ser memoria escondida, ya que se crea sin que la persona quiera. Sirve para aumentar el rendimiento y la velocidad de la ejecución.

La memoria caché que es un sistema de almacenamiento de tecnología más rápida de almacenamiento ya que suele tener memoria SRAM. La memoria caché es usada por el sistema de memoria para mantener la información más comúnmente usada por el procesador.

En cuanto a la jerarquía por velocidad es:
- REgistro de CPU 
- Cache
- Memoria principal
- DIscos magnéticos
- Cintas magnéticas

### Memoria externa
Tenemos los disccos duros, memorias usb... Suelen tener un gran tamaño de almacenamiento a costa de una velocidad más lenta.

## Perifericos
Los periféricos, tienen un controlador por detras encargado de transformar la información externa en señales eléctricas. Tenemos dispositivos:
- De entrada: Donde se transofrma en así para que pueda ser usado.
- De salida: Donde el proceo es inverso.


Hay dos niveles en la relaización de una Entrada/Salida:
- Transferencias elementales de información: Sirven para la recepción o envío de una información individual.
- Operaciones de entrada/salida: Donde la transferencia es en un conjunto de datos, que van en bloque. Las operaciones de E/S se componen, por lo tanto en transferencias elementales.

La mayor parte de las variables físicas de la naturaleza, son señales o funciones que varían continuamente con el tiempo. Estas señales podemos traducirla a señales eléctricas analógicas mediante sensores.

## Estructuras básicas de interconexión
Los compenentes de un equipo suelen comunicarse de alguna manera, y todo ellos es gracias a la placa base, que contiene ranuras para que puedan entrar los distintos elementos.

Los distitnos componentes están conectados trabajan a distinto ritmo, para ello se usa:
- Buses específicos.
- Memorais intermedias
- COntroladores de E/S
- Controlador de Acceso Directo a memoria

Los distintos elementos de un computador se interconectan por medio de buses, estos buses transportar datos e instrucciones, direcciones y señales de control y de estado. Estos buses pueden ser distitnos para poder adaptarse a la velocidad de aquello que lo necesite, también se establece una jerarquia de velocidades para saber, quien necesia o no velocidad.

Esta jerarquia tradicional:
- Buses internos.
- Bus delantero
- Buses locales
- Bus del panel posterior
- Buses de expansión
- BUses de entrada/salida
