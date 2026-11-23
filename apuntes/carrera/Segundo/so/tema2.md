---
title: Procesos y Hebras
description: 
published: true
date: 2026-11-23T16:10:17.379Z
tags: 
editor: markdown
dateCreated: 2026-09-30T16:41:57.893Z
---

# Procesos y Hebras
## Conceptos fundamentales sobre procesos
Proceso = programa + estado de ejecución. Para ejecutarse necesita al menos memoria para texto,datos y pila, y los registros de la CPU.

Un proceso se define como un programa que esta en ejecución y esta ejecución debe realizarse sin interferencias, provocada por la ejecución de otros programas.
- Un programa es un fichero estático que se puede ejecutar.
- Un proceso es lo mismo que un programa que se esta ejecutando.

Toda ejecución de programa es caracterizada por su traza de ejecución. Distintos procesos pueden ejecutar el mismo programa.


Todo proceso requiere de recursos que el SO se encarga de controlar, como puede ser memoria, CPU... Dentro del apartado de ejecución de la CPU, se debe diferenciar entre la ejecución de usuario y la ejecución de kernel, similar pasa a la memoria que está en estado protegido del kernel (Donde solo opera el kernel y el codigo de este espacio es llamado reentrante) y la de continuo o usuario (Donde cada proceso tiene un espacio de direcciones protegido).


Para la ejecución debemos tener en cuenta:
- Contexto del proceso: Para el modo usuario sería el código del propio usuario, para el modo kernel los syscalls y excepciones
- Conexto de kernel: En modo usuario no está permitido sin embargo para el modo kernel, es el tratamiento de interrupciones y tareas del sistema.

El SO se ejecuta de la siguiente manera:
- El núcleo se ejcuta como una entidad separada en modo kernel, no como un proceso normal y el código del sistema operativo se opera de forma separa al modo kernel.

Todos los procesos comparten el mismo espacio de kernel. Cada proceso tiene su propia pila de kernel porque el codigo del kernel es reentrante. La información de memoria de cada proceso se guarda en memoria del kernel.

A la hora de pensar en proceso, debemos pensar en, una unidad de actividad caracterizada por:
- La ejecución de una secuencia de instrucciones (traza).
- Un estado de computación actual (contexto).
- Un conjunto de recursos (dado por el SO).

Cuando el SO decide que el proceso en ejecución abandone la CPU, guarda los registros en su PCB. Esa acción de pasar la CPU a otro proceso es el cambio de contexto. Su tiempo va en detrimento de la productividad.

### PCB Process Control Block
Tenemos que definir PCB (Process Control Block), es una estructura de datos que contiene información relativa al concepto del proceso, ya que es algo creado gestionado y destruido unicamente por el kernel, conteniendo la siguiente información:
- PID (Process IDentifier)
- Process State (Del diagram de estado, Listo, ejecución, bloqueado...)
- Contexto de registro
- Información de memoria
- Lista de recursos utilizados

Por lo tanto un proceso tiene texto y datos asociados, a su vez tiene una pila asociada, y el SO almacena toda esta inforamción en el PCB, es por ello que podemos definir PCB como metadatos en la memoria de los procesos. (El PCB reside en memoria del kernel, no en el espacio de usuario del proceso)

Todos los cambios que se realizan en el proceso, incluso sus datos guardados por detención se salvan en el PCB. 

El keernel mantiene una tabla de procesos principal (una entrada pro proceso) y tablas de memoria, de E/S y de archivos.
### Cambio de contexto
Es un apartado importante, ya que nos permite entender el "multitasking OS" o SO multitareas, esto sucede:
- Cuando un proceso en ejecución acaba su tiempo en de ejecución (timeout o se acabo su timeslice)
- Como consecuencia de una llamada que bloqueante del sistema.
- Debido a una interrupción.
- El proceso abandona por si mismo la CPU.

Es la función del despachador (dispatch), que veremos en la parte de planficación:
- Dejar en suspenso la ejecución de un proceso, almacenando los datos en el PCB
- Restaurar el contexto de registro del proceso que se va a ejecutar en CPU.
- Continuar con el ciclo de captación-ejecución de instrucciones utilizando el nuevo valor de registro PC.

