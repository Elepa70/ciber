---
title: Clases
description: 
published: true
date: 2025-11-18T17:56:43.732Z
tags: 
editor: markdown
dateCreated: 2025-11-18T16:39:51.836Z
---

# Clases
## Motivación
Hasta ahora solemos usar variables para todo, ya sean variables de un mismo tipo:
- Array unidimensionales.
- Registros (struct).

Pero esto genera el problema de que para poder almacenar datos, estos deben ser visible desde el exterior, y aunque pueda ser modificable mediante uso de funciones, nada puede imprimir interactuar con los otros valores. Y si no hay buenas credenciales, esto provocará que no podemos asegurar que los datos estén seguro.

La solución es la encapsulación, es decir, aunar datos y comportamientos en un único módulo. No accedemos al campo de forma directa, si no, necesitamos una función que está por medio.

Algunas de las ventajas que nos da es:
- Acceso seguro a los datos.
- Permite garantizar que los datos son siempre válidos.
- Se podría cambiar los campos (variables) de internos y todo funcionaría bien externamente.

## Programación orientada a objetos
Una clase es un tipo de dato complejo, que está diseñado por el programador, el cúal contiene:
- Funciones: Denominado métodos, con comportamientos.
- Datos: Se denominan atributos de las clases.

Las clases las definimos con:
``` C++
class (nombre_variable) {
};

int main () {
	(nombre_clase) (nombre_variable);
}
```

Dentro de las clases, tenemos que tener en cuenta que, cuando definimos variables, las llamamos objetos.
## Definición de clases
Una clase está compuesto por:
- Atributos o datos, que contiene la misma estructura de la clase y espacio de memoria propio.
- Métodos o funciones, funciones o procedimientos definidos dentro de la clase.

### Atributos
Un atributo, son aquellos datos que pertenecen a la clase que estámos usando. Por ejemplo para una persona: nombre, apellido y DNI (Si queremos añadir más cosas podemos hacerlo).

### Sintaxis
Antes del main ponemos:
```C++
// Todo esto es privado, no se puede visualizar desde fuera.
class (nombreclase){
	(tipo) (atributo);
	(tipo) (atributo);
  
private:
	(tipo) (metodo)((tipo) (nombre_argumento)...){
  }

//A partir de ahora, todo esto es publico.
public:
	(tipo) (metodo)((tipo) (nombre_argumento)...){
  }
};
```
Ejemplo:
```C++
class Point2D{
	int x;
  int y;
  
  public:
  	void moveUP(){
    	y++;
    }
    void modeDown(){
    	y--;
    }
};
```

Para poder usar las clases debemos hacer
```C++
//Declaración de la variable
Point2D punto1;

//Llamar un método
punto1.moveUP();
```