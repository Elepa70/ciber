---
title: Resumen para Examen
description: 
published: true
date: 2026-06-18T13:28:27.269Z
tags: 
editor: markdown
dateCreated: 2026-06-18T10:37:37.720Z
---

Aquí puedes tener una zona de apuntes rapidos para distintos temas.
# Álgebras de Boole
De este apartado debemos saber hacer:

## Boole y caracteristicas
La álgebra de boole es una conjunto $B$ que tiene operaciones binarias suma y producto.
Propiedades importantes:
- Idempotencia: $x+x=x$ y $x*x=x$.
- Dominación: $x+1=1$ y $x*0=0$.
- Doble complementario: $\overline{\overline{x}}=x$.
- Leyes De Morgan: $\overline{X*Y}=\overline{X}+\overline{Y}$ y $\overline{X+Y}=\overline{X}*\overline{Y}$.

## Expresión booleana
Las expresiones booleanas las construimos en base a literales (1 o 0) y recurrentes (+ *). Estas expresiones pueden ser dadas en:
- Minterms: Conjunto de valores de una expresión que recopila información en función de $F^n$ que hace que la cumpla. Con los minterms podemos escribir la Forma Normal Disyuntiva ($xy+\overline{X}y$).
- Maxterms: Es el contrario de los minterms, con esto podemos hacer la Forma Normal Conjuntiva ($(x+y)(\overline{X}y)$).

## Simplificación de circuitos

- Mapas de Karnaugh: "Tabla donde marcamos aquellos valores que cumplen con la función dada" obtenemos los minterms.
- Quine-McCluskey: Método dedicado a la optimización de funciones booleanas para sacar minterms. "Colocamos todos los valores en una columna agrupados según cuantos 1 tengamos, a la derecha de esta fila, iremos comprobando en grupos de mayor a menor cantidad de 1 si lo hay una diferencia de 1 valor, en caso de que existe esta diferencia la pondremos a la derecha escribiendo "-", en el posición donde difiere. Tras todo esto obtenemos una serie de valores, tras esto hacemos una tabla, donde por columna está los minters y por fila estará los valores obtenidos. 
> Recomendable mirar en los apuntes si se tiene mucha duda, no es viable representarlo en estos apuntes.
{.is-info}

# Lógica proposicional
En este apartado, ya hemos deberiamos haber entendido como funciona la Álgebra de Boole, ahora nos toca jugar con ellas para llegar a los que nos pide.

En este apartado, nos suelen pedir:
- Dada X cantidad de formulas, demostrar que es tautología.
- Dada X cantidad de formula, demostrar que Y es consecuencia lógica.
- Nos dan un texto y debemos traducirlo a lenguaje proposicional.

## Interpretaciones
Es vital saber esta parte:
- Tautología, si $I(\alpha)=1$ para **TODA** interpretación.
- Contradición, si $I(\alpha)=0$ para **TODA** interpretación.
- Satisfacible, si $I(\alpha)=1$ para alguna interpretación.
- Refutable, si $I(\alpha)=0$ para alguna interpretación.
- Contigente, es tanto satisfacible como refutable.

## Simbolos
- Disyunción $\wedge$, se lee como $\alpha$ y $\beta$.
- Conjunción $\vee$, se lee como $\alpha$ o $\beta$.
- Negación $\neg$, se lee como no $\alpha$.
- Implicación $\rightarrow$, se lee como $\alpha$ implia a $\beta$. Se puede traducir a $\alpha \rightarrow \beta = \neg \alpha \vee \beta$.
- Equivalencia: $\leftrightarrow$, ambas se implican a si mismo, se traduce como: Se puede traducir a $\alpha \leftrightarrow \beta = (\neg \alpha \vee \beta) \wedge (\neg \beta \vee \alpha)$.

La consecuencia logica por lo tanto es, dado una serie de formulas combinadas con los anteriores simbolos, $\gamma \vDash \alpha$, siendo $\gamma$ una serie de formulas.

## Deducción y Reducción a lo absurdo.

Es posible que las fórmulas que nos den tenga muchas implicaciones y sea inviable poder reducirlas en OR y AND (Conjunción y Disyunción), es por ello que debemos tener en cuenta la Deducción.
### El teorema de deducción
Con el teorema de la deducción, podemos ir "recortando" partes de la formula dada, para hacerla más sencilla, esto funciona de la siguiente manera:

> Examen Final Julio 2023.
{.is-info}

