---
title: Sincronización en memoria compartida
description: 
published: true
date: 2026-10-09T16:42:13.746Z
tags: 
editor: markdown
dateCreated: 2026-10-09T16:36:44.576Z
---

# Sincronización en memoria compartida
Las sincronizaciónes que vamos a ver en este tema, va a estar dividido en dos:
- Soluciones en bajo nivel con espera ocupada: Basadas en programa que contiene explícitamente instrucciones de bajo nivel de lectura y escritura.
- Soluciones en alto nivel: Se tiene una capa de software por encima con un interfaz para la aplicaciones.

Cuando un proceso tiene que esperar a algun evento por X condición, entra en un estado de espera infinita, a esto lo denominamos **espera ocupada**. Podemos encontrar dos tipos de soluciones:
- Solución software: Usan operaciones simple de lectura y escritura de datos simples.
- Solución hardware (cerrojos): Esta basado en instrucciones máquinas específicas, con varios procesadores involucrado.