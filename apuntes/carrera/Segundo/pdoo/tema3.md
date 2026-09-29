---
title: Consultores, Modificadores y agrupacion de elementos
description: 
published: true
date: 2026-09-29T10:27:27.416Z
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
Existe un problema a la hora de asignar o devolver referencias ya que en ambos lenguajes siempre estamos usando punteros, para ello debemos tener en cuenta lo siguiente:
- Crear solo los que sean realmente necesarios.
- Tener en cuenta si se devuelven (o se asignan) referencias.
- No hay una regla a aplicar en todos los casos, ya que depende de nuestro interes.

> Siempre debemos decirlo nosotros según la situación.
{.is-success}

## Agrupación de elementos
### Paquetes de Java
En Java tenemos la posiblidad de agrupar clases, que es un espacio de nombres, sus usos principales son:
- Debemos poner el nombre del paquete (en minusculas) para indicar lso elementos definidos en el mismo.
- Indicar que se van a usar los paquetes.
- En disco, aparece como una carpeta del sistema de ficheros.

Declaración:
```Java
package miPaquetito;
// Todas las funciones...

import miPaquetito.Clasecita //Usamos la clase Clasecita, del paquete miPaquetito
```
> Todo paquete en Java es independiente del resto.
{.is-info}
### Modulos de Ruby
Los modulos de Ruby, nos sirven para agrupar una gran variedad de elementos, como son clases, constantes funciones...

Su uso es:
- Abrimos el módulo para la realizar la definición y se cierra el módulo.
- Se puede copiar todo el contenido del módulo.
- Existe la posibilidad de crear módulos en módulos.

Declaración con ejemplo:
```Ruby
modulo Modulazo
	class A
  end
  
  module Modulito
  	class B
    end
  end
end

class Ejemplo
	include Modulazo # Copiamos el contenido de Modulazo
end
```
### Proyectos de Ruby
Las buenas praxis establecen que cada clase que forma parte de un proyecto, se debe definir en un archivo distinto.
Los lenguajes compilados como C++, procesan todos los archivos de la fuente antes de ejecutar el programa principal, sin embargo Ruby esta interpretado por si mismo, esto conlleva:
- No sabe que un proyecto está formado por varios archivos.
- No realiza un procesamiento previo que sea capaz de identificar las clases.

Para ello, es necesario referenciar los archivos mediante el uso de "require" si es archivo del lenguaje o "require_relative" si es un archivo propio.
> Unicamente conectar los archivos SI se va a usar en el código, de otra manera producirá un error, ya que no ha sido utilizado.
{.is-error}
