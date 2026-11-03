---
title: Sincronización en memoria compartida
description: 
published: true
date: 2026-11-03T10:21:41.557Z
tags: 
editor: markdown
dateCreated: 2026-10-09T16:36:44.576Z
---

# Sincronización en memoria compartida
Las sincronizaciónes que vamos a ver en este tema, va a estar dividido en dos:
- Soluciones en bajo nivel con espera ocupada: Basadas en programa que contiene explícitamente instrucciones de bajo nivel de lectura y escritura.
- Soluciones en alto nivel: Se tiene una capa de software por encima con un interfaz para la aplicaciones.

Cuando un proceso tiene que esperar a algun evento por X condición, entra en un estado de espera infinita, a esto lo denominamos **espera ocupada**. Podemos encontrar dos tipos de soluciones:
- Solución software: Usan operaciones simple de lectura y escritura de datos simples.
- Solución hardware (cerrojos): Esta basado en instrucciones máquinas específicas, con varios procesadores involucrado.


## Soluciones software
> Resumir 8
{.is-error}

Este tipo de soluciones surgen basado en las soluciones 

### Secciones críticas
De momento tenemos definido las secciones críticas como una zona de código donde se debe realizar todo de seguido sin que afecten terminos estructura ajena.

Realmente se divide en tres partes:
- Protocolo de entrada (PE): Unas instrucciones donde puede haber espera hasta entrar.
- Sección crítica (SC): Las instrucciones que deben ser ejecutada por un único proceso.
- Protocolo de salida (PS): Instrucciones que permiten indicar al resto de procesos que se ha acabado la parte critica.

Algunas de las restricciones que vamos a definir en estas secciones criticas son:
- Cada proceso debe ejecutar únicamente una sección critica.
- La SC es un único bloque contiguo de instrucción.
- Se va a ejecutar un bucle infinito donde está, la sección critica (inclusive el PE de antes y el PS de después), y el resto de sentencias.


> Mientras que un proceso este en una sección crítica nunca deberá finalizar o abortar (propiamente o externamente), no puede haber bucles infinitos ni ser bloqueado o suspendido indefinidamente de manera externa.
{.is-warning}

### Propiedad de exclusión mutua
Tenemos tres propiedades mínimas a cumplir:
1. Exclusión mutua: Para que un algoritmo de exclusión mutua se efectue, se debe evitar que dos procesos se estén ejecutando una sección critica a la vez.
2. Progreso: Si hay dos procesos en el PE, uno de ellos deberá entrar si o si. Que un proceso entre o no a la sección critica, debe depender de los procesos.
3. Espera limitada: Si hay un proceso que esta esperando una sección critica, eventualmente debe poder ser desbloqueado para hacerlo.

Además si se pueden cumplir dos propiedades, es mejor:
4. Equidad: No se perjudicar a un proceso de forma consistente.
5. Eficiencia: El algoritmo debe ser el más eficiente posible.

### Refinamiento sucesivo de Dijkstra
Partiendo de dos procesos, con un bucle infinito, ejecutando la sección critica y después el resto. Vamos mejorando este algoritmo hasta que cumpla las tres propiedades, llegando a un algoritmo de Dekker (Versión final correcta).

### Algoritmo de Dekker
Durante el refinamiento sucesivo anterior, se llego a un algoritmo donde uno de los algoritmos hace una pequeña espera, al otro. Esta espera lo hace mediante un condicional, donde se abre durante unos segundos la posibilidad de que el otro proceso ejecute su sección critica, pero después se cierra.

## Soluciones hardware con espera ocupada (cerrojos) para E.M.
Un candado lo podemos definir (a mala manera), como un bucle "infinito" hasta que la condición pase a false.
```C++
while (true){}
```

Los cerrojos son una solución hardware basada en esperas ocupadas, esta espera es un bucle que se ejecuta hasta que otro proceso finaliza su sección critica. 

Aunque esto puede ayudarnos a evitar bucles, debemos ser consciente de que debemos bloquear siempre después de que entre uno de los procesos al bucle, para que no haya problematica con la duplicación.

