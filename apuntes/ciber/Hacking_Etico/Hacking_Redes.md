---
title: Hacking de redes inalámbricas
description: En este tema se va a abarcar a temas relacionados a redes inalámbricas.
published: true
date: 2025-03-14T17:35:33.390Z
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