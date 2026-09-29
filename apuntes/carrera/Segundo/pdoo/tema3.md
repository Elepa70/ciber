---
title: Consultores, Modificadores y agrupacion de elementos
description: 
published: true
date: 2026-09-29T09:54:50.742Z
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


### Modificadores
Por otro lado también existen una serie de métodos dedicados a modificar un valor de un atributo, nombrado:
- En Java: setAtributo()
- En Ruby: atributo
> Similar al anterior método, se debe controlar el alcance y la exposición de estos objetos.
{.is-warning}

Ejemplo:


### Ejemplos anteriores
En Java:
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


// En el Main
Ejemplo e = new Ejemplo(2);
e.setInstancia(3);
System.out.printIn (p.getInstancia());
System.out.printIn (Ejemplo.getClase());
```


En Ruby:
```Ruby
class Ejemplo
	@@CLASE = 2
  def initialize (a)
  	@instancia = a
  end
  
  attr_reader :instancia		#Consultor
  attr_writeer :instancia		#Modificador
  attr_accessor :instancia	#Consultor y modificador
  
  def self.CLASE=c
  	@@CLASE = c
  end
end

# En el main

e = Ejemplo.new(2)

e.instancia=3 #Usar modificador

puts e.instancia #Usar consultor

Ejemplo.CLASE=5 #Modificador de clase
```

### Devolver o asignar las referencias
Existe un problema a la hora de asignar o devolver referencias ya que en ambos lenguajes siempre estamos usando punteros, para ello establecemos las siguientes normas:
- Crear solo los que sean realmente necesarios.
- Tener en cuenta si se devuelven (o se asignan) referencias.
- No hay una regla a aplicar en todos los casos, ya que depende de nuestro interes.

Siempre debemos decirlo nosotros según la situación.