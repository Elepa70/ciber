---
title: Temario Windows
description: 
published: true
date: 2025-01-14T12:18:30.583Z
tags: iso, windows
editor: markdown
dateCreated: 2025-01-14T12:18:30.583Z
---

# TEMARIO DE WINDOWS

---

## ÍNDICE DE CONTENIDOS
1. **MBR**  
   - Acerca del Windows Server 2008
   - Arranque del ordenador
   - El sector de arranque maestro (MBR)
   - GPT
   - Particiones
   - Tipos de particiones
   - Utilización de las particiones primarias y lógicas
   - Estructura de particiones
2. **BCD y Bootrec**  
   - Elementos de arranque
   - El BCD
   - Bootrec
3. **Registro**  
   - Registro virtualizado
   - Registro transaccional
   - Copias de seguridad
   - Modificaciones del registro
4. **MSI**  
   - Actualizaciones
   - Instalación de software
5. **SCRIPT**
   - ONLINE
   - OFFLINE
6. **TODOS LOS COMANDOS**
   - MBR
   - BCD y Bootrec
   - Registro
   - MSI
7. **Preguntas algo rebuscadas**
   - MBR
   - BCD y Bootrec
   - Registro
   - MSI

---

## 1. MBR

### Acerca del Windows Server 2008
Antes de instalar Windows Server 2008, es esencial elegir un sistema de archivos:
- **FAT (File Allocation Table):** Compatible con MS-DOS y cualquier Windows.
- **FAT32:** Permite particiones entre 2 GB y 4 GB, con volúmenes de hasta 2 TB.
- **NTFS (New Technology File System):** Volúmenes de hasta 16 TB con funcionalidades avanzadas, ideal para sistemas modernos.

### Arranque del ordenador
El proceso de arranque incluye:
1. La BIOS carga el POST (Power-On Self-Test) desde una memoria no volátil.
2. La BIOS busca un sistema operativo en el MBR y lo carga en la RAM.
3. Se utiliza el CMOS para almacenar configuraciones de hardware.

### El sector de arranque maestro (MBR)
- Reside en los primeros 512 bytes del disco de inicio.
- Contiene:
  - **Bootloader:** 446 bytes.
  - **Número mágico:** 2 bytes con valor `55 xAA`.
  - **Tabla de particiones:** Detalles sobre las particiones activas.

Importante: El MBR es único, pero cada partición tiene su propio sector de arranque.

### GPT
- Supera las limitaciones del MBR (máximo de 2.19 TB por partición).
- Características:
  - Compatible con UEFI.
  - Hasta 128 particiones primarias.
  - Tamaño máximo de partición: 9.4 Zettabytes.
  - Almacena dos copias de seguridad de la tabla de particiones.

### Particiones
Motivos para particionar:
1. **Organización:** División entre usuarios o propósitos.
2. **Multi-SO:** Cada sistema operativo requiere su propia partición.
3. **Seguridad:** Separar datos y sistema operativo.

Tipos:
- **Primarias:** Directamente arrancables.
- **Lógicas:** Dentro de una partición extendida.
- **GPT:** Hasta 128 particiones primarias.

---

## 2. BCD y Bootrec

### Elementos de arranque
El flujo general:
1. La CPU ejecuta el código de la BIOS.
2. Se carga el MBR, que identifica la partición activa.
3. El VBC (Volume Boot Code) encuentra y ejecuta el gestor de arranque (bootmgr o NTLDR).
4. El gestor consulta el BCD y carga el sistema operativo.

### El BCD
- Estructura arbórea que contiene:
  - **BCD Store:** Almacén.
  - **BCD Object:** Gestor de arranque.
  - **Elementos:** Parámetros asignados.
- Elementos destacados:
  - **Device:** Dispositivo donde se encuentra.
  - **Locale:** Idioma.
  - **Timeout:** Tiempo para iniciar.

### Bootrec
- Soluciona problemas del MBR, VBC y BCD.
- Comandos clave:
  - `bootrec /fixmbr`
  - `bootrec /fixboot`
  - `bootrec /rebuildbcd`

---

## 3. Registro

### Registro virtualizado
- Copias privadas para cada aplicación con permisos restringidos.

### Registro transaccional
- Cambios en el registro realizados como operaciones atómicas.

### Copias de seguridad
Comandos:
- Crear: `wbadmin start systemstatebackup -backuptarget:(unidad)`
- Restaurar: `wbadmin start systemstaterecovery -version:(copia)`

### Modificaciones del registro
- HKEY_CLASSES_ROOT: Personalización de menús contextuales.
- HKEY_CURRENT_USER: Deshabilitar botones (DWORD NoClose).
- HKEY_LOCAL_MACHINE: Ejecutar programas al inicio.

---

## 4. MSI

### Actualizaciones
Tipos:
1. **Importantes:** Mejoran la seguridad.
2. **Recomendadas:** Mejoran la experiencia del usuario.
3. **Opcionales:** No se instalan automáticamente.

### Instalación de software
Formatos:
- `.msi`: Instalaciones automatizadas.
- `.mst`: Modifica configuraciones de `.msi`.
- `.msp`: Parches para software instalado.

Comandos:
- Instalación silenciosa: `msiexec /quiet /i archivo.msi`
- Instalación con transformaciones: `msiexec /i archivo.msi TRANSFORMS=archivo.mst`

---

## 5. SCRIPT

### ONLINE
- Crear un archivo `.bat` con el contenido deseado.
- Ubicar el script en:
  - `HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion/Run`

### OFFLINE
- Acceder al registro desde la consola de recuperación.
- Montar y modificar el registro manualmente.

---

## 6. TODOS LOS COMANDOS

### MBR
- `diskpart`
- `select disk/partition`
- `convert GPT/MBR`

### BCD y Bootrec
- `bcdedit /create`
- `bootrec /fixmbr`
- `bootrec /rebuildbcd`

### Registro
- `wbadmin start systemstatebackup`
- `regedit`

### MSI
- `msiexec /quiet /i archivo.msi TRANSFORMS=archivo.mst`


