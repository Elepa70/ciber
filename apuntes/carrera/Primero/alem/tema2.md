---
title: Aritmética entera y modular
description: 
published: true
date: 2026-01-12T09:40:46.421Z
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
$a = 4 * 10^{3} + 2 * 10^{3} + 5 * 10^{3} + 7 * 10^{0}$.

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

## Algoritmo de la división de enteros $\mathbb{Z}$.
Sean $a,b \in \mathbb{Z} \text{ con } b \neq 0$. Entonces existen números $c,r \in \mathbb{Z}$ tales que:
- $a=b*c+r$.
- $0 \leq r < |b|$.

Claro, esto es igual que con el conjunto $\mathbb{N}$, sin embargo debemos tener en cuenta que aquí tenemos valores negativos. Se van a describir 4 ejemplos para poder entenderlo.

> Cuando decimos div es el cociente. Con mod, queremos el resto.
{.is-info}

- Ambos son positivos: Esto es una división normal y no jugaremos con ningún valor. 
$147 \text{ div } 5 = 29 | 147 \text{ mód } 5= 2 | 29*5+2=147$.
- El divisor es negativo, en este caso el cociente también será negativo, para que el resultado sea positivo.
$147 \text{ div } (-5) = -29 | 147 \text{ mód } 5= 2 | (-29)*(-5)+2=147$.
- El cociente es negativo, aquí ya cambia la cosa, en este caso vamos a usar un digito mayor al del cociente y restaremos la diferencia con el divisor para obtener el resto.
$-147 \text{ div } 5 = -30 | -147 \text{ mód } 5= 3 | (-30)*5+3=-147$.
- Tanto cociente como divisor es negativo. Aplicamos la misma logica que antes resultando en un valor negativo.
$-147 \text{ div } -5 = 30 | -147 \text{ mód } -5= 3 | 30*(-5)+3=-147$.


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

# Algoritmo de Euclides y su "extensión".
Para poder expresar un valor de la siguiente manera: $n \geq 2: n=p_{1}^{e_{1}}*p_{2}^{e_{2}}*p_{r}^{e_{r}}$. Primero debemos conocer cuál es su descomposición.

Para ello podemos realizar el motodo convencional, que consiste ir buscando los primos de cada valor, y tras ellos comparar aquellos elementos que se repiten en ambos valores.

Ejemplo para $a=1575$ y $b=363$, descomponiendo ambos valores obtenemos.
$a=3^{2}*5^{2}*7$ y $a=2^{4}*3*7$, entonces tomaremos los valores $3*5 \text{ y } 7$.



Sin embargo podemos usar el algoritmo de euclides, este consiste en ir dividiendo los valores hasta encontrar un resto 0.

Por ejemplo: $mdc(3337,2773)$, lo primero que haremos será dividir $3337/2773$.
$3337/2773=1 + 564$. Ahora dividremos el cociente entre el resto.
$2773/564=4 + 517$.
$564/517=1 + 47$.
$517/47=11 + 0$.

Por lo tanto el maximo común divisor, es 47.

Bien, esta ampliación, lo que haremos será buscar el coeficiente de Bézout.

> POR CORREGIR.
> {.is-danger}

Lamentablemente en este entorno no es posible mostrar la tabla guía que se realiza para poder hacerlo. Sin embargo vamos a explicarlo igualmente.

Lo que haremos con la tabla es realizar lo mismo que hemos hecho anteriormente, sin embargo de forma ordenada. Hasta que encontremos un valor que nos haga el resto 0.

Para ello la distribución de la tabla será:
a
b
$r_{1}$   | $c_{1}$

Bien, en $r_{1}$ , pondremos el resto obtenido entre dividir $a/b$, y en $c_{1}$  ponemos el coeficiente usado.

Tras esto, haremos como antes, dividir el $b/$r_{1}$, para obtener $r_{2}$ y $c_{2}$, seguiremos con $r_{1}/r_{2}$, etc etc etc   

Es decir:
$r_{1}=a-c_{1} *b$.
$r_{2}=b-c_{2} *r_{1}$.
$r_{3}=r_{1}-c_{3} *r_{2}$.

Una vez finalicemos, vamos a hacer la segunda parte de la tabla, una extensión.

Esta extensión esta formada por $u$ y $v$.

