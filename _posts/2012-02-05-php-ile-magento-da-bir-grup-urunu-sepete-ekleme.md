---
ID: 287
post_title: 'PHP ile Magento&#8217;da Bir Grup Ürünü Sepete Ekleme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-magento-da-bir-grup-urunu-sepete-ekleme-287.html
published: true
post_date: 2012-02-05 02:46:03
---
Merhaba arkadaşlar,

Magento'da basit ürünleri(simple prodcut) sepete atmanızı sağlayacak PHP kodu oldukça basittir. Tek ihtiyacınız olan '<strong>$cart-&gt;addProduct()</strong>' fonksiyonudur. Bu fonksiyonla beraber ürün id ve miktarını da gönderirsiniz. Fakat grup ürünlerin sepete atılması biraz farklıdır.

Öncelikle grup ürün nedir diyenlerin sorularını cevaplandıralım. Grup ürün olarak bir ürün açarsınız ve ürüne farklı ürünler bağlarsınız. Bağlayacağınız ürünler daha önce basit olarak girilmiş ürünlerdir. "Ekran Kartları" diye bir grup ürün seçersiniz ve buna "A ekran kartı" ve "B ekran kartı" ürünlerini bağlarsınız. Müşterilerini "Ekran Kartları" ürünüe girdiği zaman bu iki üründen bir tanesini veya ikisini aynı anda dilediği miktarda sipariş edebilir. Daha detaylı bilgi isterseniz kendiniz bir grup ürün ekleyip buna bir kaç ürünü bağlarsınız ve sitenizde kontrol edebilirsiniz.

Grup ürünleri sepete ekleme işlemi de oldukça basit bir işlemdir aslında. Bunun için bir $super_grup isimli bir dizi oluşturacağız ve bu dizide bağlanan ürünlerden satın alınmak istenilenleri ve miktarlarını addProduct() fonksiyonu ile işleyeceğiz. Bunun için aşağıdaki kodu kullanacağız:

<pre class="lang:php decode:1 " >&amp;lt;?php
// İlgili &uuml;r&uuml;nleri tutmamızı sağlayacak dizi
$super_grup = array();

// Grup &uuml;r&uuml;n&uuml;n id'si
$grup_urun_id = &amp;lt;grup_urun_id&amp;gt;;

// Bu grup urunde bağlanan urunlerden bizim sepete ekleteceklerimiz
$bagli_urunler = array('&amp;lt;bagli_urun_id_1&amp;gt;','&amp;lt;bagli_urun_id_2&amp;gt;','&amp;lt;bagli_urun_id_3&amp;gt;');
// Bu grup &uuml;r&uuml;nde yedi tane bağlı &uuml;r&uuml;n var fakat biz &uuml;&ccedil; tanesi se&ccedil;tik ;) Yani isteğe g&ouml;re &amp;lt;bagli_urun_id_4&amp;gt; vs. ekleyebilirdik

// Her bağlı &uuml;r&uuml;n i&ccedil;in ikişer tane sepete atalım
$adet = 2;

// Sepete atılacak bağlı &uuml;r&uuml;nleri $super_grup dizisine atalım ve &uuml;r&uuml;n id'lerini de dizi anahtarı olarak belirleyelim ve karşılarına da miktarlarını yazalım
foreach($bagli_urunler as $bagli_urun){
 if(intval($bagli_urun)){
   $super_grup[$bagli_urun] = $adet;
 }
}

// Grup &uuml;r&uuml;n&uuml; sepete ekleyelim
try {
 // Grup &uuml;r&uuml;n bilgileri &ccedil;ekmek i&ccedil;in gerekli nesneyi y&uuml;kleyelim
 $urun = Mage::getModel('catalog/product')-&amp;gt;load($grup_urun_id);

 // &Uuml;r&uuml;n uygun mu kontrol edelim
 if (!$urun) {
  echo &amp;quot;Hata ile karşılaşıldı!&amp;quot;;
  return;
 }

 // Sepet nesnesini &ccedil;ağıralım
 $sepet = Mage::getModel('checkout/cart');

 // Grup &uuml;r&uuml;n i&ccedil;in parametreleri alalım
 $parametreler = array('super_group' =&amp;gt; $super_grup);

 // &Uuml;r&uuml;nleri belirlediğimiz parametrelerle sepete atalım ve kaydedelim
 $sepet-&amp;gt;addProduct($urun, $parametreler)-&amp;gt;save();

 Mage::getSingleton('checkout/session')-&amp;gt;setCartWasUpdated(true);

 echo $this-&amp;gt;__('%s sepetinize eklendi.', Mage::helper('core')-&amp;gt;htmlEscape($urun-&amp;gt;getName()));

}
catch (Mage_Core_Exception $e){
 if (Mage::getSingleton('checkout/session')-&amp;gt;getUseNotice(true)){
  echo $this-&amp;gt;__($e-&amp;gt;getMessage());
 }
 else{
  $messages = array_unique(explode(&amp;quot;n&amp;quot;, $e-&amp;gt;getMessage()));
  foreach ($messages as $message) {
   echo &amp;quot;&amp;lt;br /&amp;gt;&amp;quot;.$message;
  }
 }
}
catch (Exception $e){
 echo $this-&amp;gt;__('&Uuml;r&uuml;n&uuml; sepete ekleyemezsiniz.');
}
?&amp;gt;</pre>

Yukarıdaki kodda nerede ne yaptığımızı açıkladım. Umarım işinize yarar,
Kolay gelsin