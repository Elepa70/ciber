---
title: Metodología de la Programación
description: 
published: true
date: 2026-04-20T17:07:26.346Z
tags: 
editor: markdown
dateCreated: 2026-04-20T16:39:39.324Z
---

# Metodología de la Programación
En C++ se permite el uso de conjuntos de operadores con los tipos predefinidos que hacen que el código sea leible, esto nos ayuda sobretodo cuando tenemos tantas operaciones que pueden ser más engorrosa.

Cuando tenemos más de un campo en una clase, debemos aprender a sobrecargar los operadores para poder decidir le orden de estas clases.

Sobrecargar es una función o metodo, con la palabra operator_simbolo_(), que nos permite modificar lo que haga ese operador.

> No podemos modificar la sintaxis de los operadores, si sumar implica dos valores, deben ser dos valores.
{.is-warning}

## Operadores que no se puede sobrecargar
- .
- .*
- ::
- ?:
- sizeof

El resto de operadores se sobrecarga, eso sí uno a uno, pero no sobrecargar el ("+"), no implica que sobrecargarmos el ("+=").

## Formas de sobrecargar
Podemos sobrecargar como función externa o como función interna.
### Sobrecarga como función externa
Consiste en añadir una función externa a la clase, que recibirá dos objetos de la clase y devolverá el resultado de la operación.

Por ejemplo
```C++
Polinomio operador+(const Polinomio &p1, const Polinomio &p2);

//Para llamar a la función
v =p+q; // Es lo mismo que poner v= operator+(p,q);
```

En caso de que el primer operador sea de diferente objeto a la clase, es necesario que la declaremos como función externa.
### Sobrecarga como función miembro
En este caso, añadimos un método a la clase que recibirá un objeto de la case y devolverá el resultado de la operación.

```C++
Polinomio Polinomio::operator+(const Polinomio &p) const;

p+q // Es igual que p.operator+(q)
```
La única limitación que hay, es que no es posible sumar un float antes que el polinomio.

Estas sobrecarga necesitan tener acceos al código fuente de la clase y el primer operador es del tipo de la clase, si no, no se puede.

## Operador de asignación
Como vimos con el operador copia, debemos hacer lo mismo con el operador de asignación, ya que es posible que resulte a una doble eliminación de datos.

### Primera aproximación
Usando:
```C++
void operator=(const Polinomio &pol); //p =q, entonces p.operator=(q)
```
En este caso estamos copiando un polinomio en uno que ya existe, no creandolo.

Por esto es necesario que cuando lo declaremos, eliminemos auqellos valores que tenia.