---
title: Arrays, cadenas estilo C y matrices
description: 
published: true
date: 2026-02-24T20:21:46.909Z
tags: 
editor: markdown
dateCreated: 2026-02-24T20:21:46.909Z
---

# Arrays, cadenas estilo C y matrices
## Cadenas de caracteres

La cadena de caracteres es una secuencia ordenada de caracteres de longitud variable, donde nos permite trabajar con datos. En C++ tenemos cstring y string.

Dentro de un array de tipo char, tenemos un tamaño determinado que acaba en el caracter nulo, '\0'.

Cuando declaramos caracteres tenemos que tener en cuenta como lo declaramos ya que dependiendo de como lo hayamos iniciado, podemos tener un tamaño menor o mayor.

Cuando decalaramos una variable de tipo char, es igual poner
```C++
char nombre[X]="Algo";
char nombre[]="Algo";
```

Hay un problema con el 'cin' ya que busca un separador antes del dato, entonces si hay un espacio también se lo come, para ello tenemos el ```cin.getline(<cadena>,<tamaño>);```

Por ejemplo
```C++
char nombre[80];
cout << "Introducir nombre: ";
cin.getline(nombre,80);
cout << "El nombre introducido es: "<<nombre;
```

### cstring
Es una biblioteca que nos permite trabajar a un "alto nivel" con cadenas del tipo C, ya que nos permite copiar, devolver longitud, concaenar, comparar o buscar el puntero entre cadenas.
Esto es realmente util pero para hacer el cambio necesiatmos hacer lo siguiente:

```C++
int main(){
    char cadena1[]='Hola';
    string cadena2;
    char cadena3[10];

    cadena2=cadena1;
    strcpy(cadena3,cadena2.c_str());
```

Dentro de las funciones la importante son:
```strncpy(<cadena1>,<cadena2>.c_str(),int maxsize)``` = Copiar cadenas.

```strlen(<cadena>)``` = Longitud de cadena. Debe tener el caracter nulo.

```strncat(<cadena1>,<cadena2>,int maxsize)``` = Concatenar cadenas, ponemos limite.

```strcmp(<cadena1>,<cadena2>)``` = Comparar cadenas, si la cadena1 es menor lexicograficamente a la segunda, entonces devuelve un menor a 0, si es igual 0 y otro caso + de 0.

```strstr(<cadena1>,<cadena2>)``` = Devuelve un puntero de ocurrencia de la segunda cadena en la primera.

Todavia no sabemos que es exactamente el puntero, más adelante lo daremos !WARNING


## Decalaraciones de matrices de 2 dimensiones, es decir vectores/matrices
Para declarar una matriz de dos dimensiones podemos hacer
```C++
int main(){
    const int DIM_FILAS = X;
    const int DIM_COLUMNA = Y;
    double matriz[DIM_FILAS][DIM_COLUMNA];
}
```

Para inicializarlo podemos hacer:
- Forma segura, donde ponemos los valores entre llaves (int m[2][3]={{1,2,3},{4,5,6}};}
- Faltan elementos entonces se añade cero int m[2][2]={{1},{3,4}};
- Linealmente y cuando se complete una fila salta a la otra. m[2][3]={1,2,3,4,5};

Realmente lo que estamos haciendo es un array de arrays, por ello todos los elementos de las matrices se almacenan en un bloque contiguo de memoria.
La organizacion depende del lenguaje, ya que por ejemplo para C++, se hace por filas.


Cuando tenemos un elemento m[i][j], cuando el compilador desea acceder a un elemento [X][Y], debe pasar por la fila X y de ahí moverse al meneto Y.

La posición del elemento m[i][j] se calcula como i*COL + j;

### Operaciones con matrices
Debemos tener en cuenta las siguientes cosas:
- Acceso: Comienza a 0, y lo hacemos con Matriz[0][2].
- Asignación: Añadir elementos a una matriz. Matriz[0][1]= Matriz[1][1]+Matriz[2][1]
- Lectura y escritura: Con cout y cin.

Tenemos bucles para encontrar elementos aunque no vamos a verlo ahora mismo
