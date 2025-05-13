---
title: Untitled Page
description: 
published: true
date: 2025-05-13T09:55:51.024Z
tags: 
editor: markdown
dateCreated: 2025-03-16T21:41:56.033Z
---

*[HTML]: Hyper Text Markup Language
*[W3C]:  World Wide Web Consortium
The HTML specification
is maintained by the W3C.





- [**Apuntes**](/apuntes)
- [**Proyectos**](/proyectos)
- [**Políticas legales**](/politicas)
- [**Sobre Mí**](/mio)
- [**Contacto**](/contacto)
- [**Otros**](/otros)
  {.links-list}

| Sección      | Descripción          |
|------------- |---------------------- |
| **Apuntes**  | Material académico   |
| **Proyectos**| Portafolio personal  |
| **Contacto** | Formulario y redes   |

\documentclass[11pt,a4paper]{report}
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage{graphicx}
\usepackage{amsthm}
\usepackage{tikz}
\usepackage{cancel}
\usepackage{ragged2e}
\usepackage[left=2.5cm,right=2cm,top=2cm,bottom=2cm]{geometry}
\usepackage[hidelinks]{hyperref}

\title{Cálculo}
\author{Trevor Chen Zhang}
%\date{Julio de 2023}

\begin{document}

\maketitle
\tableofcontents
\chapter{Introducción}
\section{Contexto histórico}

En estos apuntes vamos a hablar de un tema muy importante en matemáticas, las derivadas e integrales. A pesar de su gran peso en las matemáticas, no fueron creadas por solo matemáticos, fueron creados por el gran físico Newton y el matemático Leibniz. Newton tenía grandes ideas, pero no tenía las herramientas para trabajar, entonces fue cuando creó las matemáticas para poder seguir con sus investigaciones, dando así, una nueva rama en las matemáticas. \newline

Hoy en día, las derivadas e integrales juegan un papel muy importante en la sociedad. Por ejemplo, gracias a las derivadas, podemos diseñar carreteras, edificios, enviar y recibir ondas electromagnéticas para comunicarnos, etc. Además, las derivadas tienen otros usos como por ejemplo ver cómo varía una función. Por poner un ejemplo, si tenemos una función que nos describe la posición de un objeto a lo largo del tiempo, entonces, si la derivamos con respecto el tiempo, obtenemos cuál es la velocidad instantánea en ese momento.

\section{Conceptos}

En esta sección vamos a explicar algunos conceptos importantes para entender estos nuevos conceptos.

\subsection{Límites}

En matemáticas, usamos herramientas para ver lo que pasa lo que ocurre cuando nos acercamos mucho a un punto o lo que ocurre en el infinito. Por ejemplo, cuando estudiamos una función como por ejemplo $f(x)=1/x$, todos sabemos que no está definida en $x=0$, pero eso no significa que no podamos estudiar lo que pasa en ese punto. Por ejemplo, es una aberración escribir $f(x)=\infty$ porque no tiene sentido, pero en efecto, podemos estudiar lo que sucede cerca. Tenemos dos lados por donde acercarnos, desde la derecha o desde la izquierda. Si lo hacemos por la derecha, nos estaremos acercando mediante números mayores que el punto, y si lo hacemos desde la izquierda, lo haremos mediante números menores que este, y es por eso que usamos la siguiente notación
$$\lim_{x\to 0^{-}}f(x) \text{ y }\lim_{x\to 0^{+}}f(x)$$

Ahora que tenemos esta nueva herramienta, podemos ver lo que pasa con la función. En vuestro nivel, está permitido darle un valor a la función y después hacer deducciones. Por ejemplo
$$f(0.001)>0\Rightarrow \lim_{x\to 0^{+}}f(x)=+\infty.$$
$$f(-0.999)>0\Rightarrow \lim_{x\to 0^{-}}f(x)=-\infty.$$

La diferencia reside en que no estamos diciendo que la imagen de un punto es infinito, lo que estamos diciendo es que a medida que nos acercamos a ese punto, la función tiende a $+\infty$ desde la derecha y por la izquierda tiende a $-\infty$.

En estos apuntes no nos vamos a centrar en cómo resolver límites, pero básicamente hay ya ciertos métodos para resolverlos. Por ejemplo, si tenemos una indeterminación del tipo 0/0, entonces podemos aplicar la regla de L'Hôpital-Bernoulli o intentar simplificar la raíz común en el numerador y denominar; o si tenemos una indeterminación del tipo $\infty-\infty$, multiplicamos y dividimos por el conjugado, etc.\newline

Es importante utilizar correctamente la notación de límites porque a veces se nos puede olvidar escribir $f(x)$ o hacia dónde tiende el límite. Sin embargo, no es tan importante escribir el signo encima del número porque al no escribirlo, estamos diciendo que nos acercamos a la vez por la derecha y por la izquierda. Si lo calculamos por separado y coinciden los límites, entonces decimos que existe el límite y ese valor que hemos obtenido es el valor del límite.\newline

También es importante tener en cuenta que no es lo mismo el valor del límite y el valor de la función. Por ejemplo, si definimos una función a trozos, en los puntos de ruptura, es posible que los valores en ambos extremos no coincidan; o por ejemplo, si tenemos la indeterminación 0/0 donde no está definida la función en ese punto, lo que pasa es que el límite exista, pero la función no está definida.\newline

En conclusión, cuando trabajamos con límites, no estamos diciendo que la función valga tal en un punto, lo que en verdad estamos diciendo es que la función tiende a un valor cuando nos acercamos a ese punto (o $\pm\infty$). Como consecuencia podemos definir que una función es continua en un punto $a$ si y solo si
$$\lim_{x\to a^{-}}f(x)=\lim_{x\to a^{+}}f(x)=f(a)$$

\subsection{Funciones continuas}

Ahora que entendemos mejor los límites, podemos estudiar la continuidad de una función.

En matemáticas decimos que una función es continua en un punto $a$ si y solo si
$$\text{Sea }f \text{ una función  }f:A\to \mathbb{R}$$
$$\text{Dado } \varepsilon >0\text{, } \exists \delta >0\text{ } /\text{ } \forall x\in A, \text{ si }|x-a|<\delta\Rightarrow |f(x)-f(a)|<\varepsilon$$

