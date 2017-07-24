---
ID: 302
post_title: >
  JavaScript ile Uzak Adresten Veri
  Çekmek
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery/javascript-ile-uzak-adresten-veri-cekmek-302.html
published: true
post_date: 2012-02-23 03:04:45
---
Merhaba arkadaşlar,

Bu makalemde JavaScript ile farklı bir domain'den nasıl veri çekeceğinizi anlatıyorum. Bildiğiniz gibi domain'ler farklı oldukları zaman javascript ile işlem yapmak güçleşiyor.

Şimdi iki tane domain hayal edin. Birinde javascript kullanacağız, diğerinde ise PHP kullanacağız. JavaScript kullandığımız domain abc.com olsun. Diğer domain de def.com olsun. def.com'daki bilgleri abc.com'a çekmek için JSONP'siz $.post, $.get, $.ajax yöntemlerini kullanabilir miyiz? Kesinlikle hayır. Bu fonksiyonlarla harici bir domainden asla veri çekemeyiz. Bu noktada bizim yardımımıza $.getJSON() fonksiyonu koşuyor. Aslında bu da aşağıda göreceğiniz Ajax fonksiyonunun kısaltılmış halidir:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$.ajax({
 url: url,
 dataType: 'json',
 data: data,
 success: callback
});</pre>
$.getJSON ile farklı bir domain'e GET methodu ile veri gönderip oradan gelecek olan JSON datayı işleyebiliriz. Şimdi abc.com'dan şöyle bir sorgu göndereceğiz def.com'a: <strong>$.getJSON("http://def.com/trkodlama.php?jsoncallback=?");</strong>. Hemen abc.com adresimizin javascript kısmını kodlayalım
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// Bu kodu yazarken sayfanıza jquery yi eklediğinizi varsayıyorum.
$(document).ready(function () {
	var _this = $(this);
	$.getJSON("http://def.com/trkodlama.php?jsoncallback=?", function(data) {
		$.each(data.urunler, function(i,urun){
			icerik = '&lt;p&gt;' + urun.baslik + '&lt;/p&gt;';
			icerik += '&lt;p&gt;' + urun.aciklama+ '&lt;/p&gt;';
			icerik += '&lt;img src="' + urun.resim + '" alt=""&gt;';
			icerik += '&lt;br&gt;';
			$(icerik).appendTo("body");
		});
	});
});</pre>
Şimdide def.com/trkodlama.php dosyasının kodlarını verelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$dizi = Array('urunler' =&gt;
    Array(
        0 =&gt; Array(
            'baslik'    =&gt; 'Ürün 1',
            'aciklama'  =&gt; 'Kaliteli bir ürün',
            'resim'     =&gt; '/resim/15/1.jpg'
        ),
        1 =&gt; Array(
            'baslik'    =&gt; 'Ürün 2',
            'aciklama'  =&gt; 'Kalitesiz ama ucuz bir ürün',
            'resim'     =&gt; '/resim/15/2.jpg'
        )
    )
);
echo json_encode($dizi);
?&gt;</pre>
Kullanımı bu şekilde, umarım faydalı olur arkadaşlar,
Kolay gelsin,