---
title: Los artefactos - Windows
description: 
published: true
date: 2025-02-08T11:20:03.054Z
tags: windows
editor: markdown
dateCreated: 2025-02-08T11:20:03.054Z
---

# Los artefactos de Windows
En este punto, vamos a hablar de los artefactos de Windows. Son archivos que aportan una grandisima cantidad de información para los forenses. Aquí veremos donde encontrarlos y que hace cada uno.
## Prefetch
Windows, para hacer una mejora de rendimineto de carga del sistema, implemento una carpeta llamada Prefetch, donde el sistema operativo realiza un seguimiento del inicio y de los programas que se abren habitualmente.

Estos archivos tienen una extensión pf, y un ejeplo para poder analizarlo es con WinPrefech View de Nirsoft. Estos archivos lo encontramos en **%WINDIR%\prefetch**. Cuando un programa es ejecutado, se crea un prefech que continee información del programa, path de ruta, fecha y hora de creación y ultima apertura.

### SuperFetch
Consiste en la mejora de Prefetch, ya que en vez de un archivo pf, se crea directamente cache de ficheros. Esto está disponible en el registro de windows, con la ruta **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\sysmain**. Pero esta función no hace desaparecer a Prefech, ya que simplemente es una ayuda.
## Logs
Un log es un registro de eventos, que almacena datos sobre quien, que, cuando, donde y por que un evento ocurre.

Las rutas mas importantes de los logs son:
- %WINDIR%\setupact.log: Información de acciones de instalación.
- %WINDIR%\setuperr.log: Errores durante la instalación.
- %WINDIR%\WindowsUpdate.log: Información de transaccion y actualizaciones de sistema.
- %WINDIR%\Debut\mrt.log: Eliminación de software malintencionados de windows.
- %WINDIR%\security\logs\scepcomp.old: Componentes de windows no instalados.
- %WINDIR%\SoftwareDistribution\ReportingEvents.log: Relativo a actualizaciones.
- %WINDIR%\Logs\CBS\CBS.log: Ficheros pertenecientes a "Windows Reousrce Protection"
- %WINDIR%\setupapi.log: Información de unidades, services pack y hotfixes.
- %WINDIR%\INF\setupapi.dev.log: Drivers.
- %WINDIR%\INF\setupapi.app.log: Registro de instalación de aplicaciones.
- %WINDIR%\memory.dmp: Volcados de memoria.
- %WINDIR%\System32\config%WINDIR%\System32\winevt\Logs: Información logs disponible desde el visor de eventos.
## Ficheros de hibernación
Existe un fichero llamado hiberfil.sys, el cual contiene un tamaño similar o igual a la memoria RAM, que guarda el estado de la máquina en hibernación. 
## Volume Shadow Copy
Es una tecnología de Windows, que permite realizar backups automáticamente o manualmente. Estos backups nos permite hacer copias de seguridad de un volumen, y evitar el bloqueo de archvios. 
## Registro del sistema
Es la base de datos jerárquica de windows, donde se almacena toda la configuración y opciones del sistema operativo de Microsoft Windows. Contiene la configuración de componentes de bajo nivel del sistema operativo y también información de aplicaciones que perite la correcta funcion del mismo. 

El registro de información es mediante claves y valores. Haciendo similitud, las claves son contenedores de carpetas que pueden contener subclaves.
