---
ID: 31
post_title: Google Translate Çevirmesin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/web-tasarim/google-translate-cevirmesin-31.html
published: true
post_date: 2009-06-10 07:15:34
---
Google aramalarında sayfalarınızın yanında "Bu sayfanın çevirisini yap" yazısına tıklandığında sayfanızın çevrilmesini istemiyor musunuz? Yapmanız gereken tek şey çevrilmesini istemediğiniz sayfaların meta etiket bölümüne:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;meta name="google" value="notranslate"&gt;</pre>
yazmanız yeterli olacaktır.

Eğer sayfanızın çevrilmesini istiyorsanız ama sadece belirli kısımların çevrilmesini istemiyorsanız taglarınıza class="notranslate" parametresini eklemeniz gerekmektedir.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;p class="notranslate"&gt;çevirilmeyecek&lt;/p&gt;</pre>
Şeklinde yazdığınız taktirde o kısımlar çevrilmeyecektir.