Esta es la definición de continuidad en un punto, pero es demasiado compleja para el nivel que se espera que tengas en estos niveles, pero utilizando algunas caracterizaciones, podemos decir que una función es continua si y solo si

$$\lim_{x\to a^{-}}f(x)=\lim_{x\to a^{+}}f(x)=f(a)$$

Ahora que tenemos más conocimientos teóricos, vamos a explicar con más detalles ambos puntos.

\begin{itemize}
    \item Definición de continuidad: En primer lugar, $\varepsilon$ y $\delta$ se utilizan en general para indicar distancias casi insignificantes. Para esta definición, lo que hacemos es tomar el valor que queramos de $\varepsilon$, entonces, si la función es continua en el punto $a$, tendremos en el eje $OY$ un intervalo $(f(a)-\varepsilon,f(a)+\varepsilon)$ y eso estará asociado a un intervalo $a-\delta,a+\delta$ donde la imagen de todos los puntos de ese intervalo estará en el intervalo que hemos mencionado del eje $OY$. Para entender mejor esta definición, es mejor mirar qué ocurre cuando la función no es continua en el punto $a$.

    \includegraphics[scale=0.5]{Ejemplo de discontinuidad en un punto.png}

    En el eje $OY$ tomamos un intervalo cualquiera, por ejemplo el intervalo $(1,3)$, ahora en el $OX$, si la función es continua en ese punto, debemos ser capaces de encontrar un intervalo $(4-\delta,4+\delta)$, en el que las imágenes de estos puntes tengas sus imágenes en el primer intervalo definido. Como podemos observar esto es imposible que ocurra, puesto que a la derecha de 4, las imágenes se salen de este intervalo. Si la función fuera continua, entonces, da igual lo pequeño que sea nuestro $\varepsilon$, que habrá un intervalo de radio $\delta$ en el que las imágenes de los puntos de este intervalo estén en el de radio $\varepsilon$.
    
    \item Caracterización: Esta es más sencilla de entender, \textit{grosso modo}, nos acercamos al punto por ambos lados, si los límites no coinciden, entonces no puede ser continua porque por un lado nos da un valor, y por el otro nos arroja otro valor diferente. Básicamente, si los límites no coinciden, entonces al dibujar la función, en el punto donde los límites no coinciden, tendremos que levantar el lápiz del papel. Cabe a destacar que hablamos de continuidad solo en el dominio de una función, es decir, la función $f(x)=1/x$ es continua. ¿Cómo puede ser continua si en 0 se va a infinito? Como hemos mencionado anteriormente, la función solo puede ser continua en su dominio, luego en el 0, al no estar definida la función, no hablamos de este punto. Sin embargo, si queremos dar el conjunto de puntos donde la función es continua, sí que tenemos que excluir el 0.
\end{itemize}


\chapter{Derivadas}
En primer lugar, ¿sabemos lo que es una derivada? Para trabajar con ellas, es interesante al menos entender un poco qué es. Es probable que hayas escuchado que es otra función diferente que te dice el valor de la pendiente de la recta tangente, pero ¿sabes lo que significa eso en realidad?
\newline

El objetivo de estos apuntes no es enseñar este tema de forma precisa, si buscas rigor, mejor estudia la carrera de matemáticas.\newline

\section{Definición}
Empecemos. Vamos a utilizar una función elemental. Por ejemplo la función $$f(x)=\sqrt{x}$$

\includegraphics[]{geogebra-export.png}

Ahora, escogemos un punto cualquiera  y lo llamamos $A$.

\includegraphics[]{geogebra-export (1).png}

Una vez escogido ese punto, tomamos otro cualquiera y trazamos la recta que pasa por esos dos puntos.

\includegraphics[]{geogebra-export (2).png}

Aproximadamente, esta recta nos indica cuánto está cambiando la función en el intervalo $[a,b]$, pero, ¿qué ocurre si hacemos este intervalo cada vez más pequeño?

\includegraphics[scale=2]{geogebra-export (3).png}

Ahora que hemos juntado más los puntos $A$ y $B$, podemos ver que la información que nos proporciona es cada vez más precisa. Entonces, la pregunta más lógica es, ¿qué es lo que ocurre si hacemos que la distancia entre estos puntos sea prácticamente nula?

\includegraphics[scale=4]{geogebra-export (4).png}

Si nos paramos a pensar qué ocurre si hacemos que estos dos puntos coincidan, podemos apreciar que eso es básicamente una recta tangente. La ventaja que presenta esto es que nos proporciona una información muy precisa de cómo va variando la función.\newline

Trabajemos con un poco de rigor ahora. Para calcular la pendiente entre el punto $A$ y otro aleatorio, es decir, $x$ utilizamos la siguiente fórmula

$$\text{Pendiente}=\frac{f(x)-f(a)}{x-a}=\frac{f(a+h)-f(a)}{a+h-a}=\frac{f(a+h)-f(a)}{h}$$ donde $h$ es la distancia entre $x$ y $a$. Básicamente reescribimos qué es $x$ a partir de $a$\newline

Como hemos visto anteriormente, para calcular la derivada en un punto, solamente tenemos que hacer que la diferencia entre ese punto aleatorio y $a$ 0. En otras palabras, tenemos que calcular el límite de la pendiente cuando el punto $x$ tiende a $a$
$$f'(a)=\lim_{x\to a} \frac{f(x)-f(a)}{x-a}$$ 

o también podemos verlo con el incremento $h$
$$f'(a)=\lim_{h\to 0}\frac{f(a+h)-f(a)}{h}$$\newpage

\textbf{Ejemplo:} Calcula la derivada de la función $f(x)=x^{2}$ en $x=5$ aplicando la definición, y después, compara con el resultado aplicando la fórmula.

$$f'(5)=\lim_{h\to 0}\frac{(5+h)^{2}-5^{2}}{h}=\lim_{h\to 0}\frac{25+10h+h^{2}-25}{h}=\lim_{h\to 0}\frac{10h+h^{2}}{h}=\lim_{h\to 0}\frac{h(10+h)}{h}=$$

