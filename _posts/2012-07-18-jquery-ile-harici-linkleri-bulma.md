---
ID: 1141
post_title: jQuery ile Harici Linkleri Bulma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-harici-linkleri-bulma-1141.html
published: true
post_date: 2012-07-18 01:34:50
---
Web sitenizden dışarı giden linkleri farklı bir stil ile göstermek isterseniz ne yapacaksınız?
<ul>
	<li>Bütün dışarı çıkan linklere tek tek bir stil belirleyeceksiniz</li>
	<li>Ya da bu makaleyi okuyarak kısa yoldan çözüme kavuşacaksınz.</li>
</ul>
Seçim sizin!

Bu makalede sayfadaki bütün harici linkleri yakalayan ve onlara birer <strong>class</strong> atayan jquery işlemini gösteriyorum.

Bunun için iki farklı yöntem uygulayacağız. İkisinden birini seçip uygulayabilirsiniz.
<h2>Yöntem 1</h2>
<pre class="lang:js decode:1 " > $('a').filter(function() {
return this.hostname &amp;amp;amp;&amp;amp;amp; this.hostname !== location.hostname;
 }).addClass(&amp;amp;quot;harici&amp;amp;quot;);</pre>
<h2>Yöntem 2</h2>
<pre class="lang:js decode:1 " >$('a').each(function() {
var duzenliIfade = new RegExp('/' + window.location.host + '/');
if (!duzenliIfade.test(this.href)) { // Harici Link Bulundu!
this.addClass(&amp;amp;quot;harici&amp;amp;quot;)
}
 });</pre>

Bu iki yöntem ile yaptığımız işlem aynı. Sayfadaki harici linkleri bulduk ve onları <strong>class='harici'</strong> şeklinde yeniden şekillendirdik. Bu yöntem ile kullanıcılarınızı da hangi linkin dışarıya gittiğini bilmelerini sağlayarak mutlu edebilirsiniz.

Umarım işinize yarar, kolay gelsin.