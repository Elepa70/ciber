---
title: Introducción al hacking ético
description: Primer tema de la asignatura "Hacking Ético"
published: true
date: 2024-11-03T11:00:26.550Z
tags: 
editor: markdown
dateCreated: 2024-10-29T11:54:23.119Z
---

# Introducción al hacking ético
Bienvenido al primer tema de esta asignatura. Este primer tema nos sirve para poder introducir y aprender conceptos generales de seguridad y terminologias del mismo campo.
También se explicarán los distintos de amenazas existente y como realizar una auditoría.

## Historia
Empecemos por el principio. La palabra **hackers** viene de los primeros pioneros informaticos que buscaban dar soluciones rapidas a problemas.

Al principio la tecnologia evoluciono rapidamente, provocando que varias universidades estadounidensas tengan una red conectada entre si. Y esto evoluciono hasta la posibilidad de conectarse a Internet mediante el uso de lineas telefonicas que eran muy lenta y a su vez muy caras. Fue en este momento donde surguieron el **phreaking**, que erá piratear las comunicaciones telefonicas para realizar llamadas gratuitas o conectarse a internet de forma ilimitada. 

Debido a la ilegalidad que esto supondría, comenzó a surgir una **subcultura underground**, donde los jovenes usaban **nicknames** para ocultar su identidad. Algunos llegarón a ser detenidos como es el caso de:
- Loyd Blankedship: Conocido como The Mentor, miembro de Legion of Doom. Publico libros como Consciene of a Hacker.
- John T. Drapper: Conocido como Captain Crunch, usaba silbatos vendidos en cereales que imitaban el mismo tono de frecuencia que las lineas telefonicas, para hacer llamadas gratuitas.
- Vladimir Levin: El primer hacker en robar un banco desde internet, accediendo a Citibank y haciendo transferencias por valor a 10 millones de dólares.
- Kevin Poulsen: Conocido como Dark Dante. Manipulaba los llamadas de los concursos telefonicos para ganar.
- Kevin Mitnick: Uno de los hackers mas famosos, ya que estuvo dentro de los sistemas de la NASA y el Departamento de Defensa de los Estados Unidos. 

### En España
En España, también surguió esta cultura underground mencionada anteriormente, y viene correctamente resumida en el libro de Mercè Molist Ferrer, llamado La historia nunca contada del underground hacker en la península ibérica. En libro se puede ver los foros, metodos y acciones mas relevantes sobre los primeros hackers ibericos. 

### Ciberdelincuencia actual
La delincuencia ha crecido enormemente desde el COVID-19, ya que durante estos años de pandemia, el uso de dispositivos electronico se ha disparado. Es por ello que si observamos cualquier tabla, podemos ver como hay un enorme aumento de delitos informaticos durante esta epoca. Esto podemos ver en la siguiente tabla

