---
title: Programación a nivel máquina
description: 
published: false
date: 2026-09-28T17:01:48.312Z
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

Ahora existe los AMD (Advanced Micro Devices), que han estado en la cola de Intel en todo, siendo más lentas y muchisimo mas baratas. Sin embargo decidieron reclutar a los mejores diseñadores y construyendo el Opteron con el pentium 4, y desarrollaron su propia extensión 64 btis.

Sin embargo recientemente Intel ha evitado esta guerra con una serie de mejoras:
- 1995-2011: Líder en semiconductores
- 2015: TSMC líder, y en 2019 estuvo por detras de Samsung.
- En 2018-2024 ha estado en competición con Samsung en facturación.

Ahora AMD esta luchando contra Intel con las nuevas CPUs (Los Ryzen). Sin embargo el mercado de computación esta dominado por NVidia


Volviendo con Intel, hay varios años claves:
- En 2001, se intenta hacer un cambio radical de 32 a 64 bits, pensado para programación en paralelo y fue un fracaso debido a que habia fallo de compilación entre procesadores. 
- En 2003: AMD saca una evolución satisfactoria con el AMD64.
- En 2004: Intel anuncia su EM64T, que es practicamente copiando el trabajo de AMD.
- Todos los procesadores de x86 salvo muy gama baja soportan los x86-64.


De todo lo anterior vamos a ver sobre todo los x86-64/Intel64.
### Lenguaje C, ensamblador
Debemos explicar:
- Arquitectura: Es el manual del procesador, lo que te permite entender para escribir en código ensamblador. 
- Código máquina: Son auqellos programas que ejecuta el procesador.
- Código ensamblador: Es una representación textual del código máquina. 

- Microarquitectura: Es como está fabricado la CPU. 

Algunos ejemplos de repertorios ISAs:
- Intel: La familia IA32, lo conocemos por x86.
- ARM: Usado normalmente en teléfonos.
- RISC-V: Consiste en un nuevo tipo de ISA open-source, apostado sobretodo por Europa.


Un procesador tiene:
- Contador de programa: Que tiene la dirección del próximo codigo a ejecutar.
- Archivo de regsitro: Son los datos del programa.
- Códigos de condición o flags de estado: Que suelen ser señales importantes dependiendo de lo que se haya ejecutado.

Por otro lado tenemos la mmeoria, siendo un array direciconable por bytes que almacena código y datos del usuario.


La conversión de un codigo C en código objeto, los pasos son los siguientes:
- Un programa en terminación c, es puro texto y cuando lo compilamos (gcc -S), pasaremos a un programa asm
- Este tipo de progrmaas (acabado en s), y este paso nos permite poder ensamblar el programa.
- En el parto de ensamblado el programa ya es binario (termina en .o), y  por último se le hace un programa en binario que es lo que entiende el equipo para ejecutarse.

Los datos en C, cada uno tiene un espacio a ocupar en bytes por ejemplo los importantes son:
- int, ocupa 4
- long int, ocupa 8
- char, ocupa 1
- double ocupa 8

Los datos enteros suelen ser de 1,2,4 u 8 bytes, con el valor de dato y direccion, sin embargo los datos son de  punto flotante de 4,8 ó 10 bytes. 

Los ensambladores ejecutan instrucciones, que son operaciones aritmético/lógicas. También transfieren datos entre memoria y registros, y establecen transferencias de controles debido a incondicionales o condicionales (if, bucles...).

Los codigos objetos (terminación .o), el ensamblador los traduce del .s a .o, codificandola en binario, imagen casi completa del codigos ejecutable. Le faltan enlaces entre códigos de firechos diferentes.

Los enlazadores resuelven referencias entre ficheros, combinando con librerias de tiempo ejecutable estáticas.

El desensamblador, son herramientas útiles que examinan código objeto, analizando el patrón de bits de series de instrucción, siendo capaces de producir la versión aproximada del código ensamblado. Cualquier cosa que se pueda interpretar como codigo ejecutable se puede desensamblar, examinando sus bytes y reconstruyendo su fuente.

### Formato de datos, conceptos básicos
Los registros enteros de x86-63 son
- %rax - %rdx (expansión solo tiene rax con eax)
- %rsi, %rdi, %rsp, %rbp (expansion con e--)
- %r8 - %r15 (expansión con r-d)

La primera instrucción que vamos a ver es:
- Mover datos o  movq: Se opera con movq Source, Dest.  Puede ser de forma inmediata (Datos enteros constantes, con el prefijo $), registros (Usado por % y con un valor válido mencionado anteriormente, jamas usar %rsp.) y si no es ningúno de lo anterior es memoria. 


En todas si hay
### Aritmetica