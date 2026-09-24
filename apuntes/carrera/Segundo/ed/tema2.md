---
title: Abstractos
description: 
published: true
date: 2026-09-24T16:56:07.938Z
tags: 
editor: markdown
dateCreated: 2026-09-24T14:40:17.180Z
---

# Tipo de datos abstractos
## Definiciones de algunas palabras
A la hora de hacer código o implementar cualquier cosa en general, lo ideal es hacer documentación.
Definimos **documentación**: Son aquellas operaciones o especificaciones que ofrece un módulo.
Otro palabra a definir es **abstracción por especificación**, que serian aquellos metodos o detalles independientes de implementación, se resume en importa *el qué pero no el cómo*.

Dentro de un módulo hay que diferenciar dos cosas:
- Especificación: Aquellas características sintácticas (es un lenguaje donde indica las cabeceras de la funcion) y semánticas (lenguaje natural para guiar). Esta parte es importante ya que para trabajos en grupo hace falta que quede claro para que otros miembros del grupo sepan que necesitan.
- Implementación: Documento que presenta las caracterísitcas de forma internas al módulo.

La **abstracción procedimental**, consiste en reunir un monton de operaciones en una única operación.



## T.D.A. o Tipos de datos abstractos
Lo definimos como un tipo de datos que tiene asociado un conjunto de operaciones. Estas operaciones realizan una especificación independiente de la implementación.

Algunos ejemplos puede ser lso constructores, destructores, modficadores...

> Un consejo: A la hora de hacerle operaciones a los T.D.A, debemos intentar ser minimalistas.
{.is-success}

A la hora de implementarlos, debemos elegir primero una representación (tipo de rep), y basandonos en esta representación escogida, debemos dar una implementación de operación.

Ejemplo:
```C++
/* Vamos a representar un tipo de fecha */
// Representación: Representar una fecha en el calendario occidental

//REP:
class Fecha{
	private:
  	int dia, mes, anho;
}
```
La transformación de un tipo rep a la especificación, es lo que se denomina **función de abstracción**. Por ejemplo, en el ejemplo anterior lo que hacemos es fijar quien es el dia, quien es el mes y quien es el año. La definimos como: $f_{A}:rep \rightarrow T.D.A. \text{ (definido en la especificacion)}$.

