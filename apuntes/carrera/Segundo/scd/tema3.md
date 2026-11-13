---
title: Sistemas basados en paso de mensajes
description: 
published: true
date: 2026-11-13T18:03:46.649Z
tags: 
editor: markdown
dateCreated: 2026-11-13T17:54:15.792Z
---

# Sistemas basados en paso de mensajes
## Mecanismos básicos en sistemas basados en paso de mensajes
### Introducción
Hasta ahora hemos trabajado en un sistema multiprocesador, ahora vamos a usar los sitemas distribuidos (conjunto de procesos que no comparten memoria pero envian datos en una red), literalmente Torrent o internet.

Lo que se ha añadido con respecto a los temas anteriores, es que se han añadido una serie de herramientas nuevas para poder enviar y recibir la información. Esta información ( o mensajes) oculta el hardware ya que no tiene que ver y su portabilidad se puede implementar segun la arquitectura usada.
### Vista lógica arquitectura y modelo de ejecución
Los procesos se comunican mediante envío y recepción de mensajes.
El código lo podemos diseñar de una u otra manera según unos estilos que queramos seguir:
- SPMD (Single Program Multiple Data): Es un estilo muy simple donde depende de una variable se hace uno u otro, actualmente en desuso.
- MPMD (Multiple Program Multiple Data): Distintos procesos ejecutan el mismo o diferentes programas segun los ficheros ejecutables.
### Primitivas básicas de paso de mensajes
El paso de un mensaje entre dos procesos constituye en una transferencia de una secuencia finita de bytes:
- Se leen variables d eun proceso emisor
- Se establece una red de envio de inforamción
- Se establece una variable de proceso receptor
- Existe una sincronziación para poder estar esperando respuesta y para poder estar enviando.

En el apartado de sincronización, vamos a tener:
- send (variable_origen, idenfiticador_destino)
- receive (variable_destino, identificador_proceso_origen)


Para definir quienes hacen cada trabajo:
- Directo estático: Se usará un identificador para todos los procesos.
- Indirecto: Los mensajes se almacenarán en intermedios y seran accesible por los procesos. Estos canales o buzones que almacenan la información puede ser canales (uno a uno, cada emisor va a cada receptor), generales (Todos los procesos lo envian al mismo y lo reciben al mismo) y por puertos (muchos emisores y un unico receptor).
## Paradigmas de interacción de procesos en programas distribuidos

## Mecanismos de alto nivel en sistemas distribuidos
