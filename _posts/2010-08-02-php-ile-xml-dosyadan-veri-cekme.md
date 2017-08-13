---
ID: 71
post_title: 'PHP ile XML Dosya&#8217;dan Veri Çekme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-xml-dosyadan-veri-cekme-71.html
published: true
post_date: 2010-08-02 08:06:11
---
Bu makalemde PHP ile XML dosyasındaki veriyi nasıl okuyacağımızı göstereceğim. Bu makaleyi okuduktan sonra dilediğiniz sitenin(paylaşıma açık olması gerekli) XML dosyalarına erişebilirsiniz. Ayrıca kendi RSS Okuyucunuzu bile yapabilirsiniz. Sonuçta RSS okuyucularının çıkış noktası XML dosyalarının yorumlanmasıdır.

Teorik Bilgi: PHP simpleXML XML dosylarınızı nesneye çevirmenizi sağlar. Bu makalede simpleXML'in simplexml_load_file() fonksiyonunu göreceğiz.

Fonksiyonun kullanım yapısı şu şekildedir:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
simplexml_load_file('dosya'); // Daha detaylı bir kullanım için php.net'i ziyaret etmeyi unutmayın</pre>
Hemen bir örnek ile kullanımını göstereyim. Öncelikle uyeler.xml adlı bir dosya oluşturun. Bu dosyanın içeriği aşağıdaki gibi olsun:
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;uyeler&gt;
    &lt;uye&gt;
        &lt;ad&gt;sagoral&lt;/ad&gt;
        &lt;adres&gt;İzmir Türkiye&lt;/adres&gt;
        &lt;email&gt;ounal@trkodlama.com&lt;/email&gt;
    &lt;/uye&gt;
    &lt;uye&gt;
        &lt;ad&gt;Oral ÜNAL&lt;/ad&gt;
        &lt;adres&gt;İzmir Çiğli&lt;/adres&gt;
        &lt;email&gt;ounal_2@trkodlama.com&lt;/email&gt;
    &lt;/uye&gt;
    &lt;uye&gt;
        &lt;ad&gt;Oral&lt;/ad&gt;
        &lt;adres&gt;Çiğli Türkiye&lt;/adres&gt;
        &lt;email&gt;ounal_3@trkodlama.com&lt;/email&gt;
    &lt;/uye&gt;
&lt;/uyeler&gt;</pre>
Aşağıdaki PHP kodu ile XML dosyamızdaki bütün verileri simplexml_load_file() ve foreach() kullanarak okuyalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Şimdi uyeler.xml dosyamızı çekelim ve eğer hata meydala gelirse hatayı yazdıralım:
if(!$xml=simplexml_load_file('uyeler.xml')){
    trigger_error('XML dosyasını okurken hata meydana geldi.',E_USER_ERROR);
}

echo 'XML dosyasının içeriğini yazdıralım:...&lt;br /&gt;';
foreach($xml as $uye){
    echo 'Ad: '.$uye-&gt;ad.' Adres: '.$uye-&gt;adres.'
    Email: '.$uye-&gt;email.'&lt;br /&gt;';
}</pre>
Yukarıdaki PHP kodunun ekran görüntüsü aşağıdaki gibi olacaktır:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">XML Dosyasının içeriğini yazdıralım:...
Ad: sagoral Adres: İzmir Türkiye Email: ounal@trkodlama.com
Ad: Oral ÜNAL Adres: İzmir Çiğli Email: ounal_2@trkodlama.com
Ad: Oral Adres: Çiğli Türkiye Email: ounal_3@trkodlama.com</pre>
Gerçekten çok kolaymış değil mi? Ne kadar kolay olduğunu gördünüz. Å?imdi bir örnek daha yapalım ve tamamen pekiştirelim. Bu örneğimizde sadece adları alalım ve alt alta sıralayalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Şimdi uyeler.xml dosyamızı çekelim ve eğer hata meydala gelirse hatayı yazdıralım:
if(!$xml=simplexml_load_file('uyeler.xml')){
    trigger_error('XML dosyasını okurken hata meydana geldi.',E_USER_ERROR);
}

echo 'XML dosyasının içeriğini yazdıralım:...&lt;br /&gt;';
foreach($xml as $uye){
echo 'Ad: '.$uye-&gt;ad.' &lt;br /&gt;';
}</pre>
Yukarıdaki PHP kodunun ekran görüntüsü aşağıdaki gibi olacaktır:

XML Dosyasının içeriğini yazdıralım:...
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Ad: sagoral
Ad: Oral ÜNAL
Ad: Oral</pre>
Ne kadar kolay olduğunu görmüş olduk. Şimdi XML dosyasından bilgi çekme tarzımızı değiştirelim. Bu işlemde oldukça basittir. Tamamen dizi mantığı ile bu olayından üstesinden geleceğiz. Örneğimizi inceleyelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Sadece ilk üyenin bilgilerini çekelim
if(!$xml=simplexml_load_file('uyeler.xml')){
    trigger_error('XML dosyasını okurken hata meydana geldi.',E_USER_ERROR);
}

// İlk kullanıcının adını alalım
echo 'İlk kullanıcının adı: '.$xml-&gt;uye[0]-&gt;ad;</pre>
Yukarıdaki kodun ekran görüntüsü aşağıdaki gibi olacaktır:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">İlk kullanıcının adı: sagoral</pre>
PHP'de biliyorsunuz sayma işlemi 0'dan başlıyor.. Bu nedenle 1. üyenin bilgisini çekerken 0; 2. üyenin bilgisini çekerken 1 kullanıyoruz. Yani dizilerle aynı mantıkla çalışıyor.

Umarım yararlı olmuştur. Kolay gelsin,