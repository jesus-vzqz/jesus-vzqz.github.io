---
layout: post
title: Árboles sintácticos
---



## 1. Intro

LaTeX es un lenguaje de marcado --basado en TeX-- que se usa para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica en generar, p. ej., diagramas de flujo, grafos, árboles de decisión, automátas, etc. a través de gráficos vectoriales (`PGF/TikZ`) y complejas fórmulas matemáticas gracias a su **modo matemático**. 

¡LaTeX es una herramienta versátil!, ya que cuenta con una sinfinidad de paquetes que siempre se ajustan a nuestras necesidades.

En el caso de la lingüística, resulta muy útil porque existen un conjunto de paquetes que nos permiten escribir símbolos fonéticos (con `tipa`), glosas (con `gb4e` o `covington`), enumeración de ejemplos (con `gb4e`,  `ling-macros`, `linguex` o `philex` ), estructuras de representación del discurso (con `drs`), árboles de dependencia (con `TikZ-dependency`) y árboles sintácticos de constituyentes (con `xyling`, `xy`, `tikz-qtree` o `forest`), etc. Como podemos observar mucha gente ha dedicado tiempo y esfuerzo para crear estos paquetes lingüísticos, cabría que considerar si el aprendizaje y el uso de estos formaría parte complementaría dentro de nuestra formación profesional como lingüístas. ¡Yo pienso que sí! Incluso el aprendizaje de cosas nuevas siempre puede resultarnos satisfactorio.

A lo largo de este *post*, nos enfocaremos en explicar algunas maneras en las que podemos dibujar árboles sintácticos con `forest` porque pensamos que es un paquete bastante intuitivo para la elaboración de representaciones árboreas. Además, para lograr este objetivo, consideraremos que el lector ya cuenta con algunos conocimientos básicos en el uso LaTeX; si este no es el caso existen muy buenos manuales en internet. 

Añado un curso en GitHub (no es el único) que posiblemente pueda interesar:

