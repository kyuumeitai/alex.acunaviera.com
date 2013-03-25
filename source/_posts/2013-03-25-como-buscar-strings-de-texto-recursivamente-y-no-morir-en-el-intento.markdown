---
layout: post
title: "Cómo buscar strings de texto recursivamente y no morir en el intento."
date: 2013-03-25 14:27
comments: true
categories: código terminal tip
---

Como les decía, ahora estoy usando Octopress. Y lo instalé, (y subí, via rsync, como lo dice el tutorial). Nada muy complejo. Entonces, me encuentro con el sitio por defecto, y empiezo a buscar ciertos strings para reemplazar la traducción (porque [como bien dice el @zentaurus](http://o.tiuque.cl/aprendiendo/octopress/), no tiene un sistema centralizado para hacer traducciones). Entonces, me di cuenta de dos cosas:

1. Necesito generar otro *layout* en Octopress para hacer quickies y tirar tips rápido.
2. Necesito buscar recursivamente textos tipo "Posted" de forma rápida, para saber dónde editar y no revisar los archivos uno por uno.

Para el primero necesito tiempo (y estoy terminando mi hora de almuerzo, así que para la otra), pero el segundo punto lo utilizo a menudo en Multinet. 
<!-- more -->
Dice así:

	$ grep -H -r "Posted" .
	
Donde `grep` es una utilidad para buscar texto, el modificador `-H` hace que siempre salga al principio el archivo donde está el texto a buscar, no importa que se repita el archivo `-r` lo hace recursivo, "Posted" es el string de texto a buscar, y con el `.` especifico dónde quiero buscarlo (el punto quiere decir *búscalo aquí, en el directorio donde estoy parado*).

La salida de este comando arrojó lo siguiente:

	./.themes/classic/source/_includes/post/author.html:{% if author %}<span class="byline author vcard">Posted by <span class="fn">{{ author }}</span></span>{% endif %}
	./public/blog/2013/03/25/hola-mundo-bienvenido-a-wordp-dot-dot-dot-oh/index.html:<span class="byline author vcard">Posted by <span class="fn">Álex Acuña Viera</span></span>
	./source/_includes/post/author.html:{% if author %}<span class="byline author vcard">Posted by <span class="fn">{{ author }}</span></span>{% endif %}

Y otras líneas más (era mucho, pero así se entiende).
	
Si se fijan, el primero tiene el layout de Octopress, luego vienen los archivos compilados en HTML de los posts anteriores, y el resto eran los archivos markdown donde estoy escribiendo en este momento.

Así, puedo ir, modificar el archivo y listo.

