---
title: Normalización
description: Una vez realizado el esquema Entidad/Relación, debemos evitar Redundancias y Ambigüedades
published: true
date: 2025-01-09T12:47:02.215Z
tags: bbdd, forma normal, armstrong
editor: markdown
dateCreated: 2025-01-09T12:47:02.215Z
---

# Tema 6: Normalización

## Problemas del esquema relacional
Aunque hayamos realizado el esquema Entidad/Relación, se pueden dar casos donde se producen:
- **Redundancia**
- **Ambigüedades**
- **Pérdida de restricciones de integridad**
- **Anomalías en operaciones de modificación de datos**

Para corregir estos errores, se recurre a las **Formas Normales** como método de solución.

---

## Formas Normales

El concepto fue iniciado por **Codd** y continuado por otros autores. Las **formas normales** se estructuran en etapas, y cuanto más alta es la forma normal, más se garantiza la eliminación de redundancia y otros problemas.

- Las formas normales están fundamentadas en principios matemáticos.
- Se asegura que alcanzando la **3ª Forma Normal** o la **Forma Normal de Boyce-Codd (BCNF)**, una base de datos está completamente normalizada.
- La **4ª** y **5ª Formas Normales** son menos comunes y más polémicas, por lo que el requisito mínimo es alcanzar la 3ª Forma Normal.

**La normalización de datos** consiste en descomponer esquemas de relación que no cumplen las condiciones, distribuyendo sus atributos entre esquemas más pequeños que sí cumplen las condiciones establecidas.

---

## Definiciones previas
### Dependencia funcional
Dada una relación **R**, se dice que un atributo **Y** depende funcionalmente de un atributo **X** (X → Y), si y sólo si, para cualquier valor de **X** existe un único valor de **Y** en **R**.

### Determinante de una relación
Un **determinante** es un atributo simple o compuesto del cual depende completamente otro atributo dentro de la relación.

### Atributo primo
Un **atributo primo** es aquel que forma parte de la clave primaria de la relación.

### Dependencia funcional plena o completa
Un atributo **Y** pertenece a una relación **R** y es funcionalmente dependiente de forma completa de otro atributo **X** (en **R**) si **Y** depende de **X**, pero no de ningún subconjunto de **X**.

### Dependencia Funcional Trivial
Una dependencia funcional es trivial si **X** determina a **Y**, y **Y** es un subconjunto o igual a **X**.

### Dependencia funcional elemental
Es aquella donde **X** determina a **Y**, y **Y** es un atributo único.

### Dependencia funcional Transitiva
Una dependencia es transitiva si se cumple que:
- X → Y
- Y → Z
- X no determina directamente a Z.
  
En este caso, se dice que **Z** tiene una dependencia transitiva respecto a **X** a través de **Y**.

---

## Axiomas de Armstrong
Los **Axiomas de Armstrong** definen propiedades fundamentales de las dependencias funcionales en un sistema relacional.

### Reflexividad
Si **Y** pertenece a **X**, entonces **X → Y** (es una dependencia funcional trivial).

### Aumentatividad
Si **X → Y**, entonces añadiendo el mismo atributo **Z** a ambos lados se cumple que:
- **XZ → YZ**

### Transitividad
Si **X → Y** y **Y → Z**, entonces **X → Z**.

### Autodeterminación
Todo atributo determina a sí mismo: **X → X**.

### Descomposición
Si **X → YZ**, entonces:
- **X → Y**
- **X → Z**

### Unión
Si **X → Y** y **X → Z**, entonces:
- **X → YZ**

### Composición
Si **X → Y** y **Z → W**, entonces:
- **XZ → YW**

### Pseudotransitividad
Si **X → Y** y **ZY → W**, entonces:
- **ZX → W**


