---
ID: 9981
post_title: >
  PSR Nedir? Türkçesi PHP Standartları
  Tavsiyeleri Nedir?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/psr-nedir-turkcesi-php-standartlari-tavsiyeleri-nedir-9981.html
published: true
post_date: 2016-08-10 11:13:45
---
Eğer hırslı bir PHP Geliştirici iseniz, yolunuz mutlaka PSR kısaltması ile kesişmiştir. Bu yazı hazırlanırken PSR-0, PSR-1, PSR-2, PSR-3, PSR-4 ve PSR-7 olmak üzere kabul edilmiş 6 standart tavsiyesi bulunuyor. Bunlara ilave olarak PSR-6 Caching Interface (Önbellek Arayüzü) standardı onay ve PSR-5 PHPDoc Standard (PHPDoc Standardı), PSR-8 Huggable Interface (Sarılabilir Arayüzü), PSR-9 Security Disclosure (Güvenlik Bilgilendirmesi) ve PSR-10 Security Advisories (Güvenlik Önerileri) standartları taslak aşamasında bekliyor.

Bu yazıda kabul edilmiş standartların neler olduğunu ve neden dikkate almanız gerektiğini incelemeye çalışacağım.
<h2>Kısa Özet</h2>
PHP kod yazmak için hiçbir zaman tam anlamıyla merkezileşmiş bir standarta sahip olmadı. Büyük yazılım ekiplerine sahip şirketler ve birden fazla kod tabanını idame ettiren kişiler projeleri için isimlendirme ve kodlama stilleri hazırladılar. Bazıları <a href="http://pear.php.net/manual/en/standards.php">PEAR</a> veya <a href="http://framework.zend.com/manual/1.12/en/coding-standard.html">Zend Framework</a> gibi iyi dökümante edilmiş standartları baz almaya çalışırken, diğerleri sıfırdan birşeyler üretmeye çalıştılar.
<h3>The Framework Interoperability Group (PHP-FIG)</h3>
2009 yılındaki php|tek konferansında, çeşitli projeleri temsil eden kişiler projeleri arasında ortaklaşa çalışmanın yollarını tartıştılar. Bunun üzerine kod tabanları arasında bir grup standarda uyulması gündeme geldi.

Bir süre kendilerine “PHP Standards Group” dedikten sonra, bu ismin grubun amacını doğru yansıtmadığını düşündükleri için Framework Interoperability Group (FIG) olarak yollarına devam ediyorlar. Grubun ismi kod çatılarına atıfta bulunsa da çeşitli projeleri temsil eden birçok geliştirici oylayıcı üye olarak gruba kabul edildi.
<h4>PHP-FIG’in Amacı</h4>
PHP-FIG proje temsilcileri arasında bir dialog ortamı oluşturarak, beraber çalışmanın yollarını aramaktadır. Bu zamana kadar oluşan dialoglar sonucunda 6 tavsiye kabul edilmiştir. Bu tavsiyeler isteyen herkes tarafından uygulanabilmekle birlikte, kimse için zorunlu değildir.
<h2 data-fontsize="18" data-lineheight="27">PSR-0: Autoloader Standard (Otomatik Yükleme Standardı) ve PSR-4 Improved Autoloading (Gelişmiş Otomatik Yükleme)</h2>
<blockquote>PSR-0 tekrar kullanılabilir kod için büyük bir adımdır.</blockquote>
Her dosyanın başında ihtiyaç duyduğunuz tüm dosyalar için include veya require tanımlaması yaptığınızı hatırlıyor musunuz? Çok şükür bu kullanım PHP 5 ile birlikte gelen sihirli <code>__autoload()</code> fonksiyonu sayesinde değişti. PHP 5.1.2 ‘nin bize tanıştırdığı <a href="http://php.net/manual/en/function.spl-autoload.php"><code>spl_autoload()</code></a> ve <a href="http://php.net/manual/en/function.spl-autoload-register.php"><code>spl_autoload_register()</code></a> sayesinde otomatik yükleme çok daha kolay ve dinamik hale geldi.

Otomatik yükleme fonksiyonu ne kadar iyi olsa da, mevcut kod yapılarında nasıl uygulanması gerektiğini tanımlamıyordu. A kütüphanesi ile B kütüphanesinin klasör ve sınıf adı yapısına bakış açısı birbirinden farklı olabiliyor. Fakat siz iki kütüphaneyi de kullanmak istiyorsunuz.

Tüm olasılıkları kapsayacak üzgün bir otomatik yükleme (autoloader) sınıfı yazmak hızlı bir şekilde kaosa dönüşüyordu. Sınıf isimlerini ve nerede olmaları gerektiğini tanımlayan bir standart olmadan otomatik yükleme bir rüyadan ibaretti.

