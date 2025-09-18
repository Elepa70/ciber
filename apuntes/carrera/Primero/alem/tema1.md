---
title: Conjuntos, Aplicaciones y Relaciones
description: 
published: true
date: 2025-09-18T23:42:53.299Z
tags: 
editor: markdown
dateCreated: 2025-09-18T13:04:27.935Z
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
Un ejemplo lo podemos ver con $\mathbb{N,Z,Q,R\text{ o }C}$


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

Conmutatividad de la unión e intersección: $A \cup B = B \cup A ,\quad A\cap B = B \cap A$
Identidad de la unión e intersección: $A \cup A = A ,\quad A \cap A = A$
$A \cup (A \cap B) = A ,\quad A \cap (A \cup B) = A$
Distributiva de la unión e intersección: $A \cup (B \cap C) = (A \cup B) \cap (A \cup) ,\quad A \cap(B\cup C) = (A\cap B) \cup (A \cap C)$