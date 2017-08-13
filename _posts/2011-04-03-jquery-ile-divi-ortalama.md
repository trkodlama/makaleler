---
ID: 130
post_title: 'jQuery ile Div&#8217;i Ortalama'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/jquery-ile-divi-ortalama-130.html
published: true
post_date: 2011-04-03 17:13:24
---
Bugün jQuery kullanarak bir div elementini sayfanın nasıl ortasına yerleştireceğinizi anlatıyorum.

Bu makalede jQuery'nin width() ve height() fonksiyonlarından faydalanıyoruz. Lafı fazla uzatmayalım. Öncelikle bir index.html adlı dosya oluşturalım. Daha sonra bu dosyanın içine aşağıdaki kodu ekleyelim:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(document).ready(function(){
    var blok = $('#orta');
    var yuk = $(window).height();
    var gen = $(document).width();
    var sT = window.scrollY;
    $('#orta').css({
        left : gen/2 - (blok.width() / 2),
        top : sT + yuk/2 - (blok.height() / 2)
    });
});</pre>
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">body{
    background-color: #0000CC;
}
#orta{
    position: absolute;
    width: 250px;
    height: 250px;
    background-color: #CC0000;
}</pre>
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;html&gt;
&lt;head&gt;
&lt;!-- Stil ve JS dosyalarını yükleyin. --&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="orta"&gt;Bu Blok Sayfayı Tam Ortalayacaktır&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>
Burada tam olarak şunu yaptık. yuk değişkenine geçerli pencerenin yüksekliğini atadık. #orta adlı bloğun top değerini bulduğumuz yuk değerinin yarısından #orta adlı bloğun yarısını çıkararak bulduğumuz değeri atadık. Bu sayede sayanın dikey olarak tam ortasına yerleştirmiş oluyoruz. Aynı mantıkla yatay olarak yerleştirdik.

<strong>GÜNCELLEME: <a href="https://www.trkodlama.com/web-tasarim-2/yazilari-yatay-ve-dikey-olarak-flexbox-ile-kusursuz-ortalama-6210.html">Flexbox ile ortalama</a> için tıklayınız.</strong>

Herkesin problemi var genelde bu sayfa ortalama ile ilgili. Bende paylaşmak istedim sizinle. Umarım anlatabilmişimdir.

Kolay gelsin,