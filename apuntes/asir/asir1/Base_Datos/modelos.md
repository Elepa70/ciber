---
title: Modelo de datos relacional
description: 
published: true
date: 2025-01-07T19:10:21.317Z
tags: bbdd, entidad-relacion, duplas, tuplas, sgbd
editor: markdown
dateCreated: 2025-01-07T19:10:21.317Z
---

# TEMA 3: MODELO DE DATOS RELACIONAL

## Introducción
El diseño de una base de datos consiste en definir la estructura de los datos que deben tener un sistema de información determinado. Para ello, se suele seguir una regla general, unas fases de proceso con:

- **Diseño conceptual:** Descripción de alto nivel de la estructura de la base de datos, cuyo objetivo es describir el contenido de información de la base de datos y no las estructuras de almacenamiento.
- **Diseño lógico:** Es una descripción de la estructura de la base de datos en términos de las estructuras de datos que pueda procesar un tipo de SGBD. Este diseño se adapta al SGBD que se vaya a usar, como pueden ser tablas en SQL.
- **Diseño físico:** Da una descripción de la implementación de una base de datos en memoria secundaria: las estructuras de almacenamiento y los métodos utilizados para tener un acceso eficiente a los datos.

---

## El modelo relacional
En este modelo, las capas de diseño conceptual y lógico se parecen mucho. Se emplea mediante diagramas de **Entidad/Relación** (modelo conceptual) y **tablas y relaciones** (modelo lógico), lo podemos ver en lenguajes como **MySQL**.

Se creó teniendo en cuenta la teoría de **normalización de relaciones** (Objetivo: eliminación de comportamientos anómalos de relaciones y eliminación de redundancia).

La representación de la información obtenida causa:
- Que origine esquemas que representen fielmente la información, los objetos y las relaciones entre ellos existentes en el dominio del problema.
- Pueda ser entendida fácilmente por los usuarios que no tengan preparación previa.
- Haga posible ampliar el esquema de la base de datos sin modificar la estructura lógica existente y, por tanto, sin modificar los programas de aplicación.
- Permita la máxima flexibilidad en la formulación de los interrogantes previstos y no previstos sobre la información mantenida en la base de datos.

---

## Terminología del modelo relacional
Las normas por las que se rige el modelo relacional de base de datos:
- Todos los datos se representan en forma de **tablas (relaciones)**.
- Las tablas se componen por **filas (registros)** y **columnas (campos)**.
- Una tabla es homogénea por columnas (todos los datos de una columna son de la misma clase).
- Cada fila de la tabla representa un ítem de datos elemental.
- Cada columna de la tabla tiene asignado un **nombre único**.
- Todas las filas son diferentes (no hay duplicados).
- Las filas y columnas carecen de orden al ser almacenadas.
- El orden de las columnas lo determina cada consulta.
- Cada tabla debe poseer una **clave primaria**.
- Para establecer una relación entre dos tablas, es necesario incluir en una de ellas la **clave primaria** de la otra, denominada **clave externa**.

A una tabla se le denomina **relación**. A las filas se les denomina **tuplas** y al conjunto de sus columnas **dominio de la relación**.

---

### Relación
Una **relación** es una tabla con nombre propio compuesta por:
- **Filas (Registro-Tupla):** Cardinalidad, número de tuplas en un instante dado.
- **Columnas (Campo-Atributo):** También conocidas como grado/dominio, son independientes del tiempo.

---

### Dominios y atributos
Los valores que pueden tomar los atributos de una relación se toman de un **dominio**.
Un dominio describe el rango de valores válidos que puede tomar un atributo de una relación.
En una relación, puede existir tantos dominios como atributos, o varios atributos pueden tomar valores sobre un mismo dominio.

---

### Intención y extensión
Una relación en una base de datos relacional tiene dos componentes:
- **Intención:** Estructura estática del objeto del mundo real representado mediante la relación.
  - Define la estructura de datos y sus restricciones de integridad.
- **Extensión:** Hace referencia al número de tuplas que contiene en un instante dado.

---

## Consistencia de la representación lógica relacional
### Claves de las relaciones
Si uno o un conjunto de atributos toman un valor único en el dominio del problema, identifican de forma única una tupla (Clave primaria).

- **Clave primaria:** Identificador único de las tuplas.
- **Clave candidata:** Atributos que cumplen unicidad y minimalidad. De ellas se elige la clave primaria.

### Reglas de integridad relacionales
- **Clave primaria:** No puede tener valores nulos.
- **Clave externa:** Debe ser nula o coincidir con un valor en la relación original.

**Restricciones adicionales:**
- Valores permitidos para los atributos.
- Condiciones basadas en predicados.

---

### Implementación de la integridad en los SGBD
- Las reglas de integridad garantizan que los estados de la base de datos sean correctos.
- Un sistema debe rechazar valores nulos en claves primarias.
- Se debe evitar la duplicidad de claves primarias.
- Las claves externas deben cumplir las reglas referenciales.

Un **SGBD** debe permitir especificar:
- Estructura de la relación.
- Clave primaria.
- Clave externa asociada.
- Operaciones desencadenadas por actualizaciones y borrados.

