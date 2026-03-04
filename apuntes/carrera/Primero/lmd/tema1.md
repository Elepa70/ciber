---
title: Álgebra de Boole
description: 
published: true
date: 2026-03-04T15:27:40.131Z
tags: 
editor: markdown
dateCreated: 2026-02-25T11:10:30.264Z
---

# Álgebra de Boole
El primer tema que vamos a tratar, consiste en el Álgebra de Boole.
## Definición
Un Álgebra de Boole es un conjunto $B$ con dos operaciones binarias internas:
- Suma ($+$ o $\cup$)
- Producto ($*$ o $\cap$)

Con estas operaciones se cumplen las propiedades de:
- Asociatividad.
- Conmutatividad
- Elemento neutro (Para la suma es el 0 y para el producto es el 1)
- Existencia de un elemento complementario, es decir, que para $A$ existe un $\overline{A}$ .

### Propiedades
De las anteriores definiciones podemos obtener una serie de propiedades.
- Idempotencia: $x+x=x$ y $x*x=x$.
- Dominación: $x+1=1$ y $x*0=0$.
- Absorción: $x+(x*y)=x$ y $x*(x+y)=x$.
- Propiedad cancelativa: $x+y=x+z$ y cumpliendo $x*y=x*z$, entonces $y=z$.
- Doble complementario: $\overline{\overline{x}}=x$.
- $x+(\overline{x}*y)=x+y$ y $x(\overline{x}+y)=x*y$.
- Leyes De Morgan: $\overline{X*Y}=\overline{X}+\overline{Y}$ y $\overline{X+Y}=\overline{X}*\overline{Y}$.

> Los más importantes a aprender son: Idempotencia, Dominación, Doble Complementario y las Leyes De Morgan, ya que el resto es posible que lo obtengamos de las anteriores.
{.is-info}

Cuando tengamos una propiedad, tenemos que tener en cuenta la **propiedad dual**, donde se hace un intercambio de $+$ y $*$, y también los $0$ y $1$.

> Si una propiedad es cierta, también lo es su propiedad dual.
{.is-success}

### Teorema
> El teorema puede ser confuso, con un ejemplo es más guiado.
{.is-warning}

Si $(B,+,*,0,1,\overline{ })$ y $(T,+,*,0,1,\overline{ })$ son algebras de Boole, entonces $BxT$ es álgebra de Boole.
Entonces podemos hacer:
- Operaciones: $(b_{1},t_{1})*(b_{2},t_{2})=(b_{1}*t_{1},b_{2}*t_{2})$ y $(b_{1},b_{2})+(t_{1},t_{2})=(b_{1}+b_{2},t_{1}+t_{2})$.
- Elemento neutro: $(1,1)$ es elemento neutro para el $*$ y el $(0,0)$ es elemento neutro para $+$.
- Elemento complementario: $\overline{(b,t)}=(\overline{B},\overline{T})$.


#### Ejemplo del teorema
> Puede dar a confusión ya que ha sido copiado y interpretado.
{.is-danger}

Definimos a $B$ como $(B,+,*)$, es decir tenemos verdadero o falso (1 o 0).
Definimos a $B^{2}$ como: $B^{2}=B*B=\{(0,0),(0,1),(1,0),(1,1)\}$.

Esto son todos las posibles combinaciones que podemos hacer con los elementos dados.

Si hacemos las operaciones anteriores, debemos ir con cada elemento con el que ocupa la posición.

> Siempre trabajaremos con un $B^{n}$ donde $n\geq1$.
{.is-info}


## Órdenes
Debemos recordar lo dado en Algebra Lineal.

Un orden parcial en un conjunto P es una relación binaria ($\leq$), que cumple:
- Propiedad reflexiva: Para cualquier $a \in P, a\leq a$.
- Propiedad antisimétrica: Si $a\leq b$ y $b\leq a$ entonces $a=b$.
- Propiedad transitiva: Si $a\leq b$ y $b \leq c$ entonces $a \leq c$.

> Tras esto vemos los diagramas de Hasse, debido a la falta de medios para representarlos, recomiendo acudir a fuentes fiables de Internet.
{.is-info}

## Expresión booleana
Antes de definirlas, vamos a explicar sus caracteristicas:
- Literales: Aquellos elementos que toman como valor true or false (1 o 0), pudiendo ser variables, o complementario de variables.
- Recurrente: Definimos la recurrencia como, si $E_{1}$ y $E_{2}$ son expresiones booleanas, la suma o "or" también lo sera, el producto o "and" también, y el complementario de estos también.

Dada las anteriores definiciones, tenemos entonces que una expresión booleana la construimos en base de las anteriores reglas.

Ejemplo:
Dado $X=\{a,b\}$, entonces $1,a+b,\overline{AB}+b+0$ son expresiones booleanas, donde los literales son $a,\overline{A},b,\overline{B},0 \text{ y }1$.

