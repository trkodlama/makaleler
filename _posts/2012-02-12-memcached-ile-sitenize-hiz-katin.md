---
ID: 293
post_title: Memcached ile Sitenize Hız Katın
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/memcached-ile-sitenize-hiz-katin-293.html
published: true
post_date: 2012-02-12 02:52:30
---
En son üzerinde çalıştığınız PHP/MySQL projenizi nihayet yayınladınız. Bu çok iyi. Fakat projenizin çok fazla SQL sorguları çalıştırdığından sizin beklediğiniz gibi hızlı olmadı. Bundan dolayı bu aşırı yüklenmelerin altından kalkamayacağınızı düşünmeye başladınız. Bu konuda da büyük ihtimalle haklısınız.

Bu makalede, web sitenizin hızını nasıl muhteşem bir şekilde artırabileceğinizi göstereceğim. Ayrıca bu aşırı yüklenme derdinizi ortadan kaldıracağım. Kodlarınızla veritabanınız arasına bir önbellek katmanı koyarak veritabanınızı biraz arka plana atacağız hep beraber.

<strong>Memcached'e Giriş</strong>
Modern web siteleri ve web uygulama çok fazla miktarda veriyi kullanır ve artık tek sayfada 20 ve hatta 30 SQL sorgusu alışıldık bir durum halini aldı. Bu rakamı çok fazla ziyaretçi bulunan bir web sitesi için gereken sayı ile çarpın, sayfaların oluşturulması saniyeler alabilir ve sonra kullanıcıya gönderilir.

Performansımızı artırmak için kullanacağımız aracın adı <strong>Memcached</strong>. Bu yüksek performanslı bir önbellekleme sistemidir. Memcached'den aşağıdaki durumlarda bize yardımcı olmasını isteyeceğiz:
- V değerini K anahtarı ile sakla
- K anahtarlı V değerini getir

Memcached'i modern Linux dağıtımlarına kurmak için aşağıdaki komutlar işimizi görecektir:
Ubuntu :

[sourcecode]sudo apt-get install memcached[/sourcecode]

Gentoo :

[sourcecode]sudo emerge install memcached[/sourcecode]

Redhat :

[sourcecode]sudo yum install memcached[/sourcecode]

Kurulduktan sonra sunucu her yeniden başlatıldığında Memcached'de otomatik olarak başlatılacaktır. Memcached için ayrılan hafızayı ve bir kaç özelliği daha ayar dosyasından(/etc/memcached.conf) değiştirebilirsiniz. 64Mb varsayılan olarak ayrılan hafızadır. Ayrıca bu ayar dosyasında Memcached'in bağlı olduğu IP adresini ve portu görebilirsiniz. Varsayılan değerler(127.0.0.1 ve 11211) standart bir kurulum için ideal değerlerdir.

<strong>Memcached'e PHP ile Erişim</strong>
PHP scriptlerinizde verileri saklamak ve onlara erişmek istiyoruz. Bu da Memcached'e PHP ile erişmemiz gerekiği anlamına geliyor. Bu nedenle PHP'nin "Memcached" eklentisini kuracağız. Aslında bu da bir PECL eklentisidir. Kaldıki PECL eklentilerinin kurulumu çok basittir, ihtiyacımız olan eklentiyi aşağıdaki komut ile kurabilirsiniz:

[sourcecode]sudo pecl install memcache[/sourcecode]

PHP'de Memcache ile ilgili iki eklenti mevcut: "Memcache" ve "Memcached"(Sondaki "d" harfine dikkat edin). Bu ikisi birbirine oldukça benzerler fakat küçük farklılıkları var. Bu makalede basit olan Memcache'i kullanacağız. Kurulum bittikten sonra eklenti aktif olacak ve Memcache ile ilgili fonksiyonları PHP scriptlerimizde kullanabilir olacağız.

Memcached ile önbelleklediğimiz verileri sadece SQL sorgularından "Insert" ve "Update" komutlarını kullandığımız zaman güncellememiz gerekecek. Onun dışında önbelleklediğimiz verileri güncellememize gerek yoktur. Her yeni girdi de ve güncellemede hem MySQL hemde Memcached'i güncelleyeceğiz. Fakat veriyi okurken sadece Memcached'i kullanacağız. MySQL kullanmamıza gerek kalmayacak. Eğer Memcached'de bir hata ile karşılaşırsak MySQL'i kullanacağız.

Öncelike scriptimizin en üstünde bir memcached'e giden bir bağlantı oluşturmalıyız:

<pre class="lang:php decode:1 " >// Bağlantı sabitleri
define('MEMCACHED_HOST', '127.0.0.1');
define('MEMCACHED_PORT', '11211');

