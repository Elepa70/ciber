---
title: Introduccion
description: Introduccion
published: true
date: 2025-01-18T18:05:43.829Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:05:43.829Z
---

# Introducción

## ¿Qué es la seguridad informática?
La **seguridad informática** consiste en el análisis, prevención, minimización y mitigación de riesgos en los sistemas informáticos. También puede entenderse como la disciplina que diseña normas, procedimientos y técnicas con el fin de mantener un sistema informático seguro.

---

## ¿La seguridad informática está de moda?
Debido a la digitalización de la vida cotidiana (tiendas online, banca online, etc.), la protección de datos y la prevención de posibles vulnerabilidades se han vuelto imprescindibles. No se trata simplemente de una moda, sino de una **necesidad** para garantizar el correcto funcionamiento y la confianza en los sistemas informáticos.

---

## Objetivos de la seguridad Informática
Los principales objetivos son:

1. **Confidencialidad**: Garantizar, mediante técnicas de control de acceso, que la información solo esté disponible para personas autorizadas.  
2. **Disponibilidad**: Asegurar que los datos o servicios estén siempre accesibles cuando se necesitan.  
3. **Integridad**: Garantizar que los datos no hayan sido modificados desde su creación sin autorización.  
4. **No repudio**:  
   - **No repudio en origen**: El emisor no puede negar que envió algo.  
   - **No repudio en destino**: El receptor no puede negar que recibió algo.

---

## Mecanismos utilizados para conseguir los objetivos de seguridad
Existen múltiples mecanismos, entre los cuales destacan:

- **Autenticación**: Para identificar al emisor o usuario.  
- **Autorización**: Para otorgar o restringir accesos a determinados recursos o zonas.  
- **Auditoría**: Para verificar el correcto cumplimiento de las políticas de seguridad.  
- **Cifrado**: Para proteger la confidencialidad de la información transmitida o almacenada.  
- **Firma Electrónica o Certificado Digital**: Para confirmar la identidad y evitar el no repudio.  
- **Copias de seguridad (Backups)**: Para recuperar datos ante pérdidas o desastres.  
- **Antivirus**: Para proteger ante software malicioso (virus, troyanos, etc.).  
- **Cortafuegos (Firewalls)**: Para filtrar conexiones y evitar accesos no deseados.  
- **Proxys**: Intermediarios que ayudan a controlar y auditar el tráfico entre redes internas y externas.  
- **Sistemas de alta disponibilidad**: Aseguran el funcionamiento continuo (24x365).  
- **Leyes de protección de datos**: Obligaciones legales que velan por la seguridad y privacidad de la información.

---

## Seguridad física y lógica

### Seguridad física
Se encarga de proteger el **hardware** frente a diferentes riesgos:

- **Incendios**: Uso de mobiliario ignífugo, ubicación del CPD en zonas de bajo riesgo, sistemas antiincendios.  
- **Inundaciones**: Colocar servidores en plantas no expuestas a filtraciones, impermeabilizar paredes y techos.  
- **Robos**: Implantar controles de acceso (biometría, contraseñas), cámaras de vigilancia y seguridad privada.  
- **Señales electromagnéticas**: Evitar la cercanía a zonas con elevada radiación. Si no fuera posible, emplear cableado o recubrimientos especiales.  
- **Apagones**: Utilizar Sistemas de Alimentación Ininterrumpida (SAI) y/o grupos electrógenos diésel.  
- **Sobrecarga eléctrica**: Empleo de SAIs con protección contra picos de tensión.  
- **Desastres naturales**: Construcciones resistentes a terremotos y réplica del CPD en otras localizaciones geográficas.  
- **Roturas o fallos de hardware**: Uso de hardware redundante.

### Seguridad Lógica
Orienta sus esfuerzos a la **protección del software** y los datos:

- **Robos de información**: Cifrado de datos, contraseñas y sistemas biométricos para accesos.  
- **Pérdida de información**: Copias de seguridad, discos redundantes y sistemas tolerantes a fallos.  
- **Pérdida de integridad**: Uso de firmas digitales, chequeo periódico de sistemas de archivos y herramientas de integridad.  
- **Virus y otros ataques maliciosos**: Uso de antivirus actualizados, cortafuegos, proxy, monitorización de la red.  
- **Modificaciones no autorizadas**: Contraseñas robustas, listas de control de acceso (ACL) y cifrado de documentos.

---

## Seguridad activa y pasiva

### Seguridad activa
Es el conjunto de medidas **preventivas**, diseñadas para **evitar** que se produzcan daños:

