---
title: CheatSheet
description: 
published: true
date: 2024-11-11T18:10:56.653Z
tags: 
editor: markdown
dateCreated: 2024-11-11T18:09:52.405Z
---

# CheatSheet
En este apartado, podrá revisar comandos relevantes al uso de clonación o montaje de discos.
## Analisis de disco duro
Lo primero que deberemos saber es analizar los discos que tenemos disponibles, para saber cuál vamos a clonar. Para ello deberemos hacer
```bash
fdisk -l
```

Tras esto nos saldrá un listado de todos los discos leidos por el sistema. 

### Montaje de disco duro
Para poder saber que nombre fisico usa los disco duro en windows podremos usar el siguiente comando. 
```bash
wmic diskdrive list brief /format:list
```

Para el montaje del disco duro, una vez sepamos cuál es el nuestro, deberemos hacer uso del siguiente comando
```bash
fdisk /dev/sdX
g
n
p
1
(Enter)
(Enter)
w
```

Con el primer comando lo que hacemos es interactuar con el disco deseado y hacemos lo siguiente:
1. **g** -> Creamos una tabla de particiones GPT.
2. **n** -> Creamos una nueva partición.
3. **p** -> Decimos que la partición sea primaria.
4. **1** -> La posición que tomará la partición.
5. **(Enter)** -> Seleccionamos el principio del disco como minimo.
6. **(Enter)** -> Seleccionamos el final del disco como maximo.
7. **w** -> Guardar y salir.

Tras esto deberemos poner el siguiente comando:
```bash
mkfs.ext4 /dev/sdX1
```
Esto nos sirve para ponerle el sistema de archivo EXT4.

Por último deberemos montar el disco para poder usarlo. Para ello hacemos lo siguiente:
```bash
mount /dev/sdX1 /(carpeta)/(deseada)
```

Con todo esto, el disco ya estará montado.

## Clonado de disco
En caso de Linux, tenemos el comando DD, para hacer clonados de disco duro. Esto funciona del siguiente metodo:
```bash
dd if=/dev/sdX of=/(donde)/(queremos)/(clonar) bs=1M conv=sync,noerror status=progress
```
Esto hará una clonación de disco al completo. Hay que tener en cuenta que si ponemos de ruta **of** /dev/sdb, tenemos la clonación en un disco. Sin embargo si queremos un imagen del disco, no es necesario que sea en /dev/sdb, si no por ejemplo /mnt/disco.dd

### HASH
El hash se realiza para poder tener una prueba de que no ha sido modificado. Para ello haremos un:
```bash
sha512sum (Archivo)
```
> Si nuestro los datos a comprobar son menores a los que debemos examinar. (Hemos copiado un disco de 20GB a uno de 50GB), deberemos usar el siguiente comando.
{.is-info}

```bash
dd if=(Archivo) count= (Cantidad de sectores) bs= (Base del bloque) | sha512sum (Archivo)
```