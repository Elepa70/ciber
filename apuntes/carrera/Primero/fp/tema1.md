---
title: Introducción
description: 
published: true
date: 2025-10-07T18:36:39.033Z
tags: 
editor: markdown
dateCreated: 2025-09-29T19:32:27.944Z
---

# Introducción
> Hasta que los apuntes del profesor sean subidos a la plataforma de prado, puede haber incoherencias o expresiones que no deberían estar escritas.
{.is-warning}

En este tema vamos a ver los primeros pasos hacia la programación, sin embargo, es esencial hablar primero de los componentes del ordenador y demás cosas.
## Componentes
Los compenentes básicos de un ordenador son los siguientes:
- Hardware: Es la parte física del ordenador.
- Software: Es la parte lógica o intangible del ordenador.
- Periféricos: Son aquellas conexiones de entrada y salida de los ordenadores, ejemplo teclado o monitores.

## Algoritmos
Los algoritmos son una **secuencia** de instrucciones bien definidas que resuelven un problema concreto. Un programa del ordenador se puede considerar un software que implemente un algoritmo.

Todos los programas tienen un progreso que suele ser:
- Diseño: Se piensa y planifica la necesidad y estructura general del código.
- Codificar/Implementar: Consiste en escribir o desarrollar el código pensado anteriormente.
- Depurar: Es optimizar o arreglar errores que han surgido anteriormente.
- Mantener: Es la vuelta al ciclo, donde deberemos mantener vivo nuestro programa.

Los programas tienen una serie de caracteristicas
### Básicas
- Correcto: No debe tener errores
- Básicas: Sin ambigüedad
- Fiable: Siempre se obtiene el mismo resultado con **las mismas condiciones**.
### Esperable
- Finito: El programa debe finalizar en algún momento.
- Validez: El programa debe ser útil y resolver algún problema.
- Eficiencia: El tiempo de ejecución del programa debe ser aceptable.


## Lenguaje de programación
Los lenguaje de programación, es el mecanismo por el cuál somos capaces de interactuar con el equipo para poder realizar los algoritmos o programas. Estos lenguajes están divididos en tres:
- Lenguaje máquina: Consiste en la programación más antigua que existe, y es donde se trabaja con 0 y 1, de forma binaria y pura. Es la forma más eficiente pero la más compleja que existe.
- Lenguaje de bajo nivel: Estos lenguajes comenzarón traduciendo conceptos a binario, dando una facilidad a la hora de poder programar, algunos ejemplos son Cobol o C.
- Lenguaje de alto nivel: Estos lenguajes son los "amigables", donde no es necesario tanto detalles técnicos para que funcionen, sin embargo requieren de compilador o intérprete.

Estos compiladores o intérpretes, son traductores del código al lenguaje máquina:
- Compilador: Crea un archivo binario (O ejecutable), en base a la documentación o código fuente.
- Interprete: Consiste en un traducto de línea por línea, que transforma la orden o código en lenguaje máquina. Esto se puede ver con Java. 

Todos los lenguajes mencionados tienen un conjunto de instrucciones, que se definen en acciones o operacioens que realiza el ordenador. 

Estas instrucciones pueden ser básicas como:
- Entrada y salida: Información que viaja entre los perifericos y la memoria del equipo.
- Instrucción de calculo: Operaciones aritmetícas y lógicas que realizan los equipos.
- Instrucción de control: Modificar la secuencia de ejecución de control y flujo.

## Especificación de programar
Ahora si vamos a entrar con la programación propiamente dicha.

Un programar se realiza en uno o varios ficheros, siendo editado según la sintaxis determinada del lenguaje de programación.

Según los errores, podemos encontrar tres situaciones:
- Compilación: Error de escritura y no es posible que el programa se convierta en binario.
- Ejecución: El programa está mal escrito, resultando en errores al ejecutarse.
- Lógicas/Semánticas: El programa realiza una acción la cuál no es la deseada.

Una vez visto los errores, vamos a ver una estructura básica para evitar que suceda:
- En la primera cabecerá vamos a tener la inclusión de librerias, siendo esto utilidades al programa normalmente diseñado por las comunidades de programadores.
- La segunda cabecerá suele estar reservada para las variables que definamos.
- Por último tenemos las funciones principales (Definida como: int main(){ return 0 }). Return 0, es usado para asegurarnos que hemos obtenido un fin de codigo sin errores.

## Datos y variables
Los datos consiste en la unidad de información que podemos representar en el ordenador.

Hay que tener en cuenta que a la hora de programar, según nuestro lenguaje, podemos encontrar una diferencia entre tipado y no tipado.
- Los lenguajes tipados: Son aquellos donde los datos son necesarios definirlos.
- Los lenguajes no tipados: Son aquellos donde, debido al contexto, no es necesario definirlo.

Esto es importante ya que podemos encontrar varios errores graves, como expresar $2$ como número o como caracter alfanúmerico.

Otra caracteristica de los datos es que podemos encontrar:
- Los datos basicos: Integrados por los lenguajes de programación, como es numero, caracter o booleano.
- Los datos definidos por los usuarios: Donde es el usuario o el programador, el que le da un significado.
- Punteros: Este tipo de datos es especial, ya que se encarga de apuntar a la memoria, más adelante en el curso se le dará la importancia necesaria.


Algunos ejemplos de tipos de datos son:
- Numeros enteros, donde podemos encontrar los int(Enteros), short(Enteros en un rango menor a int), long (Enteros mayor a int) o el termino unsigned, usado delante de los demás terminos para indicar que solo se tomarán valores positivos. (No se aclará si el 0 entra)

- Reales, aquellos números donde podemos tener decimales, ya sean simples o dobles. Se aconsejan usar siempre dobles.

- Booleano, este tipo de datos, solo puede tomar dos valores, verdadero (1) o falso (0)

## Operador y expresión
La operación de asignación es el metodo que poseemos para poder almacenar valores en variables. La acción es destructiva, es decir, si ya tenia un valor con anterioridad, con una nueva asignación vamos a pisar lo que teniamos. 

En una asignación, primero lo que hacemos es resolver la ecuación o auqello que esté a la derecha, para poder asignarlo a la variable o a la izquierda.

Poseemos la sintaxis:
```C++
nombre_variable = 12;
```

Las expresiones son una serie de caracteres que nos sirve para obtener un valor. Estos caracteres los definimos como:
### Aritméticos
Dentro de las expresiones aritmeticas encontramos:
- Suma (+)
- Resta (-)
- Multiplicación (*)
- División (/)
- Resto (%)
- Incremento (++)
- Decremento (--)

También podemos usar expresiones especiales para asignarle a una variable un "calculo".
- Sumarle el valor deseado (+=)
- Restarle el valor deseado (-=)
- Multplicar el valor deseado (*=)
- Dividir el valor deseado (/=)
- Resultado del modulo el valor deseado (%=)

### Relacionales
Las expresiones relaciones son aquellas que nos dará como resultado verdadero o falso:
- Menor que (<)
- Menor igual que (<=)
- Mayor que (>)
- Mayor igual que (>=)
- Igual (==)
- Distinto (!=)