---
ID: 6496
post_title: 'WordPress&#8217;de Sadece İçerik Kısmını Gösteren Sayfa Oluşturma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpressde-sadece-icerik-kismini-gosteren-sayfa-olusturma-6496.html
published: true
post_date: 2017-02-04 00:52:18
---
Başlığı nasıl atacağımı bilemedim fakat demek istediğim olay şuydu. Bir sayfa oluşturun ve bu sayfada mevcut temanızın üst kısmı(header), alt kısmı(footer), yan kenar alanı(sidebar) ve menüler olmasın. Sadece sayfa içeriğiniz gözüksün. Adım adım bunu uygulayalım:
<h2>Adım 1 - WordPress Sayfa Teması Oluşturun</h2>
Bilgisayarınızda "page-bossayfa.php" isimli bir dosya oluşturun ve aşağıdaki kodu bu dosyanın içine kopyalayıp-yapıştırın. Sonra kaydedin tabii ki :)
<pre class="lang:php decode:true prettyprint lang-php" title="bos_sayfa.php">&lt;?php
/**
 * Template Name: Boş Sayfa
 * Bu tema sayesinde yeni sayfa oluşturduğunuzda sadece içeriğinizi göreceksiniz.
 */
?&gt;
 
&lt;html &lt;?php language_attributes(); ?&gt; class="no-js"&gt;
&lt;head&gt;
    &lt;meta charset="&lt;?php bloginfo( 'charset' ); ?&gt;"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1"&gt;
    &lt;?php /*wp_head();*/ ?&gt;
    &lt;?php 
    /**
     * temanızın css ve javascriptleri ayrıca 
     * wp'nin diğer head içerisine eklediği kodları eklemek isterseniz
     * yukarıdaki yorum satırlarını kaldırıp wp_head() fonksiyonunu çalıştırmalısınız..
     */
&lt;/head&gt;
&lt;body&gt;
&lt;?php
    while ( have_posts() ) : the_post();   
        the_content();
    endwhile;
?&gt;
&lt;?php wp_footer(); ?&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>
Bu dosyanın indirme linkini aşağıda paylaştım.
<h2>Adım 2 - Bu Dosyayı WordPress Tema Klasörünüzün İçine Yükleyin</h2>
Bu oluşturduğunuz sayfayı FTP programınızı kullanarak wp-content/themes/tema_klasorunuz/ içine yükleyin.
<h2>Adım 3 - Yeni Sayfa Oluşturun Temanızı Seçerek</h2>
WordPress yönetici panelinize girerek yeni sayfa oluşturun. <strong>Sayfa Özellikleri</strong> kısmında <strong>Şablon</strong> listesinde <strong>Boş Sayfa</strong> ismi ile yeni temanızı göreceksiniz. Onu seçin ve sayfanızı oluşturun. Bu kadar basit

<img class="aligncenter size-full wp-image-6501" src="https://www.trkodlama.com/wp-content/uploads/2017/02/bossayfa.png" alt="" width="319" height="332" />

Bu temanın çalışan bir örneğini şu adreste görebilirsiniz <a href="https://www.trkodlama.com/demo/bos-sayfa-demosu">https://www.trkodlama.com/demo/bos-sayfa-demosu</a>
<h2>Sonuç</h2>
Bu işlemi sayfa olarak değilde yazı olarak da yapabilirsiniz. O zaman dosya adınız conten-bossayfa.php olmalı. Ayrıca farklı bir yazı tipi oluşturmalısınız. Bununla ilgili de belki ilerde bir yazı daha yazabilirim.

https://www.trkodlama.com/wp-content/uploads/2017/02/page-bossayfa.rar