$$\lim_{h\to 0}\frac{10+h}{1}=\lim_{h\to 0}(10+h)=10$$

La derivada de la función es $f'(x)=2x$, entonces $f'(5)=2\cdot 5=10$

\textbf{Ejercicio:} Calcula la derivada de la función $f(x)=\sin(x)$ usando la definición de derivada.

$$f'(x)=\lim_{h\to 0}\frac{\sin(x+h)-\sin(x)}{h}=\lim_{h\to 0}\frac{\sin(x)\cos(h)+\cos(x)\sin(h)-\sin(x)}{h}=$$

$$\lim_{h\to 0}\frac{\sin(x)}{h}(\cos(h)-1)+\frac{\cos(x)\sin(h)}{h}
=\lim_{h\to 0} \frac{\sin(x)}{h}(\cos(h)-1)\frac{\cos(h)+1}{\cos(h)+1}+\frac{\cos(x)\sin(h)}{h}=
$$
$$
\lim_{h\to 0}\frac{\sin(x)[\cos^{2}(h)-1]}{h[\cos(h)+1]}+\frac{\cos(x)\sin(h)}{h}=
\lim_{h\to 0}\frac{\sin(x)[\cos^{2}(h)-1]}{h[\cos(h)+1]}+\cos(x)=
$$
$$
\lim_{h\to 0}\frac{\sin(x)[-\sin^{2}(h)]}{h[\cos(h)+1]}+\cos(x)=
\lim_{h\to 0}\frac{-\sin(x)}{\cos(h)+1}\cdot \frac{\sin^{2}(h)}{h}+\cos(x)=
$$
$$
\lim_{h\to 0}\frac{-\sin(x)}{2}\cdot \frac{\sin(h)}{h}\cdot \sin(h)+\cos(x)=
\lim_{h\to 0}\frac{-\sin(x)}{2}\cdot 1\cdot 0 +\cos(x)=\cos(x)
$$
\textbf{Recordatorio: }Para demostrar esto hemos aplicado que $\lim_{x\to 0}\sin(h)/h=1$
\section{Notaciones de la derivada}
Aunque solo conozcamos la notación de $f'(x)$, $f''(x)$, $f'''(x)$, $f^{iv)}(x)$, ..., $f^{n)}(x)$, también hay otras notaciones bastante utilizadas.

En física utilizamos principalmente dos notaciones diferentes. La primera es

$$\frac{d}{dx},\frac{d^{2}}{dx^{2}},\cdots,\frac{d^{n}}{dx^{n}}.$$

Esta notación es especialmente útil en física porque nos permite tener un mejor control con respecto a qué variable estamos derivando. Por ejemplo, si nos dan la función $r(t)=3t$, que representará la posición de nuestra partícula a lo largo de su trayectoria y en función del tiempo transcurrido. Si solo decimos $f'(t)$, se entiende pero podría causar confusión, mientras que si escribimos
$$v(t)=\frac{d(3t)}{dt},$$

sabemos que estamos derivando la posición con respecto el tiempo, y por definición, esto es la velocidad. Además, también es usado en física para resolver ecuaciones diferenciales, es decir, ecuaciones en las que aparecen derivadas como incógnitas.\newline

La segunda es ir escribiendo puntos encima de la función para representar sus derivadas. Por ejemplo
$$r(t), \dot{r}(t), \ddot{r}(t), \cdots$$


\section{Usos de las derivadas}
\subsection{Monotonía}
Cuando queremos estudiar la monotonía de una función, usamos las derivadas. Si la derivada es positiva en un intervalo, ese intervalo es creciente y de lo contrario ese intervalo es decreciente. Recordemos que si la función cambia de monotonía, entonces tenemos al menos un extremo relativo\newline

\textbf{Ejercicio:} Estudia la monotonía de la siguiente función $f(x)=x^{3}-3x+1$

Lo que haremos será derivar la función, calcular cuándo se anula la función y después estudiaremos el signo de la derivada en cada intervalo
$$f'(x)=3x^{2}-3\Rightarrow f'(x)=0\Leftrightarrow 3x^{2}-3=0\Leftrightarrow x^{2}=1\Leftrightarrow x=\pm 1$$
$f'(-2)>0,f'(0)<0,f'(2)>0$

Con la información que tenemos podemos dibujar la siguiente gráfica\newline

\tikzset{every picture/.style={line width=0.75pt}} %set default line width to 0.75pt        

\begin{tikzpicture}[x=0.75pt,y=0.75pt,yscale=-1,xscale=1]
%uncomment if require: \path (0,300); %set diagram left start at 0, and has height of 300

%Straight Lines [id:da5171085515681069] 
\draw    (100,120) -- (507.33,120) ;
%Straight Lines [id:da3055939836692576] 
\draw    (202.33,116) -- (202,123) ;
%Straight Lines [id:da8946932426538756] 
\draw    (370.33,116) -- (370,123) ;
%Straight Lines [id:da37784979128776297] 
\draw    (143,106) -- (160.79,91.28) ;
\draw [shift={(162.33,90)}, rotate = 140.39] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da5072778055133293] 
\draw    (286,89) -- (303.94,107.56) ;
\draw [shift={(305.33,109)}, rotate = 225.97] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da7879454990945116] 
\draw    (428,107) -- (445.79,92.28) ;
\draw [shift={(447.33,91)}, rotate = 140.39] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;

% Text Node
\draw (196,128) node [anchor=north west][inner sep=0.75pt]  [font=\scriptsize] [align=left] {\mbox{-}1};
% Text Node
\draw (364,129) node [anchor=north west][inner sep=0.75pt]  [font=\scriptsize] [align=left] {1};

\end{tikzpicture}

Luego, deducimos que la función es creciente en  $(-\infty,-1)\cup (1,+\infty)$y decreciente en (-1,1), y eso hace que  $x=-1$ sea un máximo relativo y $x=1$ un mínimo relativo, pero no son absolutos.

\subsection{Curvatura}

