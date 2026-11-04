---
title: Gestión de Memoria
description: 
published: true
date: 2026-11-04T17:43:33.708Z
tags: 
editor: markdown
dateCreated: 2026-11-04T16:34:14.381Z
---

# Gestión de Memoria
## Generalidades sobre gestión de memoria
### Jerarquía de memoria
La jerarquía de memoria viene de:
- CPU
- Cache (L1,L2,L3)
- RAM
- Los buses que comunican entre E/S
- HD



### Conceptos sobre cachés
La memoria chacé es una copia que puede ser accedida más rádiamente que la orgiinal, su objetivo es ser la más eficiente. Existen los terminos de aciertos de caché y fallo de caché (Si el dato se encuentra o no en la caché).

Esto funciona gracias al **principio de localidad**, los programas siguen un patrón y todos los accesos de memorias están contenidas en el mismo "lado".
### Espacios de direcciones y mapa de memoria
Debemos diferenciar entre espacios de direcciones lógicos y físicos:
- Espacios de direcciones lógico: Direcciones lógicas generadas por un programa.
- Espacios de direcciones físicos: Conjutno de direcciones físicas correspondientes a la direcciones lógicas en un instante dado de ejecución.

Cuando representamos un proceso en una imagen, debemos tener en cuenta que se dividen en tres partes principales:
- Tipo: Puede ser texto, código, datos etc etc
- Tamaño: Lo que ocupa cada apartado anterior.
- Offset: Donde empieza cada valor del tipo.
### Objetivos de la gestión de memoria
Vamos a ver varios apartados durante este tema:
- La organización de la memoria, como se divide, con un proceso o varios
- La gestión dada un esqueleto de organización. Ya que podemos tener varias estrategias a seguir para un mayor rendimiento.
- Protección y compartición, donde se busca la seguridad entre usuarios del mismo grupo.

Entrando en más detalle de organización podemos tener:
- Organización contigua (No existe o modelo antiguo): La asignación se hace en un único bloque de memmoria.
- Organización no contigua: Usado habitualmente donde se busca "dividir" el programa. Podemos encontrar paginación, segmentación y segmentación paginada.

La paginación y segmentación sin MV(Memoria Virtual) nos proporciona, que lso programas segmentados no tienen porque estar ubicado de forma contigua, los trozos deben residir en momoria principal durante su ejecución.
### Intercambio (Swapping)
La idea es intercambiar procesos entre memoria principal y auxiliar. Donde el proceso pasará a estado "Suspendido_bloqueado" (dentro del disea más simple) y lo que ocupa espacio en memoria principal, el programa, pasara a disco. El almacenamiento auxiliar debe ser un disco rápido.

El planificador (swapper), se encarga de:
- Retirar procesos de la memoria principal.
- Incorporar procesos a la memoria principal.
- Gestionar y asignar espacios de intercambio.
## Memoria virtual. Organización
### Concepto de Memoria Virtual
La memoria virtual, surge debido a la necesidad de paginación o segmentación básica. El tamaño del programa, puede exceder la cantidad de memoria física disponibel para él, el número de proceso ejecutandose en MP (Grado de multiprogramación) aumenta, resuelve también un problema del crecimiento dinámico.

Aunque para llevarlo a cabo se necesita tanto memoria principal como memoria auxiliar.


La idea clave que usan dos niveles de jerarquía de memoria para almacenar el programa:
- Memoria Principal (MP): Residen las partes del programa necesarias en un moemnto dado: conjunto residente.
- Memoria auxiliar (MA): Reside el espacio de direcciones completo del programa. 

Para que se pueda implementar es necesario:
- Tener inforamción relacionada con que partes del programa se encuentra en MP y que partes se encuentra en MA.
- Política para la resolución de un acceso a memoria situado en una parte que en ese momento no reside en MP.
- Política de movimiento de partes del espacio de direcciones entre MP y MA.

### Unidad de gestión de memoria (MMU)
Consiste un dispositivo hardware que traduce direcciones virtuales a direcciones físicas. El esquema más simple, el valor del registro de base se suma a cada dirección generada por la ejecución del programa en CPU y este resultado se utiliza en el bus de memoria. 

Tiene unos registros denominado TLB (*Translation Look-aside Buffer*, traducido y de forma correcta es búfer de búsqueda de traducción previa), que mantienen la correspondencia página virtual, página física resueltas con anterioridad.

Alguna de las responsabilidades del MMU son:
- Si hay acierto de TLB, se realiza la traducción de dirección virtual a física.
- Si hay fallo de TLB, entocnes se usa el mapa de memoria para realizar la traducción.
### Memoria Virtual paginada
La organización dentro de direcciones físicas de un proceso jamas es contigua. La memora física son asignadas con tamaños fijos, denominados marcos de página o páginas fisicas que van desde 0.5 a 8 KB.

Las direcciones del espacio lógico de un proceso se interpreta a dos niveles, los bits más significativos determinan la página virtual en la que se encuentra la dirección, y los bits menos significativos se utilizan para completar la dirección física correspondiente.

La correspondencia entre "página virtual" y marco de página la almacena la entrada de la tabla de páginas denominado dirección base del marco de páginas.

Algunos terminos:
- Dirección virtual: Es la que es generada por la CPU y se interpreta como un par de Número de páginas (Entrada de tablas de págias y que está representada por los bits más significativos) y Offset (permite completar la dirección física correspondiente a la dirección virtual).
- Dirección física: Es la dirección real de memoria principal y se calcula basado en dirección base del marco de página y el offset.


### Tabla de páginas. Implementación
La tabla de página contiene una entrada por cada "página virtual" con el sigueinte campo:
- Dirección base de marco (Escrito en Hexadecimal)
- Validez/Presencia: Un bit para comprobar que esta
- Protección o modo de acceos (rwx)
- Bit de modificación o dirty bit.

La tabla de ubicación en disco, contiene una entrada por cada página virtual del proceso con los campos:
- Identificación del dispositivo lógico que soporta la memoria axuiliar.
- Identifiación del bloque que contiene su respaldo.


### Memoria Virtual segmentada
### Segmentación paginada
## Memoria virtual. Gestión
## Gestión de memoria en Linux