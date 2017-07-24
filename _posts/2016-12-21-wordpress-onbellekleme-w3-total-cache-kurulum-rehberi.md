---
ID: 5946
post_title: 'WordPress Önbellekleme: W3 Total Cache Kurulum Rehberi'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-onbellekleme-w3-total-cache-kurulum-rehberi-5946.html
published: true
post_date: 2016-12-21 08:29:12
---
<strong>Cache </strong>türkçe karşılığı ile önbellekleme gerek server da gerekse bilgisayarlar da sistem yükünü önemli ölçülerde hafifleten bir sistemdir. Bu sistem sayesinde sürekli yapılan işler ram 'in veya hafızanın belli bir kısmında tutulur. Ardından sürekli çağrılan bu veriler hafızandan direk olarak kullanıcıya gösterilir. Bu sayede server aynı işlemler için bellek ve işlemci kullanmak zorunda kalmaz. Hem hafifler hemde kullanıcıya daha hızlı bir şekilde veri akışını sağlamış olur. <a href="http://ankaakademi.com/server-da-cache-onbellekleme-nedir-ne-ise-yarar" target="_blank">*</a>

TR Kodlama'da ben W3 Total Cache kullanıyorum ve çok düşük özellikli bir sunucuda olsam bile ne kadar hızlı yüklendiğini farkedebilirsiniz. Ayrıca bana sunucu konusunda destek olan <a href="http://www.nekil.com/?ref=trkodlama" target="_blank">Nekil</a>'e de çok teşekkür ediyorum. WordPress çekirdeği(core) çok iyi performans gösteren bir mimariye sahip değil. Fakat biz onun performansını gerek tarayıcı gerekse sunucu tarafında önbellekleyerek artırabiliriz. WordPress'de de önbellekleme yapmanın en kolay yolu eklentilerdir. Bugün sizlere en popüler ve başarılı eklenti olan <strong>W3 Total Cache</strong> eklentisinin en başarılı ayarlarını aktaracağım.
<h2>W3 TOTAL CACHE EKLENTİSİNİ İNDİRİN</h2>
W3 Total Cache eklentisini indirmek için aşağıdaki adımları takip edin:
<ol>
 	<li>WordPress yönetici paneline giriş yapın</li>
 	<li><strong>Eklentiler &gt;&gt; Yeni Ekle</strong> linkine tıklayın soldaki menüden</li>
 	<li>Arama kutusunun içine "w3 total cache" yazın ve yükleyin.</li>
</ol>
<h2>Temel W3 Total Cache Ayarları</h2>
Eklentiyi yükledikten sonra eklentiyi aktifleştirin. Aktifleştirdiğiniz anda admin barda <strong>Performance</strong> sekmesini göreceksiniz. Kurulum aşamasını başarıyla tamamladınız. Şimdi sizlere temel ayarları aktaracağım.
<h3>Genel Ayarlar(General Settings)</h3>
<ul>
 	<li><strong>Page Cache</strong> işaretleyin ve <strong>Disk: Enhanced</strong><strong> </strong>seçeneğini seçin.</li>
 	<li><strong>Minify</strong> işaretleyin ve <strong>Disk </strong>seçeneğini seçin. Bazı durumlarda minify işlemi temanızı bozabilir. En uygun ayarları Minify sekmesinde deneme yanılma yöntemi ile bulmalısınız. Eğer her türlü bozuluyorsa bu seçeneği işaretlemeyin.</li>
 	<li><strong>Database Cache</strong> seçeneğini işaretlemeyin. Bazı eklentilerin çalışmasını bozabiliyor bu nedenle tavsiye edilmiyor.</li>
 	<li><strong>Object Cache</strong> işaretleyin ve <strong>Disk</strong> seçeneğini seçin.</li>
 	<li><strong>Browser Cache </strong>işaretleyin.</li>
 	<li><strong>CDN</strong>'yi işaretlemenizi öneririm. Sunucunuzun yükün müthiş oradan azaltacaktır. Fakat CDN kurulumu için yardım almanız gerekebilir.</li>
</ul>
<h2>Gelişmiş W3 Total Cache Ayarları</h2>
Şimdi biraz daha gelişmiş ayarları yapmaya başlayabiliriz..
<h3>Sayfa Önbellekleme (Page Cache)</h3>
<strong>Performance &gt;&gt; Page Cache</strong> linkine tıklayın soldaki menüden
<h4>Sayfa Önbellekleme  - Genel (Page Cache - General)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle </span>cache front page.</li>
 	<li><span style="color: #008000;">İşaretle </span>cache feeds.</li>
 	<li><span style="color: #008000;">İşaretle </span>cache SSL (https) requests.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> cache URIs with query string variables.</li>
 	<li><span style="color: #008000;">İşaretle </span>cache 404 (not found) pages.</li>
 	<li><span style="color: #008000;">İşaretle </span>cache requests only for www.howlthemes.com site address</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> don’t cache pages for logged in users.</li>
 	<li><span style="color: #008000;">İşaretle </span>don’t cache pages for following user roles</li>
