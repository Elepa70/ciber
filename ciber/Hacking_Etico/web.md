---
title: Hacking de aplicaciones web
description: En este tema vamos a ver todo lo relacionado a Hacking Web
published: true
date: 2024-12-26T15:52:57.872Z
tags: hacking, web
editor: markdown
dateCreated: 2024-12-20T19:30:12.869Z
---

# Hacking de aplicaciones web
En este tema vamos a ver el protocolo HTTP y sus características a la seguridad. Se verán las principales vulnerabilidades mediante OWASP Top 10.
## Protocolo HTTP
HTTP (Hypertext Transfer Protocol, protocolo de transferencia de hipertexto), es un protocolo existente en la capa de aplicación usado para la transmisión de hipertextos (Contenido enriquecido con características especiales). 

Fue desarrollado por Tim Berners-Lee en el CERN en 1989. En su primera versión (HTTP/0.9), sólo admitía el método GET. Tras esto evolucionó al HTTP/1.0, el cual traería los métodos POST y HEAD, además de las cabeceras HTTP. El protocolo más tarde evolucionó a HTTP/2 en 2015 por SPDY, donde se buscaba una transmisión en binaria en vez de texto plano, y finalmente en 2021 saló la versión HTTP/3, con el protocolo QUIC para mejorar la velocidad y la seguridad integrando el TLS.

Este protocolo es cliente-servidor, y se realiza mediante peticiones, el cliente manda una petición (HTTP Request) al servidor que responderá con un (HTTP Response). El protocolo HTTP ha ido mejorando en versiones y se ha ido reforzando para ser más seguro y a ser más eficiente, es por ello que actualmente tenemos en desarrollo el protocolo HTTP 3.0, mientras que al principio teníamos la versión 1.1.

El cambio de versiones, provoca un cambio en las sintaxis, en cómo se establecen las conexiones o como se organizan las peticiones y respuestas. Sin embargo la semántica se ha ido manteniendo desde la versión 1.1.

Los métodos más comunes que conocemos son:
- GET: Solicitar recursos.
- HEAD: Similar a GET pero el servidor no devuelve los recursos dados, si no las cabeceras de respuesta.
- POST: Envíar datos.
- PUT: Reemplazar recursos.
- DELETE: Eliminar recursos.
- PATCH: Modificar parcialmente los recursos.
- OPTIONS: Describe opciones de comunicación.
- TRACE: Realiza una comunicación de prueba.
- CONNECT: Establece un túnel con el servidor identificado por el recurso solicitado.