Solo puede hacerse en modo kernel (porque toca registro privilegiados y el PCB). Cuesta nanosegundos, pero se hacen cientos o miles por segundos.
## Operaciones sobre procesos
La creación del proceso, consiste en la asignación de espacio de direcciones que se utilizará, y la creación de estructuras de datos para que se administre.

Un proceso se crea:
- Por sistema batch: Respuesta a la recepción y admisión de un trabajo.
- "logon" interactivo: Un usuario se autentifica en un terminal, y el SO crea el proceso de intérprete.
- El SO crea un proceso para llevar a cabo el servicio solicitado por el usuario.
- El proceso puede crear otros procesos, dando la relación padre-hijo.

En el último caso, el hijo obtiene los recursos mediante:
- Del SO sin que el padre intervenga.
- Compartir todo los recursos con el padre.
- Comparte algunos recursos del padre.

Este tipo de procesos pueden ejecutarse o bien concurrentemente o que el hijo termine y el padre este esperando a ello.

Respecto al espacio de direcciones, el hijo obtiene una copia del padre o se le da uno nuevo.


### UNIX-like OS
Los procesos UNIX-like OS, funciona de manera especial:
- Las llamadas al sistema "fork()", crea un hijo con una copia idéntica de la memoria y de los registros de CPU del padre. Padre e hijo continúan en el mismo punto, tras el retorno de "fork()", puede valer 0 al hijo y el PID del hijo al padre (puede devover -1 en caso de error).
- La llamada "exec()", lo que hace es reemplazar un espacio de direcciones. Es decir eliminará la memoria copia creada para el hijo
"fork() + exec()" es lo que hace un shell para ejecutar una orden.

> El PCB hijo obtiene: PID único, el registro del padre, el estado será nuevo **NO BLOQUEADO**, la memoria la cpia del padre. 
{.is-info}

En la creación de un proceso, lo hace "program loader" con los siguientes pasos:
- Creación de un PID único.
- Asignar espacio en memoria RAM o SWAP.
- Crear el PCB e inicializar campos de información.
- Insertar inforamción del PCB en la tabal de procesos (una lista donde estan todos los procesos).
- El último paso es enlazar la PCB a la cola de planificación, con posibilidad de estar en Listo o en Listo-suspendido (Ram o Swap).

Al finalizar un proceso, este llama al SO para solicitar un exit(), que provoca:
- Un aviso de finalización al padre, guardando su estado. (SIGCHLD)
- Los recursos son liberados
- El padre finaliza la ejecución de sus hijos mediante kill()
- El padre va a finalizar y por lo tanto el SO va terminando los procesos hijos evitando que continuen (Denominado terminación en cascada). En UNIX por otro lado, lo que se hace es dejar "colgados" los procesos, asociandolo al padre en init (systemd).
- También es posible que el SO termine un proceso por errores o condiciones de fallo.

> El proceso wait(), es usado por el padre únicamente para poder sincronizarse con sus hijos.
{.is-info}

## Threads o hebras
Una hebra, es una unidad básica de utilización de CPU, y para poder operar con ella el kernel requiere:
- TID, otro tipo de identificador.
- Contexto del registro: PC, PSW o SP entre otros
- Pila de ejecución, debido a que tenemos el PC ("prown counter").
- Por hebra, el kernel necesita: conexto de registros, pila y estado. La hebra comparte con sus pares una tarea (proceso), que mantiene código, datos y recursos del SO (archivos abiertos, señales). Un proceso tradicional es una tarea con una sola hebra.
Una hebra comparte con sus hebras pares (procesos familiares por asi decirlo), la información necesaria como es codigos, datos o recursos del SO.

Debido a que una hebra no tiene memoria HDD, es inviable que estas puedan entrar en un estado suspendido. Lo unico que podemos hacer es pasarlo a un estado de memoria SWAD, pero no a memoria HDD.

> Todo el conjunto de datos de los Thread lo llamaremos Thread_CTRL_Block o TCB.

Tenemos varios tipos de S.O.
- Aquel que no reconoce el concepto de hebra "single threading".
- Aquel que el kernel es capaz de soportar múltiples hebras de un proceso "multithreading"
> UNIX tradicional soporta varios procesos pero una sola hebra por proceso. Fue con Sun Solaris donde se empezo a soportar varias hebras por proceso.
{.is-info}
Los estados de la hebra son:
- Nuevo
- Ejecución
- Listo
- Bloqueado
- Finalizado
Aparte también tiene, creación, bloqueo, desbloqueo y terminación.

