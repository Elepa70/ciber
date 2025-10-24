---
title: Corriente continua
description: 
published: true
date: 2025-10-24T13:25:28.770Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:32:25.200Z
---

# Corriente continua
En los circuitos podemos llegar a encontrar dos clases de componentes:
- Estáticos: O circuitos resistivos, son aquellos donde hay uhna relación entre seáles de excitación y respuesta.
- Dinámicos: O circuitos con bobinas y condensadores donde hay integrales y direnciales en las ecuaciones.


La **linealidad** en un circuito, solo se puede contemplar si el circuito tiene las propiedades de homogeneidad y superposición.
- Homogeneidad: Si la señal de excitación (Salida), se multiplica por una constante, la salida también es multiplicada por esa constante.
- Superposición: Las señales de excitación entrantes, es igual a las que salen. De igual pasa con el sumatorio de las señales individuales entrantes y salientes.

La excitación, o la señal que se le aplica a un circuito, puede ser:
- Continua: Circuito donde la señal solo toma un unico signo, o positivo o negativo.
- Alterna: Donde la señal toma tanto valores positivos como negativos, inclusive el 0.

El tipo de respuesta es el comportamiento de un circuito, este puede ser transitoria (A habido algún cambio dentro del circuito y está subiendo o bajando en tensión), o estacionaria/permanente (No hay cambios visibles).

## Variables eléctricas básicas
### La Intensidad
La intensidad, consiste en la cantidad de carga eléctirca que atraviesa una sección en un tiempo determinado.

Es medido con un amperímetro, este instrumento posee una resistencia muy baja, para evitar modificar lo minimo posible el resultado. 

Estos valores pueden ser positivos o negativos, sin embargo esto no influye en el resultado, influye en que estamos midiendo de forma adversa a como debería ser.
### Voltio
Consiste ne la diferencia de potencia entre dos puntos.

Se mide con un voltímetro.

### Potencia
Es la cantidad de energía intercambiada, según la **ecuación del balance de potencias**, la suma algebraica de las potencias en un circuito eléctrico debe ser 0. $\sum P_{generadas}=\sum P_{consumidas}$.


## Ley de kirchhoff
### En corrientes
Según la ley de kirchhoff, el sumatorio de la intensidades entrantes y de la salientes siempre debe ser 0.
$\sum i_{entrantes}=\sum i_{salientes}$

O la diferencia entre las entrantes y salientes debe ser 0.
$\sum i_{entrantes}-\sum i_{salientes}=0$

### En corrientes
Según la ley de kirchhoff, el sumatorio de todos las tensiones, debe ser 0.
$\sum v_{m}=0$
$v_{1}+v_{2}-v_{3}+v_{4}=0$


Esto lo podemos observar a como tenemos el sentido del circuito y las resistencias.

## Clasificación de elementos
Los elementos dentro de un circuito podemos clasificarlos, según su comportamineto energético.
- Elementos activos: Son aquellos que aportan un suministro eléctrico o reducen el aportado. Podemos encontrar generadores y semiconductores.
- Elementos pasivos: A diferencia de los activos, estos se dedican a fluctuar con la energia, pudiendo disiparla (Resitencia), almacenar la energia (Bobina o Condensador).

## Las fuentes
> Esto puede llegar a ser confuso.
{.is-warning}

### Fuentes ideales
Las fuentes ideales, se presentan como esas fuentes donde es independiente a lo que ocurra, es decir, le tenemos un control completo.
- Fuente Independiente Ideal de Tensión (FIIV): Estas fuentes son como las del laboratorio de prácticas, son las que alteramos o modificamos según lo que deseemos para añadirle más o menos tensión, debemos calcular la intensidad con la que fluctua el circuito.

- Fuente Independiente Ideal de Intensidad (FIII): Estas sin embargo, son aquellas donde manejamos la intensidad de la corriente, y debemos calcular la tensión. Es el contrario de la FIIT


### Fuentes reales
Estas fuentes a diferencia de las ideales, son las que suelen usarse y las que suelen verse en el mundo real.
- Fuente Independiente Real de Tensión (FIRV): Es similar a FIIV, sin embargo con una resistencia en serie, donde disminuira el potencial a medida que aumenta la intensidad que suministra.

