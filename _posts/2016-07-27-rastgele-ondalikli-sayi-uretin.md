---
ID: 5897
post_title: Rastgele Ondalıklı Sayı Üretin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/rastgele-ondalikli-sayi-uretin-5897.html
published: true
post_date: 2016-07-27 21:50:16
---
Merhaba arkadaşlar,

Bugün basit ve kullanışlı bir fonksiyonu sizlerle paylaşmak istiyorum. Bu fonksiyon belirlediğiniz aralıklarda rastgele ondalıklı sayı üretecek.

Neden ihtiyaç duyduğumu düşünecek olursa kredi kartı authorize işlemlerinde rastgele 1 ile 3 dolar arasında ücret çekmeye çalışırken üstüne düşünmem gerekti. Neyse bu kısmı biraz hikaye :)

İsmine PHP'nin rand fonksiyonuna benzesin ve havalı olsun diye randDouble dedim, buyrun fonksiyonum:

<pre class="lang:php decode:1 " >function randDouble($min,$max){
    $aralik = $max-$min;
    $ondalik = $min + $aralik * mt_rand(0, 32767)/32767;
    $ondalik = round($ondalik, 2);
    return ((float) $ondalik);
}

// Kullanımı
echo randDouble(1,3.99);</pre>

Bu fonksiyonu hazırlarken mt_rand fonksiyonunu gördüm. rand() ile mt_rand() fonksiyonlarının farkı üzerine bir yazı da yazabilirim. mt_rand() fonksiyonunu da öğrenmiş olduk.

Umarım faydalı olur, sevgiler,