(Insertar imagen o grafico de estadisticas de ciberdelitos (oedi.es)

Ejemplo de grandes hackeos están a la orden del día como puede ser en octubre de 2021 a la plataforma multimendia Twitch, o un ataque de ransomware al CSIC (Consejo Superior de Investigaciones Científicas). Uno de los peores que han afectado a España, es el uso del software espía Pegasus, que ha afectado a los telefonos del Gobierno de España.

El uso de Ransomware, malware que cifra toda la información y no se devuelve hasta que no se haga un rescate, provocá que las empresas cedan ante los ciberdelincuentes provocando que no haya freno. Esto viene dado porque las empresas, muy amenudo, no tiene ningún plan de securización o protección de los datos. Es por ello que existen organos o empresas, como AEPD (Agencia Española de Protección de Datos), que dictimina una serie de reglas y obligaciones para la protección de datos personales. También es encargado de sancionar a aquellas empresas que no realicen o cumplan las reglas.

Debido a todo esto, la demanda del profesional formado en ciberseguridad ha crecido enormenmente hasta llegar a la cifra de 83.000 puestos necesarios según INCIBE (Instituto Nacional de Ciberseguridad de España).

## Conceptos básicos
Ahora comenzaremos a describir los conecptos mas básicos de la ciberseguridad, y para ello necesitamos definir dos terminos primoridales:
- Seguridad: Es aquella ausencia de peligro, daño o riesgo.
- Información: Conjuto organizado de datos que forman un mensaje.

Por lo tanto, la seguridad de la información sería aquel conjunto de medidas de prevención, detección y correción. Estas tres palabras tendrán importancia adelante ya que son los principios de la seguridad de la información.

Actualmente existen dos tipos de seguridades:
- Seguridad defensiva: Serían aquellas medidas encargadas de proteger la información y recursos de la organización.
- Seguridad ofensiva: Será totalmente lo contrario, consiste en intentar vulnerar los controles de seguridad y poner en riesgo alguno de los principios mencionado. 

Es normal que las empresas tengan tanto equipo de seguridad defensiva como ofensiva, ya que para intentar arreglar una vulnerabilidad, es necesario primero encontrarla. 

### Principios de la seguridad de la información
Desde un punto de la vista de la información hay tres principios básicos para garantizar su seguridad:
- Condifencialidad: Encargado de garantizar que la información solo puede ser conocida por las personasa autorizadas.
- Integridad: Encargado de que la información no sea alterada o modificada sin permisos o de forma accidental.
- Disponibilidad: Garantiza que la información es accesible siempre que los usuarios autorizados la necesiten.

A estos principios básicos, podemos añadirle dos principios esenciales, siempre y cuando la información sea compartida por distintos medios. Estos son:
- Autenticación: Garantizar quien es la persona que ha realizado la información, mediante factores de autenticación (Contraseñas). Esto nos sirve para saber que realmente esa persona ha sido quien ha enviado el mensaje.
- No repudio: Ni el emisor (No repudio de origen) ni el receptor (No repudio de destino), pueden negar que la información ha sido enviada.

### Clasificación de las medidas de seguridad
Existen una serie de medidas para la seguridad de la información, estas medidas se pueden diferenciar en distintos criterios.
Al momento de actuación.
- Seguridad activa: Consiste en aquellas que previenen algún daño en un sistema informatico. Ejemplo, un Firewall
- Seguridad pasiva: Medidas capaces de reparar o minimar un daño producido en un sistema informatico. Ejemplo, copias de seguridad.

También tenemos en función al elemento a proteger:
- Seguridad física: Consiste en la protección del hardware. Ya sea provocado o por desastres naturales.
- Seguridad lógica: Medidas que tratan de proteger el software de los datos de los sistemas informáticos. 
### Hacking: definición y aspectos legales
La RAE define Hacker o Jáquer como:
- Pirata informatico que accede ilegalmente a un sistema informático ajeno.
- Persona con grandes habilidades en el manejo de computadoras.

Esta ultima definición habilita la labor del hacker ético. Ya que solo había una visión puramente negativa aunque exista la labor del hacker ético.

La clasificación dentro de los hackers depende de sus intenciones:
- White hat hacker: Tiene como intención mejorar la seguridad, buscando abugueros de seguridad y informando a los encargados. Este profesional es contratado por una empresa u organización y tiene permisos para buscar vulnerabilidades y fallos.
- Black hat hacker: Es un ciberdelincuente, donde usa sus conocimientos para fines negativos o dañinos.
- Gray hat hacker: Es un hacker que está entre ambos casos anteriores, esto puede ser dado por distintos valores: Hacktivistas (Grupos que realizan las acciones de hackeo para logar a un proposito definido, normalmente aultruista), personas se sombrero blanco que deja un acceso para ellos, personas con sombrero negro que buscan y denuncian determinados delitos.

También existen los script kiddies, personas sin conicimentos ni habilidades que atacan a los sistemas por herramientas creadas por hackers. 

En el código penal español se recoge los siguientes artículos respecto a un hacker:
- Artículo 197bis.1. El que por cualquier medio o procedimiento, vulnera la seguridad establecidas y sin debidamente estar autorizado, acceda a un sistema de informatico.
- Artículo 197nis.2. Mediante el uso de artificios o instrumentos sin estar autorizado, intercepte trasmisiones no publicos de datos infromaticos.
- Articulo 197ter. Será castiago con pena de prisión o multa a aquel que sin autorización produzca, adquiera, importe o facilite la comision de algunos de los delitos mencionado anteriormente.

Aquí podemos observar la grandisima importancia que recae la autorización expresa para poder ser un buen hacker ético. Ya que aunque se haga sin maldad, cabe la posibilidad de que la empresa o organización tome medidas en contra de la persona autora de los hechos. 

## Amenazas a la seguridad de la información
Una amenaza, en el ambito de la seguridad de la información, es cualquier suceso que atenta contra el buen funcionamiento del sistema y puede afectar a los activos. MAGERIT (Metodología de Análisis y Gestión de Riesgos para los Sistemas de Información), establece una serie de tipos de amenazas:
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
- Insider: Persona que trabaja dentro de una empresa y busca su desbenificio.
- Exempleado: Antiguo trabajador con motivación similar a Insider.
- Hacktivist: Busca relevacia política mediante lucha contra injusticias o protección de derechos humanos. 
- State-Sponsored hacker: Ciberdelicuentes que trabajan para una nación o Estado. 

### Código dañinos: Malware
Un Malware es aquel programa informático que ha sido desarrollado para introducirse en un sistema. Lo mas comunes son lo robos de la información, pérdida de datos o espionaje.
Existe una gran cantidad de forma de propagación de malware, desde programas que vengan en un archivo comprimido con contraseña, tiendas de aplicaciones, oculto en ficheros (Stegomalware, oculto en imagenes o videos),fireless o in-memmory malware entre otros (Malware que solo existen en el momento de ejecución).

La clasificación de los malwares es basante amplio, tenemos lo siguiente:
- Exploit: Malware que aprovecha vulnerabilidades del software para compremeter el sistema, su acción maliciosa se conoce como Payload.
- Virus: Existe una gran cantidad de virus, pero su funcion es reproducirse y propragarse para hacer el maximo impacto posible.
- Ransomware: Una vez infecta un sistema, encripta la información y solicita un rescate. 
- Spyware: Recopila actividad que realiza el usuario.
- Adware: Malware que muestra constantemente anuncios.
- Troyano: Programa que deja una puerta abierta a los atacantes.
- Rootkit: Malware que proporciona acceso y control remoto del equipo infectado.
- Keylogger: Registra toda las teclas pusada en el sistema, logrando obtener contraseñas.
- Gusano: Busca su autopropagación en la red.
- Bacteria: Busca reproducirse para consumir memoria.
- Bomba lógica: Malware oculto hasta el momento de la ejecución.
- Cryptojacking: Malware que mina criptomonedas. 

Alguno de los malwares existentes fueron: Brain, Stoned, Jerusalem o Viernes 13, Gusano de Morris, Michelangelo, Concept, Laroux, AccesiV, Strange Brew, Chernobyl o CIH, Melissa, Loveletter o I Love You, Stuxnet o WannaCry.

### Tipos de ataques
Existe númerosos tipos de ataques, y según descrito por INCIBE, tenemos: 
- Ataque a contraseñas: El objetivo es obtener las credenciales de acceso a un sistema. Ya sea mediante fuerza bruta (Probar 1 a 1 la contraseña) o con diccionarios de contraseñas existentes en la red.
- Ataques de Ingeniería social: Usa la manipulación de los usuarios mediante el engaño. Aquí los más comunes son: Fraude Online, Phising, vishing, smishing, baiting, shoulder surfing (Mirar por encima del ojo) o dumpster diving (Rebuscar en la basura).
- Ataques a las conexiones: Consiste en ataques que se realizan a las redes que estan interconectadas. Los más comunes son: Ataques DDoS (denegación de servicio), Man in the Middle (Estar en medio), Spoofing (Suplantación), Sniffing (Escucha de conexiones) y Redes Trampa.
- Ataques a la cadena de suministro: Busca una vulnerabilidad en el hardware o software que pertenece a un tercero y es usado por la compañia objetivo. 
- Ataques invisibles en el código fuente: Se hace uso de código invisible para los editores de textos, para cambiar la funcionalidad del software. 

Todos estos ataques son altamente peligrosos y para evitarlo, se implanta un modelo llamado Zero Trust Security, donde se desconfia de todos siempre y todo se comprueba.


### Vulnerabilidades
Una vulnerabilidad o bug, es un fallo de diseño que pertenece a un sistema poniendo en riesgo su funcionamiento. El primer bug, pertenece a la universidad de Harvard, donde se coló una polilla o bicho en uno de los relés del computador. 

Hoy en dia este tipo de vulnerabilidades es bastante mas distintos a este que hemos mencionado anteriormente. Estas nuevas vulnerabilidades, vienen de un fallo provocado por el diseño o implementación del software, debido a que un sistema informatico se comporta por Software y Hardware, podemos diferenciar entre:
- Vulnerabilidad de Software: Afectan a los programas informáticos y ocurren habitualmente, por errores de programación en su código fuente. Debemos revisar no solo el software que usemos, si no que aplicaciones de tercero usa, ya que es posible que mediante el uso de alguna de estas aplicaciones de tercero, nuestro equipo corra riesgo. 

- Vulnerabilidades hardware: En este caso el atacante requiere tener acceso al equipo en fisico para poder saltarse todas los niveles de seguridad y crear daños. 

Existen plataformas como Zerodium, que ofrecen recompensas para las personas que encuentre alguna vulnerabilidad, con un ranking de precios o pagos según la vulnerabilidad.

Para clasificar una vulnerabilidad se hace uso del CVE (Common Vulnerabilities and Exposures), es un sistema que ofrece un identificador numérico a una vulnerabilidad de seguridad, se compone de tres elementos:
- CVE
- XXXX -> El año correspendiente
- YYYY -> Número de la vulnerabilidad.

Es por ello que la vulnerabilidad CVV-2024-2000, pertenecerá al año 2024 y es la vulnerabilidad 2000 de ese mismo año. Las vulnerabilidades son medidas en el CVSS (Common Vulnerability Scoring System), este sistema hace uso de una serie de métricas en diferentes.

Dentro de las vulnerabilidades del CVSS podemos encontrar:
- Attack Vector: Como se realizá el ataque
- Attack Complexity: DIficultad del ataque
- Privileges Required: Requisitos minimos
- User Interaction: Interaccion del usuario o administrador.
- Scope: Capacidad de saltar a otras aplicaciones.
- Confidencialidad: Si afecta a este aspecto de la seguridad.
- Integridad: Si afecta a este aspecto de la seguridad.
- Disponibilidad: Si afecta a este aspecto de la seguridad.

## Test de instrusión o pentest
Los test de intrusión son acciones legítimas de hackers que intentan hacerse el control de un sistema. En este test, se analiza los estados de seguridad de los servicios de una empresa, para la busqueda activa de vulnerabilidades que puedan ser utilizadas en contra de la empresa.
Después de este test, se presenta un informe con el test a la empresa o corporaciones para que modifiquen o reparen la seguridad.

Hay varios tipos de auditorias en los test de intrusión:
- Auditoría de caja negra: El hacker no tiene conocimiento de la organización.
- Auditoría de caja blanca: El hacker tiene acceso completo a la organización, sirve principalmente para revisar software o configuraciones.
- Auditoría de caja gris: El auditor tiene conocimiento parcial donde se intenta acceder a otro lado con permisos limitados.

Tambien se puede medir con respecto a la situación de los recursos:
- Auditoría perimetral: El auditor asume un papel de hacker buscando una forma de acceso a los sistemas internos.
- Auditoria interna: El hacker tiene rol de empleado y se realiza desde dentro.
- Auditoria interna con privilegios: El auditor tiene total permiso.

Y por ultimo según los servicios o recursos que quieren ser auditados:
- Auditoría web: La seguridad de una pagina web.
- Auditoría de aplicaciones web: Conoce el grado de seguridad de la empresa a nivel de app.
- Auditoría wireless y VoIP: Permite el conocimiento de estados de seguridad de comunicaciones inalambricas.
- Prueba de estrés DoS/DDoS: Se comprueba la resistencia a altas cargas.

Partiendo de estas formas de evaluar, la empresa decide que quieren comprobar y nosotros nos adaptaremos a este tipo de auditoria.
### Fases de un test de intrusión
Existen numerosas formas de realizar un test de intrusión, a continuación veremos la forma más generales de estos test:
1. Fase de reconocimento o footprinting: En este punto intentamos recoger toda la información posible de forma completamente externa.
1. Fase de enumeración o fingerprinting: Aquí ya empezamos a actuar con el activo en busqueda.
1. Fase de explotación: En este punto con la información recopilada en ambas fases anteriores, comenzamos a intentar vulnerar la aplicación buscando el vector de ataque.
1. Fase de posexplotación: Se comprueban los privilegios que poseen y analizar el sistema una vez ya accedido a los sistemas del objetivo. 
1. Fase de documentación: Se debe elaborar un informe con los detalles recogidos anteriormente, se suele realizar dos documentos uno para los directivos y otro para el personal IT.

Los ciberdelincuentes realizan un papel similar excluyendo la ultima parte donde se instalá herramientas como rootkits para mantener el acceso dentro de la aplicación o dispositivo.

### Contrato de test de intrusión
En el contrato del test de intrusión, es donde se establecen las reglas respecto a la auditoría. Estas reglas suelen venir regidas por las siguientes preguntas:
- ¿En qué horario debe realizarse el pentest? ¿Hay servicios críticos donde la carga de trabajo no puede superar un cierto umbral?
- ¿Se van a realizar pruebas de denegación de servicio?
- ¿Está permitida la Ingeniería social a empleados?
- ¿El personal de la organización o el personal de IT tendrá conocimiento del test?
- ¿Está permitido instalar backdoors o usar exploits peligrosos?

### Metodologías de pentesting
Existen una gran cantidad de metodologias elaboradas como referencia para ayudar con la calidad de los procesos. Se recomienda consultar a páginas como Web Security Testing Guide, para poder elaborar un buen documento. El documento está enfocado a la auditoría de aplicaciones web.

A continuación se va a explicar de forma extensa las metódologias mas utilizadas.

#### PTES (Penetration Testing Execution Standard)
Esta metódologia fue realizada alrededor del 2009, donde todavía esta en fase 1.0, y se esperá la salida de la 2.0. En esta metodología encontramos siete fases:
1. Interacciones previas: Se ofrece información sobre aspectos como estimación de tiempo y coste, basicamente el contrato.
2. Recopilación de inteligencia: En esta fase se intenta obtener información del objetivo más valiosa, donde se pueden establecer tres niveles: L1 donde se obtiene información sin esfuerzo, L2 donde se puede obtener información con el uso de herramientas del primer nivel y L3 donde se busca información del objetivo mediante herramientas más elaboradas.
1. Modelado de amenazas: En esta fase se elabora un modelo de amenazas identificando aquellos activos que la empresa prefiera proteger.
1. Análisis de vulnerabilidades: Se buscan los fallos en los sistemas que pueden ser aprovechados por el atacante.
1. Explotación: Busca tener el acceso a los sistemas de la organización, evitando cualquier restricción de seguridad.
1. Posexplotación: En esta fase se debe valorar el sistema comprometido y garantizar accesos a futuros. 
1. Informe: Redacción de lo realizado y obtenido.

#### OSSTMM (Open Source Security Testing Methodology Manual)
Fue publicada en el 2001 y actualmente esta en su versión 3.0, publicada en diciembre de 2010.
En esta metodología se hace uso del estadar rav, para medir la exposición de la empresa. Esta medida se representa de dos maneras:
- Valor positivo o negativo, donde el positivo indica exceso de controles y el negativo falta de controles.
- Mide lo mismo que antes, se mide mediante el uso de un logaritmo en base 10 donde el 100 es la medida de balance perfecta. 

Esta metodologia trae 5 canales que son los siguientes:
- Seguridad humana: Consiste en cubrir aquellas interacciones con las personas, como puede ser ingeneria social.
- Seguridad física: Se mide la forma de vulnerarlo mediante elementos físicos en el sistema.
- Seguridad en las comunicaciones inalámbricas: En este canal se cubre comunicaciones del objetivo en un rango del proximidad cercano.
- Seguridad en las telecomunicaciones: Es todo aquello con respecto a red cableada y comunicaciones telefonicas o digitales.
- Seguridad en las redes de datos: Cubre la comunicaciones entre redes de computadoras y sistemas operativos en red.

La ejecución de esta metodología está en 4 fases que son:
1. Fase de inducción: La auditoría comienza con la compresión de requisitos, ámbito y restricciones.
2. Fase de interración: Donde se conocen los diferentes sistemas y interacciones entre ellos.
3. Fase de encuesta: Donde el auditor descubra información desconocida.
4. Fase de intervención: Última fase de la auditoría para probar la penetración de los servicios.

#### Metodologías del OWASP (Open Web Application Security Project)
OWASP (Open Web Application Security Project) dispone de trés grandes guías para la evaluación de seguridad según la aplicación.
- OWASP Web Security Teting Guide (WSTG): Será vista en el apartado 4.