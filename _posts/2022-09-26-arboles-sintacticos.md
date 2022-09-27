---
layout: post
title: Árboles sintácticos
---

# Breves aproximaciones a LaTeX

LaTeX es un lenguaje de marcado --basado en TeX-- usado para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica, por ejemplo, en generar diagramas de diferentes clase a través de gráficos vectoriales (PGF/TikZ) y complejas fórmulas matemáticas gracias su modo matemático. LaTeX tiene una sinfinidad de paquetes que siempre se adecuan a nuestras necesidades.

En el caso de la lingüística, cabe resaltar que se puede usar para escribir símbolos fonéticos (con tipa), glosas (con gb4e o Covington), estructuras de representación del discurso, árboles de dependencia y árboles sintácticos. Como     

## Creando nuestras primeras representaciones 

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
