---
ID: 200
post_title: 'SEOmoz API&#8217;sini Kullanarak Bilgi Çeken Fonksiyon'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/seomoz-apisini-kullanarak-bilgi-ceken-fonksiyon-200.html
published: true
post_date: 2011-06-23 21:26:31
---
Merhaba arkadaşlar,
Bugünkü makalemde bir fonksiyon paylaşıyorum. Fonksiyonu hazırlamam bugün üç saatimi aldı ne yazık ki. SEOmoz'un wiki'sinde yeterli dökümanı bulamadığım için bu üç saatimin çoğu araştırmakla geçti.. Şimdi SEOmoz'dan veri çekmek için hazırladığım bu fonksiyonu paylaşıyorum:

<pre class="lang:php decode:1 " >&amp;lt;?php
/**
 * seomoz()
 * @author oralunal
 *
 * @param mixed $url = İncelenmesini istediğiniz sitenin URL'si
 * @param mixed $accessID = Bunu http://togl.me/c adresinden temin ediyorsunuz
 * @param mixed $secretKey = Bunu da aynı adresten temin ediyorsunuz
 * @return
 */
function seomoz($url, $accessID, $secretKey){
 $Expires = mktime() + 50; // Son kullanma tarihini ayarlayalım. Min. 50 isterseniz arttırabilirsiniz

 // Burada Signature elde etmek i&ccedil;in işlemler yapıyoruz
 $imzaya = $accessID.&amp;quot;n&amp;quot;.$Expires;
 $binaryImza = hash_hmac('sha1', $imzaya, $secretKey, true);
 $imza = urlencode(base64_encode($binaryImza));

 // Bu da veriyi &ccedil;ekeceğimiz URL
 $api_url = &amp;quot;http://lsapi.seomoz.com/linkscape/url-metrics/&amp;quot;.$url.&amp;quot;?AccessID=&amp;quot;.$accessID.&amp;quot;&amp;amp;Expires=&amp;quot;.$Expires.&amp;quot;&amp;amp;Signature=&amp;quot;.$imza;
 $sonuc = @file_get_contents($api_url); // İ&ccedil;eriği alalım
 // Eğer boş d&ouml;nerse veya hata alırsak başa d&ouml;nelim
 while($sonuc == &amp;quot;NULL&amp;quot; || !$sonuc) seomoz($url, $accessID, $secretKey);
 // json_decode ile ile gelen veriyi dizilere atalım
 $sonuc = json_decode($sonuc, true);
 return $sonuc;
}
?&amp;gt;</pre>

Gözünüzü fazla korkutmasın arkadaşlar açıklama yarısından fazlası. Fonksiyon tamamı dokuz satırdır sadece. Şimdi bir de kullanımını gösterelim:

<pre class="lang:php decode:1 " >$json = seomoz(&amp;quot;www.trkodlama.com/&amp;quot;,&amp;quot;member-xxxxxxx&amp;quot;, &amp;quot;xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&amp;quot;);
echo &amp;quot;&amp;lt;pre&amp;gt;&amp;quot;;
var_dump($json);
echo &amp;quot;&amp;lt;/pre&amp;gt;&amp;quot;;</pre>

Bu şekilde çalıştırdığımızda ekran çıktısı aşağıdaki gibi olacaktır:

[sourcecode]array(13) {
  [&quot;fmrp&quot;]=&gt;
  float(3.0741889752691)
  [&quot;fmrr&quot;]=&gt;
  float(6.8230103124604E-10)
  [&quot;pda&quot;]=&gt;
  float(20.624589977163)
  [&quot;ueid&quot;]=&gt;
  int(30)
  [&quot;ufq&quot;]=&gt;
  string(18) &quot;www.trkodlama.com/&quot;
  [&quot;uid&quot;]=&gt;
  int(421)
  [&quot;umrp&quot;]=&gt;
  float(4.4399377088343)
  [&quot;umrr&quot;]=&gt;
  float(3.9712982973246E-10)
  [&quot;upa&quot;]=&gt;
  float(27.094229777475)
  [&quot;upl&quot;]=&gt;
  string(14) &quot;trkodlama.com/&quot;
  [&quot;us&quot;]=&gt;
  int(200)
  [&quot;ut&quot;]=&gt;
  string(43) &quot;TR Kodlama - GÃ¼ncel Programlama Makaleleri&quot;
  [&quot;uu&quot;]=&gt;
  string(18) &quot;www.trkodlama.com/&quot;
}[/sourcecode]

Farkettiğiniz gibi başlık Türkçe karakter problemli. Bunun sebebi json_decode() fonksiyonunun ISO-8859-1 ile çalışmasıdır. Bunu da şu şekilde çözümleyebiliriz:

<pre class="lang:php decode:1 " >// Verimizi &ccedil;ekelim
$json = seomoz(&amp;quot;www.trkodlama.com/&amp;quot;,&amp;quot;member-xxxxxxx&amp;quot;, &amp;quot;xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&amp;quot;);

// Şimdi başlığımızı &ccedil;ekelim
$baslik_bozuk = $json[&amp;quot;ut&amp;quot;]; // Ekran &ccedil;ıktısı: TR Kodlama - G&Atilde;&frac14;ncel Programlama Makaleleri
$baslik_okay  = iconv(&amp;quot;UTF-8&amp;quot;, &amp;quot;ISO-8859-9&amp;quot;, $baslik_bozuk); // Ekran &ccedil;ıktısı: TR Kodlama - G&uuml;ncel Programlama Makaleleri</pre>

Umarım açıklayıcı olmuştur arkadaşlar, işinize yaraması dileğiyle, kolay gelsin..