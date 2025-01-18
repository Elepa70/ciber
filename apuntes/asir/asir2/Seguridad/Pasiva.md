---
title: Seguridad Pasiva
description: 
published: true
date: 2025-01-18T18:07:39.093Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:07:39.093Z
---

# TEMA 2: Seguridad pasiva Hardware y Almacenamiento  


# Ubicación física y protección física
Para garantizar la seguridad de un servidor, lo primero es decidir **dónde** instalarlo. Es fundamental proteger el hardware de desastres naturales, inundaciones, sobrecargas eléctricas, robos y otras amenazas. Para ello, se aplican barreras físicas y procedimientos de control, prevención y contramedidas.

## ¿Dónde ubicar un CPD?
Se deben evitar lugares como:

- **Primeras plantas o sótanos**: Para reducir el riesgo de inundaciones.  
- **Fachadas exteriores y ventanas**: Minimiza el vandalismo y sabotaje.  
- **Fuentes de interferencia de radiofrecuencia**.  
- **Zonas cercanas a maquinarias pesadas** o áreas con elevado riesgo.

## Distribución de un CPD
Al diseñar la distribución física de un CPD, es necesario contemplar varias salas, cada una con un propósito específico:

- **Sala de control**:  
  - Alberga monitores y personal de supervisión.  
  - Suele ser la antesala a la sala de racks, contando con sistemas de control de acceso.  
  - Dispone de falso suelo y techo, comodidad para el personal y medidas de seguridad.

- **Sala de racks**:  
  - Ubicación de los racks de servidores y dispositivos de comunicaciones.  
  - Incluye falso suelo o techo, sin ventanas ni aberturas, y controles de acceso.  
  - Espacio habilitado para la instalación de sistemas de extinción de incendios y aire acondicionado.  
  - Iluminación adecuada y pasillos de servicio para manipular los equipos.

- **Sala crítica**:  
  - Contiene grupos electrógenos, UPS, baterías, cuadros y transformadores, así como el equipo de aire acondicionado y sistemas de extinción de incendios.  
  - Requiere buena ventilación (aunque no necesariamente aire acondicionado).

- **Sala de reparaciones**:  
  - Facilita la labor de pruebas, montaje y reparaciones de equipos sin interferir en la actividad principal.

## Controles de acceso
Dependiendo de la instalación y la inversión, se pueden implementar diversos sistemas de seguridad:

- Personal de seguridad.  
- Detectores de metales y escáneres.  
- Sistemas biométricos.  
- Detectores de presencia.

## Sistemas de climatización
Los equipos generan gran cantidad de calor, de ahí la necesidad de refrigerarlos manteniendo **temperaturas** y **humedad** adecuadas:

- **Temperatura**: Entre 18°C y 22°C (crítico estar por debajo de 10°C o por encima de 30°C).  
- **Humedad relativa**: Entre 40% y 60% (50% ± 10%). Crítico superar el 80% o descender por debajo del 20%.

Si no se cumplen estas condiciones, el CPD puede sufrir fallos por sobrecalentamiento (Overtemp).

Las **técnicas de refrigeración** varían según las necesidades:

1. **Enfriamiento a nivel de sala**:  
   - Indicado para instalaciones pequeñas.  
   - Uso de aire acondicionado y extracción de aire caliente de la parte superior.

2. **Enfriamiento a nivel de hilera** (pasillo frío/pasillo caliente):  
   - Diseño que aprovecha la circulación de aire predecible.  
   - **Pasillo frío**: aire frío se inyecta frente a los equipos.  
   - **Pasillo caliente**: recoge el calor desprendido por la parte trasera de los equipos.  
   - El calor puede neutralizarse en la zona del pasillo caliente, sin necesidad de climatizar toda la sala.

Para una mayor eficiencia energética, se pueden aislar los pasillos:

- **Aislamiento de pasillo frío**: Cerramientos integrales sin requerir falso techo.  
- **Aislamiento de calor**: Uso de “chimeneas” que recogen aire caliente y lo redirigen al falso techo.

**Cálculo aproximado** de la potencia de refrigeración:
- Multiplicar la potencia de los equipos por 1,5 para obtener los vatios (W) necesarios.  
- Multiplicar la potencia de los equipos por 1,3 para conocer las frigorías/hora (fg/h).

Los aires acondicionados de uso doméstico no suelen ser ideales para CPD, debido a:
- No están diseñados para funcionar 24/7.  
- Carecen de control preciso de la humedad.  
- No eliminan la mayoría de partículas.  
- El flujo de aire no siempre es el adecuado.  
- Eficiencia energética y rendimiento limitados.

