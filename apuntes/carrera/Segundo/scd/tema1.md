---
title: Introducción
description: 
published: true
date: 2026-09-25T17:10:57.091Z
tags: 
editor: markdown
dateCreated: 2026-09-18T16:51:55.223Z
---

# Introducción
## Conceptos básicos y motivación
### Conceptos básicos relacionados con la concurrencia

Aquí vamos a describir una serie de terminos:
- Programa secuencial: Consiste en una delcaración de datos + conjutno de instrucciones que se ejecutan de forma seguida o secuencial.
- Programa concurrentes: Conjuntos de programa secuencial que se ejecutan en paralelo cada uno resolviendo lo suyo.
- Programación COncurrente: Conjutno de estandares o anotación para hacer una serie de procesos que queremos resolver.  

Vamos a tener tres grandes ramas para la programación
- Programación paralela: Busca acelerar la resolución de problemas concretos mediante la capacidad del hardware.
- Programación distribuida: Busca que varios equipos trabajen a la vez para cumplri con el programa.
- Programación de tiempo real: Se suele trabajar en un plazo de tiempo de forma estrictas, y si el programa no se ejecuta en X tiempo, el programa falla.




### Motivación de la Programación Concurrente
Este tipo de programación (Concurrente) es más estricta que el secuencial, pero es mas beneficioso por
- En sistemas con un solo procesador, se peude obtener la ventaja de realizar varias tareas con el control de E/S. 
- En multiprocesador, nos permite distribuir la tarea en varios procesadores para reducir el tiempo de ejecución.

A su vez tiene una mejora de calidad debido a que es más facil diseñar un sistema, considerando las partes del sistema un procesos.

Además sin este tipo de programación, no es posible hacer uso de:
- Cálculo intensivo múltiplo de CPU
- Cálculo intensivo en GPU
- Sistemas distribuidos de cálculo.


Debido a estos motivos se ha convertido en una herramienta esencial para el desarrollo de varias cosas como: Videojuegos, IA, animación, simulación y mucho más. Internet es uno de estos sitios donde este tipo de programación ha influido de forma masiva, ya que un equipo de forma asincrona y a la vez realiza un montón de peticiones. 
## Modelo abstracto y consideraciones sobre el hardware
### Consideraciones sobre el hardware
Antes es necesario de continuar hablar de hardware, ya que la concurrencia viene fuertemente vinculado a los sistemas concurrentes (Como funciona, no lo que es).

Es por ello que debemos saber que la CPU debe estar comunicada con otros nucleos de CPU y esto puede ser de distintas maneras:
- Monoprocesador: Aquí solo tenemos un único nucleo de CPU, donde hablara con la memoria de forma directa.
- Multiprocesador de memoria compartida: En este caso tenemos un monton de CPU conectadas a una unica memoria, con la posible desventaja de que se debe compartir el espacio.
- Multiprocesador distribuido: La CPU va a estar conectada cada una a una memoria, aunque nos puede generar una serie de probelmas como la hora de gestionar que zona de conexión va a cada CPU. En este sistema es posible que encontremos monoprocesadores o multiprocesador con memoria compartida.
### Modelo abstracto de un proceso secuencial
Un programa secuencial es un conjunto de datos y una lista secuencial de instrucciones, siendo importante la palabra secuencial, ya que el orden es lo que define el propio programa.

Algunas de las palabras claves son:
- Sentencia: Es un trozo de codigo donde se modifica de alguna menra alguna de las variables. Para ello, es necesario que tenga acceso a la memoria.
- Estado: Consiste en los valores de los programas o las variables que conocemos de C++.
- PRoceso secuencial: Es una ejecución de todas las instrucción del programa, partiendo de un estado inicial hasta un estado final.

El procesador cuando ejecuta la sentencia, necesita leer o escribir la variable, que iremos considerando **tipos primitivos** (int, bool...), conforme más largo sea, más acceso seran necesarios (string). Estos accesos los controla el controlador de memoria, y este es quien se encarga de hacer el orden, esto implica que cuando hagamos ejecuciones de instriccuiones de programa, todos los procesos se van a venir del mismo orden.

Es habitual que las sentencia necesiten 2 o más accesos a la memoria. 

Denominamos a $V(S)$ como las **variables accedidas por una sentencia $S$**.

Todo los elementos de estados desde el inicio hasta el fin lo vamos a llamar **historia** o **traza**. 

Cuando una sentencia recoge una variable, esta variable debe ser guardada en algún lado llamado **registros**. Definimos registros (r0), son variables especiales que contienen la información de otras variables.
> Usualmente este tipo de registros no los vamos a necesitar, tanto como los accesos.
{.is-info}

Para describir una traza vamos a usar una tabla con Sentencia ejecutada y estados.

> Podemos resumir esto como: Un programa secuencial es una lista finita de procesos donde se acceden a las variables, partiendo desde un estado inicial hasta un estado final.
{.is-success}


