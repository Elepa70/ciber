---
title: Condicionales
description: 
published: true
date: 2025-10-07T19:22:32.152Z
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
Estas estructuras depende de una decisión lógica para realizarse. Depende de la condición impuesta se le puede realizar una alternativa.

Para poner una condición hacemos uso de las operaciones lógicas (Están en [Introducción](/apuntes/carrera/Primero/fp/tema1) ).  Estas estructuras selectivas a su vez pueden ser simple, doble o múltiples.

### Selectivo - Simple
Estas ejecutan una acción siempre y cuando se cumpla una condición, en caso contrario, el programa continuaría sin realizarlo. Para poder expresarlo, usaremos el "if".

Ejemplo
```C++
#include <iostream>
using namespace std;

int main (){
	int a;
  
  cout << "Introduzca su edad.";
  cin >> a;
 
  if (a >= 18){
  	cout << "Usted es mayor de edad.";
  }
  
}
```

Este programa simple, lo que hace es decir que eres mayor de edad si tienes 18 o más, sin embargo no indica nada si eres menor, para esto están los selectivo dobles.

### Selectivo - Doble
Son capaces de ejecutar una alternativa, para que si o si se vaya a realizar algo de las dos.

Es decir, en el caso de que no seas mayor de edad, el programa puede dar otra salida, hacemos uso del else.

```C++
#include <iostream>
using namespace std;

int main (){
	int a;
  
  cout << "Introduzca su edad.";
  cin >> a;
 
  if (a >= 18){
  	cout << "Usted es mayor de edad.";
  } else {
  	cout << "Usted es menor de edad.";
  }
  
}
```

Ahora nuestro programa realizará algo si no cumplimos con la condición de ser mayor o tener 18.


¿Pero que pasa si vamos a necesitar más condiciones? Para ello usaremos la estructura de concionales multiples o Selectivo multiple.

### Selectivo - Multiple
En este caso ejecuta una de la alternativa en función de la condición qu ese cumpla. Es decir, si se cumple la condición 1, realiza la 1. Sino, comprueba con la 2 para realizarla y así hasta que se cumpla.
En caso de que no haya ningúna condición que lo complete, entonces el programa saldrá sin realizar nada.

```C++
#include <iostream>
using namespace std;

int main (){
	int a;
  
  cout << "Introduzca un mes pero con su número.";
  cin >> a;
 
  if (a == 1){
  	cout << "Enero";
  } else if (a==2){
  	cout << "Febrero";
  } else if (a==3){
  	cout << "Marzo";
  } else if (a==4){
  	cout << "Abril";
  } else if (a==5){
  	cout << "Mayo";
  } else if (a==6){
  	cout << "Junio";
  } else if (a==7){
  	cout << "Julio";
  } else if (a==8){
  	cout << "Agosto";
  } else if (a==9){
  	cout << "Septiembre";
  } else if (a==10){
  	cout << "Octubre";
  } else if (a==11){
  	cout << "Noviembre";
  } else {
  	cout << "Diciembre";
  }
  
}
```
> El editor es consciente de que hay un error en este ejercicio, sin embargo es puramente ilustrarivo para ver como funciona. El error es que si indicamos un número distinto de [1,11], nos dirá diciembre.
{.is-danger}

En el programa, aunque sea largo, podemos ver que depende del número que pongamos, nos dirá un resultado u otro, sin embargo si no cumple ninguno, que estuviera con anterioridad dirá Diciembre.


Ahora bien tenemos otra forma de escribirlo y es con "switch", el codigo resultaría en:
```C++
#include <iostream>
using namespace std;

int main (){
	int a;
  
  cout << "Introduzca un mes pero con su número.";
  cin >> a;

	switch (a) {
  	case 1:
  		cout << "Enero";
      break;
    case 2:
  		cout << "Febrero";
      break;
    case 3:
  		cout << "Marzo";
      break;
    case 4:
  		cout << "Abril";
      break;
    case 5:
  		cout << "Mayo";
      break;
    case 6:
  		cout << "Junio";
      break;
    case 7:
  		cout << "Julio";
      break;
    case 8:
  		cout << "Agosto";
      break;
    case 9:
  		cout << "Septiembre";
      break;
    case 10:
  		cout << "Octubre";
      break;
    case 11:
  		cout << "Noviembre";
      break;
    case 12:
  		cout << "Diciembre";
      break;
    default:
  		cout << "No se ha encontrado un número correspondiente a ese mes, por favor intentelo de nuevo.";
      break;
  }
}
```

Como podemos observar, tenemos una caracteristica especial y es que usamos el **break**, para poder salir del switch, y también tenemos el default, que consiste en que si no ha encontrado ninguna que le corresponda que efectue ese mensaje.
