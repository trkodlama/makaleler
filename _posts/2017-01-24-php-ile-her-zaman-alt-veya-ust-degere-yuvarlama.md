---
ID: 6384
post_title: >
  PHP ile Her Zaman Alt veya Üst Değere
  Yuvarlama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/php-ile-her-zaman-alt-veya-ust-degere-yuvarlama-6384.html
published: true
post_date: 2017-01-24 15:28:04
---
PHP'nin <code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">round()</code> fonksiyonunda 4 tane özellik belirtebiliyorsunuz. Bunlar <strong>PHP_ROUND_HALF_UP</strong>, <strong>PHP_ROUND_HALF_DOWN</strong>, <strong>PHP_ROUND_HALF_EVEN</strong>, <strong>PHP_ROUND_HALF_ODD</strong> dur. Bu özelliklerle buçuklu ifadeleri bir üste veya bir alta yuvarlayabildiğiniz gibi bir sonra ki tek veya çift rakama da yuvarlayabiliyorsunuz.

Fakat biz verilen sayının her zaman alt değere veya üst değere yuvarlanmasını istersek bunu sağlamıyor. Yani 1.444 sayısını 1.45 yuvarlamak isteseniz bunu tek başına round() fonksiyonunu kullanarak yuvarlayamazsınız. <strong>round()</strong> fonksiyonu bu sayıyı 1.44'e yuvarlayacaktır.

Size hazırladığım aşağıdaki fonksiyonu inceleyiniz. Detaylı açıklamalar kodlar içinde yapılmıştır:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * Sayıları tek yönde yuvarlama
 * Üste veya aşağı
 */
function round_tr($sayi, $nereye, $ondalik = 2){
    $o = (int) str_pad('1', $ondalik, '0');
    if($nereye == "up")
        return (ceil($sayi * $o) / $o);
    elseif($nereye == "down")
        return (floor($sayi * $o) / $o);
    else
        return "Üste mi yuvarlayacağız, alta mı?";
}

// Kullanımı
echo round_tr(1.4424, "up", 2);    // Çıktısı: 1.45
echo round_tr(1.4424, "down", 2);  // Çıktısı: 1.44
echo round_tr(1.4424, "down", 1);  // Çıktısı: 1.4
echo round_tr(1.4424, "up", 3);    // Çıktısı: 1.443


?&gt;</pre>
İşinize yaraması dileğiyle,