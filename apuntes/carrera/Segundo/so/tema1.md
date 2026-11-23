---
title: Estructuras de sistemas operativos
description: 
published: true
date: 2026-11-23T11:57:53.461Z
tags: 
editor: markdown
dateCreated: 2026-09-16T15:49:04.526Z
---

# Estructuras de sistemas operativos
## Recordatorio de TOC y FS
En este primer apartado, nos dedicamos a recordar lo que hemos dado el año pasado.

Durante esta asignatura vamos a también usar la abstracción como hemos visto en PDOO. 
Esto es importante ya que en SO y en HW, hay bastante poca abstracción y vamos a ir viendo porque se da esto.

### E/S

Los módulos de Entrada y Salida programada, se comunican el controlador de dispositivos (Device controller), que este a su vez se comunica con el dispositivo (device).

Las principales tecnicas de E/S son:
- Se manda a un comando de lectura a entrada salida -> Se lee el estado del modulo de entrada salida (Donde el primer campo del módulo de Entrada Salida va a estar en modo Ready o Busy, y también leerá si está OK o ERROR) -> Se comprueba el estatus (Ready, Not Ready, Error Condition) -> Se lee la palabra del módulo de E/S (Se pasa la información del I/O a la CPU) -> Escribir la palabra en memoria (De la CPU a Memoria).
> En el estado de estatus, se debe verificar que la operación sea READ y no WRITE, ya que de otro modo es un error de diseño.
{.is-danger}

- Es similar al anterior pero se puede bloquear un error o una interrupción via E/S, que vive del RSI (Explicado adelante), y una vez cometido el error avanza.
El código del kernel que se encarga del tratamiento  o la rutina del servicio de interrupción se llama RSI, que pasa de un OK a ERROR.

- Los DMA (Transferencia de Memoria directa) es el módulo que transfiere el bloque directamente a memoria. La CPU solo lo inicia y recibe una interrupción al terminar.

### CPU
Por otro lado la CPU usa varios registros, en los que tenemos PC (programa counter, dirrección de la siguiente instrucción a buscar) y IR (última instrucción buscada). Los registros de memorias de la CPU, tenemos:
- MAR: Contiene la dirección de la siguiente R/W. 
- MBR: Contiene los datos que van a escribirse o que se leen de la memoria.
- I/O AR: Son los registro de dirección de E/S.
- I/O BR: Son los registros de buffer de E/S
> Importante los dos primeros.
{.is-info}

