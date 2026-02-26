---
title: Introducción
description: 
published: true
date: 2026-02-26T17:03:04.382Z
tags: 
editor: markdown
dateCreated: 2026-02-26T16:41:21.931Z
---

# Introducción

## Conceptos básicos
Empezamos el tema describiendo la palabra informática. Esta palabra viene del conjunto de conocimientos científicos y técnicas que habilitan el tratamiento automático de la información por medio de computadoras electrónicas.

Por otro lado computadora o ordenador, es aquella máquina que nos permite efectuar operaciones lógicas con datos de entradas y que resulte en una salida de datos, sin que haya sido intervenido por un humano.

Calculadora es aquella máquina capaz de efectuar operaciones aritméticas bajo el control directo del usuario.

Los datos son aquellos conjutno de símbolos utiliados para expresar o representar 
## Estructura funcional de un computador
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


## Niveles conceptuales de descripción de un computador
## Sistemas analógicos y digitales