## Aritmetica modular
Para poder tener claro todo lo que viene después, debemos tener en cuenta lo siguiente $a,m \in \mathbb{Z}, m \neq 0. a \text{ mod } m$ Es el resto de la sificisión de $a$ entre $m$.

Por ejemplo $25 \text{ mod }7=5$, ya que $26=7*3+5$.

Dado esto para la congruencia, sea $m \geq 2$, dados $a,b, \in \mathbb{Z}$, decimos que:
$a \equiv b \text{ mod }m$ si $m|(b-a)$, $a \text{ mod } m = b \text{ mod }m$.

Es decir estamos buscando el minímo común multiplo.


Ahora lo que vamos a jugar es con las "bases", recordamos como hemos usado binario, octal, hexadecimal y decimal anteriormente, ahora haremos más o menos lo mismo. 
Cuando nos salga $\mathbb{Z}_{8}$, significa que estamos en base 8, es decir vamos de: $\{0,1,2,3,4,5,6,7,0,1,2...\}$.

Esto es importante ya que el $mcm$ de un número puede variar si estamos o no en decimal.


Y si hacemos cuentas con una modulo que no es 10, debemos tenerlo en cuenta. Por ejemplo, pensemos en un reloj, un reloj es $\mathbb{Z}_{12}$, pero cuando queremos poner las $4$ de la tarde por ejemplo, tenemos el formato digital $16$, o el $4$.

Debemos pensar todo el rato en que base estamos y ir encontrando la diferencia constantemente para poder ir operando en distintos modulos.


Aunque podamos operar en otro modulo, tenemos un pequeño problema. En operaciones como $a*x=1$, solemos despejar la x sola para poder calcular su valor. Es decir realmente hacemos $a^{-1}*a*x=1*a^{-1} \Rightarrow x=a^{-1}$.

Cuando estamos en otro modulo, esto no podemos aplicarlo con facilidad, por ello para calcular el inverso ($a^{-1}$), debemos calcular el $mcd(m,a)$ siendo $m$, $\mathbb{Z}_{m}$. Para el calculo de $a^{-1}$, hacemos uso del algoritmo extendido de Euclides.

Por ejemplo $201^{-1}$ en $\mathbb{Z}_{439}$.
> Deberíamos elaborar la tabla, sin embargo no me es posible en este formato, se irá explicando que calculos hemos hecho para resolverlo.
{.is-warning}

Lo primero que hacemos es dividir $439$ entre $201$, nos da $2$ y resto $37$. Es decir $439=201*2+37$.

Tras esto calculamos el dividendo entre el resto que nos ha dado, es decir $201$ entre $37$. $201=37*5+16$.

$37=16*2+5$.

$16=5*3+1$. Como el resto es 1, ya no podemos seguir operando.

Bien ahora debemos calcular pa parte extendida, en esta caso haremos lo siguiente:
$0-2*1=-2$ Lo que hemos hecho, es en la tabla extendida empezar con 0 y 1, tras esto cogemos el primer valor que tenemos (0) y le restamos el primer cociente por el segundo valor (1).

$1-5*(-2)=11$, Ahora nuestro primer valor es 1, que le vamos a restar el cociente del segundo valor (5) por el resultado anterior.

$-2-2*11=-24$.
$11-3*(-24)=83$, este es el último valor, por lo tanto diremos $201^{-1} \text{ mód }439=83$.

### En caso de Aritmética en $\mathbb{Z}_{p}$.

Cuando estamos ante una aritmetica de un primo, podemos llamarlo cuerpo/field/campo, todos estos nombres sirve. 


## Sistemas de congruencias
Una congruencia lineal: $ax+b \equiv cx+d \text{ mód }m;\text{ }a,b,c,d,m \in \mathbb{Z}, m \neq 0$. 

Por ejemplo, $5x + 7 \equiv 2x + 3 \text{ mod }11$. Para buscar una solución, debemos obviamente encontrar un valor a ambos lados del igual que de lo mismo. Por ejemplo 6.

$5*6+7 = 37, 2*6+3 = 15$. $37\equiv 15 \text{ mod }11$.

Aunque parezca que no, recordamos que $37$ en modulo $11$ es $4$, y que $15$ en modulo $11$ es $4$.

Vamos a estudiar las congruencias $ax \equiv b \text{ mód }m$, que son equivalentes a las vistas anteriormente.

### Reglas de resolución
Antes de ponernos a resolver un sistema de congruencia, debemos aprender una serie de propiedades.

