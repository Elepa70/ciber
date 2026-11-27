---
title: Sistemas basados en paso de mensajes
description: 
published: true
date: 2026-11-27T18:30:52.664Z
tags: 
editor: markdown
dateCreated: 2026-11-13T17:54:15.792Z
---

# Sistemas basados en paso de mensajes
## Mecanismos básicos en sistemas basados en paso de mensajes
### Introducción
Hasta ahora hemos trabajado en un sistema multiprocesador, ahora vamos a usar los sitemas distribuidos (conjunto de procesos que no comparten memoria pero envian datos en una red), literalmente Torrent o internet.

Lo que se ha añadido con respecto a los temas anteriores, es que se han añadido una serie de herramientas nuevas para poder enviar y recibir la información. Esta información ( o mensajes) oculta el hardware ya que no tiene que ver y su portabilidad se puede implementar segun la arquitectura usada.
### Vista lógica arquitectura y modelo de ejecución
Los procesos se comunican mediante envío y recepción de mensajes.
El código lo podemos diseñar de una u otra manera según unos estilos que queramos seguir:
- SPMD (Single Program Multiple Data): Es un estilo muy simple donde depende de una variable se hace uno u otro, actualmente en desuso.
- MPMD (Multiple Program Multiple Data): Distintos procesos ejecutan el mismo o diferentes programas segun los ficheros ejecutables.
### Primitivas básicas de paso de mensajes
El paso de un mensaje entre dos procesos constituye en una transferencia de una secuencia finita de bytes:
- Se leen variables d eun proceso emisor
- Se establece una red de envio de inforamción
- Se establece una variable de proceso receptor
- Existe una sincronziación para poder estar esperando respuesta y para poder estar enviando.

En el apartado de sincronización, vamos a tener:
- send (variable_origen, idenfiticador_destino)
- receive (variable_destino, identificador_proceso_origen)


Para definir quienes hacen cada trabajo:
- Directo estático: Se usará un identificador para todos los procesos.
- Indirecto: Los mensajes se almacenarán en intermedios y seran accesible por los procesos. Estos canales o buzones que almacenan la información puede ser canales (uno a uno, cada emisor va a cada receptor), generales (Todos los procesos lo envian al mismo y lo reciben al mismo) y por puertos (muchos emisores y un unico receptor).

Los identificadores de proceso suelen ser valores enteros, se pueden gestionar estaticamente o dinamicamente.


Cuando se manda un mensaje, el emisor hace una solicitud envio de mensaje, tras esto se va a copiar la variable del local al canal de comunicación que puede tardar más o menos de cuanto pese el mensaje. 

Por otro lado cuando queremos hacer una recepción, lo que hace es solicitar una solicitud de recepción, tras esto se hace una solicitud de emparejamiento  y posteriormente comienz ala escritura de la variable.

> Es necesario primero que antes de descargar debe haberse subir.
{.is-info}

Debemos tene ren cuenta que existe una seguridad en las operaicones del paso de mensajes, estas operaciones es porque se ha efectuado cosas no seguras, que puede ser:
- Operación de envío-recepción segura: Se garantiza el valor de var_orig coinciad con el valor de var_dest. Se devuelve un control para garnatizar seguridad.
- Operación de envío-recepción insegura: Se peude hacer envio inseguro (Cuando se puede modificar el var_orig) o recepción insegura (cuando se puede modificar var_dest).

### Operación síncrona cita
Se exige una cita entre emisor y receptor, esta operación "s_send" no devuelve el control hasta que se alcance el "receive" correspondiente del receptor. 

Esto puede suponer un problema de espera ociosa o interbloqueo si se gestiona de manera erronea.

### Asincrono
Se inicia el envío de los datos designados y espera bloqueados hasta que hayan terminado de copiarse todos los datos de la variabel en un lugar seguro, tras eso ya interactua la recepción síncrona.