<a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md">PSR-0</a> “Ortak çalışan otomatik yükleme için uyulması gereken zorunlu gereksinimler” i tanımlayan bir standart önerisidir. <a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md">PSR-4</a>‘ün yayınlanması ile birlikte 21 Ekim 2014’de miladını doldurmuştur.

Eğer bir proje PSR-0 veya PSR-4 standardını izliyorsa ve serbest bileşenleri varsa, kolayca ihtiyaç duyduğunuz bileşenleri alıp, vendor klasörünüze koyabilir ve PSR-0 veya PSR-4 uyumlu bir otomatik yükleyici ile o bileşenleri yükleyerek kullanabilirsiniz. Hatta daha iyisi izin verin bunu sizin yerinize <a href="http://www.teknomavi.com/yazilim/php/composer-paket-yoneticisi-nedir-nasil-kurulur-nasil-kullanilir/">Composer</a> yapabilir.

PSR-4, PSR-0’a ilave olarak kütüphane ile gelen dosyaların nereye koyulacağını da belirtmektedir.
<h2>PSR-1: Basic Coding Standard (Temel Kodlama Standardı)</h2>
<a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md">PSR-1</a> en basit düzeyde kodlama standartlarına odaklanmaktadır. Çok detaylı olmaktan kaçınmakta, bu sayede daha büyük bir kitle tarafından benimsenmesi hedeflenmektedir.
<h3>PSR-1 kapsamındaki maddelerden bazıları;</h3>
<ul>
 	<li>Dosyalar sadece <code>&lt;?php</code> ve <code>&lt;?=</code> kullanmalıdır.</li>
 	<li>PHP dosyaları sadece UTF-8 without BOM kodlamasına sahip olmalıdır.</li>
 	<li>Dosyalar ya bir sembol tanımlamalı (Sınıf, Fonksiyon, Sabit vs.) ya da bir yan etki ( çıktı üretmek, .ini ayarlarını değiştirmek vs.) üretmelidir. Fakat ikisini birden yapmamalıdır.</li>
 	<li>Namespace ve sınıflar PSR-0 veya PSR-4 standardını izlemelidir.</li>
 	<li>Sınıf isimleri <code>StudlyCaps</code> şeklinde tanımlanmalıdır.</li>
 	<li>Sınıf sabitleri tamamı büyük harf olacak şekilde tanımlanmalıdır.</li>
 	<li>Metod isimleri <code>camelCase</code> şeklinde tanımlanmalıdır.</li>
</ul>
Bu temel kurallar isimlendirmelere ve dosya yapısına odaklanmaktadır. Bu sayede paylaşılan PHP kodları görünüm ve davranış bakımından aynı olacaktır.
<h2>PSR-2: Coding Style Guide (Kodlama Stil Rehberi)</h2>
<a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md">PSR-2</a>, PSR-1 tarafından tanımlanmış temel kodlama standartlarını genişletir. Amacı paylaşılan kodların tek bir şekilde yazılmasını sağlayan bir rehber olmaktır.

Grup üyelerinin temsil ettikleri projeler üzerinde yapılan detaylı inceleme sonucunda en büyük kitleyi kapsayan özellikler temel olarak alınmıştır.
<h3>PSR-2 kapsamına genel bakış;</h3>
<ul>
 	<li>Kod PSR-1 kapsamında belirtilen kurallara uymak zorundadır.</li>
 	<li>Girintiler için 4 boşluk kullanılır. Tab değil</li>
 	<li>Satır uzunluklarında katı sınır olmamalıdır. Yumuşak sınır 120 karakterdir. Satırlar mümkünse 80 karakter veya daha kısa olmalıdır.</li>
 	<li>namespace tanımlamasından sonra bir boş satır bırakılmalıdır. use tanımlamalarından sonra da bir satır boşluk olmalıdır.</li>
 	<li>Sınıfların açılış ve kapanış parantezleri alt satırda olmalıdır.</li>
 	<li>Metodların açılış ve kapanış parantezleri alt satırda olmalıdır.</li>
 	<li>Tüm metodlarda görünürlük ( <code>public</code>, <code>protected</code>, <code>private</code> ) tanımlaması bulunmak zorundadır <code>abstract</code> ve <code>final</code> tanımlamaları görünürlük tanımlamasından önce, <code>static</code> ise görünürlük tanımlamasından sonra olmalıdır.</li>
 	<li>Kontrol yapısı anahtar kelimelerinden sonra bir boşluk olmalıdır. metod ve fonksiyon çağrılarında boşluk olmamalıdır.</li>
 	<li>Kontrol yapılarının açılış parantezleri aynı satırda, kapanış parantezleri alt satırda olmalıdır.</li>
 	<li>Kontrol yapılarının açılış parantezlerinden sonra ve kapanış parantezlerinden önce boşluk olmamalıdır.</li>
</ul>
PSR-2 kurallarının tamamına <a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md">fig-standards</a> reposundan ulaşabilirsiniz.

