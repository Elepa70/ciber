---
title: Clases en C++ (Ampliación)
description: 
published: true
date: 2026-04-07T15:19:27.740Z
tags: 
editor: markdown
dateCreated: 2026-03-24T15:51:05.523Z
---

# Clases en C++ (Ampliación)

Los datos abstractos (T.D.A.) consiste en una colección de datos y conjuntos de operaciones que realizamos con una especificación. Nos sirve como componente reutilizable para facilitar abordar problemas complejos

Este tipo de datos lo implementamos normalmente mediante struct o class, la diferencia es que mientras struct suele ser totalmente publico, los datos de las clases suelen ser privados.

Es por esto que cuando definimos datos con struct lo podemos llamar como "abstracción funcional". Por otro lado tenemos las class que lo llamamos "abstracción de datos"

Cuando usemos metodos gets, lo suyo es usar un metodo const, ya que a la hora de llamar a ese metodo, no es necesario modificar lo que vamos a obtener.

## Clases friend
Las clases friend o amigas, son aquellas que permite acceder a la parte privada de otra clase. 

No suelen ser usadas, y de hecho no es recomendable usarlo, solo en caso muy especiales. 

## Destructores
Al igual que los constructores, existen los destructores, que nos sirve para liberar los espacios de los constructores.