La tabla de verdad, nos sirve para poder evaluar las expresiones. Aunque puede ser un proceso lento o tedioso, es el mejor metodo existente hasta el momento, ya que si pudieramos encontrar un algoritmo mejor, entonces habríamos resuelto uno de los problemas del millón.

A un conjunto de funciones booleanas en $n$ variables. (Escrito: $F^{n}=\{f:B^{n}\rightarrow B\text{ es función booleana}\}$. Tambiésn es un álgebra de Boole.

Con la particularidad de $F^{n}$ tiene $2^{2^{n}}$ elementos.

Ahora que estamos hablando de álgebra de Boole del tipo $F^{n}$, debemos tener en cuenta que los átomos, son aquellas funciones donde solo exista un valor 1 para un único elemento de $B^{n}$.

### Minterms
Los minterms $m$, sobre un conjunto de $X=\{x_{1},x_{2}...\}$ es una expresión que recopila aquella una función de $F^{n}$, una tupla por así decirlo.

Cuando hayamos queremos dar una función por escrito que cumpla una expresión, lo que solemos escribir es la **Forma Normal Disyuntiva**, esta forma escrita de la siguiente manera $xyz+xy\overline{Z}$.


### Maxterm
Por otro lado los maxterms, aunque sea similar, se expresa con una suma, es al contrairo del minterm. Por otro lado aqui escribimos la **Forma Normal Conjuntiva**, donde en vez de ir agrupandolo por multiplicacion y juntarlo en suma, lo que hacemos es juntarlo en suma y ir uniendolo en multiplicaciones, es decir:
$(x+y+z)(x+y+\overline{z})$.

### Expresión booleana dual
Recordamos que cuando damos algo dual, es el contrario de la aplicación, en este caso, lo que estamos dando es que en vez de sumar multiplicamos, pero nunca hacemos el contrario.

Decimos que una función booleana $f$ es autodual si $f=f^{d}$.



## Circuitos lógicos
Las funciones booleanas, nos sirve para modelizar el diseo de circuitos electrónicos. Con esto podemos desarollar las puertas lógicas que son: NOT, AND y OR.
> Es recomendar ver el temario de TOC, para poder entender el diseño de las puertas lógicas.
{.is-warning}

Los circuitos con varias salidas, indica que al final no caban en ningún lado, simpelmente es puramente continua


### NOT
Invierte los bits. ( Dibujo: triangulo con final circular)
### AND
Solo es 1 cuando ambas señales es 1. (Dibujo: Elipse cortado por la mitad de forma recta)
### OR 
Es 1 cuando una de las dos señales es 1. (Dibujo: Elipse, más picada, cortado por la mitad de forma ovalada)

### Suma de dos bits con acarreo / Suma parcial
Este tipo de suma, es aquel donde sumamos ambos bits, pero cuando ambos valgan uno, se hace un acarreo (es decir, aumentar en 1 el siguiente valor).

Para hacerlo con puertas lógicas primer debemo shacer la parte de la suma normal, pero donde no hay 2 bits positivos, es decir: $\overline{X}y+x\overline{Y}$. Y por otro lado tendremos $xy$. Con esta tecnica podemos abrir el dibujo tanto como queramos.

### Complemento a dos
El complemento a dos nos sirve para poder deducir que simbolo lleva el número, es decir, saber si es positivo o negativo. El complemento a dos, lo que hacemos es con el número binario, añadimos un bit más para poder saber el signo. 

En caso de que el valor sea negativo, lo que hacemos es alternar los valores 0 por los 1 y los 1 por los 0, y tras eso le sumamos 1.

### Resta
En la resta lo que solemos hacer es volver uno de los dos números en complemento a dos y después hacemos una suma de ambos valores.
## Simplificación de circuitos
Para la simplificación de circuitos, vamos a ver dos métodos:
- Mapas de Karnaugh: Donde se requiera pocas variables.
- Método de Quine-McCluskey: Es muy largo, sin embargo es general. Cuantas más variables, más pasos, $2^{n}$ variables.

EN si es un problema complejo, ya que no hay un método eficiente para poder realizarlo.
### Mapas de Karnaugh
Los inventó el ingeniero, matemático y físico Maurice Karnaugh. Para el método de Karnaugh lo que hacemos:
1. Haremos una tabla o matriz de mintems, donde cada en las columnas tenemos unas variables alternando entre complementarios o no, y en la zona de las filas igual. Se recomienda poner primero los complementarios y después los "normales". Cada celda, corresponde a un minterm distinto, dependiendo de cúal estemos representando.
2. Según tengamos en las función, vamosa  añadir 1 donde se cumpla la unión de las filas con las columnas.
3. Cuando hayamos rellenado las casillas, si hay una fila o columna, que sea al completo 1 (NO DIAGONAL), podemos sacar factor común en la expresión ese valor para poder reducirlo.

En caso de tener cinco variables es necesario tirar por matrices tridimensionales, o dos matrices.