---
title: Elementos de redes
description: 
published: true
date: 2025-01-14T12:38:10.221Z
tags: 
editor: markdown
dateCreated: 2025-01-14T12:38:10.221Z
---

# Tema 5: Elementos de Redes

## Módem
- Los primeros módems utilizaban una red telefónica conmutada (RTC), transmitiendo señales analógicas de hasta 56 kbps.

## Tarjeta de Red
- Permite la conexión del dispositivo a una red.
- **Wake on Lan (WOL):** Permite arrancar un dispositivo recibiendo una señal desde la red. Hoy en día está integrado en la mayoría de dispositivos. Existe también **WoLAN** para redes inalámbricas.

## Tarjetas de Red Inalámbricas
- Trabajan en bandas de frecuencia de 2.4 y 5 GHz.
- Existen incompatibilidades entre los estándares por el uso de diferentes bandas de frecuencia.

## Otras Conexiones Inalámbricas
- **Bluetooth:** Limitado a distancias cortas. Ideal para conectar periféricos a portátiles.
- **NFC:** Comunicaciones por proximidad, con un radio de acción de 20 cm. Puede operar en modos Activo (bidireccional) y Pasivo (unidireccional).
- **RFID:** Identifica dispositivos mediante etiquetas y ondas de radio.

## Elementos de una Red

### HUB
- Trabaja en el nivel físico.
- Propaga la información recibida por un puerto a todos los demás, lo que puede generar colisiones.

### Punto de Acceso
- **Modos de operación:**
  - **Ad-hoc:** Los dispositivos se conectan directamente.
  - **Infraestructura:** Requiere un punto de acceso para gestionar las conexiones.
- **Configuración:**
  - **SSID:** Nombre de la red.
  - **Frecuencia:** 2.4 o 5 GHz.
  - **Seguridad:** Cifrado (WEP, WPA) o lista de dispositivos autorizados.

### Switch
- Trabaja en el nivel de enlace y segmenta la red, mejorando el rendimiento.
- Utiliza la **técnica de inundación** para aprender las direcciones MAC.

### Dominio de Colisión
- Segmento donde se propagan colisiones entre equipos.

### Dominio de Difusión
- Segmento donde se propagan los mensajes de difusión.

### Puente
- Une dos redes en el nivel de enlace.

### Router
- Conecta varias redes y elige la mejor ruta para enviar los datos.

### Gateway
- Conecta redes con arquitecturas diferentes.

### Firewall
- Filtra y redirige tráfico en el nivel de transporte.

### Proxy
- Trabaja en el nivel de aplicación, discriminando el tráfico según detalles específicos.

