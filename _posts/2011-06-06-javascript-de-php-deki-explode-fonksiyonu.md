---
ID: 186
post_title: 'JavaScript&#8217;de PHP&#8217;deki Explode Fonksiyonu'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/javascript-de-php-deki-explode-fonksiyonu-186.html
published: true
post_date: 2011-06-06 19:18:11
---
Merhaba arkadaşlar,
PHP'de <strong>explode()</strong> fonksiyonu sayesinde uzun yazılarımızı küçük parçalara ayırabiliyorduk. Şimdi önce explode() fonksiyonunun çalışmasını ve sonucuna bakalım sonra JavaScript ile bunu nasıl yapıyoruz onu anlatalım:

<pre class="lang:php decode:1 " >$uzun=&amp;quot;TR Kodlama son zamanların en pop&uuml;ler i&ccedil;erik sitelerinden biri haline geldi&amp;quot;;
$parcala=explode(&amp;quot;&amp;quot;, $uzun);</pre>

Bu kod çalıştırıldığı anda aşağıdaki dizi otomatik olarak oluşturulur ve $parcala değişkenine ait olur:

<pre class="lang:php decode:1 " >$uzun[0]=&amp;quot;TR&amp;quot;;
$uzun[1]=&amp;quot;Kodlama&amp;quot;;
$uzun[2]=&amp;quot;son&amp;quot;;
$uzun[3]=&amp;quot;zamanların&amp;quot;;
$uzun[4]=&amp;quot;en&amp;quot;;
$uzun[5]=&amp;quot;pop&uuml;ler&amp;quot;;
$uzun[6]=&amp;quot;i&ccedil;erik&amp;quot;;
$uzun[7]=&amp;quot;sitelerinden&amp;quot;;
$uzun[8]=&amp;quot;biri&amp;quot;;
$uzun[9]=&amp;quot;haline&amp;quot;;
$uzun[10]=&amp;quot;geldi&amp;quot;;</pre>

PHP'de çalışma mantığı bu şekildedir. Peki bunu JavaScript'te nasıl yapacağız? PHP'de explode() fonksiyonu varsa JavaScript'te de <strong>split()</strong> fonksiyonu var. Söz dizimi biraz farklı sadece o kadar.

<pre class="lang:js decode:1 " >var uzun=&amp;quot;TR Kodlama son zamanların en pop&uuml;ler i&ccedil;erik sitelerinden biri haline geldi&amp;quot;;
var parcala=uzun.split(&amp;quot;&amp;quot;);</pre>

Yine JavaScript'de parcala[0], parcala[1], ... şeklinde verilere ulaşılabilir.
Umarım faydalı olmuştur ve işinize yarar.. Kolay gelsin