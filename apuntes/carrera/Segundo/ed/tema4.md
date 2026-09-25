---
title: Plantillas
description: 
published: true
date: 2026-09-25T16:30:55.325Z
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

Este tipo de template es realmente útil en numerosos usos por ejemplo:
### Restructurar un vector

En este caso se nos quedaria:
```C++
template <class T>
void vd<T>::resize(int nuevo){
	T* aux = new T[nuevo];
  int limite = (n < nuevo)? n: nuevo;
  for(int i = 0; i < limite; i++){
  	aux[i] = datos[i];
   }
   delete[] datos;
   datos = aux;
   reservados = nuevo;
}
```

Como podemos observar es prácticamente igual que como lo conocemos.
### Sobrecarga de copiar
Ahora implementaremos el de copia:
```C++
template <class T>
void vd<T>:: copiar(const vd<T> &o) {
	datos = new T[o.reservados];
  reservados = o.reservados;
  n = o.n;
  for (int i = 0; i<n; i++){
  	datos[i] = o.datos[i];
  }
}
```
### Sobrecarga de borrar
El de eliminar es:
```C++
template <class T>
void vd<T>::borrar() {
	if (datos != nullptr) {
  	delete[] datos;
    datos = nullptr;
  }
  n = 0;
  reserva = 0;
}
```
### Sobrecarga del copia
```C++
template <class T>
vd<T> & vd<T>::operator=(const vd<T> &a){
	if (this != &a){
  	borrar();
    copiar(a);
  }
  return *this;
}
```
