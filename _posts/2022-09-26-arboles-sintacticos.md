---
layout: post
title: Árboles sintácticos
---


LaTeX es un lenguaje de marcado --basado en TeX-- que se usa para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica en generar, por ejemplo, diagramas de diferente tipo a través de gráficos vectoriales (PGF/TikZ) y complejas fórmulas matemáticas gracias su modo matemático. ¡LaTeX es una excelente herramienta!, ya que cuenta con una sinfinidad de paquetes que se ajustan siempre a nuestras necesidades.

En el caso de la lingüística, resulta muy útilporque l ede usar para escribir símbolos fonéticos (con tipa), glosas (con gb4e o Covington), estructuras de representación del discurso, árboles de dependencia y árboles sintácticos. Como     

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
