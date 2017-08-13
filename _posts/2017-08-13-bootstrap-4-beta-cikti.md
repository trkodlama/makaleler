---
ID: 9993
post_title: Bootstrap 4 Beta Çıktı
author: Oral ÜNAL
post_excerpt: |
  Hepinizin bildiği gibi uzun zamandır Bootstrap 3 kullanılıyordu. Yine uzun zamandır Bootstrap 4 alfa sürümlerini yayınlıyorlardı.
  
  Sonunda beklenen sürüm olan <strong>Bootstrap 4 </strong><strong>Beta</strong> olarak yayında. Peki <strong>Bootstrap 4 Beta</strong> ile neler değişti? Gelin hep beraber inceleyelim..
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/bootstrap-4-beta-cikti-9993.html
published: true
post_date: 2017-08-13 13:45:22
---
Hepinizin bildiği gibi uzun zamandır Bootstrap 3 kullanılıyordu. Yine uzun zamandır Bootstrap 4 alfa sürümlerini yayınlıyorlardı.

Sonunda beklenen sürüm olan <strong>Bootstrap 4 </strong><strong>Beta</strong> olarak yayında. Peki <strong>Bootstrap 4 Beta</strong> ile neler değişti:
<ul>
 	<li><strong>Normalize.css</strong> artık Bootstrap'ın gereksinim duyduğu bir kütüphane değil. Bootstrap kendi <strong>Reboot</strong> kütüphanesini kullanacak.</li>
 	<li>Esnek menü sınıf ismi .navbar-toggleable yerine artık .navbar-expand olarak güncellendi. Bununla ilgili bazı açıklar da giderildi.</li>
 	<li>Bazı anormal grid(ızgara) davranışları düzeltildi ve dökümanlar güncellendi.</li>
 	<li>Bir çok değişken ismi değiştirildi. Değişiklikleri görmek için <a class="issue-link js-issue-link" href="https://github.com/twbs/bootstrap/issues/22414" data-url="https://github.com/twbs/bootstrap/issues/22414" data-id="221112076" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#22414</a> ve <a class="issue-link js-issue-link" href="https://github.com/twbs/bootstrap/issues/22092" data-url="https://github.com/twbs/bootstrap/issues/22092" data-id="211166217" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#22092</a> linklerini takip edebilirsiniz.</li>
 	<li><strong>Gruntfile</strong> ve dökümanları paket yöneticisi ile oluşturulmalarda artık yok.</li>
 	<li>Kullanılmayan değişkenleri yakalayan bir bash scripti hazırlandı.</li>
</ul>
Daha sayamayacağım tonla yeni özellik getirildi. Tüm değişiklik listesine ulaşmak istiyorsanız <a href="https://github.com/twbs/bootstrap/issues/21568">#21568</a> linkine tıklayabilirsiniz.

TR Kodlama'da Bootstrap 4 Alpha 6 kullanıyorduk. Yeni Beta sürümüne geçeriz yakın zaman içerisinde... Bootstrap'ın tüm sürümlerini ve değişiklik kayıtlarını <a href="https://github.com/twbs/bootstrap/releases">buraya</a> tıklayarak bulabilirsiniz. Bizim değindiğimiz değişiklikler Bootstrap v4.0.0-alpha.6 sürümünden v4.0.0-beta sürümüne olanlardır.
<blockquote>Ayrıca Bootstrap'ın ne olduğunu da merak edenler olabilir. Bootstrap ile ilgili detaylı bilgi için <a href="https://www.trkodlama.com/web-tasarim-2/genis-bootstrap-rehberi-bootstrap-nedir-bootstrap-nasil-kullanilir-9384.html">Bootstrap Rehberi</a>mizi okumalısınız.</blockquote>
Yeni Bootstrap 4 Beta'yı indirmek için <a href="https://getbootstrap.com/">GetBootstrap</a> web sitesini ziyaret edin lütfen.
<h2>Bootstrap'ı CDN ile Hemen Kullanmaya Başlayın</h2>
Eğer Bootstrap'ın derlenmiş dosyalarını kullanmak istiyorsanız CDN'leri gönül rahatlığıyla kullanabilirsiniz. Bootstrap 4 Beta için aşağıdaki kod ile Bootstrap 4 Beta CSS dosyasını projenize ekleyebilirsiniz:
<h4>Bootstrap 4 Beta CSS</h4>
<pre class="line-numbers"><code class="language-html">&lt;link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css" integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M" crossorigin="anonymous"&gt;</code></pre>
Ayrıca JavaScript dosyalarını da eklemeniz gerekmektedir:
<h4>Bootstrap 4 Beta jQuery.js, Popper.js ve Bootstrap.js</h4>
<pre class="line-numbers"><code class="language-html">&lt;script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"&gt;&lt;/script&gt;
&lt;script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.11.0/umd/popper.min.js" integrity="sha384-b/U6ypiBEHpOf/4+1nzFpr53nxSS+GLCkfwBdFNTxtclqqenISfwAzpKaMNFNmj4" crossorigin="anonymous"&gt;&lt;/script&gt;
&lt;script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/js/bootstrap.min.js" integrity="sha384-h0AbiXch4ZDo7tp9hKZ4TsHbi047NrKGLO3SEJAg45jXxnGIfYzk4Si90RDIqNm1" crossorigin="anonymous"&gt;&lt;/script&gt;</code></pre>
Bir değişiklik daha dikkatimi çekti, tether.js kullanımından popper.js kullanımına geçmişler. Farklarını bilmiyorum, Önemli bir konu ise buna da değinirim bir ara.

Güle güle kullanın, Bootstrap 4 vatana millete hayırlı olsun :)

&nbsp;