Los tipos de threads, teniendo en cuenta la distinción entre single threading y multithreading.

Tenemos dos modelos de hebras
### ULT
Toda gestión de hebras se realiza a nivel de usuario, mediante biblioteca de hebras. La biblioteca se encarga de: creación/finalización, gestión de modelos de estado, planificación, salvar y cargar el contexto y la comunicación entre hebras.

Sus ventajas son:
- El cambio de hebra no hay cambio de modo.
- La planificación se adapta a la aplicación.
- Las aplicaciones se ejecutan en cualquier SO.

Por otro lado sus desventajas:
- La mayoría de llamadas al sistemas son bloqueantes, debido a que cuando una hebra llama el resto se bloquea.
- El kernel al asignar procesos a procesadores, no se puede asignar más de un procesador a más de una hebra.

La entidad de planificación para el kernel es el proceso. Si una hebra de usuario hace una llamada bloqueante, se bloquea toda la tarea (N:1).
### KLT
Toda la gestión se realiza a nivel de kernel, manteniendolo informado de los procesos y hebras. El SO proporciona un conjunto de llamadas al sistema, la entidad de planificación para el kernel es la hebra.

Sus ventajas son:
- El kernel planifica distintas hebras de la misma tarea en distintos procesadores
- El bloqueo de una hebra no provoca el resto de bloqueos evitando el problema de ULT
- Las rutinas de kernel puede ser multihebras
Desventajas:
- El cambio de hebras en una misma tarea se realiza a modo kernel, provoca un cambio de modo.

La entidad de planificiación es la hebra con correspondencia a 1:1, solo se bloquea la hebra que llama.
### El híbrido
Existe una versión hibrida creada por Solaris OS y adaptada por los UNIX posteriormente, que tiene de característica su flexibilidad dada principalmente porque es el programador quien decide el número de KLTs. Además puede hacer:
- Las ULT son proporcionadas por biblioteca de hebras invisibles para el kernel.
- La creación de hebras viene en modo usuario.
- Las KLT se usan de unidad de planificación en el kernel.
- Los procesos ligeros (LWP) soportan una o más ULT, y se asocian con una KLT. Así, las hebras que pueden bloquearse no bloquean al resto.
## Conceptos fundamentales sobre planificación
La planificación viene debido a que tenemos el problema de tener n "clientes" que quieren el mismo recurso y debemos intentar decidir a quien asignarlo.

La definición del problema de planificación de CPU:
- El SO dispone de "n" procesos/hebras en esatdo "Listo".
- El SO dispone de varios cores para ejcutar las hebras o procesos.
- El SO debe decidir que procesos o hebras asignar a qué CPU.

Hay un modelo genérico de colas, donde el SO tiene una colección de colas que representan el estado de todos los procesos en el sistema. Típicamente hay una cola por estado del proceso, cada PCB esta encolado en una cola de estado acorde a su estado y conforme un proceso haga un cambio de estado su PCB se va retirando, y enconlando en otra.

Estas colas peuden ser:
- Cola de trabajos: Conjunto de los trabajos pendiente de ser admitidos en el sistema.
- Cola de LISTOS: Conjunto de todos los procesos, cuyos programas asociados residen en memoria principal, esperando para poder ejecutar en la CPu.
- Cola de BLOQUEADOS: Conjunto de todos los procesos esperando por un dispositivo E/S particular.

La mezcla de trabajos la definimos como, si todos los procesos son limitados por E/S, la cola de listos casi simepre está vacia. Si todos son limitados por CPU, las colas de E/S casi siempre están vacias. Hay que mezclar.

Tenemos distintos tipos de planificadores (parte del SO encargado de controlar la utilización de un recurso):
- Largo plazo: Selecciona los trabajos que deben llevarse a la cola de preparados, se invoca poco frecuentemente y es más lento, pero permite controlar el grado de multiprogramación.
- Planificador a corto plazo: Se resumen en el planificador de CPU. Se invoca frecuentemente por lo que es mas rapido.
- Planificador medio plazo: Se suele encargar de devolver procesos a memoria, en algunos SO de tiempo compartido, a veces es necesario sacar procesos de la memoria. 