- **Uso de contraseñas** seguras.  
- **Listas de control de acceso** (ACL).  
- **Cifrado** de datos para evitar lecturas no autorizadas.  
- **Software de seguridad** (antivirus, antimalware, etc.).  
- **Firmas y certificados digitales**: Autenticidad e integridad de los mensajes.  
- **Cuotas de disco**: Limita el uso excesivo de almacenamiento por parte de ciertos usuarios.

### Seguridad pasiva
Conjunto de medidas enfocadas en **minimizar** el impacto una vez que ocurre un incidente:

- **Discos redundantes** (ej. RAID): Sustituyen automáticamente un disco dañado.  
- **Sistemas tolerantes a fallos** (redundancia de servidores, cableado, switches, cabinas de disco...).  
- **SAI**: Ante un corte eléctrico, garantiza el suministro temporal.  
- **Copias de seguridad**: Permiten restaurar el sistema al estado previo a un incidente.

---

## Tipos de Vulnerabilidades
Las **vulnerabilidades** son puntos débiles que pueden permitir accesos no autorizados o provocar fallos:

- **Vulnerabilidades ya conocidas**: Tienen solución o parche. Frecuentemente se publican en listas de correo y repositorios de seguridad.  
- **Vulnerabilidades desconocidas (Zero-Day)**: Todavía no han sido detectadas ni corregidas por los fabricantes. Si un atacante las descubre primero, puede explotarlas con fines maliciosos.

---

## Pen Testing o pruebas de penetración
Consisten en **evaluaciones controladas** para poner a prueba la seguridad de un sistema. Se realizan ataques simulados (conocidos como “white hat” o hacking ético) con el fin de:

- Localizar debilidades en la infraestructura.  
- Comprobar la eficacia de las medidas de seguridad existentes.  
- Evaluar el impacto potencial de un ataque real.

**Herramientas habituales**:
- **Nmap**: Escaneo de redes, detección de servicios y sistemas operativos.  
- **OpenVas / Nessus**: Escaneo de vulnerabilidades en servicios detectados.  
- **Metasploit**: Marco (framework) para ejecutar exploits una vez identificadas las vulnerabilidades.  
- **Kali Linux / Parrot**: Distribuciones de Linux con un amplio conjunto de herramientas de hacking ético.

El término **hardening** hace referencia al **proceso de securización de un sistema** (cerrar puertos innecesarios, corregir configuraciones inseguras, etc.).

---

## Mejorar la seguridad
Algunas recomendaciones para incrementar la seguridad de una organización:

1. **Identificar** los elementos críticos que se desean proteger.  
2. **Formar** al personal para concienciarlos sobre su importancia.  
3. Realizar un **estudio de vulnerabilidades** periódicamente.  
4. Elaborar y aplicar un **plan de actuación** (medidas de seguridad activa y pasiva).  
5. **Revisar** de manera continua la eficacia de estas medidas.

---

## Tipos de amenazas
Los sistemas informáticos están expuestos a una gran diversidad de amenazas. Entre ellas, se encuentran diferentes tipos de **malware** (código malicioso diseñado para dañar o provocar mal funcionamiento), que pueden perseguir distintos fines:  
- Causar daños generalizados.  
- Propagarse a gran velocidad.  
- Obtener un beneficio económico.

---

## EL CUADRO
### Tabla de principales amenazas

