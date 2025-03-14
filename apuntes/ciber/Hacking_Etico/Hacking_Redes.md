---
title: Hacking de redes inalámbricas
description: En este tema se va a abarcar a temas relacionados a redes inalámbricas.
published: true
date: 2025-03-14T19:15:59.519Z
tags: hacking, redes
editor: markdown
dateCreated: 2025-03-14T16:06:22.960Z
---

# Hacking de redes inalámbricas
En esta unidad, se va a hacer repaso de principios de tipos de redes inalámbricas, su evolución y la forma en la que ha sido vulneradas por el tiempo.

## Introducción a las comunicaciones inalámbricas
Las redes inalámbricas son aquellas comunicaciones que suceden sin necesidad de un cable, es decir, mediante ondas electromagnéticas. Las ventajas que tenemos es la commodidad de prescindir del cable, sin embargo, genera nuevos problemas de seguridad y una bajada de rendimiento. 

La principal clasificación de las redes inalámbricas se hace según su cobertura.

- WPAN (Wirelesss Personal Area Network): Redes de bajo alcance, donde su función es la conexión de dispositivos personales, periféricos o dispositivos IoT, como puede ser Bluetooth, Zigbee, RFID, NFC...

- WLAN (Wireless Local Area Network): Redes inalámbricas, basadas en la norma IEEE 802.11, usado normalmente en hogares y empresas.

- WMAN (Wireless Wide Area Network): Redes inalámbricas de área extensa. Normalmente es ofrecido por compañias de telecomunicaciones, para ofrecer servicios de red a dispositivos móviles. Aquí podemos tener tecnologías como **UMTS, GPRS y HSPA**. También podemos considerar aquí dentro las tecnologías **LPWAN** (Low Power Wide Area Network), para comunicaciones a larga distancia de dispositivos con bajo consumo.

También debemos tener en cuenta que la **capa de enlace de datos**, se divide en dos subcapas:
- La capa LLC (Link Layer Control), definida en la norma IEEE 802.2, usado para ofrecer una interfaz común a las capas superiores.
- La capa MAC (Media Access Control), implementa hardware y adaptada a las peculiaridades de distintas tecnologías de red y medios físicos. Los estándares que tiene son IEEE 802.3 (Internet), 802.11 (Redes locales inalámbricas) y 802.15 (Redes de área personal).


### Estándar 802.11 - WI-FI
802.11 es el grupo de trabajo del IEEE encargado de la definición de redes locales inalámbricas. Desde la especificación en 1997 han ido publicandose distintas versiones.

- 1999: Aparece la 802.11a y 802.11b, donde la versión a funciona para banda de 5GHz y tiene una velocidad máxima teórica de 54Mbps y canales de 22MHz. Sin embargo la 802.11b, tiene una banda de 2,4GHz con canales de 22MHz, con una velocidad máxima de 11Mbps.

- 2003: Se fija en mejorar la banda de 2,4GHz por ello surge la 802.11g como evolución del 802.11a. Se consiguen velocidades de 54Mbps.

- 2009: Aparece la versión 802.11n con dos innovaciones clave, la primera es MIMO (Multiple Inputo Multiple Output), tecnica de multiplexación espacial que, mediante el uso de más antenas, consigues crear canales en paralelo. Y la otra es capacidad de unir canaes de 20MHz de dos en dos, consiguiendo canales de 40MHz.


Tras esto surgue la Wi-Fi Alliance (Organización sin ánimo de lucro que promueve la tecnología Wi-Fi).

- 2013: Aparece el WiFi 5 o 802.11ac, funcioan en la banda de 5GHz con canales de 20MHz que pueden agregarse para formar canales más grandes de 40, 80 y hasta 160MHz. Además, duplicó el número de flujos MIMO y mejoró la tecnicó con MU-MIMO (Multiple-User MIMO). Con esto se llega a velocidades teóricas de 7Gbps.

- 2021: Se publica WiFi 6 o 802.11ax, se consigue velocidades de hasta 10 Gbps, donde soporta bandas de hasta 6 GHz con 24 canales. Aunque la verdadera innovación es la capacidad de gestionar un mayor número de dispositivos conectados al tiempo que se mantiene un buen rendimiento.

- Para 2024 está prevista la publicación de WiFi 7 o 802.11be con un alcance velocidades de hasta 46 Gbps.

### Bandas de frecuencia

Según la versión, Wi-Fi puede funcionar en la banda de frecuencias de 2,4GHz o 5GHz. Realmente se trata de rangos de frecuencia que se diferencia en **canales**.