Hay dos tipos de procesos (demasiado extremizado):
- Procesos limitados por E/S o procesos cortos, donde suele estár mas tiempo en E/S que operando en CPU
- Procesos limitados por la CPU o procesos largos.
### Dispatcher
El dispatcher() o despachador, tiene la función de otorgar el control de la CPU al proceso seleccionado por el planificador a corto plazo. Existe el termino de latencia de despacho, que es el tiempo que tarda en deterner un proceso e iniciar otro.

Suele entrar en acción con:
- Cuando un proceso finaliza o no puede continuar(seb bloquea), el despachador hace el cambio de contxto de registor y conmuta a modo usuario o kernel segun el nuevo contexto.
- Un elemento del SO determina que ese proceso no puede seguir.
- El proceso se queda sin tiempo.
- Un proceso cambia de Bloqueado a Listo.

### context_switch()
'context_switch() = schedule() + dispatch()'
- 'schedule()': el planificador de CPU. **Decide** qué proceso va a ejecutarse.
- 'dispatch()': el despachador. **Ejecuta** la decisión: guarda el contexto de registros del proceso saliente en su PCB, restaura el del entrante y conmuta a modo usuario o kernel según el nuevo contexto.

¿Cuándo toma decisiones de planificación el SO (cuándo llama a 'schedule()')?
1. **E → B**: el proceso en ejecución se bloquea (p. ej. dentro de 'RutinaE/S()' o de la syscall 'wait()').
2. **E → F**: el proceso termina ('sys_exit()').
3. **E → L**: se agota el quantum, dentro de la 'RSI_reloj()'.
4. **{N, B, SL} → L**: un proceso pasa a Listo y hay que decidir si apropiarse de la CPU (implementa la *preemption*).

- Política **no apropiativa**: solo cuentan los casos 1 y 2.
- Política **apropiativa**: cuentan los cuatro.

### Medidas
Usaremos medidas para poder determinar la productividad y el servicio de los planificadores, estas medidas pueden ser dadas por:
- Rafaga ($r$): Consiste el tiempo de servicio que necesita el proceso.
- Tiempo de respuesta ($T$): Tiempo transcurrido desde la solicitud hasta la primera respuesta.
- Tiempo de espera ($M = T-r$): Tiempo que ha estado esperando en cola de Listo.
- Penalización ($P = T/r$)
- Indice de respuesta ($R = r/T$): Fracción de tiempo donde la penalización está recibiendo servicio.

Otras medidas interesantes son:
- Tiempo del núcleo: Tiempo perdido por el SO tomando decisiones. El tiempo del núcleo (el peridido en decisiones de planificación y cambios de contexto) debería estar entre el 10% y el 30% del total en un sistema eficiente.
- TIempo de inacividad: Tiempo en el que la cola de ejecutables está vacía.
- Tiempo de retorno: Cantidad de tiempo necesario para ejecutar un proceso completo.

Las políticas de planificación, se comporta de distintas manera dependiendo de las clases de procesos, se pueden clasificar en:
- No apropiativas: Una vez que se le asigna un proceso, no se le puede retirar.
- Apropiativas: El SO puede apropiarse del procesador cuando lo desee.
Busca dar un buen rendimiento y servicio.

Ninguna política es satisfactoria para todos: mejorar a una clase de proceso va en contra de otra.
## Políticas de planificación de la CPU
Dentro de la CPU tenemos distintas politicas:
- FCFS (First Come First Served)
- Shortest Job First (SJF): Donde esta apropiativo (SRTF) y no apropiativo
- Planificación por prioridades
- Por turnos (Round-Robin)
- Colas múltiples
- Colas múltiples con realimentación

Vamos a ir describiendo cada una.
> Toda referencia a tiempo estimado es rafaga estimada.
### FCFS (First Come First Served)
Los procesos se ejecutan segun el orden de llegada, se considera no apropiativo (se ejecuta hasta que termina), es de fácil implementación pero pobre prestación. 

Penaliza fuertemente a los procesos cortos mientras uqe los largos no tanto.


