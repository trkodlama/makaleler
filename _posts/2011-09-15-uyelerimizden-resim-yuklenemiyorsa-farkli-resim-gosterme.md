---
ID: 259
post_title: >
  Resim Yüklenemiyorsa Farklı Resim
  Gösterme
author: damatmedya
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/jquery-web-tasarim-2/uyelerimizden-resim-yuklenemiyorsa-farkli-resim-gosterme-259.html
published: true
post_date: 2011-09-15 01:50:59
---
Merhaba Sevgili TR Kodlama Üyeleri,

Bu makale ile web sayfalarınızda bulunamayan veya ulaşılamayan resimlerin yerine jQuery ile nasıl farklı resimler koyabileceğinizi gösteriyorum. Örneğin a.jpg dosyası çağırılıyor fakat bulunamıyor bu resim yerine bulunamadi.jpg dosyasını gösteriyoruz. İlgili kod aşağıdaki gibidir:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;script type="text/javascript" src="http://code.jquery.com/jquery-1.6.4.js"&gt;&lt;/script&gt;
&lt;script type="text/javascript"&gt;
$(document).ready(function() {
 $('img').error(function(){
 $(this).attr('src', 'bulunamadi.jpg');
 });
});
&lt;/script&gt;</pre>
Bu kadar basit bir işlemdir arkadaşlar, kolay gelsin,