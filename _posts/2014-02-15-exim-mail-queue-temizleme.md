---
ID: 5277
post_title: Exim Mail Queue Temizleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/exim-mail-queue-temizleme-5277.html
published: true
post_date: 2014-02-15 21:42:29
---
Merhaba arkadaşlar,

Birazcık uzun bir aradan sonra sizlere çok faydalı bir ipucu sağlayacağım. Bu shell komutlarını en çok sunucusunda spam posta sıkıntısı yaşayanlar kullanacaktır. Soru cevap şeklinde paylaşıyorum:

<span style="color: #ff0000;">Soru: <span style="color: #000000;">Centos sunucumda Exim Posta Sunucusunu kullanıyorum. Posta kuyruğunu temizlemek istiyorum. Ne yapmalıyım</span></span>

<span style="color: #008000;">Cevap: <span style="color: #000000;">Exim, Unix işletim sistemlerinde kullanılan Posta Transfer Uygulamasıdır(MTA).</span></span>

<strong>Kuyruktaki postaları listelemek için:</strong>

<pre class="lang:bash decode:1 " >exim -bp</pre>

<strong>ID'si belli bir postayı kuyruktan silmek için:</strong>

<pre class="lang:bash decode:1 " >exim -Mrm {message-id}</pre>

<b>Kuyruktaki bütün postaları silmek için:</b>

<pre class="lang:bash decode:1 " >exim -bp | exiqgrep -i | xargs exim -Mrm</pre>

Umarım işinize yarar, kolay gelsin