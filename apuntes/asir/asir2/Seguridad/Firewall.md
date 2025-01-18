---
title: Firewall
description: 
published: true
date: 2025-01-18T18:16:58.965Z
tags: 
editor: markdown
dateCreated: 2025-01-18T18:16:58.965Z
---

# Firewall

## ¿Qué es un Firewall?

Un **Firewall** (o **Cortafuegos**) es un **software** o **dispositivo** cuyo objetivo es **filtrar el tráfico de red** según un conjunto de reglas. Dependiendo de su emplazamiento:

- **Firewalls personales**: Protegen un único equipo, filtrando las comunicaciones entrantes y salientes. A menudo se incorporan al propio sistema operativo o al antivirus.  
- **Firewalls perimetrales**: Protegen una red o grupo de equipos, definiendo políticas comunes. Suele situarse entre el router y los equipos internos. También puede establecerse una **DMZ (zona desmilitarizada)** para exponer servidores accesibles desde la red externa.

---

## Tipos de Firewall

Según la **capa OSI** en que operan, distinguimos:

1. **Filtrado de paquetes** (capas de Enlace/Red/Transporte):  
   - Filtra en función de direcciones IP de origen y destino, puertos, direcciones MAC, etc.

2. **Capa de aplicación** (capas Aplicación/Presentación/Sesión):  
   - Inspecciona el contenido de las peticiones HTTP, DNS, etc.  
   - Cuando se filtran URLs o se actúa de intermediario en la capa de aplicación, se denomina **proxy**.

---

## Limitaciones de los cortafuegos

Aunque un firewall es un elemento esencial de la seguridad, **no** puede ofrecer protección completa ante todos los riesgos. Sus principales limitaciones:

1. No protege contra ataques cuyo tráfico **no pase** a través de él.  
2. No puede proteger ante ataques internos llevados a cabo por usuarios legítimos.  
3. No puede proteger frente a ataques de **ingeniería social**.  
4. No puede proteger contra virus que ya están dentro de la red.  
5. No soluciona vulnerabilidades de seguridad de los **protocolos o servicios** que se han permitido pasar.

---

## Políticas de un cortafuegos

Podemos establecer **dos políticas básicas** de configuración:

1. **Política restrictiva (o “deny all”)**  
   - Todo el tráfico está **denegado** excepto lo que se **autorice explícitamente**.  
   - Mayor seguridad, configuración más compleja.

2. **Política permisiva (o “allow all”)**  
   - Todo el tráfico se **permite** excepto lo que se **prohíba explícitamente**.  
   - Menor seguridad, configuración más sencilla.

---

## Iptables

**Netfilter** es el subsistema del kernel de Linux que **intercepta** y **controla** el flujo de paquetes. **Iptables** es la herramienta de línea de comandos usada para gestionar las reglas de Netfilter.

- Cuando un paquete llega al servidor, Netfilter le aplica las **reglas** definidas en Iptables, determinando así si se acepta, se rechaza o se manipula.

### 5.1. Composición de Iptables

#### Las tablas

Existen **3 tablas** principales:

1. **Filter**: La más usada para **filtrar** el tráfico (por defecto).  
2. **NAT**: Para **enmascaramiento** (cambio de dirección origen/destino, port forwarding, etc.).  
3. **Mangle**: Permite modificar campos específicos de los paquetes (por ejemplo, TOS/QoS).

#### Cadenas

Cada tabla contiene **cadenas**, que son listas de reglas. Las cadenas más relevantes son:

- **Filter**:  
  - **INPUT**: Filtra el tráfico que se dirige al equipo local.  
  - **OUTPUT**: Filtra el tráfico originado localmente.  
  - **FORWARD**: Filtra el tráfico que atraviesa el equipo (origen y destino distintos del propio servidor).

- **NAT**:  
  - **PREROUTING**: Permite modificar la dirección de **destino** antes del enrutamiento (**DNAT**).  
  - **POSTROUTING**: Permite modificar la dirección de **origen** después del enrutamiento (**SNAT**).  
  - **OUTPUT**: **DNAT local** para paquetes generados en el propio equipo.

- **Mangle**:  
  - Permite manipular campos específicos en **PREROUTING**, **POSTROUTING**, **INPUT**, **OUTPUT** y **FORWARD** (Ej. para cambiar TOS/QoS).

---

### 5.2. Acciones

Cuando un paquete cumple una determinada regla, se aplica una **acción** (o **target**):

- **ACCEPT**: Se permite el paso del paquete.  
- **REJECT**: Se deniega el paquete, enviando una respuesta de rechazo.  
- **DROP**: Se ignora el paquete sin notificación (similar a “dejar en visto”).  
- **LOG**: Se registra la coincidencia y continúa con la siguiente regla.  
- **MASQUERADE**: Enmascara la IP de origen de forma **dinámica** (sobre todo con IPs dinámicas).  
- **DNAT**: Cambia la IP de destino (caso típico de port forwarding a un host interno).  
- **SNAT**: Cambia la IP de origen (similar a MASQUERADE, pero con IP fija).

---

### 5.3. Parámetros

#### Parámetros para reglas

