---
ID: 9180
post_title: 'Symfony Framework&#8217;ü ile İlk Sayfamızı Oluşturalım'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/symfony-frameworku-ile-ilk-sayfamizi-olusturalim-9180.html
published: true
post_date: 2017-02-16 20:09:30
---
Serimizin bu makalesinde Symfony Framework ile ilk sayfamızı oluşturmaya başlayacağız. Aslında serinin sonraki makaleleri görüntülü hazırlamak istiyorum. Çünkü yazarak anlatması ve anlaması oldukça zorlayacak gibi geliyor.
<h2>Üzerinde Çalışacağımız Klasörler</h2>
Symfony ile çalışırken kodlamalarımızı <strong>src/</strong> ve <strong>app/</strong> klasörlerinde yapacağız sadece. Bu iki klasör sizin için oldukça önemli olacaktır. Aslında <strong>web/</strong> klasörü üzerinde de değişiklik yapacağız fakat orası o kadar da önemli değil :) Kısacası app/ ve src/ klasörleri dışındaki tüm klasörleri bu aşamada görmezden gelin. <strong>src/</strong> klasörünü oluşturduğunuz bütün class'ları saklarken <strong>app/ </strong>klasörüde tema ve ayar dosyalarınızı sakladığınız klasördür.
<h2>Symfony Framework'ün de İlk Sayfayı Oluşturalım</h2>
Symfony framework'ü ile hazırlanmış varsayılan sayfanızı çalıştırın. Yani localhost:8000 adresine gidin. Sizi karşılayan sayfa varsayılan olarak gelen sayfadır ve bu sayfa <strong>DefaultController.php</strong> dosyasından derlenir. <em><strong>src/</strong></em> klasörünün altında bulabilirsiniz. Şimdi onu silin! Evet silin! Ona ihtiyacımız yok. Fakat isterseniz silmeden önce inceleyebilirsiniz. Anasayfayı tarayıcıda tekrar açın:
<blockquote><strong>No route found for "GET /"</strong></blockquote>
Bu hatayı alacaksınız gayet normal. Çünkü ana dizin için yani "/" için bir route tanımlanmadı. O zaman konumuza geri dönelim ve bir sayfa oluşturalım.

Projemiz bisiklet türleri üzerine olsun ve projemizin adı <strong>Piskiletçi</strong> olsun :) Bisiklet türlerinden ve bu türlerin farklılıklarına değinelim bol bol makalemizin içinde. İlk sayfamızda türlerimizden bir tanesi olan MTB'ye değinelim.

Symfony'de sayfa oluşturmak iki adımdan oluşuyor. Bunlar <em><strong>route</strong></em> ve<em><strong> controller</strong></em> 'dır. Aslında modern bütün framework lerde bu böyledir. <strong>Route</strong> yeni sayfamızın URL'sini oluşturmamızı sağlarken, <strong>Controller</strong> da bu sayfamızın içeriğini oluşturmamızı sağlar.
<h2>Namespaces</h2>
O zaman adım bir ile başlayalım: <em><strong>route</strong> </em>oluşturalım! Aslında biz adım iki başlayacağız. Sebebini anlayacaksınız. Şimdi <em><strong>AppBundle/Controller</strong></em> içine TurController isminde yeni bir sınıf ekliyoruz.

<img class="aligncenter size-full wp-image-9181" src="https://www.trkodlama.com/wp-content/uploads/2017/02/symfony-1.png" alt="" width="516" height="287" />

Fakat o da ne! Namespace alanı boş geliyor!?

<img class="aligncenter size-full wp-image-9182" src="https://www.trkodlama.com/wp-content/uploads/2017/02/symfony-2.png" alt="" width="552" height="351" />

Eğer bu şekilde boş gelirse yapacağınız şey çok basit, hiç boşuna paniklemeyin, hemen google'ı açıp delilercesine araştırmaya başlamayın. Esc'ye basın ve pencereyi kapatın. Soldaki proje dosyalarınızı <em><strong>src/</strong></em> klasörünüzü bulun, ona sağ tıklayın ve "<em><strong>mark directory as sources root</strong></em>" seçeneğini seçin.

<img class="aligncenter size-full wp-image-9183" src="https://www.trkodlama.com/wp-content/uploads/2017/02/symfony-3.png" alt="" width="497" height="716" />

"Ohh be, sıkıntısız çözdük" dediğinizi duyar gibiyim. Şimdi tekrar yeni sınıfımızı oluşturmayı deneyelim ve sınıfımızın adı TurController olsun. Size otomatik olarak aşağıdaki gibi bir dosya oluşturacaktır:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * Created by PhpStorm.
 * User: trkodlama
 * Date: 16.02.2017
 * Time: 18:38
 */

namespace AppBundle\Controller;


