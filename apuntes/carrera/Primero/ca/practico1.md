---
title: Apuntes para el examen practico 1
description: 
published: true
date: 2025-11-13T11:59:07.192Z
tags: 
editor: markdown
dateCreated: 2025-11-12T10:13:40.141Z
---

# Apuntes para examen practico 1
Realizado para hacerlo en máxima.

## Primeros pasos - Cosas esenciales
Siempre que queramos ejecutar algo, debemos tener en cuenta que debemos poner el ";", y después la combinación de teclas <kbd>shift enter</kbd>, o <kbd>enter</kbd> númerico.


Si no carga la cuadra poner:
```
grid = true;
```
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

### Puntos
La estructura de los puntos es la siguiente
```
wxdraw2d(
        points([[x1,y1],[x2,y2]...]),
        o
        points([x1,x2,x3...],[y1,y2,y3...])
)
```
Al igual que las graficas, podemos añadirle color y podemos ponerle a su vez:
- "point_size=": El tamaño del punto.
- "point_type=": Que tipo de punto, normalmente usamos el 7.

Los puntos lo representamos como:
```
wxdraw2d(color=red,
        point_size=2,
        point_type=7,
        points([[-3,0],[1,7],[8,-1]]),
        xrange=[-4,9],
        yrange=[-3,3]
        );
```
## Ecuaciones
Las ecuaciones las definimos como como su fueran ecuaciones normales, por ejemplo:
```
eq:5*x^4-2*x^3+7*x^2-8=x^3-5*x;
```

Con esto lo podemos nombrar, sin embargo, si solo queremos una parte de la equcación vamos a poner:
```
lhs(eq); -> Left Half Solution
rhs(eq); -> Right Half solution
```

### Resolver ecuaciones
Podemos resolver ecuaciones **básicas**, con la orden solve, sin embargo debemos si tenemos un grado mayor que 4, debemos usar otras opciones.
```
solve(4*x^2-1=0,x);
```

En algunas situaciones debemos usar el float para poder obtener el resultado de forma correcta.

```
solve(4*x^3-2*x^2+5=5*x,x);
float(%)

float(solve(4*x^3-2*x^2+5=5*x,x));
```

La orden **subst**, es una orden que nos permite sustituir una expresión en otro lado. Ejemplo
```
ec:x=sqrt(x+1);
subst((ecuacion),incognita,variable);
subst((sqrt(5)+1/2),x,ec)
```

Para poder nombrar soluciones a ecuaciones debemos hacer uso del map, por ejemplo:
```
soluciones:map(rhs,solve(x^2-3*x+1=0,x));
nombre-variable:map(rhs,accion a resolver));
```

### Solución aproximada
Cuando tenemos una ecuación polinomica cuyo grado sea mayor o igual que 5, debemos usar otor tipo de sentencias, para ello tenemos por ejemplo:
to_poly_solve

```
to_poly_solve(4*x^5-2*x^4+3*x^3+18*x-7=0,x);

to_poly_solve(ecuación,variable);
```

### Find_root
El comando find_root, usa el teorema de ceros de Bolzando para poder hallar soluciones a ecuaciones no polinómicas, por ejemplo:
```
f(x):=sqrt(x)+log(x);

wxplot2d([f(x)],[x,0,2],[y,-2,6]);

find_root(f(x),x,0.2,1);

find_root(funcion,variable a comprobar, inicio, fin);
```

El proceso que seguiremos es mirar primero la grafica para determinar si hay o no un cambio de imagen, tras esto podemos usar find_root en un intervalo que nosotros deseemos y consideremos ideal.
## Derivadas e integrales

Antes de ver ver las derivadas e integrales, vamos a usar el comando limite.
### Limites

Nos sirve para poder determinar el comportamiento de una función hacia el más infinito (inf) o hacia el menos infinito (minf).
```
limit(funcion,x,inf)
limit(funcion,x,minf)
```
Si queremos hacer el limite hacia un valor debemos poner
```
limit(funcion,x,0,plus)
limit(funcion,x,0,minus)
limit(funcion,x,0)
```

### Derivadas
El siguiente comando que vamos a usar se llama diff, nos sirve para poder calcular derivadas, por ejemplo
```
diff(funcion,x);
diff(sin(x),x);
```

