---
title: Clases, objetos y mensajes
description: 
published: true
date: 2026-09-21T10:17:14.625Z
tags: 
editor: markdown
dateCreated: 2026-09-21T07:50:38.399Z
---

# Clases, objetos y mensajes
## Objetos
### Conceptos
#### Objetos
Vamos a empezar el temario definiendo algunos conceptos claves para entenderlo todo.

> Un objeto es una entidad perfectamente delimitada, que encapsula estado y funcionamiento y posee una identidad - OMG 2001

También se peude definir como:

> Elemento, unidad o entidad individual e identificable, real o abstracta, con un papel bien definido en el problema - Dictionary of Object Technology 1995

Con estas definiciones, podemos entenderlo como un ejemplar de una clase, donde podemos saber exactamente que hace y como lo hace.
#### Clases
Las clases por otro lado, se consideran como **molde** o **plantillas**, que usaremos para la creción de objetos, en algunos lenguajes también sirve como propio objeto. 

Todo objeto creado a partir de una clase se denomina **instancia**.

Ejemplos:
```Java
Lapiz miLapiz = new Lapiz (Color.Amarillo); //Esta declaración es en Java
```

```Ruby
otroObjeto = Objeto.new(Color.Verde); #Esta declaración es en Ruby
```
#### Identidad
Cada instancia tiene su propia identidad, que nos permite diferenciarlo de otras instancia, esta identidad es la **posición de memoria**.

#### Estados y comportamiento
Un **estado** en un objeto es definido por los **valores de sus atributos**, cada objeto tiene una zona de memoria propia. 

Algunos objetos exhiben **comportamiento**, que es una seríe de funciones o procedimientos que podemos llamar (A partir de ahora **métodos**)

Ejemplo:
```Java
// Clase Videojuegos
Videojuegos Smite = new Videojuego("Smite");
Videojuegos Fortnite = new Videojuegos("Fornite");

Smite.inicia(); //Se ha invocado a su metodo. 
```

### Paradigma de programación orientada a objetos
Vamos a definir algunas palabras antes.
> La R.A.E. define paradigma como: Teoría o conjunto de teorías cuyo núcleo central se acepta sin cuestionar y que suministra la base y modelo para resolver problemas y avanzar en el conocimiento.
En programación, sería como el conjunto de reglas a seguir para desarrollar software.

La **Programación Orientada a Objetos** (La asignatura), programamos (modelamos objetos) para que cada instancia tenga una responsabilidad en una aplicación. El funcionamiento del programa viene dado que estas instancias trabajen con otras (Enviar mensajes) o hagan cosas (Ejecuten sus métodos).

El objetivo siempre va a ser tener una alta cohesión y un bajo acoplamiento. 

## Atributos y Métodos
### Atributos y métodos de instancia
Cuando describimos una clase, también debemos incluir los atributos de esa clase, que pertenecerá a cada instancia. Estos atributos son las variables de cada objeto (Nombre, Id...). Y el estado de cada objeto se describe mediante los valores de estos atributos. 

Los métodos, también definidos como funciones, son definidos en una clase y están conectados a los objetos (de esa clase).
### Atributos y métodos de clase
Los atributos de clases, almacenan información que está asociada a la propia clase **NO** a cada instancia.

Por lo tanto son globables y pueden usarla cada instancia de esa clase.

A la hora de diseñar este tipo de atributos, es obligatorio pensar que debe ser un uso **GLOBAL** y que va a ser información **común** a todas las instancias.

Ejemplos:
```Java
class Clase{
	static private int numClases = 0;
  static int getNumClases (){
  	return numClases;
  }
	private String nombre;
  Clase (String n){
  	nombre = n;
    numClases++;
  }
}
```
```Ruby
class Clase
	@@num_clases = 0 // Atributo de clase
  def self.num_clases
  	@@num_clases
  end
  
  def initialize (nom)
  	@nombre = nom //Atributo de instancia
    @@num_clases +=1
  end
end
```
### Pseudovariables
Tanto en Java como en Ruby, hay palabras reservadas para referenciar al propio objeto. Estas son:
- Java: this
- Ruby: self
### Especificaciones de acceso. Visibilidad
Existen niveles de acceso a atributos y métodos, donde nos encontramos:
- Privado: Solo la propia instancia o clase puede acceder.
- Paquete: Sin restricción dentro del mismo paquete.
- Público: Sin restricciones.

> Por buenas praxis, siempre vamos a usar la regla más restrictiva. 
{.is-danger}

## Construcción de objetos
### Constructores
Siempre que vayamos a usar un constructor, primero es obligatorio su creación, y esta creación implica necesariamente reserva de memoria y inicialización.  Como vimos en anteriores asignaturas, los constructores se encargan de inicializar las instancias.
- Clases-plantillas: Mismo nombre de la clase, invocados automáticamente usando new.
- Clases-objetos: Pueden tener otro nombre, suelen ser métodos de clase.
#### En Java
Sus caracteristica son:
- Mismo nombre que la clase.
- Solo se usan para inicializar los atributos.
- Pueden haber varios con distintos parámetros.
- Se debe usar la palabra "new" para construir un objeto.

### Mémoria dinámica y pila
