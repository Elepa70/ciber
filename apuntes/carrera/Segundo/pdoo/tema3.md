---
title: Consultores, Modificadores y agrupacion de elementos
description: 
published: true
date: 2026-09-29T09:36:21.631Z
tags: 
editor: markdown
dateCreated: 2026-09-29T09:09:09.136Z
---

# Consultores, Modificadores y agrupacion de elementos
## Consultores y Modificadores
### Consultores
Existen métodos dedicado a devovler el valor de un atributo, estos metodos los nombraremos:
- En Java: getAtributo()
- En Ruby: atributo

> Siempre se intentará crear los consultores necesarios, intentando reducir la cantidad de exposición posible.
{.is-warning}

Ejemplo:
```Java
public class Ejemplo {
	private static final int CLASE = 1;
  private int Instancia = 2;
  
  Persona (int i){
  	Instancia = i;
  }
  // Consultor de clase
  public static int getClase(){
  	return CLASE;
  }
  // Consultor de Instancia
  public static int getInstancia(){
  	return Instancia;
  }
  
  //Modificador
  public int setInstancia(int i){
  	Instancia = i;
  }
}
```
### Modificadores
Por otro lado también existen una serie de métodos dedicados a modificar un valor de un atributo, nombrado:
- En Java: setAtributo()
- En Ruby: atributo
> Similar al anterior método, se debe controlar el alcance y la exposición de estos objetos.
{.is-warning}

Ejemplo:

```Ruby
```
### Devolver o asignar las referencias