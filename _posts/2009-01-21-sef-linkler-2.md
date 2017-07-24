---
ID: 10
post_title: SEF Linkler
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/sef-linkler-2-10.html
published: true
post_date: 2009-01-21 06:18:48
---
İternette en çok duyduğum konu PHP'de linkleri nasıl SEF yani Search Engine Friendly  haline getirebiliriz. Bunu size PHP ile nasıl halledeceğinizden bahsetmek istiyorum. Hatta bahsetmiyorum direkt olarak kullanmanız gereken fonksiyonu sizlerle paylaşıyorum:
<pre class="prettyprint" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">function Slug($string)
    {
        $turkce=array("ş", "Ş", "ı", "ü", "Ü", "ö", "Ö", "ç", "Ç", "ş", "Ş", "ı", "ğ", "Ğ", "İ", "ö", "Ö", "Ç", "ç", "ü", "Ü");
        $duzgun=array("s", "s", "i", "u", "u", "o", "o", "c", "c", "s", "s", "i", "g", "g", "i", "o", "o", "c", "c", "u", "u");
        $string = str_replace($turkce, $duzgun, $string);
        return strtolower(trim(preg_replace('~[^0-9a-z]+~i', '-', html_entity_decode(preg_replace('~&amp;([a-z]{1,2})(?:acute|cedil|circ|grave|lig|orn|ring|slash|th|tilde|uml);~i', '$1', htmlentities($string, ENT_QUOTES, 'UTF-8')), ENT_QUOTES, 'UTF-8')), '-'));
}</pre>
Yukarıdaki fonksiyondan nasıl faydalanabilirsiniz? Örneğin bir haber siteniz var ve linkinizin domain.com/haber-adi-12.html olmasını istiyorsunuz. Veritabanında seo-link diye bölüm oluşturun. Veritabanına bilgiyi eklerken sef_link("Haber Adi") şeklindeki değişkenide seo-link sütununa yazın. Bu sayede veritabanından da çekerken rahatlıkla çekmiş olursunuz. Farklı farklı yöntemlerde kullanabilirsiniz. İlla ki veritabanına yazmanız şart değil.

Kolay Gelsin,
