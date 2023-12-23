---
layout: post
title: Resumen de Gramáticas y lenguajes formales
usemathjax: true
---


 Gramáticas formales y lenguajes formales

Leonor Becerra-Bonache, Gemma Bel-Enguix, M. Dolores Jiménez-López, Carlos Martín-Vide

---

# Introducción

- Los lenguajes pueden ser naturales o formales: los primeros no fueron conscientemente inventados, los segundos sí.
- **Ejemplos de lenguajes naturales** (creados para la interacción humana):
    
    inglés, español, francés
    
- **Ejemplos de lenguajes formales** (creados para objetivos específicos):
    
    lenguajes de programación: python, java, c++.
    

💡 Se define un lenguaje como un conjunto de **oraciones** (*sentences*), donde una oración es una **cadena finita de símbolos** sobre un **alfabeto.** La manipulación de esos símbolos es la fuente de la teoría formal del lenguaje (Becerra-Bonache et al., 2022, pág. 207).


- La teoría formal del lenguaje tiene su origen en las matemáticas y en la lingüística.

- Matemáticas:
    - A. Thue (**Axel Thue)** y E. Post (Emil Post), introdujeron la noción formal de sistema de rescritura (*rewriting system*), mientras A. Turing formulaba la idea de encontrar un modelo de computación donde el poder de un modelo pudiera describir la complejidad del lenguaje se genera/acepta.
- Lingüística:
    - N. Chomsky inició el estudio de la gramática y la estructura gramatical del lenguaje en 1950. Él propuso la clasificación jerárquica de las gramáticas formales, conocida como la jerarquía de Chomsky.

- La primera generación de lenguajes formales, fijada en la jerarquía de Chomsky, fue basada en la **reescritura** y provocó la generalización de modelos arbóreos para lenguajes de computación.
- La segunda fue las **gramáticas contextuales**, estas rechazaron la reescritura. Más tarde nuevas tipologías emergieron y no correspondieron a la jerarquía de Chomsky (*context-sensitive formalism*).

---

# 1. Conceptos básicos: Alfabetos, cadenas y lenguajes

*V* = **alfabeto** o vocabulario es un **conjunto finito de letras** o símbolos (v, *letters*).

*V**  = Se obtiene al haber concatenado los símbolos de *V,* es un **conjunto infinito de cadenas** (*w*, *strings*)  o **palabras** (*words*). 

*λ* = es la **cadena vacía** y no contiene letras (*letters*). Además, es el elemento unidad de *V** bajo la operación de concatenación. 

— **operación concatenación de una cadena**: es una operación asociativa y no conmutativa que cierra (se incluye) *V**, es decir: 

 para todo $w,v  \in V^* : wv \in V^*$  

La **longitud (*length, cardinalidad* ) de una cadena** *w,* denotada por *|w|*, es el número de letras de que consiste la cadena.

Ejemplo:

 $|λ| = 0$ 

 $|wv| = |w| + |v|$

$w =$ es una **subcadena** (*substring*) o **subpalabra** (*subword*) de *v* si y solo si existe $u_1,u_2$ tal que $v = u_1wu_2$

- Algunos casos especiales de subcadena:
    - Si $w \neq \lambda$  y $w \neq v$, entonces $w$ es una subcadena propia de $v$,
    - si $u_1 = \lambda$, entonces $w$ es un prefijo (**prefix**) o un cabeza (**head**).
    - si $u_2 = \lambda$, entonces $w$ es un sufijo (**suffix**) o un cola (**tail**).

La **concatenación iterada** (*iterated concatenation*) $i$-veces de $w$ se muestra de la siguiente manera:

si $w = ab$, entonces $w^3 = (ab)^3 = ababab$

$w^0 = \lambda$

si $w = a_{1}a_{2} ... a_n$, entonces su imagen espejo (*mirror image or reversal*) $w^{-1} = a_{n}a_{n-1} ... a_{1}$


💡 Cualquier subconjunto $L \subseteq V^{\*}$ incluyendo tanto a $\\emptyset$ y $\\{\lambda\\}$ es un **lenguaje**. Uno lo denota $V^{+} = V^{*} -\\{\lambda\\}$.


---

# 2. Operaciones del lenguaje

- Dado que los lenguajes son conjuntos, para obtener nuevos lenguajes podemos usar la misma operación que usamos con conjuntos.
- Operaciones usuales de teoría de conjuntos aplicados en lenguajes:
    
    **Unión**: $L_{1} \\cup L_{2} = \\{w: w \in L_{1}  \\lor w \in L_{2} \\}$
    
    **Intersección**: $L_{1} \\cap L_{2} = \\{w: w \in L_{1} \\land w \in L_{2}\\}$
    
    **Diferencia**: $L_{1} - L_{2} = \\{w: w \in L_{1} \\land w \\notin L_{2} \\}$
    
    **Complemento** de $L \\subseteq V^{\*}$ con respecto de $V^{\*} : \\bar{L} = V^{\*} - L$
    