- Fuente Independiente Real de Intensidad (FIRI): Similar a FII, con una intensidad en paralelo, con la misma intención que FIRV.

### Fuentes dependientes
Las fuentes dependientes son auqellas fuetnes de tensión/intensidad (ideales), donde las magnitudes depende de otra tensión o intensidad existente.

## Resistencia
La resistencia la definimos como un elemento pasivo que representa la oposición que ofrece un cuerpo al paso de la corriente eléctrica, disipando la energía en calor. La podemos ver con la formula:
$R = p \frac{l}{A}$, siendo R Resistencia, p potencial de resistencia, l longitud, A diametro. Sin embargo usualmente usamos la ley de Ohm $Resistencia = \frac{Voltaje}{Intensidad}$.

> Es recomendable mirar la guía de colores ya que puede facilitar mucho a la hora de hacer actividades prácticas.
{.is-info}


Debido a que la formula de la potencia es: $p=v*i$ y con la ley de ohm $v=i*R$, podemos juntar las formulas para $p=\frac{v^{2}}{R}$ o $p=i^{2}*R$.

Las potencias comunes son de 0.25W, 0.5W, 1W. Si la potencia es superior, corre el riesgo de que a la hora de disipar el calor, se queme la resistencia.
## Condensador
El condensador es una constante que cumple la relación entre la carga acumulada y la diferencia de potencial. Se denomina capacidad (C).
$C=\frac{q}{v}$.


## Circuitos equivalente
Un circuito equivalente es aquel circuito ficticio, que se comporta eléctricamente igual que el original.

## Conversiones estrella, triangulo, circuito
Estas conversiones nos sirve para dar otro punto de vista a los circuitos que se nos plantea. Se usa normalmente con tres elementos, primero debemos designar tres puntos claves, uno donde convergen ambos puntos y los demás.

### Configuración estrella
Una vez tengamos claro cuales son nuestros puntos, vamos a realizar una diagonal una diagonal desde nuestros puntos inferiores (ejemplo B y C), que contengan los elementos que hemos seleccionado (Resistencias para que sea mas facil). Ambos deben coincidir en un punto donde trazaremos una línea vertical con el otro elemento que nos falta (A).

### Configuración triangulo

En este caso, lo que haremos será trazar un triangulo equilatero, donde cada vertice sea nuestros puntos, entre media colocaremos las resistencias. Este es más simple, sin embargo las formulas pueden llegar a confudir.

### Transormación estrella <-> triangulo
Ahora vamos a ver una serie de formulas para poder realizar de forma correcta las transformaciones.

#### De Triangulo a Estrella
$R_{A}=\frac{R_{2}*R_{3}}{R_{1}+R_{2}+R_{3}}$.

$R_{B}=\frac{R_{1}*R_{3}}{R_{1}+R_{2}+R_{3}}$.

$R_{C}=\frac{R_{1}*R_{2}}{R_{1}+R_{2}+R_{3}}$.

Por lo tanto:
$R_{Estrella}=\frac{1}{3}R_{Triangulo}$.
#### De Estrella a Triangulo
$R_{1}=\frac{R_{A}*R_{B}+R_{A}*R_{C}+R_{B}*R_{C}}{R_{A}}$.

$R_{2}=\frac{R_{A}*R_{B}+R_{A}*R_{C}+R_{B}*R_{C}}{R_{B}}$.

$R_{3}=\frac{R_{A}*R_{B}+R_{A}*R_{C}+R_{B}*R_{C}}{R_{C}}$.

Por lo tanto:
$R_{Triangulo}=3R_{Estrella}$.
## Elementos topológicos
En un circutio, podemos encontrar distintos elementos que es importante saber:
- Rama: Las ramas es un segmento de un circuito, por el que circula la misma intensidad de corriente.
- Nudo: Conexión multiple de ramas. Si es de 2 es simple, si tiene 3 o más se le llama Nudo principal.
- Lazo: Conjunto de ramas que definen una trayectoria cerrada. Aquí podemos aplicar la 2º Ley de Kirchhoff
- Malla: Consiste en a quel lazo que **no**, contiene otro lazo. Es decir, que forma un circuito plano unico.

