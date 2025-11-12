---
title: Apuntes para el examen practico 1
description: 
published: true
date: 2025-11-12T10:46:42.721Z
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
Vamos a poner de nuevo como definir funciones pero con un extra
```wxmaxima
f(x):=2*x-1;
g(x,y):=x^2*y-2*x*y^2; 

define(h(x),expresión);
```
### Representar básico - wxplot2d
Para poder dibujar una función de forma básica, usaremos el comando:
```wxmaxima
wxplot2d(f(x),[x,-5,5]);

wxplot2d(funcion),[x o y, minimo de x o y, maximo de x o y]
```
Donde el minimo y el maximo es donde va a ser los limites de donde va a estar representada la función.

### Representar graficas con wxdraw2d
Ojo antes de representar gracias con este comando, debemos cargar el paquete con
```wxmaxima
load("draw");
```

La ventaja que trae wxdraw2d con respecto a wxplot2d, es que con draw podemos deibujar tanto explicitas como implicitas, es decir podemos representar esferas.

Para poder dibujar una función explicita haremos:
```wxmaxima

wxdraw2d(explicit(funcion,valor x o y, rango minimo, rango maximo);
wxdraw2d(explicit(cos(2*x),x,0,4*%pi));

```
### Representar graficas en implicita
Por otro lado para poder representar graficas en explicita debemos usar lo siguiente:
```
wxdraw2d(implicit(x^2+(y-1)^2=4,x,-2,2,y,-1,3));
```
### Colores y completar las graficas
Una vez sepamos representar las graficas, otra gran ventaja que trar wxdraw2d, sobre wxplot2d, es que podemos añadirle colores y distintas opciones para poder hacerlo más limpio visualmente, estas opciones son:
- "color=": Nos permite cambiar lo que venga después de un color en especifico.
- "line_width=": Podemos cambiar el grosor de la grafica a representar.
- "yrange=[]": Definimos el espacio que vamos a mostrar en y.
- "xrange=[]": Similar al anterior pero en x.
- "proportional_axes=xy": Ponemos ambos ejes proporcionados

Ejemplo:
```
wxdraw2d(line_width=2,
        color=red,
        explicit(x^2-1,x,-2,3),
        line_width=4,
        color=green,
        implicit(x^2-y^2=1,x,-3,3,y,-3,3),
        yrange=[-3,3]
        );
```
## Ecuaciones
## Derivadas e integrales
