---
ID: 9991
post_title: >
  Laravel Framework Nedir Ve Özellikleri
  Nelerdir?
author: Sinan Eldem
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/laravel-framework-nedir-ve-ozellikleri-nelerdir-9991.html
published: true
post_date: 2017-08-12 16:47:10
---
<h2>Laravel Nedir ?</h2>
Laravel ihtiyaç duyulan, gelişmiş bir çok özellik ve yapıyı üzerinde barındıran, PHP ve OOP tüm nimetlerinden yararlanan, web uygulamaları geliştirmeyi sağlayan açık kaynak PHP framework’ tür.

<strong>“WEB SANATÇILARININ PHP FRAMEWORK’Ü” sloganıyla kendisini özetler ve hakkını verir.</strong>
<h3>Laravel Özellikleri</h3>
Yapısı gereği gerçekten çok sade ve temiz kod yazarak istediğiniz uygulamaları geliştirme imkanı verir.

Söz dizimi çok basit ve anlamlıdır. Alışmak için zorlanmazsınız, çabuk öğrenilebilir.

Bir kaç işlem barındıran küçük uygulamalardan, büyük kurumsal projelere kadar her türlü web uygulamasını tasarlama esnekliğine sahiptir.

OOP ve PHP nin tüm nimetlerinden yararlanır böylece güncel php özelliklerinde oop uygun şekilde çalışırız.

Diğer Laravel’i laravel yapan özellikler:
<h3>ORM</h3>
ORM Nedir önce onu açıklarsak; (Object Relational Mapping) Database ile uygulamamızda (Object-Oritented) nesnelerimiz sayesinde bağlantı kurup yönetmemizi sağlayan bir yapıdır. Klasik SQL cümleleri yazmadan nesnelerimiz üzerinden veri tabanına erişim sağlayıp kontrol edebiliyor sorgular çalıştırabiliyoruz. ORM database den bağımsız çalışır. Yani Mysql, SQLite, postgresql, MSSql, Oracle gibi bir çok database için aynı kodları kullanırsınız. Bir çok avantajı var ama burada değinmeyeceğiz.

Laravel Eloquent ORM kullanır. En gelişmiş Active Record uygulamasıdır.
<pre class="line-numbers"><code class="language-php">class Message extends Eloquent {}
$message = Message::find(1);</code></pre>
Gördüğünüz gibi çok basit kullanılabilir bir yapısı vardır. Sizi bir çok tanımlama yapmak uzun cümleler yapılar kurmaktan kurtarır.