1. Podemos reducir una congruencia si es superior al módulo dado en ambos lados. Ejemplo $23x \equiv 17 \text{ mód }9$ es equivalente a $5x \equiv 8 \text{ mod }9$.
2. Si existe un $mcd$ en toda la congruencia, podemos dividir por ese $mcd$ para reducir la congruencia.  Ejemplo $12x \equiv 8 \text{ mod }22$, es equivalente a $6x \equiv 4 \text{ mod }11$.
3. Si el minimo común multiplo de la congruencia, no tiene $mcd$ de 1, se puede reducir. $3x \equiv 5 \text{  mod }13$.

Por último la congruencia $ax \equiv b \text{ mod }m$ tiene solución si, y solo sí, $mcd(a,m)|b$.


#### Ejemplo
Bien, vamos a calcular $909x \equiv 516 \text{ mod }321$. Como podemos ver es una congruencia grande, entonces uno de los metodos que tenemos para resolverlo es con el algoritmo de euclides, pero primero usemos las reglas.
1. Como podemos observar, ambos valores son superiores a 321, por lo que podemos reducirlo y quedarnos con el resto. $909x \equiv 516 \text{ mod }321 \Rightarrow 267x \equiv 195 \text{ mod }321$.
2. Como podemos observar, tenemos  un minimo común multiplo en 3, por lo que podemos hacer $89\equiv 65\text{ mod }107$.
3. Aqui no hemos podido aplicar la 3º regla, por lo tanto nos quedamos con la anterior.


Bien tras esto, ahora empezaremos a hacer el algoritmo de euclides extendido de la siguiente manera:
$107/89= 1 + 18$, recordamos dividimos $m$, entre el que está al lado de $x$.
$89/18= 4 +17$.
$18/17=1 +1$.

Bien tras esto aplicamos la extendida:
$0-1*1=-1$.
$1-4*(-1)=5$.
$-1-1*5=-6$. Por lo tanto tenemos que $89^{-1} = -6$, en $\text{mod }107$, sin embargo como es negativo vamos a pasarlo al posivito, esto podemos hacer con una suma entre $107$ y $-6$, que da $101$.

Bien ahora tenemos $x \equiv 65 * 101 \text{ mod }101 \Rightarrow x\equiv 6565 \text{ mod }107$. Para terminar el ejercicio, solo debemos saber el módulo de $6565/107$, que nos dá 38.

Por lo tanto ponemos el resultado como $x \equiv 38 \text{ mod }107$, **y** $x=38+107*k : k\in \mathbb{Z}$.

### Sistemas de congruencias lineales
Un sistema de congruencia es lo sigueinte:
$a_{1}x \equiv b_{1} \text{ mod }m_{1}$.
$a_{2}x \equiv b_{2} \text{ mod }m_{2}$.
.......................................
$a_{l}x \equiv b_{l} \text{ mod }m_{l}$.

Nuestro objetivo es buscar números enteros que sean soluciones todas las congruencias impuestas, en este caso tenemos un sistema formado por dos congruencias.

Para resolverlo tenemos varias maneras, aunque se explicará una en más detalle.
#### Teorema chino del resto
Este teorema nos dice, que dado una congruencia con la anterior forma. Si para cada $i,j$ tales que $1\leq i < j \leq l$, se tiene que $mcd(m_{i},m_{j})=1$, entonces el sistema tiene solución. Y si el sistema tiene soluci´n entonces, debe tener la forma que solemos usar: $x=a+k*M : k\in \mathbb{Z}$, siendo $M=m_{1}*m_{2}\dots$.

Este teorema, realmente no nos ayuda a resolver propiamente dicho, ya que antes debemos resolver ambas congruencias para poder efectivamente aplicar el teorema, y la solución puede ser muy costosa de encontrar.
#### Generalización del teorema chino del resto
Dado un congruencia de la forma anterior, decimos que el sistema tendra solución si y solo si, para cada $i,j$ tales que $1\leq i < j \leq l$. Se cumple $mcd(m_{i},m_{j})=1 | (b_{i}-b{j})$.

Lo que nos dice es que vamos a encontrar solución siempre y cuando tenga minímo común divisor el 1 en cada modulo dado, y que sel resultado de $b_{i}-b{j}$, sea multiplo de 1. 

Sin embargo esto tampoco nos ayuda a llegar la solución, solo es una manera que nos indica que va a tener solución.

