---
ID: 112
post_title: PHP ile SMTP Mail Yollama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/php-ile-smtp-mail-yollama-112.html
published: true
post_date: 2011-03-16 09:00:30
---
Merhaba arkadaşlar,

Bu makalemde nasıl php'nin mail() fonksiyonunu kullanmadan smtp bilgilerni kullanarak nasıl mail yollayacağınızı anlatacağım.

Öncelikle PHPMailer_v5.1 versiyonunu buradan indiriyoruz. Daha sonraki yeni bir sayfa oluşturuyoruz ve içine aşağıdaki kodu yapıştırıyoruz:
<pre class="prettyprint" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php

require_once('class.phpmailer.php');
$mail = new PHPMailer(true);

$mail-&gt;IsSMTP(); // sınıfı smtp ile kullanacağımızı tanımlıyoruz

try {
  $mail-&gt;Host= "mail.sitenizinadı.com"; // SMTP sunucu
  $mail-&gt;SMTPDebug = 2; // SMTP için sunucuyu test ediyoruz
  $mail-&gt;SMTPAuth= true;
  $mail-&gt;Port       = 587; // Genellikle smtp 587'dir.
  $mail-&gt;Username   = "isminiz@sitenizinadı.com"; // SMTP kullanıcı adınız
  $mail-&gt;Password   = "şifreniz"; // SMTP kullanıcı şifreniz
  $mail-&gt;AddReplyTo('isminiz@sitenizinadı.com', 'Oral ÜNAL'); //mail adresiniz ve isminiz
  $mail-&gt;AddAddress('isim@siteadı.com', 'John Doe'); // Mail yollanacak adres ve ismi
  $mail-&gt;SetFrom('isminiz@sitenizinadı.com', 'Oral ÜNAL');
  $mail-&gt;Subject = 'smtp mail yollamak'; //Mailimizin konusu
  $mail-&gt;AltBody = 'İstersek bir alt açıklama girebiliriz.';
  $mail-&gt;MsgHTML(file_get_contents('icerik.html')); //HTML olarak mail yollamak istersek
  $mail-&gt;AddAttachment('images/phpmailer.gif');      // Dosya eklemek
  $mail-&gt;AddAttachment('images/phpmailer_mini.gif'); // dosya eklemek
  $mail-&gt;Send();
  echo "Mesaj gönderildin";
} catch (phpmailerException $e) {
  echo $e-&gt;errorMessage();
} catch (Exception $e) {
  echo $e-&gt;getMessage();
}</pre>
Tek yapmanız gereken budur. Artık sunucunuz üzerinden SMTP mail rahatlıkla yollayabilirsiniz. Türkiye'de SMTP portları genellikle 465 ve 587'dir. Fakat siz SMTP portunuzu bilmiyorsanız sunucu hizmetini aldığınız firmaya danışın yine de.

Kolay gelsin