#### 2.4Ghz
Rango de frencuencia que va desde 2400 Mhz a 2483 Mhz. Este espacio se divide en **trece canales** de 22MHz de ancho, separadso del otro 5MHz, aunque posteriormente se añadió el canal 14. Existen muchos canales que se solapan, por ejemplo el 1,2,3,4 y 5. Esto provoca que haya perdidas de señal en los canales proximos y se generen ruido bajando el rendimiento en la red. 

Dentro de sus ventajas tenemos su extensa cobertura pero con una perdida de velocidades de red.

#### 5GHz
La banda de los 5GHz se encuentra entra 5180Mhz y 5825Mhz. Es posible tener mas o menos canales según el canal elegido. La ventaja que trae esta banda con respecto a la de 2.4GHz es la velocidad de transmisión superior pero con una cobertura menor y menor poder de penetración.

Es posible que según tu región tenga restricciones de uso, por ejemplo en Europa solo el rango de 36 y 48 es posible usarlo libremente, el resto son canales DFS o TPC.

- DFS (Dynamic Frequency Selection): son usados por servicios como, radares de defensas,  aeropuertos o servicios meteorlogícos. En caso de que un router ocupe una canal de estas caracteristicas, estará 60 segundos esperando algúna señal similar, y si la recibe saldra del canal en 10 segundos.
- TCP (Transmit Power Control): Son canales empleados por potencia de transmisiones, los routers deben esperar hasta 10 minutos para su conexión es por ello que comercailemtne no es viable.


### Protocolos de seguridad
Debemos intentar que cuando implementamos una red, cumplir la autenticidad (Que cualquiera no pueda conectarse a la red), Integridad (Un terceno puede alterar datos en tránsito) y confidencialidad (Los datos transmitidos no sean entendibles por un tercero).

El primer protoclo que vamos a ver es el **WEB** (Wired Equivalent Privacy), para las redes WLAN. Surgue en 1997 con las primeras versiones de Wi-Fi. Ofreciendo dos tipos de autenticación:
- Abierta: Donde no se solicitan credenciales
- Clave compartida: Usa algoritmos de desafío- respuesta en cuatro fases para autenticar al cliente.

Para el cifrado se utiliza un algoritmo RC4, con claves al principio de 64 bits y después de 128 bits.  El IV es una secuencia aleatoria generada dinámicamente para cada tramo que está en transito, y su objetivo es dificultar la obtención de la clave secreta.

Debido a fallos de seguridad se retiró oficialmente y se considera obsoleto.

### WPA y WPA2
WPA (Wi-Fi Protected Access) surguió en 2003 para sustituir a WEP, la intención era que los dispositivos que usaban WEP pudieran ser actualizados a WPA. En este caso se usa un algoritmo TKIP. Con este algoritmo se mejora el cifrado ya que emplea una clave temporal PTK (Pairwise Transient Key), que es generada durante la tansmisiones unicast entre un cliente determinado y un punto de acceso.

Además esta tecnologia trae dos modelos de autenticación.
- WPA Personal: Llamado WPA PSK (Pre-Shared Key), consiste en el uso de una clave compartida entre punto de acceso y los clientes, común en hogares.
- WAP Enterprise: Los clientes utilizan sus credenciales propias para poder autenticarse, apoyado por el estandar IEEE 802.1X.

WPA2 fue publicado en 2004 como 802.11i-2004 y establecido como requisito obligatorio por la Wi-Fi Allience para todo router a partir del 2006. Respecto al cifrado se usa CCMP basado en AES, ya que TKIP ha pasado a ser inseguro.


### WPA3
Aparece en 2018, e incorpora nuevas mejoras sobre WPA2, una de ellas es OWE (Opportunist Wireless Encryption), para cirar comunicaciónes de redes abiertas. 
## Ataques a redes Wi-Fi
Las comunicaciones pueden ser interceptadas por cualquiera dentro del rango de la señal inalambrica, por ello es importante la protección de la información y con una mala configuración es posible darle entrada a los atacantes de la empresa.

