---
title: Administracion de red
description: 
published: true
date: 2025-01-18T18:29:16.919Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:29:16.919Z
---

# Administracion de red

## Esquemas básicos de red
La elección y configuración de la **arquitectura de red** es fundamental. Puede ser desde lo más sencillo (un router y una LAN interna) hasta arquitecturas avanzadas con proxys, firewalls y redes perimetrales.

Elementos básicos:
- **Router**: Permite o deniega la comunicación entre dos o más redes.  
- **Red Interna**: Donde se sitúan los servidores y equipos de la empresa.  
- **Red perimetral o zona neutra**: Capa intermedia entre la red interna y el exterior (Internet), añadiendo seguridad adicional.

### Esquema de red básico
Consta de un router, una red interna y acceso a Internet. La protección depende en gran parte de la configuración del router/firewall.

### Esquema de red con una zona neutra
Se agrega una **DMZ** o red perimetral donde se alojan servicios expuestos a Internet (servidores web, de correo...). Aísla mejor la red interna.

---

## Integración de sistemas
En muchas empresas coexisten equipos Windows y GNU/Linux. Para que ambos convivan y se comuniquen, se establecen varios **niveles** de integración:

### Red
La **conectividad** de red es esencial. Suele incluir:
- **Enrutamiento**: Permitir a un equipo (o varios) actuar como router.  
- **Servidor DHCP**: Asigna configuración IP de forma automática.  
- **Servidor DNS**: Traduce nombres de host a direcciones IP.

### Datos
Los equipos comparten datos garantizando acceso y seguridad:
- **Samba**: Para compartir archivos entre Windows y Linux.  
- **NFS**: Principalmente en entornos Linux/Unix (Windows Server 2008 R2 en adelante también lo soporta).  
- **Sistemas NAS** (Network Attached Storage): Soluciones dedicadas al almacenamiento en red, a menudo con RAID.  
- **Sistemas de ficheros distribuidos**: Permiten compartir y gestionar datos a gran escala de forma transparente.

### Servicios
Los equipos acceden a servicios ofrecidos por otros:
- **Acceso remoto**:  
  - Modo terminal (Telnet, SSH).  
  - Modo gráfico (VNC, Escritorio Remoto).  
- **Directorio Activo** (Windows) o equivalentes (LDAP, etc.) para gestionar usuarios y dispositivos en dominios.  
- **Servidores de impresión**: Compartir impresoras.  
- **Actualización centralizada**: Gestión de parches y versiones de sistemas.  
- **Monitorización centralizada**: Supervisar recursos y servicios de la red en tiempo real.

