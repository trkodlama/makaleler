---
ID: 128
post_title: Gönderdiğiniz E-Posta Okundu mu?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/gonderdiginiz-e-posta-okundu-mu-128.html
published: true
post_date: 2011-03-26 17:10:05
---
Merhaba arkadaşlar,

Bir süredir tembelliğim ve işlerimin yoğunluğu nedeniyle bir paylaşımda bulunamadım. Ama faydalı bir makale ile tekrar buradayım.

Bu makale ile PHP ve .htaccess kullanarak gönderdiğiniz epostaların okunup okunmadığını nasıl kontrol edebileceğinizi anlatıyorum. Öncelikle 'eposta' adlı bir klasör oluşturalım. Bu makalede ben '/resimler/eposta/' dizinini kullanıyorum. Bu klasörün içinde yeni bir .htaccess dosyası oluşturun. AllowOverride ayarınızın All olarak ayarlı olduğundan emin olun.

.htaccess dosyanıza aşağıdaki kodu ekleyin:

[sourcecode][/sourcecode]

Sonraki adım da 1x1 piksel boyutlarında takip.png adlı bir dosyası oluşturun ve bunu da aynı klasörün içine atın. Bu resim epostanızın içinde açılacaktır.

Daha sonra takip.php adlı bir dosya daha oluşturun. Bu dosyada gönderdiğinizin epostanın okundu işlemini yapacağız.

<pre class="lang:php decode:1 " >&amp;lt;?php  
$takipId = $_REQUEST['x'];  
// $takipId ile epostanın g&ouml;nderildiği kişinin Id'sini &ccedil;ekiyoruz.  
// Veritabanında bu kişiyi bulup okudu s&uuml;tununu 1 olarak değiştiriyoruz  
// Veritabanı işleminin mantığını anlattım sadece  
   
header('Content-Type:image/png');  
echo file_get_contents('takip.png');   
?&amp;gt;</pre>

Eposta yollarken aşağıdaki HTML kodu epostanızın sonuna ekleyin. Bu sayede ID'si 1234 olan kullanıcı epostayı açtığında ve o resim yüklendiğinde veritabanında okundu olarak işaretlenecektir. htaccess ile çalışan scriptimizi çok basit bir şekilde maskeledik.

<pre class="lang:html decode:1 " >&amp;lt;img src='http://www.trkodlama.com/resimler/email/resim1234.png'&amp;gt;</pre>

Yararlı olur diye düşündüm, kolay gelsin..