---
title: Sistemas en el nivel de transferencia entre registros (RT)
description: 
published: true
date: 2026-05-28T16:42:54.311Z
tags: 
editor: markdown
dateCreated: 2026-05-28T15:34:43.246Z
---

# Sistemas en el nivel de transferencia entre registros (RT)
En este tema vamos a ver conceptos básicos de organización, descripción, análisis y síntesis de sistemas digitales.
## Introducción
El Sistema RT ejecuta ordenes externas y/o códigos de operación. Cada instrucción representa una "tarea" a realizar por el sistema, y cada "tarea" se consigue secuenciando durante un numero de pulsos de reloj.

Una microoperación es una operación elemental entre registros que se realiza (normalmente) en un ciclo de reloj.

## Unidad de procesamiento o camino de datos. Ejemplos de operaciones
### Camino de datos
La Unidad del sistema donde se ejecutan las operaciones $RT$ o microoperaciones:
Están compuesto por:
- Componentes de almacenamiento
- Circuitos de enrutamiento de datos
- Unidades funcionales de procesamiento de datos


### Módulos de enrutamiento (Enlaces y Buses)
Modos de enlazar elementos de forma que sean posible transferencias de información entre cualesquiera de ellos.

Componentes de control de los buses:
- Demultiplexores/decodificadores
- Selectores de datos (multiplexores)
- Adaptadores tri-estado

Existen varios tipos de buses como:
#### Buses dedicados
Es una única fuente y destino para cada bus.
Tiene las desventajas de que:
- Requiere un gran número de líneas de interconexión.
- Difícil ampliación
Ventajas:
- Posibilidad de transferencias simultaneas, implicando mayor velocidad.

#### Bus compartido
Consiste en un bus enlazando diferentes fuentes y destinos.
Tiene las ventajas de que:
- No son posible transferencias simultaneas donde se tenga más de una fuente.
- Se requiere lógica de control del bus más compleja.
Ventajas:
- Simplifica la interconexión.
- Fácilmente ampliable.
En este tipo de bus, podemos encontrar los buffer triestados, donde se tiene una entrada de acceso donde si:
- Marca 0: no avanza la información.
- Marca 1: Avanza la información.


Este tipo de bus, puede ser similar a un multiplexor, ya que haría la misma función que el buffer triestado. Y podríamos conectarlo al bus compartido.

La diferencia es que en las señales de control del multiplexor (Lo tipico de C1 y C2), tenemos las ReA ReB ReC..., siendo similar pero no identico.

### Microoperaciones y palabras de control
Ahora tenemos el concepto de "conjunto de microoperaciones de n camino de datos".
Estas palabars de control están compuestas por:
- Seleccion de entrada, para saber de donde vienen los datos.
- El control de la ALU.
- Si va a escribir en  R.
- Si vamos a leer en R.

## Unidad de Control
### Misión de la Unidad de Control: Motivación
La unidad de control es la encargada de secuenciar microoperaciones del camino de datos de acuerdo con un algorítmo del sistema RT a realizar.