---
ID: 1327
post_title: >
  mailcheck.js Sayesinde E-Posta
  Alanlarınızdaki Hatalı Girişlerin
  Önüne Geçin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mailcheck-js-sayesinde-e-posta-alanlarinizdaki-hatali-girislerin-onune-gecin-1327.html
published: true
post_date: 2012-10-21 23:17:02
---
Merhaba arkadaşlar,

Bugün sizlere <strong>mailcheck.js</strong> isminde bir javascript kütüphanesini ve <strong>jQuery eklentisi</strong>ni tanıtıyorum. Bu eklenti kullanıcılarınıza e-posta adreslerini girdiklerinde bir hata varsa hemen bir öneri sunar. Google kadar profesyonel öneriler olmasa da genel olarak iş görebilecek önerilerdir. Örneğin kullanıcı "user@hotnail.con" şeklinde yazdığı zaman e-posta adresini <strong>Mailcheck</strong> otomatik olarak "user@hotmail.com" u önerir. Mailcheck en bilindik domainler için domain önermesi yapar ve uzantılarda da önerme yapılacak bir durum varsa yine önerir. Örneğin "com" yerine "cmo" yazıldığında.

Bu sayede hatalı email adresi yazma ihtimalini %50 oranında düşürmeye fayda sağlar.

Kontrol edilen başlıca domainler ise şöyledir: "yahoo.com, google.com, hotmail.com, gmail.com, me.com, aol.com, mac.com, live.com, comcast.net, googlemail.com, msn.com, hotmail.co.uk, yahoo.co.uk, facebook.com, verizon.net, sbcglobal.net, att.net, gmx.com ve mail.com". Kontrol edilen uzantılar da şunlardır: "com, net, org, info, edu, gov, co.uk ve mil".

<a href="http://www.trkodlama.com/wp-content/uploads/2012/10/mail-check.jpg"><img class="aligncenter size-full wp-image-1328" title="mail-check" src="http://www.trkodlama.com/wp-content/uploads/2012/10/mail-check.jpg" alt="" width="580" height="167" /></a>
<h3>Kurulumu</h3>
Öncelikle jQuery ve Mailcheck dosyalarını ekleyin:

<pre class="lang:html decode:1 " >&amp;lt;script src=&amp;quot;jquery.min.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt;
&amp;lt;script src=&amp;quot;mailcheck.min.js&amp;quot;&amp;gt;&amp;lt;/script&amp;gt;</pre>

Text bir input oluşturalım:

<pre class="lang:html decode:1 " >&amp;lt;input id=&amp;quot;email&amp;quot; name=&amp;quot;email&amp;quot; type=&amp;quot;text&amp;quot; /&amp;gt;</pre>

Şimdi Mailcheck'i email id'li inputa iliştirelim. Bu işlemi yaparken isteğe bağlı olarak domainleri ve uzantıları sınırlayabilirsiniz(ekstra tanımlayarak):

<pre class="lang:html decode:1 " >&amp;lt;script&amp;gt;
var domainler = ['trkodlama.com', 'hotmail.com', 'gmail.com', 'aol.com'];
var uzantilar = [&amp;quot;com&amp;quot;, &amp;quot;net&amp;quot;, &amp;quot;org&amp;quot;];

$('#email').on('blur', function() {
  $(this).mailcheck({
    domains: domainler,                     // isteğe bağlı
    topLevelDomains: uzantilar,       // isteğe bağlı
    suggested: function(element, suggestion) {
      // tavsiye varsa yapılacak işlemler
    },
    empty: function(element) {
      // tavsiye yoksa yapılacak işlemler
    }
  });
});
&amp;lt;/script&amp;gt;</pre>

Suggested ve empty şeklinde iki ayrı callback fonksiyon kullanabileceğiniz alan vardı Mailcheck'de. Suggested alanında  sadece eğer bir tavsiye varsa callback fonksiyonunuz çalışır. Ve tavsiyeler size aşağıdaki formatta bir nesne ile gönderilir:

<pre class="lang:js decode:1 " >{
  address: 'info',            // @ işaretinden &ouml;nceki kısım
  domain: 'trkodlama.com',    // tavsiye edilen domain
  topLevelDomain: 'com',      // tavsiye edilen domainin uzantısı
  full: 'info@trkodlama.com'  // tavsiye edilen mailin tamamı
}</pre>

empty ise değer sunulacak bir öneri yoksa çalıştırılır.

Bu fonksiyonu jQuery çalıştırmadan da kullanabilirsiniz fakat onu burada anlatmıyorum. Siz fonksiyonun github sayfasını inceleyerek kullanımını öğrenebilirsiniz.

Gereksinimler: jQuery Framework
Demo: <a title="demo" href="https://github.com/Kicksend/mailcheck" rel="nofollow" target="_blank">https://github.com/Kicksend/mailcheck</a>
Lisans: MIT Lisanslı

[wpdm_file id=9]