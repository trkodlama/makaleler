---
ID: 6189
post_title: >
  PHP İle Sayfa Oluşturma Süresini
  Hesaplama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-sayfa-olusturma-suresini-hesaplama-6189.html
published: true
post_date: 2017-01-17 08:02:49
---
Sayfalarınızın PHP'de oluşturulma sürelerini ölçmek hazırladığınız kodların performansı hakkında size fikir verir. Bu sayede kodlamanızı daha da optimize etmeniz gerekip gerekmediğine karar verebilirsiniz. Ayrıca hazırladığınız iki farklı algoritmanın hangisinin daha fazla performans sağladığını ölçmek için de oluşturma süresini hesaplamanız gerekir.

Sayfa oluşturma süresini PHP 5'den önce ve sonra diye iki kısımda inceleyebiliriz. Bunun nedeni PHP 5'den önce <a href="http://php.net/manual/tr/function.microtime.php" target="_blank"><strong>microtime()</strong></a> fonksiyonu ile uğraşmak biraz fazla zahmetli bir işlem olmasına karşın PHP 5'den sonra bu zahmetinin ortadan kalkmasıdır.
<blockquote>PHP 5 ile gelen <strong>gerçek_sayı</strong> değiştirgesi bazı işlemleri yapmadan direk sonuca ulaşmanızı sağlıyor.
İşlev, isteğe bağlı olarak değiştirgesiz çağırıldığında; "msan. san." dizgesini döndürür. 'san.' geçerli zamanın Unix Zamam Başlangıcından (1 Ocak 1970 0:00:00 GMT) itibaren hesaplanan saniyeyi ve 'msan.' ise mikrosaniye kısmını belirtir. Dizgenin iki kısmı da saniye cinsindendir.
İsteğe bağlı kullanılan bu değiştirgeyle <code class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">TRUE</code>  aktarıldığında, saniyeler float türünde döndürülür.</blockquote>
<h2>PHP 5'den Sonra Sayfa Yüklenme Hızını Bulma</h2>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$sure_baslangici = microtime(true);

// Biraz bekle
usleep(100);

$sure_bitimi = microtime(true);
$sure = $sure_bitimi - $sure_baslangici;

echo "Bekleme süresi: $sure saniye.\n";
?&gt;</pre>
<h2>PHP 5'den Önce Sayfa Yüklenme Hızını Bulma</h2>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * PHP 5 davranışını taklit eden basit bir işlev
 */
function microtime_float()
{
    list($usec, $sec) = explode(" ", microtime());
    return ((float)$usec + (float)$sec);
}

$sure_baslangici = microtime_float();

// Biraz bekle
usleep(100);

$sure_bitimi = microtime_float();
$sure = $sure_bitimi - $sure_baslangici;

echo "Bekleme süresi: $sure saniye\n";
?&gt;</pre>
Umarım işinize yarar, kolay gelsin dilerim..