| **NOMBRE**    | **¿Qué es?**                                                                                                                   | **Efecto**                                                                                                  | **Forma de infección**                                                                    |
|---------------|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **Virus**     | Código malicioso que altera el funcionamiento de un equipo. Se ejecuta al abrir un archivo infectado.                          | - Alterar comportamiento del equipo <br>- Eliminar archivos personales <br>- Borrar el disco <br>- Propagarse a sí mismo | A través de archivos infectados o su ejecución voluntaria                                 |
| **Gusano**    | Código malicioso que se propaga a través de la red, consumiendo recursos.                                                      | - Problemas de rendimiento de la red <br>- Saturación de recursos                                            | - Auto-duplicación <br>- Archivos infectados <br>- Redes no protegidas                    |
| **Troyano**   | Código malicioso con apariencia inofensiva.                                                                                    | - Acceso a datos privados <br>- Creación de puertas traseras                                                 | Archivos que simulan ser legítimos                                                       |
| **Spyware**   | Software que monitorea hábitos y recopila información personal del usuario.                                                    | - Robo de información personal <br>- Posible venta o envío de datos                                          | Instalación junto a programas gratuitos o sitios maliciosos                               |
| **Spam**      | Correos o mensajes no deseados.                                                                                                | - Pérdida de tiempo <br>- Saturación de servidores                                                            | - Mensajería masiva (correo, foros, redes sociales)                                       |
| **Hoax / Bulos** | Mensajes con información engañosa o falsa.                                                                                 | - Pérdida de tiempo <br>- Saturación de servidores <br>- Daña la imagen (desinformación)                      | Mensajería (correo, redes sociales)                                                       |
| **Floods** (Inundaciones) | Envío masivo de información en un corto periodo.                                                                  | - Saturación de servidores <br>- Imposibilidad de acceder a un servicio                                      | Mensajería masiva, ataques organizados                                                   |
| **Jokes**     | Programas que simulan virus sin causar daño real.                                                                              | - Alarma o confusión al usuario <br>- Pérdida de tiempo                                                       | Descargas en páginas de poca confianza                                                  |
| **Pop-up**    | Ventanas emergentes molestas al navegar.                                                                                       | - Dificultan la navegación <br>- Pérdida de tiempo                                                            | Visitar páginas web con contenido malicioso o dudoso                                      |
| **Droppers**  | Programas que evitan la detección de antivirus, “disfrazando” la carga maliciosa.                                              | - Facilitan la posterior infección con malware                                                                | - Descarga desde páginas dudosas <br>- Correos electrónicos con adjuntos                  |
| **Spoofing**  | Suplantación de identidad (ej. IP, direcciones de correo).                                                                     | - Robo de credenciales <br>- Estafas y fraudes                                                                | Depende del tipo de spoofing (correo, IP, páginas falsas, etc.)                           |
| **Fake-news** | Noticias falsas que buscan confundir o manipular.                                                                              | - Desinformación <br>- Pérdida de tiempo                                                                      | Mensajería, redes sociales, correo                                                       |
| **Exploits**  | Programas que aprovechan vulnerabilidades específicas.                                                                         | - Diversos ataques según la vulnerabilidad (desbordamiento de búfer, escalada de privilegios, etc.)          | - Navegador <br>- Sistema operativo <br>- Software de aplicación                          |
| **Phishing**  | Bombardeo de mensajes falsos imitando a entidades legítimas.                                                                   | - Robo de datos confidenciales (usuario, contraseña, datos bancarios) <br>- Estafas y pérdidas económicas    | - Correos electrónicos <br>- Mensajes en redes sociales                                  |
| **Sniffer**   | Programa que monitoriza el tráfico de red.                                                                                     | - Robo de información confidencial                                                                            | - Escaneo de puertos <br>- Escucha activa en redes no cifradas                           |
| **Keyloggers**| Registra las pulsaciones del teclado.                                                                                          | - Robo de contraseñas y credenciales                                                                          | - Instalación como software malicioso <br>- Infección por troyanos                        |
| **DoS**       | Ataque de Denegación de Servicio basado en peticiones masivas a un recurso.                                                   | - Saturación de servicios <br>- Imposibilidad de acceso legítimo                                             | - Envío masivo de paquetes <br>- Escaneo de puertos y exploit para denegar recursos       |
| **Hijacking** | Secuestro de sesión, web, IP u otro recurso.                                                                                   | - Control del recurso por parte del atacante <br>- Robo de datos                                             | Visitar páginas dudosas, exploits específicos                                            |
| **Diccionario** | Ataques por fuerza bruta probando contraseñas comunes.                                                                      | - Obtención de credenciales                                                                                   | - Escaneo de puertos y uso de listas de contraseñas frecuentes                           |
| **Data miners**| Programas que recogen datos de navegación y uso para analizarlos sin consentimiento.                                          | - Obtención de hábitos y patrones del usuario                                                                 | Visitar sitios web que ejecutan scripts maliciosos                                       |
| **Pharming**  | Modificación maliciosa en servidores DNS o archivos “hosts” para redirigir a sitios falsos.                                    | - Robo de credenciales <br>- Estafas y pérdidas económicas                                                    | - Exploit en software DNS <br>- Manipulación del archivo “hosts”                         |
| **Ransomware**| Cifra los archivos del usuario y pide un rescate para su liberación.                                                           | - Pérdida de datos <br>- Pago de rescates <br>- Dañar económicamente                                          | Descargas de software malicioso, correos con adjuntos infectados                          |

---

## Leyes relacionadas

### Reglamento General de Protección de Datos (RGPD)
Es un reglamento de alcance **europeo** que garantiza la protección de las personas físicas en lo relativo al tratamiento de datos personales y la libre circulación de estos datos.

### Ley Orgánica de Protección de Datos Personales y garantía de los derechos digitales (LOPD GDD)
Ley de ámbito **nacional** (España) que desarrolla y complementa el RGPD, regulando el tratamiento de datos personales y reforzando los derechos digitales de la ciudadanía.

---
