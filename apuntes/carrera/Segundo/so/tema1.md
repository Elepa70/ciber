---
title: Estructuras de sistemas operativos
description: 
published: true
date: 2026-09-23T17:17:19.557Z
tags: 
editor: markdown
dateCreated: 2026-09-16T15:49:04.526Z
---

# Estructuras de sistemas operativos
> Revisar estructura
{.is-warning}

## Recordatorio de TOC y FS
En este primer apartado, nos dedicamos a recordar lo que hemos dado el año pasado.

Durante esta asignatura vamos a también usar la abstracción como hemos visto en PDOO. 
Esto es importante ya que en SO y en HW, hay bastante poca abstracción y vamos a ir viendo porque se da esto.

### E/S

Los módulos de Entrada y Salida, se comunican el controlador de dispositivos (Device controller), que este a su vez se comunica con el dispositivo (device).

Las principales tecnicas de E/S son:
- Se manda a un comando de lectura a entrada salida -> Se lee el estado del modulo de entrada salida (Donde el primer campo del módulo de Entrada Salida va a estar en modo Ready o Busy, y también leerá si está OK o ERROR) -> Se comprueba el estatus (Ready, Not Ready, Error Condition) -> Se lee la palabra del módulo de E/S (Se pasa la información del I/O a la CPU) -> Escribir la palabra en memoria (De la CPU a Memoria).
> En el estado de estatus, se debe verificar que la operación sea READ y no WRITE, ya que de otro modo es un error de diseño.
{.is-danger}

- Es similar al anterior pero se puede bloquear un error o una interrupción via E/S, que vive del RSI (Explicado adelante), y una vez cometido el error avanza.
El código del kernel que se encarga del tratamiento  o la rutina del servicio de interrupción se llama RSI, que pasa de un OK a ERROR.

- Los DMA (Transferencia de Memoria directa) son aquellos donde se hace un input a la memoria de forma directa y no para hasta que no haya completado, independientemente los procesos.

### CPU
Por otro lado la CPU usa varios registros, en los que tenemos PC (programa counter, que usa las siglas del siguiente programa) y IR (Es aquel que esta siendo ejecutado en ese momento). Los registros de memorias de la CPU, tenemos:
- MAR: Contiene la dirección de la siguiente R/W. 
- MBR: Contiene los datos que van a escribirse en memoria.
- I/O AR: Son los registro de dirección de E/S.
- I/O BR: Son los registros de buffer de E/S
> Importante los dos primeros.
{.is-info}

