---
ID: 5786
post_title: >
  Boşta Kalan Gerçek Ram Değerimi
  Nasıl Öğrenirim?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/bosta-kalan-gercek-ram-degerimi-nasil-ogrenirim-5786.html
published: true
post_date: 2015-05-25 23:41:08
---
Merhaba arkadaşlar,

Hızlı bir ipucu paylaşıyorum. Şu sıralar sunucu optimizasyonuna kafa yoruyorum biraz. Linux sunucunuzda boşta kalan gerçek ram değerini aşağıdaki komut ile öğrenebilirsiniz:

<pre class="lang:bash decode:1 " >free -m</pre>

Bu komutu çalıştırdığınızda şöyle bir çıktı elde edersiniz.

<a href="http://www.trkodlama.com/wp-content/uploads/2015/05/bostaki-ram-miktari.png"><img class="aligncenter size-full wp-image-5787" src="http://www.trkodlama.com/wp-content/uploads/2015/05/bostaki-ram-miktari.png" alt="bostaki-ram-miktari" width="594" height="85" /></a>

<strong>-/+ buffers/cache</strong> satırı ve <strong>free</strong> sütunundaki değer sizin gerçek boşta kalan bellek değeriniz.