---
title: Introducción al hacking ético
description: Primer tema de la asignatura "Hacking Ético"
published: true
date: 2024-11-04T18:37:11.586Z
tags: 
editor: markdown
dateCreated: 2024-10-29T11:54:23.119Z
---

# Introducción al hacking ético
Bienvenido al primer tema de esta asignatura. Este primer tema nos sirve para poder introducir y aprender conceptos generales de seguridad y terminologías del mismo campo.
También se explicarán los distintos tipos de amenazas existentes y cómo realizar una auditoría.

## Historia
Empecemos por el principio. La palabra **hackers** viene de los primeros pioneros informáticos que buscaban dar soluciones rápidas a problemas.

Al principio la tecnología evolucionó rápidamente, provocando que varias universidades estadounidenses tengan una red conectada entre sí. Y esto evolucionó hasta la posibilidad de conectarse a Internet mediante el uso de líneas telefónicas que eran muy lentas y a su vez muy caras. Fue en este momento donde surgieron el **phreaking**, que será piratear las comunicaciones telefónicas para realizar llamadas gratuitas o conectarse a internet de forma ilimitada. 

Debido a la ilegalidad que esto supondría, comenzó a surgir una **subcultura underground**, donde los jóvenes usaban **nicknames** para ocultar su identidad. Algunos llegaron a ser detenidos como es el caso de:
- Loyd Blankenship: Conocido como The Mentor, miembro de Legion of Doom. Publicó libros como Conscience of a Hacker.
- John T. Drapper: Conocido como Captain Crunch, usaba silbatos vendidos en cereales que imitaban el mismo tono de frecuencia que las líneas telefónicas, para hacer llamadas gratuitas.
- Vladimir Levin: El primer hacker en robar un banco desde internet, accediendo a Citibank y haciendo transferencias por valor de 10 millones de dólares.
- Kevin Poulsen: Conocido como Dark Dante. Manipulaba las llamadas de los concursos telefónicos para ganar.
- Kevin Mitnick: Uno de los hackers más famosos, ya que estuvo dentro de los sistemas de la NASA y el Departamento de Defensa de los Estados Unidos. 

### En España
En España, también surgió esta cultura underground mencionada anteriormente, y viene correctamente resumida en el libro de Mercè Molist Ferrer, llamado La historia nunca contada del underground hacker en la península ibérica. En el libro se pueden ver los foros, métodos y acciones más relevantes sobre los primeros hackers ibéricos. 

### Ciberdelincuencia actual
La delincuencia ha crecido enormemente desde el COVID-19, ya que durante estos años de pandemia, el uso de dispositivos electrónicos se ha disparado. Es por ello que si observamos cualquier tabla, podemos ver como hay un enorme aumento de delitos informáticos durante esta época. Esto podemos ver en la siguiente tabla