Messages (“s” Siz table belirtmez iseniz çoğul hali olan “s” takısını ekleyerek database de tablo seçer) tablosundan id = 1 olan mesajı getirir.
<h3>Blade Template</h3>
Blade adı verilen template engine sahiptir. Uygulamanıza yine çok kolay ve sade şekilde arayüzle bütünleştirebiliriz. Öğrenilmesi yine kolaydır,temiz ve dinamik arayüzler hazırlayabilirsiniz html ve php kodları içinde savaş vermezsiniz.
<h3>Route</h3>
Müthiş bir route (yönlendirme) mekanizması vardır. Yorulmadan temiz URL elde eder api ler için uygun erişim yönlendirmeleri yapabilirsiniz. Php yapısında yabancı olmadığınız şekilde.
<pre class="line-numbers"><code class="language-php">Route::get('users', function()
{
   return 'Users!';
});</code></pre>
Burada ister yönlendirmelerinizi yapabilir ister filtrelerden kontrollerden geçirebilir ister Controller class larınıza yönlendirebilirsiniz. Hatta burada bu fonksiyonda uygulamanızın gerçekleştireceği işlemleri dahil controller class lara gerek kalmadan gerçekleştirebilirsiniz. (Önerilmez)
<h3>Migrations (Sürüm Kontrolü, Göçler)</h3>
Veri tabanı sürüm kontrol sistemidir. Artisan Komut Satırı ile uygulamanızın veritabanına şemalar ekleyebilir düzenleyebilirsiniz. Veri tabanı yönetim sistemine gitmeden sisteminizdeki veritabanınızı oluşturmaya yada güncellemeye yarayan yapı. Örneğin uygulamanızı başka bir ortama taşıdınız, veri tabanını oluşturmaya çalışmaktansa uygulamanızda ki hali hazırdaki yapıyı çalıştırarak sistemi hazır hale getirmiş oluyoruz.
<h3>Unit Test (Birim Test)</h3>
Uygulamanızı test etmek için birim testler oluşturup çalıştırmamızı sağlar. Artisan komut satırıyla hazırladığımız testleri çalıştırabiliriz.
<h3>Automatic Pagination (Otomatik Sayfalandırma)</h3>
Laravel bizim yerimize sayfalama sistemini düşünmüş ve bizi zahmete sokmadan el atmış. Kolay şekilde kullanabilir istersek değiştirebiliriz.
<h3>Modüler paket yönetimi ve composer</h3>
Composer, uygulamanızın üçüncü parti paketlerini kontrol edip hızlı şekilde ekleyip yönetmeyi sağlar. Composer ile bağımlılıklarınızı paketlerinizi dert etmez tek tek uğraşmak yerine çok kolay bir şekilde dahil edebilirsiniz.
<h3>Performans</h3>
Cache mekanizmaları sunar. Redis ile bütünleşmiş bir yapısı var adeta evlat edinmişcesine sahip çıkar, bünyesine katmıştır. Projenize redis dahil etmek için ekstra uğraşmanıza gerek yoktur.Çok hızlı ve basit şekilde yapılandırabilirsiniz.

Dahili olarak auth, filter gibi bir çok yapıyı içinde barındırıyor. Bunu yine kendi yapısına uygun ve basit şekilde sunar. Hemen hemen her uygulamada auth mekanizması olur ve bunu yapmak için ekstra çabaya gireriz. İşte laravel bunu da pas geçmemiş çok güzel bunun gibi yapılarda sunmuş.

Bir çok Symfony bileşeni üzerine kurulmuştur.

Güvenli, hızlı, sitenizi ayağa kaldırmak çok kolaydır.

Tek komutla sitenizi aktif hale veya yapım aşamasına alma gibi seveceğiniz bir çok özelliği daha mevcuttur.
<h3>Topluluk</h3>
Bir yapıda en büyük özelliklerden birisi de bana göre topluluktur. Başınız sıkıştığında yardım alabileceğiniz, danışacağınız, müthiş örnekler ve çözümler bulabilmeniz gibi bir çok yardımı dokunur.

Çok hızlı büyüyen topluluğa sahiptir. Henüz genç bir freamwork sayılır. Bu sebeple örneğin bir codeigniter kadar topluluğa ve aşinalığa sahip değildir. Ancak çok hızlı büyümektedir. Popülerliği her geçen gün artmaktadır. Türkiye ‘ dede kabul görmüş hızla atan bir kitlesi var, ayrıca iş ilanlarında da laraveli görmek mümkün. Türkiye’ de Sinan Eldem’ in çok iyi çalışmaları var. Katkılarından dolayı kendi adıma da teşekkürü borç bilirim. çok iyi bir Türkçe döküman hazırlanmış. Ayrıca resmi sitesinde , yerli ve yabancı forumlarına yine ulaşabilirsiniz. Ulaşmakla yetinmeyip sizde katkıda bulunursanız çok daha başka güzel olur:)

Döküman sıkıntısı yaşamaz, çok kısa zamanda öğrenebilir yardımlar alabilirsiniz.
<h3>Laravel ile Yapılan Siteler</h3>
Laravel ile oluşturulmuş uygulamaların yer aldığı <a href="http://builtwithlaravel.com/">http://builtwithlaravel.com/</a> siteden gerçek çalışmalara göz atabilirsiniz.

Sunucu Gereksinimleri
<ol>
 	<li>PHP &gt;= 5.5.9</li>
 	<li>OpenSSL PHP Extension</li>
 	<li>PDO PHP Extension</li>
 	<li>Mbstring PHP Extension</li>
 	<li>Tokenizer PHP Extension</li>
 	<li>MCrypt PHP Eklentisi</li>
