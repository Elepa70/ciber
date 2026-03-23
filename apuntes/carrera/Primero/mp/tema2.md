---
title: Funciones (ampliación)
description: 
published: true
date: 2026-03-23T17:50:23.722Z
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