PSR-2 standartları günümüzde özellikle github üzerindeki açık kaynak repolarda aktif şekilde kullanılmaya başladı. Bunun en büyük avantajı repo’ya katkıda bulunan kişilerin gönderdiği kodların diff görünümlerinin daha düzgün olması ve herkesin özel kod formatı yüzünden kodun gereksiz yere değişmemesi olduğunu düşünüyorum. Hali hazırda popüler olan tüm editörler PSR-2 uyumlu kod formatlama seçenekleri sunuyorlar. Bu sayede geliştiriciler tek bir seçenek ile evrensel formata uygun kod yazabiliyorlar.
<h2>PSR-3: Logger Interface (Loglayıcı Arayüzü)</h2>
PSR-3 paylaşılmış bir loglayıcı arayüzünü tanımlar ve <a href="http://tools.ietf.org/html/rfc5424">The Syslog Protocol (RFC 5424)</a> tarafından belirlenmiş 8 seviyeyi (debug, info, notice, warning, error, critical, alert, emergency) içermektedir.

Bu sekiz Syslog seviyesi metod adı olarak tanımlanmıştir ve her biri <code>$mesaj</code> ve <code>$içerik</code> olmak üzere iki parametre kabul etmektedir. $içerik parametresi, $mesaj parametresi ile düzgün aktarılamayan değerleri taşımaktadır.
<blockquote>PSR-3 gibi bir ortak arayüz standartı; frameworkler, kütüphaneler ve diğer uygulamaların bu ortak arayüze tür dayatma (<a href="http://php.net/manual/tr/language.oop5.typehinting.php">typehint</a>) yapması sayesinde, geliştiricilerin tercih ettikleri uygulamayı seçmelerine olanak sağlamaktadır.</blockquote>
Başka bir deyişle, <a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md">PSR-3</a> uyumlu bir loglama bileşeni, rahatlıkla PSR-3 uyumlu başka bir bileşen ile değiştirilebilmektedir. Bu loglayıcı entegrasyonları ile log çağrıları arasında maksimum ortak çalışmayı garanti altına almaktadır.

Hali hazırda birçok popüler framework’le birlikte gelen <a href="https://github.com/Seldaek/monolog">Monolog</a> PSR-3 destekli olarak çalışmaktadır.
<h2>PSR-7: HTTP Message Interface (HTTP Mesaj Arayüzü)</h2>
HTTP mesajları internetin en temel bileşenidir. Bir web sayfasını yüklemek için bir talep (request) yapar ve karşılığınca bir cevap (response) alırsınız. Bir php sitesinin çalışabilmesi için de aynı şekilde gelen talebin anlamlandırılması ve talebe uygun cevabın hazırlanarak müşteriye ulaştırılması gerekir. <a href="https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-7-http-message.md">PSR-7</a> ile birlikte frameworklerin ve harici bileşenlerin tek bir mesaj arayüzü kullanması ve bu sayede frameworkler ve bileşenler arasındaki tekrar kod kullanılabilirliği arttırılması hedeflenmiştir.

PSR-7 paylaşılmış HTTP mesaj arayüzlerini tanımlar. Bu PSR kapsamında 7 adet arayüz sağlanmaktadır.

Bu arayüzlerden ve kullanım amaçlarından kısaca bahsetmek gerekirse;
<ul>
 	<li>MessageInterface: Gelen ve giden mesajların tanımlandığı temel arayüzdür.</li>
 	<li>RequestInterface: MessageInterface’i genişleterek talep mesajlarının arayüzünü oluşturur.</li>
 	<li>ResponseInterface: MessageInterface’i genişleterek cevap mesajlarının arayüzüdür.</li>
 	<li>ServerRequestInterface: RequestInterface’i genişleterek sunucu tarafından yapılan taleplerde kullanılan mesaj parametrelerinin tanımlanmasını ve kullanılmasını sağlayan bir arayüzdür.</li>
 	<li>StreamInterface: Mesajların gövdesini oluşturur. Evrensel ve esnek bir yapı olması için, düz bir metin bile olsa akış olarak tanımlanır ve kullanılır.</li>
 	<li>UploadedFileInterface: Mesajlarla birlikte yüklenen dosyaları tanımlayan arayüzdür. <code>$_FILES</code> değişkeni yüklenen dosyanın yükleme metoduna göre farklılık gösterebildiğinden, bu nesne dosya içeriğini standart hale getirir.</li>
 	<li>UriInterface: Talebin yapıldığı URI’yi yönetmek için kullanılır.</li>
</ul>
Hali hazırda, Pek çok bileşen tarafından kullanılan Guzzle, versiyon 6 ile birlikte PSR-7 altyapısını kullanmaya başladı. Ayrıca Symfony, bünyesindeki popüler HttpFoundation bileşenin PSR-7 uyumluluğunu sağlamak için PSR-7 Bridge adında ek bir bileşen yayınladı.