#### Escenario inventado
Vamos a dar una serie de valores para ver el problema:
- R (Indice de respuesta)= 1000 mseg (1 seg)
- r (Rafaga)= 10 mseg

Dado los datos anteriores, vamos a calcular el proceso r (Proceso de E/S), dadas 1000 operaciones de E/S. Se traduce en dar 1000 veces la vuelta de Listro -> Ejecutandose -> Bloqueado...

Cada proceso (r) lee 1 bloque cada segundo, por lo tanto los mil bloques tardara 1000 segundos.

En caso de tener un planificador de timeout 10 mseg, los procesos finalizarían en 10 segundos.

### SJF
Ahora tenemos el más corta primero, donde se busca aquel servicio con un tiempo de servicio menor, este proceso tampoco es apropiativo. 

En caso de que dos procesos sean igual en tiempo, se usa FCFS.

Disminuye el tiempo de respuesta de los procesos cortos y discriman a los largos. 
> Para determinar el tiempo estimado, tenemos una constante en la PCB. A su vez tenemos dos parametros "tiempo entrada" y "tiempo sale" de la CPU, la rafaga la mediremos entre la diferencia de entrada y salida.
{.is-info}

El problema de este método, debemos tener en cuenta que existe la posibilidad de inanición, donde un equipo proceso NUNCA va a poder entrar en el equipo. Por ello también se puede hacer dos planificadores:
- tiempo de llegada a listo: Marca simplemente la hora donde han entrado en listo.
- M = tiempo actual - t llegada de listo: Marca el tiempo que lleva actualmente esperando.

Lo que se puede hacer es que cuando M llegue a un umbral deseado, modificamos su supuesto tiempo estimado al mínimo para que sea el primero.

Tiempo medio de espera bajo.
### SRTF (Shortest Remaining Time First)
Es similar al anterior, pero con una apropiación de la CPU. Donde si el servicio que ha entrado en cola es menor que el tiempo de servicio al que se esta ejecutandose.

En caso de que haya un proceso con menor tiempo, se realiza un cambio de contexto y este pasa a la zona de listos. 

Lo que se hace es calcular el tiempo restante mediante, tiempo estimado - (tiempo actual - tiempo llegada a la CPU). 

Se comprueba al entrar un proceso a la cola de listos. Da la menor penalización media (mantiene la cola de listos al mínimo).
### Planificación por prioridades
Aquí se le asocia a cada proceso un número de prioridad (entero), por lo tanto en el PCB en su apartado de planificación ahora hay un entero que indica su prioridad.

Cuanto mayor prioridad menor va a ser el entero (Método tradicional), y también puede ser apropiativa o no paropiativa.

Sin embargo tenemos el mismo problema que antes, la inanición (donde los procesos de baja prioirdad no puede ejecutarse), sin embargo se puede ir dadonle prioridad segun pase el tiempo (La solución es envejecimiento).

### Round-Robin ( O por Turnos)
La CPU se asigna espacios de tiempo (quatum - timeskips).

Dentro de estos tiempos, se puede dar:
- El proceso finaliza o bloquea antes de agotar el quantum, por lo tanto se libre de la CPU y se va a la cola.
- El proceso no termina y se apropia, colocandose al final de la cola de ejecutables.

Penaliza a todos los procesos por igual, cortos o largos. Las ráfagas muy cortas quedan más penalizadas de lo deseable. 

Los valores del quantum (Tipico de 10 a 100ms) se puede medir en:
- Muy grandes se convierten en FCFS
- Muy cortos, el sistema monopoliza la CPU haciendo constantemente cambios de contexto
### Colas múltiples
La cola de listos tienen una división en varias colas y cada proceso es asignado **PERMANENTEMENTE** a una de esas colas, cada cola posee un algoritmo propio (Unos usas RR, otros usas FCFS...).

Cada cola se tiene un planificación indicada:
- Planificación con prioridades fijas: Primero se sirven los interactivos y luego los batch (No importante)
- Tiempo compartido entre colas: (No importante)

El ejemplo del reparto de tiempo 80% a interactivo con RR y 20% a batch con FCFS.
### Multilevel Feedback Queue (Colas múltiples con realimentación)
Se tienen distintas colas, donde en cada cola se ejecuta un algoritmo distinto, su diferencia con el anterior, es que en este podemos fragmentar o indicar las colas cuales son para que cosa. Por ejmplo si tenemos 127 colas, dedicarle los 60 primeros al kernel.

