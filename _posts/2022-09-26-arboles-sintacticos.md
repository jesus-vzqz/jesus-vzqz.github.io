---
layout: post
title: Árboles sintácticos
---



# 1. Intro

LaTeX es un lenguaje de marcado --basado en TeX-- que se usa para el procesamiento de textos científicos con una alta calidad tipográfica. Aunque nos permite crear una multiplicidad de escritos como lo son artículos, libros, presentaciones, cartas, etc., su poder radica en generar, p. ej., diagramas de flujo, grafos, árboles de decisión, automátas, etc. a través de gráficos vectoriales (`PGF/TikZ`) y complejas fórmulas matemáticas gracias a su **modo matemático**. 

¡LaTeX es una herramienta versátil!, ya que cuenta con una sinfinidad de paquetes que siempre se ajustan a nuestras necesidades.

En el caso de la lingüística, resulta muy útil porque existen un conjunto de paquetes que nos permiten escribir símbolos fonéticos (con `tipa`), glosas (con `gb4e` o `covington`), enumeración de ejemplos (con `gb4e`,  `ling-macros`, `linguex` o `philex` ), estructuras de representación del discurso (con `drs`), árboles de dependencia (con `TikZ-dependency`) y árboles sintácticos de constituyentes (con `xyling`, `xy`, `tikz-qtree` o `forest`), etc. Como podemos observar mucha gente ha dedicado tiempo y esfuerzo para crear estos paquetes lingüísticos, cabría que considerar si el aprendizaje y el uso de estos formaría parte complementaría dentro de nuestra formación profesional como lingüístas. ¡Yo pienso que sí! Incluso el aprendizaje de cosas nuevas siempre puede resultarnos satisfactorio.

A lo largo de este *post*, nos enfocaremos en explicar algunas maneras en las que podemos dibujar árboles sintácticos con `forest` porque pensamos que es un paquete bastante intuitivo para la elaboración de representaciones árboreas. Además, para lograr este objetivo, consideraremos que el lector ya cuenta con algunos conocimientos básicos en el uso LaTeX; si este no es el caso existen muy buenos manuales en internet. 

Añado un curso en GitHub (no es el único) que posiblemente pueda interesar:

