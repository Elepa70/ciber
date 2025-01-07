---
title: Sistemas gestores de ficheros
description: 
published: true
date: 2025-01-07T17:46:39.999Z
tags: bbdd, gestores de ficheros
editor: markdown
dateCreated: 2025-01-07T17:46:39.999Z
---

# TEMA 1: SISTEMAS GESTORES DE FICHEROS

## Introducción a los ficheros
Los **ficheros** o **archivos** se definen como agrupaciones de datos relacionados que hacen referencia a uno o varios temas determinados y pueden estar ubicados en uno o más lugares concretos.

En terminología informática, un fichero es una estructura de datos que agrupa una secuencia de cero o más tuplas denominadas **registros**, y que a su vez se componen de otras estructuras de datos conocidas como **campos**.

- **Registros:** Unidad de tratamiento de los ficheros de datos.
- **Campos:** Mínima unidad de información creada con sentido en sí misma.

---

## Sistemas Gestores de Ficheros Convencionales

### Clasificación de los ficheros según su uso
Según su función y uso, los ficheros se clasifican en:

#### Permanentes
Son aquellos cuyo contenido permanece prácticamente inalterable en el tiempo. Existen tres tipos:

- **Maestros:** Información actualizada frecuentemente y en tiempo real.
- **Constantes:** Contenido prácticamente inmutable, como nombres de empresas o archivos INI de Windows.
- **Históricos:** Almacenan resultados de operaciones para consultas o análisis estadísticos.

#### Temporales
Duran poco tiempo tras su creación:

- **De movimiento:** Almacenan información temporal para actualizar ficheros maestros.
- **De maniobra:** Contienen datos de procesos en curso y se eliminan una vez finalizados.

---

## Modos de Organización y Acceso

### Modos de direccionabilidad
La **organización de un fichero** es la forma de estructurar y almacenar datos en un dispositivo de almacenamiento. Depende del dispositivo y se define durante su creación.

#### Tipos de archivos según direccionabilidad:

- **Archivos sin dirección (Secuenciales):** Se accede secuencialmente desde el inicio hasta el dato deseado.
- **Archivos con dirección:** Existe una relación directa entre la clave y la dirección del dato. Es decir, podemos investigar un punto sin necesidad de partir desde el inicio.

Dentro de los archivos con dirección podemos encontrar lo siguiente: 

- **Archivos de acceso directo:** La clave coincide con la dirección.
- **Con conversión clave:** Utilizan una **función HASH** para asociar claves con direcciones.
- **Organización secuencial indexada:** Acceso dinámico con tres áreas:
   - **Índices:** Segmentan el área primaria.
   - **Área primaria:** Contiene los datos ordenados.
   - **Área de excedentes:** Almacena nuevos registros.

---

## Modos de Acceso
Se denomina **modo de acceso** a aquella forma en la que un dispositivo que maneja un suporte de información posiciona en un lugar determinado un archivo, para realizar la operación de lectura o escritura de un registro. Los modos de acceso son los siguientes:
- **Acceso secuencial:** Se accede registro por registro de forma ordenada.
- **Acceso directo:** Permite acceder directamente a cualquier registro mediante una clave.

---

## Operaciones sobre los ficheros

### Operaciones sobre un fichero
- **Creación:** Generar un nuevo fichero.
- **Apertura:** Necesaria para realizar cualquier operación.
- **Ordenación:** Organizar los registros según criterios establecidos.
- **Compactación:** Eliminar huecos libres en los registros.
- **Cierre:** Finalizar las operaciones.

### Operaciones sobre registros
- **Actualización:** Adición, inserción, modificación o eliminación de registros.
- **Consulta:** Acceso a registros para verificar campos.

### Operaciones que crean nuevos ficheros
- **Copia:** Duplicar estructura y contenido.
- **Intersección:** Crear un nuevo fichero con registros comunes.
- **Concatenación:** Fusionar dos ficheros en uno.
- **Partición:** Dividir un fichero según criterios específicos.

---

## Problemas en la gestión de datos con sistemas gestores de ficheros

### Respecto a los ficheros
Se debe a la necesidad de controlar la integridad semántica, el control de autorizaciones y la concurrencia de accesos o acceso simultáneo de varios usuarios al mismo ficheros de datos.
- **Integridad semántica:** Validar restricciones en los datos.
- **Control de autorizaciones:** Identificadores únicos para evitar accesos indebidos.
- **Control de concurrencia:** Resolver conflictos de acceso simultáneo.

### Respecto a los datos
Se deben a su estructura física, al modo de estar almacenados en diferentes archivos y se destacan los siguientes problemas
- **Redundancia:** Duplicación innecesaria de datos.
- **Inconsistencia:** Datos contradictorios.
- **Aislamiento:** Dificultad para encontrar datos dispersos.

---

## Características Generales y Ventajas de una Base de Datos

Las bases de datos surgen para eliminar los problemas de gestión con archivos convencionales, proporcionando un sistema más eficiente e independiente.

### Características
- **Desempeño:** Tiempo de respuesta adecuado.
- **Mínima redundancia:** Reducción de duplicación.
- **Capacidad de acceso:** Acceso optimizado a los datos.
- **Simplicidad:** Representación lógica clara.
- **Integridad:** Garantía de veracidad en los datos.
- **Seguridad y privacidad:** Protección contra pérdidas y accesos no autorizados.
- **Afinación:** Organización eficiente para tiempos de respuesta óptimos.
- **Interfaz con el pasado y futuro:** Adaptabilidad a cambios.

### Ventajas
- Control centralizado.
- Mayor coherencia de datos.
- Almacenamiento eficiente.
- Mantenimiento de integridad.

---

## Cuándo NO usar un SGBD

- **Costes elevados:** Altas inversiones iniciales.
- **Aplicaciones simples y estables:** Sin cambios esperados.
- **Requerimientos estrictos en tiempo real:** Pueden no ser óptimos.
- **Sin acceso concurrente necesario.**


