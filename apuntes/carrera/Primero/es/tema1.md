---
title:  Estadística descriptiva unidimensional
description: 
published: true
date: 2026-03-03T17:11:15.792Z
tags: 
editor: markdown
dateCreated: 2026-02-24T19:57:28.469Z
---

#  Estadística descriptiva unidimensional

La Estadística recoge una gran diversidad de técnicas encaminadas a analizar esta información por medio de la observación y la experimentación.
La Estadística estudia una serie de procedimientos: Recogida, Resumen, Análisis y Interpretación.

## Clases de fenómenos
Podemos clasificar los fenómenos en dos grandes categorias:
- Deterministicos: Bajo mismas condiciones iniciales siempre sucede lo mismo.
- Aleatorios: Bajo las mismas condiciones iniciales, hay resultados diferentes.

La Estadística Descriptiva, se encarga de organizar, resumir y presentar, conjuntos de datos mediante tablas, gráficos y medidas numéricas que permite comprender sus características principales.
## Conceptos de la estadistica
En el ambito estadistico solemos usar lo siguiente:
- Población, consiste en el conjuntos de individuo que cumple una propiedad comunes. Dentro de esto tenemos:
    - Individuo: Cada sujeto
    - Tamaño de poblaicon: Total de individuos (n).

- Muestra: Subconjutno representativo de una población.

- Caracteres: Propiedades, rasgos o cualidade que poseen los individuos.

- Modalidades: Valores que puede tomar un caracter. Ejemplo longitud de la altura, son todas las posibles longitudes obtenibles.

Los caracteres podemos clasificarlo aún más, esto lo podemos clasificar en:
- Cualitativos / Atributos: Modalidades no numéricas, por ejemplo color de pelo. 

Tenemos Nominales (No admite orden natural), y Ordinales (Establece orden o grado entre las modalidades).


- Cuantitativos: Modalidades numéricas. 

Tenemos Discretos (Valores aislados, no hay decimales) y Continuos (Cualquier valor dentro de un intervarlo, puede haber decimales).

Las cuantitativas discretas suelen ser las cuentas de, es decir enteros, mientars que el continuos son mas peso, temperatura, altura, cosas que permiten decimales.


### Variable estadística
Una variable estadística (v.e.), consiste en una representación matemática de un carácter, solemos usar x,y,z.

Dependiendod e las clasificación de caracteres ahora tenemos las variables estadisticas:
- Cualitativas
- Cuantitativos.

Cuando ya tenemos todos los datos, idealmente lo que ahremos serán usar una serie de herramientas muy utiles, las cuales son:
- Tablas de frecuencias.
- Representaciones gráficas.
- Representaciones numéricas.

## Tablas de frencuencias o distribución de frecuencias
Es una tabla formada por columnas, donde ponemos las variables y después ponemos los datos. Dicho más bonito:
- Tabla donde se ordena y clasifica la información que encierra los datos en base al número de veces que se repiten.

Dentro de esta tabla tenemos cuatro frecuencias, pero solo usaremos 2 si es cualitativas.
- Frecuencia absoluta ($n_{i}$): Nº de veces que se repita la modalidad $x_{i}$.
- Frecuencia relativa ($f_{i}$): Proporción de individuos que presentan modalidad $x_{i}$. Es decir hacer= $f_{i}=\frac{n_{i}}{n}$

A partir de aqui añadimos las de cuantitativas.
- Frecuencia absoluta acumulada ($N_{i}$): Que consiste ne el número de veces que se presenta esta modalidad.
- Frecuencia relativa acumulada ($F_{i}$): Similar al anterior.

### Tablas de frecuencias para v.e. continuas
Cuando tenemos v.e. continuas (Es decir cuantitativos continuas, con decimales), tenemos que modificar una serie de cosas, estas modificaciones son las siguientes:
- Los datos se agrupan en clases o intervalos de valores.
- Extremos de clase : Valores extremos que determiann una clase $I_{i}$, es decir $e_{i-1}$ y $e_{i}$.
- Marca de clase ($x_{i}$): Punto medio del intervalo $x_{i}=\frac{e_{i-1}+e_{i}}{2}$.
- Amplitud del intervalo ($a_{i}$): La diferencia entre sus extremos $a_{i}=e_{i}-e_{i-1}$.
- Densidad de frecuencia ($h_{i}$): Número de individuos en la clase por unidad de amplitud: $h_{i}=\frac{n_{i}}{a_{i}}$. Util cuando los intervalos no son regulares.

## Representación gráficas
La información obtenida anteriormente, la podemos representar en una tabla, lo cúal es lo más sencillo para poder mostrarlo.

Dependiendo de que tipo de datos tenemos unos o otros modos de gráficas, que son:
- Datos cualitativos: Diagrama de sectores o diagrama de barras.
- Datos cuantitativos: Diagrama de barras (Discretas) o diagrama histograma (Continuas, decimales)

### Diagrama de sectores
Para este tipo de diagrama, nos hace falta $\alpha$, que la obtenemos:
$\alpha_{i}=360*\frac{n_{i}}{n}$ o $360*f_{i}$.
### Diagrama de barras
No es necesario hacer ningun calculo extra.
### Histograma
Consiste realmente en un diagrama de barra, lo unico que todo está junto y se usa de dato

