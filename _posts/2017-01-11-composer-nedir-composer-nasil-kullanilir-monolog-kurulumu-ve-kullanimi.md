---
ID: 6071
post_title: >
  Composer Nedir? Composer Nasıl
  Kullanılır? Composer ile Monolog
  Kurulumu
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/composer-nedir-composer-nasil-kullanilir-monolog-kurulumu-ve-kullanimi-6071.html
published: true
post_date: 2017-01-11 23:12:13
---
Merhaba arkadaşlar,

Composer projelerinizde kütüphaneleri otomatik olarak indirip kuran bir araçtır. Öyle basit bir ayar dosyası ile kütüphaneleri her seferinde indirip kurma zahmetinden sizi kurtarır. Ayrıca isterseniz onların otomatik olarak güncellenmesini de sağlar. Bu nedenle oldukça kullanışlı bir araç.
<h1>Composer Windows Kurulumu</h1>
Bu yazıda Composer'ı Windows için kuruyorum. Fakat isterseniz <a href="https://getcomposer.org/" target="_blank">Composer web sitesinde</a> diğer işletim sistemlerinde kurulumu ile ilgili detaylı bilgiye ulaşabilirsiniz.

Composer'ın indirme sayfası için <a href="https://getcomposer.org/download/" target="_blank">buraya</a> tıklayın veya <a href="https://getcomposer.org/Composer-Setup.exe">buraya</a> tıklayarak direkt indirmeye başlayabilirsiniz. İndirdiğiniz dosyayı çalıştırın ve yüklemeye başlayın.

<img class="aligncenter size-full wp-image-6072" src="http://www.trkodlama.com/wp-content/uploads/2017/01/composer-setup.png" alt="" width="499" height="388" />

Bu ekrana geldiğinizde <strong>php.exe</strong>'nin bulunduğu dizini seçin. Composer kurulumu otomatik olarak bulmaya çalışacaktır fakat bulamazsa lütfen siz yerini gösterin. Daha sonra kurulumu tamamlayın.
<h1>Composer Temel Kullanımı</h1>
Composer'a kullanacağımız kütüphaneleri ve versiyonlarını composer.json dosyası ile bildiriyoruz. Dosyanın formatı şöyledir olmalıdır:
<pre class="lang:default decode:true ">{
    "require": {
        "monolog/monolog": "^1.22"
    }
}</pre>
&nbsp;

Peki monolog kütüphanesini nasıl kuracağız? CMD'yi çalıştırın ve <strong>cd</strong> komutuyla proje dizininize gidin.
<pre class="lang:default decode:true ">composer require monolog/monolog</pre>
&nbsp;

Bu sayede Monolog'u kurmuş olacaksınız projenize... Oldukça basit değil mi?

Umarım işinize yarar, kolay gelsin dilerim