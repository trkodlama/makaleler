---
ID: 275
post_title: '&lt;alt:a&gt; Formatındaki XML&#8217;i PHP ile Okuma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/alt-a-formatindaki-xml-i-php-ile-okuma-275.html
published: true
post_date: 2012-01-25 02:29:44
---
Merhaba arkadaşlar,

Bugün forumlarda bir soruyla karşılaştım. Bunu ve çözümünü sizlerle paylaşmak istedim. Neyse, konuyu uzatmayalım. Şimdi daha önce

<pre class="lang:xml decode:1 " >&amp;lt;a&amp;gt;
 &nbsp;&amp;lt;strong&amp;gt;tr&amp;lt;/strong&amp;gt;
 &nbsp;kodlama
&amp;lt;/a&amp;gt;</pre>

Formatındaki XML'i nasıl PHP işleyeceğimizi http://www.trkodlama.com/php-ile-xml-dosya-dan-veri-cekme-310.html bu makalede anlatmıştım. Bu sefer mevcut XML yapımız biraz daha farklı... Aşağıdaki gibi bir XML(icerik.xml olsun) yapımız olduğunda PHP kodumuz nasıl olacak onu görelim:

<pre class="lang:xml decode:1 " >
   AAAAAAA
   1111111
   ornek1
   ornek2
</pre>

Burada kafamızı karıştıran nokta eleman-info etiketindeki "-" işareti ve ce:a ve ce:b etiketleri.. Bunları PHP SimpleXML ile aşağıdaki şekilde kolaylıkla işleyebiliriz:

<pre class="lang:php decode:1 " >&amp;lt;!--?php header(&amp;quot;Content-Type: text/html; charset=utf8&amp;quot;); // Karakter problemi i&ccedil;in gerekli $a=simplexml_load_file(&amp;quot;icerik.xml&amp;quot;); // i&ccedil;erik.xml dosyamızı &ccedil;ekelim // AAAAAAA kısmını &ccedil;eken kod: echo $xml---&amp;gt;{'eleman-info'}-&amp;gt;id;

// 1111111 kısmını &ccedil;eken kod:
echo $xml-&amp;gt;{'eleman-info'}-&amp;gt;aid;

// ornek1 kısmını &ccedil;eken kod:
echo $xml-&amp;gt;{'eleman-info'}-&amp;gt;children(&amp;quot;ce&amp;quot;,true)-&amp;gt;{'a'};

// ornek2 kısmını &ccedil;eken kod:
echo $xml-&amp;gt;{'eleman-info'}-&amp;gt;children(&amp;quot;ce&amp;quot;,true)-&amp;gt;{'b'};
?&amp;gt;</pre>

eleman-info altındaki ce:a ve ce:b'yi çekmek için SimpleXML'i yukarıda gördüğünüz gibi kullanıyoruz. Bu makaleyi yazmama vesile olan <strong>un.real</strong> ve <strong>grk3mm</strong> takma isimli arkadaşlara teşekkür ederim.

Kolay gelsin,