class TurController
{

}</pre>
<blockquote>Eğer <strong>Namespace</strong> kavramıyla ilgili bilginiz yoksa biraz araştırma yapmanızı öneririm. Yakında namespace üzerine belki bir makale yazabilirim. Fakat şu anda google'da arayıp birşeyler okumanızı öneriyorum.</blockquote>
Burada en önemli olay <strong>namespace</strong> ile <strong>proje dizininiz</strong> birbiriyle eşleşmelidir. Aksi halde Symfony framework çalışmayacaktır.
<h2>Controller ve Route</h2>
Şimdi <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >public function showAction()</pre> ile sayfamızı oluşturalım.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * Created by PhpStorm.
 * User: trkodlama
 * Date: 16.02.2017
 * Time: 18:38
 */

namespace AppBundle\Controller;


class TurController
{
    public function showAction(){
        
    }
}</pre>
İşte bu kadar. Bu bizim <em><strong>controller</strong></em>'ımız. Sayfamızı oluşturacak temel iskelet bu aslında. Adının da bir önemi yok. Şimdi route oluşturacağız. Route oluşturmak için yorum satırlarını kullanıyoruz. <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >/**</pre>  ile başlayıp <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >@Route</pre>  ekliyoruz. Serimizin bir önceki <a href="https://www.trkodlama.com/makaleler/php-symfony-frameworku-ile-calisirken-phpstorm-kullaniyoruz-9178.html">makalesinde</a> kurmuş olduğumuz PHP Annotations eklentisi sayesinde otomatik olarak tamamlıyor zaten PHP Storm. Fakat tamamlarken size birden fazla alternatif sunabilir. <strong>FrameworkExtraBundle</strong>'ı seçmeye dikkat edin. Bu oldukça önemlidir. Son olarak da parantez içine "/tur" yazalım ve bitirelim:

<img class="aligncenter size-full wp-image-9184" src="https://www.trkodlama.com/wp-content/uploads/2017/02/symfony-4.png" alt="" width="520" height="380" />

Oto tamamlama burada çok önemli. Oto tamamlamayı kullanmak zorundasınız. Farkettiyseniz hemen <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >use</pre> komutunu ekledi sayfanıza. Bu sayede sınıfımızın son hali şu şekilde oldu:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * Created by PhpStorm.
 * User: trkodlama
 * Date: 16.02.2017
 * Time: 18:38
 */

namespace AppBundle\Controller;

use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;

class TurController
{
    /**
     * @Route("/tur")
     */
    public function showAction(){

    }
}</pre>
Çok güzel! Artık bir sayfamız çalışıyor. Projenizin ana dizini 404 hatası vermeye devam ederken <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >/tur</pre> adresine giderseniz artık boş bir sayfa ile karşılaşacaksınız. Bu da böyle bir sayfanızın olduğunu gösteriyor :)
<h2>Ekrana Çıktı Oluşturalım</h2>
Daha önce dediğim gibi controller'ın amacı sayfayı oluşturmak. Controller'ın bir kuralı var oda Symfony Response nesnesini kullanarak return yapmalısınız.

Return olarak çıktınızı html, json vs olarak rahatlıkla oluşturabilirsiniz.

Şu aşamada işleri biraz basit tutalım: <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >return new Response</pre>. <em>Response</em> sınıfı <strong>HttpFoundation</strong> komponentinden geliyor. Tabii ki yine oto tamamlamanının bizim yerimize tamamlamasına izin veriyoruz; bu sayede gerekli gördüğü namespace'i projemize hemen ekliyor. Aksi halde problemlerle karşılaşabiliriz:

<img class="aligncenter size-full wp-image-9185" src="https://www.trkodlama.com/wp-content/uploads/2017/02/symfony-5.png" alt="" width="619" height="541" />

Vee şimdi ekrana <strong>İki tekerli yoldaşlarımız</strong> yazdırıyoruz. Buyrun sınıfımızın son hali:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * Created by PhpStorm.
 * User: trkodlama
 * Date: 16.02.2017
 * Time: 18:38
 */

namespace AppBundle\Controller;

use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Symfony\Component\HttpFoundation\Response;

class TurController
{
    /**
     * @Route("/tur")
     */
    public function showAction(){
        return new Response('İki tekerli yoldaşlarımız');
    }
}</pre>
İşte Bu Kadar!

Bir dosya ve bir fonksiyon ile sayfamızı oluşturduk. Bu iş bu kadar kolay. Anasayfanızı tekrar açın ve yenileyin. Tabii ki çalışmayacak çünkü aslında /tur adresini açmalıydınız :) Vuhuu! Symfony ile hazırlamış olduğunuz ilk sayfaya "Merhaba" deyin. Çok basit değil mi?

Serimizin bir sonraki makalesinde dinamik URL'ler oluşturmayı göreceğiz.

Sevgilerimle,