(Insertar imagen o gráfico de estadísticas de ciberdelitos (oedi.es)

Ejemplo de grandes hackeos están a la orden del día como puede ser en octubre de 2021 a la plataforma multimedia Twitch, o un ataque de ransomware al CSIC (Consejo Superior de Investigaciones Científicas). Uno de los peores que han afectado a España, es el uso del software espía Pegasus, que ha afectado a los teléfonos del Gobierno de España.

El uso de Ransomware, malware que cifra toda la información y no se devuelve hasta que no se haga un rescate, provoca que las empresas cedan ante los ciberdelincuentes provocando que no haya freno. Esto viene dado porque las empresas, muy a menudo, no tienen ningún plan de securización o protección de los datos. Es por ello que existen órganos o empresas, como AEPD (Agencia Española de Protección de Datos), que dictaminan una serie de reglas y obligaciones para la protección de datos personales. También es encargado de sancionar a aquellas empresas que no realicen o cumplan las reglas.

Debido a todo esto, la demanda del profesional formado en ciberseguridad ha crecido enormemente hasta llegar a la cifra de 83.000 puestos necesarios según INCIBE (Instituto Nacional de Ciberseguridad de España).

## Conceptos básicos
Ahora comenzaremos a describir los conceptos más básicos de la ciberseguridad, y para ello necesitamos definir dos términos primordiales:
- Seguridad: Es aquella ausencia de peligro, daño o riesgo.
- Información: Conjunto organizado de datos que forman un mensaje.

Por lo tanto, la seguridad de la información sería aquel conjunto de medidas de prevención, detección y corrección. Estas tres palabras tendrán importancia más adelante ya que son los principios de la seguridad de la información.

Actualmente existen dos tipos de seguridades:
- Seguridad defensiva: Serían aquellas medidas encargadas de proteger la información y recursos de la organización.
- Seguridad ofensiva: Será totalmente lo contrario, consiste en intentar vulnerar los controles de seguridad y poner en riesgo alguno de los principios mencionados. 

Es normal que las empresas tengan tanto equipo de seguridad defensiva como ofensiva, ya que para intentar arreglar una vulnerabilidad, es necesario primero encontrarla. 

### Principios de la seguridad de la información
Desde un punto de la vista de la información hay tres principios básicos para garantizar su seguridad:
- Confidencialidad: Encargado de garantizar que la información sólo puede ser conocida por las personas autorizadas.
- Integridad: Encargado de que la información no sea alterada o modificada sin permisos o de forma accidental.
- Disponibilidad: Garantiza que la información es accesible siempre que los usuarios autorizados la necesiten.

A estos principios básicos, podemos añadir dos principios esenciales, siempre y cuando la información sea compartida por distintos medios. Estos son:
- Autenticación: Garantizar quién es la persona que ha realizado la información, mediante factores de autenticación (Contraseñas). Esto nos sirve para saber que realmente esa persona ha sido quien ha enviado el mensaje.
- No repudio: Ni el emisor (No repudio de origen) ni el receptor (No repudio de destino), pueden negar que la información ha sido enviada.

### Clasificación de las medidas de seguridad
Existen una serie de medidas para la seguridad de la información, estas medidas se pueden diferenciar en distintos criterios.
Al momento de actuación.
- Seguridad activa: Consiste en aquellas que previenen algún daño en un sistema informático. Ejemplo, un Firewall
- Seguridad pasiva: Medidas capaces de reparar o minimizar un daño producido en un sistema informático. Ejemplo, copias de seguridad.

También tenemos en función al elemento a proteger:
- Seguridad física: Consiste en la protección del hardware. Ya sea provocado o por desastres naturales.
- Seguridad lógica: Medidas que tratan de proteger el software de los datos de los sistemas informáticos. 
### Hacking: definición y aspectos legales
La RAE define Hacker o Jáquer como:
- Pirata informático que accede ilegalmente a un sistema informático ajeno.
- Persona con grandes habilidades en el manejo de computadoras.

Esta última definición habilita la labor del hacker ético. Ya que solo había una visión puramente negativa aunque exista la labor del hacker ético.

La clasificación dentro de los hackers depende de sus intenciones:
- White hat hacker: Tiene como intención mejorar la seguridad, buscando agujeros de seguridad e informando a los encargados. Este profesional es contratado por una empresa u organización y tiene permisos para buscar vulnerabilidades y fallos.
- Black hat hacker: Es un ciberdelincuente, donde usa sus conocimientos para fines negativos o dañinos.
- Gray hat hacker: Es un hacker que está entre ambos casos anteriores, esto puede ser dado por distintos valores: Hacktivistas (Grupos que realizan las acciones de hackeo para logar a un proposito definido, normalmente aultruista), personas se sombrero blanco que deja un acceso para ellos, personas con sombrero negro que buscan y denuncian determinados delitos.

También existen los script kiddies, personas sin conocimientos ni habilidades que atacan a los sistemas por herramientas creadas por hackers. 

En el código penal español se recoge los siguientes artículos respecto a un hacker:
- Artículo 197 bis.1. El que por cualquier medio o procedimiento, vulnera la seguridad establecidas y sin estar debidamente autorizado, acceda a un sistema informático.
- Artículo 197 bis.2. Mediante el uso de artificios o instrumentos sin estar autorizado, intercepte transmisiones no públicas de datos informáticos.
- Artículo 197 ter. Será castigado con pena de prisión o multa a aquel que sin autorización produzca, adquiera, importe o facilite la comisión de algunos de los delitos mencionados anteriormente.

Aquí podemos observar la grandísima importancia que recae en la autorización expresa para poder ser un buen hacker ético. Ya que aunque se haga sin maldad, cabe la posibilidad de que la empresa o organización tome medidas en contra de la persona autora de los hechos. 

## Amenazas a la seguridad de la información
Una amenaza, en el ámbito de la seguridad de la información, es cualquier suceso que atenta contra el buen funcionamiento del sistema y puede afectar a los activos. MAGERIT (Metodología de Análisis y Gestión de Riesgos para los Sistemas de Información), establece una serie de tipos de amenazas:
- De origen natural: Accidentes naturales como terremotos o inundaciones.
- Del entorno: Cortes de suministro o contaminación.
- Defectos de las aplicaciones: Fallos o vulnerabilidades en los sistemas por errores.
- Causadas por las personas de forma accidental: Ingeniería social.
- Causadas por las personas de forma deliberada: Ataques de unas personas de forma deliberada para obtener algún beneficio.

### Tipos de intrusos y motivaciones
Anteriormente hemos descrito que hay varios tipos de hackers según sus intenciones, ahora toca el apartado para los distintos tipos de intrusos. Estos son:
- Cracker: Busca provocar daños y obtener beneficios de forma ilegal.
- Phreaker: Busca acceder a Internet de forma gratuita.
- Spammer: Realiza envío masivo de mensajes de correo electrónico.
- Lamer: Es aquel hacker sin conocimientos expandidos en el tema que intenta aprender. Se le puede decir también wannabe o script-kiddie.
- Insider: Persona que trabaja dentro de una empresa y busca su desbeneficio.
- Ex Empleado: Antiguo trabajador con motivación similar a Insider.
- Hacktivist: Busca relevancia política mediante lucha contra injusticias o protección de derechos humanos. 
- State-Sponsored hacker: Ciberdelincuentes que trabajan para una nación o Estado. 

### Código dañinos: Malware
Un malware es aquel programa informático que ha sido desarrollado para introducirse en un sistema. Los más comunes son los robos de la información, pérdida de datos o espionaje.
Existe una gran cantidad de forma de propagación de malware, desde programas que vengan en un archivo comprimido con contraseña, tiendas de aplicaciones, oculto en ficheros (Stegomalware, oculto en imágenes o videos),fireless o in-memory malware entre otros (Malware que solo existen en el momento de ejecución).

La clasificación de los malwares es bastante amplio, tenemos lo siguiente:
- Exploit: Malware que aprovecha vulnerabilidades del software para comprometer el sistema, su acción maliciosa se conoce como Payload.
- Virus: Existe una gran cantidad de virus, pero su función es reproducirse y propagarse para hacer el máximo impacto posible.
- Ransomware: Una vez infectado un sistema, encripta la información y solicita un rescate. 
- Spyware: Recopila actividad que realiza el usuario.
- Adware: Malware que muestra constantemente anuncios.
- Troyano: Programa que deja una puerta abierta a los atacantes.
- Rootkit: Malware que proporciona acceso y control remoto del equipo infectado.
- Keylogger: Registra todas las teclas pulsadas en el sistema, logrando obtener contraseñas.
- Gusano: Busca su autopropagación en la red.
- Bacteria: Busca reproducirse para consumir memoria.
- Bomba lógica: Malware oculto hasta el momento de la ejecución.
- Cryptojacking: Malware que minar criptomonedas. 

Alguno de los malwares existentes fueron: Brain, Stoned, Jerusalem o Viernes 13, Gusano de Morris, Michelangelo, Concept, Laroux, AccesiB, Strange Brew, Chernobyl o CIH, Melissa, Loveletter o I Love You, Stuxnet o WannaCry.

### Tipos de ataques
Existen numerosos tipos de ataques, y según descrito por INCIBE, tenemos: 
- Ataque a contraseñas: El objetivo es obtener las credenciales de acceso a un sistema. Ya sea mediante fuerza bruta (Probar 1 a 1 la contraseña) o con diccionarios de contraseñas existentes en la red.
- Ataques de Ingeniería social: Usa la manipulación de los usuarios mediante el engaño. Aquí los más comunes son: Fraude Online, Phishing, vishing, smishing, baiting, shoulder surfing (Mirar por encima del ojo) o dumpster diving (Rebuscar en la basura).
- Ataques a las conexiones: Consiste en ataques que se realizan a las redes que están interconectadas. Los más comunes son: Ataques DDoS (denegación de servicio), Man in the Middle (Estar en medio), Spoofing (Suplantación), Sniffing (Escucha de conexiones) y Redes Trampa.
- Ataques a la cadena de suministro: Busca una vulnerabilidad en el hardware o software que pertenece a un tercero y es usado por la compañía objetivo. 
- Ataques invisibles en el código fuente: Se hace uso de código invisible para los editores de textos, para cambiar la funcionalidad del software. 

Todos estos ataques son altamente peligrosos y para evitarlo, se implanta un modelo llamado Zero Trust Security, donde se desconfía de todos siempre y todo se comprueba.


### Vulnerabilidades
Una vulnerabilidad o bug, es un fallo de diseño que pertenece a un sistema poniendo en riesgo su funcionamiento. El primer bug, pertenece a la universidad de Harvard, donde se coló una polilla o bicho en uno de los relés del computador. 

Hoy en día este tipo de vulnerabilidades es bastante más distintos a este que hemos mencionado anteriormente. Estas nuevas vulnerabilidades, vienen de un fallo provocado por el diseño o implementación del software, debido a que un sistema informático se comporta por Software y Hardware, podemos diferenciar entre:
- Vulnerabilidad de Software: Afectan a los programas informáticos y ocurren habitualmente, por errores de programación en su código fuente. Debemos revisar no solo el software que usemos, si no que aplicaciones de tercero usa, ya que es posible que mediante el uso de alguna de estas aplicaciones de tercero, nuestro equipo corra riesgo. 

- Vulnerabilidades hardware: En este caso el atacante requiere tener acceso al equipo en físico para poder saltarse todas los niveles de seguridad y crear daños. 

Existen plataformas como Zerodium, que ofrecen recompensas para las personas que encuentren alguna vulnerabilidad, con un ranking de precios o pagos según la vulnerabilidad.

Para clasificar una vulnerabilidad se hace uso del CVE (Common Vulnerabilities and Exposures), es un sistema que ofrece un identificador numérico a una vulnerabilidad de seguridad, se compone de tres elementos:
- CVE
- XXXX -> El año correspondiente
- YYYY -> Número de la vulnerabilidad.

Es por ello que la vulnerabilidad CVV-2024-2000, pertenece al año 2024 y es la vulnerabilidad 2000 de ese mismo año. Las vulnerabilidades son medidas en el CVSS (Common Vulnerability Scoring System), este sistema hace uso de una serie de métricas en diferentes.

Dentro de las vulnerabilidades del CVSS podemos encontrar:
- Attack Vector: Como se realiza el ataque
- Attack Complexity: DIficultad del ataque
- Privileges Required: Requisitos mínimos
- User Interaction: Interacción del usuario o administrador.
- Scope: Capacidad de saltar a otras aplicaciones.
- Confidencialidad: Si afecta a este aspecto de la seguridad.
- Integridad: Si afecta a este aspecto de la seguridad.
- Disponibilidad: Si afecta a este aspecto de la seguridad.

## Test de intrusión o pentest
Los test de intrusión son acciones legítimas de hackers que intentan hacerse del control de un sistema. En este test, se analiza los estados de seguridad de los servicios de una empresa, para la búsqueda activa de vulnerabilidades que puedan ser utilizadas en contra de la empresa.
Después de este test, se presenta un informe con el test a la empresa o corporaciones para que modifiquen o reparen la seguridad.

Hay varios tipos de auditorías en los test de intrusión:
- Auditoría de caja negra: El hacker no tiene conocimiento de la organización.
- Auditoría de caja blanca: El hacker tiene acceso completo a la organización, sirve principalmente para revisar software o configuraciones.
- Auditoría de caja gris: El auditor tiene conocimiento parcial donde se intenta acceder a otro lado con permisos limitados.

También se puede medir con respecto a la situación de los recursos:
- Auditoría perimetral: El auditor asume un papel de hacker buscando una forma de acceso a los sistemas internos.
- Auditoría interna: El hacker tiene rol de empleado y se realiza desde dentro.
- Auditoría interna con privilegios: El auditor tiene total permiso.

Y por último según los servicios o recursos que quieren ser auditados:
- Auditoría web: La seguridad de una página web.
- Auditoría de aplicaciones web: Conoce el grado de seguridad de la empresa a nivel de app.
- Auditoría wireless y VoIP: Permite el conocimiento de estados de seguridad de comunicaciones inalámbricas.
- Prueba de estrés DoS/DDoS: Se comprueba la resistencia a altas cargas.

Partiendo de estas formas de evaluar, la empresa decide que quieren comprobar y nosotros nos adaptamos a este tipo de auditoría.
### Fases de un test de intrusión
Existen numerosas formas de realizar un test de intrusión, a continuación veremos la forma más generales de estos test:
1. Fase de reconocimiento o footprinting: En este punto intentamos recoger toda la información posible de forma completamente externa.
1. Fase de enumeración o fingerprinting: Aquí ya empezamos a actuar con el activo en búsqueda.
1. Fase de explotación: En este punto con la información recopilada en ambas fases anteriores, comenzamos a intentar vulnerar la aplicación buscando el vector de ataque.
1. Fase de posexplotación: Se comprueban los privilegios que poseen y analizar el sistema una vez ya accedido a los sistemas del objetivo. 
1. Fase de documentación: Se debe elaborar un informe con los detalles recogidos anteriormente, se suele realizar dos documentos uno para los directivos y otro para el personal IT.

Los ciberdelincuentes realizan un papel similar excluyendo la última parte donde se instala herramientas como rootkits para mantener el acceso dentro de la aplicación o dispositivo.

### Contrato de test de intrusión
En el contrato del test de intrusión, es donde se establecen las reglas respecto a la auditoría. Estas reglas suelen venir regidas por las siguientes preguntas:
- ¿En qué horario debe realizarse el pentest? ¿Hay servicios críticos donde la carga de trabajo no puede superar un cierto umbral?
- ¿Se van a realizar pruebas de denegación de servicio?
- ¿Está permitida la Ingeniería social a empleados?
- ¿El personal de la organización o el personal de IT tendrá conocimiento del test?
- ¿Está permitido instalar backdoors o usar exploits peligrosos?

### Metodologías de pentesting
Existen una gran cantidad de metodologías elaboradas como referencia para ayudar con la calidad de los procesos. Se recomienda consultar páginas como Web Security Testing Guide, para poder elaborar un buen documento. El documento está enfocado a la auditoría de aplicaciones web.

A continuación se va a explicar de forma extensa las metodologías más utilizadas.

#### PTES (Penetration Testing Execution Standard)
Esta metodología fue realizada alrededor del 2009, donde todavía está en fase 1.0, y se espera la salida de la 2.0. En esta metodología encontramos siete fases:
1. Interacciones previas: Se ofrece información sobre aspectos como estimación de tiempo y coste, básicamente el contrato.
2. Recopilación de inteligencia: En esta fase se intenta obtener información del objetivo más valiosa, donde se pueden establecer tres niveles: L1 donde se obtiene información sin esfuerzo, L2 donde se puede obtener información con el uso de herramientas del primer nivel y L3 donde se busca información del objetivo mediante herramientas más elaboradas.
1. Modelado de amenazas: En esta fase se elabora un modelo de amenazas identificando aquellos activos que la empresa prefiere proteger.
1. Análisis de vulnerabilidades: Se buscan los fallos en los sistemas que pueden ser aprovechados por el atacante.
1. Explotación: Busca tener el acceso a los sistemas de la organización, evitando cualquier restricción de seguridad.
1. Posexplotación: En esta fase se debe valorar el sistema comprometido y garantizar accesos a futuros. 
1. Informe: Redacción de lo realizado y obtenido.

#### OSSTMM (Open Source Security Testing Methodology Manual)
Fue publicada en el 2001 y actualmente está en su versión 3.0, publicada en diciembre de 2010.
En esta metodología se hace uso del estándar rav, para medir la exposición de la empresa. Esta medida se representa de dos maneras:
- Valor positivo o negativo, donde el positivo indica exceso de controles y el negativo falta de controles.
- Mide lo mismo que antes, se mide mediante el uso de un logaritmo en base 10 donde el 100 es la medida de balance perfecta. 

Esta metodología tiene 5 canales que son los siguientes:
- Seguridad humana: Consiste en cubrir aquellas interacciones con las personas, como puede ser ingeniería social.
- Seguridad física: Se mide la forma de vulnerar mediante elementos físicos en el sistema.
- Seguridad en las comunicaciones inalámbricas: En este canal se cubre comunicaciones del objetivo en un rango de proximidad cercano.
- Seguridad en las telecomunicaciones: Es todo aquello con respecto a red cableada y comunicaciones telefónicas o digitales.
- Seguridad en las redes de datos: Cubre las comunicaciones entre redes de computadoras y sistemas operativos en red.

La ejecución de esta metodología está en 4 fases que son:
1. Fase de inducción: La auditoría comienza con la compresión de requisitos, ámbito y restricciones.
2. Fase de interacción: Donde se conocen los diferentes sistemas e interacciones entre ellos.
3. Fase de encuesta: Donde el auditor descubre información desconocida.
4. Fase de intervención: Última fase de la auditoría para probar la penetración de los servicios.

#### Metodologías del OWASP (Open Web Application Security Project)
OWASP (Open Web Application Security Project) dispone de tres grandes guías para la evaluación de seguridad según la aplicación.
- OWASP Web Security Testing Guide (WSTG): Será vista en el apartado 4. Está completamente dedicado a las aplicaciones web y a sus auditorías.

- OWASP Mobile Application Security Testing Guide (MASTG): Es un manual para realizar las pruebas de seguridad e ingeniería inversa de aplicaciones móviles.
- OWASP Firmware Security Testing Methodology (FSTM): Firmware responsable del funcionamiento del funcionamiento de cualquier dispositivo embebido, y se busca securizar el acceso no autorizado.

#### Otras metodologías
Es interesante conocer algunas otras metodologías, se describirán brevemente:
- PCI DSS (Payment Card Industry Data Security Standard): Protege los sistemas de pago.
- PTF (Penetration Testing Framework): Recoge información útil con respecto al pentesting.
- NIST SP 800-115 (Technical Guide to Information Security and Assessment): Aquí se recogen recomendaciones prácticas, para diseñar e implementar las medidas de seguridad en nuestras aplicaciones.
- CAF (The Cyber Assessment Framework): Diseñado por el NCSC (National Cyber Security Center) de Reino Unido.

### Equipos de seguridad
Suele haber dos equipos de seguridad:
- Red Team: Realiza las labores de seguridad ofensivas.
- Blue Team: Realiza las labores defensivas.

Los Red Team siempre intentarán continuamente vulnerar las defensas de los sistemas de información, para poder tener acceso o provocar algún tipo de daño. Es por ello que el trabajo del Blue Team es que no tengan éxito, y así trabajar en conjunto en una perfecta o buena forma de proteger los sistemas.

Actualmente ha empezado a surgir el Purple Team, que busca la unión de ambos teams. También se ha empezado a surgir otro tipo de teams como Yellow (Builders o los desarrolladores de sistemas), Orange (Mezcla entre Red Team y Yello) o el Green (Mezcla entre Red Team y Yellow).

## Cómo convertirse en hacker
En este apartado se van a haber algunos consejos y laboratorios para poder aprender a convertirse en hacker. Hay que tener en cuenta que no es un trabajo sencillo, puesto que debes tener un gran conocimiento de todas las cosas, y para ello es necesario tener bastante experiencia. De momento vamos a comenzar con la descripción de un buen hacker o ciber investigador:
- Arquitectura de computadoras y lenguaje ensamblador: Son aquellos elementos del funcionamiento hardware y software de los sistemas informáticos.
- Redes de ordenadores y protocolos de red: Diferentes tipos de arquitectura, tipos de redes, dispositivos de las redes de comunicaciones, protocolos TCP/IP y OSI.
- Administrador de sistemas operativos: Instalar, configurar, elementos, permisos, roles y administrador de servicios en sistemas operativos.
- Gestión y administración de base de datos: Conocer los diferentes lenguajes de modelos de datos, diferentes sistemas gestores de bases de datos, estructura y comandos de administración.
- Lenguajes de programación: Conocimiento en lenguajes tanto bajo nivel (C, C + +), orientados a objetos (Java), aplicaciones móviles (Android), tecnologías web (javascript) o scripting (Powershell).
- Criptografía: Conocimiento de los funcionamientos algoritmos criptográficos y aplicación práctica.

Es importante tener una base en todos los aspectos anteriores, ya que será difícil poder avanzar sin conocimiento previo de esto. 

### Capture The Flag
Uno de los mejores métodos para aprender, es mediante el uso de retos en capturar la bandera, donde se deja un código oculto (FLAG), que sirve para demostrar que has conseguido vulnerar la máquina. Existen una series de reglas como, no mostrar la solución para que todo el mundo intente conseguirlo por metodología propia. 

Existen tres tipos de categorías:
- Retos (Challenges): Suelen consistir en un tipo de habilidad técnica o vulnerabilidad concreta. Suelen ser los más comunes en retos o challenges. 
- Máquinas (Boxes): Consiste en explotar una máquina a través de algún servicio vulnerable o mal configurado.
- Redes: Es un entorno que simula una red empresarial con distintas máquinas y se intenta pivotar entre las máquinas.

Para realizar estos retos disponemos de una grandísima cantidad de sitios webs donde se pueden realizar como: Atenea, Academia Hacker, Una al mes, Pico CTF, CTF Time, Hack The Box, Try hack me, VulnHub HackMyVM o Proving Ground entre otras.

También es posible buscar tanto información como youtubers que tengan amplios conocimientos en el tema, por ello podremos ver guías como: The Journey to Try Harder to The Cyber Mentor. Entre otros youtubers interesantes a observar tenemos: Ipsec, John Hammond, Live Overflow, HackerSploit, s4vitar, Hack4u etc etc

### Certificados de ciberseguridad
Hay una grandísima cantidad de certificaciones de ciberseguridad, donde las más importantes son: CEH, PenTest +, eJPT, eCPPT, HTB CpTS, PNPT, OSCP. 

### Bug bounty
Los bug bounty son recompensas proporcionadas por las organizaciones a aquellas personas que logren encontrar un bug en sus sistemas. Sin embargo, algunas plataformas intermediarias también existen para hacer este servicio, en el que encontramos: Bugcrowd, HackerOne, Integrity, Immunefi.

### Herramientas para el pentesting
Se recomienda el uso de Kali Linux, ParrotOS, BlackArch o CommandoVM para hacer pruebas de pentesting, ya qué estas herramientas suelen traer muchos software con la misma finalidad.

### Mantenerse informado
Para poder estar informado, es necesario tener conocimiento de en qué páginas webs podremos encontrar todo, por ello se recomienda acudir a sitios web como: una al día, un informático en el lado del mal, flu project, hackplayers, the hacker way, hacking articles, google project zero o ars technica. 

Además de sitios web. Existen numerosas conferencias donde se hablan sobre temas de ciberseguridad donde encontramos: BlackHat, DEFCON, RootedCON, Navaja Negra, DragonJar, H-CON, No cON Name, Congreso C1b3rWall o Jornadas STIC del CCN-CERT.



En el libro se habla de realizar una serie de prácticas como Reto básico en la plataforma de Atenea o prácticas en Hack The Box.
El contenido está disponible bajo Dominio público, por Pablo Sánchez Hidalgo. | Con la tecnología de Wiki.js

