---
title: Introducción a la eficiencia de algoritmos
description: 
published: true
date: 2026-09-17T16:32:32.367Z
tags: 
editor: markdown
dateCreated: 2026-09-17T15:40:45.988Z
---

# Introducción a la eficiencia de algoritmos
Nos situamos en el mundo real, y ante un problema tenemos que seguir una serie de cosas a plantearnos:
- ¿Se puede resolver mediante un ordenador?: En este apartado lo que hacemos es analizar el mundo real y vamos a ir modulando las partes. Con esto llegamos a la **MODELIZACIÓN**.
- Tras la modelización vamos a desarrollar un **ALGORITMO**, que va a tener una **EFICIENCIA** determinada y unos **DATOS** (Que viene de Dominio, especificación y impletación), en esto último es donde nos fijaremos. Los algoritmos los diseñamos guiandonos en **TÉCNICAS DE DISEÑO**, que estan muy definidas para poder desarrollar los algoritmos (Como el divide venceras u otros, se irá viendo durante la asignatura).
- Con el algoritmo planteado, pasamos a la **IMPLENTACIÓN**(Gracias a FP o MP), y una vez hecho vamos a tener un **PROGRAMA**, que debemos comprobar si cumple con lo que queremos (**Validación**) y si funciona correctamente (**Fiabilidad**).

Para organizar los datos en memorais tenemos varios metodos, que depende de las operacioens frecuentes y el tipo de datos que usemos, alguno de los ejemplso son:
- Búsqueda o consulta (Binaria donde el vector esta ordenado y vamos dividiendo el vector, o secuencial comparamos valor a valor)
- Inserción
- Borrado
- Ordenación (Inserción, Selección, Burbuja o MergeSort)

### Ordenación
Dentro de la ordenación tenemos 4 principales a explicar:
- Insercción: Es muy eficiente, siempre y cuando esten todos ordenados
- Selección: Hace una búsqueda exhaustiva del mínimo todo el rato.
- Burbuja: Es el más facil de implementar pero el menos eficiente de todos
- MergeSort o Divide y Vencerás: Es el más complejo de implementar pero funciona muy bien a grandes volúmenes de datos.


## Eficiencia y complejidad en tiempo y espacio

## Cotas de eficiencia

## Caso peor, caso promedio y análisis amortizado

## Cálculo del tiempo de ejecución de un algoritmo 