### Metodología OWISAM
La metodología OWISAM (Open Wireless Security Assessment Methodology), fue creada por una empresa española llamada Tarlogic en 2013. Esta metodología tiene una serie de controles que se deben llevar a cabo para analizar el riesgo de seguridad, estos tienen diez categorias que son:
- OWISAM-TR-001: Red de comunicaciones Wi-Fi abierta.
- OWISAM-TR-002: Presencia de cirado WEP en redes de comunicaiones.
- OWISAM-TR-003: Algoritmo de generación de claves del dispositivos inseguro.
- OWISAM-TR-004: Clave WEP/WPA/WPA2 basada en diccionario.
- OWISAM-TR-005: Mecanismo de autenticación inseguros.
- OWISAM-TR-006: Dispositivos con soporte de Wi-Fi protected setup PIN activo.
- OWISAM-TR-007: Red Wi-Fi no autorizada por la organización.
- OWISAM-TR-008: Portal hotspot inseguro.
- OWISAM-TR-009: Cliente intentando conectar a red insegura.
- OWISAM-TR-010: Rango de cobertura de la red demasiado extenso.

Aparte también enemos en cuenta los diez riesgos que afectan a las redes inalámbricas y que OWISAM las clasifica en un top 10.

- OWISAM-DI: Descubrimiento de dispositivos, recopilación sobre la información de las redes inalámbricas.
- OWISAM-FP: Fingerprinting, analisis de las funcionalidades de los disposiivos de comunicaciones.
- OWISAM-AU: Pruebas sobre la autenticación, análisis de los mecanismos de autenticación.
- OWISAM-CP: Cifrado de las comunicaciones, análisis de los mecanismos de cifrado de  información.
- OWISAM-CF: Configuración de la plataforma, verificación de la configuración de las redes.
- OWISAM-IF: Pruebas de infraestructura, controles de seguridad sobre la infraestructura wireless.
- OWISAM-DS: Pruebas de denegación de servicio, controles orientados a verificar la disponibilidad del entorno.
- OWISAM-GD: Pruebas sobre directivas y normativas, análisis de aspectos normativos que aplican al uso de las redes Wi-Fi.
- OWISAM-CT: Pruebas sobre los clientes inalámbricos, ataques contra clientes inalámbricos.
- OWISAM-HS: Pruebas sobre hotsposts y portales cautivos, debilidades que afectan al uso de portales cautivos.
Para poder realizar ataques es necesario que la tarjeta de red pase a modo monitor, para poder leer todo el tráfico inalámbrico e inyectar paquetes.

### Suite aircrack-ng
La suite aircrack-ng, es un conjunto de herramientas para realizar audotirías de redes inalámbricas. Esa disponible para Windows y Linux y consta con las siguientes herramientas:
- airmon-ng: Permite cambiar el modo de trabajo de la tarjeta inalámbrica a modo monitor.
- airodump-ng: Aplicación que permite escuchar todo el tráfico.
- airbase-ng: Permite abarcar a los clientes inalámbricos asociados a un puno de acceso.
- aircrack-ng: Herramienta que permite realizar ataques de fuerza bruta.
- airdecap-ng: Habilita descifrar capturas de tráfico cifrados con WEP y WPA.
- airdecloack-ng: Elimina paquetes de tipo WEP cloacking, frames que insertan algunos puntos de acceso para dificultar el ataque estadístico.
- aireplay-ng: Permite realizar ataques sobre los putnos de acceso inyectando frames.
- airolib-ng: Permite crear un servidor wireless.
- airtun-ng: Permite crear interfaces virtuales empleadas para monitorización de tráfic cifrado.

### Ataques a los protocolos de seguridad
A continuación vamos a comentar acerca de las primeras investigaciones sobre vulnerabilidades en el protocolo 802.11 que han permitido diseñas los ataques para poder obtener claves utilizadas en las comunicaciones. Los más importantes son:
- WEP: Korek ChopChop Attack, Fragmentation Attack, PTW Attack.
- WPA: Ohigashi-Mori Attack, Michael Attack, Hole196 vulnerability.
- WPA2: Krack Attacks, Kr00k.
- WPA3: Dragonblood bugs.


En **WEP**, como comentamos se hace uso de IV, que es generado en texto plano. Este IV (Vector de inicialización) usa 24 bits, por lo que si hay mucho trafico en una red, es posible sacar mediante estadistica cuál es el vector usado para generar los códigos aleatorios. 

En **WPA** y **WPA2**, el ataque se centra más en el handshake entre un equipo y un punto de acceso, ya que una obtenido este handshake es posible mediante un ataque de fuerza bruta sacar la contraseña. Es por ello que en este tipo de redes, la seguridad reside en la contraseña.

En **WPS**, es un software cómodo y rápido para que los dispositivos se conecten a una red Wi-Fi sin necesidad de establecer contraseñas constantemente. Normalmente se hace mediante un PIN, NFC, USB o un botón del dispositivo. Es un metodo altamente inseguro, ya que las contraseñas están precompartidas.


