---
ID: 366
post_title: PHP 5.4 ile Neler Değişti?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-5-4-ile-neler-degisti-366.html
published: true
post_date: 2012-03-17 04:04:33
---
Merhaba arkadaşlar,

Bu yazımda PHP 5.4 ile yeni eklenen ve kaldırılan fonksiyonları ve özellikleri anlatıyorum.

1 Mart 2012 tarihinde PHP ekibi PHP 5.4'ü resmen yayınladı. Yeni gelen PHP 5.4 ile 100'ün üzerinde güvenlik açığı kapatılırken oldukça iyi bir kaç özellik eklenmiş.
<blockquote>Bu makaleyi yazma sebebim PHP'nin bundan sonra desteklediği ve desteklemediği şeyleri göstermek içindir.</blockquote>
<h2><span>PHP 5.4 - </span>KALDIRILAN ÖZELLİKLER</h2>
<ol>
	<li><strong>break()</strong> ve <strong>continue()</strong> fonksiyonları değişkenler üzerinde işlem yapmayacak.</li>
	<li><strong>safe_mode</strong> bundan sonra desteklenmeyecek</li>
	<li><strong>register_globals</strong> ve <strong>register_long_arrays</strong> silindi.</li>
	<li><strong>Magic Quotes</strong> silindi.</li>
</ol>
<h2><span>PHP 5.4 - </span>KALDIRILAN FONKSİYONLAR</h2>
<ol>
	<li>define_syslog_variables()</li>
	<li>import_request_variables()</li>
	<li>session_is_registered()</li>
	<li>session_register()</li>
	<li>session_unregister()</li>
	<li>mysqli_bind_param()</li>
	<li>mysqli_bind_result()</li>
	<li>mysqli_fetch()</li>
</ol>
<h2><span>PHP 5.4 - </span>KALDIRILAN EKLENTİLER</h2>
<ol>
	<li>sqlite</li>
</ol>
Şimdi PHP 5.4 ile gelenlere bakalım
<h2><span>PHP 5.4 - </span>EKLENEN ÖZELLİKLER</h2>
<ol>
	<li>Varsayılan karakter seti UTF-8</li>
	<li>İkili Gösterim</li>
	<li>session.upload yol gösterici</li>
	<li><a title="PHP 5.4 ve Dizilerdeki Yenilik" href="http://www.trkodlama.com/php/php-5-4-ve-dizilerdeki-yenilik-348.html" target="_blank">Dizilerin gösterimleri</a></li>
	<li>Oturum durumları</li>
	<li>Dosya yükleme takibi</li>
	<li>vs.</li>
</ol>
<h2><span>PHP 5.4 - </span>EKLENEN FONKSİYONLAR</h2>
<ol>
	<li>hex2bin()</li>
	<li>http_Response_codes()</li>
	<li>get_declared_traits()</li>
	<li>getimagesizefromstring()</li>
	<li>trait_exists()</li>
	<li>header_register_callback()</li>
	<li>class_uses()</li>
	<li>session_status()</li>
	<li>session_register_shutdown()</li>
	<li>mysqli_error_list()</li>
	<li>mysqli_stmt_error_list()</li>
</ol>

<h2><span>PHP 5.4 - </span>REZERVE EDİLEN YENİ İSİMLER</h2>
<ol>
	<li>trait</li>

	<li>callable</li>

	<li>insteadof</li>
</ol>

Bunlar anladığım kadarıyla PHP 5.4'deki yeni özellikler ve kaldırılan özellikler. Fakat hata yapmış olabilirim. Eğer hatalı gördüğünüz bir kısım olursa lütfen beni uyarın. Yeni eklenen özellikler ile ilgili mesaj yazmaya devam edeceğim.

Umarım faydalı olur bu haliyle de, kolay gelsin,

<strong>Güncelleme:</strong> <a href="http://www.phpr.org/php-5-4-ile-gelen-yeni-ozellikler/" target="_blank">Bu sayfadan</a> daha detaylı bilgilere ulaşabilirsiniz.