Una vez calculada la primera derivada de la función, podemos volver a derivarla para obtener información de la curvatura.\newline

En general haremos lo siguiente

\begin{itemize}
    \item Calcular la segunda derivada.
    \item Calcular cuándo se anula la segunda derivada.
    \item Al igual que como hacemos con la monotonía, dibujamos una recta y marcamos esos puntos.
    \item Vamos dando valores en los diferentes intervalos.
    \item Si el valor es positivo, la función en ese intervalo es convexa y si es negativa, entonces cóncava.
    \item Los puntos donde la función cambia de monotonía se denominan puntos de inflexión.
\end{itemize}

\textbf{Ejemplo: }Calcula los puntos de inflexión de la función $f(x)=\frac{x}{x^{2}+1}$
Empecemos calculando la segunda derivada
$$f'(x)=\frac{x^{2}+1-2x^{2}}{\left(x^{2}+1\right)^{2}}=\frac{1-x^{2}}{\left(x^{2}+1\right)^{2}}\Rightarrow f''(x)=\frac{-2x\left(x^{2}+1\right)^{2}-\left(1-x^{2}\right)\cdot2\left(x^{2}+1\right)\cdot2x}{\left(x^{2}+1\right)^{4}}$$

$$f''(x)=\frac{-2x\left(-x^{2}+3\right)}{\left(x^{2}+1\right)^{3}}\Rightarrow f''(x)=0\Leftrightarrow x=0 \text{ o }x=\pm\sqrt{3}$$

Si le damos valores a la segunda derivada, obtenemos que en $(\-\infty,-\sqrt{3})$ obtenemos un valor negativo, entre $(-\sqrt{3},0)$ uno positivo, de $(0,\sqrt{3})$ uno negativo y finalmente en $(\sqrt{3},+\infty)$ uno positivo. En conclusión, los puntos de inflexión son $x=-\sqrt{3}$, $x=0$ y $x=\sqrt{3}$. Además, la función es cóncava en el $(\-\infty,-\sqrt{3})\cup (0,\sqrt{3})$ y convexa en $(-\sqrt{3},0)\cup(\sqrt{3},+\infty)$

\subsection{Recta tangente}
Como la derivada nos da el valor de la recta tangente en un cierto punto, podemos usar esta información para calcular la forma explícita de la recta. \newline

\textbf{Ejercicio: } Calcula la recta tangente de $f(x)=x^{2}+5x-3$ en $x=3$
$$f'(x)=2x+5\Rightarrow f'(3)=6+5=11$$

Aplicamos la fórmula de la ecuación de la recta punto-pendiente $y=y_{0}+m(x-x_{0})$ donde $m$ es la pendiente, $x$,$y$ es un punto arbitrario y $x_{0}$,$y_{0}$ es un punto por donde pasa la recta.

Como necesitamos la recta tangente en $x=3$, tenemos que evaluar la función en $x=3$, entonces, $f(3)=21$
$$y=21+11(x-3)\Rightarrow y=11x-12$$


\section{Cómo calcular derivadas}

 Como ya sabrás, hay una tabla donde se recogen las derivadas de una función. Además, es importante tener en cuenta la regla de la cadena\newline

La mayoría de estas tablas no indican cómo se deriva el producto de dos funciones
$$f(x)=g(x)h(x)\Rightarrow f'(x)=g'(x)h(x)+g(x)h'(x)$$

Para la división es
$$f(x)=\frac{g(x)}{h(x)}=\frac{g'(x)h(x)-g(x)h'(x)}{h^{2}(x)}$$

La derivada de la suma es la suma de las derivadas
$$f(x)=f_{1}(x)+\cdots +f_{n}(x)\Rightarrow f'(x)=f_{1}'(x)+\cdots +f_{n}'(x)$$

Primero de todo, vamos a buscar una tabla con las derivadas. Por ejemplo, vamos a empezar derivando un polinomio. Como ejemplo, vamos a derivar la función $f(x)=5x^{3}-4x^{2}+x-7$. Recordemos que la derivada de la suma es la suma de las derivadas, y además, $f(x)=ax^{b}\Rightarrow f'(x)=abx^{b-1}$. Entonces,
$$f'(x)=5\cdot 3x^{2}\cdot 1 -4\cdot 2x \cdot 1 + 1x^{0}\cdot 1 -0=15x^{2}-8x+1$$

Como recordatorio, después de haber aplicado lo que nos indica la tabla, tenemos que aplicar también la cadena. Se multiplica por 1 en cada sumando porque ese es el valor de la derivada de $x$.

Vamos a derivar una función un poco más compleja
$$f(x)=\sqrt{e^{-x^{2}+5}+\cos(\pi x)}$$

Definamos una función $g$ que será el radicando de la raíz
$$g(x)=e^{-x^{2}+5}+\cos(\pi x)$$

Aplicamos la regla de la derivada para las raíces cuadradas
$$f'(x)=\frac{g'(x)}{2\sqrt{e^{-x^{2}+5}+\cos(\pi x)}}$$

Ahora derivamos $g$
$$g'(x)=e^{-x^{2}+5}(-2x)-\sin(\pi x)\cdot \pi$$

Al final nos queda
$$f'(x)=\frac{-2xe^{-x^{2}+5}-\pi\sin(\pi x)\cdot}{2\sqrt{e^{-x^{2}+5}+\cos(\pi x)}}$$\newline

\textbf{Ejercicio:} Derivada la siguiente función $f(x)=\ln(x\sqrt{1-x})$

Como de costumbre, creamos una función $g$ que es el argumento del logaritmo
$$g(x)=x\sqrt{1-x}$$

Derivamos aplicando la regla de los logaritmos
$$f'(x)=\frac{g'(x)}{x\sqrt{1-x}}$$

Derivamos también la función $g$
$$g'(x)=1\cdot \sqrt{1-x}-\frac{x}{2\sqrt{1-x}}$$

Al final obtenemos que la derivada de la función es
$$f'(x)=\frac{\sqrt{1-x}-\frac{x}{2\sqrt{1-x}}}{x\sqrt{1-x}}$$

Podemos seguir operando, pero por lo general no se pide.

