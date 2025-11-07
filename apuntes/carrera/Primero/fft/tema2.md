---
title: Elementos Reactivos
description: 
published: true
date: 2025-11-07T16:35:35.247Z
tags: 
editor: markdown
dateCreated: 2025-10-24T15:13:57.545Z
---

# Elementos Reactivos

## Condensadores
Los condensadores, son dos conductores (armaduras), muy proximas entre sí y separadas por un aislante perfecto. Se representa en circuitos como dos lineas rectas paralelas una a la otra.

Los condensadores, almacenan carga eléctrica, dependiendo de la d.d.p. V que se le aplique y la capacidad del condensador, y también almacenan energia.

La capacidad, se mide con Faradios (F), 1F=1Culombio/1Voltio, se suele utilizar el microfaradio, nano faradio o picofaradio.

### Tipos de condensadores
Los condensadores planos, son dos placas planas paralelas de superficie S, donde la distancia d de los planos es menor que en las placas, sin embargo estas no están con aislante solo hay vacío.

#### Variación de la carga almacenada $\Rightarrow$ Corriente.
Aunque la corriente no atraviesa un aislante como antes, debe ser finita y continua, ya que este condensador no puede almacenarla.

Los condensadores dependen de:
- Separación entra armaduras (d)
- Área de las armaduras (S)
- Material aislante si existen ($\in$)
- No depende de la carga Q y de la d.d.p.

#### Calculos
Los condensadores en serie se mide como: $\frac{1}{C_{eq}}=\frac{1}{C_{1}}+\frac{1}{C_{2}}... = \varSigma \frac{1}{C_{i}}$.

Por otro lado en paralelos, se mide con la suma de forma directa, no hace falta usar el inverso es decir: $C_{eq}=C_{1}+C_{2}+C_{3}\dots +C_{n}= \varSigma C_{i}$.

## Inductores
Los inductores, son un conducto continuo enrollado de manera que forma un conjunto de espiras paralelas y próximas entre sí. Cuando es travesado por una corriente eléctrica, se produce en su interior un campo magnético proporcional a la lo que la corriente genera.

El simbolo es de una serie de "ovalos verticales" conectados uno con los otros.

> IMPORTANTE DE EXAMEN.
{.is-info}

Debemos saber muy bien la ley de Faraday
### Ley de Faraday
La ley de faraday se escribede de la manera $\varepsilon = - \frac{d \phi_{m}}{dt}$. 

Para que la tensión en el inductor sea finita, es necesario que la corriente que lo atraviesa sea continua, es decir v=0.

### Calculos
Para inductores en serie, la formula es $L_{eq}=L_{1}+L_{2}$.

Para los inductores en paralelo, la foruma es: $\frac{1}{L_{eq}}= \frac{1}{L_{1}}+\frac{1}{L_{2}}$.

Al giual pasa con los sumatorios.

## Circuitos con condensadores e inductores
Cuando tenemos que las tensiones y corrientes eléctricas en sus elemetnos son cosntantes en el tiempo podemos ver que los dispositivos pasivos como condensadores y bobina sufren cambios.
- Condensador: Pasa a convertirse en un circuito abierto, ya que V=cte y I=0. 
- Bobina: Se sustituye por un corto circuito pero por el motivo contrario. I=cte, y V=0.

## Analisis de circuito en régimen transitorio.

Un régimen permanente, es aquel donde:
- Las excitaciones llevan mucho tiempo aplicadas.
- Las características de las fuentes no cambian con el tiempo.

Por lo tanto la respuesta del circuito, sigue las naturalezas regidas por las excitaciones, lo que nos permite un estudio continuo

Por otro lado el régimen transitorio:
- Las excitaciones se aplican o suprimen de forma brusca.
Lo que genera una respuesta distinta a la naturaleza de la excitación.

Lo que resulta en un estudio de análisis integro-diferencial.

## Osciloscopio - Carga y Descarga 
Cuando usemos un osciloscopio, podemos tener varios resultados, si el valor es distinto de 0, es que está en carga constante, sin embargo si es 0, es que está descargado. Graficamente, solo deberémos fijarnos de si la tabla está en subida o en bajada, ya que puede significar carga o descarga.
El elemento que mediremos será el condensador.


## Calculos
Cuando tengamos un sistema cerrado, nuestro condensador está en carga, y sin embargo si lo tenemos abierto, el condensador comienza a descargarse. 

Vamos a tener casos donde el circuito puede perder conectividad o no hay conexión con la fuente.
En el caso de que el circuito esté abierto, el condensador pasará a estar descargado constantemente ya que no hay voltaje por ese lado.

Por otro lado, si hay circuito cerrado, el condensador estará en carga o descarga, es decir, funcionando.

Hay distintas formulas (Todavía a poner), que usaremos según donde estemos:
- Justo antes del cambio de estado (Cerrado - Abierto)
- En cerrado.
- En abierto.


### Carga de condensador, circuito cerrado
Cuando cargamos un condensador tenemos un tiempo 0, o mayor que 0, ya que empezará a recibir energía a partir del primer segundo.

Cuando $t=0$, tenemos que el interruptor ha cambiado la posición, es decir se ha abierto el circuito, provocando que el $v_{c}=0$, el voltaje del condensador es 0.

Cuando el condensador empieza a cargarse, tenemos que $v_{c}=V$, es decir el voltaje va a tender al voltaje de la tensión, y llegará conforma más tendamos al infinito (Cuando llegue al momento).

### Tiempo de subida o bajada
Consiste en el tiempo que tarda un condensador hasta llegar a su máximo o desargarse, lo podemos hacer con la formula:
$V*(1-e^{-\frac{1}{ti}t})$, despejando sale: $\ln(V)=-\frac{1}{ti}t$.

### Fórmulas copiadas
Ecuación de nudo:
$i_{1}+\frac{v_{c}}{R}+i_{2}=0$.
$(C_{1}+C_{2})\frac{dv_{c}}{dt}+\frac{v_{c}}{R}=0$.
$pi x \frac{fx(t)}{dt}+x(t)=K$.
$Rx(C_{1}+C_{2})\frac{dv_{c}}{dt}+v_{c}=0$.
$x(t)=K+(x_{o}-K)e^{-1\frac{t}{pi}}$.

Cada cosa es:
$i_{1-2}$: Intensidad en un nudo
$v_{c}$: Tensión del condensador.
$R$: Resistencia.
$C_{1}$: Valor del condensador.
$dv_{c}$: Derivada de la tensión conforme al tiempo.
$ti$: Ni idea todavía.
$K$: Ni idea todavía.