## Representaciones numéricas
La información presentada en la distribuciones de frecuencia se puede sintentizar en medidas o cantidades numéricas. Tenemos:
- Medidades de posición y tendencia central: Podemos observar el comportamiento global de los datos observados y localizar el centro de distribución.
- Medidas de dispersión: Determinan la variabilidad de los datos de distribución y de la maor o menor representatividad de las medidas de posición central.
- Medidas de forma: Reflejan la distribución.

Ahora explicaremos en detalle las distintas medidas.
### Medidas de posición.
Se llaman medidas de posición, tendencia central o centralización, a los valores numéricos donde se agrupan de mayor o menor medida. POdemos encontrar dos clases centrales:
- Medidas de posición centrales, con medida aritmética (miden el centro), mediana (la mitad) y moda (el valor más frecuente).
- Medidas de posición no cenrales: Solo tenemos los cuantiles que miden porcentajes.

La media aritmética es aquella media que solemos hacer para saber que nota tenemos en el examen. La forma de calcular la media es: $\overline{X}=\frac{1}{n} \sum x_{i}n_{i}$.

Básicamente es la suma de todos los valores entre el número de casos que hay.


La moda por otro lado es el valor que mas se repite o valor más usual en una distribuciión. Normalmente lo haremos gracias a $n_{i}$.
Sin embargo si lo datos nos lo dan en datos continuos, entonces tenemos usar $h_{i}$ que la obtenemos con $h_{i}=\frac{n_{i}}{a_{i}}$.
Para poder saber exactamente cual es la moda exacta es mediante la siguiente formula.
$M_{o}=I_{i-1}+\frac{h_{i}-h_{i-1}}{(h_{i}-h_{i-1})+(h_{i}-h_{i+1})}a_{i}$.

La mediana es aquel centro posicional del conjunto de los datos. Lo que hacemos es ordenarlos de menor a mayor, y tras eso hacemos $\frac{n}{2}$, diferenciando dos casos.
- Si no es entero, redondeamos al entero siguiente, siendo $Me=x_{i}$.
- Si es entero, entonces $Me=[x_{i},x_{i+1}]$.

En caso de tener datos discretos, nos fijaremos en $F_{o}$ y debemos ver:
- Si existe un valor exacto que sea $F_{o}=0.5$, la mediana sería la media entre ese valor y el siguiente.
- Si no existiera ese valor, sería aquel valor que supere por primera vez en 0.5.

En caso de datos continuos, la mediana sera aquel valor que supere $F_{i}$ por primera vez, y se hace la siguiente formula:
$M_{e}=I_{i-1}+\frac{\frac{n}{2}-N_{i-1}}{n_{i}}a_{i}$ O $M_{e}=I_{i-1}+\frac{\frac{1}{2}-F_{i-1}}{f_{i}}a_{i}$.


#### Cuantiles
Los cuantiles son aquellos variables $X$ como valor de la variable que acumula el $\alpha*100%$ de la distribución.
Es como dividir los datos, dentro de esto encontramos:
- Cuartiles: Donde dividimos la distribución en 4 partes iguales.
- Deciles: DOnde dividimos la distribución en 10 partes iguales.
- Percentiles: Donde dividimos la distribución en 100 partes iguales.

Para poder cálcular los percentiles lo que hacemos es ordenar los datos de menor a mayor, tras esto calculamos $\frac{kn}{100}$.
- Si el valor no es un número entero, entonces lo redondeamos al siguiente y $P_{k}=x_{i}$.
- Si fuera entero, entonces $P_{k}=[x_{i},x_{i+1}]$.


Para poder calcular los cuantiles lo que podemos hacer es:
- $\frac{n*k}{100}$, siendo n el número total de variables y k el percentil deseado. Y el valor que nos dé lo buscamos en $N_{i}$, siendo justo el siguiente al valor que tenemos.
- Directamente buscamos lo buscamos en $F_{i}$, hasta llegar al que deseamos.

Debemos tener en cuenta que en k puede ser 25 cuando hablamos de cuartiles, 10 cuando hablamos de deciles o 1 cuando hablamos de percentiles.

Cuando ya hemos calculado en el anterior, podemos tener dos situaciones:
- El valor no está en nuestra tabla, por lo tanto cogemos el siguiente y nuestro percentil será $\overline{X_{i}}$.
- El valor está en nuestra tabla, por lo tanto nuestro valor será justo la media del mismo y el siguiente.
### Medidas de dispersión
Las medidas de dispersión nos sirve para determinar si los datos están muy dispersos o están más juntos. Esto lo podemos clasificar en dos grupos:
- Medias de dispersión absolutas: La usamos para poder analizar la variabilidad de una única distribución de frecuencias.
- Medidas de dispersión relativa: Nos sirve para medir la variabilidad de cocientes (proporciones), donde comparamos varias variables.

En las medidas de dispersión absoluta tenemos:
- El rango ($R$ o $max$), que consiste en la diferencia entre $max\{x_{i}\}-min\{x_{i}\}$.
- El rango intercuartílico ($RIQ$), es igual pero lo que hacemos es $Q_{3}-Q_{1}=P_{75}-P_{25}$.
- Varianza ($\sigma^{2}$ o $Var(X)$), se define como $\frac{1}{n}\sum (x_{i}-\overline{X})^{2}*n_{i}$ o la mas utilizada que es $\frac{1}{n}\sum x_{i}^{2}*n_{i}-\overline{X}^{2}$.
- Desviación típica: Se define como $\sigma = +\sqrt{ \sigma^{2}}$.


Al tener unos datos muy juntos o dispersos, (no lo sabemos), lo que hacemos es hacer una medida que nos permite calcular la medida de dispersión