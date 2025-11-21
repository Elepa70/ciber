---
title: Corriente alterna
description: 
published: true
date: 2025-11-21T15:34:14.931Z
tags: 
editor: markdown
dateCreated: 2025-11-14T14:50:15.753Z
---

# Corriente alterna
La corriente alterna está relacionada directamente con la corriente que solemos usar en casa.

## Sismtea de energléctrica
El sistema de energía electrica tiene cuatro partes:
- Generación: Producción de energía electrica mediante materias primas.
- Trasnporte: La transmisión de la energía electrica, que va muy alta entre 220kV y 400kV.
- Distribución: La trnasmisicón de energía eléctrica desde las redes hasta zona de consumo.
- Comercialización: Venta de energía eléctrica para los consumidores finales

El trnasporte se hace en corriente altenra, ya que trane una gran facilidad de generación, no varía tanto las ondas y es facil de adptar.

## Diferencia con respecto a la continua

En la corriente alterna, debemos tener en cuenta una serie de cosas. Para empezar la formula de OHM pasa a ser:
$\frac{V(t)}{I(t)}=Z$.

## Clasificacide las ondas
Como estamos en alterna, a diferencia de continua podemos ver una serie de ondas, estas ondas las podemos clasificar segun:
- Simetria: Par o Impar.
- Tipo: Continua o Alterna.
- Regularidad.

Dependiendo de cuales elementos y la cantidad de los mismos tengamos en el circuito, esto alterara la manera en la que las ondas se muestra, pudiendo retrasarla, adelantarlas etc etc

## Parametros asociados a la onda
Normalmente nosotros vamos a investigar una serie alterna normal, donde nos solemos fijar en:
- Los valores picos, donde podemos calcula $A(t)=A_{max}*sen t$.
- El inicio de la señal. Si no comienza en el eje debemos cambiar la formula anterior a $A(t)=A_{max}*sen (wt+K)$. Donde $K$ es la diferencia de distancia entre el pico que debería tomar y el que toma.

- Ciclo: Es de la forma de onda comprendida en un período.
- Frecuencia (f): Es el número de ciclos por unidad de tiempo.

- Valor medio de la señal $A_{m}$, vale $\frac{1}{T}$.
- Valor eficaz: $A_{ef}=\frac{A_{max}}{\sqrt{2}}$.
- $F_{f}=\frac{A_{ef}}{A_{m}}$.

## Analisis en el tiempo
Dependiendo del tipo de circuito debemos usar una u otra formula
### Resitencia
$V(t)=i_{R}(t)R$.
$i_{R}(t)=\frac{V(t)}{R}$.
### Bobina
$V(t)=L\frac{di_{L}(t)}{dt}$.
$i_{L}(t)=\frac{1}{L}\text{ integral}V(t)dt$.
### Condensador
$V(t)= \frac{1}{C}\text{ integral}i_{C}(t)dt$.
$i_{C}(t)=C\frac{dV(t)}{dt}$.


Una vez tengamos estas ecuaciones para poder calcular $v(t)=V_{o}*sen(wt)$, debemos despejar donde ponga V, para poder calcular i_{R}.

Con $v(t)=V_{o}*sen (wt)$, tenemos tres funciones distintas
- $i_{R}(t)=\frac{V_{o}}{R}sen(wt)$.
- $i_{L}(t)=\frac{V_{o}}{wL}sen(wt-90º)$.
- $i_{c}(t)=V_{o}*cwsen(wt+90º)$.

Aunque esto sea engorroso, nosotros usaremos la forma fasorial, que nos quedaría de las anteriores formulas en orden:

## Dominio fasorial
Ya no dependemos del tiempo, ahora dependemos de las fases.
- $I_{R}=\frac{V_{o}}{R}\text{ "Caja"}0º$.
- $I_{L}=\frac{V_{o}}{wL}\text{ "Caja"}-90º$.
- $I_{C}=V_{o}w\text{ "Caja"}90º$.

Lo que llamamos caja, es en verdad el fasor, un conjunto de operaciones que podemos realizar en la calculadora.


Cuando tenemos una resistencia y bobina, vamos a estar en una fase positiva, si fuera un condensador estariamos negativo.
Sin embargo, en caso de tener los tres componentes, dependerá de los valores de los 3 elementos el ser positivo o negativo.
