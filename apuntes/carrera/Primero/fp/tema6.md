---
title: Ordenación y búsqueda en vectores
description: 
published: true
date: 2025-11-11T18:08:40.668Z
tags: 
editor: markdown
dateCreated: 2025-11-11T17:04:55.247Z
---

# Ordenación y búsqueda en vectores
## Introducción
Ordenar y búsqueda nos va a servir para la eficiencia computacional de los equipos, para poder realizar lo máximo en el minimo tiempo posible. 

La ordenación es la operación de organizar un conjunto de datos en un orden dado:
- Orden numérico crecimiento o decrecimiento.
- Orden alfabético directo o inverso.

La búsqueda es el encontrar algo (No se me ocurre mejor forma de decirlo).
- Podemos averiguar si un elemento pertenece o no.
- Nos facilitan las tareas automáticas.

## Ordenación
Vamos a usar varios métodos de ordenación.

### Ordenación - Método de la burbuja
En este orden lo que hacemos es hacer que los valores "floten" y se vayan comparando con los demás para ir hasta el final. Cuanto mayor sea el valor más lejos del vector va a llegar.
```C++
// declarar variables
// leer vector
for (i = 1; i < N; i++) {
 
 for (j = 0; j < N - i; j++) {
 	if (v[j] > v[j + 1]) {
 	aux = v[j];
 	v[j] = v[j + 1];
 	v[j + 1] = aux;
 	}
 
 }
}


\\ El mejorado

i = 1;
flag = false
while(i < N && !flag) {
 flag = true;
 
 for (j = 0; j < N - i; j++) {
 	if (v[j] > v[j + 1]) {
 	aux = v[j];
 	v[j] = v[j + 1];
 	v[j + 1] = aux;
 	flag = false;
 	}
  
 }
 i++;
}
```


### Ordenación - Selección y reemplazo
Es similar al anterior, con la diferencia de que el cambiamos completamente las posiciones. Da igual si acabará siendo mayor o no.
```C++
for (i = 0; i < N - 1; i++) {
 k = i;
 
 for (j = i + 1; j < N; j++) {
 	if (v[j] < v[k]) {
 		k = j;
 	}
 
 }
 
 aux = v[i];
 v[i] = v[k];
 v[k] = aux;
}
```
### Ordenación - inserción
En este metodo partimos con zona ya ordenada, y cuando añadimos valores, lo que hacemos es comparar si esfectivamente es mayor al anterior, en caso negativo se compara con los demás y ya se ordena.
```C++
for (i = 1; i < N; i++) {
 aux = v[i];
 j = i - 1;
 
 	while (j >= 0 && aux < v[j]) {
 	v[j + 1] = v[j];
 	j--;
 	}
  
 v[j + 1] = aux;
}
```

## Búsqueda
### Búsqueda secuencial
Consiste en un método sencillo, el cual consiste en recorrer todo el vector desde el principio hasta el final. 

Lo que hacemos es ir comparando los elementos uno a uno, y tiene la ventaja de que no tiene porque estar ordenado.
### Búsqueda binaria
En este caso, lo que hacemos es dividir el espacio que vayamos a usar en dos.
- Mayor que la mitad.
- Menos que la mitad.

Lo que hacemos es comparar el vector que tenemos con la mitad, si es menor nos quedamos con la parte de "abajo" y si es mayor te quedas con la "parte de arriba".

Ojo, tiene que estar ordenado si o si.