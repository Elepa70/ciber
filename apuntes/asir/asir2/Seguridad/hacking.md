---
title: Conceptos basicos de Hacking
description: 
published: true
date: 2025-01-18T18:12:30.254Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:12:30.254Z
---

# Conceptos básicos de Hacking Web

## OWASP Top 10
**OWASP** (Open Web Application Security Project) es una iniciativa de código abierto dedicada a identificar y combatir las vulnerabilidades de software que hacen que las aplicaciones web sean inseguras. Publica periódicamente un listado llamado **OWASP Top 10**, que recopila las vulnerabilidades más frecuentes y peligrosas explotadas en la actualidad.

En su versión de 2021, el Top 10 incluye:

1. Control de acceso roto  
2. Fallos de criptografía  
3. Defectos de inyecciones  
4. Diseño inseguro  
5. Configuraciones incorrectas  
6. Tecnologías desactualizadas y vulnerables  
7. Fallos de identificación y autenticación  
8. Fallos de integridad de datos y software  
9. Fallos de monitoreo y registro de seguridad  
10. Falsificación de solicitudes del lado del servidor (SSRF)

Este listado es una **referencia clave** para que pentesters, desarrolladores y administradores de seguridad realicen auditorías y refuercen la seguridad de sus aplicaciones web.

---

## Explicación de categorías

### Control de acceso roto
El **control de acceso** debe asegurar que los usuarios solo puedan realizar las acciones y acceder a los recursos que se les hayan asignado. Las vulnerabilidades más comunes en esta área incluyen:

- **Violación del principio de mínimo privilegio**: Se otorgan permisos más amplios de lo necesario.  
- **Elevación de privilegios**: Un usuario sin autenticación o con privilegios básicos puede actuar con permisos de administrador.  
- **Forzar la navegación** a recursos restringidos (páginas autenticadas o con privilegios más altos) sin los debidos controles.

### Fallos de criptografía
Consiste en no asegurar correctamente los datos en tránsito o en reposo. Algunas preguntas clave:

- ¿Se utilizan **algoritmos** o **protocolos** criptográficos obsoletos o débiles?  
- ¿Los datos viajan en **texto claro**?  
- ¿Faltan **cabeceras de seguridad** en las respuestas HTTP (ej. HSTS, Strict-Transport-Security)?

En muchos países o sectores, la ley exige cifrar los datos sensibles (p. ej. RGPD en Europa).

### Defectos de inyecciones
Esta categoría se detalla más adelante, pero hace referencia a todos los tipos de **inyección** (SQL, XSS, comandos, etc.) debidos a una validación insuficiente de la entrada/salida de datos.

### Diseño inseguro
Se produce cuando no existe un **diseño de control** adecuado o este no se implementa de forma eficaz. Los controles de seguridad deben ser parte integral del diseño de la aplicación, en lugar de un añadido posterior.

### Configuraciones incorrectas
Una **configuración insegura** o por defecto puede permitir al atacante escalar privilegios o acceder a información sensible. Ejemplos:

- **Cuentas de usuario/contraseñas por defecto** aún habilitadas.  
- **Mensajes de error** que brindan demasiada información sobre el sistema.  
- **Funciones innecesarias** instaladas o expuestas (p.ej. paneles de administración abiertos).

### Tecnologías desactualizadas y vulnerables
Muchas vulnerabilidades surgen de no **actualizar** librerías, frameworks o componentes en la aplicación. Las **CVE** (Common Vulnerabilities and Exposures) clasifican estas brechas; si no se aplican los parches correspondientes, el sistema queda expuesto.

### Fallos de identificación y autenticación
Se producen cuando hay errores en los procesos de **inicio de sesión**, **gestión de sesión** o **autenticación** del usuario. Por ejemplo:

- Permitir ataques de **fuerza bruta**.  
- Uso de **contraseñas débiles** o por defecto.  
- Almacenar contraseñas en **texto plano** o con algoritmos de cifrado/“hash” inadecuados.

### Fallos de integridad de datos y software
Ocurren cuando no se protegen adecuadamente los datos o el código frente a modificaciones no autorizadas. Ejemplos:

- Uso de **plugins** o componentes externos sin verificar su origen o integridad.  
- Falta de **firmas digitales** o métodos de comprobación para asegurarse de que el software proviene de la fuente legítima.

### Fallos de monitoreo y registro de seguridad
Si no se **registran** y **supervisan** correctamente los eventos, resulta imposible detectar ataques o responder a tiempo. Inconvenientes:

- No se registran accesos o inicios de sesión.  
- Los registros se almacenan solamente en local o de forma insegura.  
- Falta de sistemas de detección de intrusiones (IDS) o alertas de seguridad en tiempo real.

### Falsificación de solicitudes del lado del servidor (SSRF)
Se da cuando una aplicación invoca una **URL** y esta puede ser manipulada para acceder a recursos internos o privados (p.ej., un panel de administración). Permite a los atacantes usar el servidor como un **proxy** para llegar a lugares que normalmente no serían accesibles desde el exterior.

---

## Inyecciones
Una **inyección** ocurre cuando la aplicación no valida adecuadamente los datos introducidos por el usuario (o por otra fuente), permitiendo que un atacante **inyecte** código malicioso.

### Inyecciones XSS
**Cross-Site Scripting (XSS)** ocurre cuando un atacante inyecta código JavaScript (u otro lenguaje) en una página web sin que el servidor o el navegador lo validen. Un **XSS** puede robar cookies, desfigurar sitios o hacer phishing de credenciales. Existen dos tipos principales:

- **XSS persistente**: El código malicioso se **almacena** en el servidor (p.ej. en la base de datos). Cada vez que otro usuario visita la página comprometida, se ejecuta el script.
- **XSS reflejado**: El script va incluido en un **enlace** malicioso y **no** se guarda en el servidor. Cuando la víctima hace clic en ese enlace, el navegador ejecuta el payload malicioso.

### Inyecciones de comandos
El atacante logra insertar comandos del **sistema operativo** en un parámetro de la aplicación web. Si no existe una validación adecuada, esos comandos se ejecutan con los privilegios del usuario que corre la aplicación (p.ej. usuario del servidor web). Puede dar acceso total a la máquina o permitir la ejecución de acciones destructivas.

### Inyecciones SQL
La **inyección SQL** aprovecha la falta de sanitización en las consultas a la base de datos. Introduciendo caracteres especiales o comandos maliciosos, el atacante puede:

- Extraer información confidencial.  
- Modificar datos o tablas.  
- Eliminar registros.  
- Adquirir privilegios administrativos.

Distintos tipos de SQLi incluyen:
- **Error-based**: El atacante induce errores en la base de datos que revelan información.  
- **Time-based blind**: El servidor no muestra mensajes, pero se miden los tiempos de respuesta para inferir datos.  
- **Union-based**: Se inyectan sentencias `UNION` para combinar resultados ilegítimos con consultas legítimas.  

Herramientas como **SQLMap** facilitan la automatización de estas pruebas.

### Inclusión de ficheros
Este ataque se da cuando la aplicación permite **incluir** archivos locales o remotos sin validar las rutas. Ejemplos:

- **LFI (Local File Inclusion)**: Permite cargar archivos locales del servidor (p.ej. `/etc/passwd`).  
- **RFI (Remote File Inclusion)**: Permite cargar archivos remotos (p.ej. un script malicioso) y ejecutarlo en el servidor.

Este tipo de vulnerabilidad aparece cuando se manipulan parámetros que se usan directamente en funciones de inclusión (`include`, `require`, etc.).

---
