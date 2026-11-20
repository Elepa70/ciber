---
title: Sistemas basados en paso de mensajes
description: 
published: true
date: 2026-11-20T18:16:38.932Z
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
## Paradigmas de interacción de procesos en programas distribuidos

## Mecanismos de alto nivel en sistemas distribuidos