#### Resolución de sistemas de congruencias
Ahora vamos a usar un método que si nos va a facilitar el calcular el resultado.

El metodo consiste en resolver la primera congruencia, y la solución que tengamos se la añadiremos a la segunda. Tras esto si tenemos más congruencias, la solución de la anterior se la añadiremos a la proxima.

> Debemos recordar las propiedades de la congruencia, donde si tenemos una congruencia del tipo $ax\equiv b \text{ mod }m$, solo tendrá solución si $mcd(a,m)=n$ y $n|b$.
{.is-warning}

> Hay un caso especial, donde si encontramos una congruencia del tipo $0x\equiv 0 \text{ mod } n$, esto se puede sustituir como $0x\equiv 0 \text{ mod } 1$, y es una congruencia que es una verdad absoluta. Como decir $0x=0$.
{.is-info}

##### Ejemplo
Vamos a resolver un ejemplo puesto por el profesor:
$26x \equiv 22 \text{ mod }44$.
$35x \equiv 49 \text{ mod }78$.
$11x \equiv 7 \text{ mod }51$.

Lo primero que hacemos es resolver: $26x \equiv 22 \text{ mod }44$.

Aplicamos las propiedades que sabemos y reducimos la expresión a $13x \equiv 11 \text{ mod }22$, y comprobamos que $\text{mcd}(13,22)=1; 1|11$. Por lo que hay solución.

Bien pues hacemos los calculos pertinentes para obtener $13^{-1}$ ( Algoritmo extendido de Euclides). Y obtenemos $x \equiv 11 \text{ mod }22$, por lo que la solución es $x = 11 + 22 * k_{1}$.
> Recordamos nuestra x.
{.is-warning}

Ahora que tenemos este resultado lo sustituimos en el segundo formando:
$35x \equiv 49 \text{ mod }78 \Rightarrow 35*(11 + 22 * k_{1}) \equiv 49 \text{ mod }78 = 385+770k_{1}\equiv 49 \text{ mod }78 \Rightarrow 770k_{1}\equiv -336 \text{ mod }78$.

Limpiamos los resultados y obtenemos:
$68k{1}\equiv 54 \text{ mod }78$. Y comenzamos con las operaciones como antes, $mcd(68,78)=2; 2|54$, por lo tanto hay solución.

$34k_{1}\equiv 27 \text{ mod }39 \Rightarrow 34k^{-1}\text{ mod }39 = 31$.
$k_{1}\equiv 27*31 \text{ mod }39 \Rightarrow k_{1}\equiv 18 \text{ mod }39$.

Solución:
$k_{1}= 18 + 39 * k_{2}$.
Ahora sustituirmos el valor en la $x$ que teneiamos.

$x = 11 + 22 * k_{1} = 11+22(18+39*k_{2})=407+858*k_{2}$

Ahora volveremos a hacer lo mismo que antes.

$11x \equiv 7 \text{ mod }51 \Rightarrow 11*(407+858*k_{2}) \equiv 7 \text{ mod }51 \Rightarrow 4477+9438k_{2}\equiv 7 \text{ mod }51 \Rightarrow 9438k_{2}\equiv -4470 \text{ mod }51$.

Limpiamos todo un poco y obtenemos:
$3k_{2}\equiv 18 \text{ mod }51$. $mcd(3,51)=3; 3|18.$ Hay solución.

Ahora calcularemos $k_{2}\equiv 6 \text{ mod }17$, como podemos observar, se ha reducido tanto que se ha solucionado solo. Por lo que solo nos queda sustituir en la k que tenemos, ya que la solución es: $k_{2}=6 + 17*k$.
> Usamos k generica ya que es la última.
{.is-info}

Ahora sustituimos el valor en la x y obtenemos:
$x=407+858(6+17*k)=407+5148+14586*k=5555+14586*k$. Por lo tanto nuestra solución es:

$x=5555+14586*k:k\in \mathbb{Z}$.

## Ecuaciones diofanticas
Las ecuaciones diofanticas son del tipo: $ax+by=c$. Aunque este tipo de ecuaciones, las conocemos de bachillerato, si que es verdad que de primeras no podemos darle una solución unica al resultado.

Por ejemplo en la ecucación diofántica $2x+4y=20$, podemos dar como resultado $(0,5)$ o $(10,0)$, sin emabrgo con operaciones más grandes, esta tarea no resulta tan sencilla.


