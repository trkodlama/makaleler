---
ID: 219
post_title: >
  TRK Doğrular jQuery Fonksiyonu ile Form
  Alanlarınızı Doğrulayın
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/trk-dogrular-jquery-fonksiyonu-ile-form-alanlarinizi-dogrulayin-219.html
published: true
post_date: 2011-07-23 00:04:18
---
Merhaba arkadaşlar,
TRK Doğrular adını verdiğimiz bir jQuery form doğrulama fonksiyonu hazırladık sizler için. Fonksiyonun kurulumu ve kullanımı çok basittir. Ama önce fonksiyonun özelliklerini açıklayalım:
<ol>
	<li>Kurulumu çok basittir. Kullanımı daha basittir.</li>
	<li>class="required" olarak belirtilen form alanlarını boş bırakarak formu göndermeye çalıştığınızda boş inputlar kırmızıya döner. Yani sınıfları olur. Bu alanlar doldurulmadan formu gönderilmez.</li>
	<li>Boş bırakılan alanların üstüne tıklandığında ve birşeyler yazılmaya başlandığında input eski haline döner. Yani warning tanımlaması kalkar.</li>
	<li>class kısmına ekstra sınıflar yazabilirsiniz. Örnek class="stilim diger_stilim required"</li>
</ol>
Fonksiyonun kurulumu için <strong>trk_dogrular.js</strong> dosyasını indirmeniz gerekmektedir.
<h3>Kurulumu</h3>
HTML sayfanızın ... tagları arasına jQuery kütüphanesi ile trk_dogrular kütüphanesini ekleyin:

<pre class="lang:html decode:1 " >&amp;lt;script type=&amp;quot;text/javascript&amp;quot; src=&amp;quot;http://code.jquery.com/jquery-latest.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt;
&amp;lt;script type=&amp;quot;text/javascript&amp;quot; src=&amp;quot;trk_dogrular.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt;</pre>

Bu iki satırın hemen altına:

<pre class="lang:js decode:1 " >&amp;lt;script type=&amp;quot;text/javascript&amp;quot;&amp;gt;
    $(document).ready(function(){
        $(&amp;quot;#ornek_form&amp;quot;).trkDogrular();
    });
&amp;lt;/script&amp;gt;</pre>

Satırlarını ekleyin. Daha sonra bir form oluşturun ve form id'sine "ornek_form" adını verin. Daha sonra eklediğiniz inputlara ekleyin. Bunu eklediğiniz inputlar doldurulması zorunlu alanlar olacaklardır.

<pre class="lang:html decode:1 " >&amp;lt;form id=&amp;quot;ornek_form&amp;quot; action=&amp;quot;&amp;quot;&amp;gt;Adınız &amp;lt;input class=&amp;quot;required&amp;quot; type=&amp;quot;text&amp;quot; /&amp;gt;
 Soyadınız &amp;lt;input class=&amp;quot;required&amp;quot; type=&amp;quot;text&amp;quot; /&amp;gt;
 Eposta &amp;lt;input class=&amp;quot;required&amp;quot; type=&amp;quot;text&amp;quot; /&amp;gt;
 &amp;lt;input type=&amp;quot;submit&amp;quot; value=&amp;quot;G&ouml;nder&amp;quot; /&amp;gt;&amp;lt;/form&amp;gt;
</pre>

Hatalı olan yani boş bırakılan input alanlarına .warning isminde bir class eklenmektedir. İsteğe bağlı olarak düzenleyebilirsiniz.

<pre class="lang:css decode:1 " >.warning{
     border: 1px solid red;
}</pre>

Bu fonksiyon ile ilgili yaşadığınız problemleri lütfen yorum olarak yazmayı ihmal etmeyin. Sizlerin geri dönüşleriyle bu fonksiyon geliştirilecektir.

<strong><a href="http://www.trkodlama.com/demo/trk_dogrular/index.htm" target="_blank">Demoyu incelemek için tıklayın</a>.</strong>
[wpdm_file id=1]