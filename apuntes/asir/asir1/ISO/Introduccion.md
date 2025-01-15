---
title: Caracterización de sistemas operativos
description: 
published: true
date: 2025-01-15T16:59:10.688Z
tags: introduccion, iso
editor: markdown
dateCreated: 2025-01-14T12:11:40.198Z
---

# Caracterización de sistemas operativos

## El sistema informático
La palabra **informática** proviene de "información" y "automática". Un **ordenador** es una máquina informática con gran capacidad para tratar información.

Un sistema informático está compuesto por tres elementos:
1. **Componente físico:** Hardware.
2. **Componente lógico:** Software de base.
3. **Componente humano:** Usuarios y técnicos.

## Clasificación de los sistemas informáticos
### Por su uso:
- **De uso general:** Ejecutan varios tipos de aplicaciones.
- **De uso específico:** Diseñados para uno o pocos programas.

### Por sus prestaciones:
- **Superordenadores:** Gran capacidad de cálculos.
- **Computadores centrales (mainframes).**
- **Sistemas medios.**
- **Estaciones de trabajo.**
- **Microordenadores.**

---

## El sistema operativo
Un **sistema operativo** es un conjunto de programas que actúan como intermediarios entre el usuario y el hardware, gestionando y optimizando los recursos del sistema.

### POST
El **POST** (Power-On Self-Test) es el primer diagnóstico que se ejecuta al encender el ordenador, verificando periféricos y parámetros.

### Funciones del sistema operativo:
1. Control de ejecución de programas.
2. Administración de periféricos.
3. Gestión de permisos y usuarios.
4. Control de concurrencia.
5. Control de errores.
6. Administración de memoria.
7. Control de seguridad.

---

## Elementos y estructura de un sistema operativo
El sistema operativo se divide en 5 niveles, conectados entre sí:

1. **Gestión del procesador:**
   - Incluye el **Kernel**, que gestiona la CPU.
   - Funciones principales:
     - Comunicación y conmutación de procesos.
     - Control de interrupciones.
     - Manejo de errores.

2. **Gestión de memoria:**
   - Asigna y libera memoria para los procesos.

3. **Gestión de procesos:**
   - Creación y destrucción de procesos.
   - Intercambio de mensajes y arranque.

4. **Gestión de dispositivos:**
   - Maneja entradas y salidas.

5. **Gestión de información:**
   - Administra nombres lógicos para acceder a los recursos.

**Características de los niveles:**
- Realizan un subconjunto de funciones.
- Usan las funciones del nivel inferior.
- Interfaz definida para modificar un nivel sin afectar a otros.

---

## Utilización del sistema operativo
1. **Modo comando:** Interacción mediante línea de comandos.
2. **Modo gráfico:** Uso de ventanas, íconos y ratón.

---

## Gestión de procesos
### Multiprogramación
- En sistemas monoprocesadores solo se ejecuta un proceso a la vez.
- Varios procesos se mantienen en memoria para optimizar el uso de la CPU.

### Planificación de la CPU
Decisiones:
- **Expropiativas:**
  - Cuando un proceso pasa de ejecución a listo.
  - Cuando pasa de espera a listo.
- **No expropiativas:**
  - Cuando un proceso termina.

---

## Administración de memoria
### Jerarquía de memoria
1. **Registros de CPU.**
2. **Memoria caché.**
3. **Memoria RAM.**
4. **Memoria externa:** Virtual, disco duro, etc.

- **Velocidad:** Mayor en niveles superiores.
- **Capacidad:** Menor en niveles superiores.

### Funciones del administrador de memoria:
- Control de memoria utilizada y libre.
- Asignación de memoria a procesos.
- Intercambio entre memoria y disco.

### Tipos de sistemas:
1. **Monoprogramados:** Memoria dividida entre usuario y sistema operativo.
2. **Multiprogramados:**
   - **Particiones:**
     - Fijas o variables.
   - **Paginación:** Divide memoria en bloques de igual tamaño.
   - **Segmentación:** Direcciones lógicas en segmentos.
   - **Segmentación paginada:** Combina ambos conceptos.

---

## Clasificación de los sistemas operativos
### Por servicios ofrecidos:
- **Usuarios:** Mono/multiusuario.
- **Tareas:** Mono/multitarea.
- **Procesadores:** Monoprocesador o multiprocesador.
  - **Simétrico:** Carga distribuida entre procesadores.
  - **Asimétrico:** Tareas asignadas por prioridad.

### Por forma de ofrecer servicios:
- **Centralizados:** Uso de mainframes.
- **Distribuidos:** Procesos entre varios procesadores.
- **En red:** Computadoras conectadas para transmitir información.
- **De escritorio:** Usados en equipos personales.

### Por disponibilidad:
- **Propietarios:** Licencia necesaria, sin acceso al código fuente.
- **Libres:** Uso, modificación y distribución permitidos.

---

## Tipos de aplicaciones
- **Freeware:** Gratuitas.
- **Libres o propietarias.**
- **Open Source:** Acceso o no al código fuente.

### Tipos de licencias:
1. **OEM:** Vinculada al hardware.
2. **Retail:** Compra para siempre.
3. **Por volumen:** Similar a OEM, pero en paquetes.

---

## Gestores de arranque
Dispositivo encargado de cargar el sistema operativo.
- **Completo:** Cuando el ordenador está listo para aceptar requerimientos externos.
- Ejemplos: LILO, GNU GRUB, Boot Magic, etc.