Para est etipo de operaciones, lo que se hace es usar i_send y i_receive. En este caso no se espera ni si quiera al emparejamiento, directamente envia la información. Aunque sea asincrono también existe el wait_send y wait_recv, donde se bloquea los cambios que se puedan hacer en el SPM.
### Espera selectiva
Las esperas selectivas es una operación que permite esperar bloqueada de múltiples emisores. Usan palabras reservadas select y when.

Estas palabras tienen casi la mismas funciones que un switch y case, ya que se busca hacer una acción según lo que llegue.
```
select
	when (condicion a cumplir) receive(variable,proceso) do
  	//sentencias...
  when (condicion a cumplir) receive(variable,proceso) do
  	//sentencias...
  ...
end
```
Esto siempre va a funcionar cuando:
- La condición se cumple.
- Se ha recivido la orden por parte del proceso concreto.
En caso de que esto no se cumpla, se hace un guarda que se ejecutará cuando corresponda.

Es posible que necesitemos hacer muchas esperas para cada valor, para ello podemos usar el "for" a modo de utilidad para esperar.
```
for indice := inicial to final
	when condition receive(mensaje,proceso) do
  	sentencias
```
Esto lo que hace es que no tengamos que crear los when que necesitemos, si no una especie de "vector" de whens para poder hacer la espera.
## Paradigmas de interacción de procesos en programas distribuidos
### Introducción
El paradigma de interacción define un esquema de interacción entre procesos y estructura de control. Unos pocos paradigmas de interacción se utilizan repetidamente para desarrollar muchos programas distribuidos.
### Maestro-Esclavo
Es una tecnología en desuso, pero ideal para aprender.

Definimos el problema:
- Proceso maestro: Tiene un "problema" que es troceado en varios subtareas.
- Proceso esclavo: Ejecuta y resuelve esta subtarea, y se la devuelve al maestro una vez finalizado.


### Iteración síncrona
Se diseño para resolver problemas concretos, son problemas en los cuales se deben resolver de forma iterativa una serie de cálculo en los mismo cálculos.

> Basicamente los calculos que acabo de hacer, se vuelven a usar
{.is-info}

### Encauzamiento (pipelining)
Consiste en el paradigma más sencillo, en el cual tenemos un problema y lo dividimos ne varias subtareas, estos problemas se va en correlación y se va resolviendo en cauce.
## Mecanismos de alto nivel en sistemas distribuidos
### Introducción
Todo lo que hemos visto, sigue tiene un nivel bajo de abstracción. Usualmente para trabajar se necesita otros metodos.
Vamos a ver dos mecanismos de mayor nivel:
- Llamada a procedimiento remoto (RPC)
- Invocación remota de métodos (RMI)

Estos métodos estan basados en procedimientos y funciones, por un proceso llamador.

En caso del modelo de invocación remota (RPC), esta llamada la realiza otra máquina y este se quedará bloqueado hasta que se le permita seguir ejecutando.
### El paradigma Cliente-Servidor
Es el paradigma más frecuente en programación distribuida, hay una relación asimétrica netre dos procesos:
- Servidor: Gestiona un recurso y ofrece un servicio a otros procesos, que seran los clientes.
- Cliente: Necesita el servicio y envía un mensaje de petición al servidor.

Algunos problemas que plantea ese tipo de solución, es que el Servidor falla, el cliente se queda esperando. Luego si un cliente no incova el receive y el servidor realiza el send el servidor se quedará bloqueado.

Para poder solucionarlo, hay dos formas. El par (recepción de petición y envío de respuesta) se debe considerar como uan única operación de comunicación. El mecanismo de llamada a procedimiento remoto (RPC)
### Llamada a Procedimiento (RPC)
Debemos tener en cuenta una serie de cosas:
- Llamada a procedimiento remoto (Remote Procedure Call): Este tipo de mecanismo de comunicación entre procesos que sigue el esquema cliente-servidor.
- Diferencial ppal respecto a una llamada a procedimiento lcoal: El programa que invoca el procedimiento (cliente) y el procedimiento invocado (proceso servidor) peuden pertenecer a máquinas diferentes del sistema.

