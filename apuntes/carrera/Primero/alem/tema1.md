---
title: Conjuntos, Aplicaciones y Relaciones
description: 
published: true
date: 2025-09-29T19:36:23.097Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:32:14.565Z
---

# Conjuntos, Aplicaciones y Relaciones
Este es el primer temario y vamos a hablar fundamentalmente de estos tres terminos, explicando que es cada uno y usandolos poseteriormente en tareas practicas.

## Conjuntos
**Un conjunto es una colección de objetos**, sin embargo cabe la posiblidad de entrar en la paradoja de Russell. Para evitar esto mismo, usaremos el axioma de **Zermelo - Fraenkel**, para ganar riguridad aunque no intuición.


Tras haber definido conjunto, debemos explayarnos más, por lo que:
Supongamos que tenemos un conjunto llamado *X*, y un objeto de ese conjunto se llama *a*. Por lo tanto podemos escribir como *a ∈ X*, y se leería a pertenece a X.

Este objeto puede ser lo que necesitemos que sea, desde cosas cotidianas hasta letras o numeros, incluso nuestra imaginación.


Uno de los conjuntos más importante o especiales, es el **conjunto vacío**, y se escribe como $\emptyset$ o $\{\}$, también cabe destacar la existencia de los conjuntos $\mathbb{N}$ (los números naturales), $\mathbb{Z}$ (los números enteros), $\mathbb{Q}$ (los números racionales), $\mathbb{C}$ (los números complejos) y $\mathbb{R}$ (los números reales).
### Definir conjuntos
Un conjunto queda determinado por sus **elementos** y debe ser escritas mediantes llaves, por ejemplo:
- Dado un conjunto $X$ cuyos elementos son 3, 5 y 8, quedará escrito: $X =\{3,5,8\}$

Dado un conjunto, podemos crear un conjunto con elementos del conjunto anterior, creando lo que llamamos un  **subconjunto**.

También cabe la posibilidad de que no seamos capaces de poder describir la totalidad del conjunto, como puede ser el caso de densidad de elementos que tiene.
Un ejemplo lo podemos ver con $\mathbb{N,Z,Q,R\text{ o }C}$.


La otra forma de definir un conjunto es **indicando que debe cumplir** para pertenecer a él.

Por ejemplo, podemos definir el conjunto $Z$, como: $Z = \{ n \in \mathbb{N} : n < 10000 \}$

En este caso, estamos indicando que los números que son naturales y inferior a 10000, pertenecen al conjunto $Z$.


Otro ejemplo podría ser, dado el conjunto $(1,3]$, como: $(1,3]= \{m\in\mathbb{R} : 1<m\leq 3\}$

Dos conjuntos son **iguales** si y solo si, todos los elementos son iguales.

> En una igualdad, no se le da importancia al orden de los elementos en los conjunto. Ejemplo $X = \{3,2,1\}$, sería igual a $Y = \{1,2,3\}$
{.is-info}


Cuando todo elemento de un conjunto está dentro de otro, decimos que es un subconjunto. 
Ejemplo con la cadena de inclusiones: $\mathbb{N}\subset\mathbb{Z}\subset\mathbb{Q}\subset\mathbb{R}\subset\mathbb{C}$


Tal y como hemos definido la igualdad y la inclusión, se tiene que $X=Y\Leftrightarrow X \subseteq Y \text{ e } Y \subseteq X$


### Conjunto potencia
Dado un conjunto $X$, definimos el conjunto potencia como el conjunto de **todos** los subconjuntos posibles del conjunto $X$, también llamado las partes de $X$ y se denota por como $\mathcal{P}(X)$.

Como ejemplos calcularemos $\mathcal{P}(X)$, donde $X=\{1,2,3\}$ entonces:
$\mathcal{P}(X) = \{\emptyset,\{1\},\{2\},\{3\},\{1,2\},\{1,3\},\{2,3\},\{1,2,3\}\}$

Como podemos observar, hemos añadido el conjunto vacío, ya que el conjunto vacío siempre va a ser subconjunto de cualquiera.
### Operaciones de conjuntos
A continuación, veremos las distintas operaciones que podemos realizar con los conjuntos.
#### Unión de conjuntos
Definimos dos conjuntos como $A = \{0,2,3,5\}$ y $B = \{1,2,4,8\}$. La unión de ambos sería $A \cup B =\{0,1,2,3,4,5,8\}$.


