---
title: HighSchool
description: Write Up de la máquina High School de la plataforma TryHackMe
published: true
date: 2025-05-09T15:26:40.455Z
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
