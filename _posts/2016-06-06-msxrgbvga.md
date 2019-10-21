---
title:  "Montando Conversor RGB -> VGA"
subtitle: "MSX RGB -> VGA"
author: "Alexandre"
avatar: "img/authors/zed.jpg"
image: "img/2016-06-06/00.jpg"
date:   2016-06-06 12:12:12
images1:
  - image_path: img/2016-06-06/01.jpg
    title: Esquema
    link: /img/2016-06-06/01.jpg 
  - image_path: img/2016-06-06/02.jpg
    title: Protoboard
    link: /img/2016-06-06/02.jpg
images2:
  - image_path: img/2016-06-06/03.jpg
    title: Esquema
    link: /img/2016-06-06/03.jpg 
  - image_path: img/2016-06-06/04.jpg
    title: Protoboard
    link: /img/2016-06-06/04.jpg
  - image_path: img/2016-06-06/05.jpg
    title: Esquema
    link: /img/2016-06-06/05.jpg 
  - image_path: img/2016-06-06/06.jpg
    title: Protoboard
    link: /img/2016-06-06/06.jpg
  - image_path: img/2016-06-06/07.jpg
    title: Esquema
    link: /img/2016-06-06/07.jpg 
  - image_path: img/2016-06-06/08.jpg
    title: Protoboard
    link: /img/2016-06-06/08.jpg
  - image_path: img/2016-06-06/09.jpg
    title: Esquema
    link: /img/2016-06-06/09.jpg 
---

	
Resolvi me aventurar um pouco em eletrônica e montar um conversos RGB -&gt; VGA para o meu MSX Gradiente para conectar em um monitor Samsung 710n.


Peguei esquema do site da http://www.msxpro.com/rgb-vga.html .
Como não entendo como interpretar um esquema para montar o circuito, pedi muita ajuda para o pessoal da lista de MSX, agradeço a todos que me ajudaram.

<a href="/img/2016-06-06/adaptador.gif" target="_blank"><img class="alignnone size-medium wp-image-989" src="/img/2016-06-06/adaptador.gif" alt="adaptador" width="300" height="197"></a>



Utilizei esta lista de componentes:

- 1 resistor de 1k;
- 1 resistor de 680k;
- 1 diodo Zener 5v1 por meio Watt;
- 1 LM1881;
- 1 soquete torneado de 8 pinos;
- 3 capacitores 100n;
- 1 conector fêmea db15 denso (vga);
- 1 soquete macho din 8 ou din 7;
- 1 cabo 8 vias;

Como não sei interpretar o esquema, acabei desenhando no papel como que faria o layout do circuito, e depois, montei um teste na protoboard.


<ul class="photo-gallery">
  {% for image in page.images1 %}
    <li>
      <a href="{{ image.link }}" target="_blank">
        <img src="{{ image.image_path }}" alt="{{ image.title}}"/>
      </a>
    </li>
  {% endfor %}
</ul>





<p style="clear:left;">Depois de testar, é hora de montar a placa e soldar os conectores.

<ul class="photo-gallery">
  {% for image in page.images2 %}
    <li>
      <a href="{{ image.link }}" target="_blank">
        <img src="{{ image.image_path }}" alt="{{ image.title}}"/>
      </a>
    </li>
  {% endfor %}
</ul>


