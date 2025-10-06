---
title: Aritmética entera y modular
description: 
published: true
date: 2025-10-06T18:37:40.117Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:45:03.771Z
---

# Sistemas de numeración
## Definición de números naturales

Vamos a empezar, con la definición de las números naturales.


Podemos definir los números naturales, como aquellos que usamos para enumerar, incluyo en el 0. Tiene una serie de propiedades que son:
- Conmutividad
- Existe un número neutro 0, que cualquier número sumado a el es el mismo número. Con el producto es el 1.
- Está ordenado, desde el 0 hasta el infinito.

## Algoritmo de la división

El algoritmo de la división lo podemos definir como
Sean $a,b \in \mathbb{N} \text{ con } b \neq 0$. Entonces existen números $c, r \in \mathbb{ N }$ tales que cumplen:
- $a = b * c + r$.

## Sistema decimal
Es el sistema que conocemos, es decir el que está en base 10. $(0,1,2,3,4,5,6,7,8,9)$. Es decir el número 4853, podemos escribirlo como.

$a = 4853$
$a = 4 * 10^{3} + 2 * 10^{3} + 5 * 10^{3} + 7 * 10^{0}$

Así que podemos decir lo siguiente:
Sean $a,b \in \mathbb{N} \text{ con } a \neq 0 \text{ y } b \geq 2$. Entonces existen números $m \in \mathbb{N}, m \neq 0 \text{ y } a_{0},a_{1}, \dots ,a_{m} \in \mathbb{N}$  tales que cumplen:
- $a \leq a_{i} \leq b$.
- $a = \sum_{k=0}^{m} a_{k}*b^{m}+a_{m-1} *b ^{m-1} \dots +a_{1} *b + a_{0}$.
- $a_{m} \neq 0$.

## Operaciones
Las operaciones las podemos realizar en cualquier base de la misma manera, solo debemos tener en cuenta un detalle importante.
En base 10, la que conocemos, cuando llegamos al número 9, cambiamos el simbolo a 10. Si por ejemplo lo hacemos en base 6, cuando lleguemos a la cuenta 5+1, en vez de que sea 6, es 10.

## Cambios de base
Para hacer cambios de base, debemos tener en cuenta dos cosas.
1. Multiplicar si tenemos una base menor a la que queremos llegar. Ejemplo, $253)_{6} = 2*5^{3}+5*5^{2}+3*5^{1}$
2. Dividir si tenemos una base mayor a la que queremos llegar. Ejemplo, $450)_{10}$ deberemos dividir el número 

## Truco con Binarios
Con los números binarios, podemos hacer un cambio más sencillo al octal y al hexadecimal. Esto es debido a que el binario, al estar en base 2, las potencias de dos llegan a 8($2^{3}$) y a 16($2^{4}$).

Para hacer este truco, cuando tengamos un número binario y queramos pasarlo a octal, simplemente deberemos agrupar de 3 en 3 los números y leerlo como si fuera decimal. Al igual pasa con el hexadecimal.

# Representación en complementos

Como hemos hecho anteriormente, ahora vamos a describir el algoritmo de la división del conjunto $\mathbb{Z}$.

## Algoritmo de la división de enteros $\mathbb{Z}$
Sean $a,b \in \mathbb{Z} \text{ con } b \neq 0$. Entonces existen números $c,r \in \mathbb{Z}$ tales que:
- $a=b*c+r$.
- $0 \leq r < |b|$.

Claro, esto es igual que con el conjunto $\mathbb{N}$, sin embargo debemos tener en cuenta que aquí tenemos valores negativos. Se van a describir 4 ejemplos para poder entenderlo.

> Cuando decimos div es el cociente. Con mod, queremos el resto.
{.is-info}

- Ambos son positivos: Esto es una división normal y no jugaremos con ningún valor. 
147 div 5 = 29 | 147 mód 5= 2 | $29*5+2=147$.
- El divisor es negativo, en este caso el cociente también será negativo, para que el resultado sea positivo.
147 div (-5) = -29 | 147 mód 5= 2 | $(-29)*(-5)+2=147$
- El cociente es negativo, aquí ya cambia la cosa, en este caso vamos a usar un digito mayor al del cociente y restaremos la diferencia con el divisor para obtener el resto.
-147 div 5 = -30 | -147 mód 5= 3 | $(-30)*5+3=-147$
- Tanto cociente como divisor es negativo. Aplicamos la misma logica que antes resultando en un valor negativo.
-147 div -5 = 30 | -147 mód -5= 3 | $30*(-5)+3=-147$


## Complementos
Cuando hacemos una suma como puede ser 187 + 34, tenemos muchos metodos para realizarlo. Un metodo es con el complemento de 10. 
> Aunque no sea suceptible a examen, es recomendable realizar los aprenderlo para poder aplicarlo en binario.
{.is-warning}

Si $x$ es un número positivo, lo que haremos será añadirle 0 a su izquierda, tantos como necesitemos.

Sin embargo, si $x$ fuera negativo, para poder representarlo como $-x$, vamos a sustituir cada cifra con lo que le falta llegar hasta 9. Tras esto le sumaremos uno para que tenga sentido la operación que explicaremos. Ejemplo -25, sería 75.

Bien una vez tengamos esto, lo que haremos será usar la suma para poder restar. Ejemplo:

$65-25= 065+975 = 1040$.

Claro en este caso parece que nos ha salido un número completamente distinto sin embargo, como hemos operado con 3 dígitos, todo aquello que sea exceso se elimina. En este caso eliminaríamos el 1, y podemos comprobar que nos saldría $040 = 40$.

¿Y si lo hicieramos al reves?
Vamos a hacer $25-65$
Esto lo traduciremos a $025+935= 960$.  