Antes de poder resolver estas ecuaciones, debemos saber si tenemos o no resultado, ya que estamos operando en $\mathbb{Z}$.

### ¿Tiene resultado?
Para que la ecuación diofantica $ax+by=c$, tenga resultado, se debe verificar que $\text{mcd}(a,b)|c$. Es decir que el maximo común divisor de "los valores que acompañan a las incognitas", sea divisor del valor aparte.

### Resolución

Para poder resolver ecuaciones diofánticas, lo que hacemos es expresarla como una congruencia, por ejemplo $29x+38y=94$, lo expresamos como $29x\equiv 94 \text{ mod }38$, y lo resolvemos.

La solución que nos dé ($x=36+38k:k\in \mathbb{Z}$), la vamos a sustituir en nuestra primera función.

Dandonos como resultado: $29(36+38k)+38y=94$, ojo esta operación **NO**, puede dar un radical, ya que estamos operando en $\mathbb{Z}$.

Como resultado, y nos saldrá $y=-25-29k$. Por lo tanto nuestras soluciones serían $x=36+38k$ y $y=-25-29k$, donde $k\in \mathbb{Z}$.


### ¿Y si tengo más de dos incognitas?
Es exactamente igual procedimiento solo que más largo, debemos primero realizar el $mcd(a,b,d)|c$, y si se cumple, es que el sistema de diofanticas tiene solución.

## Función de Euler
Antes de empezar, debemos recordar que $a$ es unidad de $\mathbb{Z}_{n}$, si $a*v=1$. Es decir, existe un valor $v$, que multiplicado por $a$ hace 1.

Por lo tanto $U(\mathbb{Z}_{n}) = \{a\in \mathbb{Z}_{n}:a\text{ es unidad}\}$.

Por ejemplo en el caso de:
- $\mathbb{Z}_{4}=\{0,1,2,3\}$, tenemos $U(\mathbb{Z}_{2}) = \{1,3\}$, ya que el $2$, nunca hace unidad, si seguimos sumando $2$ en modulo $4$, siempre obtendremos $2$.

Por lo tanto definimos la función de Euler ($\varphi$) como la cantidad de valores que son unitarios en un módulo. Retomando el ejemplo anterior tenemos que $\varphi(4)=2$.

Para los valores primos, debido a que los primos son solo divisibles entre le mismo y el 1, obtenemos que, si $p$ es primo, $\varphi(p)=p-1$. Claro este se cumple con los primos naturales, ¿pero y si es un primo en potencia?.

Aquí tenemos lo siguiente:
$\varphi(p^{a})=p^{a}-p^{a-1}$. Es decir para el caso de $n=3^3$, la cantidad de valores unidad será $\varphi(3^{3})=3^{3}-3^{2}$.

Claro pero y si ahora lo hacemos con $36$, que es $2^{2}*3^{2}$. Lo que haremos será de cada termino que hayamos obtenido en potencia, restarlo con el anterior y multiplicarlo. Es decir $\varphi(36)=(2^{2}-2^{2-1})*(3^{2}-3^{2-1}) = 2*3=6$.

Este metodo nos es util en baja escala, pero y si queremos calcular algo como $3^{10} mod 7$. En este caso podemos calcular una serie de potencias de 3 en modulo 7 hasta que veamos que cicle.
- $3^{0} = 1$.
- $3^{1} = 3$.
- $3^{2} = 2$.
- $3^{3} = 6$.
- $3^{4} = 4$.
- $3^{5} = 5$.
- $\dots$.

Si siguieramos, nos daríamos cuenta que estamos en un circulo vicioso entre esos terminos, estamo "ciclando" entre ellos. En ese caso, deberemos simplemente hacer un división de la potencia que tenemos, entre los valores que hemos obtenido al ciclar ($6$), y el resto será la posición que ocupa. Por ejemplo $3^123 mod 7$, pues $123/6=20$, con modulo 3, por lo tanto será $6$.

### Teorema de Fermat
El teorema de fermat nos dice que dados dos números enteros, donde uno de ellos es mayor que 2. Si el minimó común multiplo es 1, entocnes $a^{\varphi(n)}\equiv 1\text{ mod }n$.

> Por completar.
{.is-warning}

Si en el seguimos el teorema, cuando nos encontramos dos valores cuyo maximo común divisor sea distinto de 1, no podemos aplicar lo del bucle. Sin embargo es posible que este bucle se produzca más adelante, no indica que no exista.
