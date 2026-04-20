---
title: Metodología de la Programación
description: 
published: true
date: 2026-04-20T16:48:13.407Z
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
```
