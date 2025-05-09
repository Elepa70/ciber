---
title: Mr-Robot1
description: Write Up de la máquina Mr-Robot1 de vulnub
published: true
date: 2025-05-09T16:53:50.571Z
tags: 
editor: markdown
dateCreated: 2025-05-06T15:55:20.165Z
---

# Mr Robot
Bienvenido al Write-Up de la máquina Mr.Robot, de TryHackMe. 

Primero de todo deberemos saber en que IP está la máquina que queremos atacar, para ello hacemos uso del siguiente comando:
```
sudo netdiscover -i eth0 -r 10.0.2.0/24
```
![Descubrimiento de la IP](/imagenes/mrrobot_2.png)

Como podemos observar, tiene la ip 16 ya que las tres primeras ips.
## Reconocimiento
Comenzamos la tarea con un reconocimientos de puertos para ello hacemos uso del comando:
```
nmap -sT -Pn -sV {IP}
```
Como podemos observar, tenemos los puertos 22, 80 y 443 abiertos, por lo que podemos hacer un Dirb para analizar los puertos importantes.
![Mapeo de puertos](/imagenes/mrrobot_1.png)

Cuando nos dirigimos al website, podemos ver como si Mr.Robot, nos estuviera hablando:
- prepare: Video relacionado con la serie.
- fsociety: Video relacionado con la serie.
- inform: Serie de imagenes relacionada con la serie.
- question: Serie de imagenes relacionadas con la serie.
- wakeup: Video relacionado con la serie.
- join: Chat supuestamente intereactivo con mr.robot.

![Imagen Index del equipo](/imagenes/mrrobot_3.png)
Ahora haremos uso de dirb con:
```
dirb http://{IP}
```
![uso del Dirb](/imagenes/mrrobot_4.png)

Como podemos observar dentro del analisis del dirb podemos encontrar, que tenemos robots y robots.txt disponibles para poder hacer una comprobación de aquellos sitios que no quiere que estén disponibles.


![Información del Txt](/imagenes/mrrobot_5.png)

Como podemos observar, tenemos un diccionario y después lo que parece ser una txt, entramos el el lugarl de la clave y obtendremos la primera clave.
![Primera clave](/imagenes/mrrobot_6.png)

Después nos descargaremos el diccionario que queremos mediante un
```
wget http://{IP}/fsocity.dic
```
![Diccionario](/imagenes/mrrobot_7.png)
Como podemos observar de vuelta en el dirb, estamos en un Wordpress, por lo que el acceso al menú será wp-admin.

Probamos a introducir una contraseña aleatoria para ver las posibles respuestas.
![Prueba de acceso al wordpress](/imagenes/mrrobot_8.png)

Gracias a la información del error y al diccionario que tenemos, podemos intentar realizar un ataque de fuerza bruta al login.
## Explotación
Lo primero que vamos a hacer será abrir nuestro burpsuite y captar la petición de envio de credenciales, después lo enviaremos a Intruder, y seleccionaremos con los caracteres especiales el log. Además debemos tener en cuenta que tenemos el diccionario añadido correctamente a la derecha en Payloads.
![Preparación de Burpsuite](/imagenes/mrrobot_9.png)

Tras darle a start, podemos observar como poco a poco va a comenzar a probar todas las credenciales que tenemos en nuestro diccionario.
![Exito en el test](/imagenes/mrrobot_10.png)

Como podemos observar si ordenamos por longitud de respuestas, tenemos que con el payload Elliot, hemos conseguido acertar, por lo que ya tenemos una pista de que podria ser.

Repetiriamos el proceso con el usuario y pero con el contraseña, y obtendriamos las credenciales que son: Elliot/ER28-0652.

Ahora que tenemos las credenciales ahora podemos intentar vulnerar el Wordpress con Metasploit, para ello hacemos 
```
msfconsole
```

Tras esto hacemos una buesqueda de shell en wordpress
```
search wp_admin_shell
```

Y debemos modificar los parametros con lo siguiente:
- RHOST: {IP}
- USERNAME: Elliot
- PASSWORD: ER28-0652
- wpcheck: false

![Metasploit](/imagenes/mrrobot_12.png)

Tras ejecutar el script, podemos ver como ha funcionado si hacemos un ls, podemos ver cosas
![Shell](/imagenes/mrrobot_13.png)

Ahora vamos a buscar la flag, que esta en el directorio home de un usuario robot.
![Busqueda de flag](/imagenes/mrrobot_14.png)

Lamentablemente no podemos leer el archivo, sin embargo tenemos la contraseña del usuario codificada en md5, 
![Contraseña](/imagenes/mrrobot_15.png)

Ahora que sabemos la contraseña: abcdefghijklmnopqrstuvwxyz, podemos intentar loguearnos como el usuario, sin embargo debemos actiar la shell con shell y securizar la shell
![Shell securizada](/imagenes/mrrobot_16.png)

```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

Hacemos Control + Z, y despues escribimos
```
stty raw -echo;fg
export TERM=xterm
```

Ahora podemos regirstramos como el usuario
![Su](/imagenes/mrrobot_17.png)

Ahora si podemos leer la flag que está en el mismo directorio.
![Flags](/imagenes/mrrobot_18.png)

Ahora vamos a intentar hacer una escalada de privilegios medidante:
```
sudo -l
find / -perm -4000 -type f 2>/dev/null
```

![Escalada de privilegios](/imagenes/mrrobot_19.png)

Podemos observar que podemos usar nmap como root, por lo que podemos crear una shell de la siguiente manera:
```
nmap --interactive
!sh
```
![Escalada](/imagenes/mrrobot_20.png)

Una vez tengamos la escalada hecha, podemos leer la última flag.
![Fin](/imagenes/mrrobot_21.png)
