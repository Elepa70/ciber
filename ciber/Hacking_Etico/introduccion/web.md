---
title: Hacking de aplicaciones web
description: En este tema vamos a ver todo lo relacionado a Hacking Web
published: true
date: 2024-12-15T12:12:18.202Z
tags: hacking, web
editor: markdown
dateCreated: 2024-12-05T16:41:03.095Z
---

# Hacking de aplicaciones web
En este tema vamos a ver el protoclo HTTP y sus caracteristicas a la seguridad. Se verán las principales vulnerabilidades mediante OWASP Top 10.
## Protocolo HTTP
HTTP (Hypertext Transfer Protocol, protocolo de transferencia de hipertexto), es un protocolo existente en la capa de aplicación usado para la transmisión de hipertextos (Contenido enriquecido con carácteristicas especiales).

Este protocolo es cliente-servidor, y se realiza mediante peticiones, el cliente manda una petición (HTTP Request) al servidor que responderá con un (HTTP Response). El protocolo HTTP ha ido mejorando en versiones y se ha ido reforzando para ser más seguro y a ser mas eficiente, es por ello que actualmente tenemos en desarrollo el protocolo HTTP 3.0, mientras que al principio teniamos la version 1.1.

El cambio de versiones, provoca un cambio en las sintaxis, a como se establecen las conexiones o como se organizan las peticiones y respuestas. Sin embargo la semantica se ha ido manteniendo desde la version 1.1.

### HTTP cookies
HTTP es por diseño un protocolo sin estado, es decir, no es capaz de identificar si una petición viene de un usuario o otro, ni cuantas peticiones hace cada uno.

Esto genera problema en cuanto al las sesiones y conexiones establecidas, es decir, como puede verificar el servidor que el usuario activo es quien ha colocado la contraseña o si no es otra petición que le haya llegado justo en ese momento. Para poder resolver este problema se desarrollaron las Cookies. 

Las cookies funcionan en las cabeceras de HTTP de la siguiente manera:
1. El cliente cuando envia por primera vez una petición al servidor, este lo que hace es responderle con un Set-Cookie, para poder establecer una cookie que use.
2. El cliente recibe la cookie y ya hace una comunicación con el servidor de forma normal y con el uso de la cookie que le fue ofrecida, esta cookie la tendremos en la cabecera HTTP a nombre de Cookie.

Cuando el servidor envia la cookie, puede hacerlo a demás con varios atributos especiales. Estos atributos especiales son:
- Fecha de expiración (Expires): Indica cuando caduca la cookie, cuando la cookie caduca, se deja de enviar al servidor.  Esto provoca la existencia de dos tipos de cookies, las de sesión que se eliminan cuando el cliente se cierra y las permanentes que se eliminan cuando pasa el tiempo.
- Dominio (Domain): Indica los dominios especificos donde esta cookie es efectiva. Si no se especifica, solo pordra ser usada unicamente en el dominio donde se recogio.
- Path: Es una ruta existente en la URL de la petición para poder enviar la cookie.
- Atributos de seguridad: Existen varias opciones para establecerle aun mas seguridad, como puede ser los atributos SameSite, HttpOnly, Secure etc etc...

El formato que tiene una cabecera con la Cookie es:
Set-Cookie: \Cookies>=<Cookies\>; Expires=\<Expires>; Domain=\<Dominio>; Path=\<path>; Atributos de seguridad
## Seguridad en HTTP
La principal iniciativa de seguridad es HTTPs, el cúal es el mismo protocolo de HTTP sin embargo, se le añade un túnel cifrado de extremo a extremo entre el cliente y el servidor, esto propone para al cliente varios servicios básicos:
- Cifrado de las comunicaciones.
- Certificar la identidad del servidor.
- Integridad de los datos, para confirmar que no han sido modificados por un tercero.

Para que este túnel sea posible, se usa el protocolo TLS (Transport Layer Security), que es la evolución del SSL (Secure Socket Layer).
SSL llegó a ver la versión 3.0, sin embargo por númerosas vulnerabilidades, en 1990 se define el TLS 1.0 con el RFC 2246, la versión actual o más reciente de este protocolo es el 1.3 (RFC 8846).

Ambos protocolos se basan en el PKI (Public Key Infraestructure), dnde un certificado TLS, firmado por autoridades de certificación, otorga dos claves: una pública y otra privada. Es un cifrado híbrido donde la clave pública se usa para compartir una clave de sesión, con la que tanto cliente como servidor cifran la comunicación.

El protocolo TLS actúa justo después de la conexión TCP para iniciar una comunicación HTTP desde el cliente. En este momento tanto servidor como cliente negocian:
- Versión de TLS a usar
- El cliente envia las claves publicas por parte del servidor
- Verificar la clave con una entidad certificadora
- Generar las claves de sesión con las que cifrar. 

Esta es la norma general, pero puede variar según la versión de TLS.

Esta seguridad de TLS se complementea con otros mecanismos añadidos por el protocolo HTTP.
### Cabeceras de seguridad
En HTTP hay un conjunto de cabeceras de petición y respuesta orientadas a mejorar la seguridad de la transferencia. Vamos a repasar el uso seguro de HTTP Cookies y el funcionamiento de CORS (HTTP Access Control).

Herramientas de analisis, pueden detectar como vulnerable la falta de estas etiquetas, sin embargo, es importante que el pentester verifique manualmente si realmente es una vulnerabilidad, ya que muchas funciones de estas cabeceras de seguridad pueden chocar directamente con la función del servidor.

El protocolo envía una cabecera HTTP con el formato que vimos anteriormente:
Set-Cookie: \Cookies>=<Cookies\>; Expires=\<Expires>; Domain=\<Dominio>; Path=\<path>; Atributos de seguridad