Es por ello que existe la instrucción "**TestAndSet**", instrucción máquina disponible en algunos procesadores, con las caracteristicas:
- Admitir como argumento la dirección de memoria una variable lógica.
- Invocar como función desde LLPP a alto nivel y ejecutar, la lecutra del cerrojo, ponerlo en tru y devolver el valor anterior del cerrojo.
- Durante su ejecución ninguna instrucción ejecutada por otro proceso puede leer ni escribir la variable lógica.

Un ejemplo sencillo en pseudocodigo es:
```
var sc_ocuapda : boolean := false;
begin
	while true do begin
  	while TestAndSet (sc_ocupada ) do begin end
    {critica}
    sc_ocupada :=false;
    {demas}
  end
end
```
### Desventaja de cerrojos
Debido a que hace espera ocupada, se produce un consumo de tiempo en CPU en procesos inutiles, mientra sque podrian hacer algo.

Otros de sus motivos es que al ser un booleano (true or false), existe la posibilidad de que un equipo malicioso establezca un estado erroneo provocando un bucle infinito.

### Uso
Sigue siendo uno de los metodos más usados, sobretodo en el kernel de equipos, ya que es muy optimo a lo que respecta a la pérdida de eficiencia. 

## Semaforos
Los semátoforos traen una serie de mejoras respecto a los candados como pueden ser:
- La espera bloqueada
- Resuelve problemas como exclusión mutua con esquemas sencillos.
- Usado para problemas de sincronización.

Un semaforo es una instancia de una estructura de datos que contiene:
- Conjunto de procesos bloqueados.
- Un valor natural, llamado valro de semáforo.

Ambos valores estaran en memoria compartida para que puedan usarse en cualquier lugar.

Dentro de sus operaciones tenemos:
- sem_wait, donde si el valor es 0, se bloquea el proceso, en caso contrario accede y decrementa el valor.
- sem_signal, incrementa el valor de la unidad.

