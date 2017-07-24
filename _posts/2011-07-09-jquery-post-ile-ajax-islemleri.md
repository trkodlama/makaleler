---
ID: 209
post_title: jQuery $.post ile AJAX İşlemleri
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-post-ile-ajax-islemleri-209.html
published: true
post_date: 2011-07-09 22:49:19
---
Merhaba arkadaşlar,

Bugün sizlere herkesin çok merak ettiği AJAX işlemlerinden bahsediyorum. AJAX işlemlerimizi jQuery JavaScript kütüphanesi ile gerçekleştireceğiz. Öncelikle jQuery kütüphanesini <a href="http://www.jquery.com" target="_blank">buraya tıklayarak</a> indirelim. Ben bu AJAX işlemlerini PHP ile anlatacağım, aynı mantıkla ASP ile de yapabilirsiniz.

Öncelikle <strong>index.html</strong> adlı bir dosya oluşturalım ve bu dosyanın içine aşağıdaki kodları ekleyelim:

<pre class="lang:html decode:1 " >&amp;lt;!DOCTYPE html PUBLIC &amp;quot;-//W3C//DTD XHTML 1.0 Transitional//EN&amp;quot; &amp;quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&amp;quot;&amp;gt;
&amp;lt;html xmlns=&amp;quot;http://www.w3.org/1999/xhtml xml:lang=&amp;quot;en&amp;quot; lang=&amp;quot;en&amp;quot;&amp;gt;

&amp;lt;head&amp;gt;
	&amp;lt;meta http-equiv=&amp;quot;content-type&amp;quot; content=&amp;quot;text/html; charset=iso-8859-1&amp;quot; /&amp;gt;
	&amp;lt;meta name=&amp;quot;author&amp;quot; content=&amp;quot;trkodlama.com&amp;quot; /&amp;gt;

	&amp;lt;title&amp;gt;PHP ile AJAX işlemleri&amp;lt;/title&amp;gt;
    &amp;lt;script src=&amp;quot;js/jquery-1.6.2.min.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt; &amp;lt;!-- js isimli bir klas&ouml;r oluşturup indirdiğimiz jQuery k&uuml;t&uuml;phanesini i&ccedil;ine klas&ouml;r&uuml;n i&ccedil;ine attık --&amp;gt;
&amp;lt;/head&amp;gt;
&amp;lt;body&amp;gt;
    &amp;lt;h1&amp;gt;Bir Form &Ouml;rneği&amp;lt;/h1&amp;gt;
    &amp;lt;p&amp;gt;Aşağıdaki &ouml;rnek bir form &ouml;rneği olacak. Butona tıkladığı anda islem.php sayfasına form bilgileri POST methodu ile g&ouml;nderilecektir. Ordan gelen cevaba g&ouml;re sayfada işlemler ger&ccedil;ekleştirilecektir.&amp;lt;/p&amp;gt;
    &amp;lt;form method=&amp;quot;POST&amp;quot; id=&amp;quot;girisFormu&amp;quot;&amp;gt;
    &amp;lt;p&amp;gt;Kullanıcı Adınız: &amp;lt;input type=&amp;quot;text&amp;quot; name=&amp;quot;kullanici&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;p&amp;gt;Şifreniz: &amp;lt;input type=&amp;quot;password&amp;quot; name=&amp;quot;sifre&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;p&amp;gt;&amp;lt;input type=&amp;quot;button&amp;quot; id=&amp;quot;jQueryTetikleyicisi&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;/form&amp;gt;
    &amp;lt;p id=&amp;quot;sonuc&amp;quot;&amp;gt;Butona tıkladığınız anda bu yazı değişecek islem.php sayfasından gelen cevap yazdırılacaktır.&amp;lt;/p&amp;gt;
&amp;lt;/body&amp;gt;
&amp;lt;/html&amp;gt;</pre>

Yukarıdaki kodda daha jQuery kodlarımızı eklemedik, o nedenle butona basmanız henüz birşeyi değiştirmeyecek. Fakat alanlarımızı gerekli bölümleri oluşturduk. Şimdi yapacağımız işlem çok basit.<strong>jQueryTetikleyicisi</strong>'ne yani butona tıkladığımız <strong>girisFormu</strong> formu serialize() fonksiyonu aracılığıyla düzenlenecek ve düzenlenmiş veriyi <strong>islem.php</strong> sayfasına göndereceğiz. Orada sanki normal bir PHP sayfaymış gibi $_POST ile gelen verileri işleyeceğiz. <strong>islem.php</strong> sayfasından bir yazı göndereceğiz ve o yazıyı <strong>sonuc</strong> isimli alana yazdıracağız. Ama ondan önce yarım kalan HTML sayfamızı tamamlayalım:

<pre class="lang:html decode:1 " >&amp;lt;!DOCTYPE html PUBLIC &amp;quot;-//W3C//DTD XHTML 1.0 Transitional//EN&amp;quot; &amp;quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&amp;quot;&amp;gt;
&amp;lt;html xmlns=&amp;quot;http://www.w3.org/1999/xhtml xml:lang=&amp;quot;en&amp;quot; lang=&amp;quot;en&amp;quot;&amp;gt;

