---
title: Estructura de datos lineales
description: 
published: true
date: 2026-10-01T16:48:01.796Z
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