Dentro de los registros de la CPU tenemos:
#### Registros de CPU de propósito general
Se acceden por programas y clasificarlo en registros de datos. Los más importantes son registros índice, puntero a segmento y puntero a la pila (BP: Base del marco de la pila actual, y SP es la cima de la pila, se clasifican en registros de datos y registros de direcciones).
#### Otros registros de CPU
Tenemos:
- Programa Counter (PC): Dirección de la siguiente ejecución.
- Instruction Register (IR): Última instrucción que se fué a usar.
- Program Status Word (PSW): Información de códigos de condición. Tenemos el modo de ejecución OO (Kernel, unicamente por el SO), 01 (Modo User). También tenemos los entry points que existe las: Interrupciones (Pueden ser internas al micro o excepción, excepciones y Llamadas al sistema (Provocadas por el SO o por nosotros).

> Las interrupciones vienen de un controlador de dispositivos y son asíncronas. Las excepciones las provoca la instrucción en ejecución (división por cero, fallo de página) y puede ser recuperables o no. Las llamadas al sistema (TRAP) son interrupciones software que pide el propio programa.
{.is-warning}
> El concepto de máquina desnuda es aquel que se define como: Todo repertorio por instrucción microprocesador (NO SIRVE ENSAMBLADOR), puede acceder a toda la memoria y solo permite E/S a bajo nivel.




### Memoria principal
Por último tenemos la memoria RAM o principal 

Es una tabla o array lineal compuesto por números de elementos con distintos tamaños. Las palabras son direccionables con números naturales desde el 0, siendo este número la dirección de memoria, y los espacio de dirección son un conjunto de número que representa las direcciones de una memoria.

Posee las operaciones de Lectura (R) y Escritura (W). Las direcciones se codifican en base 2, si utilizamos n bits para codificar las direcciones, el espacio de direcciones tiene una cardinalidad de 2^n direcciones.

Tenemos varios modelos de memoria:
- Flat memory model: Espacio lineal desde 0 hasta el 2^32-1,granularidad de byte. Con este método te permitiría acceder a una sección de memoria con el modo usuario. 
- Segmented memory model:Son aquellos programas que ven el espacio como espacios independientes llamados segmentos. Dirección lógica
- Real-address mode memory model: No es muy usado y no se va a explicar en profundidad hasta el tema 3.

La memoria RAM también interactua con el E/S:
- Control y temporización: Controlar la transferencia del dato al procesador.
- Comunicarse con el procesador y con el dispositivo.
- Almacenamiento temporal de datos o buffers: 
- Detección de errores:

Todos estos modulos estan conectadas entre ellas mediante buses donde destacamos:
- Control Bus
- Address bus
- Data bus


Si recordamos hablamos de las Entry Points, que son Interrupción, excepción y llamadas. Ahora vamos a hablar sobre el tratamiento de interrupciones:

### Interrupciones
El tratamiento de excepciones parte desde la parte Hardware de la siguiente manera:
1. El controlador solicita la interrupción. "El dispositivo controlador detecta un error y lo interrumpe."
1. La CPU termina la instrucción en curso. "El dispositivo controlador detecta un error y lo interrumpe."
1. Apila PSW y PC. "El proceso envia una señal informando de la interrupción." "El procesador mueve el PSW en modo 0 (modo protegido) y el PC al stack."
1. Se activa el modo kernel.
1. Carga el PC con el contenido del vector de dispositivo. "El proceador busca y carga el nuevo RSI(Rutina de Servicio de Interrupción), para identificar cual es el nuevo dispositivo que ha dado error. Este mecanismo se llama: Mecanismo de interrupciones vectorizadas (Consiste en un array, reservado en una zona de RAM intocable del Sistema Operativo, que contiene la dirección de la 1º Instrucción del RSI i, y también la dirección de la 1º Instrucción de la rutina servicio excepción, siendo divididas por el 80h siendo el gestor de general al sistema, cualquiera de estas pueden ser cargadas en memoria)."

> Con esto en cuenta, lo que se hace es que se añade en memoeria (PC), el VI[80h], que es el gestor general de llamadas al sistema.
{.is-info}

Ahora tenemos también la parte en Software:
- Se guarda o graba el resto del estado del procesador. Donde se salva todos los registros del RSI.
- El proceso se interrupte.
- Se reestablece el proceso de estado de la información.
- Por último lo que se hace el restaurar el antiguo PSW y el PC. Esto se hace con *i ret* (interrupt return). Donde lo que hace es cargar el marco de la pila y cargarlo en el registro (El PC y el PSW).


En las interrupción software o llamadas al sistema, cambia un poco con respecto al anterior. El hardware sigue apliando el PSW y el PC, activa modo kernel (0 protegido) y cagar el PC con el contenido del vector dentro del gestor general. 

El vector de interrupciones es un array en una zona protegida de la RAM. Cada entrada tiene dirección de la primera instrucción de una RSI o rutina de excepción. La entrada 0x80 es el gestor general de llamadas al sistema. 

Dentro de las interrupciones debemos saber que existe una prioridad de interrupciones donde cuanto menor sea el número mayor es la urgencia que tiene. En caso de intentar solucionar una interrupción de un valor mayor al que acaba de entrar, este se para y deja entrar al mas urgente. Esto se almacena en la pila de control de sistema, y se va a seguir almacenando y extrañendo conforme vaya resolviendo.
## Componentes de un SO

### Procesos

Lo primero que tenemos que definir una serie de cositas
- Procesos: Concepto que permite monitorizar y controlar la ejecución de varios programas. Tiene asociados el programa y su PCB. 

Un proceso al crearse lo que hace es:
- Crea o genera un PCB, donde se inicializa sus campos.
- Se carga el programa en RAM, para ir al gestor de memoria. 
- Nos establecemos en Listo, donde se generaria un pid_t PID (En unix),se le añade un contexto de registro del procesador (PC, PSW, SP, BR indica la base en la pila y LR indica el fin en la pila), añadimos el estado (que debe ser Nuevo, Finalizado, Listo, Ejecudandose o Bloqueado) y por último añadimos la memoria.

> Existen unas consideraciones con Multiprogramación, Compartir tiempo, Calendariod e CPU o memoria virtual por ejemplo.
{.is-info}

La multiprogramación nos habilita que varios programas se ejecuten a la vez, lo hacemos mediante un context_switch donde cambiamos el estado de ejecutado a bloqueado. Sin embargo esto puede generar problemas ya que la unica de manera de esperar otra E/S es entrar en modo bloqueado y no volver a Listo automaticamente.

En tiempo compartido, al agotarse el quantum el proceso pasa e Ejecución a Listo (no a Bloqueado) y el planificador da la CPU a otro.
> CPU scheduling y swapping se darán en el tema 2 y la memoria virtual en el tema 3.
{.is-success}


La funcionalidad de los procesos, tenemos la creación del PCB con todo lo explicado anteriormente y la eliminación del mismo a la hora de finalizarse, también el bloqueo (sleep) y desbloqueo (wakeup) que se verá más adelante, y por último la comunicación de procesos también se verá mas adelante.

### En la memoria
La memoria nos sirve para:
- Protección de la memoria del kernel y las regiones de programas.
- Compartición por parte de regiones ocupadas por programas para comunicarse entre ellos.
- Se encarga también de la jerarquía de la memoria con la asignación y liberación del mismo, mediante la memoria asignada y libre.
- Algoritmos para decidir cuánta memoria asignar a cada proceso y cuándo liberar toda la memoria de un proceso manteniéndolo en almacenamiento secundario (Swapping).

### Archivos y Directorios
Un archivo consiste en una colección de contenidos de información usualmente identificada.
Alguna de sus funcionalidades:
- Tiene los archivos de procesamiento (Abrir, cerrar, escribir, leer...) 
- Creacion, eliminacion...

El sistema de archivos gestiona la asignación y liberación de espacio de disco y mantiene la ubicación de los datos y los metadatos (inode en UNIX/LINUX)
### Dispositivos E/S
Donde se busca el controlar los funcionamientos de los dispositivos de E/S, la protección de su utilización por parte de las aplicaciones, tener una interfaz independiente y por último los Device Drives o el manejador de dispositivo.

### SO
Un sistema operativo en su gestión de recursos debe garantizar:
- Equitatividad: Garantizar el acceso a los recursos para todo proceso.
- Respuesta diferencial: Planificar la asignacuón de recursos teniendo en cuenta las características d elos clientes.
- Eficiencia: Maximizar la productividad, minimizar el tiempo de respuesta y, en tiempo compartido, permitir que trabajen tatnos usuarios como sea posible.

Dentro de un SO tenemos una serie de componentes:
- Gestor de procesos
- Gestor de memoria
- Gestor de archivos
- Gestor de E/S y gestor de comunicación (que son similares pero donde se diferencia en que, pero componentes separados, ya que el sistema de archivos pertenece al gestor de archivos).


### Interfaces entre Usuario y SO
- Tenemos la Shell o CLI (Command Line Interface)
- Tenemos la GUI (Graphic User Interface), interfaz grafica

Y por último de System Calls o llamada de sistemas que vamos a desarrollar en profundidad. Dentro de una llamada al sistema tenemos que el usuario ejecuta un programa, llamando a la biblioteca y activa la trampa.

La trampa, es ese metodo que se usamos para poder hacer sys_calls. En el manejador de llamadas al sistema, lo que se hace es pasar el ID de la llamada (Para poder identificar que le hace falta) + los parametros que requiere al kernel. 

Para pasar los pasos de parámetros, tenemos varios metodos (En registo de CPU, Parametro en memoria y Parametros en una pila).

Los id de llamadas tienen su propia tabla, cada uno con su numero, y tienen un pequeño puntero a funcion con sys_read, para que empiece a trabajar, en este caso hace la rutina de servicio de la llamada, con sus sys_open una vez identificado.

Una vez fianlizado, se hace un iret para **SALIR** del modo Kernel, y ya finalizar el programa.

> En detalle
{.is-success}

Una interpretación del system call es:
1. Se meten los nbytes en la pila
2. Se añade el &bufer en la pila
3. Se añade el fd en la pila
4. Se llama a la función read.
5. Se coloca el código para la lectura en el registro.
6. Se hace el trap al kernel y pasamos al espacio reservado del kernel (sistema operativo)
7. El despachador busca y llama al manejador de llamadas al sistema.
8. Se regresa del espacio del jernel, con el procedimiento llamador
9. La biblioteca devuelve lo que ha traido el trap
10. Se incrementa el SP y se hace el read.

Alguno de los identificadores de llamada importante de Linux son:
- 0: Read
- 1: Write
- 60: Exit

## Estructuras/Arquitecturas de los SOs
Existen dos tipos de arquitecturas principales:
### Arquitectura monolítica
Es la más utilizada, la que se usa ahora o la que "funciona". El SO es el único programa que se ejecuta en el modo más privilegiado del procesador (ring 0).

Alguno de los problemas, es que posee una fuerte dependencia de módulos, es por ello que hay dificultad a entender el codigo o realizar cosas. A su vez, si cualquier módulo falla o crashea, se puede provocar la caída del sistema.

Los servicios se obtienen por llamadas al procedimiento y los módulos no ocultan información.
### Arquitectura microkernel
Una pequeña parte de la funcionalidad del SO se implemente como kernel y el resto como procesos del user. 
Este tipo de arquitectura el microkernel soporta memoria virtual de bajo nivel, creación de procesos (hebras), comunicación y sincronización. 

En este modelo, no tenemos procesos todo el procesos, propiamente dicho, tenemos mensajes.

La aplicación hace send(Server, &m) y espera con receive(Server,&r). El microkernel entrega el mensaje al servidor, que genera el resultado y lo envía al kernel para que lo devuelva a la aplicación.

Ventajas y desventajas:
- Fiablidad: Los errores de módulo, no provocan el crasheo del S.O., por lo tanto puede recuperarse.
- Extensibilidad: Se pueden ir añadiendo nuevos sercivios como usuarios.
- Peor rendimiento: Lamentablemente este tipo de arquitectura microkernel tiene un rendimiento menor, ya qu ese deben hacer varios cambios de modo y de espacio de direcciones para que sea funcional.

## SOs de propósito específico
Tenemos servidores especificos segun el uso.
### RTOS (SO de Tiempo Real)
Se suelen utilizar para aplicaciones especializadas, usualmente por sistemas de control. Este tipo de SO debe garantizar una corrección tanto del resultado lógico como del tiempo empleado para saber los resultados.

Sin embargo, el problema es planificar las actividades para cumplir todos los requisitos de tiempo (planificador).

Algunas cosillas extra y caracteristicas:
- Los RTOS clasifican los procesos en el tiempo real.
- Los procesos RT tienen de objetivo procesar eventos que se producen regular o irregularmente, los procesos RT tienen un deadline de inciio o de finalización.
- Los eventos ocurren en tiempo real.
- Determinismo: Tiempo en reconecer una interrupción.
- Reactividad: Tiempo que tarda la RSI. Tanto este como el determinismo determinan el tiempo de respuesta.
- Control de prioridad de los procesos RT.
- Fiabilidad: Posee mayor tolerancia a fallos, un RTOS es estable si, cuando no puede cumplir todo los plazos, cumple los de los procesos más críticos.

### SO para Sistemas Empotrados
Los SO para sistemas empotrados, esta especializado para utilizar computadores incluidos en sistemas más grandes. Estos computadores pueden ser los de un coche o el GPS

El EOSs viene más limitada que un SO normal. Suelen proporcionar robustez a la ejecución de procesos ya que lidia con restricciones de memorias.