---
title: Criptografia
description: 
published: true
date: 2025-01-18T18:09:58.337Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:09:58.337Z
---

# Criptografía

## Conceptos básicos de criptografía
La palabra **criptografía** proviene del griego: *kryptós* (“oculto”) y *graphé* (“escritura”), por lo que su significado literal es “escritura oculta”. Se encarga de estudiar las distintas técnicas empleadas para **transformar** la información y **hacerla irreconocible** a terceros no autorizados.

Un **algoritmo criptográfico** es una función matemática utilizada en los procesos de cifrado y descifrado. Trabaja en combinación con una **clave** o **llave** criptográfica. Al cifrar, el algoritmo combina la información con la clave, resultando en un texto cifrado (o criptograma). Para descifrarlo, el mismo algoritmo realiza el proceso inverso con la clave correspondiente.

La **ciencia del criptoanálisis** estudia las técnicas para **romper** los sistemas de cifrado sin poseer las claves legítimas.

---

## Historia

### Escítala
Los primeros mensajes cifrados documentados datan del siglo V a.C., en la Grecia espartana, donde se utilizaba la **escítala**. Consistía en enrollar una cinta de cuero sobre un bastón de un grosor determinado para escribir el mensaje en líneas paralelas. Para descifrarlo, era necesario utilizar otro bastón del mismo grosor y enrollar la cinta en él.

### Polybios
Los griegos desarrollaron un sistema matemático conocido como **cuadrado o tabla de Polybios**, donde cada letra del alfabeto se sustituye por sus coordenadas en la tabla, facilitando un cifrado básico por sustitución.

### Método César
El **método César** (o cifrado de César) consiste en **desplazar** cada letra del mensaje un número fijo de posiciones en el alfabeto. Uno de sus principales problemas radica en que es fácilmente rompible mediante análisis de frecuencias o palabras repetidas.

### Cifrado Vigenère
Para solventar las debilidades del método César, se creó el **cifrado Vigenère**, que utiliza **varios alfabetos** para cifrar un texto. El receptor debe conocer la **secuencia de alfabetos** (o la palabra clave) empleada. Con este sistema, cada letra del mensaje se cifra con una posición distinta, dependiendo de la clave, lo que dificulta el criptoanálisis por frecuencia.

En esta clase de cifrados clásicos se emplean dos técnicas fundamentales:  
- **Sustitución** (reemplazar letras, ej. César).  
- **Transposición** (cambiar el orden de las letras, ej. escítala).

### La máquina Enigma y la máquina Colossus
Durante la **Segunda Guerra Mundial**, los alemanes utilizaron la máquina **Enigma**, considerada en su momento casi indescifrable. Sin embargo, los británicos desarrollaron la máquina **Colossus**, gracias a los trabajos de **Alan Turing** y otros criptógrafos, logrando descifrar gran parte de las comunicaciones alemanas.

En la actualidad, la criptografía moderna se basa fundamentalmente en **cifrado simétrico** y **cifrado asimétrico**.

---

## Cifrado Simétrico
En el **cifrado simétrico**, se emplea **una sola clave** para cifrar y descifrar el mensaje. Su seguridad depende de que esta clave permanezca secreta.

**Ventajas**:
- Alta **velocidad** de cifrado, ideal para grandes cantidades de datos.

**Inconvenientes**:
- Es necesario **intercambiar** las claves de cifrado de forma segura.  
- Hace falta una clave distinta para cada par de usuarios que desee comunicarse.

---

## Cifrado Asimétrico
El **cifrado asimétrico** utiliza un **par** de claves: una **clave privada**, conocida únicamente por el usuario, y una **clave pública**, conocida por todos. 

La **clave pública** se deriva de la privada, pero no es factible obtener la clave privada a partir de la pública debido a la complejidad matemática involucrada (p.ej., factorización de grandes números primos). Aunque en teoría se puede romper con suficientes recursos, a día de hoy se considera inviable para claves de tamaño adecuado (excepción potencial: ordenadores cuánticos en el futuro).

**Ventajas**:
- No se requiere **intercambiar** la clave secreta.  
- Cada usuario solo necesita **2 claves** (privada y pública), reduciendo la proliferación de claves.

**Inconvenientes**:
- **Más lento** que el cifrado simétrico.  
- Las claves suelen ser **mucho más largas** que en el cifrado simétrico, para asegurar la misma robustez.

---

## Criptografía híbrida
Combina **cifrado simétrico** y **cifrado asimétrico** para aprovechar lo mejor de cada uno:

1. Se genera una **clave simétrica** aleatoria para cifrar el mensaje (más rápido).  
2. Dicha clave simétrica se cifra con la **clave pública** del receptor (cifrado asimétrico).  
3. El destinatario, con su **clave privada**, descifra la clave simétrica y posteriormente descifra el mensaje.

De esta forma se obtiene:
- **Confidencialidad**: Solo el receptor legítimo puede descifrar la clave simétrica.  
- **Integridad**: El mensaje no puede ser modificado sin invalidar el cifrado.

---

