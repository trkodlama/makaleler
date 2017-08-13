---
ID: 126
post_title: 'Fatal error: Cannot redeclare function Hatası'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/fatal-error-cannot-redeclare-function-hatasi-126.html
published: true
post_date: 2011-03-19 17:06:22
---
Merhaba arkadaşlar,

Sıkıcı bir günün ardından PHP programlamaya yeni başlayanların hep başına gelen bir hatadan bahsediyorum.
<blockquote><strong>Fatal error: Cannot redeclare function</strong></blockquote>
Bu hata ile bende zamanında çok karşılaşıyordum. Düzensiz bir template sistemim olurdu. Template dosyamın içinde bir fonksiyon oluştururdum. Fakat aynı fonksiyonu asıl işlemlerimi yaptığım sayfada da tanımlıyordum. Bu şekilde iki farklı yerde aynı adla iki fonksiyon tanımlayınca PHP'nin kafası karışıyor ve hata veriyor. Şimdi örnek bir fonksiyon yazalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
function foo($deger) {
 return $deger;
}
?&gt;</pre>
Bildiğiniz gibi programcı insan biraz tembel ve üşengeçtir. Bu nedenle bu fonksiyon var mı yok mu diye kontrole etmek yerine basit bir fonksiyon ise tekrar yazar template dosyasında. İşte bu noktada basit bir kontrolle bu işlemi hata almadan atlatabiliriz:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
if(!function_exists('foo')){
    function foo($deger) {
         return $deger;
    }
}
?&gt;</pre>
<a href="http://php.net/manual/en/function.function-exists.php" target="_blank">function_exists()</a> fonksiyonu böyle bir fonksiyon var mı yok mu diye kontrol etmemizi sağlar. Eğer bu isimle bir fonksiyon tanımlı değilse yeni fonksiyonumuzu tanımlamamıza imkan verir.

Yeni yeni uğraşanlar için güzel bir makale oldu bence, kolay gelsin.