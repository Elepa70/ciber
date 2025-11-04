---
title: Funciones
description: 
published: true
date: 2025-11-04T18:13:39.159Z
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

Se declará de la siguiente manera
```C++
void nombre_funcion(lista_paramettros){
	<declaracion_variables>
  <cuerpo_funcion>
}

// Como podemos ver, no tenemos un return.
```

## Ámbito de las variables
Consiste en definir donde existe y donde se declara esa variable, tenemos varios tipos de variables, clasificadas como:
- Locales: Declaradas y definidas dentro de un subprograma, distintas a las variables definidas en otros subprogramas y si otro subprograma declara una variable con el mismo nombre, este no interferíra.
- Globales:Están declaradas en el algoritmo principal y para todos los subprogramas, útil para anidadas.

Estas últimas no se recomiendan el uso. De hecho es mejor no usarla en absoluto.

Toda variable declarada en una función o bloque, consiste que son locales a esa función, donde no existen fuera del bloque que está declarado.

Si una variable la declaramos en el mismo bloque o función dos veces, lo que hacemos es "machacar" lo que tenemos de antes. 

## Paso a parámetros
La información entre el subprograma y el programa llamador, se establece a través de las lista de parámetros. Existen dos tipos:
- Paso por valor: Copia del valor de la vairable. "Fotocopia"
- Paso por referencia: Pasa una referencia de la variable. "Das el documento"

### Paso por valor
Lo que modifiquemos aquí no afectará al de verdad, simplemente lo usamos en el subprograma.

### Paso por referencia
Este es mas peligroso, ya que implica que una perdida de información o corrupción en este apartado, hace daño a la variable.