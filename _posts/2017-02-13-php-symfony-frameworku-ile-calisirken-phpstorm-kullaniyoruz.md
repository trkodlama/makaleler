---
ID: 9178
post_title: 'PHP Symfony Framework&#8217;ü ile Çalışırken PhpStorm Kullanıyoruz'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/symfony-3/php-symfony-frameworku-ile-calisirken-phpstorm-kullaniyoruz-9178.html
published: true
post_date: 2017-02-13 19:55:26
---
Bu seriyi anlatırken ben PhpStorm kullanıyor olacağım. Çünkü PhpStorm Symfony framework'ü ile çalışan en iyi PHP IDE'si. Bu IDE'yi bu şekilde överken herhangi bir para da almıyorum fakat PhpStorm çalışanları beni izleyip bana bir kahve ısmarlamak isterlerse hayır demem.

Neyse, PhpStorm çok güçlü bir IDE. 6 yıldır kullanıyorum Güven Atbakan arkadaşım sayesinde. Fakat ücretsiz bir program değil. Yine de bu seriyi incelerken kullanabilirsiniz tabii ki. Çünkü deneme sürümü sunuyorlar size. Web sitesine gidip indirebilirsiniz.

Öncelikle indirmemiz gereken iki eklenti var PhpStorm'a. Bu eklentiler:
<ul>
 	<li>PhpStorm Symfony Eklentisi <a href="https://plugins.jetbrains.com/idea/plugin/7219-symfony-plugin">plugins.jetbrains.com/idea/plugin/7219-symfony-plugin</a></li>
 	<li>PhpStorm PHP Annotations Eklentisi <a href="https://plugins.jetbrains.com/idea/plugin/7320-php-annotations">plugins.jetbrains.com/idea/plugin/7320-php-annotations</a></li>
</ul>
Peki ne işimize yarayacak bu eklenti?
<h2>Symfony Eklentisi</h2>
Öncelikle bu eklenti Symfony 2 ve Symfony 3 desteği var, bunu belirtelim. Symfony eklentisi ile Symfony framework'ü ile geliştirme yapmak o kadar kolaylaşıyor ki. Herşey aslında otomatikleşiyor. Bütün işlemlerinizi bir kaç tıklama ile halledebiliyorsunuz neredeyse. Gerek fonksiyon isimlerini tamamlama olsun, gerek bağımlılıklarınızı otomatik olarak sınıflarınıza dahil etme olsun ve daha nicesi. Aynı zaman da Php Annotations eklentisi ile de uyumlu çalışıyor.

Kullandığınız sınıflar, fonksiyonlar, terimler vs. yani her yazdığınız yaml, xml ve php dosyalarından referans göstererek girebilmenizi sağlıyor.

Doctrine sınıfını destekliyor. Template motoru olan ve Symfony'de kullanacağımız Twig desteği mevcut. Router işlemlerinizi kolaylaştırır ve Router'larınızı Twig dosyalarınızda rahatlıkla kullanabilmenizi sağlıyor.

Bilinmeyen bir route, template, service veya asset girdiğinizde sizi uyarır. Daha bir çok özelliği mevcut.
<h2>Symfony Eklentisi Kurulumu</h2>
Symfony eklentisini kurmak için PhpStorm menüsünden şu adımı takip edin:
<blockquote><strong>File &gt; Settings &gt; Plugins </strong>kısmına gidin ve orada aşağıdaki butonlardan <strong>Browse repositories...</strong> butonuna tıklayın. Karşınıza gelen arama kutusuna <strong>Symfony Plugin</strong> yazın ve gelen sonuçlardan <strong>Symfony Plugin</strong>'e tıklayın. Sağ taraftaki yeşil Install butonuna tıklayın ve kurulum bitti.</blockquote>
<h2><strong>PHP Annotations Eklentisi</strong></h2>
Bu eklenti ise Symfony'de özellikle Route tanımlarken ihtiyacınız olacak bir eklentidir. Bu eklenti sayesinde Route'larınızı yorum satırında tanımlarken PhpStorm'un Oto-Tamamlama ve Referans gösterme hizmetleri aktif olur ki buna gerçekten ihtiyacımız var.
<h2>PHP Annotations Eklentisi Kurulumu</h2>
Yukarıdaki adımların aynısını takip edin fakat arama kutusuna bu sefer <strong>PHP Annotations</strong> yazın ve öyle arayın.

Eveeeet, PhpStorm'umuz da artık kullanıma hazır. Artık yeni bir Symfony projesi oluşturabilirsiniz. İlk Symfony projemizi oluşturalım:
<h2>Yeni Symfony Projesi Oluşturma</h2>
Yeni Symfony projesi oluşturmak için <strong>File &gt; New Project</strong> tıklıyoruz. Sol tarafta projemizin ne projesi olduğunu soruyor. Orada Symfony'yi buluyoruz ve tıklıyoruz. Bize bazı seçenekler de sunuyor. Onlar da şöyle:
<ul>
 	<li><strong>Location</strong>: Projemiz için bir dizin belirlememizi istiyor.</li>
 	<li><strong>Symfony Version</strong>: Kullanacağımız Symfony versiyonunu seçmemizi istiyor. Biz bu seri de <strong>Symfony 3.2.3</strong> kullanacağız.</li>
 	<li><strong>Demo Application</strong>: Demo bir uygulama kurup kurmayacağımızı soruyor. Normal de işaretsiz bırakacağız bunu. Fakat şöyle bir örnek uygulamayı incelemek isterseniz bu kutuyu işaretleyip göz atabilirsiniz.</li>
 	<li><strong>Path to PHP executable</strong>: <strong>php.exe</strong> dosyanızı seçerek göstermenizi istiyor.</li>
</ul>
<strong>Bitti!</strong> Boş bir Symfony projesi de oluşturmuş olduk. Önceki <a href="https://www.trkodlama.com/makaleler/symfony-kurulumu-9162.html">makalemizde</a> paylaşmış olduğumuz CMD komutuyla symfony projemizi çalıştıralım ve http://localhost:8000 adresinden çalıştırın bakalım. Biraz heyecanlısınız ama azıcık. İlerleyen makalelerde neleri nasıl yaptığınızı anladığınız da daha çok heyecanlanacaksınız. Sevgilerimle,