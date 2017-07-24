---
ID: 341
post_title: 'Magento&#8217;da Mağaza Kodunu Alma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magentoda-magaza-kodunu-alma-341.html
published: true
post_date: 2012-03-14 20:12:50
---
Merhaba arkadaşlar,

Bu yazıda sizlere mağaza kodu almayı göstereceğim. Ama ondan önce buna neden ihtiyaç duyabileceğinizi anlatıyorum.

Magento bilindiği üzere oldukça gelişmiş bir e-ticaret sistemidir. Bu sistemin en büyük silahlarından birisi ya da şöyle diyelim bu sistemi diğerlerinden ayıran en güçlü özelliği çoklu mağaza özelliğidir.

Çoklu mağaza(Multi store) özelliği sayesinde tek bir yönetici paneli ile birden fazla domain'i yönetebiliyorsunuz. Yani farklı e-ticaret amaçları için almış olduğunuz domainlerin hepsinin içeriğini, kategorilerini, ürünlerini tek bir panelden yönebiliyorsunuz. Aynı yönetici paneline sahip olmalarına rağmen birbirlerinden tamamen bağımsız web sayfaları yapmanıza olanak sağlıyor.

Şimdi gelelim neden buna ihtiyaç duyacağınıza.. İki adet web siteniz var ve siz sadece birinde görünmesini istediğiniz temasal düzenlemeler yapmak istiyorsunuz. İşte bu noktada bu  tek satırlık mağaza kodunu alan PHP koduna ihtiyaç duyarsınız.

Bu arada çoklu mağaza oluştururken her mağaza için unique bir mağaza kodu belirlersiniz. Biz bu mağaza koduna göre işlem yapacağız.

<pre class="lang:php decode:1 " >$magaza_kodu =&nbsp;Mage::app()-&amp;gt;getStore()-&amp;gt;getCode();</pre>

Yukarıdaki kod ile mağaza kodunu rahatlıkla alabilirsiniz. Şimdi diyelim ki iki adet mağazamız var. Bunların kodları <strong>magaza_1</strong> ve <strong>magaza_2</strong> olsun. Bir örnekle şunu yapalım, "Merhaba" yazısı <strong>magaza_1</strong>'de görünmesin ama <strong>magaza_2</strong>'de görünsün:

<pre class="lang:php decode:1 " >&amp;lt;?php
$magaza_kodu =&nbsp;Mage::app()-&amp;gt;getStore()-&amp;gt;getCode();

if($magaza_kodu == &amp;quot;magaza_2&amp;quot;){
echo &amp;quot;Merhaba&amp;quot;;
}
?&amp;gt;</pre>

Yukarıdaki kod ile net bir şekilde anlaşıldığı gibi eğer mağaza kodu magaza_2 ise "Merhaba" yazdıracak. İhtiyacınız olursa kullanmaktan kesinlikle çekinmeyin arkadaşlar, kolay gelsin.