Debido a que la unión es una operación asociativa, podemos poner: $A \cup B \cup C = (A \cup B) \cup C = A \cup (B \cup C)$
#### Intersección de conjuntos
Definimos dos conjuntos como $A = \{0,2,3,5\}$ y $B = \{1,2,4,8\}$. La intersección de ambos sería $A \cap B =\{2\}$.


Debido a que la intersección es una operación asociativa, podemos poner: $A \cap B \cap C = (A \cap B) \cap C = A \cap (B \cap C)$

#### Diferencia de conjuntos
Definimos dos conjuntos como $A = \{0,2,3,5\}$ y $B = \{1,2,4,8\}$. La diferencia de ambos sería $A \setminus B =\{0,3,5\}$.

> En la diferencia de conjuntos, no se cumple con la asociatividad en general.
{.is-warning}

#### Diferencia simétrica de conjuntos
Definimos dos conjuntos como $A = \{0,2,3,5\}$ y $B = \{1,2,4,8\}$. La diferencia de ambos sería $A \Delta B =\{0,3,4,5,8\}$.

Podemos describirlo como: $A \Delta B = (A \cup B) \setminus (A \cap B) = (A \setminus B) \cup ( B \setminus A)$
> En la diferencia de conjuntos, no se cumple con la asociatividad en general.
{.is-warning}

#### Complementario de conjuntos
Dado un conjunto de referencia, que llamaremos **universo** o **espacio muestral**, todas las operaciones que realicemos serán entre subconjuntos del mismo.

Sea $X$ un universo y $A$ un conjunto (Subconjunto de $X$), definimos el complementario de $A$, como todos los valores de $X$ que no pertenezcan a $A$. Lo denotaremos como $\bar{A}, A'\text{ o }A^{c}$

$\bar{A} = X \setminus A = \{x \in X : x \notin A \}$ 


> Ahora irían las tablas de pertenencia, sin embargo no se van a escribir en estos apuntes, para más información de como funcionan, consultar apuntes del docente o Internet (Fuentes fiables).
{.is-info}

### Identidades entre conjuntos
Existe una serie de identidades entre conjuntos.

Para ello vamos a imponer que $X$ es un conjunto que hace papel de **universo**, y $A,B \text{ y }C$, son tres subconjuntos de este universo. Por lo tanto:

- Conmutatividad de la unión e intersección: $A \cup B = B \cup A ,\quad A\cap B = B \cap A$

- Identidad de la unión e intersección: $A \cup A = A ,\quad A \cap A = A$

- $A \cup (A \cap B) = A ,\quad A \cap (A \cup B) = A$

- Distributiva de la unión e intersección: $A \cup (B \cap C) = (A \cup B) \cap (A \cup C ) ,\quad A \cap(B\cup C) = (A\cap B) \cup (A \cap C)$

- Propiedades del complementario: $A \cup \bar{A}=X , \quad A \cap \bar{A} = \emptyset$

- Leyes de Morgan: $\overline{A\cup B} = \bar{A} \cap \bar{B} \quad \overline{A\cap B}= \bar{A} \cup \bar{B} \quad A \setminus (B\cap C) = (A\setminus B)\cup (A\setminus C) \quad A \setminus (B\cup C) = (A\setminus B)\cap (A\setminus C)$

### Producto cartesiano
Tenemos los dos conjuntos, para definiremos el producto cartesiano como un nuevo conjunto, cuyos elementos son parejas donde la primera coordenada pertenece a un conjunto y la segunda pertenecerá al otro.

Ejemplo: Teniendo los conjuntos $A =\{0,1,2\} \text{ y } B=\{0,2,4\}$, entonces el producto cartesiano es :
$A\times B = \{(0,0),(0,2),(0,4),(1,0),(1,2),(1,4),(2,0),(2,2),(2,4)\}$

Ojo las parejas $(0,2) \text{ y } (2,0)$, el orden tiene relevancia, ya que cabe por ejemplo, existe el $(0,4)$ pero no existe el $(4,0)$.

