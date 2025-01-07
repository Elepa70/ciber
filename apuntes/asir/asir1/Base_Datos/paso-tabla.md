---
title: Paso a tabla
description: 
published: true
date: 2025-01-07T19:16:29.933Z
tags: bbdd, tabla
editor: markdown
dateCreated: 2025-01-07T19:16:29.933Z
---

# Tema 5: Paso a Tabla

## Primer paso: Eliminación de atributos multivaluados y compuestos
Antes de comenzar a realizar un paso a tabla adecuado, se deben eliminar los **atributos multivaluados** y **compuestos**:
- **Atributos multivaluados:** Aquellos que pueden tomar varios valores (ej., Color de coche: Rojo, Amarillo y Verde). Para eliminarlos, se debe crear una **entidad débil** que represente esta característica.
- **Atributos compuestos:** Aquellos que pueden descomponerse en varios atributos (ej., Dirección: Calle, Nº, CP, Localidad). Para eliminarlos, simplemente se extiende su concepto.

## Segundo paso: Transformación de las entidades
- **Entidades fuertes:** Se convierten en tablas. Sus atributos se convierten en columnas, su clave primaria es el identificador principal, y los identificadores candidatos se convierten en claves candidatas.
- **Entidades débiles:**
   - Si necesitan una clave primaria compuesta, se combina la clave primaria de la entidad fuerte con la de la débil.
   - Si la entidad débil tiene una clave suficiente, la clave primaria de la fuerte se convierte en clave externa o candidata.
- **Generalización:** Las subentidades tendrán sus propias tablas. Si la clave primaria de la superentidad es distinta, se añade como clave externa.
- **Agregación:** Se crea una tabla con las tres claves primarias involucradas.

## Tercer paso: Transformación de las relaciones
### Reflexivas
- **Opción 1 (1:1):** Se crea una tabla y se añade como clave externa el identificador de la entidad en uno de sus roles.
- **Opción 2 (1:N):** Se crea una tabla para la relación como si fuera un binario N:M.

### Relación 1:1
- **Participación total:** Si las entidades tienen el mismo identificador, se fusionan en una tabla. Si son diferentes, se intercambian las claves primarias y externas.
- **Participación parcial:** Se puede añadir como clave externa o crear una tabla auxiliar con las claves primarias.

### Relación 1:N
- **Participación total o (0,n):** Ambas entidades generan tablas. La clave primaria de la entidad con menor cardinalidad se añade como clave externa en la otra.
- **Participación parcial o (0,1):** Se crean tablas independientes y una tabla para la relación.

### Relación N:M
- **Independiente:** Se crean tablas para ambas entidades y una tabla intermedia que contiene las claves primarias de ambas.

Este proceso garantiza una transición adecuada desde un modelo entidad-relación hacia un modelo tabular eficiente y funcional.

