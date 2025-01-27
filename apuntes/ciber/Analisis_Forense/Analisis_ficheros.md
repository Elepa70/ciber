---
title: Analisis de los sistema de Ficheros
description: 
published: true
date: 2025-01-27T12:00:27.718Z
tags: forense
editor: markdown
dateCreated: 2025-01-27T12:00:27.718Z
---

# Analisis forense en Windows | Sistema de Ficheros
En este apartado vamos a hacer un analisis de los sistemas de ficheros y también de los archivos que podemos recuperar y encontrar ahí.
## MBR (Master Boot Record)
Es una tecnología que se introdujo en 1983, con el IBM PC DOS 2.0, y se ha convertido en parte esencial de los equipos windows.

El Master Boot Record, es el primer sector físico de un almacen de datos, usado normalmente para arracnar ordenadores, siempre tiene una misma dirección que consiste en Cilindros, Cabeza y Sectores. Su tamaño es de 512 bytes.

Su estructura es la siguiente:
- Programa de inicio (Bootloader)
- Soporte de datos
- Tabla de particiones maestra
- MBR (Magic number, firma de arranque)

El programa de inciio, es un pequeño software que realiza la función de iniciar el sistema operativo, tras una serie de procedimientos.

La parte de soporte de datos, se usa para aquellos equipos que sean Windows 2000 y posteriores, para que puedan reconocer la tabla de particiones.

La tabla de particiones, es la zona donde se recogen los datos de las divisiones de los soportes de datos. Este apartado también recoge datos de tipo de soportes de datos (FAT 32).

Por último el magic number, es una cadena de 55 y AA en dos bytes. Sirve para verificar que es un sistema de arranque y si no se encuentra, se puede considerar que el proceso ha fallado.

El MBR requiere de un encendido por el BIOS al encender el PC. La BIOS es un software especial conocido como firmware (Firm: Firme), ubicado en la placa base de un equipo y incrustado en un cip especial. La BIOS solo comprueba que esté presente un bootloader.
Una vez encontrado el Bootloader, comienza una reacción en cadena y es el booloader de la partición, quien toma el control de la memoria principal.


En caso de que el MBR esté dañado, es posible repararlo automanticamente con herramienta de Windows o manualmente mediante un sistema de comandos de Windows con comandos como: bootrec/fixmbr, bootrec/fixboot.

Otras alternativas al MBR es el GPT, ya que el MBR tiene algunos problemas.
- Las particiones solo pueden llegar a ser de 2 TB
- Solo puede tener 4 particiones primarias
---

## GPT
La tabla de particiones GUID, consiste en un estándar para configurar las tablas de particiones, en los medios de almacenamiento, especialmente los discos duros. La GPT forma parte de la UEFI.

GPT se diferencia en MBR por:
- Particiones primarias ilimitadas.
- Protección mediante sumas de verificación CRC32.
- Copia de seguridad de la cabecera en el final.
- Compatibilidad con sistemas anteriores.
- Identificación clara de particiones y medios de almacenamiento.

La tabla de particiones GUID tiene una estructura en cuatro sectores:
- Registro de arranque principal protector: Está en el primer lugar, se menciona en el MBR protector, para garantizar la compatibilidad con estilos de particiones anteriores.
- Tabla de partición GUID primaria: Cabecera GPT y entradas de partión.
- Particiones: Cabeceras y entradas de cada partición.
- Tabla de partición GUID secundaria: Copia de la cabecera GPT y las entradas de partición, reflejando el mismo orden.

El motivo por el que se empieza a usar GPT más que MBR, es porque le esta comiendo terreno al ´ltimo. Las tablas de particiones GUID, son utilizadas por todos los sistemas informáticos modernos.

## Analisis forense de sistemas de archivos
Les recomiendo echarle un ojo a las siguientes prácticas para poder visualizar como realizar un analisis forense:
> Debido a la falta de tiempo, se subirán cuando se puedan disculpé las molestias. Si quiere mas información consulte el uso de DiskPart, DD, DC3dd 
{.is-danger}
