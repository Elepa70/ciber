---
title: Punteros y memoria dinámica
description: 
published: true
date: 2026-03-02T18:23:25.055Z
tags: 
editor: markdown
dateCreated: 2026-03-02T17:37:25.989Z
---

# Punteros y memoria din
Vamos a hablar sobre un nuevo tipo de dato llamado puntero.

Solemos tener un problema a la hora de conocer el tiempo de compilación la cantidad de memoria que se va a necesitar para almacenar los datos. El uso de arrays grandes supone un desgato de memoria enorme.

Para ello, existe el tipo de dato puntero, donde nos permite definir los espacios de reserva para el tiempo de ejecución y crear variables en tiempo de ejecución, eso si es responsabilidad del programador.

## Tipo de punteros
Los punteros contiene la dirección de memoria de otro lado, donde existe un tipo de puntero especial llamado dirección nula con valor 0.

La declaración consiste:
```C++
int * ptri; //Declaracion de puntero a entero.
```

Lo que hacemos en vez de declarar un valor, simplemente estamos reservando ese espacio para usarlo más adelante, aunque no tenga un valor.

Usualmente "ptri" se usa para punteros a enteros y "ptrc" se usa para punteros a caracteres.

## Operaciones con punteros
Bien ya sabemos que los punteros reservan un espacio de memoria, ahora vamos a ver los datos.

Los punteros usan dos caraceteres.
### Operador &
Este operador lo que hace es devolvernos la dirección de la variable.

Por ejemplo:
```C++
int i=5, * ptri;
ptri = &i;
``` 

Con esto, el puntero ptri, lo que está obteniendo la dirección de memoria de i.

### Operador *
Este operador de indirección, nos sirve para devolver el valor del objeto apuntado.
Con ejemplo:

```C++
char c, * ptrc;
ptrc = &c;
*ptrc = 'A';
```
Lo que hemos hecho en el ejercicio anterior, es modificar el valor que hay en ese puntero.

Podemos inicializar con la dirección de una variable, o apuntando a un lugar, que es la zona nula.
```C++
int a;
int *ptri=&a;

int *ptrI= 0; // Menos recomendado
int *PtrI = NULL; //Mas recomendado
int *pTrI = nullptr; // Igual que el anterior
```

Con los punteros, podemos hacer uso de las operaciones normales, es decir: <,>,<=,>=,!=,==.
> Ojo, debemos diferenciar de p1, con *p1, ya que uno compara el contenido y otro la dirección de memoria.
{.is-warning}

Cuando tengamos arrays, interectuamos igual, y si queremos apuntar a un valor del vector, tenemos que hacer
```C++
p=&v[i];
```

### Operadores aritméticos
Con los operadores +,-,++,-,+= y -=, los punteros funcionan de una forma casi similar a un número entero.

Cuando sumamos algo a un puntero de forma normal, lo que hacemos es avanzar en dirección de memoria.

## Punteros y arrays
Los arrays y los punteros tienen una gran relación. Ya que los arrays lo que hacen es reservar memorai para almacenar una serie de elementos del tipo que hemos puesto.

ES decir crea un puntero constantemente como hemos llamado el array, que apunta a la primera posición del mismo.

Es por eso que podemos hacer:
```C++
int v[5]={1,2,3,4,5};
cout << *v << endl; // Esto realmente devuelve 1, ya que siempre apunta a la primera posición.
cout << *(v+2); // Es equivalente a preguntar por v[2]
```

