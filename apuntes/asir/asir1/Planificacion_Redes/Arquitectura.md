---
title: Arquitectura de redes
description: 
published: true
date: 2025-01-14T12:23:57.063Z
tags: iso, osi
editor: markdown
dateCreated: 2025-01-14T12:23:57.063Z
---

# TEMA 2: Arquitectura de redes


## Jerarquía de protocolos
La comunicación en redes utiliza una **jerarquía de protocolos** basada en capas. Esto facilita la resolución de problemas dividiéndolos en niveles independientes.

### Encapsulación
Las capas añaden información al mensaje al descender. En el receptor, cada capa procesa la parte que le corresponde y pasa el resto a la superior.

---

## Modelo OSI (Open Systems Interconnection)
Modelo de referencia para la comunicación entre sistemas. Sus capas son:

1. **Físico:** Identifica los dígitos binarios entre estaciones contiguas. Dispositivo: concentrador/Hub. Unidad: bit.
2. **Enlace:** Gestiona la comunicación entre nodos adyacentes. Funciones: corrección de errores, control de flujo y acceso al medio. Dispositivo: conmutador. Unidad: frame.
3. **Red:** Facilita la comunicación entre dispositivos no adyacentes. Funciones: enrutado y adaptación de paquetes. Dispositivo: router. Unidad: paquete.
4. **Transporte:** Garantiza transmisión fiable, sin errores ni duplicaciones. Dispositivo: firewall.
5. **Sesión:** Establece y controla las sesiones. Funciones: agrupamiento de datos y recuperación de interrupciones.
6. **Presentación:** Garantiza un formato común en la información. Funciones: encriptación y cambio de códigos.
7. **Aplicación:** Proporciona servicios de comunicación a los programas. Dispositivo: proxy.

### Limitaciones del modelo OSI
- Diseño desequilibrado.
- Repetición de funciones.
- Bajo rendimiento por encapsulación excesiva.

---

## Modelo TCP/IP
Modelo práctico con cuatro capas:

1. **Acceso al medio:** Gestiona el acceso a redes establecidas. Protocolos: LAN, RTC, PPP.
2. **Red:** Envía paquetes independientemente del destino. Protocolos: IP.
3. **Transporte:** Comunica origen y destino con control de errores. Protocolos: TCP, UDP, SCTP.
4. **Aplicación:** Combina capas superiores de OSI. Protocolos: HTTP, SSH, FTP.

---

## Arquitecturas y Tecnologías

### ATM (Asynchronous Transfer Mode)
Diseñada para redes de alta velocidad y baja tasa de errores. Transmite celdas de igual tamaño e incluye indicadores de calidad de servicio (QoS). Uso limitado por su alto costo.

### Red Microsoft
- **NetBIOS:** Diseñado para LAN, identifica equipos por nombre y difunde información.
- **NetBEUI:** Complemento de NetBIOS para redes LAN, sencillo y optimizado.

### Red telefónica conmutada (RTC)
Proporciona servicios básicos de comunicación.

### DSL (Digital Subscriber Line)
Usa filtros para separar voz y datos. Componentes principales:
- **DSLAM:** Discrimina señales y las redirige.
- **Backend ATM:** Transporta paquetes TCP/IP encapsulados en celdas ATM.

### FTTH (Fibra óptica)
Fibra hasta la casa del usuario. Variantes:
- **FTTN:** Fibra hasta el nodo (<400m de cobre).
- **FTTC:** Fibra hasta la acera (<300m de cobre).
- **FTTB:** Fibra hasta el edificio (<70m de cobre).
- **FTTH:** Fibra hasta la casa del usuario.

### WiMAX
Tecnología de acceso WAN con cobertura de hasta 50 km.

### Redes locales (IEEE 802)
- **Ethernet:** Topologías: Bus y Estrella. Protocolo para evitar colisiones.
- **Wi-Fi:** Modo Ad-hoc e infraestructura (SSID, canal, seguridad).
- **Li-Fi:** Usa luz para transmitir datos.
- **FDDI:** Alta velocidad y fiabilidad, basada en fibra óptica multimodo.
- **PLC:** Comunicación mediante cables eléctricos.
- **BPL:** Usa líneas de alta tensión para transmitir datos a largas distancias.