[Introducción a LaTeX](https://github.com/piratax007/LaTeX_Course)


### 1.1. Creando nuestras primeras representaciones con forest

Para comenzar, tendremos que cargar el paquete de `forest` en el preámbulo de nuestro documento:


```{=latex}

\usepackage[linguistics]{forest}

```

Una cuestión importante que debemos tomar en cuenta para el futuro es que al momento de hacer las flechas de los movimientos sintácticos que conectan los nodos,  `forest` produce un conflicto con algunos caracteres del paquete `babel` en español. Para evitar este problema, tenemos que escribir lo siguiente: 


```{=latex}

\usepackage[spanish, es-noshorthands]{babel}

```

Esto nos mantendrá prevenidos de futuros errores que puedan resultarnos frustantes. Muy bien, ahora, dentro del cuerpo de nuestro documento, llamaremos al ambiente de `forest`. En este punto, veremos que la sintaxis básica de este paquete consiste en usar corchetes para anidar otros corchetes. ¡Así de fácil! Como observamos en el siguiente ejemplo, el corchete más grande tiene en su inicio un **1**, que corresponde a la posición del nodo madre, y anida otros dos corchetes con sus respectivos números: **2** y **3**, que son los nodos hermanos. 


```{=latex}

\begin{document}

\begin{forest}
[1 [2] [3]]
\end{forest}

\end{document}
```

Compilamos y  produce:

<img src = "/images/post_1/ejemplo1.png" width = "500" height = "300" alt = "Primer ejemplo">

<!--- ![Primer ejemplo](/images/post_1/ejemplo1.png) -->

Si hemos comprendido esto, ya estamos a la mitad del camino para construir diagramas mucho más complejos, pero antes repitamos este mismo proceso y hagamos otras combinaciones para practicar.

```{=latex}

\begin{forest}
[1 [2 [4] [5]] [3 [6] [7]]]
\end{forest}

```
<img src = "/images/post_1/ejemplo2.png" width = "500" height = "300" alt = "Segundo ejemplo">


<!--- ![Segundo ejemplo](/images/post_1/ejemplo2.png) -->

```{=latex}

\begin{forest}
[1 [2 [6]] [3 [7]] [4[8]] [5[9]]]
\end{forest}

```


<img src = "/images/post_1/ejemplo3.png" width = "500" height = "300" alt = "Tercer ejemplo">

<!--- ![Tercer ejemplo](/images/post_1/ejemplo3.png) -->


### 1.2. Creando el esquema X-barra

Daremos un paso más allá y trataremos de dibujar el esquema de X-barra. Lo primero que debemos de saber es que temos una proyección máxima **SX**, que domina dos nodos: **SY** y **X'**. Hay que recordar que el primero es la posición del especificador y el segundo, de la proyección intermedia. Además, tenemos una proyección intermedia **X'**  que domina dos nodos: el núcleo sobre el cuál se proyecta toda la estructura **X<sup>0</sup>** y el complemento **SZ**. De todo esto, primero, podemos empeñarnos en construir la parte de arriba:

```{=latex}

\usepackage{philex} %Utilizamos este paquete para la numeración de nuestros ejemplos, diagramas, etc.

\begin{document}

\lb{ejemploxbar1}{
\begin{forest}
    [SX [SY] [X'] ]
\end{forest}
    }

\end{document}
```

Puede resultar un poco confuso este segmento de código, pero, con el fin de enumerar nuestro esquema, solamente  hemos añadido un ambiente del paquete `philex`. Expliquemos un poco este ámbiente `lb{}{}`: dentro de las primera llaves `{}` escribimos un identificador de nuestro ejemplo, para usarlo más tarde en alguna referencias cruzadas a lo largo del escrito de nuestro texto y tener control de ellos; yo he utilizado `ejemploxbar1`, pero puede llevar cualquier otro que deseen. En las segundas llaves, hemos anidado el ambiente de `forest`. 

En cuanto al encorchetado dentro de este ámbiente, observamos que el corchete principal, el más externo **SX**, contiene otros dos: **SX** y **X'**. Después de compilarlo, obtenemos el siguiente resultado:


<img src = "/images/post_1/ejemplo4.png" width = "500" height = "300" alt = "Cuarto ejemplo">

<!---![Cuarto ejemplo](/images/post_1/ejemplo4.png) -->


Como podemos observar, nuestro esquema de X-barra sigue incompleto falta añadir el nivel de abajo. Por lo tanto, lo único que tenemos que hacer es anidar dentro de la proyección intermedia dos corchetes más para obtener nuestro primer esquema X-barra.  


```{=latex}
\lb{ejemploxbar1}{
\begin{forest}
    [SX [SY] [X' [X$^0$] [SZ]] ]
\end{forest}
}

```

<img src = "/images/post_1/ejemplo5.png" width = "500" height = "300" alt = "Quinto ejemplo">


<!--- ![Quinto ejemplo](/images/post_1/ejemplo5.png) -->

Antes de terminar este apartado, me gustaría señalar que algunas veces tenemos que dibujar diagramas mucho más complejos, por lo que va a llegar un momento en el que resultará complicado manejar todo el encorchetado. Para evitar esto, eso se recomiendo separar en cada linea por niveles los segmentos más importantes de nuestro árbol con sangrías y alinear el corchete de cierre al final con el de apertura. Todo esto no modificará el resultado, pero nos ayudará prevenir muchos posibles errores.


```{=latex}
\lb{ejemploxbar1}{
    \begin{forest}
    [SX [SY] 
        [X' [X$^0$] [SZ]
        ] 
    ]
    \end{forest}
}

```

## 1.2. Proyecciones intermedias

La utilidad de las proyecciones intermedias es que nos permiten justificar la posición de los adjuntos que ocurren en una construcción sintáctica, además de que son recursivas, es decir, pueden proyectarse más de una vez dentro de la estructura arborea. En el caso de la nuestra, no tomamos en cuenta esta proyección, pero ya es hora. Lo que tenemos que hacer es anidar en nuestra proyección intermedia otra proyección con la misma etiqueta más la posición de adjunto. Esta nueva proyección intermedia albergará otro que su vez incluirá el núcleo y la posición de sujeto.     

```{=latex}

\lb{ejemploxbar2}{
    \begin{forest}
    [SX [SY] 
        [X' 
            [X' [X$^0$] [SZ]] [SW] 
        ]     
    ]
    \end{forest}
    }
   
```

<img src = "/images/post_1/ejemplo6.png" width = "500" height = "300" alt = "Sexto ejemplo">

<!--- ![Sexto ejemplo](/images/post_1/ejemplo6.png) -->


Podemos repetir el mismo proceso para producir otro nivel. En la siguiente línea se muestra un ejemplo:
    
```{=latex}
\begin{forest}
        [SX [especificador]
            [X'
                [X'  
                    [X' [X$^0$] [Complemento]] 
                    [Segundo Complemento]] 
                        [Adjunto]
            ]
        ]
    \end{forest}
```

<img src = "/images/post_1/ejemplo7.png" width = "500" height = "300" alt = "Séptimo ejemplo">

<!--- ![Séptimo ejemplo](/images/post_1/ejemplo7.png)  -->


## Movimiento sintáctico


<img src = "/images/post_1/ejemplo8.png" width = "500" height = "300" alt = "Octavo ejemplo">

<!--- ![Octavo ejemplo](/images/post_1/ejemplo8.png)  -->

