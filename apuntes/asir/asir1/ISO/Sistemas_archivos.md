---
title: Sistemas de archivos
description: 
published: true
date: 2025-01-14T12:17:10.382Z
tags: iso, archivos
editor: markdown
dateCreated: 2025-01-14T12:17:10.382Z
---

# TEMA 2: LOS SISTEMAS DE ARCHIVOS

Un **sistema de archivos** es una estructura utilizada para organizar y gestionar archivos en un dispositivo interno o externo mediante una función determinada. Los sistemas de archivos constan de dos elementos fundamentales:

1. **Archivos:** Objetos que contienen los datos.
2. **Directorios/carpetas:** Contenedores que almacenan archivos u otros directorios, facilitando una mayor organización.

---

## Los archivos
### Elementos clave:
1. **Nombre del archivo:** Identificador del archivo.
2. **Extensión del archivo:** Indica el tipo de archivo. Por ejemplo:
   - En MS-DOS: Hasta 8 caracteres en el nombre y 3 en la extensión.
   - En Windows: Hasta 255 caracteres con el uso de LFN (Long File Name).

### Atributos de los archivos:
- **Atributo de sistema (S).**
- **Atributo de oculto (H).**
- **Atributo de solo lectura (R).**
- **Atributo de archivo (A).**
- **Fecha y hora.**
- **Tamaño del archivo.**

### Tipos de archivos:
1. **Ejecutables:** Diseñados para funcionar por sí mismos.
2. **No ejecutables:** Almacenan información para ser utilizada por otros programas.

### Comodines/Wildcards:
Facilitan la selección de ficheros:
- `*`: Sustituye a todos los caracteres.
- `?`: Sustituye a un carácter.
- `[0Aa-9Zz]`: Representa un rango de caracteres.
- `[!Aa-Zz]`: Excluye los caracteres del rango especificado.
- `{}`: Une varias búsquedas.

---

## Los directorios
Los directorios tienen una estructura jerárquica en forma de árbol. En todo sistema de archivos existe un directorio especial denominado **raíz**, desde el cual se puede buscar un archivo mediante:

- **Ruta de acceso absoluta:** Parte desde la raíz.
- **Ruta de acceso relativa:** Parte desde la ubicación actual.

### Atributos de los directorios:
- **Atributo oculto (H).**
- **Atributo de solo lectura (R).**
- **Atributo de archivo (A).**
- **Fecha y hora.**

---

## Implementación del sistema de archivos
Un **bloque** está compuesto por un conjunto de sectores asociados a un archivo. Los archivos se almacenan en uno o más bloques de sectores.

- **Tamaño de los bloques:**
  - Si los bloques son demasiado pequeños, el tiempo de lectura es mayor.
  - Si son demasiado grandes, se desperdicia espacio en disco.

### Técnicas de asignación de bloques:
1. **Asignación adyacente:**
   - Los bloques de un archivo se colocan contiguamente.
   - Ventajas: Rápido acceso.
   - Desventajas: Difícil de implementar y puede causar fragmentación del espacio.

2. **Asignación en forma de lista ligada:**
   - El directorio contiene la dirección del primer bloque del archivo.
   - Cada bloque almacena la dirección del siguiente bloque hasta llegar a un bloque nulo.
