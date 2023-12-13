<h2>Calibrar una impressora 3D	</h2>


<p>(Impressores 3D)


[TOC]


<h2 id="enunciat">Enunciat</h2>


Conjunt de test o passos per aconseguir calibrar correctament una impressora 3D.



<h2 id="torre-de-temperatura">Torre de temperatura</h2>


<h3>Descripció</h3>


Impressió d’un objecte amb aspecte de torre on cada bloc s’imprimirà amb una temperatura diferent, és a dir, comemcem amb una temperatura màxima d’impressió i l’anem descendint cada 5 graus per comprobar la temperatura l’extrusió d’un material.


```
🔅 Es recomana el seu us cada vegada que emprem un nou material.
```


<h3>Impressora</h3>


Aquesta prova es realitza emprant la impressora [Prusa i3 MK3S+](https://www.prusa3d.com/es/categoria/original-prusa-i3-mk3s/).

<h3>Model STL</h3>


**Plataforma**: [Printables.com: 3D model database](#bookmark=id.u12klh5vmi5h)

**Objecte 3D**: [Temperature tower](https://www.printables.com/model/316034-temperature-tower) _(material PLA)_

<h3>Material</h3>


S’usa aquest filament per la prova de torre de temperatura:


<table>
  <tr>
   <td><strong>Característiques</strong>
   </td>
   <td><strong>Filament</strong>
   </td>
  </tr>
  <tr>
   <td><strong>Tipus</strong>: PLA Basic
<p>
<strong>Model</strong>: Basic
<p>
<strong>Color</strong>: Bambu Green (10501) 
<p>
<strong>Marca</strong>: Bambu Lab
<p>
<strong>Temperatura</strong>: 195-230ºC
<p>
<a href="https://eu.store.bambulab.com/en-es/products/pla-basic-filament?variant=46673378607452">Web</a>
   </td>
   <td>

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image1.jpg" width="" alt="alt_text" title="image_tooltip">

   </td>
  </tr>
</table>


<h3>Configuració</h3>


Si emprem [PrusaSlicer](#bookmark=id.vazuuk5zzkog) o Cura necessitarem indicar a cada capa d’inici del bloc la temperatura que volem imprimir.

Els paràmetres:



* **Temperatura**: L'escrita en el primer esglaó de la torre a imprimir.
* **Cabal**: 100%
* **Altura de la capa**: 0,2 mm
* **Perímetre**: 2 o 3
* **Farciment**: 5 o 10% (el patró és indiferent)

El rang de temperatures de la torre serà 190-225 ºC, per tant, haurem d’ajustar les capes inicials de cada bloc amb una diferencia de 5º C, començant per la temperatura més alta i a mesura que la torre creix, anirem baixant la temperatura.

<h4>_Cas d’ús: PrusaSlicer_</h4>


Pas 1: Afegim el model de la torre i ajustem els paràmetres (veure 

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "configuració"). Did you generate a TOC with blue links? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[configuració](#heading=h.mumsqpljsap7)).

Pas 2: Seguidament fem _Laminar_.

Pas 3: Ara, indiquem la temperatura de cada bloc amb el gcode **_M104 S(Temperatura)_**. 

Ens posicionem en la capa de canvi de bloc, per exemple, en la imatge següent el bloc es el de la temperatura 205 ºC, per rant el següent és el de 200 ºC de temperatura. Fem clic amb el botó dret i seleccionem _Afegir codi G personalitzat_.



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Introduim el gcode **_M104 S200_**, per indicar que la temperatura serà de 200 ºC.



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")


Finalment, obtenim el canvi de totes les temperatures.



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")


Només queda fer clic a _Exportar el codi G_ i realitzar la impressió per avaluar el test.


```
🔅 L'eina SuperSlicer genera una torre de termperatura automàticament per imprimir.
```


<h3>Resultat</h3>


Una vegada que la torre de temperatura ha acabat d'imprimir, observem els diferents passos amb èmfasis en les següents preguntes _([imatge anterior](#bookmark=id.k4gskpg31e39))_:



* **Ponts**: forat central de la peça.
* **Voladissos de 15, 30 i 60 graus**: costat esquerra de la peça.
* **Zones arrodonides i petites retraccions**: costat dret de la peça.
* **Nombres**

Després d'analitzar tots els esglaons, seleccionem el que millor s'adapta a aquestes situacions i la temperatura indicada en ell serà la temperatura òptima per al material analitzat.

<h4>_Cas d’ús_</h4>


Un cop analitzades les imatges de la impressió, el rang amb menys problemes sembla de 190-205 ºC de temperatura, esent el valor de 200 ºC la tempreatura ideal per aquest filament, ja que no s’aprecien problemes de _pont_, ni _voladissos_, ni_ arrodoniments_  ni en els _nombres_, només hi ha petits filaments**_ (Stringing)_** degut a la retroacció que haurem d’ajustar en properes calibracions.



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.jpg "image_tooltip")


<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.jpg "image_tooltip")



```
🔅 És possible que la peça no s'imprimeixi per complet perquè el fusor està embussat a causa de la baixa temperatura. Si això succeeix, detingui la impressió i analitzi la part incompleta de la mateixa manera.
```




<h2 id="fluxe">Fluxe</h2>


<h3>Descripció</h3>


Volem calibrar la quantitat de filament exacta que surt pel nostre nozzle sobretot en impressions dinàmiques.  Impressió d’un objecte amb aspecte de torre on cada bloc s’imprimirà amb una temperatura diferent, és a dir, comemcem amb una temperatura màxima d’impressió i l’anem descendint cada 5 graus per comprobar la temperatura l’extrusió d’un material.


```
🔅 Es recomana el seu us cada vegada que emprem un nou material.
```


<h3>Impressora</h3>


Aquesta prova es realitza emprant la impressora [Prusa i3 MK3S+](https://www.prusa3d.com/es/categoria/original-prusa-i3-mk3s/).

<h3>Model STL</h3>


**Plataforma**: [Printables.com: 3D model database](#bookmark=id.u12klh5vmi5h)

**Objecte 3D**: [Temperature tower](https://www.printables.com/model/316034-temperature-tower) _(material PLA)_

<h3>Material</h3>


S’usa aquest filament per la prova de torre de temperatura:


<table>
  <tr>
   <td><strong>Característiques</strong>
   </td>
   <td><strong>Filament</strong>
   </td>
  </tr>
  <tr>
   <td><strong>Tipus</strong>: PLA Basic
<p>
<strong>Model</strong>: Basic
<p>
<strong>Color</strong>: Bambu Green (10501) 
<p>
<strong>Marca</strong>: Bambu Lab
<p>
<strong>Temperatura</strong>: 195-230ºC
<p>
<a href="https://eu.store.bambulab.com/en-es/products/pla-basic-filament?variant=46673378607452">Web</a>
   </td>
   <td>

<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image7.jpg" width="" alt="alt_text" title="image_tooltip">

   </td>
  </tr>
</table>




<h2 id="recursos">Recursos</h2>



    [Printables.com: 3D model database](https://www.printables.com/)


    [PrusaSlicer](https://github.com/prusa3d/PrusaSlicer/releases)


    [SuperSlicer](https://github.com/supermerill/SuperSlicer)