&amp;lt;head&amp;gt;
	&amp;lt;meta http-equiv=&amp;quot;content-type&amp;quot; content=&amp;quot;text/html; charset=iso-8859-1&amp;quot; /&amp;gt;
	&amp;lt;meta name=&amp;quot;author&amp;quot; content=&amp;quot;trkodlama.com&amp;quot; /&amp;gt;

	&amp;lt;title&amp;gt;PHP ile AJAX işlemleri&amp;lt;/title&amp;gt;
    &amp;lt;script src=&amp;quot;js/jquery-1.6.2.min.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt; &amp;lt;!-- js isimli bir klas&ouml;r oluşturup indirdiğimiz jQuery k&uuml;t&uuml;phanesini i&ccedil;ine klas&ouml;r&uuml;n i&ccedil;ine attık --&amp;gt;
    &amp;lt;script&amp;gt;
    $(document).ready(function(){
        $(&amp;quot;#jQueryTetikleyicisi&amp;quot;).click(function(){
            var formData = $(&amp;quot;#girisFormu&amp;quot;).serialize();
            $.post(&amp;quot;islem.php, formData, function(data){
                $(&amp;quot;#sonuc&amp;quot;).html(data);
            });
        });
    });
    &amp;lt;/script&amp;gt;
&amp;lt;/head&amp;gt;

&amp;lt;body&amp;gt;

    &amp;lt;h1&amp;gt;Bir Form &Ouml;rneği&amp;lt;/h1&amp;gt;
    &amp;lt;p&amp;gt;Aşağıdaki &ouml;rnek bir form &ouml;rneği olacak. Butona tıkladığı anda islem.php sayfasına form bilgileri POST methodu ile g&ouml;nderilecektir. Ordan gelen cevaba g&ouml;re sayfada işlemler ger&ccedil;ekleştirilecektir.&amp;lt;/p&amp;gt;
    &amp;lt;form method=&amp;quot;POST&amp;quot; id=&amp;quot;girisFormu&amp;quot;&amp;gt;
    &amp;lt;p&amp;gt;Kullanıcı Adınız: &amp;lt;input type=&amp;quot;text&amp;quot; name=&amp;quot;kullanici&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;p&amp;gt;Şifreniz: &amp;lt;input type=&amp;quot;password&amp;quot; name=&amp;quot;sifre&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;p&amp;gt;&amp;lt;input type=&amp;quot;button&amp;quot; id=&amp;quot;jQueryTetikleyicisi&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;
    &amp;lt;/form&amp;gt;
    &amp;lt;p id=&amp;quot;sonuc&amp;quot;&amp;gt;Butona tıkladığınız anda bu yazı değişecek islem.php sayfasından gelen cevap yazdırılacaktır.&amp;lt;/p&amp;gt;
&amp;lt;/body&amp;gt;
&amp;lt;/html&amp;gt;</pre>

Şimdi biraz da kullandığımız <strong>jQuery</strong> fonksiyonlarını anlatalım

<strong>$.post()</strong>
Yaptığı işlem çok basittir. Sizin belirttiğiniz sayfaya gider, eğer sayfaya post etmek istediğiniz veriler varsa onları da post eder ve isteğe bağlı olarak sayfadan gelen sonuçları alır. Biraz örnekleyelim:

<pre class="lang:js decode:1 " >$.post(&amp;quot;deneme.php)  </pre>

Bu şekilde çalıştırırsanız deneme.php sayfasını arkaplanda açar ve çıkar. Herhangi bir veri post etmez. Sonuç döndürmez.

<pre class="lang:js decode:1 " >$.post(&amp;quot;deneme.php, &amp;quot;site=trkodlama&amp;amp;amp;tld=com&amp;quot;);</pre>

Bu ise deneme.php sayfasına site ve tld parametrelerini post eder.

<pre class="lang:js decode:1 " >$.post(&amp;quot;deneme.php, &amp;quot;site=trkodlama&amp;amp;amp;tld=com&amp;quot;, function(data){
     alert(data);
});</pre>

Bu şekilde ise sayfadan gelen sonucu alert ile ekrana yazmamızı sağlar.

<strong>.serialize()</strong>: http://togl.me/323 adresinden detaylı bilgiye ulaşabilirsiniz

<strong>.click()</strong>: http://togl.me/c9 adresinden detaylı bilgiye ulaşabilirsiniz

<strong>.html()</strong>: http://togl.me/294 adresinden detaylı bilgiye ulaşabilirsiniz

Bu kadar açıklama yeterli olmuştur. Şimdi de islem.php sayfamızı yazalım:

<pre class="lang:php decode:1 " >&amp;lt;?php

/**
 * @author trkodlama
 * @copyright 2011
 */

$kullanici=trim($_POST[&amp;quot;kullanici&amp;quot;]);
$sifre=trim($_POST[&amp;quot;sifre&amp;quot;]);

if(strlen($kullanici)&amp;lt;4){
    echo &amp;quot;Kullanıcı adınız en az 4 karakter olmalıdır&amp;quot;;
}
elseif(strlen($sifre)&amp;lt;6){
    echo &amp;quot;Şifreniz en az 6 karakter olmalıdır&amp;quot;;
}
elseif($kullanici=&amp;quot;trkodlama.com&amp;quot; &amp;amp;&amp;amp; $sifre=&amp;quot;ajax&amp;quot;){
    echo &amp;quot;Tebrikler başarı ile giriş yaptınız&amp;quot;;
}
else{
    echo &amp;quot;Hatalı kullanıcı adı veya şifre&amp;quot;;
}

?&amp;gt;</pre>

Burada yaptığımız işlemler basit, sayfadan gelen verileri kontrol ettik, ona göre bir cevap verdik. Siz burda mysql kullanarak kontrollerinizi yapacaksınız. Tek fark budur.

Sorularını yorum olarak yada forumdan iletebilirsiniz, kolay gelsin arkadaşlar.

[wpdm_file id=6]