Los procesos pueden moverse entre colas a diferencia de las colas múltiples, estos procesadore se pueden mover entre las colas.

Todas entran en la cola de mayor prioridad. Cada cola usa RR. Entre colas hay prioridades no apropiativas. Si un proceso consume su quantum completo sin bloquearse pasa a la cola i+1. En la última cola permanente hasta que termina.

Para poder usar esto debemos definir:
- Número de colas.
- Algoritmo usado en cada una de las colas.
- Método para determinar cuando mover de un proceso a una cola o a otra.
> Consideremos que tenemos 5 colas, y cada una consume un quantum distinto ($q_1,q_2,q_3,q_4,q_5$). Si un proceso es más grande que el quantum, entonces lo movemos a la siguiente cola que tiene un quantum de mayor tiempo, para que no se "divida" o deba usar más de uno.
- Método para determinar que cola se introducirá primero
- Algoritmo de planificación entre las colas. Y si el proceso está en un número menor de cola 

> Se puede dar el caso de inanición, para ello se va moviendo el proceso a una cola inmediatamente superior o una serie de colas superior.
{.is-danger}

Mide en ejecución el comportamiento real de los procesos y es el esquema usado en Unix, Linux y Windows.
### Planificación en multiprocesadores
Dentro del mundo de multiprocesadores tenemos una serie de cosas a tener en cuenta:
- Granularidad (Que consiste en la frecuencia de sincronización), donde tenemos grano grueso (Procesos con baja sincronización) y grano medio (hebras con alta sincronziación).
- Planificación de procesos, igual que en monoprocesadores pero tenemos en cuenta (nº de CPUs y asignación liberación de procesos)
- Planificación de hilos (Permite explotar el paralelismo real dentro de una aplicación)

Algunos aspectos de diseño son:
- Asignación de procesos a procesadores
- Uso de multiprogramación en cada procesador individual
- Activación del proceso: plnif_CPU(), para nuevos aspectos multihebras.

Indagamos un poco más en los diseños
#### Asignación de procesos a procesadores
Consiste en una estrategia simple, donde se trata los procesadores como una pool de recursos a asignar (ya sea estatico o dinamico), también asigna estáticamente procesos a un procesador, con una cola dedicada para cada procesador.

Sus soluciones son que asigna dinámicamente proceso a procesador, con cola global para todos los procesadores, y con un balance dinámico de carga.

#### Uso de multiprogramación en cada procesador individual
En el momento que hay muchos procesadores y granularidad media, el maximizar la utilización de CPU pasa a segundo plano en detrimento de aumentar la productividad de las aplicaciones.

Para ello tenemos:
1. Compartición de carga, con una cola global de hilos preparados (En modo LISTO), cuando un procesador está ocioso, se selecciona un hilo de la cola.
2. Planificación en pandilla, se planifica un conjunto de hilos afines, para ejecutarse un conjunto de procesadores al mismo tiempo. Suele funcionar bien para aplicaciones.
3. Asignación de procesadores deidcado, cuando se planifica una aplicación, se asigna un procesador a cada uno de sus hilos hasat que termine la aplicación. Lo que puede provocar que algunos procesadores puede estar ociosos.
4. Planifificación dinámica, la aplicación permite que varíe dinámicamente el número de hilos en un proceso, donde el SO ajusta la carga para mejorar la utilización.

### Planifiación en sistemas de tiempo real
La exactitud del sistema no depende sólo del resultado lógico de un cálculo sino también del instante en el que se produce.
Las tareas intentan controlar o reaccionar ante sucesos que se producen en "tiempo real". 

Los distintos enfoques depende de:
- Cuándo el sistema realiza un análisis de viabilidad de la planififación, estudia si puede atender a todos los eventos periódicos dado el tiempo necesario para ejecutar la tarea y el periodo.
- Si éste se realiza estática o dinámicamente.
- Si el resultado del análisis produce un plan de planificación.

Tiene un plazo real duro (es un plazo obligatorio) frente a un plazo suave (no obligatorio) sobre tareas periodicas frente a las aperiodicas.

