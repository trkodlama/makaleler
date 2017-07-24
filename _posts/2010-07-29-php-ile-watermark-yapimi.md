---
ID: 68
post_title: PHP ile Watermark Yapımı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-watermark-yapimi-68.html
published: true
post_date: 2010-07-29 07:58:22
---
Merhaba arkadaşlar,
Bugünkü makalemde PHP ve HTACCESS yardımı ile web sitenizdeki resimlerinize nasıl watermark yani resimlerin üzerine kendi logonuzu nasıl ekleyebileceğinizden bahsediyorum.
Bunları kendiniz tedarik edin. Yani watermark.php ve .htaccess isimli iki dosya oluşturun. Daha sonra arkaplanı transparan ve opacity'si %60-%70 civarında olan bir PNG logo oluşturun kendinize. En sonra olarak da elinizdeki JPG resimlerden birini alın. Bunların hepsini bir klasöre atın.
Şimdi gelelim dosyalarımızın içeriklerine..
<strong>watermark.php:</strong>
[sourcecode lang="php"]&lt;?php
    $dizin = $_SERVER['DOCUMENT_ROOT'].$_SERVER['REQUEST_URI'];

    // İstenilen resmi alalım
    $resim = imagecreatefromstring(file_get_contents($dizin));

    $w = imagesx($resim);
    $h = imagesy($resim);

    // Watermark'ı yükleyelim.. Logo.png'yi değiştirin...
    $watermark = imagecreatefrompng('logo.png');
    $ww = imagesx($watermark);
    $wh = imagesy($watermark);

    // Logoyu resimle birleştiriyoruz
    imagecopy($resim, $watermark, $w-$ww, $h-$wh, 0, 0, $ww, $wh);

    // Resmi basalım...
    header('Content-type: image/jpeg');

    // Şu anda JPG kalitesi %75'dir. Bu varsayılan ayardır. Bunu %100 yapmak için şunu kullanın imagejpeg($resim,null,100);
    imagejpeg($resim);
    exit();
?&gt;[/sourcecode]
<strong>.htaccess:</strong>
[sourcecode lang="php"]RewriteEngine On
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule .(gif|jpeg|jpg|png)$ watermark.php [QSA,NC][/sourcecode]
Bu dosyalarınızın bulunduğu klasördeki bütün resimlerde artık logo.png diye belirttiğiniz dosya bulunacaktır.
<strong>Ekstra Özellikler:</strong>
Sistemde varsayılan olarak JPG Quality yani JPG kalitesi %75'dir. Bunu arttırmak için
[sourcecode lang="php"]imagejpeg($resim);[/sourcecode]
satırını
[sourcecode lang="php"]imagejpeg($resim, null, %100);[/sourcecode]
şeklinde değiştirin. %100 kısmını kendinize göre düzenleyin.
Eğer watermark logonun üzerine eklediğiniz resmi ortalamasını istiyorsanız aşağıdaki satırı
[sourcecode lang="php"]imagecopy($resim, $watermark, $w-$ww, $h-$wh, 0, 0, $ww, $wh);[/sourcecode]
şu satırla değiştirmelisiniz:
[sourcecode lang="php"]imagecopy($resim, $watermark, (($w/2)-($ww/2)), (($h/2)-($wh/2)), 0, 0, $ww, $wh);[/sourcecode]
Umarım faydalı olur.

Kolay gelsin,