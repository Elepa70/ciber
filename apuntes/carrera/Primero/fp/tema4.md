---
title: Vectores, Matrices y Registros
description: 
published: true
date: 2025-10-28T11:18:54.173Z
tags: 
editor: markdown
dateCreated: 2025-10-21T17:00:06.294Z
---

# Vectores, Matrices y Registros

Los lenguajes de programación tienen datos primitivo, **SIN LIBRERIAS**, es decir: char, int, long, bool...

Sin embargo, si solo podemos usar, no seriamos capaces de crear infraestructuras como las de hoy en dia. Esto se verá más adelante en la asignatura Estructuras de Datos.

Existen tipos d edatos estructurados, que nacen de los datos primitivos, estos tipos de datos son:
- Estáticos: Consiste en un tipo de dato, donde el tipo de dato lo defines cuando lo compilas.
- Dinámicos: Conforme se vaya ejecutando el programa, el tipo de dato crece o decrece. Usualmente es más usado, sin embargo actualmente solo veremos estáticos.


Los tipos de datos simples, representan un único valor, una variable de tipo entero representa un único número entero.

Los tipos de datos estructurados pueden representar una colección de valores, las variables representan un conjunto de valores. 

## Vectores

Un array, es un conjunto finito y ordenado de elementos homogéneos. Es decir sabemos la cantidad de elementos que hay, con un orden impuesto y tiene el miso tipo de datos.

Un array, consiste en una estructura general, y pueden ser: vectores (Unidimensional), matrices (Bidimensionales, o tabla) o cubos (Mayor a 2 dimensiones).



Los vectores consiste en el array más simple, y se representan como un conjunto de elementos consecutivos de un mismo tipo a los que se pueden acceder mediante un índice. 
- Los índices: Empiezan con el 0, aunque esto no tiene porque ser siempre cierto debemos comprobar según donde estemos trabajando. 
- Rango: Conssite en la cantidad de elemetos que hay.

Podemos expresarlo como
```C++
v[0]
v[3]
v[i+i] \\ Ojo debemos primero haber declarado i, y debe ser entero.
```

> Ojo, si ponemos v[N], teniendo un array de tamaño N, esto fallará, similar pasa si buscamos un elementos que esta fuera por debajo del array. Este error se llama violación de segmento.
{.is-danger}

Los vectores, se almacenan en la memoria principal del equipo en orden adyacente, es decir todo junto.

Las variables o los vectores tienen las mismas funciones, es decir podemos declararla, asignarle valores, leerlo etc etc... 

Las operaciones dentro de los vectores, necesitamos ir elemento a elemento. 

### Declaración
```C++
// Inicio con valores
int vector[10] = {1,2,3,4,5,6,7,8,9,10};

// Sin valores
int vector_solo[3];

//Asignar valores
vector_solo [0] = 1;
vector_solo [1] = 19;
vector_solo [i] = a*b;

cin >> vector_solo [2];
```
Siempre que tengamos una variable en un array, la declararemos como una constante. 

Al igual que las variables, los vectores, debemos asegurarnos que tienen un valor asignado, si no. Podemos causar un error con que el vector tenga un valor desconocido.

## Matrices
Las matrices consiste en arrays de dos dimensiones, o más dimensiones. También podemos considerarlo un vector de vectores.

Aunque pueda considerase una "tabla", es decir posea filas y columnas, realmente podemos representarlo como un vecto de vectores, en vez de verlo como un conjunto de vectores (Es decir, una linea recta, que se divide en pocos vectores).

```C++
\\ Para declarar arrays haremos:
int v[N][M];

\\ Para acceder al valor del array:
v[0][0];
```
Para comprenderlo, debemos tener en cuenta que el primer valor ([M] e nuestro caso), hace referencia a la fila a la que queramos acceder, y la segunda ([N]), es nuestra columna.

Las acciones que podemos hacer con las matrices, son las mismas que los vectores, añadiendo la posibilidad de recorrido secuencial.


Este recorrido, lo solemos usar mediante el uso del bucle for.

## Dato String
Este dato es importante y por eso lo volvemos a ver aquí. Se considera un dato primitivo, aunque volvamos a verlo aquí.

En C, para declarar un char o variable habia el problema de que no se sabia cuantos caracteres se tienen.  Sin embargo en C++, usaremos String.

```C++ 
string s1;
string s2 = "hola"; // Importancia a tener las dobles comillas, ya que las comillas simples no sirven.
```

Funciona igual que cualquier variable, también podemos hacer comparación, ya que podemos comparar caracter a caracter.
> Es Key sensitive, por lo que diferencia entre mayusculas y minusculas.
{.is-danger}

Con las terminaciones:
- s.size() o s.length(): Comprobamos la longitud del string.
- s.[indice]: Indicamos el caracter que esta en ese indice.
- s.empty(): COmprobación de que está vacio.
- s3 = s1 + s2: La suma de strings, lo que hace es juntar ambos strings sin espacios.

## Registro o Struct
Los structs nos permiten solucionar una serie de problemas con respecto a los datos estructurados. Es como "una variable de variables".

```C++
struct <nombre_registro>{
	tipo_1 campo1;
  tipo_2 campo2;
};




\\ Van fuera del main
int main(){}


\\ Ejemplo
struct punto3d{
	double x;
  double y;
  double z;
};

int main(){
	punto3d p1, p2;
  
  cout << "Dime el valor de X del punto 1";
  cin >> p1.x;
  cout << "Dime el valor de Y del punto 1";
  cin >> p1.y;
  cout << "Dime el valor de Z del punto 1";
  cin >> p1.z;
  
  
  cout << "Dime el valor de X del punto 2";
  cin >> p2.x;
  cout << "Dime el valor de Y del punto 2";
  cin >> p2.y;
  cout << "Dime el valor de Z del punto 2";
  cin >> p2.z;
	return 0;
}
```

ESte tipo de variables son especiales ya que requieres de ser declaradas fueras del main, y para poder acceder a los miembors