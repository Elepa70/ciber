---
title: Programación a nivel máquina
description: 
published: true
date: 2026-09-28T16:06:02.461Z
tags: 
editor: markdown
dateCreated: 2026-09-28T15:41:33.390Z
---

# Programación a nivel máquina
> Este tema es el más grande de la asignatura, es por ello que la página sea más extensa de lo normal.
{.is-warning}

## Primera parte

### Perspectiva historica e intel
Los procesadores Intel dominaron el mercado con sus procesadores familia del x86. En el año 1978, pasarón a 16 bits con el modelo 8086, y desde ahí fue mejorando hasta que hoy en dia los manuales tienen 5 mil páginas.


Estos procesadores son CISC (Instrucciones Complejos donde incluye muchisimas instrucciones diferentes), en contraparte tenemos los RISC (Computador con repertorio de instrucciones reducido, donde hay pocas instrucciones pero con muchas acciones.

Sin embargo debido a que Intel lo trabajo muy bien con RISC su buena interpretación parece que sea CISC, provocando que ganara la cuota de mercado.  
> Estas máquinas suelen ser de estilo 1/2, ya que no puedes sumar memoria con memoria
{.is-info}

Algunos de los hitos signifiativos a mencionar son:
- 8086: En el año 1978, que permitia direccionamiento de 1MB
- 386: En el 1985, es el primer procesador 32 bits (conocido como x86) con direccionamiento plano y arrancando UNIX.
- Pentium 4E: En el año 2004, fue el primer procesador intel de 64 bits (conocido x86-64).
- Core 2: En el año 2006, primer procesador multi-core de intel.
- Core i7: En el año 2008, con cuatro cores y hyperthreading.

Estos modelos obtienen lo que tenian anteriormente y más cosas llamado compatibilidad ascendente, usualmente lo que traen estas mejoras son:
- Instrucciones multimedia
- Instrucciones para operaciones condicionales eficientes.
- El paso al 64 bits
- Mucho más núcleos.

Esto es debido a que se va mejorando el proceso de forma nanometrica, mediante los procesos fatograficos. 
### Lenguaje C, ensamblador
### Formato de datos
### Aritmetica