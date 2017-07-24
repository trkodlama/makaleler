---
ID: 63
post_title: Flash ve Z-Index Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/flash-ve-z-index-problemi-63.html
published: true
post_date: 2010-07-26 07:49:44
---
Bu problemi web sitesi olan bir çok kişi yaşamıştır. Özellikle sitesinde açılır menü kullanan kişiler hep menülerinin flash'ın altında kaldığından şikayet ederler. Bunun sebebi siz her ne kadar menünüzün z-index değerini en büyük yaptığınızı düşünseniz de flash dosyalarının z-index değeri sonsuza ayarlıdır. Bu nedenle de açılır menüleriniz flash'ın altında kalır.
[sourcecode lang="css"].acilirmenu{
  position: absolute;
  top: 0;
  left: 0;
  z-index: 6000;
}[/sourcecode]
Bu şekilde bile hazırlasanız menülerinizi yani z-index değerini 6000 bile yapsanız flash'ın arkasında kalmaya devam edecektir. Bunun için yapmanız gereken tek işlem flash parametrelerinden wmode'u transparent veya opaque yapmanızdır.
[sourcecode lang="html"]&lt;param name=&quot;wmode&quot; value=&quot;transparent&quot;&gt;[/sourcecode]
Veya
[sourcecode lang="html"]&lt;param name=&quot;wmode&quot; value=&quot;opaque&quot;&gt;[/sourcecode]
Günümüzde Flash  dosyalarının görüntülenmesi için en çok kullanılan kütüphane SWFObject'dir. Birde bunun için ne yapmanız gerektiğini gösterelim:
[sourcecode lang="js"]&lt;script&gt;
// Tabii ki bunları script tagları arasına yazıyoruz
var so = new SWFObject(&quot;images/news.swf&quot;, &quot;news&quot;, &quot;160&quot;, &quot;60&quot;, &quot;6&quot;, &quot;#000000&quot;);
// Bu satırla wmode için opaque değerini atamış olduk
so.addParam(&quot;wmode&quot;, &quot;opaque&quot;);
so.write(&quot;flashcontent&quot;);
&lt;/script&gt;[/sourcecode]
Daha sonra flash içeriğin görünmesini istediğiniz yere şunu yazıyorsunuz
[sourcecode lang="html"]&lt;div id=&quot;flashcontent&quot;&gt;&lt;/div&gt;[/sourcecode]
Kolay gelsin,