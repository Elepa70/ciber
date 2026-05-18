---
title: Gestión de E/S Ficheros
description: 
published: true
date: 2026-05-18T16:45:59.558Z
tags: 
editor: markdown
dateCreated: 2026-05-11T16:50:06.739Z
---

# Gestión de E/S. Ficheros
## Introducción
Flujo, es una abstracción que representa cualquier fuente o consumidor de datos y que permite realizar operaciones de E/S de datos con él. Se puede ver como una secuencia de bytes que fluye desde o hacia algún dispositivos.

Tenemos tres tipos de flujos:
- Entrada: La secuendia de datos fluey desde un dispositivo de entrada.
- Salida: La secuencia de bytes fluye desde el program hacia un dispositivo de salida.
- Flujo de entrada/salida: Secuencia que fluye en ambos sentidos.

Por ejemplo, la cabecera "iostream", nos perite usar lso flujos de E/S estándares.

Las operaciones de E/S con dispositivos suelen ser lentas comparandose con la CPU o memoria de transferencia. Para aumentar esta efciacia, la E/S se comunica con un bufer intermedio para almacenar temporalmente los daots y cuando se llenan, los envia.
## Entrada/Salida
TEnemos dos tipos de E/S:
- Con Formato: Tiene una transofrmación de caracteres (Teclado), la transofrmación se hace mediante datos comprensible.
- Sin Formato: La información se transmite en bruto, sin transformación.

### Funcion put
La función ostream::put(), lo que hace es enviar un carácter c al objeto devolviendo una referencia.
### Funcion ostream::write()
Devuelve un areferencia al flujo que lo llama.
### Funcion istream::get()
Extrae un carácter del flujo y devuelve su valor convertido a entero, devolverá EOF si leemos más allá del último del carácter del flujo.
### FUncion istream::getline()
Es casi identico a get(), con la diferencia de extraer el delim del flujo.
### Función global getline()
Extrae caracteres del flujo y los almacenas como un string.
### Funcion istream::ignore()
Lo que hace es extraer caracteres del flujo y los elimina.
### FUncion istream::read() y istream::readsome()
Extrae un bloque de n caracteres del flujo y los almacena, normalmente se usa para archvios binarios. Ojo la unica diferecnia entre read y readsome, con readsome devuelve un número de caracteres extraidos con exito.

Algunas de las restricciones que tenemos en los flujos es:
- No podemos crear objetos ostream o istream.
- Los flujos no tienen definidiso ni constructo de copia ni operador=.
- Por tanto no es posible hacer asignaciones entre flujos.
- Tampoco es posible crear nuevos flujo smediante constructor de copia.
- No podemos pasar un flujo como argumento por valor en una función.
- Los flujos tampoco deben pasarse como argumentos const.
- Un flujo debe ser pasado por referencia o bien como un puntero al flujo.


## Flujos asociados a ficheros
Un fichero es una secuencia de bytes. Es por ello que podemos usar las funciones anteriores aquí.

Usaremos la biblioteca "ofstream".
Para trabajar con ficheros de texto, normalmente usaremos:
- >>
- <<
- get()
- getline()
- put()

### Apertura de fichero
Lo hacemos mediante una función llamada "open()". Lo que hace es abrir este flujo para poder trabajar, podemos abrirlo en distinto modo.
```C++
open(const char *filenmae, openmode mode);
mode = in // Lectura de archivo
mode = out // Salida de archivo
mode =in|out //Ambas
```

### Cierre de un fichero
De la misma manera que abrimos un flujo, tenemos el que cierra el flujo con "close()".


### Curiosidad
Cuando abrimeos el fichero, podemos hacer uso del if([fichero]), para ir usando el fichero como condición de que está abriendo.

## Estados de los flujos
## Manejo de ficheros en C
## Entrada/Salida con formato
## Flujos asociados a strings