### Data Centers Ecológicos
El coste de refrigeración de un CPD puede llegar a representar hasta el 50% de la potencia total consumida. Por ello, muchas compañías optan por ubicar sus CPD en lugares donde se aprovechan recursos naturales:

- HP usando energía eólica.  
- Microsoft con centros de datos bajo el mar.  
- Google enfriando equipos con agua marina.  
- Yahoo! en Suiza, empleando el frío exterior.

---

## Sistemas de Alimentación Ininterrumpida (SAI)
Un **SAI** o **UPS** (*Uninterruptible Power Supply*) es un dispositivo que alimenta y protege cargas críticas frente a cortes o caídas de tensión. Permite mantener el suministro eléctrico aunque falle la alimentación principal.

**Parámetros clave** de un SAI:

- **Potencia**:  
  - Se expresa en **potencia aparente** (VA, voltioamperios) o **potencia real** (W, vatios).  
  - Normalmente, la potencia real equivale a alrededor del 60% de los VA.  

- **Autonomía**:  
  - Tiempo durante el cual el SAI puede alimentar las cargas al producirse un corte de suministro.

**Tipos de SAI**:
1. **SAI “On-Line”**:  
   - Modos de funcionamiento: Bypass (mantenimiento), AC (en línea) y Batería.  
   - Alimenta de forma continua (excepto en modo Bypass).  
   - Genera una onda sinusoidal de alta calidad, aislando la carga de la red.  
   - Excelente protección frente a variaciones eléctricas.

2. **SAI “Off-Line”** o “Standby”:  
   - Modos: AC (en línea) y Batería.  
   - No protege contra todas las perturbaciones.  
   - No genera una onda sinusoidal pura.  
   - Puede haber un corte breve al pasar a baterías.

3. **SAI Interactivo** (“In-Line”):  
   - Usa un AVR (regulador de voltaje) entre la red y la carga.  
   - No aísla completamente de la red.  
   - Mayor calidad de onda que un Off-Line, pero menor que un On-Line.

###  ¿Cómo dimensionar un SAI?
Para dimensionar correctamente un SAI:

- **Potencia de carga**:  
  - Se expresa como potencia aparente (**S**, en VA) o potencia real (**P**, en W).  
  - El **factor de potencia (FA)** es la relación P/S. Cuanto más próximo a 1, mayor eficiencia.  
    - En SAI domésticos es habitual un FA de 0,6; en profesionales, entre 0,8 y 0,9.  
  - Debe contemplarse un **margen de seguridad**. Por ejemplo:  
    \[
      \text{Potencia de carga del SAI} = \text{Suma de VA de los equipos} \times 1{,}2
    \]

- **Cálculo de VA** si solo se conocen los W de consumo de un equipo:  
  \[
    \text{VA} = \frac{\text{W}}{\text{FA}}
  \]

- **TIER**: Clasificación de centros de datos según disponibilidad y redundancia:  
  - **TIER I**: 99,67% de disponibilidad, sin redundancias.  
  - **TIER II**: 99,75% de disponibilidad, posible redundancia parcial.  
  - **TIER III**: 99,982% de disponibilidad, componentes redundantes y mantenibles sin parar.  
  - **TIER IV**: 99,995% de disponibilidad, la más alta.

**Otras características** de un SAI:
- Conectores RJ11 para proteger la línea telefónica.  
- Puertos RS-232 y USB para monitorizar el estado.  
- Tarjeta de red (SNMP) para gestión remota.  
- Tomas de corriente con protecciones extra (back-up y supresión de picos).

---

## Sistemas RAID
El **RAID** (Redundant Array of Independent Disks) es un sistema de almacenamiento que combina varios discos para:

- Aumentar la capacidad total.  
- Mejorar la tolerancia a fallos (redundancia).  
- Incrementar la velocidad de acceso.

Puede implementarse por **software** (económico, menor rendimiento y mayor consumo de CPU) o **hardware** (mejor rendimiento, pero más caro).

### Tipos de RAID

- **RAID 0 (Striping)**  
  - Reparte la información entre varios discos de forma equitativa.  
  - **Ventaja**: Aumento de velocidad y capacidad.  
  - **Desventaja**: La pérdida de un disco implica perder parte de los datos.

- **RAID 1 (Mirroring)**  
  - La información se duplica en dos o más discos.  
  - **Ventaja**: Tolerancia a fallos (uno de los discos puede fallar sin perder datos).  
  - **Desventaja**: Duplicar la información conlleva un mayor coste de almacenamiento.

