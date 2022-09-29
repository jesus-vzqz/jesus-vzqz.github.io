---
layout: post
title: Árboles sintácticos
---

LaTeX es un lenguaje de marcado --basado en TeX-- que se usa para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica en generar, p. ej., diagramas de diferente clase (diagramas de flujo, grafos, árboles de decisión, automátas, etc) a través de gráficos vectoriales (**PGF/TikZ**) y complejas fórmulas matemáticas gracias su **modo matemático**. ¡LaTeX es una herramienta versátil!, ya que cuenta con una sinfinidad de paquetes que siempre se ajustan a nuestras necesidades.

En el caso de la lingüística, resulta muy útil porque existen un conjunto de paquetes que nos permiten escribir símbolos fonéticos (con **tipa**), glosas (con **gb4e** o **covington**), enumeración de ejemplos (con **gb4e,  ling-macros, linguex o philex** ), estructuras de representación del discurso (con **drs**), árboles de dependencia (con **TikZ-dependency**) y árboles sintácticos (con **xyling, xy, tikz-qtree o forest**), etc. Dada esta breve presentación de paquetes, cabría que considerar si el aprendezije y el uso de estos forma parte de nuestra formación profesional como lingüístas. ¡Yo pienso que sí! Incluso el aprendizaje de cosas nuevas siempre puede resultarnos satisfactorio.

En fin, a lo largo de este *post*, me enfocaré en explicar algunas maneras en las que podemos dibujar árboles sintácticos con **forest** porque creo que es un paquete bastante intuitivo para la elaboración de representaciones árboreas. Además, para lograr este objetivo, consideraré que el lector ya cuenta con algunos conocimientos básicos en el uso LaTeX; si este no es el caso existen muy buenos manuales en internet. 

Añado un curso que posiblemente pueda interesar:

[Introducción a LaTeX](https://github.com/piratax007/LaTeX_Course)



## Creando nuestras primeras representaciones con el paquete forest

Para comenzar, tendremos que cargar el paquete de forest en el preámbulo de nuestro documento:


```{=latex}

\usepackage[linguistics]{forest}

```

Una cuestión importante que debemos tomar en cuenta para futuro es que al momento de hacer las flechas de los movimientos sintácticos que conectan los nodos,  **forest** tiene conflicto con algunos caracteres del paquete **babel** en español. Para evitar este problema, tenemos que escribir lo siguiente: 


```{=latex}

\usepackage[spanish, es-noshorthands]{babel}

```

Esto nos mantendrá prevenidos para futuros errores que pueden occurrir. Muy bien, ahora dentro del cuerpo de nuestro documento, llamaremos al ambiente de **forest**. La sintaxis básica de este paquete consiste en

```{=latex}

\begin{document}

\begin{forest}

[1 [2] [3]]

\end{forest}

\end{document}
```




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
