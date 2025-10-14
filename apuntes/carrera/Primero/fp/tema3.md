---
title: Estructuras de control
description: 
published: true
date: 2025-10-14T16:07:08.415Z
tags: 
editor: markdown
dateCreated: 2025-10-14T15:39:08.081Z
---

# Estructuras de control
## Estructuras repetitivas
Los ordenadores tienen un diseño donde nos permite repetir una serie de acciones, estas acciones lo llamaremos "bucle". 

> Cada ejecución de las instrucciones de un bucle, se llama iteración.
{.is-info}


Debemos tener en cuenta una serie de cosas a la hroa de diseñar un bucle:
1. ¿Contenido del bucle?
2. ¿Veces a ejecutar el bucle?
3. ¿Condición de parada del bucle?


Tenemos unos 3 bucles:
- While: Estructura de mientas
- While_do: (Rellenar)
- For: Forma mas especial


## While
El bucle while se repite **siempre y cuando** se cumpla la condición. Antes de entrar también se evalúa la condición.

```C++

#include <iostream>
using namespace std;
int main()
{
    int suma;
    suma = 0;
    while (suma <= 5){
        cout << suma << endl;
        suma+=1;
    }
    return 0;
}
```

## Do-While
Se traduce como hacer mientras, y aunque parezca similar al while, tenemos una diferencia.

En este tipo de bucle, siempre se va a ejecutar **al menos** una vez, y si la condición se cumple, se continua en el bucle. 

```C++
#include <iostream>
using namespace std;
int main()
{
    int n;
    
    do {
    	cout <<"Introduzca el valor";
    	cin >> n;
    } while (n<=0);
    return 0;
}
```