El protocolo también trae una serie de indicadores para mostrar el estado de una petición que están organizadas en:
- 2XX Mensaje de éxito: 200 OK (Petición exitosa), 201 CREATED (Petición se ha completado y se ha creado el recurso)
- 3XX Mensaje de redirección: 301 Moved Permanently (EL recurso ha cambiado de ubicación a otra de forma permanente, se usa la respueta Location)
- 4XX Mensaje de error del cliente: 400 Bad Request (Error en la sintaxis de la petición), 403 Forbidden (El servidor no quiere dar respuesta a la petición y 404 Not Found (No se ha encontrado el recurso)
- 5XX Mensaje de error del servidor: 500 Internal Server Error (Error genérico del servidor)

### HTTP cookies
HTTP es por diseño un protocolo sin estado, es decir, no es capaz de identificar si una petición viene de un usuario o otro, ni cuantas peticiones hace cada uno.

Esto genera problema en cuanto a las sesiones y conexiones establecidas, es decir, cómo puede verificar el servidor que el usuario activo es quien ha colocado la contraseña o si no es otra petición que le haya llegado justo en ese momento. Para poder resolver este problema se desarrollaron las Cookies. 

Las cookies funcionan en las cabeceras de HTTP de la siguiente manera:
1. El cliente cuando envía por primera vez una petición al servidor, este lo que hace es responder con un Set-Cookie, para poder establecer una cookie que use.
2. El cliente recibe la cookie y ya hace una comunicación con el servidor de forma normal y con el uso de la cookie que le fue ofrecida, esta cookie la tendremos en la cabecera HTTP a nombre de Cookie.

Cuando el servidor envía la cookie, puede hacerlo además con varios atributos especiales. Estos atributos especiales son:
- Fecha de expiración (Expires): Indica cuándo caduca la cookie, cuando la cookie caduca, se deja de enviar al servidor.  Esto provoca la existencia de dos tipos de cookies, las de sesión que se eliminan cuando el cliente se cierra y las permanentes que se eliminan cuando pasa el tiempo.
- Dominio (Domain): Indica los dominios específicos donde esta cookie es efectiva. Si no se especifica, sólo podrá ser usada únicamente en el dominio donde se recoge.
- Path: Es una ruta existente en la URL de la petición para poder enviar la cookie.
- Atributos de seguridad: Existen varias opciones para establecer aún más seguridad, como puede ser los atributos SameSite, HttpOnly, Secure etc etc...

El formato que tiene una cabecera con la Cookie es:
Set-Cookie: \Cookies>=<Cookies\>; Expires=\<Expires>; Domain=\<Dominio>; Path=\<path>; Atributos de seguridad
## Seguridad en HTTP
La principal iniciativa de seguridad es HTTPs, el cúal es el mismo protocolo de HTTP sin embargo, se le añade un túnel cifrado de extremo a extremo entre el cliente y el servidor, esto propone para al cliente varios servicios básicos:
- Cifrado de las comunicaciones.
- Certificar la identidad del servidor.
- Integridad de los datos, para confirmar que no han sido modificados por un tercero.

Para que este túnel sea posible, se usa el protocolo TLS (Transport Layer Security), que es la evolución del SSL (Secure Socket Layer).
SSL llegó a ver la versión 3.0, sin embargo por numerosas vulnerabilidades, en 1990 se define el TLS 1.0 con el RFC 2246, la versión actual o más reciente de este protocolo es el 1.3 (RFC 8846).

Ambos protocolos se basan en el PKI (Public Key Infraestructure), donde un certificado TLS, firmado por autoridades de certificación, otorga dos claves: una pública y otra privada. Es un cifrado híbrido donde la clave pública se usa para compartir una clave de sesión, con la que tanto cliente como servidor cifran la comunicación.

El protocolo TLS actúa justo después de la conexión TCP para iniciar una comunicación HTTP desde el cliente. En este momento tanto servidor como cliente negocian:
- Versión de TLS a usar
- El cliente envía las claves públicas por parte del servidor
- Verificar la clave con una entidad certificadora
- Generar las claves de sesión con las que cifrar. 

Esta es la norma general, pero puede variar según la versión de TLS.

Esta seguridad de TLS se complementa con otros mecanismos añadidos por el protocolo HTTP.


### Cabeceras de seguridad
En HTTP hay un conjunto de cabeceras de petición y respuesta orientadas a mejorar la seguridad de la transferencia. Vamos a repasar el uso seguro de HTTP Cookies y el funcionamiento de CORS (HTTP Access Control).

Herramientas de análisis, pueden detectar como vulnerable la falta de estas etiquetas, sin embargo, es importante que el pentester verifique manualmente si realmente es una vulnerabilidad, ya que muchas funciones de estas cabeceras de seguridad pueden chocar directamente con la función del servidor.

El protocolo envía una cabecera HTTP con el formato que vimos anteriormente:
Set-Cookie: \<Cookies>=<Cookies\>; Expires=\<Expires>; Domain=\<Dominio>; Path=\<path>; Atributos de seguridad

La primera línea es para el atributo Path y Domain, ya que permite restringir dónde se enviará esa cookie. Sin embargo, se dispone además de los llamados atributos de seguridad, que permiten indicar características para proteger la cookie. Estos protocolos son SameSite, Secure y HTTPOnly.

- Atributo SameSite: Antes de la aparición de este protocolo, el navegador enviaba todas las cookies que fueron enviadas por ese servidor independientemente si esa solicitud fue realizada por otro dominio. Para evitar esto, se desarrolló el atributo SameSite, donde se controla el comportamiento de estas cookies con: None (Siempre envía todas las cookies al servidor), Lax (El navegador enviará las cookies si es mediante una petición GET y si fue porque el usuario hizo click) y Strict (El navegador no enviará las cookies en solicitudes Cross-Site, que no sean mismo dominio, mismo protocolo y mismo puerto).
Set-Cookie: \<Cookies>=<Cookies\>; SameSite=Strict/Lax/None

- Atributo Secure: Si está presente indica que la cookie solo puede ser enviada con una comunicación segura como HTTPs.
Set-Cookie: \<Cookies>=<Cookies\>; Secure
- Atributo HttpOnly: Evita que el cliente pueda acceder a la cookie mediante Javascript, ya que delimita que la cookie pueda ser recibida mediante Http.
Set-Cookie: \<Cookies>=<Cookies\>; HttpOnly
### HTTP Access Control (CORS)
CORS es un protocolo de seguridad empleado por los navegadores, cuando se intenta solicitar un recurso de un origen distinto al origen del primer recurso solicitado. 

Imaginamos que entramos en el dominio A, en este dominio no hay ningún problema ya que descargamos todos los archivos y todas las cosas, sin embargo este dominio tiene partes del dominio B, esto provoca que el Navegador tenga que acudir al dominio B a recibir esa información, esto se denomina Cross-origin request.

Normalmente los navegadores tienen un protocolo denominado Same-Origin-Policy, donde el navegador no debe confiar en recursos cargados desde orígenes arbitrarios distintos al del recurso de la petición original.

Sin embargo es muy común encontrarse dominios donde recoja recursos ubicados en otros dominios, aquí es donde entra en juego CORS para verificar que todas las solicitudes son legítimas. Una petición CORS la puede realizar diferentes elementos HTML:
- Invocación a través de scripts XMLHttpRequest o mediante la API Fetch
- Fuentes para la web cargadas desde sitios externos.
- Texturas WebGL
- Imágenes y vídeo dibujados en un canvas mediante drawImage().
- Formas CSS desde imágenes.

En cuanto el navegador detecta una solicitud Cross-origin, se comprueba las cabeceras CORS para autorizar o no la petición, estas cabeceras pueden ser: simples o verificadas/preflighted.

Las solicitudes simples son aquellas que cumplen los siguientes requisitos:
- El método HTTP es Get, Post o Head.
- La petición HTTP se pueden añadir manualmente: Accept, Accept-Language, Content-Language, Content-Type y Range.
- La cabecera Content-Type, de estar presente, solo puede tomar algunos de los valores como: application/x-www-form-url-enconded, multipart/form-data o text/plain.

En esta situación el navegador simplemente enviará la cabecera HTTP Origin en la solicitud indicando el origen del recurso principal y tras eso, mirará la cabecera de respuesta Access-Control-Allow-Origin, dependiendo de su valor lo aceptará o lo bloqueará.

Los valores de la cabecera Access-Control-Allow-Origin pueden ser:
- "*" : Comodín indicando que desde cualquier origen.
- Origen específico: Solo se puede compartir a ese origen.

En las solicitudes preflighted, debe ser cuando no se produzcan ninguna de las condiciones de las simple, es decir:
- Se usa otro método como puede ser PUT o Delete
- Se incluye alguna cabecera que no estaba en la lista de cabeceras permitidas.
- La cabecera Content-Type no tiene un valor mencionado anteriormente.
- Se adjuntan credenciales a la solicitud.

En este caso se establecen varias comunicaciones entre cliente y servidor. El navegador en cuanto interpreta que necesita recursos externos a él, hace una petición al servidor de forma especial preguntando solo las cabeceras, si el servidor lo ve seguro le devuelve las cabeceras que acepta y es entonces cuando el navegador decide interpretar si aceptar o no.

### Ataques a HTTP
Las aplicaciones y servidores web emplean en muchas ocasiones las cabeceras de petición y respuesta HTTP para proveer de la funcionalidad necesaria al servicio. Si estas cabeceras no están bien usadas, puede dar a ataques del tipo: HTTP Host Header Injection, HTTP Request/Response Splitting y HTTP Request Smuggling.
## OWASP
La organización OWASP (Open Web Application Security Project), es una fundación sin ánimo de lucro apoyada por multitud de empresas e instituciones educativas y particulares de todo el mundo. El objetivo es la mejora y seguridad del software.

Su aportación a la seguridad web, está recogida en proyectos, donde pueden ser herramientas, documentos, librerías, material de referencia o metodologías, todos ellos de código abierto y desarrollado por la comunidad, algunos de los proyectos más populares son:
- ASVS (Application Security Verification Standard): Estándar de seguridad web basado en listas de requisitos y test.
- OWASP SAMM (Software Assurance Maturity Model): Modelo de madurez de software que proporciona las herramientas y medios para que una organización analice y adopte de manera progresiva una cultura de la seguridad en todos sus procesos.
- OWASP ZAP: Herramienta de seguridad gratuita y de código libre para el pentesting.
- OWASP Juice Shop: Aplicación web insegura para el entrenamiento y aprendizaje de hacking web.
- OWASP WSTG: Es una guía para testear la seguridad de las aplicaciones y los servicios web.
- OWASP MSTG: Manual para pruebas de seguridad de aplicaciones móviles e ingeniería inversa.

Además tiene desarrollado OWASP Top 10, que vamos a ver a continuación.
### OWASP Top 10
El proyecto OWASP Top 10, recopila las 10 categorías de vulnerabilidades más importantes presentes en aplicaciones web. Se renueva con cierta periodicidad, siendo la última versión de 2021 (Fecha Junio 2023).

Este top se hace mediante los datos cedidos por empresas de seguridad por todo el mundo desde un año en específico (en este caso 2017) y se va haciendo un recuento de cada CWE (Common Weakness Enumeration) presente en cada aplicación.  Tras eso se pondera las CVSS de los CVE  asociados a los CWE encontrados, y con ello se hacen las primeras 8 categorías. Las dos últimas, son vulnerabilidades antiguas bastante importantes votadas por la comunidad de OWASP, esto sirve para dar a luz antiguas vulnerabilidades y recordar lo que pasó y cómo se mejoró.

Para poder interpretar las 10 vulnerabilidades más comunes según OWASP, es necesario conocer una serie de términos:
- CWE mapeadas: Cantidad de números CEW asignados a la categoría.
- Tasa de incidencia: Porcentaje de población de aplicaciones que tiene una instancia de un tipo de vulnerabilidad.
- Impacto ponderado: Ponderación que se hace basado en la puntuación de impactos CVSS de los CVE asignados.
- Explotabilidad ponderada: Igual que el impacto ponderado pero con la puntuación de CVSS
- Cobertura de las pruebas: Porcentaje de aplicaciones analizadas por cada organización para una determinada vulnerabilidad
- Total de ocurrencia: Total de aplicaciones en la que se ha encontrado alguna ocurrencia de CWE asociado.

Ahora vamos a describir brevemente cada vulnerabilidad de OWASP Top 10 2021.
#### AO1:2021 Broken Access Control (Pérdida de control de acceso)
Consiste en que el usuario puede realizar acciones que no deberían estar asignadas, vulnerabilidades comunes:
- CWE-35: Path Traversal.
- CWE-352: Cross-Site Request Forgery (CSRF)
- CWE-284: Improper Access Control.
#### AO2:2021 Cryptographic Failures (Errores criptográficos)
Consiste en la exposición de datos confidenciales o del compromiso del sistema por parte de un fallo criptográfico, vulnerabilidades asociadas:
- CWE-328: Use of Weak Hash
- CWE-261: Weak Encoding for Password
- CWE-326: Inadequate Encryption Strength
#### AO3:2021 Injection (Inyección)
Las vulnerabilidades de este estilo, surgen cuando no se sanean la entrada de usuario sin codificar los parámetros y permitiendo su modificación o cuando es posible.
- CWE-89: Inyección SQL
- CWE-78: Inyección de comandos de sistemas operativos
- CWE-79: XSS
#### AO4:2021 Insecure design (Diseño inseguro)
Existe debido a un mal diseño de la aplicación, vienen por diseño de software. Vulnerabilidades comunes son:
- CWE-653: Aislamiento o compartición inadecuados.
- CWE-656: Confianza en la seguridad por oscuridad.
#### AO5:2021 Security Misconfiguration (Configuración de seguridad incorrecta)
Relacionado con deficiencias o insuficiencias en la configuración del software del entorno. Puede ser ocasionado por falta de bastionado, dejar habilitadas funciones innecesarias, no enviar cabeceras o directivas de seguridad.
- CWE-260 Contraseñas en ficheros de configuración
- CWE-1004: Cookie sensible
- 
#### AO6:2021 Vulnerable and Outdated Components
Esta categoría hace referencia al riesgo al que se expone una aplicación debido a un componente por no estar suficientemente actualizado. Podemos encontrar:
- CWE-1104: Uso de componentes de terceros sin mantener
#### AO7:2021 Identification and Authentication Failures (Fallos en identificación y autenticación)
Aquí contemplamos los ataques relacionados con la identidad, la autenticación y la gestión de sesiones de usuarios. Como puede ser permitir ataques de fuerza bruta, contraseñas débiles o bien conocidas. DEbemos encontrar:
- CWE-613: Expiración insuficiente de sesión
- CWE-620: Cambios de contraseña sin verificar
#### AO8:2021 Software and Data Integrity Failures (Fallos en el software y en la integridad de los datos)
Las vulnerabilidades de está categoría es por el uso de plugins o aplicaciones no confiables que puede permitir un acceso no autorizado a atacantes. Podemos encontrar:
- CWE-829: Inclusión de funcionalidad de terceros no confiables
- CWE-494: Descarga de código sin verificación de integridad
- CWE-502: Deserialización de datos no confiables.
#### AO9:2021 Security Logging and Monitoring Failures
Trata de deficiencias en el monitoreo y registro del sistema, provocando una lenta actuación del equipo de seguridad y no pudiendo realizar bien la funciones, ya que están ciegos ante ataques.
#### A10:2021 Server-Side Request Forgery (SSRF)
Está dedicado a la vulnerabilidad a una única debilidad:
- CWE-918: Server-Side Request Forgery
