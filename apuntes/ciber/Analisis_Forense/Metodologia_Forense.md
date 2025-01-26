---
title: La Metodología Forense
description: 
published: true
date: 2025-01-26T12:42:56.948Z
tags: forense
editor: markdown
dateCreated: 2025-01-26T12:42:56.948Z
---

# Metodología Forense
En este apartado, se va a hablar de evidencias, tipos de evidencias, como adquirirlas y como preservarlas. Las evidencias es el corazón de la tarea forense, ya que sin ellos no podemos hacer nada.
## La evidencia digital
Las evidencias digitales pueden ser de dos tipos:
- Evidencias volátiles: Son aquellas que cambian facilmente como puede ser la RAM.
- Evidencia no volátiles: No realizan cambios con tanta facilidad, como un disco duro.
### Acotación de escena
Siempre que es posible, nos intentamos llevar el equipo para el analisís, pero que pasaría si en vez de un equipo entero, fuera un servidor, o un sistema critico en una empresa.

En este caso, deberemos acotar la escena teniendo en cuenta las siguientes pautas:
- ¿Qué equipos han sufrido de manera directa el incidente?
- ¿Qué otros equipos pueden haber sido afectado?

Tras esto intentamos analizar si cabe la posibilidad de hacer un analisis en caliente o si podemos llevarnos las pruebas al labotorio. Si nos encontramos en la situación de intentar llevarse un equipo critico, la respuesta claramente será hacer una adquisició en caliente.

### Adquisición de la evidencia
Antes de adquirir una evidencia, es necesario saber que es adquirirla y porque lo queremos hacer.
Adquirir una evidencia es crear una copia en un archivoq ue contenga toda la información original. Esta copia puede tener os formatos diferentes:
- Imagne forense: Copia exacta de un dispositivo físico en un archivo.
- Clonado forense: Copiado bit a bit de un dispositivo fisico en otro similar.

> Es importante tener en cuenta que cuando hacemos un clonado, el dispositivo de recepción, debe tener la misma o mayor capacidad que el de origen.
{.is-info}

Lo recomendado es el uso de imagen forense, ya que podriamos almacenar más de una imagen en los dispositivos.

También debemos tener en cuenta el concepto de adquisición física o lógica.
- Adquisición fisica incluye tanto la información, como las partes que componen al disco. Es decir, MBR, tabla de particiones...
- Adquisición lógica es aquel que solo incluye la parte de la información que deseamos, el volumen lógico "C" en Windows, por ejemplo.

#### Adquisición de evidencias volátiles
Las evidencias volátiles debemos obtenerlas en caliente, es decir con el equipo encendido y operando. Una de las primeras adquisiciones en caliente que nos viene a la mente, sería la memoria RAM. Para la adquisición de memoria RAM, es necesario el uso de herramientas o programass que puedan hacerlo.
> Tened en cuenta que el uso de programas, hace que parcialmente la prueba esté contaminada con estas herramientas.
{.is-danger}

Mediante el uso de herramientas de análisis de memoria RAM, podemos obtener contraseñas, documentos abiertos, imagenes, programas ejecución y mucho mas.
#### Adquisición de evidencias no volátiles
Con las evidencias no volátiles no es necesario que el equipo este encendido, puede estar en frio (apagado). Para la adquisición de estas prueabs podemos hacerlo mediante otro tipo de herramienta como FTK Imager.

#### Preservaión de la integridad e identidad
Para la preservación, es esencail realizar comprobaciones para verificar que es correcto el analisis que estamos haciendo de la prueba. Por lo tanto vamos a hacer uso de funciones hash.
> La función hash, nos permite verificar la integridad de la prueba, ya que no es posible repetir está cadena de caracteres.
{.is-info}

Por lo tanto deberemos comparar el primer hash (El que hemos realizado en la prueba original) con el segundo hash (La evidencia ya capturada), si es el mismo, entonces hemos verificado que es el mismo archivo.

Sin embargo, en caso de que tomemos evidencias en caliente, nos posible realizar una comprobación de hash, ya que en caliente como la memoria ram, el cambio es constante.

### Normativa ISO/IEC 27037
La normativa ISO/IEC 27037, nos divide el procedimiento de adquisción de pruebas en:
- Adquisición de evidencias en dispositivos encendidos: Primero se verifica que no esté encriptado, en caso de que este encriptado es necesario pedir la clave o bien hacer adquisicion en caliente, por otro lado si no lo está o si ya tenemos la evidencia continuamos con la información volatil. 
- Adquisición de evidecias en dispositivos apagados: Es bastante más sencilla, pero nos inhabilita obtener más información debido a la naturaleza de la prueba (No hay información volatil).
- Adquisicion en dispositivos criticos: En este caso es necesario la ayuda del personal técnico encargado de la gestión de dichos dispositivos.
- Adquisición parcial de evidencias: Cuando nos resulta imposible realizar una adquisición completa de las evidencias. Las realizaremos parcialmente, seguiremos los procedimientos anteriormente mencionados pero identificandoq ue datos son interesantes para el analisis.
- Adquisición de dispositivos de almacenamiento: Estas pruebas son menos volatiles, por lo que son los ultimos en ser adquiridos.
- Preservación: Deberemos hacer la verificación de las firmas digitales, para comprobar que lo adquirido es copia fiel de la evidencia original.
## La metodología forense informática
La metodología forense, nos permite obtener una organización en la forma de hacer el analisis forense:
- Asegurar la escena.
- Identificar y recolectar las evidencias.
- Preservar las evidencias.
- Analizar las evidencias obtenidas.
- Redactar informes sobre los resultados.

### Adquisición de pruebas (imaging)
#### Asegurar zonas
En esta estapa debemos hacer:
- Realizar fotografía del entorno del equipo.
- Proteger huellas dactilaes, recomendable el uso de guantes de látex.
- Anotar hora y fecha de los equipos implicados.
- Analizar si hay algún proceso en pantalla.
#### Identificación y recolectación
Deberemos analizar que datos son o más volatiles para la adquisición de las pruebas, también deberemos listar los equipos con sus caracteristicas, dibujando la estrcutura de red.

Tras realizar todo esto, podemos hacer una función hashs, con los datos obtenidos en caliente o frio para la verificación del las pruebas obtenidas.
#### Preservación de evidencias
Un mal uso de las pruebas, puede invalidad toda la investigación, por lo tanto es muy importante realizar una cadena de custodia. Una cadena de custiodia es aquel procedimiento controlado donde la finalidad es evitar cualquier tipo de manipulación, manteniendo el control absoluto sobre los elementos.