El resultado no es correcto, ya que nos quedaría el último paso. Como hicimos antes, al invertirlo que hicimos fue intentar llegar a 1000, haremos lo mismo con el resultado, Así que haremos $1000-960 = 40$. O calcular cuantos valores nos queda para llegar a 1000.


## Complementos de 2
Esto es importante porque un ordenador solo entiende $0$ y $1$. Con esto en mente, es facil hacer operaciones matematicas en binario, sin embargo para hacer restas es algo más complejo, ya que necesitariamos de otro recurso extra en los ordenadores para puedan realizarlo.

Es aquí donde entra el complemento, usamos el inverso para que actue como una resta, cuando realmente estamos sumando.


Pongamos que hacemos uso de 8 bits. $2^8=256$, sin embargo también queremos representar los negativos, por lo que usaremos 1 de esos bits para indicar el signo.
Con esto con 8 bits podemos representar desde el -128 hasta el 127.

Lo único donde deberemos fijarnos es a la hora de hacer el inverso de un número binario, esto lo haremos de la siguiente manera:
0010 1010 => 1101 0101 +1 => 1101 0110

De esta manera hemos representando el número 42.
Podemos describir esto como: $2^{7}*n-2^{6}*n+2^{5}*n+2^{4}*n+2^{3}*n+2^{2}*n+2^{1}*n+2^{0}*n$.
Siendo n el valor del bit en ese momento, es decir o 1 o 0.

### Overflow
Overflow consiste en un error provocado por desbordamiento de la memoria, es decir, nos hemos pasado de los bits usables y hemos generado un valor que no le corresponde realmente.

Si intentamos sumar $57 + 95$ nos dará $152$, sin embargo si restringimos a base 2 y con 8 bits tenemos el siguiente problema:
$00111001+01011111=10011000$

Claro el número obtenido haciendo la formula anterior es $-104$. Por lo que no corresponde correctamente

Igualmente pasa con la resta, si restamos dos valores muy grandes como es $-54-89=-143$
Sin embargo en binario con 8 bits:
$11001010 + 10100111 = 1\text{ } 0111\text{ } 0001$

Como podemos observar, tenemos 1 bit de más que es desechado entonces el valor que nos da es:
$01110001$, que le corresponde al número $113$

# Divisibilidad
Divisibilidad o también conocido como Teorema Fundamental de la Aritmetica.

Encontramos la definición de la siguiente manera:
Sean $a,b$, dos números enteros. Decimos que:
- $a \text{ divide a } b$.
- $b \text{ es multiplo de } a$.
- $a \text{ es divisor de } b$ y por lo tanto lo escribimos como $a|b$.

**SI** existe un número entero $c$ tal que $b=a*c$.

Podemos encontrar entre sus propiedades:
- Para cualquier $a \in \mathbb{Z}$ se tiene que $1|a$ y $a|0$.
- Si $a|1$ entonces a = 1 ó a = -1. Pasa alreves con el cero que es $0|a$.
- Si $a|b$ y $b|a$ entonces $a=\pm b$.
- Es transitiva.

## Máximo común divisor
Sean $a,b$ dos números enteros, decimos que d es un máximo común divisor de $a$ y $b$ si:
- $d|a$ y $d|b$ (d es divisior común de a y b)
- $c|a$ y $c|b$ entonces $c|d$ (De todos los divisores, es el más grande).

Por ejemplo: $mcd(30,36)=6$

## Mínimo común múltiplo
Sean $a,b$ dos números enteros, decimos que m es un mínimo común múltiplo de $a$ y $b$ si:
- $a|m$ y $b|m$ (m es mñultiplo común de a y b)
- $a|n$ y $b|n$ entonces $m|n$ (De todos los múltiplos es el más pequeño).

Por ejemplo: $mcm(30,36)=180$

## Números primos
Podemos definir los números primos de dos maneras:
- La más conocida: Los números primos son aquellos cuyos únicos divisores son 1 y el mismo. (Además de -1 y si mismo pero en negativo.
- Matématicamente: Un número primo es aquel número entero, distinto de -1,0 y 1, que cumple: $p|ab => p|a \text{ ó } p|b$

## Teorema fundamental de la aritmética
Nos dice que podemos expresar cualquier número de la siguiente manera:
Sea $n \geq 2: n=p_{1}^{e_{1}}*p_{2}^{e_{2}}*p_{r}^{e_{r}}$

Ejemplo, podemos expresar el número 700 como $700=2^{2}*3^{0}*5^{2}*7$

Como te has habrá dado cuenta, hemos puesto $3^{0} = 1$, esto es porque podemos añadir cualquier valor, siempre y cuando lo elevemos a 0, excluyendo cuando sea esencial.

Bien con el ejemplo anterior podemos expresar 700 como:
$2^{0}*5^{0}*7^{0}=1$.
$2^{0}*5^{1}*7^{0}=5$.
$2^{0}*5^{2}*7^{0}=25$...

$2^{2}*5^{2}*7^{1}=700$.

Como resultado obtenemos que $D(700)=\{1,2,4,5,7,10,14,20,25,28,35,50,70,100,140,175,350,700\}$.

Todos los valores son los divisores de 700.

Ahora bien, si queremos expresar los divisores comunes entre dos valores, podemos aplicar lo siguiente:
$mcd(a,b)=p_{1}^{min\{\ e_{1},f_{1}\}}*p_{2}^{min\{\ e_{2},f_{2}\}}...$
$mcm(a,b)=p_{1}^{max\{\ e_{1},f_{1}\}}*p_{2}^{max\{\ e_{2},f_{2}\}}...$