\textbf{Ejercicio:} Deriva la siguiente función $f:[-2,2\pi]\to\mathbb{R}$, tal que 
$$f(x)=
\left\{
\begin{array}{ccl}
      5x+1 &\text{ si } -2\leq x\leq0 \\
      e^{x}\cos(x) &\text{ si } 0<x\leq 2\pi
\end{array}
\right.
$$
Primero, vemos que ambas funciones son continuas en general y en particular, en el intervalo en que están definidas, pero no sabemos si en el punto en el que se cambia de definición es o no continua. Entonces, veamos si es o no continua en $x=0$

$$\lim_{x\to 0^{-}}f(x)=\lim_{x\to 0}(5x+1)=1=f(0)$$
$$\lim_{x\to 0^{+}}f(x)=\lim_{x\to 0}\left(e^{x}\cos(x)\right)=1\cdot1$$
$$\lim_{x\to 0^{-}}f(x)=\lim_{x\to 0^{+}}f(x)=f(0)\text{ La función es continua}$$

Una vez que hemos visto que la función es continua, nos falta ver si es derivable y si lo es, dónde es derivable. A simple vista podemos ver que por separado, ambas funciones son derivables y nos faltaría ver qué ocurre en el punto $x=0$. Para calcularlo, calcularemos las derivadas y después veremos qué ocurre con el límite de la derivada en ese punto.
$$f'(x)=
\left\{
\begin{array}{ccl}
      5 &\text{ si } -2\leq x<0 \\
      e^{x}\left[\cos(x)-\sen(x)\right] &\text{ si } 0<x\leq 2\pi
\end{array}
\right.
$$
En 0 podemos ver claramente que la segunda definición de la función no vale 5, luego no es derivable en $x=0$, por lo tanto ya habríamos acabado el ejercicio.\newline

Cuando trabajamos con funciones elementales (con las que solemos trabajar) suelen ser tanto continuas como derivables. Sin embargo, las funciones definidas por trozos puede ocurrir que la función cambie de definición y deje de ser continua, entonces ¿cuáles son las condiciones necesarias para que la función sea derivable, hay condiciones suficientes?\newline

Una condición que es necesaria, pero no suficiente es la continuidad, es decir, para poder decir que una función es derivable sí o sí debe ser continua en todos los puntos del dominio, pero no es suficiente porque hay funciones continuas que no son derivables. Como por ejemplo la función $f(x)=|x|$.

Desarrollemos la función valor absoluto
$$f(x)=\left\{
\begin{array}
    \\ x \text{ si } x \geq 0
    \\ -x \text{ si }x< 0
\end{array}
\right.
$$
Vamos a primero estudiar la continuidad en $x=0$
$$\lim_{x\to 0^{+}}f(x)=0\text{ , }\lim_{x\to 0^{-}}f(x)=0\text{ y } f(0)=0$$

Todo esto nos dice que en $x=0$, la función es continua, pero, ¿es también la derivada continua en ese punto?
$$f'(x)=\left\{
\begin{array}
    \\ 1 \text{ si } x > 0
    \\-1 \text{ si }x< 0
\end{array}
\right.
$$

No sería necesario estudiar los límites laterales porque se evidentemente que no coincidirán, luego la función no es derivable. Como detalle a tener en cuenta, no se ha escrito las igualdades en la derivada porque puede ocurrir como en este caso que no exista. De existir, podemos añadir las igualdades a forma de conclusión\newline

Como resumen general, imagina que tenemos la gráfica de una función. Si la función presenta un pico, como por ejemplo de la función valor absoluto, entonces la función no es derivable, y si la función sí presenta una curva suave, entonces la función probablemente sea derivable.\newline

\textbf{Ejemplo: } Considera la función: $\mathbb{R}\to\mathbb{R}$ definida por
$$f(x)=\frac{1}{e^{x}+e^{-x}}$$
a) Estudia los extremos absolutos de $f$
b) Calcula $\lim_{x\to+\infty} x^{2}f(x)$

$$\frac{1}{e^{x}+e^{-x}}=\left(e^{x}+e^{-x}\right)^{-1}\Rightarrow f'(x)=-\left(e^{x}+e^{-x}\right)^{-2}\cdot \left(e^{x}-e^{-x}\right)=$$
$$=\frac{\left(e^{-x}-e^{x}\right)}{\left(e^{x}+e^{-x}\right)^{2}}\Rightarrow f'(x)=0\Leftrightarrow e^{-x}=e^{x}\Leftrightarrow -x=x\Leftrightarrow x=0$$

Le damos valores a ambos lados del intervalo y ahora veamos qué signo nos devuelve la derivada. $f'(-1)>0$ y $f'(1)<0$, luego la función es creciente en $(-\infty,0)$ y decreciente en $(0,+\infty)$. Con esta información sabemos que la función presenta un máximo relativo en $x=0$, pero ¿es máximo absoluto?, para ello vamos a calcular los límites en el infinito.
$$\lim_{x\to-\infty}f(x)=\frac{1}{\infty}=0$$
$$\lim_{x\to+\infty}f(x)=\frac{1}{\infty}=0$$

Teniendo en cuenta que la función solo toma valores positivos y que además en el infinito tiende a 0, deducimos que el máximo relativo en $x=0$ es también un máximo absoluto.

$$\lim_{x\to+\infty} x^{2}f(x)=\lim_{x\to+\infty}\frac{x^{2}}{e^{x}+e^{-x}}=\frac{\infty}{\infty}\Rightarrow\text{ aplicamos L'Hôpital}\Rightarrow\lim_{x\to+\infty}\frac{2x}{e^{x}-e^{-x}}=\frac{\infty}{\infty}\Rightarrow$$

$$\Rightarrow\text{ volvemos a usar L'Hôpital }\Rightarrow\lim_{x\to+\infty}\frac{2}{e^{x}+e^{-x}}=\frac{2}{\infty}=0.$$

\chapter{Integrales}
Si alguna vez has escuchado algo sobre las integrales, probablemente te suene algo relacionado con el área bajo una curva. Esto más o menos se podría considerar la definición, pero si queremos ser rigurosos, debemos dominar un concepto algo complejo que son las particiones, pero no son estrictamente necesarias en este nivel.\newline

Antes de empezar con el concepto de integral, vamos a hablar un poco de las aplicaciones que le damos a las integrales. Por ejemplo, en física las podemos usar para calcular el trabajo de una fuerza, ya sea constante o no, calcular la velocidad a partir de la aceleración, o la posición a partir de la velocidad; en matemáticas, las podemos usar para calcular la longitud de una curva o el volumen de sólidos de revolución; en medicina las podemos utilizar para calcular la cantidad de medicamento administrado a un paciente durante un periodo de tiempo.\newline

Además, en matemáticas, cuando tenemos un operador, en general, también tenemos el operador contrario. Por ejemplo, la suma y la resta; el producto y la división; y en este caso la derivada y la integral. Asimismo, tenemos un teorema que nos relaciona ambos conceptos.

\section{Definición}

%Inserte la imagen sobre las particiones

Lo que haremos será ir partiendo el eje $OX$ y de cada partición alzamos un rectángulo. Si empezamos con un solo rectángulo, el área que obtenemos no es muy preciso, pero si tomamos dos rectángulos, el área total de estos dos rectángulos se asemejará cada vez más al área real. Hay que tener en cuenta (para entender el concepto) que tenemos dos opciones de rectángulo. Si hacemos coincidir el extremo izquierdo del rectángulo con la valor de la función, entonces el rectángulo que obtenemos tendrá menos área del que debería, y si lo hacemos al revés, tendrá área de más. Aunque no lo demostremos, da igual qué tipo de partición escojamos, si hacemos infinitas particiones, ambas nos devuelve el mismo valor, que es el área bajo la curva.

Tomemos $p=\{a=t_{0}<t_{1}<\cdots<t_{n}\}$

\section{Cómo calcular integrales}
\subsection{Integral por partes}
El método de integración por partes nos permite resolver algunas integrales que están formadas por un producto o una división.\newline

Vamos a demostrar de dónde sale la fórmula. 

Primero, recordemos cuál es la derivada del producto de dos funciones.
$$f(x)=g(x)\cdot h(x)\Rightarrow f'(x)=g'(x)h(x)+g(x)h'(x)$$

Integremos ambas partes
$$\int f'(x)dx=\int \left[ g'(x)h(x)+g(x)h'(x)\right]dx=\int g'(x)h(x)dx+\int g(x)h'(x)dx$$

Sabemos que Si integramos la derivada de una función dada, entonces obtenemos la función y haciendo un cambio de variable, entonces obtenemos que
$$u=g(x)\Rightarrow \frac{du}{dx}=g'(x)\Rightarrow du=g'(x)dx$$
$$v=h(x)\Rightarrow \frac{dv}{dx}=h'(x)\Rightarrow dv=h'(x)dx$$

Entonces
$$uv=\int vdu+\int udv\Rightarrow \int udv=uv-\int vdu.$$

Para utilizar esta 'fórmula' debemos decidir quién será nuestra $u$ y qué será el $dv$.

\text{Ejemplo: } Integre la siguiente función $f(x)=x\cos(x)$

Usaremos $u=x\Rightarrow du=dx$ y $dv=\cos(x)dx\Rightarrow v=\sen(x)$, entonces obtenemos que
$$\int x\cos(x)dx=x\cos(x)-\int \sen(x)dx=x\cos(x)+\cos(x)+C.$$
\subsection{Integral por sustitución}
Lo que hacemos es transformar una primitiva en otra diferente y más fácil mediante un cambio de variable. Lo que haremos será $y=g(x)$ y, por ende, $dy=g'(x)dx$, entonces obtenemos que
$$\int f(g(x))g'(x)dx=\int f(y)dy.$$

\textbf{Ejemplo:} Resuelve la siguiente integral 
$$\int \frac{e^{x}+3e^{2x}}{2+e^{x}}dx$$

Hacemos un cambio de variable donde $y=e^{x}$ y $dy=e^{x}dx$
$$\int \frac{e^{x}+3e^{2x}}{2+e^{x}}dx=\int \frac{y+3y^{2}}{2+y}\cdot\frac{1}{y}dy=\int \frac{1+3y}{2+y}dy$$
$$\int \frac{1+3y}{2+y}dy=\int \left(3-\frac{5}{2+y}\right)dy=3\int dy-5\int\frac{1}{2+y}dy=3y-5\ln|2+y|+C$$

Deshacemos el cambio de variable y lo que obtenemos es que el resultado de la integral es
$$3e^{x}-5\ln|2+e^{x}|+C$$

Este resultado está bien, pero si queremos demostrar una mayor destreza en las matemáticas, podemos quitar el valor absoluto, puesto que $e^{x}$ siempre toma valores positivos, luego podemos dejar el resultado como
$$\int \frac{e^{x}+3e^{2x}}{2+e^{x}}dx=3e^{x}-5\ln(2+e^{x})+C$$
\textbf{Anotación:} En la primera igualdad para resolver la integral, hemos desarrollado lo que es la fracción a partir de $D=dc+r$, lo que hacemos es dividir ambas partes de la igualdad entre el divisor, por lo que obtenemos $D/c=c+(r/d)$. Si realizamos la división, observamos que el cociente que obtenemos es 3 y el resto es -5. 
\section{Usos de la integral}
En esta sección vamos a tratar solo las aplicaciones que les damos en Matemáticas.

\subsection{Área bajo una curva}
Si queremos calcular el área por debajo de una curva, usamos las integrales, pero a veces, no es tan inmediato. Si la función es mayor que cero en todo el intervalo, entonces, es inmediato. Sin embargo, si la funciones tiene intervalos donde la función sea menor que cero, entonces, tendremos que averiguar dónde es menor que cero y ya después integraremos con un valor absoluto.\newline

\textbf{Ejemplo:} Calcula el área bajo la curva de la función $f(x)=\sin(x)$ desde $x=0$ hasta $x=2\pi$\newline

Primero, calculemos a ver qué pasa si integramos directamente desde 0 hasta $2\pi$.
$$\int_{0}^{2\pi}\sin(x)dx=\left.\cos(x)\right]_{0}^{2\pi}=\cos(2\pi)-\cos(0)=0-0=0.$$

Ahora lo haremos teniendo en cuenta que la función tiene una parte negativa.
Vamos a calcular primero cuándo la función se anula.
$$f(x)=0\Leftrightarrow \sin(x)=0\Leftrightarrow x=0+\pi k, k\in\mathbb{Z}.$$

Ahora sabemos que la función se anula en  $x=0$, $x=\pi$ y $x=2\pi$. Si graficamos la función, podemos ver dónde la función es positiva y dónde es negativa, pero si no la graficamos, lo que podemos hacer es dar un valor en cada intervalo. La función es positiva en $(0,\pi)$ y negativa en $(\pi,2\pi)$.

$$\text{Área}=\left|\int_{0}^{\pi}\sin(x)dx\right|+\left|\int_{\pi}^{2\pi}\sin(x)\right|=\left.\cos(x)\right]{0}^{\pi}+\left|\left.\cos(x)\right]{\pi}^{2\pi}\right|=$$