</ul>
<h4>Sayfa Önbellekleme - Önbellek Önyükleme (Page Cache- Cache Preload)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> automatically prime the page cache.</li>
 	<li>Update interval değerini 11000 saniye olarak ayarlayın.</li>
 	<li>XML formatında site haritası adresini girin.</li>
 	<li><span style="color: #008000;">İşaretle</span> preload the post cache upon publish events.</li>
</ul>
<h3>Tarayıcı Önbellekleme (Browser Cache)</h3>
<strong>Performance</strong> &gt;&gt; <strong>Browser Cache</strong> linkine tıklayın soldaki menüden
<h4>Tarayıcı Önbellekleme - Genel (Browser Cache- General)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Set Last-Modified header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set expires header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set cache control header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set entity tag (eTag).</li>
 	<li><span style="color: #008000;">İşaretle</span> Set W3 Total Cache header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Enable HTTP (gzip) compression.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Prevent caching of objects after settings change.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Don’t set cookies for static files.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Do not process 404 errors for static objects with WordPress.</li>
</ul>
<h4>Tarayıcı Önbellekleme - CSS&amp;JS (Browser Cache- CSS &amp; JS)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Set Last-Modified header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set expires header.</li>
 	<li>Header lifetime 31536000 saniye olarak girin.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set cache control header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set entity tag (ETag).</li>
 	<li><span style="color: #008000;">İşaretle</span> Set W3 Total Cache header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Enable HTTP (gzip) compression.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Prevent caching of objects after settings change.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Disable cookies for static files.</li>
</ul>
<h4>Tarayıcı önbellekleme - HTML&amp;XML (Browser Cache- HTML &amp; XML)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Set Last-Modified header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set expires header.</li>
 	<li>Header lifetime 3600 saniye olarak girin.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set cache control header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set entity tag (ETag).</li>
 	<li><span style="color: #008000;">İşaretle</span> Set W3 Total Cache header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Enable HTTP (gzip) compression.</li>
</ul>
<h4>Tarayıcı Önbellekleme - Medya &amp; Diğer Dosyalar (Browser Cache- Media &amp; Other Files)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Set Last-Modified header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set expires header.</li>
 	<li>Header lifetime 31536000 saniye olarak girin.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set cache control header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Set entity tag (ETag).</li>
 	<li><span style="color: #008000;">İşaretle</span> Set W3 Total Cache header.</li>
 	<li><span style="color: #008000;">İşaretle</span> Enable HTTP (gzip) compression.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Prevent caching of objects after settings change.</li>
 	<li><span style="color: #ff0000;">İşaretleme</span> Disable cookies for static files.</li>
</ul>
Bu ayarlar Google Pagespeed Insights'daki notunuzu gözle görülür bir şekilde yükseltecektir.
<h3>Küçültme (Minify)</h3>
<strong>Performance</strong> &gt;&gt; <strong>Minify</strong> linkine tıklayın soldaki menüden
<h4>Küçültme - Genel (Minify- General)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> rewrite URL structure.</li>
</ul>
<h4>Küçültme - HTML&amp;XML (Minify- HTML &amp; XML)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Enable HTML minify settings.</li>
 	<li><span style="color: #008000;">İşaretle</span> Inline CSS minification.</li>
 	<li><span style="color: #008000;">İşaretle</span> Inline JS minification.</li>
 	<li><span style="color: #008000;">İşaretle</span> Hide comments.</li>
</ul>
<h4>Küçültme - JS (Minify- JS)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Enable JS minify settings.</li>
</ul>
<h4>Küçültme - CSS (Minify- CSS)</h4>
<ul>
 	<li><span style="color: #008000;">İşaretle</span> Enable CSS minify settings.</li>
 	<li><span style="color: #008000;">İşaretle</span> Remove unnecessary backslashes.</li>
</ul>
İşte bu kadar. Bu ayarlarla WordPress siteniz uçuşa geçecek. Artık sitenizin altına "Tek rakibimiz Türk Hava Yolları" yazabilirsiniz :)

Herhangi bir hata ile karşılaşırsanız lütfen yorum olarak bizimle paylaşın. İşinize yaraması dileğiyle,