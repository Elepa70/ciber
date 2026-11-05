---
title: Arboles
description: 
published: true
date: 2026-11-05T16:56:52.182Z
tags: 
editor: markdown
dateCreated: 2026-10-30T16:40:19.312Z
---

# Arboles
## Conceptos generales
Un arbol, consiste en un grafo aciclico donde cada nodo tiene grado de entrada 1 (excluyendo la raíz) y grado de salida 0 o más.

> Podemos usar de ejemplo la estructura de archivos de Linux.
{.is-info}

Dentro de los arboles se pueden hacer subárbol con distintos raices si solo cogemos los valores de ese hacia el anterior.

Para poder obtener la altura, lo que hacemos es contar desde la base (archivo más bajo) y vamos en subida hasta encontrar la raíz.

Estas formas de contar o cortar las líneas, lo llamamos niveles donde el 0 es el más alto y vamos en subida bajando el arbol.


## Árbol binario
Los arboles binarios se caracterizán porque pueden tener 0, 1 o 2 hijos. Donde podemos encontrar:
- Árbol binario homogeneo: Es un árbol binario donde cada nodo tiene o 0 o 2 hijos.
- Árbol Binario Completo: Tienes todos los niveles completos excepto el último empezando desde la izquierda. Esto será importante para arboles parcialmente ordenados.

Podemos hacer dos tipos de recorridos grandes.
### Recorrido en profundidad
Los recorridos en profundidad a su vez, se difieren en tres subgrupos:
- Recorrido prefijo: Lo que hace es analizar la raíz y posteriormente los subarboles de cada uno desde la raíz. (/ es la raíz, subarbol /home /etc /var ...). Se va describiendo cada uno en orden, por ejemplo / /home /home/pablo /home/algo /etc /etc/...

- Recorrido Infijo: Este caso es el más erratico, ya que tenemos que se recorre de forma semi inversa y se escribe como: /home/pablo /home /home/algo / /etc/something... Es como si fuera de izquierda a derecha.

- Postfijo: Va desde lo más bajo a lo más alto partiendo de izquierda a derecha.
### Recorrido en anchura
Se va recorriendo por niveles y listandos según la altura. Partiendo del nivel 0

## Implementación
Ya hemos descrito a nivel teorico pero ahora toca escribirlo en codigo para ello tenemos que saber implementar varios aspectos importantes.

TEniendo una representación de codigo así:
```C++
template <class T>
struct nodewrapper{
	T et;
  nodewrapper * padre;
  nodewrapper * hijoizq;
  nodewrapper * hijoder;
  nodewrapper(){
  	padre = 0;
    hijoizq=hijoder=0;
  }
  nodewrapper (const T &e){
  	et=e;
    padre=0;
    hijoizq=hijoder=0;
  }
};
```

### Modificadores
Para el copy podemos usar la siguiente estructura:
```C++
template <class T>
void copy (const nodewrapper <T> * ong, nodewrapper<T> *&dest){
	if (ong == nullptr){
  	dest = nullptr;
  } else {
  	dest = new nodewrapper<T>(ong->et);
    copy (ong->hijoizq, dest->hijoizq);
    copy (ong->hijoder,dest->hijoder);
    if (dest->hijoizq != nullptr){
    	dest->hijoizq->padre = dest;
  }
}
```