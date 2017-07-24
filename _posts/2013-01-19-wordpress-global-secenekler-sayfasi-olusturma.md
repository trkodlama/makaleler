---
ID: 1454
post_title: >
  WordPress Global Seçenekler Sayfası
  Oluşturma
author: Oral ÜNAL
post_excerpt: "wp_options tablosu site adı, açıklaması, slogan, site adresi gibi sitenizle ilgili bütün bilgileri hafızasında tutar. Bütün bu bilgileri <strong>get_option()</strong> fonksiyonunu kullanarak rahatlıkla çekebilirsiniz. Tek yapmanız gereken fonksiyonun içine ilgili alanın adını yazmanız. Örneğin <strong>get_option('home) </strong>size anasayfanızın URL'sini verecektir. Fakat WordPress yeni bunların yanına yeni seçenekler eklemenize müsade etmiyor. Kaldı ki bu makale ile bu problemi rahatlıkla aşacağız. Bu makale WordPress yönetici panelinize yeni bir sayfa oluşturacak ve sayfa sayesinde kendi global seçeneklerinizi kaydedebileceksiniz."
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-global-secenekler-sayfasi-olusturma-1454.html
published: true
post_date: 2013-01-19 01:55:10
---
Merhaba,

WordPress en hızlı yoldan çok etkili ve gösterişli web siteleri oluşturabilmemiz için muhteşem bir platform haline geldi. Ve WordPress yaptığı bütün işleri sadece 11 veritabanı tablosu ile hallediyor. wp_options bu tablolardan yalnızca bir tanesi.

