---
ID: 714
post_title: 'PHP Ders 2: PHP Sözdizimi Kuralları'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ders-2-php-sozdizimi-kurallari-714.html
published: true
post_date: 2012-06-20 00:59:53
---
PHP sunucuda yorumlanır ve tarayıcıya HTML çıktısı gönderir.

<hr />

<h3>Basit PHP Sözdizimi Kuralları</h3>
Bir PHP kodu her zaman &lt;?php ile başlar ve ?&gt; ile biter. PHP kodları bir dökümanda her yerde bulunabilir.

Bazı sunucular kısa steno destekler ve kodlamanıza başlarken &lt;?php yerine &lt;? ile başlamanıza izin verir.

Fakat maksimum uyumluluk için, standart formunu(&lt;?php) kullanmanızı tavsiye ederiz.

<pre class="lang:php decode:1 " >&amp;lt;?php
?&amp;gt;</pre>

Bir PHP dosyası normalde HTML dosyasıymış gibi HTML taglarını da içerir PHP kodlarının yanında.

Aşağıda tarayıcıa "Merhaba Dünya" yazısını gönderen bir PHP kodunu görüyoruz:

<pre class="lang:php decode:1 " >&amp;lt;html&amp;gt;
&amp;lt;body&amp;gt;

&amp;lt;?php
echo &nbsp;&amp;quot;Merhaba D&uuml;nya!&amp;quot;;
?&amp;gt;

&amp;lt;/body&amp;gt;
&amp;lt;/html&amp;gt;</pre>

PHP'de her kod satırı noktalı virgül ile sona ermelidir. Noktalı virgül PHP'de bir işlemin bittiğini diğer işleme hazır olunduğunu belirtir.

PHP'de yazının çıktısını almak için iki faklı komut kullanılabilir: echo ve print. Yukarıdaki örnekte biz "echo" komutunu kullanarak "Merhaba Dünya" yazısının çıktısını aldık.

<strong>Not:</strong> PHP dosyalarının çalıştırılacağı dosyanın uzantısının .php olmasına dikkat edin. .html uzantılı dosyalarda PHP kodları çalışmayacaktır.

<hr />

<h3>PHP'de Yorum Satırları</h3>
PHP'de yorum satırları eklemek için iki yöntem vardır. Tek satırlık yorumlar için // işaretlerini kullanırız satır başında. Fakat uzun yorumlar için /*....*/ işaretlerini kullanırız. /* ile */ arasına yazdığımız yazılar PHP tarafından dikkate alınmaz.

<pre class="lang:php decode:1 " >&amp;lt;html&amp;gt;
&amp;lt;body&amp;gt;

&amp;lt;?php

//Bu&nbsp;bir&nbsp;yorum&nbsp;satırıdır

/*
Bu&nbsp;uzun
satırlardan&nbsp;oluşan
bir&nbsp;yorum&nbsp;bloğudur.
*/

?&amp;gt;

&amp;lt;/body&amp;gt;
&amp;lt;/html&amp;gt;</pre>

<dl></dl>