- **RAID 5**  
  - Distribuye los datos y la paridad entre todos los discos.  
  - **Ventaja**: Tolerancia a fallos: si un disco falla, se puede regenerar la información.  
  - **Desventaja**: Rendimiento algo menor en escritura, necesidad de al menos 3 discos.

- **RAID 6**  
  - Similar a RAID 5, pero con un segundo bloque de paridad.  
  - **Ventaja**: Soporta la pérdida de hasta 2 discos.

- **RAID 0+1**  
  - Combina el striping (RAID 0) y luego la duplicación (RAID 1).  
  - **Ventaja**: Velocidad y redundancia.  
  - **Desventaja**: Se necesitan al menos 4 discos, coste elevado.

- **RAID 1+0**  
  - Inverso al anterior: primero espejado (RAID 1) y después striping (RAID 0).  
  - **Ventaja**: Alta velocidad y tolerancia a fallos con menor impacto en la escritura.

- **RAID Z**  
  - Variante propia de sistemas de ficheros como ZFS (similar a RAID 5).  
  - Escribe en “stripes” completas y utiliza espejado para bloques pequeños, mejorando la eficiencia.

**Consideraciones**:
- Es recomendable usar tarjetas RAID (SCSI o SATA) con posibilidad de intercambio en caliente (“hot-swap”).  
- Preferible usar discos de **mismo tamaño y velocidad**.  
- Posible incluir un disco **Hot Spare** (disco de repuesto) que entra en funcionamiento al fallar otro.  
- RAID no sustituye las copias de seguridad externas.

### Sistemas RAID por software en Windows Server
En Windows Server, los **volúmenes dinámicos** permiten configurar:

- **Volúmenes simples**: Usan un único disco físico.  
- **Volúmenes distribuidos (JBOD)**: Unión de varios discos sin redundancia ni mejora de velocidad.  
- **Volúmenes seccionados (RAID 0)**.  
- **Volúmenes reflejados (RAID 1)**.  
- **RAID 5**.

### Sistemas NAS
Un **NAS** (Network Attached Storage) es una tecnología de almacenamiento que comparte información con equipos en una **red local**. Se accede a través de protocolos de red a nivel de **archivo** (ej. SMB, NFS).  

- **SMB/Samba**: Compartición de archivos en entornos Windows.  
- **NFS**: Compartición en entornos Linux/UNIX.

Los NAS suelen incluir:

- Cabinas de discos con RAID.  
- Administración simplificada para compartir almacenamiento.  

Su función principal es **almacenar y compartir** ficheros a nivel de red.

### Sistemas SAN
Una **SAN** (Storage Area Network) es una red dedicada de **alta velocidad** que conecta servidores con cabinas de almacenamiento. Los servidores ven esas cabinas como **discos locales**.

- Frecuente uso de **fibra óptica** para máxima velocidad.  
- iSCSI permite transportar bloques de datos a través de redes Ethernet (TCP/IP).  
  - **Target iSCSI**: Servidor que ofrece uno o más recursos de almacenamiento en la red.  
  - **Iniciador iSCSI**: Cliente que consume esos recursos.

Una SAN proporciona acceso a **nivel de bloque**, creando volúmenes denominados LUN (Logical Unit Number). 

### Sistemas DAS
El **DAS** (Direct Attached Storage) es un sistema de almacenamiento **conectado directamente** a un servidor por cables (SCSI, SATA, SAS, etc.). Extiende la capacidad local del servidor sin pasar por la red.

### Diferencias y similitudes, ventajas y desventajas

|                        | **NAS**                                                                 | **DAS**                                                                   | **SAN**                                                                   |
|------------------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Protocolos y S. Archivos** | Peticiones de datos mediante SMB/NFS. El sistema de archivos reside en el NAS. | Se conectan directamente al servidor; el sistema de archivos está en el cliente. | Uso de protocolo iSCSI o FC a nivel de bloque; el sistema de archivos está en el cliente. |
| **Conexión al archivo** | Habitualmente Ethernet (1/10/25 Gbps).                                 | Conexión directa (SCSI, SATA, SAS).                                       | Fibra óptica o iSCSI sobre Ethernet; alta velocidad (8/16 Gbps o más).    |
| **Uso de RAID**        | Sí, en el dispositivo NAS.                                              | Sí, si la controladora o el servidor lo soporta.                          | Sí, en la cabina y a veces también en el servidor.                         |

---