$$=|\cos(\pi)-\cos(0)|+|\cos(2\pi)-\cos(\pi)|=|-1-1|+|1-(-1)|=2+2=4u^{2}.$$

\textbf{Nota:} Como estamos calculando un área, estamos dando un valor numérico y nos haría falta decir en qué unidad lo estamos midiendo. Como no tenemos ninguna información sobre la unidad de medida, podemos simplemente utilizar $u$ de unidad.\newline

La función $f(x)=\sin(x)$ es un buen ejemplo de por qué hay que tener cuidado con las partes donde la función es negativa. En este caso, la función tiene el mismo área desde 0 hasta $\pi$ y desde $\pi$ hasta $2\pi$. 

\subsection{Área entre dos curvas}
Para calcular el área entre dos curvas, haremos lo siguiente:

\begin{itemize}
    \item Si podemos, esbozar más o menos ambas funciones en una gráfica.
    \item Calcular la intersección de ambas, y esas intersecciones serán los límites de integración.
    \item Razonar qué función es mayor.
    \item Hacer la diferencia entre ambas funciones y así la nueva función tendrá el área que queremos calcular. Si no queremos o no sabemos cuál es la menor, podemos utilizar el valor absoluto porque al final es lo mismo, ya que podríamos sacar factor común -1 de la integral.
    \item Integramos la diferencia.

