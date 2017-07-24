---
ID: 273
post_title: >
  PHP Projelerinizdeki Türkçe Karakter
  Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-projelerinizdeki-turkce-karakter-problemi-273.html
published: true
post_date: 2012-01-24 02:25:25
---
Merhaba arkadaşlar,

Uzun zamandır makale yazamıyordum. Bugün yeni makaleme başladım türkçe karakter probleminin çözümünü projeme eklemeyi unuttuğumdan dolayı bende türkçe karakter problemi yaşadım.. Şükür ki çözümü biliyordum. Sizlere bugün bu problemin çözümünü anlatıyorum..

Türkçe karakter çözümünün temelinde karakter setinizi UTF-8 olarak ayarlamak yatıyor..

Projelerinize bir kaç satırlık kodu eklemezseniz "ü,ı,ğ,ö,ç,ş" gibi harflerin yerine "�" gibi bir sembol çıkar. Çözümü çok basittir. Projelerinizde bir tane ayar dosyanız vardır ve bu dosyayı bütün dosylarınıza include edersiniz.. Bunu yapmıyorsanız da yapmanızı tavsiye ederim. Bu ayar dosyanızın en üstüne aşağıdaki kodu ekleyin:

<pre class="lang:php decode:1 " >header(&amp;quot;Content-type: text/html; charset=utf-8&amp;quot;);</pre>

Bundan sonra bir işlemimiz daha kaldı. Veritabanına bağlandığımızda girdileri UTF-8 olarak almamızı sağlayacak SQL kodlarını çalıştırmamız gerekiyor.

<pre class="lang:php decode:1 " >mysql_select_db(&amp;quot;db_adi&amp;quot;); // Veritabanımızı se&ccedil;tikten sonra aşağıdaki kodları ekliyoruz
mysql_query(&amp;quot;SET NAMES 'utf8' COLLATE 'utf8_turkish_ci'&amp;quot;);
mysql_query(&amp;quot;SET CHARACTER SET utf8&amp;quot;);
mysql_query(&amp;quot;SET COLLATION_CONNECTION = 'utf8_turkish_ci'&amp;quot;);</pre>
Bu işlemlerden sonra dosyalarınızı UTF-8 formatında kaydetmeyi unutmayın..

Kolay gelsin,