El producto cartesiano de un mismo conjunto se denota de la siguiente manera $A^{2} = A \times A$.

Por ejemplo, recuperando el conjunto $A$, $A^{2}$ quedaría de la siguiente manera: $A^{2} = A \times A = \{ (0,0),(0,1),(0,2),(1,0),(1,1),(1,2),(2,0),(2,1),(2,2) \}$


## Aplicaciones
Definimos la aplicación como: "Sean $X$ e $Y$ dos conjunttos. Una aplicación de $X$ en $Y$ es una forma de asignarle (o asociarle) a cada eelemento de $X$ un elemento (y sólo uno) del conjunto $Y$"

Si $f$ es una aplicación de $X$ e $Y$, escribiremos $f:X \rightarrow Y\text{ o }X \overset{ f }{\longrightarrow} Y$: al conjunto $X$ se llama dominio de la aplicación y al conjunto $Y$, codominio.

Para dar una aplicación hay que especificar:
1. Un conjunto $X$ que será el dominio.
2. Un conjunto $Y$ que será el codominio. ¡ Podría ser el mismo conjunto $X$!
3. Una regla que asigna cada elemento del dominio un elemento del codominio.

Por ejemplo:
Dada la aplicación $g : \mathbb{N} \rightarrow \mathbb{Z}$, dada por $g(n) = 2n$, es distinto a $f : \mathbb{N} \rightarrow \mathbb{N}$ con la aplicación $f(n)=2n \text{ para } n \in \mathbb{N}$. Ya que el codominio cambia.


También podemos expresar una aplicación dando explícitamente las imágenes de los elementos del dominio. 
Ejemplo:
Sea $X=\{0,1,2,3\}$ y $f : X \rightarrow \mathbb{N}$, la aplicación dada por: $f(0)=2,f(1)=7,f(2)=1,f(3)=9$.

Y aunque aparienta que no tiene sentido, en realidad si porque hay una expresión que responde a está aplicación. En este caslo la aplicación $f$ responde a $f(x)=\frac{25x^{3}-108x^{2}+113x+12}{6}$

> Importante.
{.is-warning}

Cuando queremos definir una aplicación. Debemos asegurarnos que lo estamos definiendo realmente es una aplicación.

Un ejemplo $f:\mathbb{N} \rightarrow \mathbb{N}$, la aplicación dada es $f(x)=x^{2}-60x+800$
En este caso, estamos indicando que el codominio es $\mathbb{N}$, es decir los números naturales, sin embargo encontramos varios números como $f(25)=-75$, donde **NO** se cumple la aplicación.


También debemos pasar que hubiera elementos del dominio, que no se le pueda asignar ningun elemento. (Aunque suene confuso tiene sentido).
Imaginaos una aplicación que cuando $f(3)= \frac{0}{0}$, este valor no existe, por lo que no podría estar definido **si**, nuestro codominio fuera $\mathbb{R}$.


Otro ejemplo donde podemos darnos cuenta que falla la aplicación es el siguiente:
$f\colon \mathbb{Q} \rightarrow \mathbb{Q} \text{ como } f(\frac{a}{b})=\frac{a+b}{2}$

En este caso podemos asignar valores como $\frac{1}{2} = 0,5$, sin embargo $0,5$ puede valer también $\frac{2}{4}=\frac{3}{6}=\frac{4}{8}$, y para cada valor de estos, nos cambia el resultado que obtenemos en $f$.
Ojo, como nuestro codominio es $\mathbb{Q}$, que debe estar dado en fracción con números enteros, en el caso de $f(\frac{2}{4})=3$, por lo tanto no se cumple esta aplicación.

### Grafo de aplicación
Sean $X \text{ e }Y$ dos conjuntos y $f\colon X \rightarrow Y$ una aplicación. Definimos el frado de la aplicación $f$ como el siguiente subconjunto $X \times Y$.

Ejemplo, si $f \colon \mathbb{N} \rightarrow \mathbb{N}$, es la aplicación dada por $f(n)=2n$, entonces el grafo de $f$ es: $G(f)={(0,0),(1,2),(2,4),(3,6)\dots)}$