Las primera linea es para el atributo Path y Domain, ya que permite restringir dónde se enviará esa cookie. Sin embargo, se dispone además de los llamados atributos de seguridad, que permiten indicar características para proteger la cookie. Estos protocolos son SameSite, Secure y HTTPOnly.

- Atributo SameSite: Antes de la aparición de este protocolo, el navegador enviaba todas las cookies que fueron enviadas por ese servidor independientemente si esa solicitud fue realizada por otro dominio. Para evitar esto, se desarrollo el atributo SameSite, donde se controla el comportamiento de estas cookies con: None (Siempre envia todas las cookies al servidor), Lax (El navegador enviara las cookies si es mediante una peticion GET y si fue porque el usuario hizo click) y Strict (El navegador no enviará las cookies en solicitudes Cross-Site, que no sean mismo dominio, mismo protocolo y mismo puerto).
Set-Cookie: \Cookies>=<Cookies\>; SameSite=Strict/Lax/None

- Atributo Secure: Si está presente indica que la cookie solo puede ser enviada con una comunicación segura como HTTPs.
Set-Cookie: \Cookies>=<Cookies\>; Secure
- Atributo HttpOnly: Evita que el cliente pueda acceder a la cookie mediante Javascript, ya que delimita que la cookie pueda ser recibida mediante Http.
Set-Cookie: \Cookies>=<Cookies\>; HttpOnly
### HTTP Access Control (CORS)
CORS es un protoclo de seguridad empleado por los navegadores, cuando se intenta solicitar un recurso de un origen distinto al origen del primer recurso solicitado. 

Imaginamos que entramos en el dominio A, en este dominio no hay ningun problema ya que descargaremos todos los archivos y todas las cosas, sin embargo este dominio tiene partes del dominio B, esto provoca que el Navegador tenga que acudir al dominio B a recibir esa información, esto se demonima Croos-origin request.

Normalmente los navegadores tienen un protocolo denominado Same-Origin-Policy, donde el navegador no debe confiar en recursos cargados desde orígenes arbitrarios distintos al del recurso de la petición original.

Sin embargo es muy común encontrarse dominios donde recoga recursos ubicados en otros dominios, aquí es donde entra en juego CORS para verificar que todas las solicitudes son legitimas. Una petición CORS la puede realizar diferentes elementos HTML:
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
- * : Comodín indicando que desde cualquier origen.
- Origen especifico: Solo se puede compartir a ese origen.

En las solicitudes preflighted, debe ser cuando no se produzcan ninguna de las condiciones de las simple, es decir:
- Se usa otró método como puede ser PUT o Delete
- Se incluye alguna cabecera que no estaba en la lsita de cabeceras permitidas.
- La cabecerá Content-Type no tiene un valor mencionado anteriormente.
- Se adjuntan credenciales a la solicitud.

En este caso se establecen varias comunicaciones entre cliente y servidor. El navegador en cuanto interpreta que necesita recursos externos a el, hace una petición al servidor de forma especial preguntando solo las cabeceras, si el servidor lo ve seguro le devuelve las cabeceras que acepta y es entonces cuando el navegador decide interpretar si aceptar o no.

### Ataques a HTTP
Las aplicaciones y servidores web emplean en muchas ocasiones las cabeceras de petición y respuesta HTTP para proveer de la funcionalidad necesaria al servicio. Si estas cabeceras no están bien usadas, puede dar a ataques del tipo: HTTP Host Header Injection, HTTP Request/Response Splitting y HTTP Request Smuggling.
## OWASP
La organización OWASP (Open Web Application Security Project), es una fundación sin ánimo de lucro apoyada por multitud de empresas e insituticiones educativas y particulares de todo el mundo. El objetivo es la mejora y seguridad del software.

Su aportación a la seguridad web, está recogida en proyectos, donde pueden ser herramientas, documentos, librerías, material de referencia o metodlogías, todos ellos de código abierto y desarrollado por la comunidad, algunos de los proyectos más populares son:
- ASVS (Application Security Verification Standard): Estándar de seguridad web basado en listas de requsitos y test.
- OWASP SAMM (Software Assureance Maturity Model): Modelo de madurez de software que proporciona las herramientas y medios para que una organización analice y adopte de manera progresiva una cultra de la seguridad en todos sus procesos.
- OWASP ZAP: Herramienta de seguridad gratuita y de código libre para el pentesting.
- OWASP JuiceShop: Aplicación web insegura para el entrenamiento y aprendizaje de hacking web.
- OWASP WSTG: Es una guía para testear la seguridad de las aplicaciones y los servicios web.
- OWASP MSTG: Manual para pruebas de seguridad de aplicaciones móviles e ingeniería inversa.

Además tiene desarrollado OWASP Top 10, que vamos a ver a continuación.
### OWASP Top 10
El proyecto OWASP Top 10, recopila las 10 categorías de vulnerabilidades más importantes presentes en aplicaciones web. Se renueva con cierta periocidad, siendo la última versión de 2021 (Fecha Junio 2023).

Este top se hace mediante los datos cedidos por empresas de seguridad por todo el mundo desde un año en especifico (en este caso 2017) y se va haciendo un recuento de cada CWE (Common Weakness Enumeration) presente en cada aplicación. 
### Aplicacines web vulnerables
## Principales vulnerabilidades web y su explotación
### Local File Inclusion (LFI) y Remote File Inclusion (RFI)
### File upload vulnerabilities
### Access control vulnerabilities (IDOR)
### SQL Injection (SQLi)
### Cross Site Scripting (XSS)
### Cross Site Request Foregy (CSRF)
### Server Side Request Forgery (SSRF)
### Server-Side Template Injection (SSTI)
### XML External Entity (XXE) Injection
### OS Command Injetion