- Tensión del Nudo n: Consiste en la diferencia de potencia entre el nudo n y otro elegido como referencia (Nudo de tierra habitualmente, un icono de un triangulo hacia abajo).

La tensión en un nudo, lo que vamos a comprobar es comprobar los elementos entre los nudos indicados, y el valor será la diferencia que procede entre ambas tensiones.
## Impedancia y admitancia
La Impedancia (Z), con la siguiente formula: $Z=\frac{v}{i}$, es una medida de oposición que presenta un circuito a una corriente cuando se aplica una tensión.

Sin embargo la Admitancia (Y), es lo contrario, $Y=\frac{i}{v}$.

Podemos conectar ambas formulas con: $Z=\frac{1}{Y}$.

## Planteamiento general de resolución de ejercicios
Cuando nos enfrentamos a los ejercicios, podemos usar las leyes de Kirchhoff, y las ecuaciones que obtenemos de ellos. No spermite realizar un método de análisis. 

Con estos métodos de análisis, podemos resolver con ecuaciones de corriente de mallas (Lo que solemos hacer), o ecucaciones de tensiones de nudos.  Con el método directo, pasamos con las ecucaciones de corriente de mallas en matrices, para poder aplicar la regla de cramer.

Cuando empecemos a analizar las mallas de los casos genericos, lo que vamos a hacer es comprobar el sentido de la corriente conforme a los elemetnos que encontramos. El sentido de la corriente lo imponemos nosotros, pero debe ser el mismo, y tras esto.



### Regla de Cramer
La regla de Cramer, nos permite la resolución de cualquier sistema de n ecuaciones con n incógnitas. Es recomendable acudir a fuentes externas para poder revisar como fucnionan


### Casos excepcionales
Hay veces que debido a que tenemos funtes de tensión y una seríe de nodos, si le añadimos una fuente de corriente, nos dificulta muchisimo mas el trabajo. Es por ello que buscamos alterar este último apartado con uno que rentabilice más.



## Teorema de linealidad
El teorema de linealidad, nos dice, que si multiplicamos el valor de todas las fuentes independientes, por una constante. La respuesta del circuito estará multiplicada por esa constante también.

Dentro de este teorema, podemos ver:
- Cortociuitos, es decir hacer cero su tensión (En una fuente de tensión)
- Circuito abierto, es decir hacer su intensidad cero (En una fuente de intensidad).

Esto se fundamenta con el principio de superposición, ya que intentamos anular una de las entradsa de corriente o intensidad en el circuito, para calcular la otra, y después haremos lo mismo con lauq enos sobre. 

La suma de ambas intensidades o tensiónes nos dara el resultado que buscamos.

## Resistencia equivalente
La resistencia equivalente, consiste en una conexión entra formada unicamente por resistencias, que la obtenemos normalmente por asociación, conversión y simplificación de elementos pasivos. Usarem	os normalemente el principio de superposición.

### Equivalencia Thévenin
Consiste en un teorema, realizada, por un donde en una circuito cerrado, realizamos una simplificación de las resistencias, pero teneiendo en cuenta la fuente de energía (Voltaje o Corriente), que tengamos. En caso de tener una que es independiente, no podemos modificarla.

Cuando tenemos por ejemplo un circuito cerrado formadocon 3 resistencias y una fuente de tensión independiente, lo que hacemos es cortocircuitar las fuente, y la formula que haremos será:
- Calcular los valores en paralelo y en serie como lo solemos ahcer de nromal
- El $V_{TH}$, lo calculamos con la intensidad de la malla, y sustituyendo la intensidad de la malla, con la formula e Ohm.

### Equivalente Norton
En este caso, o que hacemos es lo mismo pero con intensidades, es decir. $R_{TH}=R_{N}$, solo que Norton solo se usa en intensidad de cortocircuito y la Thévenin, con circuito abiertos.
