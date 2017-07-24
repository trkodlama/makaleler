---
ID: 1290
post_title: CSS Clearfix
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/css-clearfix-1290.html
published: true
post_date: 2012-10-15 18:41:51
---
Merhaba arkadaşlar,

Her CSS dosyanıza neredeyse hep eklediğiniz bir css bloğu paylaşıyorum sizinle. CSS Clearfix olarak adlandırılan bu kodcuğa ihtiyaç duymamızın sebebi ise sağa sola fırlatılmış(<strong>float</strong>) bloklar içinde bulundukları bloğun yüksekliğine etki etmezler. Bu sıkıntıyı gidermek için css clearfix adıyla aklımıza kazınmış olan sınıfı kullanırız. İşte o pratik CSS Kodu:

<pre class="lang:css decode:1 " >.clearfix:after {
	content: &amp;quot;.&amp;quot;;
	display: block;
	clear: both;
	visibility: hidden;
	line-height: 0;
	height: 0;
}
 
.clearfix {
	display: inline-block;
}
 
html[xmlns] .clearfix {
	display: block;
}
 
* html .clearfix {
	height: 1%;
}</pre>

Umarım işinize yarar, kolay gelsin,