| Parámetro   | Función                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------|
| **`-i`**    | Interfaz de **entrada**                                                                                  |
| **`-o`**    | Interfaz de **salida**                                                                                   |
| **`-s`**    | Dirección **origen** (IP o rango)                                                                        |
| **`-d`**    | Dirección **destino** (IP o rango)                                                                       |
| **`-p`**    | Protocolo (ej: `tcp`, `udp`, `icmp`)                                                                    |
| **`--sport`** | Puerto de **origen** (puede ser un puerto específico o un rango)                                      |
| **`--dport`** | Puerto de **destino**                                                                                 |
| **`-j`**    | Acción a ejecutar (`ACCEPT`, `DROP`, `REJECT`, etc.)                                                    |

#### Parámetros para cadenas

| Parámetro | Función                                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------------------|
| **`-A`**  | Añade (**Append**) una nueva regla al **final** de la cadena                                                            |
| **`-I`**  | Inserta (**Insert**) una regla en la **posición** especificada                                                          |
| **`-R`**  | Reemplaza (**Replace**) una regla existente                                                                            |
| **`-E`**  | Cambia el **nombre** de una cadena propia                                                                               |
| **`-L`**  | Lista (**List**) todas las reglas de la cadena especificada                                                             |
| **`-N`**  | Crea una **nueva cadena**                                                                                               |
| **`-P`**  | Configura la **política por defecto** (ej: `INPUT DROP`)                                                                |
| **`-D`**  | Elimina (**Delete**) la regla especificada                                                                              |
| **`-X`**  | Elimina **todas** las reglas de la cadena (si está vacía)                                                               |
| **`-F`**  | Borra (**Flush**) todas las reglas definidas en la cadena                                                               |
| **`-Z`**  | Pone a **cero** los contadores de paquetes y bytes                                                                      |

---

## Otras consideraciones importantes

### 6.1. Estructura de una regla

Un ejemplo de creación de regla podría ser:

    iptables -t filter -A INPUT -p tcp --dport 23 -j DROP

- **Tabla**: `filter`  
- **Acción**: `-A INPUT` (append a la cadena INPUT)  
- **Condiciones**: protocolo `tcp`, puerto destino `23`  
- **Decisión**: `-j DROP`

### 6.2. Esquema de filtrado

Al llegar un paquete:

1. **PREROUTING** (NAT/Mangle): Si hace falta, se modifica la dirección de destino.  
2. **FORWARD** (Filter): Si el paquete no va dirigido a este equipo, pasa por la cadena FORWARD.  
   - Tras el FORWARD, va a **POSTROUTING** (NAT/Mangle) para modificar la dirección de origen si procede.  
3. **INPUT** (Filter): Si el paquete es para este equipo, se aplica INPUT.  
   - El proceso local maneja el paquete. Si el proceso emite respuesta, ésta pasa por **OUTPUT** (Filter).  
   - Finalmente, el paquete sale por **POSTROUTING** si es necesario (SNAT).

### 6.3. Orden de las reglas

Las reglas se **evalúan** en el orden en que se listan. Una vez que una regla coincide, se aplica su acción y **no** se siguen evaluando reglas posteriores. Por ello, se suelen poner primero las reglas **más restrictivas** o las más frecuentes.

### 6.4. Política predeterminada

Si un paquete no coincide con ninguna regla, el firewall aplica la **política por defecto** de la cadena. Esta puede ser `ACCEPT` o `DROP` (normalmente se prefiere `DROP` para mayor seguridad).

### 6.5. Registro de paquetes

La acción **`LOG`** sirve para **registrar** la coincidencia en el log del sistema. Opciones útiles:

- **`--log-level nivel`** (0 = emerg, 1 = alert, 2 = crit, 3 = err, 4 = warning, 5 = notice, 6 = info, 7 = debug)  
- **`--log-prefix "cadena"`** para añadir un texto identificativo al log.  
- Módulo **limit** (`-m limit`) para evitar la saturación de logs (`--limit`).

---

## Negociación de una conexión en TCP

El protocolo **TCP** inicia una conexión con el **handshake** de **tres vías**:

1. El cliente envía **SYN**.  
2. El servidor responde con **SYN/ACK** si el puerto está abierto (o **RST** si no).  
3. El cliente envía **ACK**, completando la conexión.

Iptables puede filtrar conexiones en función de estas banderas (**`--tcp-flags`**), para permitir o denegar conexiones en diferentes etapas.

---

## Gestión de usuarios

Podemos crear una **nueva cadena** con `-N`, agrupando reglas similares, y luego "llamarla" desde la cadena principal para simplificar la configuración.

---

## Seguimiento de conexiones

Iptables/Netfilter pueden hacer **stateful inspection** (seguimiento del estado de la conexión). Con la extensión `-m state` y parámetros como:

- **`NEW`**: Paquete que inicia una nueva conexión.  
- **`ESTABLISHED`**: Forma parte de una conexión ya existente.  
- **`RELATED`**: Inicia una conexión relacionada con otra ya existente (p.ej. transferencias de datos en FTP).  
- **`INVALID`**: Paquete que no encaja en ninguna conexión conocida.

Ejemplo:

    iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

---

## Manipulación de paquetes

El **enmascaramiento** se utiliza cuando los equipos de la red local acceden a Internet usando la IP pública del **gateway**. Estas manipulaciones se realizan en **NAT**:

- **PREROUTING**: Cambiar dirección de **destino** (`DNAT`).  
- **OUTPUT**: Modificar destino en paquetes **generados localmente**.  
- **POSTROUTING**: Modificar dirección de **origen** (`SNAT` o `MASQUERADE`) antes de enviar el paquete a la red.
