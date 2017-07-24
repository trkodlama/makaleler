---
ID: 298
post_title: >
  JavaScript ile UNIX Zaman
  Damgası(timestamp)
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/javascript-ile-unix-zaman-damgasitimestamp-298.html
published: true
post_date: 2012-02-15 02:59:29
---
erhaba arkadaşlar,

JavaScript Date nesnesinin tarih ve zamanlarla çalışmak için fonksiyonları vardır. <strong>getTime()</strong>fonksiyonu ile zamanı milisaniye cinsinden elde edebiliyoruz. Bu makale ile bu elde ettiğimiz değeri nasıl UNIX zaman damgasına(timestamp) çevirebileceğimizi göstereceğim.

Anlık tarih ve zamanı UNİX zaman damgasına aşağıdaki gibi çevirebiliriz:

<pre class="lang:js decode:1 " >var zd = Math.round((new Date()).getTime() / 1000);</pre>

Şimdi açıklayalım. (new Data()).getTime() ile zamanı UNIX zaman damgasına benzer ama mili saniye cinsinden bir değer alıyoruz. Daha sonra bunu 1000 ile bölerek normal saniyeyi elde ediyoruz. Math.round() ile de bölümden sonra elde ettiğimiz sayıyı yuvarlıyoruz. Artık "zd" değişkeni bir UNIX zaman damgası değeri içeriyor.

Umarım işinize yarar,
Kolay gelsin