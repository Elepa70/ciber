---
title: Sincronización en memoria compartida
description: 
published: true
date: 2026-10-16T16:47:54.227Z
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
2. Progreso: Si hay dos procesos en el PE, uno de ellos deberá entrar si o si. Que un proceso entre o no a la sección critica, debe depender de los procesos.
3. Espera limitada: Si hay un proceso que esta esperando una sección critica, eventualmente debe poder ser desbloqueado para hacerlo.

Además si se pueden cumplir dos propiedades, es mejor:
4. Equidad: No se perjudicar a un proceso de forma consistente.
5. Eficiencia: El algoritmo debe ser el más eficiente posible.

### Refinamiento sucesivo de Dijkstra
Partiendo de dos procesos, con un bucle infinito, ejecutando la sección critica y después el resto. Vamos mejorando este algoritmo hasta que cumpla las tres propiedades, llegando a un algoritmo de Dekker (Versión final correcta).

### Algoritmo de Dekker
Durante el refinamiento sucesivo anterior, se llego a un algoritmo donde uno de los algoritmos hace una pequeña espera, al otro. Esta espera lo hace mediante un condicional, donde se abre durante unos segundos la posibilidad de que el otro proceso ejecute su sección critica, pero después se cierra.

## Soluciones hardware con espera ocupada (cerrojos) para E.M.
Un candado lo podemos definir (a mala manera), como un bucle "infinito" hasta que la condición pase a false.
```C++
while (true){}
```

Los cerrojos son una solución hardware basada en esperas ocupadas, esta espera es un bucle que se ejecuta hasta que otro proceso finaliza su sección critica. 

Aunque esto puede ayudarnos a evitar bucles, debemos ser consciente de que debemos bloquear siempre después de que entre uno de los procesos al bucle, para que no haya problematica con la duplicación.

Es por ello que existe la instrucción "**TestAndSet**", instrucción máquina disponible en algunos procesadores, con las caracteristicas:
- Admitir como argumento la dirección de memoria una variable lógica.
- Invocar como función desde LLPP a alto nivel y ejecutar, la lecutra del cerrojo, ponerlo en tru y devolver el valor anterior del cerrojo.
- Durante su ejecución ninguna instrucción ejecutada por otro proceso puede leer ni escribir la variable lógica.

Un ejemplo sencillo en pseudocodigo es:
```
var sc_ocuapda : boolean := false;
begin
	while true do begin
  	while TestAndSet (sc_ocupada ) do begin end
    {critica}
    sc_ocupada :=false;
    {demas}
  end
end
```