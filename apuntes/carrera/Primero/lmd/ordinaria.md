---
title: Resumen para Examen
description: 
published: true
date: 2026-06-18T11:33:48.822Z
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
> Ojo, los $\forall x $ se pueden juntar con otros $\forall x$ siempre y cuando hay aun $\wedge$ en medio, al igual pasa con $\exists y$ se puede juntar con otros $\exists b$ si hay $\vee$.
{.is-warning}

# Unificación y Resolución
# Inducción y Recurrencia
# Grafos
