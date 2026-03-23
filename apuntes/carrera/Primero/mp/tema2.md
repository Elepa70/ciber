---
title: Funciones (ampliación)
description: 
published: true
date: 2026-03-23T18:16:34.101Z
tags: 
editor: markdown
dateCreated: 2026-03-23T17:41:11.866Z
---

# Funciones (ampliación)
## Función main
Normalmente un programa de C++ comienza cuando el S.O. le transfiere control al main y finaliza cuando este acaba.

Aunque hemos usado el main de forma simple, podemos usar a main con dos argumentos:
```C++
main(int argc, char *argv[])
```
- Valor de retorno: Consiste en un int devuelto por main, informa al S.O. de posibles código donde; El 0 es Ok, y cualquier otro valor es un error.
- Argumentos de main: Tenemos el int argc ( Número de argumentos usados al ejecutar el programa) y el char *argv[] (Array de cadeas con cada uno de los argumentos.

## Referencias
Consiste en un alias para datos o objetos usado en las funciones usada como copia o por referencia. Auqnue también podemos usarlo para:
- Referencias como alias a otras variables.
- Devolución por referencia desde una función.

Para ello podemos hacer:
```C++
int a=0;
int &ref=a;
ref=5;
cout << a << endl;
```

En cuanto a devolución por referencia:
- Una función puede devolver una referencia a un dato o objeto.
```C++
int& dato(int *v, int i){
	return v[i];
}
```
- La referencia puede usarse directamente en la asignación.
```C++
int main(){
	int v[3]={1,2,3};
  int a = valor(v,3);
}
```
- O lado izquierdo de la asignación
```C++
int main(){
	int v[]={1,2,3};
  valor(v,3);
}
```

## Paso de parámetros a funciones por valor y referencia
El paso de parámetros por referencia, los valores de las variables $a$ y $b$ no se han modificado, sin embargo se han intercambiado sus copias en un entorno swap.

Para asignar un paso por referencia debemos tener en cuenta que debemos poner el "&", lo que hacemos realmetne es crear un "alias" con el contenido de a y b para poder hacer el cambio.

### Deducir paso por referencia o por valor
Lo que hacemos es:
- Un paso por valor, si el argumento que nos han pasado, es un metodo para obtener la solución.
- Paso por referencia, si el argumento es usado para almacenar a la salida.

## Paso con valor por defecto
A una función le asignamos un valor por defecto, es decir llamar una función donde ya hay uno de los dos argumentos que tiene un valor predeterminado.
```C++
void algo(int b, int c=1){}
```
## Sobrecarga de funciones
C++ nos habilita definir una función por nombre, tipo de argumentos, número de argumentos o orden de argumentos. No hace falta diferenciar en nombres.