</ol>
<h2>Laravel Kurulum</h2>
<h4>Composer ile kurulum</h4>
<pre class="command-line" data-host="trkodlama" data-user="root"><code class="language-bash">composer create-project laravel/laravel laravel-test-proje1 --prefer-dist</code></pre>
Bulunduğunuz dizinde “laravel-test-proje1″ klasöre laraveli indirip kuracaktır.

<strong>Github – Git ile Kurulum</strong>

Github adresi: <a href="https://github.com/laravel/laravel">https://github.com/laravel/laravel</a>

Git clone: <a href="https://github.com/laravel/laravel.git">https://github.com/laravel/laravel.git</a>

Kurulum yapmak istediğimiz dizine gelerek
<pre class="command-line"><code class="language-bash">git clone  https://github.com/laravel/laravel.git</code></pre>
ile git reposundan kendi localimize çekiyoruz. Sonra composer ile laravel in bağımlılıklarını yüklememizi sağlar.(Biliyoruz ki artık composer kullanıyoruz laravel bağımlılıklar, paketler için)
<pre class="line-numbers"><code class="language-bash">composer install</code></pre>
Evet laravel freamwork edinmiş olduk artık. Sunucunuzdan laraveli indirdiğiniz dizine gelirseniz, public klasöründe laravel in çalıştığını görürüz. Bizi laravel logosunun karşlıladığı bir sayfa görüyorsak her şey yolundadır.

Benim örneğimden “http://localhost/testLaravel/” girdiğimde laravel dizinleri gösterilir.

Not: sunucunuzun “app/storage” dizinine yazma izni vermemiz gerekebilir.

Laravel nedir, özellikleri nedir, neden laravel, laravel nasıl kurulur gibi temel bilgileri edindik Sonraki yazılarda laraveli detaylı işleyip uygulamalar geliştireceğiz. Şahsen kendi projelerim ve profesyonel hayatta da etkin şekilde kullanacağım.
<h2>Tavsiyem</h2>
Hangi freamwork iyidir, hangi freamwork onu döver gibi konulara girmeden sadece laravel açısından kendi gözlem ve önerilerimi aktarayım. Ancak freamwork karşılaştırmaları avantaj, dezavantajları alternatifleri, kullanım alanları gibi bilgilerin olacağı başka bir yazıya yer verebiliriz.

Gerçekten öğrenilmesi kolay, söz dizimi, yapısı, basitliği kodlarla sanat yapar gibi çalışmanıza imkan vermesiyle kendisine bağlıyor mest ediyor. Çalışmaktan mutluluk duyuyorsunuz. Projenizde her şey düzenli, yerli yerinde oluyor. Yapının içinde boğulmuyorsunuz aradığınızı buluyorsunuz. Kodlar sizinle konuşur gibi olduğu için dilinden anlıyorsunuz:) Geri döndüğünüzde abi burada ne yapmıştım demiyorsunuz(tabi yinede geliştirmenize göre değişebilir) :) Dahili bir çok yapı bulundurmakla kalmıyor bunları karmaşadan ve hantallıktan uzak şekilde sunuyor. Auth, Redis bunlardan sadece bazıları. Projenizi çok kısa zamanda ayağa kaldırır vakit kaybetmezsiniz. Eski usul kod geliştirmeyi unutur modern kabul görmüş programcılığa adım atarsınız. ORM, OOP, Template Engine,Redis,Composer,Unit Test vb yapılara aşina olursunuz.Artılarını çok yakından hissedersiniz. Uygulamanızı kısa zamanda ayağa kaldırır, her uygulama geliştirmede alt yapılar oluşturmak zorunda kalmazsınız. Her şey çok basit çok yalındır. Düşündüğünüz bir çok şey etrafında toplanmıştır.

En azından denemenizde göz atmanızda fayda olacağını düşünüyorum. Bir başlarsanız daha tadından yenmeyeceğini fark eder tavsiyelerime katılırsınız.