Sea $\alpha = (a \rightarrow \neg b) \rightarrow [(\neg a \rightarrow \neg c) \rightarrow (( \neg c \rightarrow b) \rightarrow[ a\vee \neg \vee b \vee c \rightarrow a \neg \wedge b \wedge c ])]$, demuestra sin tabalas de verdad que es tautología.

La mejor forma de operar es ir deducciendo según las implicaciones que tenemos, por ejemplo, para ello vamos a ir "quitando" las premisas de las implicaciones para añadirlas a nuestro conjunto a examinar ejemplo.
$(a \rightarrow \neg b) \vDash (\neg a \rightarrow \neg c) \rightarrow (( \neg c \rightarrow b) \rightarrow[ a\vee \neg \vee b \vee c \rightarrow a \neg \wedge b \wedge c ])$.

Ahora lo tenemos más sencillo, pero podemos seguir hasta:
$(a \rightarrow \neg b), (\neg a \rightarrow \neg c), ( \neg c \rightarrow b), a\vee \neg \vee b \vee c   \vDash a \neg \wedge b \wedge c$.

Ahora se nos ha quedado que todo lo anterior debe ser consecuencia logica de lo último.

### Reducción a lo absurdo
Para poder terminar esta ejercicio, nos hace falta hacer una reducción al absurdo. Para que entender esto, podemos decir que $\vDash = \rightarrow$, la única manera para que esto sea falso es que lo que está antes de la implicación sea verdadero y lo que está después sea falso.

Entonces, si añadimos lo que está después de la implicación dentro de nuestras clausuras, de forma negada, si encontramos una Contradicción, significa que la formula original es verdadera ya que no existe un metodo para hacerla falsa.

En nuestro ejemplo se nos quedaría:
$(a \rightarrow \neg b), (\neg a \rightarrow \neg c), ( \neg c \rightarrow b), a\vee \neg \vee b \vee c, \neg(a \neg \wedge b \wedge c)   \vDash \square$.

## Resolución de preposiciones
Para resolverlo únicamente debemos hacer el algoritmo de Davis-Putman. Donde buscamos literales que sean siempre positivos o negativos en todas las clausulas dadas, y jugar con ellas hasta obtener la contradicción. (Ojo debemos clausular antes las formulas y para ello debemos quitar las implicaciones).

> No me es viable poder mostrar un ejemplo en esta plataforma, recomiendo buscarlo en internet.
{.is-info}

## Traducir
Para traducir unicamente debemos entender el lenguaje normal, saber que es una implicación o que es una negación cuando el texto lo presenta.

# Lógica de Predicados
En este apartado, ya o solo usamos literales, si no que también usamos funciones y cuantificadores.

Para hacer esto debemos entender que son estas cosas
## Alfabeto
El alfabeto de primer orden se compone en:
- C: Simbolos constantes.
- V: Variables.
- F: Simbolos de funcion (Devuelver verdadero o falso).
- R: Simbolos de relación (Como sumar dos numeros o lo que nos diga).

Además tenemos los contectores como antes y los cuantificadores para tdoo ($\forall$) y existe ($\exists$).

## Clasificación
Al igual que en el anterior tema tenemos otras clasificaciónes:
- Válidas: Para toda valoración es verdad.
- Satisfacible: Para algunas valoraciones es verdad.
- Refutable: Para algunas valoraciones es falsa.
- No válida, para algunas interpretaciones es falsa.


En este tipo de ejercicios, nos suele dar una fórmula y debemos interpretarla según el alfabeto dado o viceversa, dos dan en un enunciado y lo debemos expresar en el lenguaje dado.

Aquí no hay trucos, lo ideal es practicar.

Sin embargo también nos pueden preguntar respecto a Forma Normal de Prenexa, Forma Normal de Skolem y Forma Clausulada.

## Formas normales
Las formas normales, es dado un fórmula transformarla y reducirla en las formas más simple que nos pidan.
### Forma normal Prenexa
Consiste en una formula donde todo los cuantificadores están al principio.

