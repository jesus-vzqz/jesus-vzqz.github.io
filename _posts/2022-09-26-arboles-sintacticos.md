---
layout: post
title: Árboles sintácticos
---

## Intro

LaTeX es un lenguaje de marcado --basado en TeX-- que se usa para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica en generar, p. ej., diagramas de diferente clase (diagramas de flujo, grafos, árboles de decisión, automátas, etc) a través de gráficos vectoriales (**PGF/TikZ**) y complejas fórmulas matemáticas gracias su **modo matemático**. ¡LaTeX es una herramienta versátil!, ya que cuenta con una sinfinidad de paquetes que siempre se ajustan a nuestras necesidades.

En el caso de la lingüística, resulta muy útil porque existen un conjunto de paquetes que nos permiten escribir símbolos fonéticos (con **tipa**), glosas (con **gb4e** o **covington**), enumeración de ejemplos (con **gb4e,  ling-macros, linguex o philex** ), estructuras de representación del discurso (con **drs**), árboles de dependencia (con **TikZ-dependency**) y árboles sintácticos (con **xyling, xy, tikz-qtree o forest**), etc. Dada esta breve presentación de paquetes, cabría que considerar si el aprendezije y el uso de estos forma parte de nuestra formación profesional como lingüístas. ¡Yo pienso que sí! Incluso el aprendizaje de cosas nuevas siempre puede resultarnos satisfactorio.

En fin, a lo largo de este *post*, me enfocaré en explicar algunas maneras en las que podemos dibujar árboles sintácticos con **forest** porque creo que es un paquete bastante intuitivo para la elaboración de representaciones árboreas. Además, para lograr este objetivo, consideraré que el lector ya cuenta con algunos conocimientos básicos en el uso LaTeX; si este no es el caso existen muy buenos manuales en internet. 

Añado un curso que posiblemente pueda interesar:

[Introducción a LaTeX](https://github.com/piratax007/LaTeX_Course)


### Creando nuestras primeras representaciones con forest

Para comenzar, tendremos que cargar el paquete de forest en el preámbulo de nuestro documento:


```{=latex}

\usepackage[linguistics]{forest}

```

Una cuestión importante que debemos tomar en cuenta para el futuro es que al momento de hacer las flechas de los movimientos sintácticos que conectan los nodos,  **forest** produce un conflicto con algunos caracteres del paquete **babel** en español. Para evitar este problema, tenemos que escribir lo siguiente: 


```{=latex}

\usepackage[spanish, es-noshorthands]{babel}

```

Esto nos mantendrá prevenidos para futuros errores que puedan resultarnos frustantes. Muy bien, ahora, dentro del cuerpo de nuestro documento, llamaremos al ambiente de **forest**. En este punto, veremos que la sintaxis básica de este paquete consiste en usar corchetes para anidar otros corchetes. ¡Así de fácil! Como observamos en el siguiente ejemplo, el corchete más grande tiene en su inicio un **1**, que corresponde a la posición del nodo madre, y anida otros dos corchetes con sus respectivos números: **2** y **3**, que son los nodos hermanos. 


```{=latex}

\begin{document}

\begin{forest}
[1 [2] [3]]
\end{forest}

\end{document}
```

Compilamos y  produce:

![Primer ejemplo](/images/post_1/ejemplo1.png)

Si hemos comprendido esto, ya estamos a la mitad del camino para construir diagramas mucho más complejos, pero antes repitamos este mismo proceso y hagámos otras combinaciones para practicar.

```{=latex}

\begin{forest}
[1 [2 [4] [5]] [3 [6] [7]]]
\end{forest}

```
![Segundo ejemplo](/images/post_1/ejemplo2.png)

```{=latex}

\begin{forest}
[1 [2 [6]] [3 [7]] [4[8]] [5[9]]]
\end{forest}

```
![Tercer ejemplo](/images/post_1/ejemplo3.png)


### Creando el esquema X-barra


```{=latex}

\usepackage[spanish]{babel}
\usepackage[linguistics]{forest}
\usepackage{philex}

\begin{document}
\lb{1}{
    \lba{1a}{SX $\rightarrow$  SY, X'}
    \lbb{1b}{X' $\rightarrow$ X$^0$, SZ}
    \lbz{1c}{ Esquema de la X': \\   
    \begin{forest}
    [SX [SY \\ (Especificador) ] 
        [X' [X$^0$ \\ (Núcleo)] 
            [SZ \\ (Complemento) ]]]
    \end{forest}}}


    \begin{forest}
    [SX [especificador]
        [X' 
            [X' [X$^0$] [complemento]
            ] [adjunto]]]
    \end{forest}
        
Página 141 de Fundamentos de Sintaxis Formal.

    \begin{forest}
        [SX [especificador]
            [X'
                [X'  
                    [X' [X$^0$] [Complemento]] 
                    [Segundo Complemento]] 
                        [Adjunto]]]
    \end{forest}
```
