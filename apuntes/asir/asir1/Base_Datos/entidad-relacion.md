---
title: Modelo Entidad/Relación
description: 
published: true
date: 2025-01-07T19:15:27.314Z
tags: bbdd, entidad-relacion, cardinalidad
editor: markdown
dateCreated: 2025-01-07T19:15:27.314Z
---

# Tema 4: Modelo Entidad/Relación

## Modelo Entidad Relación y sus elementos básicos
El **modelo entidad-relación** es un conjunto de conceptos, reglas y notaciones que permiten formalizar la semántica del mundo real que se pretende modelar, en una representación gráfica denominada **esquema de la Base de Datos**.

### Sus elementos básicos son:
- **Entidades:** Conjuntos de elementos con existencia propia y que se caracterizan por las mismas propiedades. Son cosas de las que queremos guardar información.
- **Atributos:** Consisten en aquellas cualidades de las entidades.
- **Interrelación:** Representan las asociaciones del mundo real entre una o más entidades. Además, estas interrelaciones también tienen elementos que son:
   - **Nombre:** Identificador único en el esquema.
   - **Grado:** Número de entidades participantes.
   - **Tipo de correspondencia:** 1 a 1, 1 a N, N a M.
   - **Rol:** Función que desempeña cada tipo de entidad participante.

#### Cardinalidad
Se refiere al número de participaciones en un mínimo y un máximo. Se representa entre paréntesis y con comas, por ejemplo: **(1, n)**.

#### Otros elementos importantes
- **Tipo de Correspondencia:** Expresan las restricciones del mundo real en las relaciones entre entidades.
- **Agregación:** Permite agregar una relación a otra relación existente.
- **Generalización:** Se extraen atributos comunes a diferentes entidades para simplificar el modelo.

El modelo entidad-relación es una herramienta esencial para el diseño estructurado y claro de bases de datos, permitiendo representar fielmente el mundo real en el esquema lógico de una base de datos.

