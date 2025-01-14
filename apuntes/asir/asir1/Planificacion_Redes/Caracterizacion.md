---
title: Caracterización de redes
description: 
published: true
date: 2025-01-14T12:22:49.863Z
tags: redes
editor: markdown
dateCreated: 2025-01-14T12:22:49.863Z
---

# TEMA 1: Caracterización de redes

## Tipos de Transmisión
Existen varios tipos de transmisión que se diferencian por su forma de comunicarse:

### Según la sincronía
- **Sincronía:** Se usan bits para indicar el inicio del bloque, requiere mejor sincronía entre emisor y receptor.
- **Asíncrona:** Utiliza 1 bit al principio y 2 al final de cada bloque. Permite tiempos variables y utiliza una señal para preparar al receptor.

### Según el medio de transmisión
- **Serie:** Todas las señales se transmiten en una sola línea de datos secuencial. Ideal para largas distancias.
- **Paralelo:** Información transmitida por varias líneas, requiere más canales y es adecuado para distancias cortas.

### Según la explotación del circuito de datos
- **Simplex:** Comunicación unidireccional (ej.: radio).
- **Semi-Duplex:** Comunicación bidireccional, pero no simultánea (ej.: walkie-talkie).
- **Dúplex:** Comunicación bidireccional y simultánea (ej.: teléfono).

---

## Tipos de Redes
Las redes se clasifican según su topología:

### Según la topología
- **Malla:** Enlace punto a punto entre dispositivos. Ventajas: robustez, seguridad y rendimiento.
- **Estrella:** Dispositivos conectados a un concentrador. Ventajas: menor complejidad y fácil reconfiguración.
- **Árbol:** Similar a la estrella, pero con concentradores secundarios. Mejora la potencia y distancia.
- **Bus:** Topología multipunto con un cable troncal. Ventaja: facilidad de instalación.
- **Anillo:** Dispositivos conectados en un circuito cerrado. Desventaja: falla si un enlace se interrumpe.

### Según la localización geográfica
- **LAN:** Redes de área local, en un ámbito reducido como un edificio.
- **WAN:** Redes de área amplia, cubren grandes distancias (ej.: ciudades).
- **PAN:** Redes de área personal (ej.: puestos de trabajo).
- **Red de campus:** Varias LAN que cubren una zona geográfica delimitada.
- **MAN:** Redes de área metropolitana, incluyen varias redes de campus.