> Es como otra forma de escribir resultados en una tabla. (Alumno)
{.is-success}

También debemos podemos "vincular" o asociar, un elemento de un conjunto a otro, y tras esto a otro.
Ejemplo:
Sea $f\colon \mathbb{N} \rightarrow \mathbb{N}$ y $g \colon \mathbb{N} \rightarrow \mathbb{N}$, y las aplicaciones dadas son $f(n) = n^{2} \text{ y } g(n) = n+3$
Si cogemos el número natural $5$, la aplicación $f$ le asocia el número $25$, y tras esto la aplicación $g$ le asociará el número $28$.

Podemos expresarlo también de la siguiente manera:
$(g \circ f)(5)=g(f(5))=g(25)=28$

La expresión de la aplicación la podemos dar como:
$(g \circ f)(n)=g(f(n))=g(n^{2})=n^{2}+3$

> Hay que tener en cuenta que $(f \circ g)$ y $(g \circ f)$, no son lo mismo.
{.is-warning}

### Composición de aplicaciones
Teniendo tres conjuntos como pueden ser $Z,X,Y$, si para cada elemento de $X$, tenemos uno de $Y$, y para cada elemento de $Y$, tenemos uno de $Z$. Podemos entonces asociar cada elemento de $X$ a $Z$. Esto es la composición de aplicaciones.

Rigiendonos en la composición de aplicaciones, podemos poner en este caso $(f \circ g)$ y $(g \circ f)$ que nos dará lo mismo.

Poniendo como ejemplo que $X,Y,Z,T$ son cuatro conjutnos y $f:X \rightarrow Y,g:Y \rightarrow Z \text{ y } h:Z \rightarrow T,$Las propiedades que podemos encontrar son:
- La aplicación identidad es un elemento neutro para la composición. $f \circ Id_{x}=f$
- Es asociativa, $h \circ (g \circ f) = (h \circ g) \circ f$.


### Tipos de aplicaciones
Tenemos varios tipos de aplicaciones según lo que vayamos a utilizar.

#### Inyectivas
Las aplicaciones Inyectivas, son aquellas donde dado dos conjuntos y una aplicación, cada elemento de un dominio tiene un unico elemento del codominio, y que distinto o unico con respecto al resto de elementos. Por ejemplo: DNI y Persona.


Para cualquier conjunto, la aplicación de $Id_{x}$ es inyectiva.

Para la composición de aplicaciones, poniendo de ejemplo $X,Y,Z$ son cuatro conjuntos y $f:X \rightarrow Y\text{ y }g:Y \rightarrow Z$

- Si f y g son inyectivas, entonces $g \circ f$ también lo será.
- Si $g \circ f$ son inyectivas, entonces $f$ es inyectiva, pero $g$ no tiene porqué serlo.
- Si $f$ es inyectiva, entonces existe $h:Y \rightarrow X$ tal que $h \circ f = Id_{x}$. Esto se le conoce como inversa por la izquierda.


#### Sobreyectivas
Las aplicaciones Sobreyectivas, son aquellas donde dado dos conjuntos y una aplicación, cada elemento del codominio, puede tener uno o varios elementos del dominio. Ejemplo, la función $f(x)=x^2$

Para cualquier conjunto, la aplicación de $Id_{x}$ es sobreyectiva.

Para la composición de aplicaciones, poniendo de ejemplo $X,Y,Z$ son cuatro conjuntos y $f:X \rightarrow Y\text{ y }g:Y \rightarrow Z$

- Si f y g son sobreyectivas, entonces $g \circ f$ también lo es.
- Si $g \circ f$ es sobreyectiva, entocnes $g$ lo es, pero $f$ no tiene porqué serlo.
- Si $f$ es sobreyectiva, entonces existe $h: Y \rightarrow X$, que provoca $f \circ h = Id_{y}$. En este caso decimos que es una inversa por la derecha.



#### Biyectivas
Las aplicaciones biyectivas, son aquellas donde dado dos conjuntos y una aplicación, la aplicación es inyectiva y sobreyectiva.

Para la composición de aplicaciones, poniendo de ejemplo $X,Y,Z$ son cuatro conjuntos y $f:X \rightarrow Y\text{ y }g:Y \rightarrow Z$