[Introducción a LaTeX](https://github.com/piratax007/LaTeX_Course)


## 1.1. Creando nuestras primeras representaciones con forest

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


## 1.2. Creando el esquema X-barra

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

## 1.3. Proyecciones intermedias

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


## 1.4. Movimiento sintáctico

Ya hemos visto algunos principios básicos para crear árboles sintácticos. Ahora, comenzaremos la manera de dibujar flechas entre los nodos, lo que corresponde dentro de la teoría cómo los movimientos sintácticos. Veamos el siguiente ejemplo tomado de Camacho (2018):  

<img src = "/images/post_1/ejemplo8.png" width = "500" height = "300" alt = "Octavo ejemplo">

<!--- ![Octavo ejemplo](/images/post_1/ejemplo8.png)  -->

Para construir el árbol anterior, debemos de seguir los pasos previamente presentados. Un código cercano para dibujar el árbol anterior puede ser escrito de la siguiente manera:

```{=latex}
\lb{x}{
\textbf{Construcción inergativa:}\\
    \lba{x1}{El paciente tosió}
    \lbb{x2}{
\begin{forest}
    [ST [T] 
        [Sv [SD[el][SN[paciente]]]
            [v'[tosió, name = 2]
                [SV [\sout{tosió}, name = 1][X]]]]]
\draw[->] (1) to[out=south,in=south] (2);
\end{forest}}}
```

En este caso, observamos cómo en el nodo correspondiente a `[v'[tosió, name = 2]` hemos indicado después de la coma `,` un parametro `name =2` en el que expresamos la etiqueta de este, llamándolo `2` (podría escribirse cualquier otro nombrae, p. ej., `núcleo2` o `posición2`). Dentro del mismo ambiente de `forest`, notamos cómo en el nodo de `[SV [\sout{tosió}, name = 1][X]]]`  asignamos `1`. Estas dos etiquetas son importantes porque nos van a ayudar a dirigir la dirección de nuestras flechas. 

Despúes de terminar el encorchetado de nuestro árbol sintáctico, podemos comenzar a dibujar las flechas que indican el movimiento sintáctico, para eso hacemos uso del comandoo de `tikz` `\draw[]`. Con este comando podemos especificar la dirección de la punta que queremos dibujar -- p. ej.,`\draw[->]`, `\draw[<-]`, `\draw[<->]`-- hasta el punto de inicio y final de la flecha `(1) to[out=south,in=south] (2)`, es decir, la cola de la flecha `(1)` se va a dirigir a `(2)`, la salida (`out = south`) será al sur y la llegada de la punta (`in = south`) será al sur. 

```{=latex}
\draw[->] (1) to[out=south,in=south] (2);
```

## 1.5 Otros ejemplos 

Ahora veamos otros ejemplos de código para poder dibujar árboles mucho más versátiles y detallados, tomados de Camacho (2018). 

```{=latex}
\begin{forest}
for tree={s sep=2mm, inner sep=0, l=0}
    [{envió$_{v}$+Flex/T} 
        [{Pablo$_N$ (FD)}]
        [{envió$_{v}$+Flex/T}
            [{le+envió$_V$+Flex/T}, name = objetivo4]    
            [{v$_L$(Fv$_L$)}
                [{un$_D$}(FD)   
                    [un$_D$] [diccionario$_N$(FN), name = objetivo1]] 
                [V$_L$
                    [\sout{Pablo} (FD)] 
                    [V$_L$
                        [{\sout{le+envió}+V$_L$}, name = objetivo3]
                        [envió$_V$ (FV) 
                            [{\sout{le+envió$_V$}}, name = objetivo2] 
                            [Apl(FApl)
                                [{a-Gabi$_N$(FD)}] 
                                [Apl
                                    [{\sout{le-Apl}}, name = salida2]
                                    [un$_D$ 
                                        [\sout{un}$_D$] [\sout{diccionario}$_N$, name = salida1]
                                    ]
                                ]
                            ]
                        ]
                    ]
                ]
            ]    
        ]
    ]
\draw[->] (salida1) to[out=south west,in=south] (objetivo1);
\draw[->] (salida2) to[out=south west,in=south] (objetivo2);
\draw[->] (objetivo2) to[out=south west,in=south] (objetivo3);
\draw[->] (objetivo3) to[out=south west, in=south] (objetivo4);
\end{forest}

```
<img src = "/images/post_1/ejemplo9.png" width = "500" height = "300" alt = "Noveno ejemplo">
<!--- ![Noveno ejemplo](/images/post_1/ejemplo9.png)  -->

En el anterior ejemplo, hemos puesto en práctica todos los elementos expresados a lo largo de este post. Algunos de los detalles que caben destacar se relacionan con la posición del arco de la flecha que atraviesa los caracteres que forman parte de los nodos. En el ejemplo anterior, repetimos el proceso para que cada una de las flechas saliera por los nodos definidos con una dirección de salida (`out = south west`) y una de entrada (`in = south`), sin embargo, esto ha provocado que la calidad de nuestro árbol no sea tan buena. Para eso, necesitamos cambiar el parámetro de la dirección de salida y entrada. 


```{=latex}
\begin{forest}
for tree={s sep=2mm, inner sep=0, l=0}
    [{envió$_{v}$+Flex/T} 
        [{Pablo$_N$ (FD)}]
        [{envió$_{v}$+Flex/T}
            [{le+envió$_V$+Flex/T}, name = objetivo4]    
            [{v$_L$(Fv$_L$)}
                [{un$_D$}(FD)   
                    [un$_D$] [diccionario$_N$(FN), name = objetivo1]] 
                [V$_L$
                    [\sout{Pablo} (FD)] 
                    [V$_L$
                        [{\sout{le+envió}+V$_L$}, name = objetivo3]
                        [envió$_V$ (FV) 
                            [{\sout{le+envió$_V$}}, name = objetivo2] 
                            [Apl(FApl)
                                [{a-Gabi$_N$(FD)}] 
                                [Apl
                                    [{\sout{le-Apl}}, name = salida2]
                                    [un$_D$ 
                                        [\sout{un}$_D$] [\sout{diccionario}$_N$, name = salida1]
                                    ]
                                ]
                            ]
                        ]
                    ]
                ]
            ]    
        ]
    ]
\draw[->] (salida1) to[out=south west,in=south] (objetivo1);
\draw[->] (salida2) to[out=-110,in=180] (objetivo2.south);
\draw[->] (objetivo2) to[out=south west,in=south] (objetivo3);
\draw[->] (objetivo3) to[out= -110, in= -122] (objetivo4.west);
\end{forest}
```

Los cambios que se han realizado son los siguientes: `\draw[->] (salida2) to[out=-110,in=180] (objetivo2.south);`, en esta linea se dibuja una flecha (`\draw[->]`), de la `(salida2)` hacia `(objetivo2.south)`, indicando el punto de llagada es hacia el sur del nodo. En el caso de lo que está encorchetado, `to[out=-110,in=180]`, expresamos que la dirección de salida es de `-110` grados (medidos en sentido antihorario desde el este) y la dirección de entrada es de 180 grados (o sea, oeste).

Si se nos dificulta pensar las medidas, hay que saber que en `Tikz`, las direcciones de las flechas las medimos en grados y pueden ser representadas dentro de un plano cartesiano. Por tanto, `0` y `360`grados corresponden al este (hacia la derecha del plano cartesiano, `90` grados corresponde al norte (la parte de arriba del plano), 180 grados corresponde al oeste (a la izquierda) y `270` grados corresponde al sur (abajo).   

De este modo, en la línea de `\draw[->] (objetivo3) to[out= -110, in= -122] (objetivo4.west);` indicamos que tanto la salida y la llegada sean en el sureste, especificando la llegada en la parte este del nodo. La ventaja de estas modificaciones es que nos permiten manejar la curvatura de las flechas y evitar la superposición de los elementos dentro del árbol. Al final obtenemos el siguiente ejemplo: 

<img src = "/images/post_1/ejemplo10.png" width = "500" height = "300" alt = "Décimo ejemplo">

<!--- ![Décimo ejemplo](/images/post_1/ejemplo10.png)  -->








