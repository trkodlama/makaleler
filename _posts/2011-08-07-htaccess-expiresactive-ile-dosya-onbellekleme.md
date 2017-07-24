---
ID: 226
post_title: >
  .htaccess ExpiresActive ile Dosya
  Önbellekleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htaccess-expiresactive-ile-dosya-onbellekleme-226.html
published: true
post_date: 2011-08-07 00:16:24
---
Merhaba arkadaşlar,

Bugün sizlere çok faydalı bir htaccess kodu paylaşıyorum. Bu kod sayesinde tarayıcılara sitenizde bulunan JPEG, GIF, BMP, PNG, CSS ve JS dosyalarını önbelleğe almaları gerektiğini bildirin. Bu JavaScript kodu tarayıcıya bu resimler için Expires header'ını gönderir. Son kullanma vaktini saniye cinsinden belirtiyorsunuz. Tabii ki farklı şekilleri de var fakat benim paylaşacağım kod saniye cinsinden.

Lafı uzatmadan kodu paylaşıyorum:

[sourcecode]ExpiresActive On
ExpiresByType image/gif A604800
ExpiresByType image/jpg A604800
ExpiresByType image/jpeg A604800
ExpiresByType image/png A604800
ExpiresByType image/bmp A604800
ExpiresByType text/css A604800
ExpiresByType text/javascript A604800
ExpiresByType application/javascript A604800
ExpiresByType application/x-javascript A604800[/sourcecode]

Bu kodu .htaccess dosyanızın içine ekleyin. Burda ExpiresActive On ile ilgili modülü açtık ve ExpiresByType ile dosya türlerini belirtip son kullanma vaktini belirledik. Siz burda <strong>AXXXXX </strong>kısmında XXXXX kısmını değiştirebilirsiniz kendinize göre. Başına <strong>A</strong> harfinin olmasına dikkat edin.

Yukarıdaki kod gif, jpg, jpeg, css, png, bmp ve js uzantılı dosyalar için tarayıcıya Expires: Şimdiki Zaman + 604800 sn. başlığını gönderir. Tarayıcı bu başlık bilgisi ile dosyalarını önbelleğe alır ve sayfanız açılırken daha hızlı açılır.

Umarım faydalı olur,
Kolay gelsin,