---
title: Estructura STL
description: 
published: true
date: 2026-10-16T15:43:00.723Z
tags: 
editor: markdown
dateCreated: 2026-10-15T17:12:54.174Z
---

# Estructura STL
La estructura STL tieen un monton de contendeores secuenciales, adaptativos y asociativos que ya hemos visto en los anteriores temas.

Ahora vamos a ver una serie de conjuntos (o set), que son aquello contenedores donde se almacenan elementos no repetidos de un tipo base de forma ordenada.

Vamos describiendo uno a uno
#### insert()
Encargado de copiar o mover un objeto existente al conjunto, permite la insercción de valores individuales o rangos.

#### emplace() & emplace_hint()
Este directamente coloca el objeto en la ubicación final de la memoria, permitiendo optimizar el rendimiento. El Emplace_hint, es una sugerencia de donde estará.

#### find()
Nos devuelve un iterador apuntando al elemento. En caso de que el elemento no exista devuelve un iterador end().
#### count()
Busca cuantos elementos coinciden con el valor indicado.

#### erase()
Nos permite una serie de opciones:
- Eliminar por valor.
- Eliminar por posición indicando el iterador.
- Eliminar un rango de valores.
#### clear()
Elimina completamente todos los elementos de forma inmediata.

#### lower_bound()
Devuelve un iterador del elemento igual o inmediatamente superior del elemento indicado.
#### upper_bound()
Devuelve un iterador del elemento estrictamente mayor.

#### insert
Nos permite insertar una serie de elementos pero de distinta maneras:
- Podemos insertar un conjunto. (Sin repetir)
- Insertar un elemento.
- Mediante un iterador, donde se le suguiere la posición el donde podria insertarlo.