Tenemos una serie de enfoques:
- Enfoque estatico dirigido por tabla: Análisis estático que genera una planificación que determina cuándo empezará cada tarea.
- Enfoque estaticos expulsivos dirigos por prioridad: Los análisis no generan una planfiifcación, solo se usa para dar prioridad a las tareas. 
- Enfoques dinámicos basados en un plan: Se determina la viabilidad en tiempo de ejecución, aceptando una nueva tarea si es posible satisfacer sus restricciones de tiempo.
- Enfoque dinámico de menor esfuerzo: No se hace análisis, el sistema pretende cumplir todos los plazos y abortar ejecuciones si su plazo ha finalizado.


Hay un problema en todos los sistemas llamado de Inversión de Prioridad.

Este problema es un problema de condición de carrera (no podemos controlar), una tarea de mayor prioridad espera por una tarea de menor prioridad debido al bloqueo de un recurso de uso exclusivo. En herencia y techo de prioridad, la tarea recupera su prioridad original al liberar el recurso.
> Pongamos 3 procesos, con prioridades 1(high), 60(medium) y 127(low). Los procesos comparten una sección crítica, y el low ha sido quien ha entrado primero, y después viene el high. El high se queda esperando y se bloquea por falta de recursos, pero cuando se libera el low entra el medium, dejando al high desbloqueandose y cuando entre en listo se colará cuando medium termine.

Para evitar esto:
- Herencia de prioridad: La tarea menos prioritaria hereda la prioridad de la tarea más prioritaria.
- Techo de prioridad: Se asocia una prioridad a cada recurso de uso exclusivo que es más alta que cualquier tarea, y esa prioridad se le asigna a la tarea que le de ese recurso.
## Implementación de procesos/hebras en Linux: task

> Vamos a ver muchas cosas repetidas
{.is-warning}
Tenemos el PID (**P**rocess **ID**entifier), y el núcleo identifica a cada proceso gracias a esto. En linux, los procesos es la misma entidad que se crea con la llamda del sistema **fork()** y **clone()**.

Los procesos especiales que existen durante la vida del sistema son:
- Proceoss 0: Creados a mano cuando arranca el sistema y crea al proceso 1 (init).
- Proceso 1 (init): Antecesor a cualquier proceso del sistema.

El kernel almacena la lista de procesos como una lista circular doblemente enlazada (task list), cada elemento e sun descriptor de proceso (PCB).

La tast_struct cotniene:
- Estado
- Prioridades (prio, static_prio, normal_prio)
- Policy
- Sched_class
- Sched_entity
- MM
- PID
- Punteros: parent, children, sibling, rt_priority
- Datos de señaeles.

Dentro de los estados tenemos:
- TASK_RUNNING: Ejecutandose
- TASK_INTERRUPTIBLE: Bloqueado, sale con el suceo o con una señal
- TASK_UNINTERRUPTIBLE: Bloqueado, solo sale con el suceso nada de señal.
- TASK_STOPPED: Detenido
- TASK_TRACED: Esta siendo trazada
- EXIT_ZOMBIE: No existe pero conserva su task_struct

En los procesos lo que sucede es:
- Cuando el proceso $P_0$ hace un **fork()**, se genera un proceso $P_1$, por lo tanto $P_0$ es padre de $P_1$ (siendo este el hijo).
- Si el proceso $P_0$, hace varias llamadas al sistema **fork()**, genera varios procesos hijo y la relación entre ellos es de hermanos.
- Todo los procesos son descendientes del proceso init (PID 1).


A nivel de kernel, no se sabe diferenciar lo que es una hebra y un proceso, linux implementa el concepto de hebra como si fuera un proceso sin más, que simplemente comparte recursos con otros procesos. 

Toda hebra tiene su propia **task_struct**.

Sobre las hebras del kernel, tenemos:
- A veces es útil que el kernel realice operaciones en segundo plano, para lo cual se crean hebras kernel. 
- Las hebras kernel no tienen espacio de direcciones.
- Se ejecutan únicamente en el pesacio del kernel.
- Son planificadas y pueden ser apropiadas.
- termina cuando hacen **do_exit()**

