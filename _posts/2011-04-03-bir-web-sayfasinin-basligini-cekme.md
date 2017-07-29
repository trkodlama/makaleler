---
ID: 132
post_title: >
  Bir Web Sayfasının Başlığını
  Çekme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/bir-web-sayfasinin-basligini-cekme-132.html
published: true
post_date: 2011-04-03 17:26:24
---
Merhaba arkadaşlar,

Bu makale ile bir web adresinin <code>&lt;title&gt;...&lt;/title&gt;</code> etiketleri arasındaki kısmı nasıl çekeceğimizi göreceğiz. Projelerinizde belki kullanma isteği duyarsınız. Üyelerinize girilen sayfanın başlığını göstermek istersiniz belki..

Hemen başlayalım.. Öncelikle bir fonksiyon oluşturalım ve bu fonksiyon bizim başlık çeken fonksiyonumuz olsun..

<pre class="line-numbers"><code class="language-php">&lt;?php  
  
/** 
 * @author oralunal 
 * @copyright 2011 
 */  
  
/** 
 * baslikCek() 
 */  
function baslikCek($a,$b,$c){ 
    $y = explode($b,$a); 
    $x = explode($c,$y[1]); 
    
    return $x[0]; 
}  
?&gt;</code></pre>

Yukarıdaki fonksiyonumuz $url ile yollanan web sayfasını açıyor. İçerisinde title taglarını arıyor. Eğer title tagları mevcutsa arasındaki değeri döndürüyor. Eğer bağlandığı web sayfasında title tagı mevcut değilse false dönüyor. Kullanımı da aşağıdaki gibidir:

<pre class="line-numbers"><code class="language-php">&lt;?php  
  
/** 
 * @author oralunal 
 * @copyright 2011 
 */  
  
$url    = 'http://www.trkodlama.com';  
$baslik = baslikCek(file_get_contents($url), "&lt;title&gt;", "&lt;/title&gt;");

echo "&lt;a title=\"$baslik\" href=\"$url\" target=\"_blank\"&gt;$baslik&lt;/a&gt;";
  
?&gt;</code></pre>

Yukarıdaki scriptin ekran çıktısı aşağıdaki gibi olacaktır:
TR Kodlama - Güncel Programlama Makaleleri

Kolay gelsin,