- Operaciones específicas de la teoría de lenguajes aplicadas en lenguajes:
    
    **Concatenación**: $L_{1}L_{2} = \\{w_{1}w_{2}: w_{1} \\in L_{1}  \\land w_{2} \in L_{2} \\}$
    
    **Iteración**: 
    
    $L^0 = \\{\lambda\\}$,
    
    $L^1 = L$,
    
    $L^2= LL$, 
    
    ...
    
    **Clausura de iteración: estrella de Kleene** (*closure of the iteration: Kleene star*):
    
    $$L^\* = \bigcup_{i \geq 0} L^i$$


    **Clausura positiva de la iteración: Kleene plus** (*positive closure of the iteration*):
    
    $$L^+ = \bigcup_{i \geq 1} L^i $$
    
    - Hay que notar que $L^+$ es igual a $L^*$ si $\lambda \in L$ e igual a $L^\* - \\{\lambda\\}$ si $\lambda \notin L$
    
    **Imagen espejo**: $L^{-1} = \\{w: w^{-1} \in L \\}$
    
    - Hay que notar que $(L^{-1})^{-1} = L$ y que $(L^{-1})^i = (L^i)^{-1}$ para cada $i \geq 0$
    
    **Right quotient** (cociente de la derecha) de $L_1$ sobre $L_2: L_1/L_2 = \\{w:$ donde existe $v \in L_2$  tal que $wv \in L_1 \\}$
    
    **Right derivative** de $L$ sobre $v: \partial_{v}^{r} L = L /\\{v\\} = \\{w: wc \in L \\}$
    
    **Head of** $L \subseteq V^\*: HEAD(L) = \\{w \in V^\*:$  donde existe $v \in V^\*$  tal que $wv \in L \\}$
    
    - Hay que notar que para cada $L:L \subseteq HEAD(L)$
    
    **Left quotient** de $L_1$ sobre $L_2\backslash L_1: \\{w:$  donde existe  $v \in L_2$  tal que $vw \in L_1 \\}$
    
    **Left derivative** de $L$ sobre $V: \partial_{v}^{l}L = \\{v\\} \backslash L = \\{w: wv \in L \\}$
    
    **Tail** of $L \subseteq V^\*: TAIL(L) = \{w \in V^\*:$  donde existe $v \in V^\*$  tal que $vw \in L \\}$ 
    
    - Hay que notar que para cada $L: L \subseteq TAIL(L)$
    
    **Morfismo**: Dados dos alfabetos $V_1, V_2,$  una asignación (*a mapping*) $h: V_{1}^{*} \longrightarrow V_{2}^{*}$ es un morfismo si y solo si: 
    
    [(i)] para cada $w \in V_1^{*}$, donde existe $v \in V_2^{*}$, tal que $v = h(w)$  and $v$  es único
    
    [(ii)] para cada $w, u \in V_1^{*}: h(wu) = h(w)h(u)$
    
    - A morphism is called $\lambda$-free if, for every $w \in V_{1}^{*}$, if $w \neq \lambda$  then $h(w) \neq \lambda$
    
    **Morphic image**: $h(L) = \{v \in V_2^*: v = h(w)$, para algún $w \in L\}$
    
    Un morfismo se llama un **isomorfismo** si, para cada $w,u \in V_1^*$, si $h(w) = h(u)$ entonces $w = u$
    
    (1) Un isomorfismo entre $V_1 = \{0, 1, 2, ... 9\}$ y $V_2 = \{0, 1\}$ es la codificación binaria de la representación decimal de los enteros:
    
    $h(0) = 0000, h(1) = 0001, ..., h(9) = 1001$
    

<aside>
💡 La unión, la concatenación y la estrella de Kleen son denominadas operaciones regulares (Becerra-Bonache et al., 2022, pág. 209).

</aside>

## 3. Gramáticas

<aside>
💡 Una gramática es un mecanismo finito por el cual podemos generar las cadenas de un lenguaje.

</aside>

> **Definición 1** Una gramática (formal) es una construcción $G = (N, T, S, P)$, donde
> 
- $N$ es un **alfabeto no-terminal**,
- $T$ es un **alfabeto terminal**,
- $N \cap T = \empty$,
- $S$ es la **letra inicial** (*initial letter*) o **axioma**, $S \in N$,
- $P$ es el conjunto de **reglas de reescritura** o **producciones**. $P$ es un conjunto finito de pares $(w, v)$ tal que $w, v \in (N \cup T)^*$ y $w$  contiene al menos una letra de $N$. $(w, v)$  usualmente se escribe como  $w \rightarrow v$.

> **Definición 2** Dado que $G = (N, T , S , P)$ y $w, v \in (N \cup T)^*$, una **derivación inmediata** o **directa** (en un paso) $w \Rightarrow_{G} v$ se lleva a cabo (*holds*) si y solo si: (i)  existe $u_1, u_2 \in (N \cup T)^*$ tal que $w = u_1\alpha u_2$ y $v = u_1\beta u_2$, y (ii) existe un $\alpha \longrightarrow \beta \in P$
> 

> **Definición 3** Dado que $G = (N, T, S, P)$ y $w, v \in (N \cup T)^*$, una **derivación** $w \Rightarrow_{G}^{*}v$ se lleva a cabo si y solo si existe tanto $w = v$ como $z \in (N \cup T)^*$  tal que $w \Rightarrow_{G}^{*} z$ y $z \Rightarrow _{G} v$.
> 

Hay que notar que $\Rightarrow_{G}^{*}$ denota la *reflexive transitive closure* y $\Rightarrow_{G}^{+}$ la *transitive closure,* respectivamente de $\Rightarrow_{G^{\cdot}}$

> **Definición 4** El lenguaje generado por una gramática se define como:
> 

$L(G) = \{W: S \Rightarrow_{G}^{*} w$   y $w \in T^{*} \}$

(2) Sea $G = (N, T, S, P)$ una gramática tal que: 

$N = \{S, A, B\}$,

$T = \{a, b, c\}$,

$P = \{S \rightarrow abc, S \rightarrow aAbc, Ab \rightarrow bA, Ac \rightarrow Bbcc, bB \rightarrow Bb, aB \rightarrow aaA, aB \rightarrow aa \}$ 

El lenguaje que se genera por $G$ es el siguiente: 

$L(G) = \{a^nb^nc^n: n \geq 1\}$
