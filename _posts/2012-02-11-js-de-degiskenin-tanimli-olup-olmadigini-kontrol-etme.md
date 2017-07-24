---
ID: 291
post_title: 'JS&#8217;de Değişkenin Tanımlı Olup Olmadığını Kontrol Etme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/js-de-degiskenin-tanimli-olup-olmadigini-kontrol-etme-291.html
published: true
post_date: 2012-02-11 02:49:41
---
Merhaba arkadaşlar,

Bu makalede basit bir kontrolü anlatacağım. Ben bilmiyordum ilk defa ihtiyacım oldu ve araştırdım oldukça basit bir yöntem. JavaScript'de bir değişkenin tanımlı olup olmadığını nasıl kontrol edeceğimizi göstereceğim(jQuery kullanarak).

Bir form alanınızın olduğunu düşünün. Bu form alanınızda radio seçimi yaptırıyorsunuz. Örnek radio'lar:

<pre class="lang:html decode:1 " >&amp;lt;input type=&amp;quot;radio&amp;quot; id=&amp;quot;radio&amp;quot; value=&amp;quot;deneme1&amp;quot; /&amp;gt; Deneme 1
&amp;lt;input type=&amp;quot;radio&amp;quot; id=&amp;quot;radio&amp;quot; value=&amp;quot;deneme2&amp;quot; /&amp;gt; Deneme 2
&amp;lt;input type=&amp;quot;radio&amp;quot; id=&amp;quot;radio&amp;quot; value=&amp;quot;deneme3&amp;quot; /&amp;gt; Deneme 3</pre>

Şimdi bunları nasıl kontrol edeceğimizi gösterelim. Diyelim ki gönder butonu bir fonksiyonu çalıştırıyor. Ve bu fonksiyonda veriler işleniyor, kontrol edilip ajax ile gönderiliyor vs. İlgili javascript fonksiyonun sadece bizi ilgilendiren kısmı aşağıdaki gibi olacaktır:

<pre class="lang:js decode:1 " >function formuGonder(){
  .
  .
  .
  var radio_degeri = $(&amp;quot;$radio&amp;quot;).val();
  // Yukarıdaki formdan herhangi bir radio değeri se&ccedil;ilmediği zaman radio_degeri &amp;quot;undefined&amp;quot; olarak gelecektir.
  //&amp;quot;undefined&amp;quot; olarak gelen yani tanımsız JavaScript değişkenleri if ile ş&ouml;yle kontrol ediyoruz
  if(radio_degeri==undefined){
    alert(&amp;quot;Radio inputlarından birini se&ccedil;melisiniz&amp;quot;);
  }
  .
  .
  .
}</pre>

Ben bu şekilde kontrolü yeni öğrendim. Belki benim gibi bilmeyen ender birkaç insan daha vardır diye paylaşayım dedim. Umarım işinize yarar,
Kolay gelsin,