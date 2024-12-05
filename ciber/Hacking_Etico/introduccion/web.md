---
title: Hacking de aplicaciones web
description: En este tema vamos a ver todo lo relacionado a Hacking Web
published: false
date: 2024-12-05T17:31:48.077Z
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
Set-Cookie: cookies<as>>=<cookies>; Expires=Expires<as>>; Domain=<a>; Path= <a>; Atributos de seguridad
## Seguridad en HTTP
### Cabeceras de seguridad
### HTTP Access Control
### Ataques a HTTP
## OWASP
### OWASP Top 10
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