---
title: Corriente continua
description: 
published: true
date: 2025-10-03T19:16:32.229Z
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
Es la cantidad de energía intercambiada, según la **ecuación del balance de potencias**, la suma algebraica de las potencias en un circuito eléctrico debe ser 0. $\sum P_{generadas}=\sum P_{consumidas}$


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

## Condensador
El condensador es una constante que cumple la relación entre la carga acumulada y la diferencia de potencial. Se denomina capacidad (C).
$C=\frac{q}{v}$.

