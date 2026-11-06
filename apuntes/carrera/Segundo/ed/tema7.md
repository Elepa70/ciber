---
title: Arboles
description: 
published: true
date: 2026-11-06T17:17:58.005Z
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
    if (dest->hijoizq != nullptr)
    	dest->hijoizq->padre = dest;
    if (dest->hijoder != nullptr)
    	dest->hijoder->padre = dest;
  }
}
```

Ahora toca la destrucción o borrar
```C++
template <class T>
void destroy(nodewrapper <T> *n){
	if(n != nullptr){
  	destroy (n->hijoizq);
    destroy (n->hijoder);
    delete n;
  }
}
```

Insercción de un nodo un subarbol (Puesto para la derecha, pero para el de la izq cambiar las palabras)
```C++
template <class T>
void insert_right (nodewrapper <T> *n, nodewrapper <T> * rama){
	nodewrapper <T> *uax = n->hijoder;
  if (rama != nullptr){
  	n->hijoder = rama;
    rama->padre = n;
  } else {
  	n->hijoder = nullptr;
  }
  destroy(aux);
}
```

Desenlazar rama de la izquierda
```C++
template <class T>
void prune_left (nodewrapper <T> *n, nodewrapper <T>*&dest){
	if (n->hijoizq != nullptr){
  	dest= n->hijoizq;
    dest->padre = nullptr;
    n->hijoizq = nullptr;
  } else {
  	dest = nullptr;
  }
}
```
### Recorridos
> Recordamos que tenemos dos tipos de recorridos, en profundiad y en anchura, mas sus respectivas ordenaciones.
{.is-info}

Empezamos por recorrido en profundidad preorden.
```C++
void preorden_trasversal(nodewrapper<T> *n){
	if(n!= nullptr){
  	cout <<n->et;
    preorden_trasversal(n->hijoizq);
    preorden_trasversal(n->hijoder);
  }
}
```

Ahora toca profundidad inorden
```C++
void inorder_traversal(nodewrapper<T> *n){
	if(n!= nullptr){
  	inorder_traversal(n->hijoizq);
    cout << n-> et;
    inorder_traversal(n->hijoder);  
    }
}
```

Profundidad postorden:
```C++
void postorden_traversal(nodewrapper<T> *n){
	if(n!= nullptr){
  	postorden_traversal(n->hijoizq);
    postorden_traversal(n->hijoder);
    cout << n-> et;
    }
}
```

Por niveles:
Este tiene truco ya que debemos tirar mediante una cola. 
```C++
void level_traversal(nodewrapper <T> *n){
	queue<nodewrapper<T>*> cola;
  cola push(n);
  while (!cola.empty()){
  	nodewrapper<T>*aux=cola.front();
    cola.pop();
    cout<<aux->et;
    if(aux->hijoizq != nullptr){
    	cola.push(aux->hijoizq);
    if(aux->hijoder != nullptr){
    	cola.push(aux->hijoder);
   }
   
}
```
Ahora indicando el nivel
```C++
void level_traversal_indicado(nodewrapper <T> *n, int li){
	queue<pair<nodewrapper<T>*,int>>cola;
  cola.emplace(n,0);
  while (!cola.empty()){
  	auto.aux=cola.front();
    cola.pop();
    if (li == aux.second)
    	cout << aux.first->et;
    if (aux.first->hijoizq != nullptr)
    	cola.emplace(aux.first->hijoizq,aux.second+1);
    if (aux.first->hijoder != nullptr)
    	cola.emplace(aux.first->hijoder,aux.second+1);
   }
}
```

### Escritura/Lectura
> No estoy seguro si va a aqui pero vamos a decir que si.
{.is-danger}

Vmaos a empezar con igualdad entre nodos
```C++
template <class T>
bool equals (nodewrapper <T> *n1, nodewrapper <T> *n2){
	if (n1 == nullptr && n2==nullptr)
  	return true;
  else{
  	if(n1==nullptr || n2==nullptr)
    	return false;
      else {
      	if (n1->et != n2->et) return false;
        return equals (n1->hijoizq, n2->hijoizq) && equals(n1->hijoder,n2->hijoder);
        }
   }
}
```

Contabilizar loa canidad de número de nodos que cuelgan de n más el mismo
```C++
template < class T>
int count (nodewrapper <T> *n){
	if (n == nullptr)
  	return 0;
  else 
  	return 1+count(n->hijoizq)+count(n->hijoder);
}
```

Crear un arbol dado una sencuencia de texto(n1n2n3xxxn4xx)
```C++
template <class T>
void read (istream &is, nodewrapper<T> * &n){
	char c;
  c = is.get();
  if(c=='x')
  	n=nullptr;
  else{
  	if(c=='n'){
    	T v;
     	is >> v;
      n = new nodewrapper <T>(v);
      read(is,n->hijoizq);
      read(is,n->hijoder);
      if(n->hijoizq != nullptr)
      	n->hijoizq->padre = n;
      if(n->hijoder !=nullptr)
      	n->hijoder->padre = n;
    }else {
    cout << "Entrada corrupta"<<endl;
    return;
  }
}
```

Ahora hacemos el contrario, dado un arbol obtener la secuencia.

```C++
template <class T>
void write (ostream & os, nodewrapper <T> * n){
	if (n == nullptr)
  	os<<'x';
  else{
  	os<<'n'<<n->et;
    write(os,n->hijoizq);
    write(os,n->hijoder);
  }
}
```
## Bintree
Tenemos otra clase llamada bin tree con la misma estructura que la arboles pero cambiando su forma de representarse ya que es lineal.
```C++
template <class T>
class bintree{
	private:
  	struct nodewrapper{
    	// Ya explicado
    }
    nodewrapper <T> * get_father (nodewrapper <T> *n);
    nodewrapper <T> * get_left (nodewrapper <T> *n);
    nodewrapper <T> * get_right (nodewrapper <T> *n);
    
    nodewrapper *laraiz;
    unsigned int num_nodes;
  public:
  //Constructores
    bintree():laraiz(nullptr){num_nodes=0;}
    bintree(const T & e){
    	laraiz= new nodewrapper<T>(e);
      num_nodes = 1;
```
Copia destructor y igual asignación serían
```C++
bintree (const bintree <T> & a){
	copy(a.laraiz,laraiz);
  num_nodes = a.num_nodes;
}
~bintree(){
	destroy(laraiz);
  num_nodes=0;
}
bintree<T> & operator=(const bintree<T> &ab){
	if (this!=&ab){
  	destroy(laraiz);
    num_nodes=0;
    copy(ab.laraiz,laraiz);
    num_nodes = ab.num_nodes;
  }
  return *this;
}
```
Luego dentro de esta clase bintree se tiene una clase node, esta clase actua como iterador.
```C++
unsigned int nu_nodes;
public:
	class node{
  	private:
    	nodewrapper *p;
    public:
    	node(nodewrapper <T>*i){ p = 1;}
      node():p(nullptr){}
      node(const node <T> &s):p(s.p){}
      
      const T & operator*(){return p->et;}
      const T & operator*() const{return p->et;}
      
      //Obtener los hijos y padre.
      node parent() const {return p->padre;}
      node left() const{return p->hijoizq;}
      node right() const{return p->hijoder;}
      
      //Comprobación de null
      bool null()const{return p==nullptr;}
      
      //Comprobar si son iguales
      bool operator!=(const node & s){ return p!=s.p;}
      bool operator==(const node & s){return p==s.p;}
      
      friend class bintree;
```

Una vez finalizada la clase amiga node, que usaremos como iterador, podremos continuar con los demás metodos de la clase bintree
```C++
//Dentro de bintree
node root(){
	if (laraiz!=0)
  	return node(laraiz);
  else
  	return node();
}

// Insercción
node insert_left(node n, const T&e){
	int num_nodes_left=count(n-p->hijoizq);
  insert_left(n.p,e);
  num_nodes+=1-num_nodes_left;
  return node(n.p->hijoizq);
}

node insert_right(node n, const T&e){
	int num_nodes_right=count(n-p->hijoder);
  insert_right(n.p,e);
  num_nodes+=1-num_nodes_right;
  return node(n.p->hijoder);
}

//podar
void prune_left(node n, bintree<T>& dest){
	int num_nodes_left=count(n.p->hijoizq);
  dest=bintree<T>();
  prune_left(n.p->hijoizq,dest.laraiz);
  dest.num_nodes=num_nodes_left;
  num_nodes -= num_nodes_left;
}

void prune_right(node n, bintree<T>& dest){
	int num_nodes_right=count(n.p->hijoder);
  dest=bintree<T>();
  prune_right(n.p->hijoder,dest.laraiz);
  dest.num_nodes=num_nodes_right;
  num_nodes -= num_nodes_right;
}