Si queremos la segunda o tercera derivada necesitariamos:
```
diff(sin(x),x,3);
```

### Recta tangente
Una vez visto la recta normal, para calcular la recta tangente nos debemos acordar de la formula de lar recta tangente que es:
**$y=mx+n \Leftrightarrow y=f(a)+f'(a)(x-a)$**.

Para poder escribirlo en maxima pondremos
```
define(f(x),sin(exp(x)));
define(df(x),diff(f(x),x));
define(tangente(x,a),f(a)+df(a)*(x-a)); 

wxdraw2d(
	explicit(f(x),x,0,3),
	explicit(tangente(x,1.5),x,0,3),
	points([[(1.5,f(1.5))]])
);
```

Lo que hacemos es definir cada parte por separado para poder calcularlo después todo junto. En este caso estamos representando la recta tangente en el punto 1.5.

### Estudios relativos
Los estudios relativos nos sirve para determinar el máximo y el mínimo de una función, para ello primero vamos a tener que calcular los puntos criticos de la función. Es decir aquellos valores que hacen que la derivada sea 0.
```
define(df(x),diff(f(x),x));
x1:find_root(df(x),x,0,1);
x3:find_root(df(x),x,1,2);
```

Tras esto podemos comprobar si son extremos relativos con la segunda función de la siguiente manera.
```
define(df2(x),diff(f(x),x,2));
df2(x1);
df2(x2);
```
Si el punto obtenido, y el resultado en la segunda derivada es $<0$, entonces es máximo relativo, si es $>0$ entonces es mínimo. Si fuera 0, entonces nos hemos equivocado.

### Polinomio de Taylor - No recuerdo si cae o no
Los polinomios de taylor, es una función especial que centrado en un punto a, con grado n, podemos encontrar un polinomio que se comporta igual que la función en torno a ese punto hasta la derivada en n.
```
taylor(f(x),x,0,8);
```

Para evitar problemas se recomienda convertirlo en un polinomio normal de la siguiente manera:
```
define(f(x),sin(3*x)+tan(x)+1);
define(p6(x),ratdisrep(taylor(f(x),x,0,6)));
```

### Integrales y Primitivas
Antes habiamos calculado la derivadas, ahora vamos a calcular las integrales, para ello simplemente debemos usar el comando integrate:
```
integrate(funcion,variable x o y);

integrate(sin(x)*exp(-3*x),x);
```
Es posible que nos pregunten sobre un parametro cuando no se sabe el valor, por ejemplo cuando ponemos "integrate(x^n,x);", nos preguntará el valor de n ya que puede variar la integral.


Hay veces donde no es viable poder usar integrate, para ello usaremos:
- romberg: Da como respuesta un número, aproximado a la integral definida.
- quadpack: Es un paquete con varias órdenes dependiendo de la integral.

Queadpack es mas completo ya que nos devuelve:
- Valor aproximado de la integral
- Error absoluto estimado
- Número de pasos hasta enocntrar el valor
- Código de error, cuando mas cercano al 0 mejor.

```
romberg(exp(-sin(x^2)),x,0,%pi);
quad_qags(exp(-sin(x^2)),x,0,%pi);
```
### Areas y curvas
Por último vamos a ver como calcular las areas y las curvas, para ello vamos a tener que calcular una integral en un rango especifico por ejemplo.

```

integrate(sqrt(4-x^2)-(-sqrt(4-x^2)),x,-2,2);
```

Sin embargo cuando nos tenemos que calcular el area entre dos funciones para ello vamos a calcular primero los lugares donde hacen cero ambas funciones con un find_root, ya que solve no se puede usar.

```
wxdraw2d(
	explicit(sin(x),x,0,3.14),
  color=red,
	explicit(cos(x),x,0,1.14)
  );
  a:find_root(sin(x)-cos(2*x),x,0,1);
  b:find_root(sin(x)-cos(2*x),x,2,3);
  
  area:-integrate(sin(x)-cos(2*x),x,0,a) + integrate(sin(x)-cos(2*x),x,a,b) - integrate(sin(x)-cos(2*x),x,b,%pi);
  float(area);
  
  
 	romberg(abs(sin(x)-cos(2*x)),x,0,%pi);
```

Ambos resultados son iguales realmente, asi que podemos escoger uno o otro modelo, el que preferamos.