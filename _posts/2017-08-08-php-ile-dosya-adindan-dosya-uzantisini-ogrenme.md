---
ID: 9949
post_title: >
  PHP ile Dosya Adından Dosya
  Uzantısını Öğrenme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ipuclari/php-ile-dosya-adindan-dosya-uzantisini-ogrenme-9949.html
published: true
post_date: 2017-08-08 09:54:06
---
Oldukça kısa bir giriş yapacağım. Çünkü üzerine düşünülecek pek fazla bir şey yok. Aslında var. Şöyle ki eğer <code>pathinfo()</code> fonksiyonunu bilmiyorsanız bir dosyanın uzantısını, dosya adından öğrenmek azıcık vaktinizi alabilir. Nasıl mı?

Öncelikle <code>.</code> işareti ile dosya adını <code>explode()</code> ettiniz ve elde ettiğiniz dizinin <code>1</code> id'li elemanını çağırdınız. Sonra bir baktınız dosya adında birden fazla <code>.</code> var. O zaman <code>count()</code> fonksiyonu işin içine girdi. Saydınız, en sonuncu dizi elemanını çağırdınız falan filan... Çoook uzun iş.

Ben PHP programlamaya ilk başladığım da böyle yapmıştım. Hazır bir fonksiyon olduğunu bilmiyordum. Kaldı ki <a href="https://www.trkodlama.com/makaleler/dizideki-ifadeleri-for-dongusu-ile-toplama-58.html">dizi elemanlarını toplarken</a> bile bir dünya işe kalkışıyormuşum. Bunun hakkında yazı bile yazmışım :)

Neyse lafı fazla uzattık. <code>pathinfo()</code> fonksiyonu ile bir dosyanın ismini, uzantısını, dizinini ve uzantısı ile beraber tam adını öğrenebiliyoruz. Detaylı bilgi için <a href="http://php.net/manual/tr/function.pathinfo.php">pathinfo()</a> tıklayınız.

Hemen basit bir örnekle gösterelim:
<pre class="line-numbers"><code class="language-php">&lt;?php
$tam_dosya_adresi = pathinfo('/home/trkodlama/htdocs/trkodlama.php');

echo $tam_dosya_adresi['dirname'], "\n";
echo $tam_dosya_adresi['basename'], "\n";
echo $tam_dosya_adresi['extension'], "\n";
echo $tam_dosya_adresi['filename'], "\n"; // PHP 5.2.0'dan beri.
?&gt;</code></pre>
Bu kodun çıktısı aşağıdaki gibi olacaktır:
<pre class="line-numbers"><code class="language-markup">/home/trkodlama/htdocs
trkodlama.php
php
trkodlama</code></pre>

Yani gördüğünüz gibi çokda zor değil, hemen açın lokalinizde bir deneme yapın. Bakalım sizde aynı sonucu elde edecek misiniz?