---
title: Introducción a Base de Datos
description: 
published: true
date: 2025-01-07T17:34:48.832Z
tags: bbdd
editor: markdown
dateCreated: 2025-01-07T17:34:48.832Z
---

# Introducción a las BBDD

## Sistemas de información
Los **sistemas de información** son un conjunto de elementos tecnológicos relacionados que cooperan para la consecución de un determinado fin empresarial, profesional o personal.

### Sistema Empresarial
Hemos descrito el sistema de información, ahora toca el **sistema empresarial**. Está compuesto por: **capital**, **recursos humanos**, **productos o servicios** y **los inmuebles donde se desarrolla la actividad**. La finalidad de una empresa es la **obtención de beneficios**.

Los **subsistemas** del sistema empresarial son:
- **Real**: Intervienen directamente en la gestión de producción.
- **Financiero**: Se encarga de la gestión, captación, administración y control de los recursos financieros.
- **Directivo**: Responsable de la definición de objetivos.

### Sistemas de información: Concepto y Componentes
Los **sistemas de información** son subsistemas de la empresa que facilitan la transferencia de información entre los demás subsistemas. Están compuestos por tres elementos:
- **Recurso físico**: Hardware, software, documentos y archivadores.
- **Recursos humanos**: Usuarios y personal informático.
- **Protocolos**: Rigen el uso y la transmisión de los flujos de información.

La implantación de estos sistemas se produce en varios niveles, siendo uno de ellos el **nivel transaccional**. Cuando la gestión de un sistema de información se realiza parcial o totalmente por ordenadores, se denomina **Sistema Informático**, cuyos tres elementos son similares a los del sistema de información:
- **Físico**: Software y hardware.
- **Recursos humanos**.
- **Normas o protocolos**: Incluyen el software.

### Justificación de la implantación de sistemas de información
Facilitan la **comprensión de la empresa** en cuanto a planificación, gestión y control de cada actividad desarrollada, además de permitir la obtención de variables para una mejor actuación en acuerdos comerciales.

Como tal, sirven para **emplear evaluaciones cuantitativas** en los diferentes departamentos empresariales.

### Tipos de sistemas de información

#### Ofimática
Aquí se incluyen sistemas de información que **no están especializados en ninguna tarea concreta**, basados en tecnologías de la información y comunicación. Existen dos tipos de elementos:
- Aquellos que permiten un **intercambio de información** (ej. Procesadores de texto, Microsoft Office).
- Aquellos **sistemas de comunicación basados en Internet** (ej. Navegadores, videollamadas).

#### Proceso electrónico de datos
Permiten **gestionar eficazmente tareas repetitivas** en diferentes departamentos, como nóminas, contabilidad o gestión de impuestos. A estos sistemas capaces de gestionar grandes volúmenes de datos se les denomina **sistemas de proceso de transacciones**.

Estas transacciones tienen dos fases:
- **Adquisición de datos**: Selección, almacenamiento informatizado, revisión y corrección de errores.
- **Tratamiento de la información**: Clasificación, codificación, creación de soportes de software y actualización de datos en tablas.

#### Sistemas de información de gestión
Cuando se necesita un mejor control de la gestión, se implementan estos sistemas, que consisten en emplear **software de bases de datos**. Permiten obtener **listados impresos**, mostrar, añadir o modificar la información en pantalla.

Se utilizan para:
- Crear **informes complejos**.
- Ayudar en la **toma de decisiones empresariales**.

#### Sistemas de soporte a la toma de decisión
Cuando un sistema de información de gestión no es suficiente, se incorpora este sistema. Combina elementos de los sistemas anteriores con tecnologías actuales (ej. comercio electrónico, gestión de compraventa). Facilita la obtención de **información personalizada** para decisiones **no repetitivas o no estructuradas**.

El **Data Mining** es utilizado en este sistema para **agrupar datos de manera eficiente**.

Estos sistemas están compuestos por:
- **Recipientes de datos**: Bases de datos y ficheros.
- **Modelos teóricos**: Software de usuario y herramientas de análisis.

Un ejemplo sería una página de **reservas de vuelos**.

#### Sistemas expertos
Son un tipo especial de sistema de soporte a la toma de decisiones. Tienen cierta **autonomía para resolver problemas** y están parametrizados y programados según modelos predefinidos.

Su objetivo es **obtener soluciones adecuadas** mediante la ejecución de acciones preprogramadas.

#### Sistemas inteligentes de soporte a la decisión
Combinan características de los **sistemas expertos** y los **sistemas de soporte a la toma de decisiones**. Son **completamente autónomos** y utilizan **inteligencia artificial** para mejorar su toma de decisiones.

Se relacionan con el **data warehousing** y funcionan como **nodo coordinador** con el sistema de información empresarial.

### Importancia de los datos en los sistemas de información
Al almacenar la información estructurada de una empresa en un sistema informático, es necesario definir dos características:
- **Diseño lógico**: Apariencia de los datos cuando son almacenados y mostrados al usuario.
- **Diseño físico**: Forma en la que se guardan los datos en un dispositivo de almacenamiento (disquete, disco duro).

Según el modelo empleado en el diseño físico, hay dos sistemas:
- **Basado en ficheros de datos**: Datos y programas de recuperación se almacenan como elementos separados.
- **Sistema de bases de datos**: Datos y programas tienen al menos **una unidad lógica**, y algunos incluso una **unidad física**.

La elección entre uno u otro depende de la **fecha de implementación**. Actualmente, las técnicas de **data warehousing** permiten que la importancia recaiga en **los datos**, no en los formatos de almacenamiento.

#### Evolución del almacenamiento de datos
1. **1ª Generación**: Sistema de archivos convencionales.
2. **2ª Generación**: IMS, modelo jerárquico.
3. **3ª Generación**: Modelo de redes, IDSS.
4. **4ª Generación**: Modelo relacional, SQL, DBL.
5. **5ª Generación**: Gestores basados en la orientación a objetos.

El **diseño lógico** en una base de datos representa un conjunto de información relativa a personas o elementos de interés. Se organiza en **tablas**, con filas y columnas:
- **Filas**: Representan registros.
- **Columnas**: Representan campos.