Sobre la creación de tasks se hace lo siguiente:
- Se hace un **fork()**, que invoca el **clone()**, y este hace un **do_fork()** llama a **copy_process()**.

Esta última hace:
1. Crear la estructura thread_info (pila kernel) y la task_struct para la nueva tarea.
1. Asigna valores inciales a los campos de la task_struct de la tarea hija.
1. Se establece el campo de estado para la trea hija.
1. Se establece valores adecuados para los flags de la tarea (**PF_SUPERPRIV=0** no es superusuario, **PF_FORKNOEXEC=1** hace fork() pero no exec()).
1. Se llama a **alloc_pid()** para la nueva PID.
1. Depende los flags enviados, puede duplicar o compartir recursos.
1. Se establece el estado de la hija a TASK_RUNNING
1. Por último **copy_process()** termina devolviendo un puntero a la task_struct de la tarea hija.


Para terminar las tareas de task_struct:
El kernel siempre libera todos sus recursos notificando al padre de la terminación y esto sucede cuando:
- Se hace una llamada a **exit()**, ya sea explícita (incluido en el programa) o implícita (El compilador añade exit() cuando termina el main()).
- Se recibe una señal de terminar al proceso (Term).

Por otro lado el do_exit() hace:
1. Activar el flag **PF_EXITING** de task_struct
1. Para cada recurso utilizado se crea un contador que va bajando cuando deja de usarse, cuando este llega a cero se destruye el recurso.
1. El valor que se pasa como argumento a **exit()** se almacenará en exit_code.
1. Se manda la señal de SIGCHILD al padre, por la finalización de su hijo.
1. Si todavía tiene hijos se hace hijos de init
1. Se establece el campo state a **EXIT_ZOMBIE**.
1. Se llama schedule()  (O content_switch()) para que el planificador haga otro proceso a ejecutar.


## Planificación de CPU en Linux
### Clases y políticas
Planificador modular con tres clases (tiempo real, CFS e idle). Entre clases hay prioridades apropiativas. Cada clase tiene un rango de prioridades, una cola por número. La entidad de planificación es sched_entity. Políticas CFS: SCHED_NORMAL, SCHED_BATCH, SCHED_IDLE. Políticas de tiempo real: SCHED_RR y SCHED_FIFO. Prioridades: [0,99] tiempo real, [100,139] normales. El proceso en ejecución es siempre el más prioritario.
### Planificador periódico: scheduler_tick()
Se llama con frecuencia HZ constante (100 a 1000 Hz). Actualiza estadísticas y llama a task_tick() de la clase. Si hay que replanificar, activa TIF_NEED_RESCHED en thread_info.
### schedule()
Se invoca de forma explícita cuando un proceso se bloquea o termina, y al volver a modo usuario desde syscall, RSI o excepción si TIF_NEED_RESCHED está activo. Pasos: determinar la runqueue y el puntero prev; actualizar estadísticas y limpiar el flag; si prev pasaba a INTERRUPTIBLE y recibió su señal, ponerlo en RUNNING; llamar a pick_next_task() de su clase; si cambia la asignación, context_switch() («nuestro dispatcher»).
### CFS
Reparte la CPU de forma imparcial. Calcula un peso por proceso (a mayor valor de prioridad estática, menor peso). El vruntime es el tiempo virtual consumido, calculado con el tiempo real, la prioridad estática y el peso. Se actualiza periódicamente, al llegar un proceso ejecutable y al bloquearse el actual. Se elige el de menor vruntime, guardados en un árbol rojo-negro con vruntime como clave.
Bloqueo en CFS: 1) a la cola del motivo; 2) estado INTERRUPTIBLE o UNINTERRUPTIBLE; 3) se quita del rbtree; 4) schedule(). Al desbloquear: 1) estado TASK_RUNNING; 2) se saca de la cola de bloqueo; 3) se añade al rbtree.
### Tiempo real
Clase rt_sched_class, siempre antes que los normales. La prioridad se fija al crear y el kernel no la modifica. Con SCHED_RR y SCHED_FIFO, Linux es soft real-time. La política se puede cambiar con una syscall.
### SMP
Repartir la carga entre CPUs, respetar la afinidad de la tarea con una CPU y poder migrar procesos (costoso). Periódicamente se comprueba el equilibrio y se reequilibra.