La interacción en este esquema es mediante un representante o delegado, que es un procedimiento lcoal que gestiona la comunicación en el lado del cliente. Los proceoss cliente y servidor no se comunican directamente, sino a través de representantes.

Las llamadas RPC funciona con una serie de pasos:
1. En el nodo cliente se invoca un procedimiento remoto como si se tratara de una llamada a procedimiento local.
2. El representante del cliente empaqueta todos los datos de la llamada, usando determinado formato para formar el cuerpo del mensaje.
3. El representante del cliente envía el mensaje con la petición de servicio al nodo.
4. El programa del cliente se quedará bloqueado esperando la respuesta.
5. En el nodo servidor, el sistema operativo desbloquea al proceso servidor para que se haga cargo de la petición.
6. El representante del servidor desempaqueta los datos del mensaje de petición y ejecuta una llamada al procedimiento.
7. Cuando finaliza la llamada el representante del servidor empaqueta los resultados en un mensaje y loe nvía.
8. El sistema operativo del nodo cliente desbloquea al proceso que hizo la llamada.
9. El representante del cliente desempaqueta el mensaje y pasa los resultados al invocador del procedimiento.

Representación de los datos:
- En un sistema distribuido, los nodos peuden tener diferente hardware y/o sistemas operativos, utilizando diferentes formatos para representar los datos.
- En estos casos los mensajes se envían usando una representación intermedia.

Paso de parámetros:
- Por valor en este caso basta con enviar al representante del servidor.
- Por referencia el bojeto referenciado debe enviarse desde el proceso cliente hacia el servidor.
### Java Remote Method Invocation (RMI)
Para poder invocar el método de un objeto, hay que dar una referencia del objeto.
Esta interfaz del objeto define sus métodos, argumentos, tipos de valores devueltos y expceciones.

La invocación de métodos remotos:
- En un entorno distribuido, un objeto podria invocar métodos de un objeto.
- Para invocar métodos de un objeto remoto, el proceso llamador debe de proporcionar el nombre del método y los parametros.

TEnemos que tener en cuenta a su vez:
- Interfaz remota: Especifica los métodos del objeto remoto que están accesibles para los demás objetos.
- Remote Method Invocation: Acción de invocar un método de la interfaz remota de un objeto remoto. La invocación de un método en una interfaz remota sigue la misma sintaxis.

El cliente y el servidor deben conocer ambos la interfaz de la clase del objeto remoto:
- En el cliente: El procesol llamador usa un objeto llamado stub, que es responsable de implementar la comunicación con el servidor.
- En el servidor: Se utiliza un objeto llamado skeleton, que es responsable de esperar la llamada, recibir los parámetros, invocar la implmentación del método, obtener los resultados y enviarlos de vuelta.

Los stubs usan la definición de interfaz remota.
Los objetos remotos se residen en el nodo servidor y son gestionados por el mismo. Los procesos clientes manejan referencias remotas.
> Por rellenar
{.is-danger}

### Servicios Web
En la actualidad, se utiliza para los servicios web, que tienen de caracteristicas:
- Usan protocolos HTTP o HTTPS sobre TCP/IP.
- Se usan codificación de datos basados en XML o JSON
- Se usan protocolos complejos, pero usualmente el sencillo REST.

Las peticiones de recurso o documentos pueden hacerse desde:
- Una aplicación cualquiera ejecutándose en el cliente, aunque en particular los más frecuente, es usar un programa Javascript.
Las peticiones pueden ser:
- Síncrona: El proceso cliente espera bloqueado la llegada de las respuestas. Se considera no aceptable en aplicaciones web interactivas.
- Asíncronas: El proceso cliente envía la petición y continúa. Cuando se recibe la respuesta, se ejecuta una función designada por el cliente al hacer la petición.