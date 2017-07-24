---
ID: 144
post_title: >
  Hexadecimal Renk Kodunu RGB Formatına
  Çevirme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/hexadecimal-renk-kodunu-rgb-formatina-cevirme-144.html
published: true
post_date: 2011-04-06 17:48:33
---
Merhaba arkadaşlar,

Bildiğiniz HTML sayfalarımızda HTML renk kodları dediğimiz 16'lık sayma sistemine göre düzenlenmiş hexadecimal renk kodları kullanırız. Bu kodlar anlamsız rastgele harfler ve rakamlardan oluşturulmuş renk kodları değildir. Hepsi 16'lık sistemden 10'luk sisteme yani RGB(red, green, blue) formatına çevirilerek tarayıcılar tarafından işlenir. Şimdi bu çevirme işinin nasıl yapıldığını anlatalım.

Renk kodlarında kullanılan karakterler: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F. Burada harfler sayıların yerlerini tutarlar. A=10, B=11, C=12, D=13, E=14 ve F=15'dir.

#FFFFFF renk kodunda ilk iki FF kırmızılığı yani RGB'deki R'yi temsil eder. Ortadaki iki FF yeşilliği yani RGB'deki G'yi temsil eder ve sondaki FF'de maviliği temsil eder. RGB'deki B.

#ABCDEF renk kodunu RGB formatına çevirelim(işlemlerde harflerin yerine değerlerini yazdık):

R= (10*16)+11 = 171
G= (12*16)+13 = 205
B= (14*16)+15 = 239

Anlayacağınız üzerine ele aldığımız her ikilinin ilk değerini 16 ile çarpıyoruz elde ettiğimiz değeri ikinci değer ile topluyoruz. Şimdi daha da anlaşılması için #1F9E67 renk kodunu çevirelim:

R= (1*16)+15 = 31
G= (9*16)+14 = 158
B= (6*16)+7 = 103

Aşağıdaki PHP fonksiyonu da Hexadecimal renk kodunu RGB'ye çevirme işlemine yaramaktadır:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
function hexToRGB($hex){  
    // Önce bütün karakterleri parçalayalım  
    $her_harf = str_split($hex);  
    foreach($her_harf AS $key=&gt;$value){  
        if($value=="F" || $value=="f") $her_harf[$key]=15;  
        elseif($value=="E" || $value=="e") $her_harf[$key]=14;  
        elseif($value=="D" || $value=="d") $her_harf[$key]=13;  
        elseif($value=="C" || $value=="c") $her_harf[$key]=12;  
        elseif($value=="B" || $value=="b") $her_harf[$key]=11;  
        elseif($value=="A" || $value=="a") $her_harf[$key]=10;  
    }  
    $r = ($her_harf[0]*16)+$her_harf[1];  
    $g = ($her_harf[2]*16)+$her_harf[3];  
    $b = ($her_harf[4]*16)+$her_harf[5];
    return "RGB: R= {$r} G= {$g} B= {$b}";
}  
  
/** 
  * Kullanımı 
  */  
echo hexToRGB("FFFFFF");  
// Ekran çıktısı: RGB: R= 255 G= 255 B= 255</pre>
Umarım işinize yarar bu makale, kolay gelsin