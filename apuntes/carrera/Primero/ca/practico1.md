---
title: Apuntes para el examen practico 1
description: 
published: true
date: 2025-11-12T10:13:40.141Z
tags: 
editor: markdown
dateCreated: 2025-11-12T10:13:40.141Z
---

# Apuntes para examen practico 1
Realizado para hacerlo en máxima.

## Primeros pasos - Cosas esenciales
Siempre que queramos ejecutar algo, debemos tener en cuenta que debemos poner el ";", y después la combinación de teclas <kbd>shift enter</kbd>, o <kbd>enter</kbd> númerico.

### Operacioens elementales
Suma 
```maxima
2+2;
```
Resta 
```maxima
2-2;
```
Producto
 
```maxima
2*2;
```

Cociente
```maxima
2/2;
```
Exponenciales
```maxima
2^2;
```

Raices y logaritmos, mostrar o no valor númerico.
```maxima
sqrt(2);
log(18); <--- Logaritmo neperiano
log10(18); <---- Logaritmo en base diez

sqrt(2),numer;
log(18),numer;
```

### Entrada y salidas
si ponemos al final del comando un "$", en vez de ";", no saldá por pantalla la ejecución.

Con la siguiente orden podemos alternar entre que salga o no por pantalla lo que deseemos.
 
```maxima
set_display('ascii);
set_display('xml);
```

### Constantes
Las constantes la vamos a representar con el caracter espcial %", por ejemplo:
```maxima
%pi;
%e;
%phi;
```
Si necesiamos mostrar por pantalla el valor que tiene, debemos poner numer al final.

### Historial
Podemos reusar lo que hemos realizado anteriormente con: 
```maxima
%;
%i2;
%o2;
```
Siendo en orden:
- Ultimo calculo.
- Segunda entrada.
- Segunda respuesta.

### Tipo de datos
Ya hemos explicado el numer pero nos queda el:
- Float: Nos muestra por pantallla la expresión decimal de un valor.
- bfloat: Similar al float pero elegimos nosotros la precisión que queramos darle.
```maxima
float();
float(sqrt(2));

fpprec : valor;
bfloat();
bfloat(sqrt(2));
```

### Trigonometricas
Las trigonometricas debemos tener en cuenta que son:
```maxima
sin();
cos();
tan();
```

Y las arcos son:
```
atan();
asin();
acos();
```

### Variables, constantes y funciones
Las variables las asignamos de esta forma:
```
variable:valor;

zimbawe:2;
```

Las funciones las expresamos como:
```
funcion.=valor de la funcion

f(x):=cos(x^2);
```
## Graficas
## Ecuaciones
## Derivadas e integrales
