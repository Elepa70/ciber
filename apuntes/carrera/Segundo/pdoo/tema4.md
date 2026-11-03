---
title: Herencia
description: 
published: true
date: 2026-11-03T16:56:26.622Z
tags: 
editor: markdown
dateCreated: 2026-11-03T16:39:48.081Z
---

# Herencia
Consiste en un mecanismo que nos permite aquellos lenguajes orientados a objetos, que nos permite ahorrar código en distintas partes del código.

## Relación de herencia
La clase de la que se deriva se denomina padre, superclase, ancestro etc etc
La clase derivada se denomina hijo, subclase, descendiente.

La relación consiste en un "es-un":
- Un descendiente es un ascendiente.
- La relación es transitiva.
- Donde se espera usar una instancia de una clase, potencialmente, también se podrá emplear una instancia de alguna clase derivada.

Usualmente cuando hablamos de heredar, lo que se hereda es **TODO** el codigo de la clase padre, cada lenguaje tiene sus particularidades. 
## Tipos de herencia
Tenemos varios tipos de herencia:
- Simple: Cada clase tiene a lo sumo un ascendiente directo, y es el más usado en la mayoría de lenguajes de programación.
- Múltiple: Una clase peude tener varios ascendientes directos y heredar de todos ellos. 
## Redefinir métodos
Podemos redefinir métodos (Sobreescribir) cuando una clase proporciona una implementación alternativa al heredado. 
> Es decir, si tenemos un metodo charlar(), de persona y creamos una clase hija niño con charlar(), no es que sobreescriba el charlar() de persona, es que usa el de niño de forma predeterminada.
{.is-info}

Sin embargo existe la palabra reservada **super**, usada para poder ejecutar la implementación del método del padre.