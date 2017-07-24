---
ID: 78
post_title: 'Warning: Cannot modify header information'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/warning-cannot-modify-header-information-78.html
published: true
post_date: 2010-08-04 08:17:34
---
Merhaba arkadaşlar,

Aşağıdaki hatayı eminim birçoğumuz vakti zamanında yaşamıştır. Eğer sayfanızda ekrana bir çıktı verdikten sonra header fonksiyonunu kullanıyorsanız bu hatayı alırsınız.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
echo "İçerik";
header("Location: index.php)
?&gt;</pre>
Yukarıdaki örneği çalıştırdığınızda bu hatayı alacaksınız:
<blockquote><strong>Warning: Cannot modify header information - headers already sent by (output started at /dizin/isim/public_html/dosya.php:123) in /dizin/isim/public_html/sistem/oturumlar.php on line 456</strong></blockquote>
Bunun çözümü kısa ve basittir. Kullandığınız sayfanın en üstüne <code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ob_start();</code>  ve en altına da <code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ob_flush();</code>  ekleyin.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
ob_start();
echo "İçerik";
header("Location: index")
ob_flush();
?&gt;</pre>
Fakat benim yegane tavsiyem ekran çıktılarınızı header'lardan sonra kullanmanızdır. Yani formatınızı şu şekilde güncellemeniz yönünde olacaktır:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$icerik = "İçerik";
header("Location: index.php");
echo $icerik;
?&gt;</pre>
Anlaşılır oldu fakat anlaşılmayan yerleri yorum olarak sorunuz lütfen.

Kolay gelsin,