### Modelo abstracto de ejecución concurrente
Un programa concurrente lo vamos a definir como, es un texto fuente donde hay variables y sentencias, donde cada programa se ejecuta concurrentemente, con variables compartidas ya sean locales o accesibles con registros
> Revisar
{.is-warning}


Una de las caracteristicas de este tipo de programa es que no finaliza hasta que todos los procesos no hayan acabado, y un programa peude estar embebido uno dentro de otro (Tenemos un sistema que efectua unas cuentas y debe intererar en un vector de 1M de elementos, y para hacer esto reparte el calculo de procesos entre las distintas CPU).

Estos procesos puede definir distintos variables propias definidas variables locales, donde cada uno de los procesos posee sus variables y no es posible acceder desde fuera del proceso, similar pasa con el registro, cada uno son independeinte de los demás.

Debido a que ahora tenemos sentencias ejecutadas a la vez o concurrentemente, ahora debemos darle una nueva notación para poder diferenciar.
- Sentencias ejecutadas de forma secuencial: $S_{A};S_{B}$.
- Sentencias ejecutadas de forma concurrente:$S_{A}||S_{B}$.

Se pueden concatenar tantas sentencias como deseemos, sin embargo hay que tener en cuenta que $S_{A};S_{B}$ no es igual que $S_{B};S_{A}$.

Los programas concurrentes **SIEMPRE** va a cumplir la propiedad de Consistencia Secuencial Estricta:
- Cada uno de los programas concurrentes,si  están definido como programas secuenciales. Esto implica que el programa sencuencial 2º de uno de los dos programas concurrentes, JAMAS podra acceder antes que el primer programa secuencial del mismo programa concurrente.
- Toda ejecución se puede definir como una traza, como una secuencia de accesos.

Al tener accesos, se modifica el estado inicial del programa se modifica también, y al tener estados vamos a tener las trazas que nos habilita ver como ha evolucionado el programa. Sin embargo las trazas ENTRE ejecuciones, pueden variar. 


### Setencias atómicas
Vamos a definir uno de los conceptos importantes
Las sentencias atómicas, es una sentencia que desde que comienza hasta que termina, no permite ningun acceso, por lo tanto tampoco produce de estado intermedio. 

Cualquier sentencia que tenga solo un acceso, ya sea escritura o lectura es atómica.
> Tecnicamente si es posible que cree otro acceso, siempre y cuando sea por el mismo, no permite que otro acceso pueda hacerlo.
{.is-info}
Alguna de las sentencias atomicas pueden ser:
- Dar un valor a una variable.
- Cargar una variable local en una variable compartida.
- Aquellas que tienen como mucho un acceso a 1 variable compartida.

Podemos encontrarnos una serie de sentencias que se pueden saltar este termino.

#### Sentencias no atómicas
Son aquellas donde se produce más de un estado intermedio o acceden a mas de una varible compartida.


Aunque existan sentencias atomicas, no podemos garantizar que estas sean seguras, ya que es posible "Machacar" estas variables compartidas durante el proceso, provocando un cambio de resultado inesperado. Esto se puede llamar Solapamiento de instrucciones atómicas, ya que intercambiamos procesos distintos atómicos dando valores y resultados inesperados.


Cuando interfoliaciamos procesos, es posible calcular la cnatidad de números posibles que pueden haber, para ello vamos a poner:
$P_1$ ejecuta $n_1$ instrucciones atómicas y $P_2$ ejecuta $n_2$, para poder calcularo hacemos $\frac((n_1+n_2)!)(n_1!n_2!)$.


La abstracción la vamos a aplicar en esta asignatura, ya que esta asignatura depende de EC en su parte máquina, vamos a ignorar algunos detalles para no repetir temario y centrarnos en las partes características relevantes y vamos a simplicar lo máximo psoible.

Esto lo vemos por ejemplo con los progresos finitos, ya que sabemos que va a tardar un tiempo finito, aunque no sepamos si es mucho o poco.  Al dar por cierta la hipotesis de progreso finito, debemos dar también por cierto las de punto de vista global (durante una jeecución siempre va a estar listo para entrar después) y la de vista local (una sentencia siempre se ejecuta, nunca se va a quedar congelado).


#### Cobegin-Coend
Estas palabras las usamos para indicar que aquello que este entre cobegin y coend, se van a ejecutar en parapelelo en vez de manera secuencial.
## Exclusión mutua y sincronización
Un programa concurrente se peude ver como una secuencia de accesos, al fin al cabo un programa concurrente es un programa que se va haciendo al unisono (muchas tareas a la vez), existe la posibilidad de que alguna sea erronea, es por ello que los se necesita que una comunicación para que sea concurrente, ya que si no se denominaría paralelos.


### Concepto de exclusión mutua

### Condición de sincronización
## Propiedades