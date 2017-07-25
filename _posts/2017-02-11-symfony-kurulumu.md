---
ID: 9162
post_title: PHP Symfony Framework Kurulumu
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/symfony-kurulumu-9162.html
published: true
post_date: 2017-02-11 22:27:18
---
Symfony'e bir giriş yapmazsak olmazdı. Bildiğiniz veya duyduğunuz üzere <strong>Symfony</strong> gelmiş geçmiş en zor framework. Şaka şaka. Symfony çok zor diye ünlenmiş fakat işin aslı öyle değil. Belki de eskiden zordu, bilemiyorum.

Symfony eğer severseniz ve birazcık uğraşırsanız o kadar basit olur ki tahmin edemezsiniz. Symfony sayesinde API veya web uygulamalarınız oldukça güçlü ve iyi tasarlanmış bir kodlamaya sahip olacaktır. Biraz zorlaşmaya başladığında ve zoru başardığınızda inanın gerçekten iyi bir geliştirici olma yolunda ilerliyorsunuz demektir. Çünkü nesne yönelimli PHP'ye çok daha hakim olacaksınız.
<h2>Symfony Framework'ü ve Bileşenleri</h2>
Pekala, Symfony nedir? İlk olarak symfony bileşen yani php kütüphanelerinin bir araya gelmiş halidir. Yani 30 civarı küçük kütüphaneden oluşmaktadır. Bu da şu demek oluyor ki Symfony'yi Symfony ile geliştirilmemiş web sitelerinizde kütüphane amaçlı da kullanabilirsiniz. Benim favori kütüphanem <strong>Finder</strong>; dizinlerde derinlemesine dosya arama konusunda çok iyi.
<h2>Symfony Kurulumu</h2>
İlk Symfony projemize oluşturmaya doğru yavaş yavaş ilerleyelim. Öncelikle <a href="http://symfony.com/download">Symfony.com</a> adresine gidin ve "Download" a tıklayın. İlk işimiz Symfony Installer'ı indirmek. Kullandığınız işletim sistemine Symfony Installer'ı nasıl indireceğiniz gösterilmiş. Ben Win kullanıyorum ve onu göstereceğim:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">php -r "file_put_contents('symfony', file_get_contents('https://symfony.com/installer'));"</pre>
<blockquote><strong>Dikkat!</strong> Eğer <strong>php</strong> komutu bulunamadıysa <strong>php.exe</strong> dosyasının tam adresini yazmalısınız. Örneğin: <pre class="class:prettyprint lang-plain_text data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >C:\\Users\\trkodlama\\php7\\php.exe</pre>  kullanın php yerine.</blockquote>
Şimdi ilk projemizi oluşturalım:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">php symfony new trkodlamaSymfonyDersleri</pre>
Bu komutla beraber Symfony framework ü ve bileşenler indirilmeye başlanıyor.
<blockquote><strong>Not: </strong>trkodlamaSymfonyDersleri sadece kurulum dizininin adını belirtiyor. Başka bir önemi yoktur.</blockquote>
Şimdi oluşturduğunuz klasörün içine girin. Burada oluşturulmuş olan dosyaları ve dizinleri göreceksiniz. Symfony framework'ünü bileşenleri <em>vendor/<strong> </strong></em>dizini içerisinde görebilirsiniz. Şimdi projemizi çalıştıralım:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">php bin/console server:run</pre>
Az önce uyardığım gibi bin/console için bulunamadı hatası alabilirsiniz. Bu durumda bin/console adresinin tam yolunu girmeniz gerekiyor. Bu komutu başarılı bir şekilde çalıştırdıktan sonra http://localhost:8000 adresinden projenize bir giriş yapabilirsiniz. Aslında Apache veya Nginx web sunucularını da kullanabilirsiniz fakat bu şekilde çalışmak daha kolay bence. 8000 portundan çalışan web sunucunuzu durdurmak için komut istemini kapatın veya Ctrl+C 'ye basın.

Kurulumu başarılı bir şekilde bitirdik. Bir sonraki makalede ilk sayfamızı oluşturmayı göreceğiz.

Bu makale serisini <a href="https://knpuniversity.com/screencast/symfony/start-project">knpuniversity.com</a> adresini kaynak olarak kullanıyorum. Güzel ve akıcı bir video serisi var. İngilizce hakimiyetiniz var ise eğer oradan devam etmenizi şiddetle öneriyorum.