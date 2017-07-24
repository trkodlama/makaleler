---
ID: 5873
post_title: 'Cron Jobs&#8217;da WGET Kullanıldığında Sayfanın Çıktısının Kaydedilmesi'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/cron-jobsda-wget-kullanildiginda-sayfanin-ciktisinin-kaydedilmesi-5873.html
published: true
post_date: 2016-07-01 01:47:15
---
Merhaba uzun bir aradan sonra,

Başlıkta aslında tam olarak paylaşmak istediğim olay anlaşılamamış olabilir. Bunu biraz detaylandırmak istiyorum açıkcası.

cPanel'i açtınız. Cron Jobs veya Zamanlanmış Görev ayarlaması yaptınız. Ve kullandığınız komut bir sayfayı açıyor belirlediğiniz periyotlarla:

<pre class="lang:bash decode:1 " >wget http://www.trkodlama.com/zamanlanmis_gorevler.php</pre>

Güzel güzel çalıştığını düşünüyorsunuz fakat FTP ile sunucunuza bağlandığınızda tonla dosya gördünüz şu isimlerle:

<ul>
    <li>zamanlanmis_gorevler.php.1</li>
    <li>zamanlanmis_gorevler.php.2</li>
    <li>zamanlanmis_gorevler.php.3</li>
    <li>zamanlanmis_gorevler.php.4</li>
    <li>zamanlanmis_gorevler.php.5</li>
    <li>zamanlanmis_gorevler.php.6</li>
    <li>zamanlanmis_gorevler.php.7</li>
    <li>.....</li>
</ul>

Bunun sebebi WGET ile siz o sayfayı indiriyorsunuz ve ekran çıktısını da sunucuya kaydediyorsunuz. Bunun önüne geçmek çok basit. İki seçenek ekliyoruz. Bunlardan bir tanesi <strong>-q</strong>; herhangi bir çıktı almanızı engelleyecektir. Ayrıca bir de <strong>--spider</strong> ekleyerek sadece HEAD sorgusu şeklinde ister adresi. Bu da tam olarak istediğiniz olay olur. Dosyanız çalışır ve çöplük dosyalardan kurtulmuş olursunuz.

<pre class="lang:bash decode:1 " >wget -q --spider http://www.trkodlama.com/zamanlanmis_gorevler.php</pre>

Bol bol makale paylaşmamız dileğiyle,