// Bağlantı
$memcache = new Memcache;
$uygunMu = $memcache-&amp;gt;connect(MEMCACHED_HOST, MEMCACHED_PORT);</pre>

Bu işlemle Memcache sunucusu ile bağlantı kurmuş olduk. Başarısız olabilir fakat başarısız bile olsa $uygunMu değişkeni sayesinde biz bunu öğrenebileceğiz.

<strong>Veriyi Önbellekleme</strong>
Artık verilerimizi yedeklemenin vakti geldi. Şimdi bir örnek yapalım. Bir sanal mağazanın ürün düzenleme sayfasını düzenleyelim. Bu mağazada her ürün sadece aşağıdaki bilgileri içeriyor:
- id
- ad
- açıklama
- fiyat

Ürün düzenleme sayfasında illaki INSERT veya UPDATE SQL komutları kullanılıyordur. Şimdi varsayalım ki bu sayfa da INSERT ile ürün ekleyeceğiz. Aşağıdaki kodda ürünü MySQL ekliyoruz. Eğer ekleme işlemi başarılı olursa product_xx anahtarları ile X dizisini değerleriyle birlikte önbellekte saklıyoruz. İşte kod:

<pre class="lang:php decode:1 " >// Değişkenleri b&uuml;t&uuml;n kontrollerden ge&ccedil;irdikten sonra vt'ye girelim
$sql = &amp;quot;INSERT INTO urunler (id, ad, aciklama, fiyat) VALUES ($id, '$ad', '$aciklama', $fiyat)&amp;quot;;
$basari= mysql_query($sql, $db);

// Verilerimizi vt'ye kayıt ettik.
// Şimdi bu verileri &ouml;nbelleğe kaydedelim
if ($basari=== true)
{
 // Bu &uuml;r&uuml;n i&ccedil;in benzersiz bir anahtar belirleyelim
 $anahtar = 'urun' . $id;

 // Şimdi de bu &uuml;r&uuml;n&uuml;n verilerini dizide toplayalım
 $urun = array('id' =&amp;gt; $id, 'ad' =&amp;gt; $ad, 'aciklama' =&amp;gt; $aciklama, 'fiyat' =&amp;gt; $fiyat);

 // &Ouml;nbellekleyelim
 $memcache-&amp;gt;set($anahtar, $urun);
}</pre>

Şimdi önbellekleme işlemini tamamlamış olduk. Unutmayın sadece SQL Insert ve Update komutlarında önbellekleme yapmanız yeterli olacaktır.

<strong>Önbellekten Veri Çekme</strong>
Eğer önbellek uygun değilse yani herhangi bir durumda çalışmazsa bu durumda tekrar MySQL'den verilerinizi çekebilirsiniz. Kısacası Memcached kullanmanızın size hiç bir zararı olmayacaktır. Hemen veri çekerken nasıl kullanacağımızı göstermek istiyorum. Diyelim ki önceki girdiğimiz üründe ürün id'si 12'ydi. Şimdide urun.php?id=12 sayfasına girdik:

<pre class="lang:php decode:1 " >$id = $_GET['id'];
// $urun değişkenimizi tanımlayalım
$urun = null;

// &Ouml;ncelikle &ouml;nbellek sunucumuz uygun mu deği mi? Onu kontrol edelim
// $uygunMu değişkeni sayfalarımızın en &uuml;st&uuml;nde &ouml;nbellek sunucuna bağlandığımız değişkendi
if ($uygunMu== true)
{
 // Şimdi daha &ouml;nce bu &uuml;r&uuml;n i&ccedil;in belirlediğimiz anahtarı tanımladık burada
 $anahtar = 'urun' . $id;

 // Şimdi &ouml;nbellek sunucumuzdan verileri &ccedil;ekelim
 $urun = $memcache-&amp;gt;get($anahtar);
 // Dizi olarak &ouml;nbelleklemiştik. Dizi olarak &ccedil;ıktımızı aldık,
 // $urun['id'], $urun['ad'], $urun['aciklama'], $urun['fiyat']
}

// $urun = $memcache-&amp;gt;get($anahtar) işlemi başarısız olursa
// hemen MySQL sorgusu burada devreye girer. Fakat başarısız olmasını gerektirecek
// bir durum genellikle ger&ccedil;ekleşmez
if (!$urun)
{
 // Burada mysql_fetch_assoc() ile veritabanından &ccedil;ekersiniz bilgilerinizi
}</pre>

Kısacası web sitesini hızlandırmak isteyen herkesin rahatlıkla kullanabileceği bir sistem. Kurulumu basit, kullanımı basit. Sitenize adapte etme kısmı biraz işkenceli olabilir. Onu da hemen halledeceğinize inancım sonsuz.

Faydalı olduğuna inanıyorum, umarım iyi bir anlatım olmuştur,
Kolay gelsin,