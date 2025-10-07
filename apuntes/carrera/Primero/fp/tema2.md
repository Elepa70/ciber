---
title: Condicionales
description: 
published: true
date: 2025-10-07T18:51:23.613Z
tags: 
editor: markdown
dateCreated: 2025-10-07T18:51:23.613Z
---

# Condicionales
Cualquier algoritmo puede ser construido siguiendo un control de flujo. Este control de flujo, es la forma en la que el programa va realizando las instrucciones.

Podemos encontrarnos los controles de flujo estándar:
- Secuncial.
- Selectivo o selección.
- Repetitivo o iterativas.

## Secuencial
Es el formato predeterminado del flujo de control, donde todas las instrucciones se realizán en el orden que está hecho (De arriba hacia abajo). Es decir se realiza una detrás de la otra.

Ejemplo:
```C++
#include <iostream>
using namespace std;

int main (){
	int a, b, resultado;
  
  a = 5;
  b = 2;
  
  resultado = b-a;
  
  cout<< "El resultado de la resta "<< a << " y "<< b << " es "<< resultado << endl;
  return 0;
}
```

## Selectivo
Estas estructuras depende de unan decisión lógica para realizarse 