---
title: Resumen de componentes
description: 
published: true
date: 2025-01-14T12:00:00.905Z
tags: hardware
editor: markdown
dateCreated: 2025-01-14T12:00:00.905Z
---

# Resumen de componentes

## Placa Base
### Componentes principales:
- Microprocesador en un socket o zócalo.
- Ranuras de memoria.
- Ranuras de expansión.
- Chips de control: chipset y BIOS.
- Conectores variados.

### Tipos de zócalo:
1. **PGA:** Contacto por presión.
2. **ZIF:** Contacto magnético, sin presión.
3. **LGA:** Pines en la placa base. Usado por Intel.

### Chipset:
- **Northbridge:** Soporte de microprocesadores, memoria, buses locales, ahorro energético y gráficas integradas.
- **Southbridge:** Gestión de otros componentes secundarios.

### BIOS:
- Programa básico para arrancar el PC y gestionar dispositivos de entrada/salida.
- Almacenada en EEPROM o FlashROM.
- Incluye POST para verificar el hardware al encender el equipo.

### Ranuras de expansión:
1. **ISA:** Obsoletas.
2. **PCI:** Mejor calidad, más pequeñas.
3. **AGP:** Para tarjetas gráficas.
4. **PCI Express:** Mayor velocidad (serie).
5. **M.2:** Para SSDs.

---

## El Microprocesador
### Velocidades:
- **Interna:** Dentro del chip.
- **Externa:** Comunicación con la placa base.

### Partes principales:
1. **Encapsulado:** Protege el silicio.
2. **Memoria caché:** Memoria ultrarrápida.
3. **Coprocesador matemático (FPU):** Para cálculos complejos.

### Parámetros de funcionamiento:
- **Velocidad del reloj:** Pulsos por segundo (Hz).
- **Velocidad del bus:** Comunicación con la placa.
- **Memoria caché:** Almacenamiento rápido para datos frecuentes.
- **Tecnología de fabricación:** Micras o nanomicras.
- **Voltaje:** Controlado por el VRM.

### Mejora del rendimiento:
- **Pipelining:** Tareas en paralelo.
- **Ejecución especulativa:** Predicción de operaciones.
- **Hyper-Threading:** Ejecutar tareas independientes.

### Procesadores multinúcleo:
- Mejor respuesta en multitarea.

---

## Memoria RAM
### Conceptos técnicos:
- **Controlador de memoria:** Gestión de datos entre RAM y procesador.
- **Bus de memoria:**
  - **Direcciones:** Ubicación de los datos.
  - **Datos:** Capacidad de transmisión por ciclo.
- **Celdas de memoria:** Chips organizados en matrices.

### Parámetros fundamentales:
- **Velocidad de acceso:** Tiempo para realizar un ciclo (ns).
- **Velocidad de reloj:** Frecuencia máxima soportada.
- **Latencia (CAS):** Retardo en el acceso.
- **Ancho de banda:** Cantidad máxima de datos por segundo. Dual Channel duplica el ancho de banda.

### Tipos de RAM:
1. **SRAM:** Retiene datos con menos energía.
2. **FPM/SDRAM:** DRAM con sincronización al reloj.
3. **DDR-SDRAM:**
   - DDR2: Mayor velocidad y menor voltaje.
   - DDR3, DDR4, DDR5: Mejores sucesores.

---

## Disco Duro
### Conceptos clave:
- **Partes móviles:** Discos giratorios y cabezales de lectura.
- **Especificaciones:**
  - Tamaño: 3.5 pulgadas.
  - Velocidad: Rotación (rpm) y transferencia (MB/s).
  - Latencia: Tiempos de búsqueda y rotación.
- **Tecnologías:**
  - **S.M.A.R.T:** Prevención de fallos.

### Interfaces:
1. **ATA:** Paralelo.
2. **SATA:** Serie, más rápido.
3. **RAID:**
   - **Mirroring:** Copias.
   - **Striping:** Fragmentación.

---

## Monitor
### Tipos:
1. **CRT:** Tubo de rayos catódicos.
2. **LCD:** Cristal líquido.
3. **LED:** Paneles monocromáticos o policromáticos.
4. **Plasma y proyectores.**

### Características:
- **Luminancia:** Brillo (cd/m²).
- **Resolución:** Píxeles representados.
- **Tasa de refresco:** Veces que se actualiza la pantalla.
- **Contraste:** Diferencia entre claro y oscuro.
- **Ángulo de visión:** Calidad de colores desde diferentes posiciones.

---

## Tarjeta Gráfica
### Tipos:
1. **Integradas:** En la placa base o chipset.
2. **Expansión:** PCIe x16.

### Configuración básica:
- **Paleta de colores:** 2^n bits.
- **Modo de vídeo:** Resolución y número de colores.
- **Memoria dedicada:** Para cálculos gráficos.

### APIs:
1. **DirectX.**
2. **OpenGL.**

---

## Impresoras y escáneres
### Impresoras:
1. **De impacto:** Matriciales, margarita o agujas.
2. **De tinta:** Inyección térmica o piezoeléctrica.
3. **Láser:** Usa tóner y tambor.
4. **Fotográficas:** Tinta, sublimación térmica o ceras.

### Parámetros:
- **Resolución:** ppp o dpi.
- **Buffer:** Memoria para cola de impresión.
- **Velocidad:** Páginas por minuto (ppm).

### Escáneres:
1. **CCD:** Condensadores ante la luz.
2. **CIS:** LEDs para iluminación.
3. **PMT:** Tubo de vacío.


