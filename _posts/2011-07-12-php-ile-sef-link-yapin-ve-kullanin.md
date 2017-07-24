---
ID: 213
post_title: PHP ile SEF Link Yapın Ve Kullanın
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/php-ile-sef-link-yapin-ve-kullanin-213.html
published: true
post_date: 2011-07-12 23:12:13
---
Merhaba arkadaşlar,

Bugün SEO'nun-arama motoru optimizasyonu- vazgeçilmezi olan arama motoru dostu link yapımını veya bunun da orjinal adıyla söylemek gerekirse SEF link yapımını göreceğiz. Şimdi makale, haber veya ürün bilgilerini tuttuğunu tablonuzda bir sütun daha oluşturun. Bu sütuna <code>sef</code> adını verin. Artık tablonuzda makale, haber veya ürün başlıklarınızın SEF halinide tutabileceğiniz bir sütununuz var. Bundan sonra yeni makale eklerken başlıklarınızın SEF halinide ekleyeceksiniz.

Bu makale ile neler öğreneceksiniz?
<ul>
 	<li>Girilen bir başlığı SEF Link'e çeviren PHP fonksiyonunu</li>
 	<li>.htaccess dosyasında RewriteEngine, RewriteBase ve RewriteRule</li>
 	<li>.htaccess dosyasının SEF link işlemlerinde nasıl kullanıldığını</li>
 	<li>deneme.com/deneme-baslik-1.html adresinin aslında deneme.com/makale_oku.php?sef=deneme-baslik&amp;id=1 sayfası olduğunu ama bunu son kullanıcının asla anlamadığını ve bu işlemin nasıl yapılacağını öğreneceksiniz.</li>
</ul>
Şimdi sizlere PHP'de kullanacağımız fonksiyonu veriyorum:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * sef_link()
 *
 * Basliklari SEF linke çevirme fonksiyonu
 *
 * @param mixed $s
 * @return
 */
function sef_link($string)
    {
        $turkce=array("ş", "Ş", "ı", "ü", "Ü", "ö", "Ö", "ç", "Ç", "ğ", "Ğ", "İ");
        $duzgun=array("s", "s", "i", "u", "u", "o", "o", "c", "c", "g", "g", "i");
        $string = str_replace($turkce, $duzgun, $string);
        $string = trim($string);
        $string = html_entity_decode($string);
        $string = strip_tags($string);
        $string = strtolower($string);
        $string = preg_replace('~[^ a-z0-9_.]~', ' ', $string);
        $string = preg_replace('~ ~', '-', $string);
        $string = preg_replace('~-+~', '-', $string);
    
        return $string;
}</pre>
Bu fonksiyon aracılığıyla başlıklarınızı sef hale getirebilirsiniz. Örnek vermek gerekirse "C++ Ders 1: Bir programın yapısı" başlığını "<strong>c-ders-1-bir-programin-yapisi"</strong> şekline çevirelim.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Sadece id, başlık ve sef'i insert ediyoruz
$baslik="C++ Ders 1: Bir programın yapısı";
$sef=sef_link($baslik);

mysqli_query($db, "INSERT INTO makale(id, baslik, sef) VALUES(NULL, '$baslik', '$sef')");
// id sütunumuz auto-increment olduğu için NULL yazdık</pre>
Şimdi veritabanına giriş yaptık. Şimdi .htaccess dosyamızı oluşturalım. Htaccess dosyası sayesinde makale_oku.php diye oluşturacağımız dosyayı gizleyip onu SEF halde görmemizi sağlayacak. Bunun için .htaccess dosyasında RewriteEngine diye bir motor çalıştıracağız. Şimdi başlayalım hemen .htaccess dosyasına:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">RewriteEngine On
RewriteBase /
RewriteRule ^([a-zA-Z0-9-_]+)-([0-9]+).html$ /makale_oku.php?sef=$1&amp;id=$2</pre>
Şimdi <strong>.htaccess</strong> dosyamızda yazdıklarımızı açıklayalım. <code class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">RewriteEngine</code>'i On yaparak linklerimizin görünümünü değiştirmemizi sağlayan motoru aktifleştirdik. Daha sonra RewriteBase ile anadizinimizi belirledik. Son satırdaki RewriteRule ile yaptığımız işlem tam olarak şu:
- Eğer adres satırı <code class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">([a-zA-Z0-9-_]+)-([0-9]+).html</code> yapısını sağlıyorsa bu sayfanın makale_oku.php dosyasını açmasını sağlıyor.
- Daha sonra <strong>$1</strong> olarak ilk değişken kısmını alır. Bizim <strong>$1</strong>'e karşılık gelen kısmımız <code class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">([a-zA-Z0-9-_]+)</code> kısmıdır.<strong>$2</strong> kısmına denk gelen kısım ise <code class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">([0-9]+)</code> kısmıdır.
Yani deneme.com/deneme-baslik-1.html sayfası aslında deneme.com/makale_oku.php?sef=deneme-baslik&amp;id=1 sayfasını çalıştırıyor. Fakat son kullanıcılar bunu asla farkedemezler. Şimdi makale_oku.php sayfamızı düzenleyelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// deneme.com/deneme-baslik-1.html adresine girmiş olalım
$sef = $_GET["sef"];
$id = $_GET["id"];

$vt_kontrol=mysqli_fetch_assoc(mysqli_query($db, "SELECT * FROM makale WHERE id=$id AND sef='$sef'"));

if(!$vt_kontrol){
	echo "404 - sayfa bulunamadı";
}
else{
	echo $vt_kontrol["baslik"];
}</pre>
Bu kadar basit arkadaşlar, sef link bu şekilde yapılmaktadır. Umarım işinize yarar, sorularınızı forumdan veya aşağıdaki yorum formu aracılığıyla iletebilirsiniz.
Kolay gelsin,