---
ID: 348
post_title: PHP 5.4 ve Dizilerdeki Yenilik
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-5-4-ve-dizilerdeki-yenilik-348.html
published: true
post_date: 2012-03-16 12:59:59
---
Merhaba arkadaşlar,

Bu yazıda PHP 5.4 ile gelen ve dizilerde devir niteliği taşıyan -şaka yapıyorum- bir özelliği anlatıyorum. Artık explode ile bir dizi elde edip onu değişkene atayıp değişken[1] şeklinde kullanma olayı tarihe geçiyor.

Yeni PHP 5.4 ile direk explode ile 2. indisi çekebilir düzeye geliyoruz. Örneklerle gösterelim. PHP 5.4'den önce:

<pre class="lang:php decode:1 " >$yazi = &amp;quot;Merhaba bu yazı yeni &ccedil;ıktı&amp;quot;;
// İlk kelimeyi almak istiyoruz
$bol = explode(&amp;quot; &amp;quot;, $yazi) ;
// B&uuml;t&uuml;n boşlukları b&ouml;ld&uuml;k ve her kelimeyi diziye aktadık.
echo $bol[0] ; // Merhaba'yı yazar sadece</pre>

Şimdi ilk kelimeyi PHP 5.4 ve sonrasında nasıl alıyoruz ona bakalım hemen:

<pre class="lang:php decode:1 " >$yazi = &amp;quot;Merhaba bu yazı yeni &ccedil;ıktı&amp;quot;;
echo explode(&amp;quot; &amp;quot;, $yazi)[0]; // Merhaba'yı yazar buda</pre>

Gerçekten çok iyi değil mi? Artık değişkenin n. indisini çekmeye çalışırken geçici bir değişken ihtiyacı duymayacaksınız. Bu değişken sayınızın ve kod miktarınızın azalması demek ki oldukça iyi bir şey bence.

Bu kullanım şeklini fonksiyonlarda da yapabilirsiniz:

<pre class="lang:php decode:1 " >function return_array()
{
  // Burada işlemlerinizi yapıyorsunuz ve return değeri array oluyor..
  return array(&amp;quot;Merhaba&amp;quot;,&amp;quot;TR&amp;quot;,&amp;quot;Kodlama&amp;quot;);
}
// Şimdi &amp;quot;Kodlama&amp;quot; kelimesini &ccedil;ekelim
echo return_array()[2]; // Kodlama</pre>

PHP 5.4 ile gelen bütün özellikleri bir makale ile anlatacağım çok yakında.

Umarım faydalı olur, kolay gelsin