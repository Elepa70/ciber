---
title: Estructura de datos lineales
description: 
published: true
date: 2026-10-08T17:03:26.455Z
tags: 
editor: markdown
dateCreated: 2026-10-01T15:53:53.196Z
---

# Estructura de Datos lineales
Las Estructuras de Datos Lineales (E.D.L), consiste en una secuencia de datos dispuestos en una dimensión (uno de tras de otro), se califican como contendedores, ya que almacenan elementos de un tipo (enteros, string...).

El propósito estructural, es que contiene una secuencia de valores alojado en un único bloque ininterrumpido. 

Ejemplo:
```C++
#include <vector>
vector <int> first;
for (int i = 0; i<10; i++){
	int a; cin >> a;
  first.push_back(a); //También tenemos push_front, donde todos los valores se añaden desde el principio (0).
}
```
En este ejemplo tenemos un "array" por así decirlo, donde iremos añadiendo números y estos se van añadiendo desde el final. (maximo n).
> Es como añadir el elementos a un array dinamico, pero sin tener absolutamente nada reservado.
{.is-info}

> Si intentaramos añadir mediante fisrt[a]=a;, entonces nos daria un error por segmento invalido ya que no existe.
{.is-warning}

Algunos elementos de manipulación que tenemos son:
- push_front: Desde el principio.
- push_back: Desde el final.
- pop_back: Eliminar desde el final.
- pop_front: Eliminar desde el inicio

## Pilas
Las pilas es una política que vamos a usar, donde se imponen un orden estricto gracias a LIFO (Last In, First Out). Este tipo de "pilas" debemos pensarlo como si fuera un bote de patatas pringles, donde solo es accesible la última añadida y las primeras añadidas no.

Debido a esta característica, a la hora de trasnladar información de una pila a otra, lo que se hace e sinvertir el orden.

Dentro de la pila, la especificación, contiene una sencuencia d evalores, diseñadas para la relaización e inserción y borarar por sus extremos o TOPES.

Ejemplo, de un texto
```C++
bool controlComillado(const string & texto){
	Pila p;
  for ( int i = 0; i<texto.size(); i++){
  	if(texto[i]==""){
    	if(p.empty())
      	p.push("");
      else
      	p.pop();
  	}
  return p.empty();
  }
```

Vamos a hacer otro ejemplo sobre caracterisitcas de LIFO, en este caso tenemos dos pilas del mismo tipo y vamos a crear una pila que contenga primero los de un elemento y después lo del otro.
```C++
stuck<int> UnirPilas(stack <int> &p1, stack <int>	&p2){
	stuck <int> res;
  while(!p1.empty()){
  	res.push(p1.top());
    p1.pop();
  }
  while(!p2.empty()){
  	res.push(p2.top());
    p2.pop();
  }
  return res;
}
```

Para representar las pilas, también podemos hacer uso de "celdas enlazadas", ya que puede tener una información que almacena y después la información del proximo elemento.

## Colas
Las colas es otro tipo de estructura de datos que son lineales, sigue una poilitica FIFO (First Input First Out), las operaciones de colas son:
- front: Consulta cúal fue el primer elemento consultado (El más antiguo).
- empty: Evaluar si esta vacia o no la cola.
- push: Añadir un nuevo elemento al final.
- Put: Eliminar un del frente.
- Size: Cuanto elementos hay en cola
- Back: Es particular de este tipo, porque consulta el último elemento insertado.
- Swap: Intercambia contenido de una cola a otra.

La forma en la que opera es sencillo: A la hora de añadir un elemento, se comprueba si ya hay uno al frente y si es el caso, comprueba el que esta justo detras, así hasta encontrar su hueco.
```C++
queue<int> UnirColas (queue <int> &q1, queue <int> &q2){
	queue <int> res (q1);
  while(!q2.empty()){
  	res.push(q2.front());
    q2.pop();
  }
}
```

## Colas con prioridad
Anteriormente hemos visto las colas y como funcionan con el modelo FIFO, sin emabrgo ahora vmaos a ver otro tipo de Colas donde existe una prioridad.

Esta prioridad sirve para poder terminar la posición a donde queda los elementos, ya que pueden estar más o menos cerca del elemento indicado con prioridad.

### Diferencias colas simples y colas con prioridad
En las colas normales:
- La regla de salida es según la llegada (FIFO), primero que entra primero en salir.
- Su uso suele ser buffers simple o colas de impresión.
- Su complejidad es de O(1).

Colas con prioridad:
- La salida se rigue por el elemento de mayor prioridad, ya que este saldrá primero.
- El triaje médico se peude ver este tipo de colas o en planificación dentro de un SO.
- Su complejidad es de $O(log(n))$.

Luego en vez de usar "front" existe "top".



## Iteradores
Los iteladores son clases que nos permiten acceder a elementos de un contenedor para poder modificarlos, ya sea moviendolos o cambiandolos.

Para poder usar los iteradores debemos tener:
1. El inicio del iterador deberá estar en la posición begin.
2. Debemos saber como avanza.
3. Debe saber como acceder a ese elemento.
4. Debe saber cuando termina.
```C
/* Void cambiar por vectores
void Cambiar (vector <int> &v){
	for (int i = 0; i < v.size(); i++){
  	if(v[i]%2 ==0)
    	v[i]=-1;
  }
}

/* Cambio con iterador

vector <int>::iterator it;
for (it = v.begin(); it!=v.end(); i++){
	if( (*it)%2==0)
  	(*it)=-1;
}
```
Algunas caracteristicas de los itirador:
- iterador.end(): Posición final (no leible o escribible de un vector).
- iterador.begin(): Posición inicial de un vector.
- iterador.at(): Es una consulta.
- iterador.back(): Devuelve la referencia del último elemento.
- iterador.front(): Consulta y modifica el de la primera posición.
- iterador.assign(): Sustituir el valor contenido del vector por el dado.
Otro tipo de iteradores:
- Tenemos el reverse_iterator(): El cúal funciona igual que el iterador pero con las operaciones rbegin() siendo la última posición del vector, y con un ++ se mueve a uno anterior.
> Siempre que queramos modificar información de un contenedor, el cúal es constante se debe usar const_iterator, ya que de otra manera no podemos acceder a la información.
{.is-warning}

## Listas
Las listas son una secuencia de elementos dispuestos en una dimensión, diseñadas para hacer inserciones y borrados en cualquier posición.

Las operaciones que tiene son:
- set: Modificar un elemento de una posición.
- get: Devolver un elemento de una posición.
- borrar: Borrar o eliminar un elemento de una posición.
- insertar: Insertar un elemento de una posición.


Las listas podemos implementarlas como celdas enlazadas, y para ello a la hora de insercción en X elementos, se busca el inmediato anterior y hacemos que ese puntero apunte a nuestro nueva celda y está nueva celda hacemos que apunte al que ocupaba la posición que deseamos.