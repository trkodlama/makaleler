---
ID: 147
post_title: Özel Karakterleri Temizleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/web-gelistirme/ozel-karakterleri-temizleme-147.html
published: true
post_date: 2011-04-09 17:50:36
---
Merhaba arkadaşlar,

Bu yazımda sizlere bir değişkeninizdeki değerden özel karakterleri nasıl temizleyebileceğinizi anlatıyorum. Bu işlemi bir REGEX kullanarak çok basit bir şekilde gerçekleştireceğiz. Hiç lafı uzatmayalım hemen bu regex yapısını paylaşalım.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$degisken="!'^+%&amp;/(A)=?_";
echo preg_replace('/[^a-zA-Z0-9]/s', '', $degisken);  
// Bu kodun ekran çıktısı sadece A olacaktır.  
  
// Birde if kontrolüne sokma yöntemini gösterelim  
if(preg_replace('/[^a-zA-Z0-9]/s', '', $degisken)=="") {
    echo "Tamamen özel karakterlerden oluşuyormuş..";
}</pre>
Umarım işinize yarar, kolay gelsin