\end{itemize}
\textbf{Ejemplo: } Calcula el área encerrada por las funciones $f(x)=x^{2}$ y $g(x)=\sqrt{x}$
Haremos este ejercicio sin graficar nada en papel.

Primero, calcularemos la intersección de estas funciones
$$x^{2}=\sqrt{x}\Leftrightarrow x^{4}=x\Leftrightarrow x^{4}-x=0\Leftrightarrow x(x^{3}-1)=0\Leftrightarrow x=0\text{ o } x^{3}=1\Rightarrow x=\pm 1$$

Como tenemos $g(x)=\sqrt{x}$, $x=-1$ no es una solución posible, por lo que tenemos $x=0$ y $x=1$ (puede darse el caso de que haya más de dos intersecciones). Ahora que conocemos los límites de integración, podemos razonar qué función es mayor. Si tenemos un buen manejo de las funciones elementales sabemos que la raíz cuadrada en ese intervalo es mayor, pero si no tenemos tiempo o no podemos, podemos restar cualquiera de ellas y meter un valor absoluto por si acaso.

$$\int_{0}^{1}(\sqrt{x}-x^{2})dx=\int_{0}^{1}x^{1/2}dx-\int_{0}^{1}x^{2}dx=\left.\frac{x^{\frac{1}{2}+1}}{1/2}-\frac{x^{3}}{3}\right]{0}^{1}=\left.2x^{\frac{3}{2}}-\frac{x^{3}}{3}\right]{0}^{1}=(2-\frac{1}{3})-(0-0)=\frac{5}{3}u^{2}.$$

\subsection{Volumen de un sólido de revolución}

Si una curva la rotamos sobre el eje $OX$, obtenemos un sólido de revolución, y para calcular el volumen, tenemos la siguiente fórmula
$$\text{Volumen}=\int_{a}^{b}\pi f^{2}(x)dx.$$

No vamos a demostrar la fórmula porque para ello tendríamos que recurrir a las particiones etiquetadas. Pero podemos ver que la fórmula es casi idéntica a la del área de un círculo $A=\pi r^(2)$. De forma intuitiva, al rotar la curva estamos creando por cada valor de $x$ una circunferencia y la imagen de ese punto es el radio de esa circunferencia. Por lo tanto si sumamos cuánto vale el área de todas esas circunferencias, tenemos el volumen del sólido. De esa idea sale la fórmula que tenemos.\newline

\textbf{Ejemplo:} Vamos a calcular el volumen de la trompeta de Gabriel. La función es $f(x)=1/x$ y el dominio es $[1,+\infty).$

Aplicaremos la fórmula.%Le tenfo que meter pi y hacerlo al cuadrado y creo que cambia
$$\text{Volumen}=\pi\int_{1}^{+\infty}\frac{1}{x^{2}}dx=\pi\lim_{b\to+\infty}\int_{1}^{b}\frac{1}{x^{2}}dx=\pi\lim_{b\to +\infty}\left.\frac{-1}{x}\right]{1}^{b}=\pi\left(\lim{b\to+\infty}\frac{-1}{b}+1\right)=\pi u^{3}.$$

Esta es una función un tanto especial porque tiene una superficie infinita, pero alberga un volumen finito. Si quisiéramos podríamos calcular la superficie, pero no lo vamos a hacer y si sintieras curiosidad por ello, en \textit{Youtube} hay un canal llamado \textit{Derivando} en el que se trata con un poco más de profundidad este tema.\newline

\textbf{Ejemplo:} Calcula el volumen que obtendríamos rotando la función $f(x)=\sqrt{x}$ sobre el eje $OX$ desde $x=1$ hasta $x=3$.

