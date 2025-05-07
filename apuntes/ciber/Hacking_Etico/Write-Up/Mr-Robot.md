---
title: Mr-Robot1
description: Write Up de la máquina Mr-Robot1 de vulnub
published: true
date: 2025-05-07T18:52:22.559Z
tags: 
editor: markdown
dateCreated: 2025-05-06T15:55:20.165Z
---

# Mr. Robot 1
Bienvenido al write up de la máquina Mr.Robot de la plataforma de VulnHub.


## Reconocimiento 
Lo primero que debemos hacer es saber que IP va a tomar la máquina Mr.Robot, para ello ejecutamos el siguiente comando:
```bash
sudo netdiscover -i eth0 -r {IP}
```
![Descubrimiento de la IP](/imagenes/mrrobot_2.png)


Tras esto podemos observar que en mi caso toma la IP 10.0.2.16, por lo que le haremos el escaneo de puertos que estamos acostumbrado.
```
nmap -sT -Pn -sV 10.0.2.16
```
![Descubrimiento de puertos](/imagenes/mrrobot_1.png)


Vamos a intentar en la página del servidor para poder observar que hay cuando entramos. Si lo hacemos podemos observar, como si fuera el inicio de un equipo y nos habla mr.robot.


![Dentro de la página](/imagenes/mrrobot_3.png)


Dentro de estos comandos tenemos:
- Prepare: Video de la serie.
- fsociety: Video de la serie.
- inform: Nos envía a otro directorio donde podemos leer varias noticias.
- pregunta: Tenemos varias imágenes sobre paranoia.
- wakeup: Video relacionado con la serie.
- join: Parece que entramos en un chat con mr.robot, donde nos preguntará por un correo para mantener contacto.


Parece que no hay nada interesante así que usaremos dirb.


```
dirb http://10.0.2.16
```


![Dirb](/imagenes/mrrobot_4.png)


Podemos observar que hay una gran cantidad de recursos, donde los que más nos interesa puede ser robots.txt / robots, y después la sección de wp-admin ya que parece que estamos en un wordpress.


![Información de robots](/imagenes/mrrobot_5.png)


Cuando entramos en el robots, podemos ver que quiere filtrar dos lugares, fsocity.dic y key-1-of-3.txt.


Si entramos en http://{IP}/key-1-of-3.txt, tenemos la primera flag.


![Flag](/imagenes/mrrobot_6.png)


Sin embargo, si entramos en fsocity.dic, tenemos un diccionario que podríamos usar pero no sabemos todavía donde exactamente.


Guardaremos el archivo con un wget.


![Descargar la wordlist](/imagenes/mrrobot_7.png)


Ahora nos podremos dirigir a wp-admin, para intentar entrar en el wordpress.


![Intento](/imagenes/mrrobot_8.png)


Con una prueba fácil podemos ver que da error, así que podemos intentar usar Burp Suite para hacer una prueba para sacar el usuario.


Para ello deberemos cargar la petición de envío en el Burpsuite y enviarlo a Intruder, después cargamos el payload y probamos.


![Fuerza bruta](/imagenes/mrrobot_9.png)


Ahora deberemos probar a intentar localizar el usuario, esto lo hacemos ordenando por longitud de respuestas las peticiones enviadas.


![Descubrimiento](/imagenes/mrrobot_10.png)


Ahora haremos lo mismo con la contraseña.


> Imagen perdida.
{.is-danger}






Como podemos ver las credenciales son Elliot/ER28-0652, es decir, el protagonista y su número de identificación. Tras esto, vamos a intentar crear una shell reversa.


## Explotación
Vamos a crear una shell reversa, para ello vamos a usar Metasploit.
```
msfconsole
```
Y el exploit que vamos a usar se llama wp_admin_shell_upload, entonces vamos a hacer un 
```
search wp_admin_shell
use 0
```
Debemos modificar una serie de parámetros que son:
- set RHOST 10.0.2.16 - IP Victima
- set USERNAME Elliot
- set PASSWORD ER28-0652
- set wpcheck false


Y podremos ejecutar el comando


![Metasploit](/imagenes/mrrobot_12.png)


Tras lanzar el exploit (Comando exploit), podemos ver que ha funcionado y estamos dentro, podemos hacer un ls para probar.


![Exploit](/imagenes/mrrobot_13.png)


Nos dirigimos al directorio /home para mirar qué homes hay, y vemos el de robot, entramos y sacamos la flag


![Moverse por directorios](/imagenes/mrrobot_14.png)


Lamentablemente no tenemos permisos suficientes para poder abrir el archivo, pero tenemos otro fichero que tiene una contraseña en md5.


Esta contraseña la vamos a descifrar, con John The Ripper o una página web, lo que prefiramos.


![Desear](/imagenes/mrrobot_15.png)


Ahora establecemos una shell, con el comando shell y después la securizados. 


![Crear la shell](/imagenes/mrrobot_16.png)


Tras esto le hacemos la escalada de privilegios


![Cambiar a robot](/imagenes/mrrobot_17.png)


Tras esto podemos leer el archivo sin problema.


![Comprobar privilegios](/imagenes/mrrobot_18.png)




Vamos a intentar hacer un sudo -l para poder ver todo, sin embargo no es posible por lo que vamos a hacer lo siguiente:
```
find / -perm -4000 -type f 2>/dev/null
```
![Comprobar escalada](/imagenes/mrrobot_19.png)


Con esto podemos buscar qué comandos podemos ejecutar como root,  y podemos observar que tenemos a nmap como opción, donde en [GTFOBins](https://gtfobins.github.io/gtfobins/nmap/#suid) se puede utilizar.


Así que vamos a hacer
```
nmap --interactive
!sh
```


![Privilegios](/imagenes/mrrobot_20.png)


Ahora somos root y podemos hallar la última flag la podemos hallar en key-3-of-3.txt


![Última contraseña](/imagenes/mrrobot_21.png)



