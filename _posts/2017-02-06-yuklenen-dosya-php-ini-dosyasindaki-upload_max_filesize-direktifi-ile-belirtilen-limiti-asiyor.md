---
ID: 6548
post_title: >
  Yüklenen Dosya php.ini Dosyasındaki
  upload_max_filesize Directive İle
  Belirtilen Limiti Aşıyor
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress/yuklenen-dosya-php-ini-dosyasindaki-upload_max_filesize-direktifi-ile-belirtilen-limiti-asiyor-6548.html
published: true
post_date: 2017-02-06 20:53:11
---
Her <strong>WordPress</strong> kullananın hemen hemen karşısına çıkmış bir hatadır sanırım. Bilmeyenler olabilir diye biraz teknik detaylara inerek anlatacağım bu makaleyi.

PHP çalıştıran sunucularda PHP için gerekli ayarların saklandığı bir dosya vardır. Bu dosyanın adı <strong>php.ini </strong>dosyasıdır. Bu dosyada PHP'nizin çalışmasını doğrudan ilgilendiren direktifler vardır. Bunlar zaman aşımı, maksimum dosya boyutu, eklentiler vs. olabilir.

Bu hatayı almanızın sebebi ise maksimum dosya boyutu limitinizin üzerinde bir dosya yüklemeye çalışmış olmanızdır. Netice itibari ile bu hatayı alırsınız:
<blockquote>Yüklenen Dosya php.ini Dosyasındaki upload_max_filesize Directive İle Belirtilen Limiti Aşıyor</blockquote>
Bu hatayı yeni bir eklenti eklerken, yeni bir tema kurulumu yaparken veya yeni bir resim/video/ses gibi medya yüklerken alabilirsiniz. Bunun sebebi yüklemeye çalıştığınız dosya boyutu PHP.ini dosyanızdaki tanımlanan limitten fazla olmasıdır. Bu sorunun çözümü için iki farklı durum söz konusu:
<h2>Durum 1 - Hosting Kullanıyorsanız</h2>
Eğer ki bir hosting kullanıyorsanız PHP.ini ayarlarına doğrudan müdahale etme imkanınız muhtemelen bulunmuyordur. Bu nedenle aşağıdaki kodları <strong>.htaccess</strong> dosyanızın içine yapıştırabilirsiniz. Fakat her hosting <strong>.htaccess</strong> dosyasının içine PHP direktiflerinin girilmesini kabul etmez. Eğer ki <strong>.htaccess</strong> dosyanızın içerisine aşağıdaki direktifleri girdikten sonra <strong>500 Internal Server Error</strong> hatası alıyorsanız veya yine aynı hatayı almaya devam ediyorsanız hosting firması .htaccess dosyasından beri PHP direktifleri tanımlamanıza izin vermiyor olabilir. Bu durumda lütfen hosting sağlayıcınızla iletişime geçin.
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">php_value upload_max_filesize 50M # Dosya boyutunuza göre ayarlayın..
php_value post_max_size 500M # Üstteki değer ile aynı yapın
php_value max_execution_time 600 # Yüklediğiniz dosyanın işlevine göre ayarlayın. Hata aldıkça artırabilirsiniz.
php_value max_input_time 600 # Bir üst satırdaki durum aynen geçerlidir.</pre>
<h2>Durum 2 - Kendi Sunucunuzsa</h2>
Eğer sunucu kendi sunucuzsa isterseniz PHP.ini dosyasını direk modifiye edebilirsiniz:
<pre class="prettyprint lang-ini" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">; Her satırı tek tek bulup düzenlemelisiniz.
upload_max_filesize = 64M
post_max_size = 64M
max_execution_time = 300
max_input_time = 300</pre>
<strong>PHP.ini</strong> dosyasında bu değişiklikleri yaptıktan sonra <strong>Apache</strong>'yi veya hangi web sunucusunu kullanıyorsanız yeniden başlatmayı ihmal etmeyin. Fakat bu yöntemi denemeden önce <strong>Durum 1</strong>'i denemenizi öneririm. Eğer kendi sitelerinizi barındırıyorsanız PHP direktiflerine .htaccess dosyasından izin verin. Eğer farklı kişilere ait siteler barındırıyorsanız ihtiyacınız olan sürenin sonunda ayarlarınızı eski haline getirip işleminizi sonlandırabilirsiniz.

Umarım faydalı olmuştur, kolay gelsin dilerim,