---
title: IPv4 y IPv6
description: 
published: true
date: 2025-01-14T13:15:46.960Z
tags: 
editor: markdown
dateCreated: 2025-01-14T13:15:08.538Z
---

# Tema 6 Parte 2

## IPv6

### Descripción
IPv6 es el sistema de direccionamiento de red que se introdujo para sustituir IPv4 debido al agotamiento de direcciones IPv4.

- En IPv6 desaparece la necesidad de realizar subredes y clases de direcciones IP públicas y privadas debido a su gran espacio de direcciones (128 bits frente a los 32 bits de IPv4).
- Aún estamos en una etapa de transición en la que IPv4 e IPv6 coexisten.

### Formas de transición entre IPv4 y IPv6
1. **Dual-Stack**: Ejecución simultánea de ambas pilas de protocolos.
2. **Tunelización**: Encapsula paquetes IPv6 en IPv4 para que puedan viajar a través de redes IPv4.
3. **Traducción (NAT64)**: Permite traducir paquetes entre IPv6 e IPv4.

### Características
- Direcciones de 128 bits representadas en hexadecimal, separadas por `:` (ejemplo: `XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX`).
- **Reglas para compactar direcciones**:
  - Supresión de ceros iniciales en cada grupo.
  - Representación de grupos contiguos de ceros con `::` (puede usarse solo una vez por dirección).
- **Longitud de prefijo**:
  - Indica la porción fija (red) y la parte variable (ID de interfaz).
  - Longitudes comunes: `/64`.

### Tipos de Direcciones
1. **Unicast**: Identifican a una única interfaz de red.
   - **Global**: Parecidas a las públicas de IPv4 (`2000::/3`).
   - **Link-local**: Generadas automáticamente en la red local (`fe80::/10`).
   - **Loopback**: Similares a `127.0.0.1` en IPv4 (`::1/128`).
   - **Sin especificar**: Utilizadas antes de configurar una dirección (`::/128`).
   - **Locales**: Similares a las privadas de IPv4 (`FC00::/7`).
2. **Multicast**: Permiten enviar paquetes a múltiples destinatarios simultáneamente (`FF00::/8`).
3. **Anycast**: Difusión por proximidad, asignada a varios dispositivos.

### Híbridos
- Direcciones IPv4 mapeadas en IPv6: `::FFFF:192.168.0.1`.
- Direcciones reservadas:
  - `::1/128`: Loopback.
  - `2001::/32`: Túnel Teredo.
  - `fe80::/10`: Link-local.

---

## TCP/IP: Introducción

La pila de protocolos TCP/IP satisface las necesidades de comunicación entre equipos. Se basa en una arquitectura modular que permite comunicaciones en red, incluyendo Internet.

- **Independencia del sistema operativo**: TCP/IP es compatible con cualquier OS.
- **Capa intermedia**: Conecta el equipo con la red de comunicaciones.
- **Historial**:
  - Unix y Linux adoptaron TCP/IP nativamente.
  - Windows lo integró posteriormente.

---

## Direccionamiento a Nivel de Enlace

### Dirección MAC
- **Descripción**:
  - Formada por 48 bits, representada en hexadecimal (6 grupos de 8 bits/1 byte).
  - Identifica de forma única cada tarjeta de red.
  - **Estructura**:
    - Los primeros 24 bits identifican al fabricante (OUI).
    - Los últimos 24 bits son únicos por dispositivo.
- **Broadcast**:
  - Dirección especial: `FF:FF:FF:FF:FF:FF`.

---

## Direccionamiento a Nivel de Red

### Dirección IP
- **Descripción**:
  - 32 bits, representada en notación decimal punteada (4 octetos).
  - Complementada por la máscara de red.
- **Máscara de Red**:
  - Determina qué parte de la dirección pertenece a la red y cuál al host.
- **Broadcast**:
  - Dirección con todos los bits del host a `1`.

### Clases de Redes
- **Clases A, B y C**:
  - Clase A: `0.0.0.0 - 127.255.255.255`.
  - Clase B: `128.0.0.0 - 191.255.255.255`.
  - Clase C: `192.0.0.0 - 223.255.255.255`.

### Excepciones
- `0.0.0.0`: Usada al inicio o para representar cualquier host.
- `127.0.0.1`: Loopback.
- `127.0.0.0 - 127.255.255.255`: Redes de loopback.

---

## Conceptos

### Tipos de Direcciones
1. **Dirección MAC**:
   - Grabada en la tarjeta de red.
2. **Máscara de Red**:
   - Define los bits de red y host.
3. **Dirección de Red**:
   - Primera IP reservada.
4. **Dirección de Broadcast**:
   - Última IP reservada.

### IPv4 Clases
- Clase A: Inicia con `0` (0-127), tiene `/8`.
- Clase B: Inicia con `10` (128-191), tiene `/16`.
- Clase C: Inicia con `110` (192-223), tiene `/24`.