### Forma normal de Skolem
Los cuantificadores existenciales desaparecen y son interpretados por los para todos anteriores si tuviera.
- $\forall x \exist y (Q(x,y)) = \forall x (Q(x,f(x))$.
- $\exist y \forall x (Q(x,y)) = \forall x (Q(x,a))$.

### Forma normal clausulada
Es lo que hemos estado haciendo en el team anterior, dividir las formuals en $\wedge$.
(en este punto ya los $\forall$ no hace falta escribirlo porque se sobre entiende).
> Ojo, los $\forall x$ se pueden juntar con otros $\forall x$ siempre y cuando hay aun $\wedge$ en medio, al igual pasa con $\exists y$ se puede juntar con otros $\exists b$ si hay $\vee$.
{.is-warning}

# Unificación y Resolución
Unificar y resolución suelen pedirnelos tras el punto anterior, y suele ser una vez tenga clasulada la fórmula intentar buscar una interpretación que sea insatisfacible por el método de la reducción a lo absurdo. Sin embargo la diferencia con el tema 2, es que aquí no tenemos literales, sino variables y constantes y el método cambia.

Es por ello que vamos a buscar las Clausulas de Horn
## Clausulas de Horn
Las caracteristicas de estas clausulas es que solo hay 1 o menos literales positivos.

Con este tipo de clausulas las resoluciones son mucho más sencilla ya que siempre partiremos de una clausula con todo negativo y tendremos algúna que sea unica positiva, nuestro objetivo.

Mientras resolvamos debemos tener en cuenta una cosa.
- Las variables (x,y,z,t), podemos cambiarla por otras variables o constantes e incluso aplicarle formulas, por ejemplo $x|f(a)$, todas las que eran x en esa clausula ahora son $f(a)$.
- Sin embargo las constantes nunca podremos cambiarlas, se quedan fijas.

# Inducción y Recurrencia
Este tema suele ser uno de lo más confusos, aquí hay un resumen rapido para intentar aplicar las normas más fundamentales.

Se divide en dos:
## Inducción
La parte de inducción se estructura internamente en:
- Caso base: Según lo que nos pida debemos comprobar que se cumple para el valor más basico posible, normalmente 0 o 1.
- Hipotesis de inducción: Aquí es recomendable poner: "Suponemos que (lo que queramos comprobar) es verdad, para todo $m \in \{1,2,3\dots n\}$". Con esto tenemos todo listo para empezar.
- Demostración: Aquí ya debemos cambiar las formulas que teniamos por (normalmente) $n+1$.

> Este tipo de ejercicio me lia personalmente, por lo tanto solo está descrito la parte más "sencilla".
{.is-info}
## Recurrencia
En el caso de Recurrencia tenemos una secuencia y debemos sacar su expresión recurrente, para elo hacemos:
- Polinomio caracteristicico de la homogenea: Sería esa expresión que es recurrente, pero unicamente aquellas partes donde esté $x_n$.
- Polinomio característico: Serían las raices del polinomio anterior + aquellas raices que hayamos obtenido de las expresiones que hayamos quitado, por ejemplo: Si teneamos un $A^n$, siendo $A$ una constante, entonces otra "raiz" sería $x-A$.
- Solución general, aquí debemos hacer una ecuación donde haya tantas incognitas como raices nos haya salido, con la forma de $A*(x)^n$, siendo $x$ la raíz, en caso de que se repite alguna tendriamos $A*(x)^n + B*n*(x)^n$.

Cuando estemos con la solución general, podemos sacar terminos con los valores de la recurrencia ya dados por ejemplo si nos dan $x_0 = 1$, entonces sustituimos con $n=0$ y la expresión la igualamos a 1, nos saldrá un sistema de ecuaciones que deberemos resolver con el metodo que deseamos.
# Grafos
Este es el último tema de la asignatura, y es importante este tema ya que se seguirá usando sus principios más adelante en la carrera. Debemos tener en cuenta una serie de cosas.
## Caracteristicas de los grafos
Simbologia:
- Vertices: Aquellos puntos de donde salen las aristas.
- Aristas: Son las zonas de donde salen los "caminos" hacia otros vertices.
- Caras: Es el espacio que queda entre las distintas aristas del grafo.

Isomorfo: Dos grafos son isomorfos si tienen el mismo numero de lados, vertices, los vertices son iguales en grados y comparten los mismos vecinos.
Conexo: Se dice que es conexo cuando por cada par de nodos hay un camino entre ellos, es decir no hay islas flotando.
Grados: Es la cantidad de aristas que salen de un vértice dado.


Para saber la cantidad de lados, en base a grados, lo que hacemos es sumar todos los lados y dividirlo entre 2. $l =\frac{1}{2}\sum g$, siengo $g$ los grados.

Los grafos $K_n$: Son aquellos grafos que tienen tantos vértices como $n$ tenga, y están todos los vértices conectados uno a otro, es decir sus lados son: $l=\frac{n*(n-1)}{2}$.

Una formula que debe cumplir es $n-l+c=2$.
## Grafos dado por matrices
Cuando nos dan un grafo por una matriz, debemos tener en cuenta lo siguiente:
Dada una Matriz A.
- La Matriz siempre es simetrica respecto a la diagonal principal, es por ello que para saber los valrores de un vértice podemos mirarlo como fila o como columna.
- Los valores de cada fila o columna, son los aristas que salen de ese vertice hacia los demás.
Dada una matriz $A^{2}$:
- En este caso, tenemos una matriz representará los caminos de longitud 2 entre un vértice y los demás, a excepción de la diagonal principal, que nos dirá el grado del vértice.

Dada una matriz $A^{n} siendo \text{ }n\geq 2$:
- Nos mostrará los caminos de longitud $n$ entre un vértice y los demás.

Para obtener un camino de longitud $x$ entre dos vértices distintos $v_a$ y $v_b$, unicamente debemos multiplicar la fila de $v_a$ por la columna $v_b$, eso sí debemos tener en cuenta que la suma de los exponentes de esas matrices, nos dará la longitud.

## Grafos bipartitos
Son aquellos grafos que podemos dibujar de manera que una parte de ellos esté a la izquierda y otros a la derecha, y entre esas partes formadas, no haya ninguna arista que vaya entre ellas.

También podemos definirlo como aquellos grafos donde no hay ciclos de 3.
## Cuando tenemos un grafo
Para deducir si tenemos un grafo tenemos que usar el método de Havel-Hakimi (HH), que consiste en:
- Ordenamos los grados de mayor a menor.
- Si devuelve 0 es grafo, en cualquier otro caso no es grafo.
- Lo que hacemos es eliminar el primer valor que tengamos y restamos 1 en tanto valores como valor tenga el que hemos eliminado. Por ejemplo si teniamos 43322, al quitar el 4, nos queda 2211, pero al quitar el siguiente 2, nos queda 111.

## Euler
Un grafo de euler es aquel que nos permite ir por todas las aristas.
Cuando nos pregunten de euler debemos saber que:
- Los circuitos de Euler solo existen cuando todos los grados son pares.
- Los caminos de Euler solo existen cuando todos los grados son pares a excepción de 2, que será el comiendo y el fin del circuito.
## Hamilton
Por otro lado Hamilton, es aquel que nos permite ir a todos los vértices.

El problema es que no tenemos un algoritmo eficiente para calcularlo, por ello el mejor método es dibujar el grafo e intentar buscar una manera para ir hacia todos.
Normalmente es recomendable dejar para el final algún grado que tenga lados con todos los demás vertices, pero es un problema $NP$.

## Grafos planos
Los grafos planos son aquellos que podemos dibujar sin que ninguna arista choque entre ella. Para poder saber si un grafo es o no plano, podemos:
- Fórmula $l\leq 3n-6$, siendo $l$ el número de lados y $n$ el número de aristas.
- Teorema de Kuratowski, un grafo es plano si al contraerse no forma ni $K_5$ ni $K_{3,3}$

## Coloración
Cuando nos pregunten por el **número** cromatico, debemos recordar que este es el valor mínimo de colores con el que podemos dibujar todo el grafo. Podemos hacerlo o bien con el dibujo o bien sabiendo que vértice va a cada vértice.

Por otro lado.
Cuando nos pregunten por el **polinomio cromático**, aquí ya comienza a ser un problema $NP-Completo$, y solo tenemos un algoritmo para hacerlo aunque no sea eficiente.
El algoritmo es el siguiente:
$p(x,G) = p(x,G'_e)-p(x,G_e)$.
Esto es:
- $p(x,G)$: El polinomio que estamos buscando
- $p(x,G'_e)$: El grafo resultando si le quitamos una arista. 
- $p(x,G_e)$: El grafo si unimos los vértices de la arista que hemos quitado.

Claro esto crea un problema de recurrencia, pero debemos saber que:
Cuando tenemos un grafo que es una linea recta con distitnos vértices puestos en ella, entonces: $p(x,G) = x(x-1)^n$, según la cantidad de linea que tengamos.
Si llegamos a un cuadrado: $p(x,G) = x(x-1)^3-x(x-1)(x-2)$.

Con esto intentaremos sacar el polinomio.
> Si cae la coloración, es altamente problable de que sea el ejercicio dificil del examen.
{.is-warning}

## Arboles
Los arboles son aquellos grafos donde a partir de un vértice principal, podemos llegar hasta los demás en una forma de arbol invertido. 
Algunas de las caracteristicas de los arboles es:
- Siempre tiene vertices con grado 1.
- Es un grafo que no tiene ciclos.
- $l=v-1$. Siendo $l$ los lados y $v$ el número de vértices.