---
ID: 81
post_title: 'PHP&#8217;de Cookie&#8217;ler'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/phpde-cookieler-81.html
published: true
post_date: 2010-08-04 08:20:21
---
Çerezler internet kullanıcılarının bilgisayarlarına web siteleri tarafından bırakılan bir nevi kimlik işlevi gören küçük dosyalardır. Web siteleri bu kimliklerle sizleri tanır.
Mesela projenizde "Beni Hatırla" seçeneği sunmak istiyorsunuz; bu işlemde sizin yardımınıza çerezler yetişir. Tabii ki farklı yollarla bu işlemi oturum(session) ve veritabanı ikilisiylede halledebilirsiniz ama çerezleri kullanmak kadar basit bir yöntem varken buna neden ihtiyaç duyarsınız ki?
<strong>Çerez Oluşturma</strong>
PHP ile çerezlerimizi <code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">setcookie()</code> fonksiyonu ile kuruyoruz. Hemen bir örnekle açıklayalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php setcookie($ad, $deger, $bitis, $dizin, $domain, $guvenli); ?&gt;</pre>
<ul>
 	<li><strong>$ad</strong> - çerezin adı. Örn: "kullaniciAdi"</li>
 	<li><strong>$deger</strong> - çerezin değeri. Örn: "sagoral"</li>
 	<li><strong>$bitis</strong> - UNIX zamandamgası şeklinde olmalı ve çerezin geçerlilik süresini belirdir. Örnek: time()+3600 Yani bir saat</li>
 	<li><strong>$dizin</strong> - çerezin geçerli olacağı dizini belirtirsiniz.
Mesela eğer dizin "/" olarak ayarlanmışsa bütün sitede geçerli olacaktır bu çerez fakat "/forum/" şeklinde ayarlansaydı çerez sitenizin trkodlama.com/forum/ adresinde geçerli olacaktı.
Bu bölümü doldurmak isteğe bağlıdır. "/" değeri varsayılandır.</li>
 	<li><strong>$domain</strong> - çerezin geçerli olacağı alanları belirlersiniz.
Örneğin ".trkodlama.com" olarak belirlerseniz çerez altdomain.trkodlama.com, deneme.trkodlama.com adreslerinde de geçerli olur.
Bir diğer şekli ise "www.trkodlama.com" şeklinde belirlerseniz sadece ana alan adı ve alt klasörlerde çalışır çerez. www.trkodlama.com/forum/, www.trkodlama.com/makaleler/ gibi..</li>
 	<li><strong>$guvenli</strong> - boolean tipidir. Sitenizin güvenli(https) sunucu olup olmadığını bildirir. Varsayılan ayarı false'dur</li>
</ul>
Şimdi örnek bir çerez oluşturalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/* setcookie() fonksiyonunu bu şekilde kullanmak ile
** setcookie("kullaniciAdi", "sagoral", time()+3600, "/", ".trkodlama.com", false);
** bu şekilde(alt satırdaki) kullanmak arasında hiçbir fark yoktur. */
setcookie("kullaniciAdi", "sagoral", time()+3600);
?&gt;</pre>
kullaniciAdi isimli bir çerez oluşturduk ve değerini desagoral yaptık. Bu çerez time()+3600 dediğimiz için bir saat süreyle geçerli olacaktır.

<strong>Uyarı: setcookie() fonksiyonu</strong> her zaman HTML içerik gönderilmeden önce kullanılmalıdır. Aksi taktirde "<a title="Warning: Cannot modify header information" href="http://www.trkodlama.com/makaleler/php/warning-cannot-modify-header-information-78.html">Warning: Cannot modify header information...</a>" şeklinde bir uyarıyla karşılaşırsınız. Gerekli çözüm linkte yazıyor.
<h3>Bir Yıllık Çerez Oluşturalım</h3>
Şimdiki çerezimizi bir yıllık oluşturalım bakalım time() değerini nasıl değiştiriyoruz?
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
setcookie("kullaniciAdi", "sagoral", time()+(60*60*24*365));
?&gt;</pre>
Bu şekilde çerezin bitiş süresi tam bir yıl sonrası oldu.
<h3>Çerezi Okuma</h3>
Şimdi çerez değerini çekelim. "<strong>kullaniciAdi</strong>" adlı bir çerez oluşturduk ve buna "<strong>sagoral</strong>" değerini atadık. Şimdi sayfalarımızda bu değeri nasıl çağırabiliriz ona bakalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Oldukça kolaydır
echo $_COOKIE["kullaniciAdi"];
?&gt;</pre>
Şu anda "sagoral" adını ekrana yazdırmış olduk.
<h3>Çerezi Silme</h3>
Sıradaki işlemimiz ise değerini "sagoral" olarak atadığımız çerezi silme:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
setcookie("kullaniciAdi", "", time()-3600);
?&gt;</pre>
Burada dikkat etmemiz gereken nokta şu, eğer çerezi eklerken bitiş süresini <strong>time()+3600</strong> olarak belirlediysek silerkende <strong>time()-3600</strong> olarak yazmamız gerekiyor. Aksi taktirde problem yaşayabilirsiniz.

Kolay gelsin,