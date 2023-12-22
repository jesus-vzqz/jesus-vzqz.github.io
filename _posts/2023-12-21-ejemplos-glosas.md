---
layout: post
title: Ejemplo de glosas en LaTeX
---


# Algunas consideraciones sobre los ejemplo 

Los siguientes ejemplos de glosas fueron extraídos Conti (2020). Los paquetes que se utilizaron fueron `philex` para la numeración y `tipa` para las glosas. 

```{=latex} 

 \lb{vaskia}{Vaskia (lengua madana; Ross, 1978, pág. 31), \textit{apud} \citep[pág. 151]{conti_fundamentos}\\
 \textit{Gagi bamban \textbf{kaiyam-ale} Kaimkadi \textbf{tuam}}\\
        Gagi pescado cocinó-MS Kaimkadi le.dar.3SG\\
        `Gagi cocinó pescado (y) se lo dio a Kaimkadi'}
```
<img src = "/images/post_2/ejemplo1.png" width = "500" height = "300" alt = "Primer ejemplo">

<!--- ![Primer ejemplo](/images/post_2/ejemplo1.png) -->

```{=latex} 
\lb{tipomarcadores}{
    \lba{tipo1}{Marcador de enlace prepositivo:\\
    \textit{\underline{Si} vienes mañana, te traigo el libro.} }
    \lbb{tipo2}{Marcador de enlace pospositivo (kombay, lengua aviu-dumut: \textit{apud} Dryer (2013):\\
    \textit{khe-khino rerakharu \underline{rodofe}}\\
    POS-piernas hinchado porque\\
    `Porque sus piernas están hinchadas'}
    \lbz{tipo3}{Marcador de enlace inserto (encore-kiga, lengua bantú, \textit{apud} Dryer (2013):\\
    \textit{wa-kanu \underline{obu} y-aa-tuuriza enjojo\\
    señor-conejo cuando él-PAS-desafiar elefante\\
    `Cuando el señor conejo desafió al elefante'}}}
```

<img src = "/images/post_2/ejemplo2.png" width = "500" height = "300" alt = "Segundo ejemplo">

<!--- ![Segundo ejemplo](/images/post_2/ejemplo2.png) -->



```{=latex}
\lb{fconcatenadas}{
    \lba{cform1}{Enclítico (yukulta, lengua tángica; \textit{apud} Dryer (2013))\\
    \textit{\textipa{pulawa\|[ta-\ng i\ng ki, \hspace{0.3cm} [\ng apay=\underline{aka}=\ng ka \hspace{0.8cm} kalka]}} \\
    morir.IND-él.FUT muy=porque=PRES enfermo\\ `Quizá muera, porque está muy enfermo'}
    \lbb{cform2}{Morfema verbal (walpiri, lengua pama-ñunga; Lehmann (1986))\\
    \textit{  \textipa{[njuntulu-lu \underline{kutja}-$\emptyset$-npa \hspace{0.3cm} wawiri pantu-mu,] \hspace{0.5cm}\ng ula kapi-na pura-ni \ng atjulu-lu  }} \\ tú-ERG MENL-AUX-SUJ.2 canguro arponear-PAS DEM FUT-SUJ.1 cocinar-PRES yo-ERG \\ `Cocinaré el canguro que arponeaste'}
   }
```

<img src = "/images/post_2/ejemplo3.png" width = "500" height = "300" alt = "Tercer ejemplo">

<!--- ![Tercer ejemplo](/images/post_2/ejemplo3.png) -->



```{=latex}
\lb{marcadcorrela}{
    \lba{marc1}{\textit{Es \underline{tan} alto \underline{como} su padre. Comparativa } }
    \lbb{marc2}{\textit{Apretó \underline{tanto} la tapa, \underline{que} el boté acabó rompiéndose.\\ Consecutiva }  }
    \lbb{marc3}{\textit{\underline{Si} no sabe montar en bici, \underline{entonces} tendrá que caminar.\\ Condicional  }  }
    \lbb{marc4}{Hindi (lengua índica; Lipták (2009)) \\ 
    \textit{ \textipa{[\underline{jo}} vahaaN khaRii hai\textipa{]} raam \underline{us} laRii-ko jaantaa hai }\\
    REL allí parando es Ram DEM chica-AC conocer es\\ `Ram conoce a la chica que está allí parada'   }
    \lbz{marc5}{Chino mandarín (lengua sínica; Bisang (1998)) \\
    \textit{J\textipa{\={\i}nti\=an \underline{su\={\i}-rán}  yu\u{o}-f\={e}ng, \underline{d\`anshi} b\`u l\v{e}ng }}\\
    hoy aunque ser-viento pero NEG frío \\ `Aunque hoy hace viento, no hace frío' }}
```

<img src = "/images/post_2/ejemplo4.png" width = "500" height = "300" alt = "Cuarto ejemplo">

<!--- ![Cuarto ejemplo](/images/post_2/ejemplo4.png) -->


```{=latex}
\lb{conveb}{
    \lba{converb1}{Wixárika (lengua corachol; Comrie (1982))\\
    \textit{\textipa{nee ne-nua-\textbf{ka} paapaa ne-p-ii-\textglotstop\textbari\textbari t\textbari}\\ yo 1SG-llegar-MS tortilla 1SG-3SG-dar}\\ `Cuando llegué, le di la tortilla' }
    \lbb{converb2}{\textit{\textipa{nee ne-nua-\textbf{ku}, iya paapaa nec-u\textglotstop\textbari it\textbari }\\ yo 1SG-llegar-SD él tortilla 1SG-dar} \\ `Cuando llegué, me dio una tortilla'          }}
```

<img src = "/images/post_2/ejemplo5.png" width = "500" height = "300" alt = "Quinto ejemplo">

<!--- ![Quinto ejemplo](/images/post_2/ejemplo5.png) -->



```{=latex}
\lb{ejempaguaruna}{
    \lba{agua1}{Aguaruna (lengua jíbara, Overall (2009)\\
     \textit{\textipa{[yu-wa-tasa-\textbf{nu}] \hspace{1.5cm} wa\textbari\textturnmrleg-hai-i}} \\
     comer.PERF-INIT-MS1SG querer.IMPERF-1SG-DECL\\ Lit. `Quiero que yo coma', `quiero comer' }
    \lbb{agua2}{\textit{\textipa{[yawa\~a \textbari k\textbari na-\textbf{ma\~{\i}}] \hspace{2cm}maa-ha-i}} \\
    perro levantar.PERF-SEC.SD1/3 matar.PERF-1SG-DECL\\ `Cuando el perro levantó (el agutí), (lo) maté'  }
    \lbz{agua3}{\textit{\textipa{[wak\textbari\textturnmrleg a-ku-m\textbari-\textbf{ka}] \hspace{2cm} yuwa-ta} }\\
    querer.IMPF-SIMUL-MS2-COND comer.PERF-IMP\\ `¡Come si quieres!'   }
}
```

<img src = "/images/post_2/ejemplo6.png" width = "500" height = "300" alt = "Sexto ejemplo">

<!--- ![Sexto ejemplo](/images/post_2/ejemplo6.png) -->


```{=latex}
\lb{wappo}{
\lba{wappo1}{Wappo (lengua yuki, Thompson, Longacre y Hwang (2007)\\
  \textit{\textipa{ah te  \v{s}awo \textbf{pa\textglotstop -tah} ha is-khi\textglotstop}} \\ 
  yo él.AC pan comer-PAS saber-NFUT\\ `Sé que comió el pan'}
    \lbb{wappo2}{\textit{\textipa{cephi \v{s}awo \textbf{pa\textglotstop-ta\textglotstop}}} \\ él pan comer-PAS \\ `Comió pan'}}
```
<img src = "/images/post_2/ejemplo7.png" width = "500" height = "300" alt = "Séptimo ejemplo">

<!--- ![Séptimo ejemplo](/images/post_2/ejemplo7.png) -->


```{=latex}
\lb{kham}{
 Kham (lengua kham-magar Watters (2009))\\ 
    \textit{\textipa{\textbf{ba-o} op\textschwa\~{\i}-zya-o-t\textschwa, \textbf{ba-o} mao-d\textschwa i-wo}} \\
    ir-NOMZ 3SG-querer-CONT-NOMZ-SUPERES ir-NOMZ\\ `Aunque quería ir, no se le permitiría (ir)' }
```
<img src = "/images/post_2/ejemplo8.png" width = "500" height = "300" alt = "Óctavo ejemplo">

<!--- ![Óctavo ejemplo](/images/post_2/ejemplo8.png) -->

```{=latex}
\lb{japonés}{Japonés (lengua japonesa, Comrie (1998))\\ 
    \textit{\textipa{[}G\textipa{akusei ga katta] hon}} \\ estudiante NOM compró libro \\
    `El libro que compró el estudiante'}
```
<img src = "/images/post_2/ejemplo9.png" width = "500" height = "300" alt = "Noveno ejemplo">

<!--- ![Noveno ejemplo](/images/post_2/ejemplo9.png) -->


```{=latex}
\lb{chino}{ 
    \lba{chino1}{Chino mandarín (lengua sínica, Haspelmath (2013)\\ 
    \textit{L\textipa{isi xiwang} Z\textipa{hangsan zao dian huijia}}\\ 'Lisi quiere que Zhangsan regrese pronto'} 
    \lbb{chino2}{\textit{N\textipa{\u{\i}  gu\`\i-xi\`a-lái qiú} Zh\={a}ngs\={a}n }} \\
    tú rodilla-bajar-venir implorar Zhangsan\\ 
    1. `Te arrodillaste e imploraste a Zhangsan'\\
    2. `Te arrodillaste para implorar a Zhangsan'\\
    3. `Te arrodillaste implorante a Zhangsan'}
```
<img src = "/images/post_2/ejemplo10.png" width = "500" height = "300" alt = "Décimo ejemplo">

<!--- ![Décimo ejemplo](/images/post_2/ejemplo10.png) -->


## Referencia en formato Bibtex

```{=latex}
@book{conti_fundamentos,
  title={Fundamentos de sintaxis tipol{\'o}gica},
  author={Conti, Carmen},
  year={2016},
  publisher={Editorial S{\'\i}ntesis}
}
```

## Referencia en APA

Conti, C. (2016). *Fundamentos de sintaxis tipológica*. Editorial Síntesis.




