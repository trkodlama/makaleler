---
ID: 1278
post_title: 'Arayüz Kodlamalarında Sayflarınızda Kullanmanız Gereken Örnek &#8220;reset.css&#8221; Dosyası'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/arayuz-kodlamalarinda-sayflarinizda-kullanmaniz-gereken-ornek-reset-css-dosyasi-1278.html
published: true
post_date: 2012-10-08 14:04:45
---
Merhaba arkadaşlar,

Arayüz kodlamalarınızı yaparken öncelikle farklı tarayıcılardaki varsayılan stilleri sıfırlamak için <strong>reset.css</strong> isminde-farklı isimlerde olabilir, ben böyle kullanıyorum- dosya ekleriz HTML'e. Daha sonra CSS kodlamamıza devam ederiz. Örnek <strong>reset.css </strong>dosyamız aşağıdaki gibidir:

<pre class="lang:css decode:1 " >/* http://www.trkodlama.com
   v1.0 | 08102012
   Lisans: yok(herkes kullanabilir)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* Eski tarayıcılar HTML5 etiketleri */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}</pre>

Umarım işinize yarar, kolay gelsin,