Aplicamos la fórmula que nos dan y obtenemos
$$\text{Volumen}=\pi\int_{1}^{3}\sqrt{x^{2}}dx=\pi\int_{1}^{3}xdx=\pi\left[\frac{x^{2}}{2}\right]_{1}^{3}=\pi\left[\frac{9}{2}-\frac{1}{2}\right]=4\pi u^{3}.$$

\subsection{Longitud de una curva}
A pesar de que no la vayas a utilizar, para calcular la longitud de una curva desde un punto $a$, hasta un punto $b$, tenemos la fórmula
$$\text{Longitud}=\int_{a}^{b}\sqrt{1+(f'(x))^{2}}dx$$

\textbf{Ejemplo: } Calcula la longitud de la curva de $f(x)=\frac{x^{4}}{8}+\frac{1}{4x^{2}}$ desde $x=1$ hasta $x=3$.

$$f'(x)=\frac{x^{3}}{2}-\frac{x^{-3}}{2}=\frac{x^{3}}{2}-\frac{1}{2x^{3}}=\frac{x^{6}-1}{2x^{3}}$$
$$1+(f'(x))^{2}=1+\frac{x^{12}-2x^{6}+1}{4x^{6}}=\frac{x^{12}+2x^{6}+1}{4x^{6}}=\frac{\left(x^{6}+1\right)^{2}}{4x^{6}}$$

$$\text{Longitud}=\int_{1}^{3}\sqrt{\frac{\left(x^{6}+1\right)^{2}}{4x^{6}}}dx=\int_{1}^{3}\frac{x^{6}+1}{2x^{3}}dx=\frac{1}{2}\int_{1}^{3} x^{3}+\frac{1}{x^{3}}dx=\frac{1}{2}\left[\frac{x^{4}}{4}-\frac{1}{2x^{2}}\right]_{1}^{3}=\frac{92}{9}u.$$

\subsection{Resolver ecuaciones diferenciales}
Al igual que tenemos las ecuaciones con fracciones, raíces, logaritmos, exponentes, también tenemos ecuaciones con derivadas, a las cuales llamaremos ecuaciones diferenciales.\newline

Para este nivel, usaremos la notación de fracciones, y aunque en matemáticas sea una aberración, consideraremos que las derivadas son fracciones.\newline

Probemos las fórmulas $x=x_{0}+v(t-t_{0})$ y $x=x_{0}+v_{0}t+\frac{1}{2}at^{2}$

Solo tenemos que saber que
$$v=\frac{dx}{dt}\text{ y } a=\frac{dv}{dt}$$

Centrémonos en la primera ecuación de las dos
$$vdt=dx\Leftrightarrow \int_{0}^{t}vdt=\int_{x_{0}}^{x}dx\Leftrightarrow vt=x-x_{0}\Leftrightarrow x=x_{0}+vt$$

Veamos qué información podemos obtener de la segunda igualdad
$$adt=dv\Leftrightarrow \int_{0}^{t}adt=\int_{v_{0}}^{v}dv\Leftrightarrow at=v-v_{0}\Leftrightarrow v=v_{0}+at$$

Si ahora queremos saber cuál es la posición durante un movimiento con aceleración, utilizamos también la primera igualdad

$$(v_{0}+at)dt=dx\Leftrightarrow \int_{0}^{t}(v_{0}+at)dt=\int_{x_{0}}^{x}dx\Leftrightarrow v_{0}t+a\frac{t^{2}}{2}=x-x_{0}\Leftrightarrow x=x_{0}+v_{0}t+a\frac{t^{2}}{2}\qed$$ 

\section{Ejemplos de resolver integrales}
$$\int \ln(x)dx$$
Vamos a resolver la integral mediante un cambio de variable. $u=\ln(x)\rightarrow du=dx/x, dv=dx\rightarrow v=x$

Nos queda
    $$\int \ln(x)=x\ln(x)-\int \frac{x}{x}dx=x\ln(x)-\int dx=x\ln(x)-x+C$$ \raggedright $\qed$

Otra integral que puede ser interesante resolver es
$$\int \sqrt{1-x^{2}}dx$$

Vamos a resolverlo mediante sustitución. $x=sent$, $dx=cos(t)dt$
\begin{proof}
    $$\int \sqrt{1-\sen^{2}(t)}dx=\int\sqrt{\cos^{2}(t)}dx=\int\cos(t)\cos(t)dt=\int\cos^{2}(t)dt$$
    $$\sqrt{ab}=5$$
\end{proof}


Ahora nos queda otra integral por resolver mediante integración por partes o también se puede resolver mediante el uso de otra forma de expresar $\cos^{2}(x)$
$$I=\int\cos^{2}(t)dt$$

Tomamos $u=\cos(t)$, $du=-\sen(t)dt$ y también $dv=cos(t)dt$ y obtenemos $v=\sen(t)$
$$\int\cos^{2}(t)dt=\cos(t)\sen(t)-\int-\sen^{2}(t)dt=\cos(t)\sen(t)+\int\left(1-\cos^{2}(t)\right)dt=$$
$$=\cos(t)\sen(t)+\int dt-I\Rightarrow 2I=\cos(t)\sen(t)+t\Rightarrow I=\frac{\cos(t)\sen(t)}{2}+\frac{t}{2}$$

$$\int\cos^{2}(t)dt=\frac{\cos(t)\sen(t)}{2}+\frac{t}{2}+C$$

Ahora simplemente tenemos que deshacer el cambio de variable
$$\sqrt{1-x^{2}}=\sqrt{1-\sen^{2}(t)}=\sqrt{\cos^{2}(t)}=\cos(t)$$
$$\int\sqrt{1-x^{2}}dt=\frac{\arcsen(x)}{2}+\frac{\sqrt{1-x^{2}}\sen(\arcsen(x))}{2}+C=\frac{\arcsen(x)}{2}+\frac{x\sqrt{1-x^{2}}}{2}+C=$$
$$=\frac{\arcsen(x)+x\sqrt{1-x^{2}}}{2}+C$$

$$\int_{0}^{1}\sqrt{x^{3}+\pi+5x}$$


\end{document}