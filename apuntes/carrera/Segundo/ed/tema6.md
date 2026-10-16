---
title: Estructura STL
description: 
published: true
date: 2026-10-16T15:58:18.779Z
tags: 
editor: markdown
dateCreated: 2026-10-15T17:12:54.174Z
---

# Estructura STL
La estructura STL tieen un monton de contendeores secuenciales, adaptativos y asociativos que ya hemos visto en los anteriores temas.

Ahora vamos a ver una serie de conjuntos (o set), que son aquello contenedores donde se almacenan elementos no repetidos de un tipo base de forma ordenada.

Vamos describiendo uno a uno
#### insert()
Encargado de copiar o mover un objeto existente al conjunto, permite la insercción de valores individuales o rangos. También puede sugerir la insercción.

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

#### value_comp
Devuelve un comparador de set que se peude usar para comparar dos objetos del contenedor.

## Ejercicio
```C++
/*Dado dos conjuntos crear una función para obtener un nuevo conjunto que sea la intersección. s1={12,15,75} s2={12,75,90}*/
set <int> Interseccion (const set<int> & s1, const set <int> &s2){
	set <int> s3;
  set <int>::const_iterator it1;
  for (it1=s.cbegin();it1!)s1.cend();++it1){
  	if (s2.find(*it1) != s2.cend()){
    	s3.insert(*it1); // También se puede hacer s3.insert(s3.end(),*it1);
    }
    
    // Otro método
    if (s2.count(*it1)!=0){
    	s3.insert(*it1);
    }
  }
}

// Ahora lo haremos con la diferencia
set <int> Diferencia (const set<int> & s1, const set <int> &s2){
	set <int> s3;
  set <int>::const_iterator it1;
  for (it1=s.cbegin();it1!)s1.cend();++it1){
  	if (s2.find(*it1) == s2.cend()){
    	s3.insert(*it1); // También se puede hacer s3.insert(s3.end(),*it1);
    }
    
    // Otro método
    if (s2.count(*it1)==0){
    	s3.insert(*it1);
    }
  }
}
```