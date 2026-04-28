---
title: Lógica de Predicados
description: 
published: true
date: 2026-04-28T14:23:15.065Z
tags: 
editor: markdown
dateCreated: 2026-04-15T13:38:24.930Z
---

# Lógica de predicados

Los cuantificadores, es lo que ha provocado desarrollar está lógica.

La lógica detras del enunciado es:
$\text{ser\_persona}(x),\text{ser\_mortal}(x),\forall x (\text{ser\_persona(x)}\rightarrow \text{ser\_mortal(x)})$. Si $\text{ser\_persona(Sócrates)}$, entonces $\text{ser\_mortal(Sócrates)}$.
## Elementos del lenguaje de primer orden
Ahora vamos a ver los elementos que componen esta lógica.
### Alfabeto
El alfabeto es el lenguajd e primer orden en la sintaxis que vamos a usar, y tiene cuatro conjuntos finitos:
- C: Símbolos constantes.
- V: Variables.
- F: Símbolos de función.
- R: Símbolos de relación o de predicado.

Además:
- Tenemos los elementos conectores
- Símbolos de paréntesis y coma
- Cunatificador universal ($\forall$) y existencial ($\exist$).

A cada símbolo de una función o símbolo del predicado, se le asocia un número natural, que se llama **aridad**. 

### Términos y fórmulas atómicas
Sea $(C,V,F,R)$ un alfabeto de un lenguaje de primer orden. Podemos definir el conjunto de terminos T como:
- Los elementos de C y V son términos.
- Si $f\inF$ con aridad $n$ y $t_1...t_n$ son términos, entonces $f(t_1...t_n)$ son términos.
- Las palabars que no se hayan construido de esta manera NO son términos.

### Lenguaje de primer orden
Es aquel lenguaje que requiere un alfabeto de primer orden, construido por palabras con:
- Fórmula atómica es una palabra de F.
- Si $\alpha \text{ y } \beta$ están en F, y $x$ es una varibale, entonces su unión, disyunción... también lo estarán.

## Semántica del lenguaje de primer orden

La interpretaciones de la fórmulas de primer orden es más complicada. Dado un alfabeto de un lenguaje de primer orden, una estructura de este lenguaje tiene los siguientes elementos:
- Conjunto vacío, o dominio y universo.
- Aplicaciones $C\rightarrow D$.

> Por resumir
{.is-danger}

### Valoración
Son valores libres que odemos asignar donde queramos. Usualmente se denota con la letra $v$.

### Interpretación
La interpretación, consiste en evaluar las valoraciones y las estructuras, es decir darle contexto y valores a las variables.

las interpretaciones son $1$ o $0$, si encontramos formas que puedan contradecir la estructura.

### Lema de Coincidencia
Si dos valoraciones que coinciden en variables libres dan lo mismo, entonces es lo mismo.

### Clasificación de las formulas
- Válidas, para toda valoración es verdad.
- Satisfacible, para algunas valoraciónes es verdad
- Refutable, para algunas valoraciónes es falsa
- No válida, para algunas interpretacion es falsa.

## Equivalencia lógica
Algunas equivalencia que verems será.
- $\not \forall x \alpha = \exists x \not \alpha$.
- $\not \exists x \alpha = \forall x \not \alpha$.
- $\forall x \forall x \alpha = \forall x \alpha$.

- $\forall x \alpha \cap \forall x \beta = \forall x (\alpha \cap \beta)$.
- $\exist x \alpha \cup \exist x \beta = \exists x (\alpha \cup \beta)$.


Realmente el temario es similar al tema anterior, pero esta vez jugamos con $\forall$ y los $\exists$.

El metodo que vamos a usar, el algoritmo mejor dicho es:
1. Eliminamos conectividades $\rightarrow$, $\leftrightarrow$.
2. Mover las negaciones hacia la formula y eliminar dobles negaciones.
3. Agrupar cuantificadores.
4. Insertar formulas o aplicar las reglas.

### Forma normal de Skolem
La forma normal de Skolem, son auqellas formulas donde no hay cuantificadores.
La utilidad real de esta forma, es que nos permite verificar y tratar el problema de satisficilidad de forma más sencilla.
### Forma clausulada
Es la forma que ya conocemos de antes, donde la hemos estado usando con anterioridad en el tema 2.

La forma clausulada es una conjunción de cláusulas, siendo una cláusula el cierre universal de una disyunción de literales.