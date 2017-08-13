---
ID: 407
post_title: >
  PHP ile IPN Kontrollü PayPal Ödeme
  Butonu
author: Oral ÜNAL
post_excerpt: >
  Bu makalede PayPal ile sitenize nasıl
  ödeme butonu ekleyeceğinizi ve
  IPN(instant payment notification) ile bu
  gelen ödemeyi nasıl
  doğrulayacağınızı anlatıyorum. Bu
  işlemler için paypal hesabınız
  olmalıdır. Eğer yoksa nasıl
  açmanız gerektiğini yine makalede
  anlatıyorum.
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-ipn-kontrollu-paypal-odeme-butonu-407.html
published: true
post_date: 2012-03-26 13:44:03
---
Merhaba arkadaşlar, bu yazımda hep beraber bir paypal hesabı açacağız ve sitemize bir ödeme yap butonu koyacağız. Daha sonra PayPal IPN ile bu ödemenin gerçek olup olmadığını göreceğiz.
<h2>Adım 1 - PayPal Hesabı Açma</h2>
PayPal hesabı açmak için <a href="http://www.paypal.com" target="_blank">www.paypal.com</a> adresine giriyoruz. Buradan <strong>Hesap Açın</strong> butonuna tıklıyoruz.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_001.png"><img class="aligncenter size-medium wp-image-408" title="Selection_001" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_001-300x218.png" alt="" width="300" height="218" /></a>

Karşımıza gelen ekranda <strong>Bireysel</strong> başlığı altındaki <strong>Hesap açın</strong> butonuna tıklıyoruz.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_002.png"><img class="aligncenter size-medium wp-image-409" title="Selection_002" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_002-300x173.png" alt="" width="300" height="173" /></a>

Daha sonra üyelik formunu dolduruyoruz. Üyelik formunu doldurun ve email hesabınızı onaylayın. İşte bu kadar şu anda sizin de bir PayPal hesabınız var.
<h2>Adım 2 - PayPal Ödeme Butonumuzu Oluşturalım</h2>
Şimdi bir satın alın butonu oluşturalım. Bu butonu oluşturmak için PayPal'a giriş yaptıktan sonra "<strong>Kullanıcı Profili</strong>" linkine tıklamanız gerekiyor. Bu linke tıkladıktan sonra "<strong>Satış Araçlarım</strong>" linkine tıklayın ve "<strong>Online Satış Yapma</strong>" altında "<strong>Paypal düğmeleri</strong>" karşısındaki "<strong>Güncelle</strong>" linkine tıklayalım.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_005.png"><img class="aligncenter size-medium wp-image-422" title="Selection_005" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_005-300x174.png" alt="" width="300" height="174" /></a>

Karşınıza gelen sayfada "<strong>Hemen Satın Alın Düğmesi Örneği</strong>" karşısında "<strong>İşlem</strong>" linkine tıklayın ve açılan pencereden "<strong>Düğmeyi düzenle</strong>" yi seçin.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_006.png"><img class="aligncenter size-medium wp-image-423" title="Selection_006" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_006-300x213.png" alt="" width="300" height="213" /></a>

Şimdi formumuzu oluşturmaya başlayalım. Form alanlarını şu şekilde yapalım:
<ol>
 	<li><strong>Öğe Adı:</strong> TR Kodlama PayPal Denemesi</li>
 	<li><strong>Fiyat:</strong> 5,00</li>
 	<li><strong>Mağaza Hesap Numaraları:</strong> Ana e-posta adresimi kullan xxx@xxx.com'u seçin</li>
</ol>
Kalan yerlere dokunmanıza gerek yok. Daha sonra kendiniz kurcalarken karıştırabilirsiniz. Şimdi Adım 3 linkine tıklayalım.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_007.png"><img class="aligncenter size-medium wp-image-424" title="Selection_007" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_007-300x246.png" alt="" width="300" height="246" /></a>

Bu adımı da şu şekilde dolduralım:
<ol>
 	<li><strong>Müşteriniz bir iletide size özel talimatlar bildirebilir mi? </strong>Hayır</li>
 	<li><strong>Müşterinizin gönderim adresine ihtiyacınız var mı?</strong> Hayır</li>
 	<li><strong>Satın alma işlemini iptal ederlerse müşterileri bu URL'ye yönlendirin</strong> kutucuğunu aktifleştirin ve müşteri siparişden vazgeçtiği zaman gideceği adresi tanımlayın</li>
 	<li><strong>Satın alma işlemini tamamladıktan sonra müşterileri bu URL'ye yönlendirin</strong> kutucuğunu aktifleştirin ve müşteri satın alma işlemini tamamladığı zaman gideceği sayfayı tanımlayın.</li>
 	<li>Son olarak önemli kısıma geldik: <strong>Gelişmiş değişkenler tanımla</strong> kutucuğunu seçin ve kutucuğun içine şunu yazın</li>
</ol>
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">notify_url=http://www.trkodlama.com/paypal/ipn.php</pre>
<strong>ipn.php</strong> dosyamızın içeriğini ilerleyen adımlarda tanımlayacağız.

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_008.png"><img class="aligncenter size-medium wp-image-425" title="Selection_008" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_008-300x260.png" alt="" width="300" height="260" /></a>

