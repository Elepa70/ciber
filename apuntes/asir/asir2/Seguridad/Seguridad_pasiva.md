---
title: Seguridad pasiva
description: 
published: true
date: 2025-01-18T18:10:54.289Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:10:54.289Z
---

# Seguridad Pasiva

## ¿Por qué hacer copias de seguridad?
En la actualidad se manejan grandes volúmenes de datos que crecen continuamente. Para protegernos frente a la **pérdida o degradación** de la información, es **imprescindible** realizar copias de seguridad (backups). Estas copias permiten **recuperar** los datos en caso de que los originales se vean afectados por:

1. Fallos de hardware  
2. Errores de software  
3. Errores humanos o sabotajes intencionados  
4. Desastres naturales

Una de las **tareas más importantes** del administrador de sistemas es elaborar e implementar un **plan de copia de seguridad y recuperación**.

---

## Planificación inicial de las copias de seguridad y la recuperación
Al diseñar una **estrategia** de copia de seguridad, se deben considerar los siguientes aspectos:

- **¿Qué datos** se deben salvaguardar?  
- **Volumen de datos**: ¿cuántos gigas/terabytes hay que respaldar?  
- **Tipo de dato**: ¿Existen restricciones legales (RGPD) o de confidencialidad?  
- **Frecuencia** de cambios en los datos.  
- **Horario idóneo** para realizar las copias de seguridad (evitar horas pico).  
- **Ubicación del almacenamiento** de las copias (¿fuera de las oficinas?).

---

## Medio y dispositivo de copia de seguridad
Para elegir la **solución de copia de seguridad** adecuada, se deben analizar:

- **Capacidad**: El hardware y los soportes deben cubrir los requerimientos de almacenamiento.  
- **Fiabilidad**: Tanto del dispositivo como del medio (cintas, discos...).  
- **Extensibilidad**: Poder ampliar la solución conforme crezcan los datos.  
- **Velocidad**: ¿Se requiere funcionamiento en paralelo o copias rápidas?  
- **Coste**: Ajustado al presupuesto de la organización.

### Soluciones habituales:
- **Unidades de cinta**:  
  - Emplean **cintas magnéticas** con capacidades de 4 GB hasta 10 GB o más.  
  - Aunque son lentas, su **bajo coste** resulta atractivo.  

- **Unidades DAT (Digital Audio Tape)**:  
  - Formatos como DLT (Digital Linear Tape) con capacidad de hasta 800 GB sin comprimir (1,6 TB comprimidos), o LTO y AIT, con capacidades aún superiores.  

- **Sistemas de cinta con cargador automático**:  
  - Pueden manejar varias cintas para crear grandes volúmenes de copia.  
  - **Desventaja**: alto coste.  

- **Unidades magneto-ópticas**:  
  - Combinan tecnología magnética y láser óptico.  
  - **Desuso** actual por su mayor coste.  

- **Unidades de disco (D2D - Disk to Disk)**:  
  - Muy rápidas para **copiar y restaurar** datos.  
  - Mayor inversión inicial, pero rentables a largo plazo gracias a su extensibilidad.

A la hora de adquirir cintas o discos, el número de unidades depende de:
- **Volumen** de datos a respaldar.  
- **Frecuencia** de las copias.  
- **Tiempo** de retención de datos históricos.

---

## Tipos de backups
Los principales tipos de copias de seguridad son:

1. **Backup completo**  
   - Copia *todos* los archivos y directorios seleccionados.  
   - Tras completarse, el sistema suele marcar el “bit de archivo” en 0.  
   - Ofrece restauración sencilla, pero consume más tiempo y espacio.

2. **Backup incremental**  
   - Copia solo los archivos **modificados** desde el último backup (sea *completo* o *incremental*).  
   - Ventaja: se ahorra espacio y tiempo al hacer la copia.  
   - Inconveniente: para restaurar, se requiere el **backup completo** y **todas** las copias incrementales intermedias.

3. **Backup diferencial**  
   - Copia los archivos **modificados** desde el último **backup completo**.  
   - Ventaja: restauración más rápida (solo el backup completo + el último diferencial).  
   - Inconveniente: ocupa más espacio que el incremental y cada diferencial va creciendo hasta que se hace un nuevo backup completo.

---

## Backup regla 3-2-1
Es una **práctica recomendada** para asegurar la protección de datos:

1. **Tres** copias de los datos: el original y al menos dos copias más.  
2. **Dos** tipos de almacenamiento: por ejemplo, disco y cinta o disco local y disco externo.  
3. **Una** copia **fuera** del sitio principal: mejor si está geográficamente separada.

---

## Estrategia de backup en cintas
Al usar cintas, suele emplearse una **programación cíclica**, rotando varios juegos de cintas. El objetivo es prolongar la vida de las cintas y reducir su número total. Puntos a considerar:

- **Reemplazo de medios**: Cada cinta tiene una vida útil limitada.  
- **Limpieza del dispositivo**: Las unidades de cinta requieren limpieza periódica.

### Esquemas de rotación más frecuentes:
- **Esquema simple**:  
  - Muy arriesgado; si aparece un virus, se corre el riesgo de **sobrescribir** con una copia ya infectada.

- **Round Robin**:  
  - Asigna 5 cintas (Lunes, Martes, Miércoles, Jueves, Viernes) para copias diarias.

- **Rotación de 8 medios** o **Abuelo-Padre-Hijo**:  
  - Se combinan:  
    - Copias diarias (incrementales/diferenciales)  
    - Copias semanales (completas)  
    - Copias mensuales (completas)  
  - Usualmente 5 cintas para cada día de la semana, 4 para semanas y 1 mensual.

Además se recomienda:
- **Almacenar las cintas** en un **armario ignífugo**.  
- **Etiquetar** correctamente cada cinta con:  
  - Tipo de copia (completa, incremental, diferencial)  
  - Fecha de realización  
  - Contenido aproximado (p.ej. sistema o base de datos)  
  - Nombre/técnico que realizó la copia  
  - Fecha de caducidad del medio según la vida útil recomendada.

---

## Estrategia de backup en discos
Cuando se usan **discos** (D2D), a menudo se recurre a dispositivos **NAS** o **SAN** con RAID. Sigue siendo conveniente **rotar** los discos o unidades lógicas, utilizando varias unidades de red o discos de servidor. Esto asegura redundancia y protección frente a fallos.

---

## Software de backup
Un sistema de copias de seguridad requiere un **software** que puede:

- Venir integrado con el sistema operativo.  
- Ser una herramienta externa.

**Aspectos clave** para elegir software de backup:
1. **Compatibilidad** con el hardware de copia elegido.  
2. Permitir **seleccionar** archivos de diversas unidades.  
3. Soportar **múltiples formatos** (normal, comprimido, cifrado...).  
4. Programar copias en **fechas y horas** específicas.  
5. **Registro** de las operaciones para su seguimiento y auditoría.

---

## Tres reglas de oro a no olvidar
1. **Rotación de medios**: No usar el mismo medio dos días consecutivos.  
2. **Copias offsite**: Mantener al menos una copia de seguridad **fuera** de la oficina.  
3. **Backup diario**: Realizar una copia regularmente (a diario o según requiera el negocio).

---

## Backup externo online (Cloud Backup)
Con la mejora de la **conectividad** a Internet, los **backups remotos** son cada vez más populares. Estas soluciones se basan en alojar las copias en un **servicio en la nube**, ofreciendo:

- **Multiplataforma** y alto rendimiento.  
- **Programar** automáticamente las copias.  
- Aprovechar la **banda ancha** optimizando el ancho de banda.  
- Almacenar **distintas versiones** de un mismo fichero.  
- **Cifrar** la información para preservar la privacidad.  
- Garantía de **equipo técnico especializado**.

Al contratar un **servicio de Backup Cloud**, verificar que cumpla con todo lo anterior y requisitos legales.

---

## Seguridad en la nube
Los **CASB** (Cloud Access Security Broker) actúan como intermediarios entre los usuarios y los servicios en la nube, ofreciendo una capa adicional de protección. Sus objetivos principales son:

- **Control de acceso y autenticación**: Definir políticas de acceso y autenticación sólidas.  
- **Monitoreo y análisis**: Registrar y analizar la actividad de los usuarios en la nube.  
- **Prevención de pérdida de datos (DLP)**: Cifrado y detección de datos sensibles.  
- **Control de aplicaciones**: Visibilidad y gestión de las aplicaciones SaaS utilizadas.  
- **Cumplimiento normativo**: Facilitar el cumplimiento de normativas (GDPR, HIPAA, etc.).

---
