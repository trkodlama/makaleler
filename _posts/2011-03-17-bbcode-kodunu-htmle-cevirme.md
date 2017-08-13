---
ID: 115
post_title: 'BBCode Kodunu HTML&#8217;e Çevirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/bbcode-kodunu-htmle-cevirme-115.html
published: true
post_date: 2011-03-17 09:04:08
---
Merhaba arkadaşlar

Bu fonksiyon ile [b]..[/b] arasına yazılanları kalın, [i]...[/i] arasına yazılanları italik vs. olarak ekrana nasıl yazdırağımızı anlatıyorum. Bunun için basit bir fonksiyon yazmamız yeterli olacaktır.

Öncelikle fonksiyon.php dosyamızı oluşturalım ve için BBCode isimli bir fonksyion oluşturalım.

Düzenli ifadeleri kullanarak bir arama ve yerine yerleştirme işlemi ile rahatlıkla bu fonksiyomnumuzu yazabiliriz.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
function BBCode ($string) {
    $search = array(
        '[b](.*?)[/b]',
        '[i](.*?)[/i]',
        '[u](.*?)[/u]',
        '[img](.*?)[/img]',
        '[url=(.*?)](.*?)[/url]',
        '[code](.*?)[/code]'
    );
    $replace = array(
        '&lt;strong&gt;1&lt;/strong&gt;',
        '&lt;em&gt;1&lt;/em&gt;',
        '&lt;span style="text-decoration: underline"&gt;1&lt;/span&gt;',
        '&lt;img src="1" alt=""&gt;',
        '&lt;a href="1"&gt;2&lt;/a&gt;',
        '&lt;code&gt;1&lt;/code&gt;'
    );

    return preg_replace($search, $replace, $string);
}
?&gt;</pre>
İşte bu kadar artık bu fonksiyonumuz kullanılmaya hazır. Kullanımı da aşağıdaki şekilde olacaktır.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
echo BBCode('Bu yazının tam olara [b]bu kısmı(!)[/b] kalın yazılacaktır!');
?&gt;</pre>
Yukarıdaki PHP komutunun ekran çıktısı: "Bu yazının tam olara bu kısmı(!) kalın yazılacaktır!" şeklinde olacaktır. PHP'nin PECL eklentisi var BBCode'larla ilgili. Detaylı bilgi için <a href="http://php.net/manual/tr/book.bbcode.php" target="_blank">tıklayınız</a>.

Kolay gelsin