En son olarak "<strong>Değişiklikleri Kaydet</strong>" butonuna tıklayalım. Karşımıza HTML bir kod gelecek. Bu kodu kaybetmeyelim. Hemen http://www.sizindomaininiz.com/paypal/index.html isimli bir dosya oluşturalım ve bu dosyanın içine sadece bu HTML kodu yapıştıralım. Tarayıcı aracılığı ile açalım index.html dosyasını. Şimdi şöyle bir görüntü elde etmeniz gerekiyor:

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_009.png"><img class="aligncenter size-medium wp-image-426" title="Selection_009" src="http://www.trkodlama.com/wp-content/uploads/2012/03/Selection_009-300x32.png" alt="" width="300" height="32" /></a>
<h2>Adım 3 - ipn.php Dosyasını Oluşturalım</h2>
ipn.php dosyasını oluşturmadan önce "PayPal" isimli bir veritabanı oluşturun ve şu komutu çalıştırın:
<pre class="prettyprint lang-mysql" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">CREATE TABLE paypal(
    id int(255) AUTO_INCREMENT,
    durum int(1),
    veri text,
    PRIMARY KEY (id)
)</pre>
Veritabanında <strong>paypal</strong> isimli bir de tablo oluşturduk bu komut sayesinde.

Önceki adımda notify_url isminde bir parametre ile ipn.php dosyamızın adresini vermiştik. Satın alma işlemi tamamlandığında PayPal arka planda ipn.php dosyanıza bir kaç veri POST eder. Siz bu verileri tekrar GET ile paypal'a yönlendirirsiniz. Eğer gönderdiğiniz veriler ilk başta POST ile gelen verilerle aynı ise VERIFIED yazılacak. Eğer farklıysa INVALID yazdırır. Bizde buna göre kontrol ederiz.

Ayrıca gelen verileri JSON formatında veritabanında saklayacağız.

Şimdi ipn.php dosyamızın içeriğini verelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
header("Content-type: text/html; charset=utf-8");

mysql_connect("localhost", "root", "") or die(mysql_error());
mysql_select_db("paypal") or die(mysql_error());

// PayPal tarafından POST eden verileri toplayalım ve işleyelim
// Paypal'a geri gönderirken parametrelerin en başına cmd=_notify-validate ekliyoruz
$req = 'cmd=_notify-validate';
$json = array();
foreach ($_POST as $key =&gt; $value) {
	$value = urlencode(stripslashes($value));
	if($key=="payment_status") $durum = $value; // Burada ödeme durumunu yakaladık.
	$req .= "&amp;$key=$value";
	$json[$key] = $value;
}

// Şimdi PayPal'a gidelim.
$sonuc = file_get_contents("https://www.paypal.com/cgi-bin/webscr?$req");

if ($sonuc=="VERIFIED" &amp;&amp; $durum=="Completed") {
	$json = json_encode($json);
	mysql_query("INSERT INTO paypal VALUES(NULL, 1, '$json')");
} else {
	mysql_query("INSERT INTO paypal VALUES(NULL, 0, '$json')");
}
?&gt;</pre>
Bu şekilde satın alma işlemi tamamlandıktan sonra herşeyi yani bütün verileri de inceleyebilirsiniz.
<h2>Adım 4 - PayPal Sandbox</h2>
Kendi kendinize test edebilmeniz için PayPal'ın sandbox isimli bir hizmeti var. Bu hizmet sayesinde ipn.php dosyanıza POST edilecek bütün verileri siz belirliyorsunuz. Mesela "<strong>Status</strong>" değeri "<strong>Completed</strong>" veya "<strong>Failed</strong>" olsun şeklinde. Eğer completed dışında bir değer yollarsanız ipn dosyası veri tabanınıza durum kısmında 0 olarak ekler. 0'lar başarısız olanlardır.

PayPal Sandbox'ı kullanabilmek için üye olmanız gerekmektedir. Ekstra bir üyelik. Ayrıca PayPal Sandbox ile test yaparken ipn.php dosyamızdaki
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$sonuc = file_get_contents("https://www.paypal.com/cgi-bin/webscr?$req");</pre>
kısmını aşağıdaki şekilde değiştirmelisiniz:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$sonuc = file_get_contents("https://www.sandbox.paypal.com/cgi-bin/webscr?$req");</pre>
PayPal Sandbox'a girmek için <strong><a href="http://developer.paypal.com" target="_blank">buraya</a></strong> tıklayın.
<h2>Sonuç</h2>
Lütfen sorularınızı sormaktan çekinmeyin. Herkes için faydalı olacağını düşündüğüm bir konuydu bu. Nette bulunan kaynaklar hep eski. Güncel kaynak yokluğunda iyi gider bu makale.

Kolay gelsin,

<strong>Son Güncelleme: 19 Kasım 2012 10:18</strong> (<a href="http://www.trkodlama.com/makaleler/php/php-ile-ipn-kontrollu-paypal-odeme-butonu-407.html/comment-page-1#comment-6700">Mert Doğan</a>'a teşekkürler.)