Dentro de los registros de la CPU tenemos:
#### Registros de CPU de propósito general
Se acceden por programas y clasificarlo en registros de datos. Los más importantes son registros índice, puntero a segmento y puntero a la pila (Este último tiene el BP que es el principio de la PIla y el SP que es el fin de la pila).
#### Otros registros de CPU
Tenemos:
- Programa Counter (PC): Dirección de la siguiente ejecución.
- Instruction Register (IR): Última instrucción que se fué a usar.
- Program Status Word (PSW): Información de códigos de condición. Tenemos el modo de ejecución OO (Kernel, unicamente por el SO), 01 (Modo User). También tenemos los entry points que existe las: Interrupciones (Pueden ser internas al micro o excepción, excepciones y Llamadas al sistema (Provocadas por el SO o por nosotros).

> Las excepciones las provocan las instrucciones en uso, donde puede llegar a "petar" el programa y aque no se puede recuperar, o si es viable recuperarla y continuar. Sin embargo las excepciones vienen por el controlador al del dispositivo. Por otro lado tenemos los TRAP o llamadas al sistema que no tiene nada que ver.
{.is-warning}

> El concepto de máquina desnuda es aquel que se define como: Todo repertorio por instrucción microprocesador (NO SIRVE ENSAMBLADOR), puede acceder a toda la memoria y solo permite E/S a bajo nivel.




### Memoria principal
Por último tenemos la memoria RAM o principal 

Es una tabla o array lineal compuesto por números de elementos con distintos tamaños. Las palabras son direccionables con números naturales desde el 0, siendo este número la dirección de memoria, y los espacio de dirección son un conjunto de número que representa las direcciones de una memoria.

Posee las operaciones de Lectura (R) y Escritura (W). Las direcciones se codifican en base 2, si utilizamos n bits para codificar las direcciones, el espacio de direcciones tiene una cardinalidad de 2^n direcciones.

Tenemos varios modelos de memoria:
- Flat memory model: Espacio lineal desde 0 hasta el 2^32-1. Con este método te permitiría acceder a una sección de memoria con el modo usuario. 
- Segmented memory model: Son aquellos programas que ven el espacio como espacios independientes llamados segmentos. 	
- Real-address mode memory model: No es muy usado y no se va a explicar en profundidad hasta el tema 3.

La memoria RAM también interactua con el E/S:
- Control y temporización: Controlar la transferencia del dato al procesador.
- Comunicarse con el procesador y con el dispositivo.
- Almacenamiento temporal de datos o buffers: 
- Detección de errores:

Abstracción hasta tema 5
Dentro del módulo de E/S tenemos

Todos estos modulos estan conectadas entre ellas mediante buses donde destacamos:
- Control Bus
- Address bus
- Data bus




Si recordamos hablamos de las Entry Points, que son Interrupción, excepción y llamadas. Ahora vamos a hablar sobre el tratamiento de interrupciones:

### Interrupciones
El tratamiento de excepciones parte desde la parte Hardware de la siguiente manera:
- El dispositivo controlador detecta un error y lo interrumpe.
- El procesador finaliza la ejecución del proceso actual..
- El proceso envia una señal informando de la interrupción.
- El procesador mueve el PSW en modo 0 (modo protegido) y el PC al stack.
- El proceador busca y carga el nuevo RSI(Rutina de Servicio de Interrupción), para identificar cual es el nuevo dispositivo que ha dado error. Este mecanismo se llama: Mecanismo de interrupciones vectorizadas (Consiste en un array, reservado en una zona de RAM intocable del Sistema Operativo, que contiene la dirección de la 1º Instrucción del RSI i, y también la dirección de la 1º Instrucción de la rutina servicio excepción, siendo divididas por el 80h siendo el gestor de general al sistema, cualquiera de estas pueden ser cargadas en memoria).
> Con esto en cuenta, lo que se hace es que se añade en memoeria (PC), el VI[80h], que es el gestor general de llamadas al sistema.
{.is-info}

Ahora tenemos también la parte en Software:
- Se guarda o graba el resto del estado del procesador. Donde se salva todos los registros del RSI.
- El proceso se interrupte.
- Se reestablece el proceso de estado de la información.
- Por último lo que se hace el restaurar el antiguo PSW y el PC. Esto se hace con *i ret* (interrupt return). Donde lo que hace es cargar el marco de la pila y cargarlo en el registro (El PC y el PSW).

Existen también las TRAP que es otra interrupción que forzamos nosotros para poder entrar en el modo protegido y hacer uso de los servicios y llamadas del servicio.


A su vez tenemos las excepciones, donde pueden ser recuperables o no recuperables. 




En las interrupción software o llamadas al sistema, cambia un poco con respecto al anterior. El hardware sigue apliando el PSW y el PC, activa modo kernel (0 protegido) y cagar el PC con el contenido del vector dentro del gestor general. 


Dentro de las interrupciones debemos saber que existe una prioridad de interrupciones donde cuanto menor sea el número mayor es la urgencia que tiene. En caso de intentar solucionar una interrupción de un valor mayor al que acaba de entrar, este se para y deja entrar al mas urgente. Esto se almacena en la pila de control de sistema, y se va a seguir almacenando y extrañendo conforme vaya resolviendo.
## Componentes de un SO

### Procesos

Lo primero que tenemos que definir una serie de cositas
- Procesos: Es aquello que necesita un S.O. para poder monitorizar el programa y controlar la su ejecución. La supervisión del los procesos viene encargado del PCB. 

Un proceso al crearse lo que hace es:
- Crea o genera un PCB, donde se inicializa sus campos.
- Se carga el programa en RAM, para ir al gestor de memoria. 
- Nos establecemos en Listo, donde se generaria un pid_t PID (En unix),se le añade un contexto de registro del procesador (PC, PSW, SP, BR indica la base en la pila y LR indica el fin en la pila), añadimos el estado (que debe ser Nuevo, Finalizado, Listo, Ejecudandose o Bloqueado) y por último añadimos la memoria.
- 

> Existen unas consideraciones con Multiprogramación, Compartir tiempo, Calendariod e CPU o memoria virtual por ejemplo.
{.is-info}

La multiprogramación nos habilita que varios programas se ejecuten a la vez, lo hacemos mediante un context_switch donde cambiamos el estado de ejecutado a bloqueado. Sin embargo esto puede generar problemas ya que la unica de manera de esperar otra E/S es entrar en modo bloqueado y no volver a Listo automaticamente.

Es por eso que el *Tiemsharing*, soluciona este problema, ya que te permite volver al estado listo, siempre y cuando tu tiempo se haya acabado (Timeout). Esto genera un dato nuevo en nuestra PCB, el contador. 

> CPU scheduling y swapping se darán en el tema 2 y la memoria virtual en el tema 3.
{.is-success}


La funcionalidad de los procesos, tenemos la creación del PCB con todo lo explicado anteriormente y la eliminación del mismo a la hora de finalizarse, también el bloqueo (sleep) y desbloqueo (wakeup) que se verá más adelante, y por último la comunicación de procesos también se verá mas adelante.

### En la memoria
La memoria nos sirve para:
- Protección de la memoria del kernel y las regiones de programas.
- Compartición por parte de regiones ocupadas por programas para comunicarse entre ellos.
- Se encarga también de la jerarquía de la memoria con la asignación y liberación del mismo, mediante la memoria asignada y libre.
- Algortimos para memoria virtual (Decidir cuanta memoria requiere cada proceso) y para swapping (para liberar toda la memoria asociadas).

### Archivos y Directorios
Un archivo consiste en una colección de contenidos de información usualmente identificada.
Alguna de sus funcionalidades:
- Tiene los archivos de procesamiento (Abrir, cerrar, escribir, leer...) 
- Creacion, eliminacion...

Los directorios se encargan de la asignación y liberación de los archivos y directorios, mediante los metadatos del Sistema de Archvios

### Dispositivos E/S
Donde se busca el controlar los funcionamientos de los dispositivos de E/S, la protección de su utilización por parte de las aplicaciones, tener una interfaz independiente y por último los Device Drives o el manejador de dispositivo.

### SO
Un sistema operativo en su gestión de recursos debe garantizar:
- Equitatividad: Garantizar el acceso a los recursos para todo proceso.
- Respuesta diferencial: El SO debe identificar y asignar a cada recursos los recursos que requiere. Esto puede chocar junto a Equitatividad, ya que los procesos en IORBs, peude provocar que algunos procesos se mueran de inanicion (no obtener ningun recurso)
- Eficiencia: Se diferencia entre usuario y para sistema, donde se busca maximizar la productividad según para que este diseñado.

Dentro de un SO tenemos una serie de componentes:
- Gestor de procesos
- Gestor de memoria
- Gestor de archivos
- Gestor de E/S y gestor de comunicación (que son similares pero donde se diferencia en que, las de comunicación tengan las de red y E/S tiene el sistema de archivos).


### Interfaces entre Usuario y SO
- Tenemos la Shell o CLI (Command Line Interface)
- Tenemos la GUI (Graphic User Interface), interfaz grafica

Y por último de System Calls o llamada de sistemas que vamos a desarrollar en profundidad. Dentro de una llamada al sistema tenemos que el usuario ejecuta un programa, llamando a la biblioteca y activa la trampa.

La trampa, es ese metodo que se usamos para poder hacer sys_calls. En el manejador de llamadas al sistema, lo que se hace es pasar el ID de la llamada (Para poder identificar que le hace falta) + los parametros que requiere al kernel. 

Para pasar los pasos de parámetros, tenemos varios metodos (En registo de CPU, Parametro en memoria y Parametros en una pila).

Los id de llamadas tienen su propia tabla, cada uno con su numero, y tienen un pequeño puntero a funcion con sys_read, para que empiece a trabajar, en este caso hace la rutina de servicio de la llamada, con sus sys_open una vez identificado.

Una vez fianlizado, se hace un iret para **SALIR** del modo Kernel, y ya finalizar el programa.



## Estructuras/Arquitecturas de los SOs

## SOs de propósito específico
