---
title: Introducción a la eficiencia de algoritmos
description: 
published: true
date: 2026-09-18T16:31:09.438Z
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

En nuestro ordenador teórico, cada operación elemental tiene un coste de tiempo constante. En este ordenador ideal tenemos una lista

> Pendiente de cambio.
{.is-warning}

### Declaraciones
Por jeemplo
```
int a;
int b;
```
Esto se considera un tick o una **operación elemental**.
### Asignación
SImilar que el anterior ya que al darle un valor a una declaración también consume una operación elemental.

### Comparación simple
En este tipo de comparaciones también su valor de operación elemental.
### Aritméticas
```
int c = a+b; // En este caso son 3 ya que tenemos declaracióm y asignación.
```
> Hasta aquí
{.is-warning}

Todas las operaciones elementales anteriores tienen un coste de O(1) o de 1 tick.

SIn embargo cuando tenemos operaciones elementales donde hay bucles (como un for), esto ya cambiara segun la cantidad de operaciones que van a haber, por ejemplo en un for tenemos:
- Declaración del i, comparación del i y después el sumatorio de la cantidad de veces que se va a hacer, tendriamos una eficiencia de O(n).


Existen las leyes físicas del código que son:
- La suma: Cuando unimos ambos tiempo, esto pertenece al máximo de f(n),g(n), es decir $O(max(f(n),g(n))$. Por ejemplo, en las sentencias if-else se aplica la regla de la suma.
- El producto: En este caso tenemos un codigo dentro de otro (un bucle anidado), por lo tanto el tiempo va a ser $O(f(n)xg(n))$ o $O(n²)$.
> Cuando hamagos los cuenteos de los bucles, debemos tener en cuenta que, es el (fin del bucle -1) - (valor de la variable) + 1
{.is-info}

Hay casos donde tenemos dos bucles anidados y en alguno de ellos vamos modificando la variable contador.

Cuando incrementamos o decrementamos la variable en multiplicación o división, debemos tener en cuenta que la $O(n)$ pasa a ser $O(log(n))$.

- Interación Simple: $O(n)$, caso de i++.
- Interación a saltos: $O(log n)$, caso de i*=2.
- Bucles Anidados (independientes): $O(n^2)$, dos bucles for sin conexión.
- Bucles Anidados (dependientes): $O(n^2)$, dos bucles con conexión.
- Anidados mixtos: $O(n log n)$, se modifica una de los dos variables dentro del bucle.

## Caso peor, caso promedio y análisis amortizado

## Cálculo del tiempo de ejecución de un algoritmo 
