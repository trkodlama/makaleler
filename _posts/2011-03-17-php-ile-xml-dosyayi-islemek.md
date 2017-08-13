---
ID: 120
post_title: PHP ile XML Dosyayı İşlemek
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-xml-dosyayi-islemek-120.html
published: true
post_date: 2011-03-17 16:10:03
---
XML(Extensible Markup Language) bilgilerinizi dallandırılmış halde saklamak için kullanılır. Genellikle uygulamalar arasında bilgi paylaşımı yapmak için kullanılır aynı zamanda RSS beslemeleride XML ile yapılmaktadır.

PHP 5'in ortaya çıkmasıya XML işleme desteği muhteşem bir şekilde arttı. Bu makale ile bizde PHP ile XML dökümanı işleme, değiştirme ve XML döküman oluşturma işlemlerini öğrenmiş olacağız. Makalenin en altında RSS beslemelerinin nasıl yapıldığını göreceğiz ve aynı zamanda basit bir RSS besleme okuyucusu hazırlamış olacağız.

Bu makaleyi tam anlamıyla kavrayabilmek için nesne tabanlı programlamaya hakim olmanız gerekiyor. Ayrıca XPath terimini biraz araştırmanız da fayda var. Çünkü bu makalede kullanacağız fakat olmasada olurlardan. O zaman başlayalım...

<strong>Parsing XML</strong>
PHP 5 SimpleXML isimli kullanımı basit olan bir sınıfa sahiptir.

Bu makale boyunca makaleler.xml adlı bir dosya oluşturdum ve trkodlama.com'da seçilmiş rastgele bir kaç makaleyi ekledim
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?xml version="1.0"?&gt;
&lt;makaleler&gt;
  &lt;makale id="1"&gt;
    &lt;baslik&gt;PHP Dersleri 1&lt;/baslik&gt;
    &lt;giris&gt;Echo komutu&lt;/giris&gt;
  &lt;/makale&gt;
  &lt;makale id="2"&gt;
    &lt;baslik&gt;PHP Dersleri 2&lt;/baslik&gt;
    &lt;giris&gt;Degiskenler&lt;/giris&gt;
  &lt;/makale&gt;
  &lt;makale id="3"&gt;
    &lt;baslik&gt;PHP Dersleri 3&lt;/baslik&gt;
    &lt;giris&gt;Kendi fonksiyonumuzu olusturalim&lt;/giris&gt;
  &lt;/makale&gt;
&lt;/makaleler&gt;</pre>
Şimdi PHP dosyamız ile XML dosyasını iki türlü işleme alabiliriz. Ya içeriği komple çekeriz ya da dosyanın yerini gösteririz:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// İçeriği çekelim
$veri = file_get_contents('makaleler.xml');
$makaleler = SimpleXMLElement($veri);
//-------------------
// Dosyanın yerini gösteririz
$makaleler = SimpleXMLElement('makaleler.xml', null, true);
?&gt;</pre>
Eğer makaleler.xml dosyası kendi sunucunuzda bulunuyorsa file_get_content() kullanamaya hiç gerek yoktur. file_get_contents() fonksiyonu ile çağırma işlemini sadece farklı web sunucularından XML dosya çekmek zorundaysak kullanmamız en temizi ve güzeli olurdur.

Dosyayı yüklemenin bir başka yöntemi ise simplexml_load_file() fonksiyonunu kullanmaktır. Bunu da şu şekilde gerçekleştirebiliriz:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$makaleler = simplexml_load_file('makaleler.xml');</pre>
Şimdi XML dosyamızdaki verileri HTML tabloya yazdıralım
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// SimpleXML
$makaleler = new SimpleXMLElement('makaleler.xml', null, true);

echo &lt;&lt;&lt;EOF
    &lt;table&gt;
        &lt;tr&gt;
			&lt;th&gt;ID&lt;/th&gt;
            &lt;th&gt;Başlık&lt;/th&gt;
            &lt;th&gt;Giriş&lt;/th&gt;
        &lt;/tr&gt;
EOF;
foreach($makaleler as $makale){
        echo &lt;&lt;&lt;EOF
            &lt;tr&gt;
                &lt;td&gt;{$makale['id']}&lt;/td&gt;
                &lt;td&gt;{$makale-&gt;baslik}&lt;/td&gt;
                &lt;td&gt;{$makale-&gt;giris}&lt;/td&gt;
            &lt;/tr&gt;
        EOF;
}
echo '&lt;/table&gt;';
?&gt;</pre>
Bu işlemin HTML çıktısı aşağıdaki gibi olacaktır:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table&gt;
        &lt;tr&gt;
                &lt;th&gt;ID&lt;/th&gt;
                &lt;th&gt;Başlık&lt;/th&gt;
                &lt;th&gt;Giriş&lt;/th&gt;
        &lt;/tr&gt;
        &lt;tr&gt;
				&lt;td&gt;1&lt;/td&gt;
                &lt;td&gt;PHP Dersleri 1&lt;/td&gt;
                &lt;td&gt;Echo komutu&lt;/td&gt;
        &lt;/tr&gt;
        &lt;tr&gt;
                &lt;td&gt;2&lt;/td&gt;
                &lt;td&gt;PHP Dersleri 2&lt;/td&gt;
                &lt;td&gt;Degiskenler&lt;/td&gt;
        &lt;/tr&gt;
        &lt;tr&gt;
                &lt;td&gt;3&lt;/td&gt;
                &lt;td&gt;PHP Dersleri 3&lt;/td&gt;
                &lt;td&gt;Kendi fonksiyonumuzu olusturalim&lt;/td&gt;
        &lt;/tr&gt;
