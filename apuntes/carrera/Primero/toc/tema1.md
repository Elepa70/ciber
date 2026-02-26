---
title: Introducción
description: 
published: true
date: 2026-02-26T17:34:24.536Z
tags: 
editor: markdown
dateCreated: 2026-02-26T16:41:21.931Z
---

# Introducción

## Conceptos básicos
Empezamos el tema describiendo la palabra informática. Esta palabra viene del conjunto de conocimientos científicos y técnicas que habilitan el tratamiento automático de la información por medio de computadoras electrónicas.

Por otro lado computadora o ordenador, es aquella máquina que nos permite efectuar operaciones lógicas con datos de entradas y que resulte en una salida de datos, sin que haya sido intervenido por un humano.

Calculadora es aquella máquina capaz de efectuar operaciones aritméticas bajo el control directo del usuario.

Los datos son aquellos conjutno de símbolos utiliados para expresar o representar un valor numérico, objeto, idea...

Codificación transformación de unos elementos mediante un metodo para que resulten en otros.

Ahora vamos a hablar sobre algunas unidades de información:
- Bit (b) es aquella unidad más elemental y básica de la informática tomando valores de 0 o 1.
- Byte (B) conssite en un grupo de 8 bits.

A partir de esto debemos tener en cuenta que existe le kilo, mega, giga, tera...


### Programas e instrucciones
Una instrucción es aquel conjunto de símbolo que nos permite representar un orden de operación en una computadora. 

Por otro lado un programa, es auqel conjunto ordenado de instrucciones, donde ya se sabe que operaciones se quiere realizar.

### Instrucciones
Respecto a las instrucciones tenemos:
- Instrucciones de ransferencias de datos: Donde se transfiere datos de una unidad a otra.
- Instrucciones de tratamiento: Donde hay reglas aritmético-lógicas.
- Instrucciones de bifurcación y saltos: Donde se altera el orden secuencial y se hacen saltos o llamadas a otras funciones.
## Estructura funcional de un computador
Sobre la estructura funcioanl de una computadora o equipo, debemos tener en cuenta que hay unidades de:
- Entrada o $E$, que son aquellos dispositivos que nos habilitan introducir datos a una computadora, mediante la naturaleza eléctrica. Esto puede ser un teclado, un digitalizador, lecto de tarjetas...
- Salida o $S$, por lógica podemos deducir que estos son los dispotivos que nos permiten obtener resultados de programas o visualizarlos. Como pueden ser monitores, o impresoras.


Por otro lado la memoria, es aquella unidad de almacenamiento tanto 
## Representación de datos numéricos
Cuando introducimos datos mediante E/S, son codificados como caracteres de texto. Estas codificaciones suele ser inapropiada cuando se trata de representar números, ya que no hay un sistema de numeración matematico.

Cuando un usuario introduce un número en el ordenador, el equipo lo codifica como texto. Cuando ese dato lo usamos, el programador le asocia un tipo.

Para representar los datos númericos, tenemos que diferenciar entre tipo enteros o tipos reales.

### Dato de tipo entero, en binario
Podemos encontrar aquellos enteros sin signos (Valor absoluto) o con signo enteros con signo.

Cuando tenemos signo debemos diferenciar entre:
- Signo y magnitud: En este caso, guardamos el primer bit, y podemos diferenciar si es positivo o no según el valor (0 positivo o 1 si es negativo).
- Complemento a 1: EN este caso, cuando es positivo, el número se escribe normal (En binario ojo), sin embargo al ser negativo, lo que hacemos es escribir el complemento a 1 del valor absoluto del valor. Es decir si es negativo, cambiamos los 1 por los 0.
- Complemento a 2: Este ya es usado, sigue cumpliendo lo mismo, cuando es positivo no lo modificamos, pero cuando es negativo hacemos el "Complemento a 2" del valor absoluto del número. Esto consiste en hacer un complemento a 1, sin embargo le sumamos un 1.
- Sesgada: Escribimos el valor númerico pero susmandole el sesgo. El seco es un valor fijo con valor de $2^{n-1}$. Siendo n el valor de bits.

Se recomienda antes de hacer cualquier cosa que para convertir un valor de decimal a binario, pasarlo por hexadecimal.

Uno de los motivos por el que codificamos en complemento a 2, es por motivo economico a la hora de hacer hardware.

Cuando queremos codificar con un número mayor de bits a un número ya codificado, debemos tener en cuenta la extensión del signo, y es "alargar" el valor del bit simbolico (normalmente aquel que da el signo) a lo largo de la nueva longitud que vayamos a imponer.


### Dato de tipo real, es decir decimal, en binario
En este caso lo que se hace es indicar un valor fijo de cifras para poder representar la parte entera y otra para la parte fraccionaria (Representado como número fijo de parte entera $p$ y en el caso de fraccionaria $q$).

Para poder convertir un número decimal a binario debemos:
1. La parte entera se convierte en binario.
2. La parte fraccionaria la convertimos en binario.
3. Ahora lo que hacemos es buscar la cantidad de bits para cada lado, donde debe estar con: $2^{p-1}\leq E \leq 2^{p}$, donde $p$ es el número de bits, $E$ es el valor de la parte entera. La parte de fraccionaria será el resto.

Este metodo puede resultar varios problemas ya que no puede dar los suficientes bits para poder hacer los datos.

Normalmente lo que se hace es usar el método de coma o punto flotante $3,2131231*10^{2}$, es decir guardamos los valores más significativo y almacenamos el valor por el que vamos a multiplicar a 10.

En caso de computadoras, se usa la normalización IEEE 754, donde en vez de hacer $10^{n}$, usamos $2^{n}$.
Para almacenar los datos de esta manera, debemos tener en cuenta que esta el primer bit con el campo del signo (0 positivo, 1 negativos), luego tenemos el campo del exponente, que está sesgado para saber cuanto debemos elevar, y por último la mantisa.

#### Ejemplo
## Niveles conceptuales de descripción de un computador
## Sistemas analógicos y digitales