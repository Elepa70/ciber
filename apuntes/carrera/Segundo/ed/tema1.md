---
title: Introducción a la eficiencia de algoritmos
description: 
published: true
date: 2026-09-17T17:27:58.537Z
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
Como se ha mencionado antes, cuando por ejemplo jugamos videojuegos donde hay varios jugadores, se puede producir un consumo de recursos como sea Tiempo o Memoria.

Para ello, debemos entender que la **Eficiencia** es la cantidad de recursos que gasta un algoritmo, e intentaremos establecer una clasificación para considerarlo mejor o peor.

> Se suele decir que cuanto mejor sea el hardware o mayor sea el hardware mejor va a ir el rendimiento, sin embargo esto es un mito ya que no se puede contemplar. 
{.is-info}

Existe un punto critico donde se cruza la Escalibidad Sostenible y el Colapso del Sistema, y esto depende del volumen de datos o usuarios usando la aplicación.

### Conceptos claves
- Algoritmo: Serie de pasos o sentencias ordenadas que nos permiten resolver un problema.
- Implentación: Traducción del algoritmo a un lenguaje de programación.
- Principio de Invarianza: Consiste en dos implementaciones d eun mismo algoritmo con diferencia de una constante.
- Análisis Asintótico: Consiste en la eficiencia de un algoritmo cuando la cantidad de datos tiende a infinito.
- Función de Eficiencia [f(n)]: Es el número de datos de entradas y el número de segundos que requiere para ejecutarse en esos $n$ datos.

La manera para obtener esta eficiencia es:
- Empírica: Se hace en la vida real, lo podemos obtener mediante:
```C++
#include <ctime>
time_t nombre_variables, nombre_variables_2;
time(&nombre_variables);
//Uso
time(&nombre_variables_2);
//Resto
difftime(&nombre_variables_2,&nombre_variables);
```

EL problema viene dado que es necesario tener todo identico para que sea empirico, con la unica solución de obtener la eficiencia de forma teórica.

- Teórica: Se hace mediante un ordenador ideal.
En este meotodo el algoritmo tiene orden de eficiencia T(n), si existe una implementación del algoritmo y su tiempo de ejecución f(n), siendo acotado superiormente por c*T(n).
> La función f(n) siempre debe estar por debajo de c*T(n).

El concepto más importante ses el O-Grande, que se reifere al tiempo de ejecución cuando nos acercamos al peor de los casos (Tendemos al infinito). Para calcular este valor lo que hacemos es en un polinomio obtener el monomio más grande y compararlo junto al polinomio. 
## Cotas de eficiencia

## Caso peor, caso promedio y análisis amortizado

## Cálculo del tiempo de ejecución de un algoritmo 
