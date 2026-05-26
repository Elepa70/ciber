---
title: Grafos
description: 
published: true
date: 2026-05-26T13:51:16.646Z
tags: 
editor: markdown
dateCreated: 2026-05-20T14:40:38.157Z
---

# Introducción a la Teoría de Grafos
## Teoría de grafos
Un grafo a nivel de calle es:
Teniendo unos vertices y una serie de lineas de unión entre esos vertices, todo el conjunto es un grafo.

Tenemos dos conjuntos:
- $V$ Conjunto de vértices.
- $E$ Conjunto de arista, (lineas de unión entre vertices), normalmente se escribe en pareja: $E=\{\{A,B\},\{A,C\},\{A,D\},\{B,D\},\dots\}$.

Con las aristas debemos tener en cuenta que:
- $\gamma$: De donde parte esa arista.
- $\delta$: hacia donde va esa arista.

## Definicioens básicas
- Un $camino$: Consiste en acudir de un vertice hacia otro.
- Un $recorrido$: Es un camino en el que no se repiten aristas, si es cerrado se le demonima $circuito$.
- Un recorrido en el que no se repiten vértices se le denomina $camino \text{ } simple$, en caso de que sea cerrado $ciclo$.

Un grafo se dice que es conexo si, para todo par de nodos existe un camino entre ellos.

Un grafo es $plano$, siempre que podamos dibujarlo sin necesidad de que las aristas se corten.

En los examenes nos pueden dar una sucesión de números naturales $d_1...d_n$, que significa la cantidad de aristas de unión que tieen los vertices.
> Los grafos solo pueden existir si la suma de sus grados son pares, y si es divisible entre la cantidad de eristas.
{.is-info}


### Teorema HH
Dado una sucesión, lo que hacemos es ordenarla de mayor a menor.
Tras esto eliminamos al valor más grande, y quitamos 1 valor hacia la derecha según el valor que hemos quitado. Y tras esto volvemos a reordenadar.

Si obtenemos 00 al final o 10, se considera gráfica.

Si encontramos valores negativos, significa que no es gráfica.
## Estructuras de datos usuales
Podemos almacenarlas de dos maneras:
- Listas de adyacencia: Se representa mediante un vector, donde cada componente i corresponde a un vértice del grafo. 
E

- Matrices de adyacencia: El grafo se representa mediante una matriz donde cada fila i es un vértice origen, cada columna j es un vértice destino.
## Algoritmos de caminos mínimos
## Algunos tipos de grafos
### Grafos de Eurler
### Grafos de Hamilton
Para poder definir grafos de hamilton, debemos definir primero:
- Camino de Hamilton: Es un camino que recorre todos los vértices una sola vez.
- Circuito de Hamilton: En un camino cerrado que recorre todos los vértices una sola vez, excluyendo uno.
- Un grafo con un circuito de Hamilton, es un grafo de Hamilton.
### Grafos de TSP  (Problema del vendedor)
Hay veces donde tenemos un grafo donde las aristas tienen distancias y en este problema se intenta buscar un ciclo de hamilton cuya suma de pesos sea mínima.

### Grafos de bipartitos
Consiste en un grafo donde se pueden separar en dos conjuntos los vertices (izquierda y derecha), donde no existen aristas que se conectan entre los vertices del mismo lado.