Bu tablo site adı, açıklaması, slogan, site adresi gibi sitenizle ilgili bütün bilgileri hafızasında tutar. Bütün bu bilgileri<b> </b><strong>get_option()</strong> fonksiyonunu kullanarak rahatlıkla çekebilirsiniz. Tek yapmanız gereken fonksiyonun içine ilgili alanın adını yazmanız. Örneğin <strong>get_option('home) </strong>size anasayfanızın URL'sini verecektir.

Fakat WordPress yeni bunların yanına yeni seçenekler eklemenize müsade etmiyor. Kaldı ki bu makale ile bu problemi rahatlıkla aşacağız. Bu makale WordPress yönetici panelinize yeni bir sayfa oluşturacak ve sayfa sayesinde kendi global seçeneklerinizi kaydedebileceksiniz.

<hr />

<h2>Ne Elde Edeceğiz?</h2>
Eğer Twitter kullanıcı adınızı kaydedip saklamak istiyorsanız bu yazıyı iyice okuyun. Yazının sonunda <strong>get_option('twitter')</strong> ile Twitter kullanıcı adınızı çekebilir olacaksınız.

<hr />

<h2>Kodlama</h2>
İlgili kod bloklarını aşağıda görebilirsiniz. Adım adım neler yapmanız gerektiğini aşağıda anlatıyorum. Aşağıdaki kod bloklarını aktif temanızın <strong><em>functions.php</em> </strong>dosyasına eklemeniz yeterli olacaktır. En alta sırayla ekleyebilirsiniz.

<hr />

<h2><span>Adım 1</span> Yönetici Paneline Menüyü Ekleyelim</h2>
Bu kod yönetici paneline hazırladığımız sayfayı görmemizi sağlayacak linki menüye ekleyecek:

<pre class="lang:php decode:1 " >add_action('admin_menu', 'global_secenekleri_ekle');  </pre>

<hr />

<h2><span>Adım 2</span> Şimdi Formu Oluşturacak Fonksiyonu Tanımlayalım</h2>
Bu kod ile formu oluşturacak fonksiyonu tanılıyoruz:

<pre class="lang:php decode:1 " >function global_secenekleri_ekle()  
{  
    add_options_page('Global Se&ccedil;enekler', 'Global Se&ccedil;enekler', 'manage_options', 'functions','global_secenekler');  
} 
</pre>

<hr />

<h2><span>Adım 3</span> Formu Tanımladık Şimdide Formu Hazırlayalım</h2>

<pre class="lang:php decode:1 " >&amp;lt;?php  
function global_secenekler()  
{  
?&amp;gt;  
    &amp;lt;div class=&amp;quot;wrap&amp;quot;&amp;gt;  
        &amp;lt;h2&amp;gt;Global Se&ccedil;enekler&amp;lt;/h2&amp;gt;  
        &amp;lt;form method=&amp;quot;post&amp;quot; action=&amp;quot;options.php&amp;quot;&amp;gt;  
            &amp;lt;?php wp_nonce_field('update-options') ?&amp;gt;  
            &amp;lt;p&amp;gt;&amp;lt;strong&amp;gt;Twitter Kullanıcı Adı:&amp;lt;/strong&amp;gt;&amp;lt;br /&amp;gt;  
                &amp;lt;input type=&amp;quot;text&amp;quot; name=&amp;quot;twitter&amp;quot; size=&amp;quot;45&amp;quot; value=&amp;quot;&amp;lt;?php echo get_option('twitter'); ?&amp;gt;&amp;quot; /&amp;gt;  
            &amp;lt;/p&amp;gt;  
            &amp;lt;p&amp;gt;&amp;lt;input type=&amp;quot;submit&amp;quot; name=&amp;quot;Submit&amp;quot; value=&amp;quot;Se&ccedil;enekleri Kaydet&amp;quot; /&amp;gt;&amp;lt;/p&amp;gt;  
            &amp;lt;input type=&amp;quot;hidden&amp;quot; name=&amp;quot;action&amp;quot; value=&amp;quot;update&amp;quot; /&amp;gt;  
            &amp;lt;input type=&amp;quot;hidden&amp;quot; name=&amp;quot;page_options&amp;quot; value=&amp;quot;twitter&amp;quot; /&amp;gt;  
        &amp;lt;/form&amp;gt;  
    &amp;lt;/div&amp;gt;  
&amp;lt;?php  
}  
?&amp;gt; </pre>

Bu formun sadece tek bir özelliği temsil ettiğine dikkat edin. Eğer birden fazla özellik tanımlamak istiyorsanız aşağıdaki iki adımı inceleyin:

<strong>1 -</strong> Tekil bir isimle yeni bir metin kutusu oluşturun. Mesela Facebook sayfanızın da linkini kullanmak istiyorsanız aşağıdaki kodu ekleyin Twitter kutusunun altına:

<pre class="lang:php decode:1 " >&amp;lt;p&amp;gt;&amp;lt;strong&amp;gt;Facebook Sayfası Linki:&amp;lt;/strong&amp;gt;&amp;lt;br /&amp;gt;  
    &amp;lt;input type=&amp;quot;text&amp;quot; name=&amp;quot;fb_link&amp;quot; size=&amp;quot;45&amp;quot; value=&amp;quot;&amp;lt;?php echo get_option('fb_link'); ?&amp;gt;&amp;quot; /&amp;gt;  
&amp;lt;/p&amp;gt; </pre>

<strong>2 -</strong> "page_options" isimli gizli input'u güncellemeniz gerekecek. O inputun içine fb_link'i de ekleyeceğiz:

<pre class="lang:html decode:1 " >&amp;lt;input type=&amp;quot;hidden&amp;quot; name=&amp;quot;page_options&amp;quot; value=&amp;quot;twitter,fb_link&amp;quot; /&amp;gt;</pre>

Gördüğünüz gibi seçenek isimlerini aralarına virgül(,) koyarak yazdık. Eğer burayı doğru tanımlamazsanız ilgili seçenek çalışmayacaktır.

<hr />

<h2>Kullanımı</h2>
Bu kodları <em>functions.php</em>'ye yazdıktan sonra yönetici panelinde ilgili menüyü göreceksiniz. O linke tıkladıktan sonra hazırladığımız formu göreceksiniz. Formu doldurun twitter kullanıcı adınızı yazın ve kaydedin.

Artık Twitter seçeneğiniz veritabanında kayıtlıdır. Tema dosyalarınızda get_option('twitter') yazdığınızda kaydettiğiniz Twitter kullanıcı adı gelecektir.

Umarım faydalı olur, kolay gelsin,