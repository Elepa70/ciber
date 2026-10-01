---
title: Estructura de datos lineales
description: 
published: true
date: 2026-10-01T15:57:27.066Z
tags: 
editor: markdown
dateCreated: 2026-10-01T15:53:53.196Z
---

# Estructura de Datos lineales
Las Estructuras de Datos Lineales (E.D.L), consiste en una secuencia de datos dispuestos en una dimensión (uno de tras de otro), se califican como contendedores, ya que almacenan elementos de un tipo (enteros, string...).

Ejemplo:
```C++
vector <int> first;
for (int i = 0; i<10; i++){
	int a; cin >> a;
  first.push_back(a); //También tenemos push_front
}
```
En este ejemplo tenemos un "array" por así decirlo, donde iremos añadiendo números y estos se van añadiendo desde el final.