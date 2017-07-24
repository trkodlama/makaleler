---
ID: 211
post_title: >
  PHP mail() Fonksiyonuyla HTML Mail
  Gönderme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/php-mail-fonksiyonuyla-html-mail-gonderme-211.html
published: true
post_date: 2011-07-12 22:59:17
---
Merhaba arkadaşlar,

Bugün sizlere PHP'nin mail fonksiyonuyla nasıl HTML mail gönderebileceğinizi anlatacağım.. Hatırlarsanız daha önce html mail göndermeyi PHP ile SMTP Mail Yollama yazımda anlatmıştım. Bu sefer sunucunun kendi ayarlarıyla yani mail() fonksiyonuyla nasıl göndereceğinizi anlatıyorum, daha doğrusu bu işlemi yapan bir fonksiyonu paylaşıyorum. Fonksiyon aşağıdaki gibidir:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
/**
 * HTMLMail()
 *
 * Mail fonksiyonu ile HTML mail göndermenizi sağlar
 *
 * @param mixed $gidecekMail
 * @param mixed $gonderenAd
 * @param mixed $gonderenMail
 * @param mixed $konu
 * @param mixed $mesaj
 * @return
 */
function HTMLMail($gidecekMail,$gonderenAd,$gonderenMail,$konu,$mesaj) {
	$headers  = "MIME-Version: 1.0\n";
	$headers .= "Content-type: text/html; charset=UTF-8\n";
	$headers .= "X-Mailer: PHP\n";
	$headers .= "X-Sender: PHP\n";
	$headers .= "From: $gonderenAd&lt;$gonderenMail&gt;\n";
	$headers .= "Reply-To: $gonderenAd&lt;$gonderenMail&gt;\n";
	$headers .= "Return-Path: $gonderenAd&lt;$gonderenMail&gt;\n";
	mail($gidecekMail,$konu,$mesaj,$headers);
}</pre>
Fonksiyonun kullanımı basittir. HTMLMail(alıcının email adresi, gönderenin adı, gönderenenin email adresi, konu, mesaj) formatındadır. Yani gönderenin adı ve gönderenin mail adresini istediğiniz şekilde düzenleyebilirsiniz. Alıcının email adresi kısmına da kime göndermek istiyorsanız onun email adresini yazın.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// no-reply@trkodlama.com'dan gidiyormuş gibi info@trkodlama.com adresine mail gönderelim
HTMLMail("info@trkodlama.com", "TR Kodlama / no-reply", "no-reply@trkodlama.com", "Konumuz Yok", "&lt;p&gt;Mesajımız deneme olsun, deneme mesajı ve örnektir.&lt;/p&gt;&lt;p&gt;Bunlarda paragraflarımız&lt;/p&gt;");</pre>
Umarım açıklayıcı olmuştur, herkese iyi günler