&lt;/table&gt;</pre>
Peki siz makalelerden sadece ikinci makalenin başlığını çekmek istiyorsunuz. O zaman şöyle yaparız(dizilerde sayma işleminin 0'dan başladığını hatırlayın)
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">echo $makaleler-&gt;makale[1]-&gt;baslik;</pre>
Aynı makalenin ID'sini şu şekilde çekiyoruz:
<pre class="lang:php decode:1 ">echo $makaleler-&amp;amp;gt;makale[1]['id'];</pre>
<strong>XPath</strong>
Aynı zamanda Xpath sorgularını da çalıştırabilirsiniz. SimpleXMLElement::xpath() methodunu kullanarak çalışırlar. Eğer bütün makalelerin başlıklarını çekmek istersek aşağıdaki gibi birşey yapabiliriz:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$basliklar = $makaleler-&gt;xpath('makale/baslik');
foreach($basliklar as $baslik)
{
        echo $baslik.PHP_EOL;
}
?&gt;</pre>
Ya da bütün ID'leri çekmek için:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$id = $makaleler-&gt;xpath('makale/@id');
foreach($id as $id){
    echo $id.PHP_EOL;
}
?&gt;</pre>
<strong>RSS Beslemelerini İşleme</strong>
Şimdi www.trkodlama.com/rss.php adresinden verileri alalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$rss = new SimpleXMLElement('http://www.trkodlama.com/rss.php', null, true);

echo "&lt;h1&gt;&lt;a href='{$rss-&gt;channel-&gt;link}'&gt;{$rss-&gt;channel-&gt;title}&lt;/a&gt;&lt;/h1&gt;".PHP_EOL.'&lt;hr /&gt;'.PHP_EOL;

foreach($rss-&gt;xpath('channel/item') as $item){
    echo &lt;&lt;&lt;EOF
        &lt;h2&gt;&lt;a href='{$item-&gt;link}'&gt;{$item-&gt;title}&lt;/a&gt;&lt;/h2&gt;
        &lt;div&gt;Gönderilme Zamanı: {$item-&gt;pubDate}&lt;/div&gt;
        {$item-&gt;description}
        &lt;hr /&gt;
    EOF;
}
?&gt;</pre>
Bu size sayfanın başında söylediğim RSS besleme okuyucumuz. Bu okuyucumuzu daha da geliştirmek için biraz AJAX kullanın ve arayüzü şık bir hale getirin.

Gördüğünüz gibi XML bilgiyi işleme XML dosyanın yapısını bildikten sonra SimpleXML ile oldukça basit. Peki yapısını bilmediğiniz bir XML'i işleme almak için ne yapmalısınız? O zaman aşağıdaki işlemleri inceleyin. Fakat hala makaleler.xml dosyamızı kullanmaya devam edeceğiz.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
function isle(SimpleXMLElement $element, $level = 0)
{
    $indent     = str_repeat("t", $level);

    $deger      = trim((string) $element);  // değeri çek ve başlangıç-bitiş arasındaki bütün boşlukları sil
    $parametreler = $element-&gt;attributes();   // bütün parametreleri çek
    $children   = $element-&gt;children();     // children(türkçe ne olarak söylenir bilmiyorum)'ları çek

    echo "{$indent}Parsing '{$element-&gt;getName()}'...".PHP_EOL;
    if(count($children) == 0 &amp;&amp; !empty($deger)) // Değer doluysa ve children'ı yoksa göster
    {
        echo "{$indent}Değer: {$element}".PHP_EOL;
    }

    // parametre var ise göster
    if(count($parametreler) &gt; 0){
        echo $indent.' deki '.count($parametreler).' parametre:'.PHP_EOL;
        foreach($parametreler as $parametre){
            echo "{$indent}- {$parametre-&gt;getName()}: {$parametre}".PHP_EOL;
        }
    }

    if(count($children)){
        echo $indent.' deki '.count($children).' children:'.PHP_EOL;
        foreach($children as $child){
            isle($child, $level+1);
        }
    }
    echo $indent.PHP_EOL; // daha temiz hale getirmek için
}

$xml = new SimpleXMLElement('makaleler.xml', null, true);

isle($xml);
</pre>
Not: Eğer bunu bir tarayıcıda çalıştırmak isterseniz <strong>header('Content-type: text/plain');</strong> kodunu ekrana herhangi bir çıktı vermeden önce kullanmalısınız. Böylece tarayıcı bunun sadece bir text olduğunu ve HTML içermediğini anlayacaktır.

Aslında SimpleXML'den çok daha güçlü bir XML işleyicimiz var. Adı da PHP DOM fakat buna şimdi değinmiyorum. Çünkü bende çok iyi bilmiyorum. PHP DOM'u iyice sindirdikten sonra sizler sunarım.

Umarım faydalı ve akıcı bir anlatım olmuştur. Sorularını forumdan, iletişim formundan veya yorum olarak sorabilirsiniz.

Kolay gelsin,