## Algoritmos de cifrado
Un **algoritmo de cifrado** es una función matemática que trabaja junto a una clave. El **principio de Kerckhoffs** establece que la **seguridad** de un sistema criptográfico debe radicar **exclusivamente** en la **clave**, no en el secreto del algoritmo. La “seguridad por oscuridad” se considera poco recomendable, ya que eventualmente se descubre la lógica interna del cifrado.

Se distinguen dos categorías principales:
- **Cifrado por bloques**: Divide la información en bloques de bits y cifra cada bloque de forma independiente.  
- **Cifrado de flujo**: Cifra bit a bit o byte a byte según se generan o leen los datos.

La **robustez** de un algoritmo depende en gran medida de la **longitud de la clave**. A mayor longitud, mayor dificultad para romperlo por fuerza bruta.

---

## Ejemplo de algoritmo de cifrado (RSA)
La **seguridad** del RSA se basa en la dificultad de la **factorización** de números grandes. A grandes rasgos, su funcionamiento es el siguiente:

1. Se eligen dos números primos grandes, *p* y *q*.  
2. Se calcula su producto \( n = p \times q \).  
3. Se calcula \(\phi(n) = (p-1) \times (q-1)\).  
4. Se elige un número \( e \) primo entre 1 y \(\phi(n)\). Este será parte de la **clave pública**.  
5. Se utiliza el **algoritmo extendido de Euclides** para hallar \( d \) (la **clave privada**).  
6. La **clave pública** se compone de \((n, e)\) y la **clave privada** de \((n, d)\).

Para **cifrar** un mensaje \( M \):  
\[
C = M^e \bmod n
\]  

Para **descifrar**:  
\[
M = C^d \bmod n
\]  

---

## Función resumen
También conocida como **función hash**, es una operación sobre un conjunto de datos de cualquier tamaño que produce un **resumen** o **huella digital** de longitud fija.

**Propiedades deseables**:
- **Ausencia de colisiones**: Dos documentos diferentes no deben generar el mismo valor hash.  
- **Unidireccionalidad**: Es imposible (o computacionalmente inviable) recuperar el documento original a partir de su hash.

Ejemplos populares: **MD5**, **SHA-1**, **SHA-256**, etc.

**Usos comunes**:
- **Verificación de integridad** de archivos.  
- **Almacenamiento de contraseñas** en forma de hash (en vez de texto plano).  
- **Firma digital** (combinarlo con cifrado de clave privada).

---

## Firma digital
Gracias al **cifrado asimétrico**, se pueden crear **firmas digitales**. Se basa en:
1. Cifrar el **resumen (hash)** del documento con la **clave privada** del firmante.  
2. Cualquier persona puede verificarlo con la **clave pública** correspondiente.

La firma digital **garantiza**:
- **Autenticación**: Solo el titular de la clave privada pudo generar esa firma.  
- **Integridad**: El más mínimo cambio en el documento altera su hash, invalidando la firma.  
- **No repudio**: El firmante no puede negar haber firmado el documento.

---

## Certificado digital
Un **certificado digital** es un documento electrónico que **asocia** una clave pública a su propietario (persona o entidad), conteniendo además información relevante sobre el mismo. Este certificado va **firmado** por una **Autoridad de Certificación (CA)** reconocida, que actúa como **tercera parte de confianza**.

En muchos casos, los certificados digitales se guardan en **tarjetas inteligentes**, para dificultar la extracción o copia de la clave privada.

---

## Terceras partes de confianza o Entidades certificadoras
Para validar la **autenticidad** de un certificado digital y evitar su falsificación, se recurre a terceras partes de confianza que sirven como **intermediarios**. Si dos usuarios confían en la misma entidad, pueden validar recíprocamente la legitimidad de sus certificados.

La entidad encargada de **emitir** certificados en un entorno de **clave pública** se denomina **Autoridad de Certificación (CA)**. En España, por ejemplo, existe la **Fábrica Nacional de Moneda y Timbre** (FNMT) como una de estas autoridades.

---

## Infraestructura de la clave pública (PKI)
La **PKI** (Public Key Infrastructure, o Infraestructura de Clave Pública) engloba el **conjunto de componentes** (software, hardware, procedimientos y políticas) necesarios para el uso de **certificados digitales** y **firmas electrónicas**.

**Servicios** que suele ofrecer una PKI:
- **Registro de claves**: Emitir un certificado nuevo para una clave pública.  
- **Revocación de certificados**: Anular un certificado emitido por causa justificada.  
- **Publicación de claves**: Poner a disposición las claves públicas de los usuarios.  
- **Evaluación de confianza**: Verificar si un certificado es válido y qué operaciones permite.  
- **Recuperación de claves**: Posibilidad de restaurar las claves de un usuario en caso necesario.

**Componentes** de una PKI:
- **Autoridad de Certificación (CA)**: Emite y revoca los certificados digitales.  
- **Autoridad de Registro (RA)**: Tramita solicitudes de certificados, verifica la identidad del solicitante y solicita su emisión a la CA.  
- **Autoridades de Repositorio**: Almacenan y publican certificados (emitidos o revocados).  
- **Otras terceras partes de confianza**: Ej. Autoridades de Fechado Digital.

---
