---
ID: 203
post_title: cURL ile HTTP Durum Kodunu Alma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/curl-ile-http-durum-kodunu-alma-203.html
published: true
post_date: 2011-06-29 22:21:52
---
Merhaba arkadaşlar,

Bu makalemde sizlerebir web sayfasının HTTP durum kodunu nasıl alacağınızı anlatıyorum. Aslında bunun çok basit bir şekilde <strong>get_headers()</strong> fonksiyonu ile halledebilirsiniz. Fakat bazı sunuculara bu şekilde bağlanamazsınız. Mesela örnek vermek gerekirse trkodlama.com adresine get_headers() ile file_get_contents() ile bağlanamazsınız. cURL ile bile CURLOPT_USERAGENT tanımlaması yapmazsanız bağlanamazsınız. Bugün paylaşacağım fonksiyon ile her sitenin HTTP durum kodunu rahatlıkla alabileceksiniz. Fonksiyon aşağıdaki gibidir:

<pre class="lang:php decode:1 " >function http_durum_kodu($url=&amp;quot;http://www.trkodlama.com&amp;quot;){
    $agent   = &amp;quot;Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.7.12) Gecko/20050915 Firefox/1.0.7&amp;quot;;
    $curl = curl_init($url);
    curl_setopt($curl, CURLOPT_USERAGENT, $agent); // Mozilla gibi g&ouml;r&uuml;nd&uuml;k
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1); // Burayı 0 yaparsanız sitenin &ccedil;ıktısını da ekrana basar. Bunu istemeyiz..
    $cikti = curl_exec($curl);
    $kod = curl_getinfo($curl, CURLINFO_HTTP_CODE); // HTTP durum kodunu aldık
    return $kod;
}</pre>

Fonksiyonun kullanımı da şöyledir:

<pre class="lang:php decode:1 " >echo http_durum_kodu(&amp;quot;http://togl.me&amp;quot;); // Ekran &Ccedil;ıktısı &amp;quot;400&amp;quot; olacaktır..</pre>

Umarım faydalı olmuştur. Herkese kolay gelsin,