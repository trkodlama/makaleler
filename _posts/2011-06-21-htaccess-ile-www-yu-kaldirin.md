---
ID: 197
post_title: '.htaccess ile WWW&#8217;yu Kaldırın'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htaccess-ile-www-yu-kaldirin-197.html
published: true
post_date: 2011-06-21 21:20:36
---
Merhaba Arkadaşlar,
Bugün sizlere URL'lerinizden "www" yani "world wide web" ibaresini nasıl kaldırabileceğinizi anlatıyorum.

Adreslerinizden "www" ibaresini kaldırmanızın faydaları:
<ul>
	<li>Daha kısa linkler</li>
	<li>Google tarafından kopya içerik gibi görünmenizi engeller</li>
	<li>Sayfalarınızda çok fazla link varsa daha az trafik</li>
</ul>
.htaccess dosyası aracılığıyla rahatlıkla WWW ibaresini kaldırabiliyorsunuz. Yani web sayfanıza http://www.trkodlama.com şeklinde erişen biri otomatik olarak kendini http://trkodlama.com'da bulacaktır. Aynı şekilde tam tersi de mümkün. http://trkodlama.com şeklinde giren birisi kendini http://www.trkodlama.com adresinde bulacaktır. Kaldı ki TR Kodlama'da "www" ibaresi zorunlu görünmektedir.

Şimdi önce "www" ibaresini nasıl kaldıracağımızı gösterelim:

[sourcecode]RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} !^trkodlama.com$ [NC]
RewriteRule ^(.*)$ http://trkodlama.com/$1 [L,R=301][/sourcecode]

Şimdi tam tersi olan her linkimize "www" ibaresini ekleyecek .htaccess kodunu verelim:

[sourcecode]RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} !^www.trkodlama.com$ [NC]
RewriteRule ^(.*)$ http://www.trkodlama.com/$1 [L,R=301][/sourcecode]

Umarım işinize yarar, herkese kolay gelsin,