Algunas de las reglas que debe cumplir los semaforos es que el número de lecturas ($#L$) debe ser menor al número de escritura ($#E$), es decir: $#L \leq #E$.

A su vez, podemos comporbar sobre la exclusión mutua lo siguiente:
- La sección crítica ($n_{sc}$), se ejecutará: $0\leq n_{sc} = n_w - n_s$.
- Debido a que el valor inicial de $v_0$ es 1, por invariante y las propiedades de los semáforos, el valor $v_t$ de sc_libre es entero no negativ cumpliendo: $0 \leq v_t = 1+n_s - n_w = 1- n_{sc}.
- Puesto que $ 0 \leq 1 - n_{sc}$, sabemos que $n_{sc}$ por lo tanto;

Se cumple que la exclusión mutua es $0 \leq n_{sc} \leq 1$.



Aunque con los semaforos tenemos una ventaja conrespecto a los cerrojos, también tiene limitaciones:
- Tiene problemas complejos de sincronzación, no se resuelven de forma facil.
- Similar a cerrojos problemas malintencionados puede provocar bloqueos indefinidos.
## Monitores
El uso de semáforos tiene una serie de limitaciones y es por ello que en 1974 se planteo un planteo el concepto de Monitor, como mecanismo de alto nivel donde se permite definir objetos abstractos compartidos.

Estos monitores nos dan:
- Datos: Como una colección de varibales encapsuladas, donde se representan un recurso compartido por varios procesos.
- Conjunto de procedimientos para poder manipular los datos.

Estos elementos le otorgan al programador:
- La garantía de cumplir con el acceso en exclusión mutua.
- Implementación de sincronización requerida.

### Propiedades del monitor
Un monitor al fin al cabo es un recurso compartido que se usa como un objeo al que se accede de forma concurrente. Este nos otorga:
- Acceso estructurado y encapsulación: Donde el usuario sólo puede acceder al recurso mediante las operaciones dadas, y el usuario ignorará las variables que representan el recurso y la implementación de las operaciones asociadas.
- Exclusión mutua en el acceso a los procedimientos: La exclusión mutua en el acceso a los procedimientos del monitor se garantiza por definición, y la implementación del monitor garantiza que no es posible que dos procesos estén ejecutando simultáneamente algún procedimiento del monitor.

```
monitor nombre_monitor;
	var
  export
  	nom_exp_1,
    nom_exp2,
  procedure nom_exp_1
  	var ;
   begin
   end
```
Como podemos ver la sintaxis consiste en:
- Declaración del monitor, donde peude tener variables permanentes como estado interno del monitor.
- Exportar monitores, donde se le dan los nombre a los procedimientos y el estado interno, pudiendo tener variables y parametros locales.
- Codigo de incialización, para ejecutar los monitores.


Dentro de las ventajas que puede incorporar los monitores sobre los semáforos, son las siguientes:
- Las variables están protegidas: Sólo pueden leerse o modificarse desde el código del monitor.
- La exclusión mutua esta garantizada: El programador no tiene que usar mecanismos explícitos de exlcusión mutua.
- Las operaciones de esperas bloqueadas y de señalización se programan exclusivamente dentro del monitor, permitiendo comprobar el código de forma más sencilla.

> Nos debemos quedar con la idea de que solo podemos usar el monitor mediante procedimientos exportados.
{.is-success}

### Funcionamiento de los montiroes
La comunicación monitor-mundo exterior, se realiza mediante los procedimientos exportados. En el caso de que un proceso requiera de un recurso del monitor, este hará una llamada y mientras el proceso está ejecutando algún procedimiento del monitor se dice que **el proceso está dentro del monitor**.
La exclusión mutua, se cumple ya que un proceso esta dentro de un monitor, ningún otro proceso podrá entrar en el monitor hasta que el primero no finalice.

Cuando sucede lo anterior, los procesos que se quedan esperando o bloqueados entran en una cola del monitor. En caso de que la cola esté vacia el monitor se queda libre y a la espera de algún proceso.

### Sincronización en monitores
Antes teniamos los *signal* y los *wait*, sin embargo ahora solo tenemos disponible sentencias de bloqueo y de activación, a la vez uqe los valores de las variables de los monitores.
# POR CORREGIR Y AÑADIR
Tenemos dos procesos denominados proceso señalador ( no es espera cola) y proceso señalado (espera la cola y es reactivo).

El proceso señalado:
- Se supone que hay codigo restante tras el wait y el signal
- Se ejecuta inmediatamente después de señalar.
- Uno de los dos puede inmediatamente ejecutar su codigo.
- Se denomina semántica de señales a la política que establece la forma concreta que resuelve el conflicto.
VOlvi hoy
El proceso señalador:
- Continua su ejecución tras el signal.

## Semantica Señalar y continuar (SC)
Se hace una espera infinita para ver cuando puede entrar y cuando no, similar a los monitores.

## Semantica señalar y salir (SS)
En este caso, un signal es similar a un return (no se ejecuta nada o se para), el señalador abandonará el monitor y si queda código posterior al signal no se ejecutará.

Esto implica una carga extra de trabajo, ya que debemos diseñarlo con el signal como código extra. 

## Semantica señalar y esperar (SE)
En este metodo, en vez de salir y morir. Lo que hace es volver a una cola donde esperara a su entrada para continuar con el código.

Si hay procesos que estuviera esperando a constantemente y ha podido entrar, y ha sido privado de nuevo, este proceso le volverá a tocar esperar siendo dificil que se vuelva a ejecutar al compleo.

## Semantica señalar y espera urgente (SU)9
Hay dos colas, una de aquellos que todavía no han entrado y aquellas que han sido expulsados de la cola previamente. 

Es uno de los mejores metodos que hay, pero implica que debemos tener una estructura extra de datos, donde estan las cola de urgencia extra. 

Toda la semantica permite resolver cualquier problema pero de mejor o pero manera, sin embargo por facilidad de uso, es posible que sea mas facil implementar uno que otros (como puede ser el de señalar y salir).

# Colas de conciión con prioridad
Hemos usado habitualmente las FIFO (First In First Out), sin embago también podemos usar las colas de prioridad para cuando saquemos elementos, podemos desbloquear mejor los elementos que deseemos.
Para hacer eso, a la hora de pasar el wait, le enviamos un parametros donde el que tenga menos valro tendra mayor prioridad.