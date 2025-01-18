---
title: Tareas de un administrador
description: 
published: true
date: 2025-01-18T18:28:08.135Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:28:08.135Z
---

# Administrador

## Tareas de un administrador
Un sistema informático requiere **planificación**, **configuración** y **atención continua** para garantizar fiabilidad, eficiencia y seguridad. Los **administradores informáticos** se encargan de mantener dichos sistemas; dependiendo del volumen de trabajo, pueden ser varios.

Las tareas principales de un administrador son:

- **Instalación y configuración de software**: Sistema operativo, servicios y aplicaciones necesarias.  
- **Instalación y configuración de hardware**: Dispositivos como impresoras, terminales, módems, cintas de backup, etc.  
- **Instalación y configuración de red**: Mantenimiento y ajustes de la infraestructura de red.  
- **Administración de usuarios**: Altas, bajas y modificación de privilegios.  
- **Formación y asesoramiento de los usuarios**: Directa o indirecta (documentación, manuales...).  
- **Inicio y apagado del sistema**: Procedimientos ordenados para evitar inconsistencias.  
- **Registro de los cambios de sistema**: Documentar cualquier actividad relevante.  
- **Seguridad del sistema**: Evitar intrusiones o interferencias entre usuarios.

---

## Hardware del servidor
En la actualidad, conocer los **componentes básicos** del hardware de un servidor es crucial para asegurar un rendimiento óptimo y una alta disponibilidad.

#### EL CPD (Centro de Procesamiento de Datos)
Es uno de los lugares más seguros e importantes de la empresa, donde se ubican todos los servidores. Suele tener:

- **Control de acceso**: Cerraduras seguras, medidas biométricas...  
- **Armarios**: Racks para servidores, routers y sistemas de alimentación.  
- **Sistemas de Alimentación**: Estabilizan la tensión y proporcionan respaldo (SAI, UPS).  
- **Ventilación**: Temperatura ideal entre 21ºC y 23ºC; a menudo con pasillos fríos y calientes.  
- **Cableado**: Ubicado en falso techo o suelo.  
- **Sistemas antiincendios**: Evitan la propagación del fuego.
### Sistemas de Racks
Un **rack** es una estantería o armario (típicamente 1,8 m de altura y 48 cm de ancho) para alojar servidores y equipos de red:

- Estandarizado en **U** (44,45 mm de altura por unidad).
- Ahorra espacio y mejora la organización y ventilación de los dispositivos.

### Servidores
Un **servidor** puede ser cualquier equipo, pero para un CPD se eligen **hardware específicos** diseñados para trabajar de forma continua (24/7). Existen distintos **formatos**:

- **Torre**: Similar a un ordenador de sobremesa; menos aconsejado para un CPD.  
- **Blade**: Integración máxima en un chasis con alta densidad de servidores. Muy utilizado en entornos de alto rendimiento.  
- **Rack**: Formato más común en CPD, optimizado para armarios de 19 pulgadas.

Otros aspectos importantes:
- **Fuentes de alimentación redundantes**: Se conectan a distintos suministros, garantizando alimentación ininterrumpida.  
- **Procesador**: Velocidad, número de núcleos y/o procesadores.  
- **RAM**: Capacidad, tipo y velocidad.  
- **Almacenamiento**: Velocidad de transferencia, tecnología de discos y capacidad total.

### Sistema RAID
Al elegir el subsistema de discos, se valora el uso de **RAID** (Redundant Array of Independent Disks), que agrupa varios discos como un único sistema de almacenamiento. Ejemplos:

- **RAID 0**: No hay tolerancia a fallos; la información se divide en varios discos (striping).  
- **RAID 1**: Tolerancia a fallos con duplicación (mirroring).  
- **RAID 0+1**: Primero aplica striping y después mirroring.  
- **RAID 5**: Incluye paridad para recuperar datos si falla un disco.

Es habitual utilizar un **disco spare** en espera para sustituir automáticamente un disco defectuoso. A menudo se recomienda separar datos de logs en diferentes arreglos de discos.

---

## Software del servidor
A la hora de elegir un **sistema operativo** para un servidor, la decisión suele estar entre **Unix/Linux** o **Windows**, según el entorno y las necesidades:

- **Linux**: Sistema abierto con una gran comunidad de soporte.  
- **Windows**: Producto comercial de Microsoft, con soporte corporativo y herramientas específicas.


