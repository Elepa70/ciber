---
title: Configuración de conmutadores y VLAN
description: 
published: true
date: 2025-01-14T12:41:05.187Z
tags: 
editor: markdown
dateCreated: 2025-01-14T12:41:05.187Z
---

# Tema 8: Configuración de Conmutadores y VLAN

## Configuración de un Conmutador
- Trabajan en el nivel de enlace, elaborando una tabla de direcciones MAC.
- **Protocolos para evitar bucles:**
  - **STP:** Protocolo de árbol de expansión.
  - **RSTP:** Versión rápida de STP.

## Luces de Conmutador
- **Apagado:** Sin conexión.
- **Verde/Amarillo:** Funcionamiento correcto.
- **Naranja:** Problemas de conexión o no full duplex.
- **Rojo:** Funcionamiento incorrecto.
- **Parpadeo:** Indica tráfico en la red.
- **Parpadeo frenético:** Posible bucle.

## VLAN (Redes Virtuales)
- Segmentan lógicamente una red LAN.
- **Ventajas:**
  - Aumentan la seguridad.
  - Mejoran el rendimiento.
  - Simplifican la administración.
- **Tipos:**
  - Por puerto.
  - Por dirección MAC.
  - Por dirección de red.
  - Por tipo de protocolo.

## Enlaces Troncales
- Canal virtual que conecta diferentes redes virtuales.
- Utilizan **etiquetado de mensajes** para distinguir las redes.

## Port Mirroring
- Puerto espejo utilizado para monitorizar el tráfico en otro puerto del conmutador.

