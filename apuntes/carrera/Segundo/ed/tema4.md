---
title: Plantillas
description: 
published: true
date: 2026-09-25T15:43:40.237Z
tags: 
editor: markdown
dateCreated: 2026-09-25T15:43:40.237Z
---

# Plantillas o Template
## Caracteristicas
Las plantillas nacen por la necesidad de extraer características comunes de un mismo nucleo. Estas abstracción funcional también es un ejemplo de abstracción porgeneralización.

Ejemplo
```C++
template <typename T> 
template <class T>
//Declaración de plantilla
voit Ejemplo( T&a, T &b){
	T aux = a;
  a = b;
  b= aux;
}


//En el main

int main(){
	int v1=3,v2=5;
  intercamibar(v1,v2);
  string a="Hello", b="Goodbye";
  intercambiar(a,b);
}
```

Las plantillas nos ofrecen la ayuda de que no tenemos que declarar el tipo de los valores, ya que es la propia plantilla que identifica que valor tiene sus variables para poder intercambiarlo.

