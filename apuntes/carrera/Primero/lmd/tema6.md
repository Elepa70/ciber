---
title: Grafos
description: 
published: true
date: 2026-05-27T15:19:33.779Z
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
Para poder definir un grafo de Euler, tenemos primero que definir:
- Un camino de Euler den $G$ es aquel que pasa por todas las aristas.
- Un circuito de Euler en $G$ es un camino que es cerrado.
- Un grafo de Euler, tiene un circuito de Euler.

Existe un circutio de euler, si y sola mente si, si el grado de sus vertices es par.
Si existe un camino (no cerrado) de euler, entonces si y sólo si, tiene exactamente dos vértices de grado impar, (donde empieza y termina el camino).
### Grafos de Hamilton
Para poder definir grafos de hamilton, debemos definir primero:
- Camino de Hamilton: Es un camino que recorre todos los vértices una sola vez.
- Circuito de Hamilton: En un camino cerrado que recorre todos los vértices una sola vez, excluyendo uno.
- Un grafo con un circuito de Hamilton, es un grafo de Hamilton.

No hay forma eficiente de saber si hay o no un grafo de hamilton, en general:
- Si tiene más de $\frac{1}{2} (n-1)(n-2)+2$ aristas, es de Hamilton.
- Si tiene menos de $n$ aristas, no es de Hamilton.
- Si $n\geq 3$ y para par de vértices no adyacentes $grafo(v)+grado(w) \geq n$ entonces $G$ es de Hamilton.
### Grafos de TSP  (Problema del vendedor)
Hay veces donde tenemos un grafo donde las aristas tienen distancias y en este problema se intenta buscar un ciclo de hamilton cuya suma de pesos sea mínima.

### Grafos de bipartitos
Consiste en un grafo donde se pueden separar en dos conjuntos los vertices (izquierda y derecha), donde no existen aristas que se conectan entre los vertices del mismo lado.

Si encontramos una longitud de ciclos impar, entonces es no es bipartitos.

Se puede escribir con $K_{n,n}$ un grafo bipartido completo de $n$ vertices. 

### Grafos Planos
Se denota por $K_n$ y se llama grafo completo de $n$ vértices, a un grafo donde los vertices y las aristas se unen cada par de vertices.

Se podría dibujar sin necesidad de que sus aritas se crucen.

Este tipo de grafos se puede dividir el plano en varias regiones (siendo cada cara externa una region).

Dado $G$ un grafo plano y conexo, con $n$ el número de nodos, $l$ el número de lados, y $c$ el número de caras de una representación plana.

Entonces siempre sale que:
- $n-l+c=2$.
- En caso de que no sea conexo, y $t$ es el número de componentes, conexas, entonces $n-l+c=2+t$.
- Si no tiene lazos, ni lados positivos, ni vertice de grado 1, se cumple que $3c\leq 2l$ y $l \leq 3n-6$. En caso de que sepamos que las caras tienen como mínimo $r$ lados, $rc \leq 2l$ y  $(r-2)l=r(n-2)$.

Redefinición de lo anterior:
- $G$ es plano, entonces $n-l+c=2$.
- $G$ es plano, entonces $l\leq 3n-6$.
- Si $G$ es plano y cada una cara tiene al menos $r$ aristas (lados), entonces $(r-2)l\leq r(n-2)$. (Es similar a la anterior pero con $r=3$, normalmente lo usamos con grafos bipartito, cuando $r=4$).
- Un grafo plano y bipartito tiene caras con almenos 4 aristas lados $l \leq 2 (n-2)$.
#### Constracción simple
Dado un grafo $G=(E,V)$ y una arista $e \in E$ que incide en $v_1$ y $v_2$, la contracción simple de $G$ a través de $e$ es el grafo $G'=(E',V')$:
- $V'$ es $V\ \{v_1\}.
- $E'$ se construye a partir de $E$ eliminando $e$ y, añadiendo aristas $w-v_2$ no esxiste en $G$.



Con el teorema de Kuratowski:
- Un grafo es plano si y solo si ningún subgrafo suyo puede contraerse en $K_5$ o a $K_{3,3}$.

## Coloración de grafos
Consiste en darle color a los vértices, de manera que vértices adyacentes no tienen el mismo color.

El menor número de colores que necesitamos para colorear un grafo se llama número cromático $x(G)$, es un número muy dificil de calcular en grandes grafos.

En el caso de $K_n$ entonces el número cromático es $K_n$.
En caso de bipartito, entonces si y solamente si, su número cromático es 2.
### Teorema de Appel-Haken
Consste en que si un grafo es plano, su número cromátoco es menor o igual que 4.

El poliomio cromático es aquel polinomio que dado un grafo y un número, cúantas numeraciones tiene ese grafo con esos colores.
El polinomio podemos calcular con la formula: $p(x,G)=p(x,G'_e)-p(x,G_e)$.
- Donde $G'_e$ es el grafo $G$ al que se le han quitado la arista e.
- Donde $G_e$ es la contracción simple de G en la airsta e.

Este algoritmo es muy lento. 