- Si f y g son biyectivas, entonces $g \circ f$ también lo es.
- Si $g \circ f$ es biyectiva, entocnes $f$ es inyectiva y $g$ es sobreyectiva.
- Si $f$ es biyectiva, entonces existe $h: Y \rightarrow X$, que provoca $f \circ h = Id_{y}$. En este caso solo hay una aplicación que puede cumplir esto, y se denomina la inversa de f, llamada $f^{-1}$.
- Si f y g son biyectivas, su inversa se expresa como $(g \circ f)^{-1} = f^{-1} \circ g^{-1}$.

# Relaciones
Vamos a definir las relaciomes con el siguiente ejemplo:

Consiremos un conjunto $X = \{0,1,2,3,4\}$ y dados $x,y \in X$ vamos a decir que $x$ está relacionado con $y$ si como $x + 2y$ es múltiplo de 4. Si llamamos R a está relación, la definiremos como: $0R0$ (0 está relacionado con 0, ya que si x=0 y y=0, el resultado es múltiplo de 4, que es 0.

Este tipo de relaciónes, las llamaremos relaciónes binarias, ya que pueden o no ser.

## Binario
Las relaciones binarias son aquellas donde se pueden dar dos casos, o es correcto o es falso lo que se plantea. Es decir, se cumple o no.

Con el ejemplo anterior, podemos describir las relaciónes de la siguiente manera:
$R = \{(0,0),(0,3),(3,0),(3,3),(1,1),(1,4),(4,1),(4,4),(2,2)\}$.

Observando bien los elementos obtenidos, podemos también hacer unos subconjuntos de la relación, en este caso obervamos que tenemos el $\{0,3\}$,$\{1,4\}$ y $\{2\}$.

Podemos decir por lo tanto que hemos creado subconjuntos de $X$, en tres subconjuntos $\{0,3\}$,$\{1,4\}$ y $\{2\}$. Se conoce como una partición del conjunto $X$.

Las particiones de un conjunto, tienen una serie de cualidades:
- $A_{i}= \emptyset$: Una partición con un valor, no puede ser un conjunto vació.
- $A_{1} \cup A_{2}\dots \cup A_{n}= X$ : La unión de todos las particiones da como resultado el conjunto.
- Si $i \neq j$ entonces $A_{i} \cap A_{j}$ : La intersacción de dos particiones es el conjunto vacío.


Una relación binaria se define como dado un conjunto $X$, una relación binaria de este conjunto es un subconjunto de $X \times X$.

Si dado un conjunto $X$, y una relación $R \subseteq X \times X$, cuando $(x,y) \in R$, diremos que $y$, estña relacionado con $x$, de la siguiente manera: $xRy$, en caso contrario diremos $xR/y$ 
> Debe ser la raya enmedio de la R, sin embargo no he encontrado de momento ese simbolo.
{.is-danger}


Dentro de las relaciones binarias, podemos encontrar subrelaciones.
> A revisar por el profesor
{.is-warning}

Estas son:
- Relación de igualdad: Donde dado una relación, ambos valores son el mismo.
- Relación de orden natural: Un valor va a ser superior a otro.
- Relación de divisibilidad: Si y es múltiplo de x, o x divide a y.
- Relación de inclusión: Si dentro del espacio de $X$, el conjunto $A \subseteq B$, ambos pertenecientes a $X$.
- Relación de congruencia: Se explicará en detalle.


Ahora vamos a clasificar las relaciones binarias en:
- Reflexiva: El mismo valor pertenece a la relación.
- Simétrica: Ambos valores se pertenecen en la relación.
- Antisimétrica: Ambos valores en realidad es el mismo valor.
- Transitiva: Si un valor está relacionado con uno y este último está relacionado a otro, decimos que el primero está relacionado con el último.

### Relaciones de equivalencia
Con esto descrito, podemos decir que una relación $R$ es de equivalencia cuando cumple que es: reflexiva, simétrica y transitiva.

Podemos denotar las relaciones de equivalencia de la siguiente manera $[x]_{R}$. Por ejemplo:

Sea $X=\{0,1,2,3,4\}$ y $R$ la relación en $X$ está dada como $xRy$ si $x+2y$ es múltiplo de 3.

Para el caso de $[0]$, vamos comparando uno a uno para comprobar que funciona:
- $¿0R0?$: En este caso sí, por lo que $0 \in [0]$
- $¿1R0?$: No, por lo que $1 \notin [0]$
- $¿2R0?$: No, por lo que $2 \notin [0]$
- $¿3R0?$: En este caso sí, por lo que $3 \in [0]$
- $¿4R0?$: No, por lo que $4 \notin [0]$

Por lo tanto definiremos $[0] =\{0,3\}$.

Esto lo podemos hacer por cada elemento del conjunto y ir obteniendo las relaciones.

Algunas caracteristicas son:
- Para cada $x \in X, [x]_{R} \neq \emptyset$.
- Si $xRy$, entonces $[x]_{R}=[y]_{R}$.



### Relación de congruencia
Sea $m$ un número entero, se ha definido la $R_{m}$, como:
$x\equiv y \text{ mód m si }y-x$ es múltiplo de m.

En el caso de m=0, siempre se cumple, al igual que con m=1.

Sin embargo en el caso de m=2, ya debemos en tener en cuenta que debe o no ser par para poder cumplir la relación que hemos establecido, es por ello que tenemos 2 formas: O par o Impar.

Esto lo escribimos de la siguiente manera
$[0]_{2}= \{\dots -2,0,2 \dots\}$.
$[1]_{2}= \{\dots -3,-1,1,3 \dots\}$.

¿Porque es así? Porque si ponemos que $X=0$, es decir $[0]$, nos saldrá que el módulo de $y$ tiene que ser múltiplo de 2, y esto son todos los números pares. Por otro lado con $[1]$, le estaríamos restando 1 a todos los valores que tome $y$, es por ello que serían los impares.


Ahora probamos con el número 3, tendriamos los múltiplos de 3 o $[0]_{3}$, aquellos cuya división entre 3 de un resto de 1, es decir $[1]_{3}$ y por último los que cuando hagamos una división entre 3, su resto sea 2 $[2]_{3}$.

O lo que es lo mismo:
- $[0]_{3} = \{x \in \mathbb{Z} : 0  \equiv x\text{ } mód \text{ } 3\} = \{x \in \mathbb{Z}:x \text{ es múltiplo de }3.\}$.
- $[1]_{3} = \{x \in \mathbb{Z} : 1  \equiv x\text{ } mód \text{ } 3\} = \{x \in \mathbb{Z}:x-1 \text{ es múltiplo de }3.\}$.
- $[2]_{3} = \{x \in \mathbb{Z} : 2  \equiv x\text{ } mód \text{ } 3\} = \{x \in \mathbb{Z}:x-2 \text{ es múltiplo de }3.\}$.

Y para saber donde pertenecerá un valor a uno de estas relaciones, solo deberemos dividir el valor con el número a relacionar, por ejemplo, dividimos $145$ entre $3$ y nos dara cociente $48$ y resto $1$, por lo que pertenece a $[1]_{3}$

Con esto podemos ver que siempre que tengamos un número, podemos encontrar la relación de congruencia hasta ese mismo valor. Es decir dado n, vamos a tener $[0]_{n},[1]_{n},[2]_{n},[3]_{n},[4]_{n}\dots[n-1]_{n}$

### Relación de orden
Una relación de orden, la describimos como una relación binaria dodne se comple que es **reflexiva,antisimétrica y transitiva.**

Cuando nos referemios a una relación $R$, diremos que $(X,R)$ es un conjunto ordenado. Sin embargo, cuando hablamos de una relación de orden, usaremos otros simbolos para indicarla como $\leq,\mid,\subseteq$. Por ejemplo $(X,\mid)$.

Sea $(X,\mid)$, un conjunto ordenado, y para dos elementos cualquiera perteneciente a $X$, como son $x$ e $y$, si tenemos que $x\leq y$ o $y \leq x$, diremos que es un conjunto totalmente ordenado. Un ejemplo puede ser los números naturales ($\mathbb{N}$), donde el 2 es menor a 3, y así sucesivamente, hay un orden total.


Sin embargo,en caso de que lo contrario no se cumpla, diremos que tenemos un orden parcial o parcialmente ordenado.



#### Diagrama de Hasse

Podemos representar los orden establecidos anteriormente de manera grafica, esto lo podemos hacer con flechas, pero lamentablemente no puedo continuar describiendolo en estos apuntes ya que el software no me lo permite. Recomiendo consultar el siguiente vídeo [Diagrama de Hasse de una relacion binaria de orden | 16/23 | UPV - Universitat Politècnica de València - UPV](https://www.youtube.com/watch?v=I7AepBaZ0Q8)


Sin embargo vamos a seguir describiendolo.

Podemos describir el orden entre varios números de forma ascendiente y sin redundancia, esto lo hacemos eliminando aquellos elementos que nos sea repetitivos o por el hecho de que es transitiva, no nos hace falta.

> Ojo
{.is-warning}

El diagrama de Hasse del conjunto $(X,\leq)$ es un grafo cuyo conjunto de véritces es el conjunto $X$, y dados dos elementos $x,y \in X$, hay un lado que une $x$ con $y$ si $x < y$ y no existe $z$ tal que $x < z< y$.

Ahora definiremos algunos elementos notables.
Sea $(X,\leq)$ un conjunto ordenado, y sea $x \in X$.
- Definimos que x es maximal (en $X$) si no existe $y \in X$ tal que $x < y$.
- Definimos que x es máximo (en $X$) si para cualquier $y \in X$ se tiene que $y \leq x$.
- Definimos que x es minima (en $X$) si no existe $y \in X$ tal que $y < x$.
- Definimos que x es mínimo (en $X$) si para cualquier $y \in X$ se tiene que $x \leq y$.



Sea $(X,\leq)$ un conjunto ordenado,$Y \sybseteq X$ un subconjunto de $X$ no vacío y $x \in X$.
- Decimos que x es cota superior de $Y$ si $y\leq x$ para cualqueri $y \in Y$.
- Decimos que x es el supremo de Y si es el mínimo del conjunto de las cotas superiores de Y.
- Decimos que x es cota inferior de $Y$ si $x\leq y$ para cualqueri $y \in Y$.
- Decimos que x es el ínfimo de Y si es el máximo del conjunto de las cotas inferiores de Y.

#### Ordenes lexicográfico y producto.

Ahora vamos a ver dos formas en las que podemos realizar el diagrama de hasse. Esto lo vveremos con productos cartesianos (Es decir, $(0,0)$ o $X \times X$.

En el lexicográfico debemos prestar atención al primer elemento de la pareja, y ya después al segundo "Como un diccionario". Este tipo de orden es mucho más rápido y sencillo.

Sin embargo con el producto, debemos tener en cuenta ambos elementos de la pareja, si en uno de los elementos tiene menor que el anterior, no podemos asociarlos.

Por eso lo escribimos como:
$(X,\leq_{1})$,  $(Y,\leq_{1})$
$(x,y), (x',y') \in X \times Y$

$(x,y)\leq_{lex} (x',y') \text{ si }x<_{1} x' \text{ o } (x=x' \text { e } y\leq_{2}y')$

$(x,y)\leq_{prod} (x',y') \text{ si }x<_{1} x' \text{ e }  y\leq_{2}y')$

Por ejemplo.

Teniendo las parejas $(1,0),(1,2),(2,0) \text{ y } (2,2)$

El orden lexicográfico será el siguiente:
$$
  \{2,2\} \\
     |  \\
  \{2,0\} \\
   \  |   \\
  \{1,2\} \\
       | \\
   \{1,0\}
$$

Sin embargo en producto será:
$$
  \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\{2,2\} \\
              \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }/\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
            \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }/\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
          \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }/\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
      \text{ }\text{ }\text{ }\text{ }/\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
        \text{ }\text{ }/\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
     / \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|   \\
  \{1,2\}\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }|\text{ }\text{ }\text{ }\text{ }\text{ }    \\
       |\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\text{ }| \\
   \{1,0\} \text{ }\text{ }\text{ }\text{ }\text{ }\text{ }\{2,0\}
$$

Esto es todo de este tema.