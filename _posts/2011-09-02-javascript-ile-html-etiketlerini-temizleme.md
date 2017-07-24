---
ID: 236
post_title: >
  JavaScript ile HTML Etiketlerini
  Temizleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/javascript-ile-html-etiketlerini-temizleme-236.html
published: true
post_date: 2011-09-02 00:42:48
---
Merhaba arkadaşlar,

Şu sıralar çok fazla proje ile ilgilendiğimden dolayı fazla makale ekleyemiyor. Sizlerden de makale ekleyen olmadığı için bu boşluklar yaşanabiliyor.

Bugün sizlere PHP'de strip_tags() fonksiyonu ile yaptığımız HTML etiketi temizle işlemini JavaScript'te nasıl yapabileceğimizi göstereceğim.. JavaScript bunun için hazır bir fonksiyon vermiyor. Biz regex kullanarak temizleyeceğiz. Hemen ilgili JavaScript fonksiyonunu paylaşıyorum:

<pre class="lang:js decode:1 " >function strip_tags(htmlKod){
    return htmlKod.replace(/(&amp;lt;([^&amp;gt;]+)&amp;gt;)/ig,&amp;quot;&amp;quot;);
}</pre>

Burada < ve > işaretlerini bulan, bu işaretler ve aralarındaki içerikleri temizleyen bir fonksiyon hazırlamış olduk. Bunun için (<([^>]+)>) regex'ini kullandık. Kullanımı ise şöyle:

<pre class="lang:js decode:1 " >var htmlVeri = &amp;quot;&amp;lt;a href='http://www.trkodlama.com'&amp;gt;trkodlama.com&amp;lt;/a&amp;gt;&amp;quot;;
alert(strip_tags(htmlVeri)); //Bu kod sadece trkodlama.com'u alert edecektir.</pre>

Umarım faydalı ve açıklayıcı ve basit olmuştur. Kolay gelsin,