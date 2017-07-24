---
ID: 188
post_title: 'Sıralanmış Kayıtlarınızın Id&#8217;sini Alma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/siralanmis-kayitlarinizin-id-sini-alma-188.html
published: true
post_date: 2011-06-08 19:22:31
---
Merhaba arkadaşlar,
Bu mesajımda sıralanmış kayıtlarınızda jQuery ile işlem yaparken id'lerini nasıl alabileceğinizi anlatıyorum.. Şimdi şöyle bir tablonuz olsun:

<pre class="lang:html decode:1 " >&amp;lt;table&amp;gt;
&amp;lt;tr&amp;gt;
&amp;lt;td&amp;gt;&Uuml;ye 1&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;Kayıt tarihi 1&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;&amp;lt;a href=&amp;quot;sil.php?id=1&amp;quot;&amp;gt;Sil&amp;lt;/td&amp;gt;
&amp;lt;/tr&amp;gt;
&amp;lt;tr&amp;gt;
&amp;lt;td&amp;gt;&Uuml;ye 2&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;Kayıt tarihi 2&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;&amp;lt;a href=&amp;quot;sil.php?id=2&amp;quot;&amp;gt;Sil&amp;lt;/td&amp;gt;
&amp;lt;/tr&amp;gt;
&amp;lt;/table&amp;gt;</pre>

Şimdi bu tablomuzu sil.php linkine göndermeyelimde jQuery $.get() metodu ile yani Ajax kullanarak silelim.. Fakat burda problem uye id'sini nasıl alacağız? Aşağıdaki kodda bunu nasıl yapabileceğinizi anlatıyorum:

<pre class="lang:html decode:1 " >&amp;lt;script&amp;gt;
 $(document).ready(function(){
   $(&amp;quot;.uye-sil&amp;quot;).click(function(){
     var idIlk = $(this).attr(&amp;quot;id&amp;quot;); // tıkladığımız linkini id'sini alıyoruz
     var id = idIlk.replace(&amp;quot;uye-&amp;quot;, &amp;quot;&amp;quot;); // Burda id'yi aldık. &amp;quot;uye-n&amp;quot; şeklinde. Şimdi &amp;quot;uye-&amp;quot; kısmını siliyoruz ve id değişkenine atıyoruz.
     $.get(&amp;quot;islem.php, &amp;quot;id=&amp;quot;+id, function(data){
       // İşlemleri yapalım
     });
 });
 });
&amp;lt;/script&amp;gt;

&amp;lt;table&amp;gt;
&amp;lt;tr&amp;gt;
&amp;lt;td&amp;gt;&Uuml;ye 1&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;Kayıt tarihi 1&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;&amp;lt;a href=&amp;quot;#!sil/uye-1&amp;quot; id=&amp;quot;uye-1&amp;quot; class=&amp;quot;uye-sil&amp;quot;&amp;gt;Sil&amp;lt;/td&amp;gt;
&amp;lt;/tr&amp;gt;
&amp;lt;tr&amp;gt;
&amp;lt;td&amp;gt;&Uuml;ye 2&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;Kayıt tarihi 2&amp;lt;/td&amp;gt;&amp;lt;td&amp;gt;&amp;lt;a&nbsp;href=&amp;quot;#!sil/uye-2&amp;quot; id=&amp;quot;uye-2&amp;quot; class=&amp;quot;uye-sil&amp;quot;&amp;gt;Sil&amp;lt;/td&amp;gt;
&amp;lt;/tr&amp;gt;
&amp;lt;/table&amp;gt;</pre>

Umarım anlatabilmişimdir. Sorularınızı yorum şeklinde veya forumdan sorabilirsiniz.
Kolay gelsin,