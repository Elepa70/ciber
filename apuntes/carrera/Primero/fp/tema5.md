---
title: Funciones
description: 
published: true
date: 2025-11-04T17:48:32.674Z
tags: 
editor: markdown
dateCreated: 2025-11-04T17:23:19.785Z
---

# Funciones
Existe una linea de pensamiento donde se va a dividir los problemas en problemas más pequeñitos.

El problema principal soluciona mediante el programa o algoritmo principal, al igual que los subprogramas. Sin embargo el subprograma está dirigido por el programa principal.

Los programas y los subprogrmaas suelen seguir una guía de comunicación:
- El programa requiere de algo que tiene el subprograma, entonces lo llama, deteniendo el flujo de programa principal.
- El subprograma obtiene los contenidos que necesita y realiza las tareas, tras esto envia un retorno que es volver al punto del programa principal con los datos que haya usado o necesitado.

## Función
Matemáticamente la conocemos,  como $f(x)$.

Una función consiste en un "subprograma", que devuelve un único dato.

La invocación depende de los argumentos que le pasemos y deben ser admitidos.

Los nombres de la funciones deben ser significativo, es decir, debemos ser consciente de saber que hace cada cosa.

```C++
// Declaramos la funciónes con
<tipo de dato> <nombre de la funcion>(<parametros a recibir>){
	//lo que se haga, aqui
  return <valor a devolver>
}

// Ejemplo
int suma(int a, int b){
	int result;
  result =a + b;
  return result;
}
```

## Procedimientos
Los procedimientos no devuelven ningún valor, es simplemente encargado de un proceso específico.