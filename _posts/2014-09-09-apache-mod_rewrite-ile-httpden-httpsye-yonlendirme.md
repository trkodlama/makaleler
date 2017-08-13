---
ID: 5442
post_title: 'HTTP Sorgularını HTTPS&#8217;ye Apache mod_rewrite Kullanarak Yölendirin'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/apache-mod_rewrite-ile-httpden-httpsye-yonlendirme-5442.html
published: true
post_date: 2014-09-09 17:42:28
---
<ul>
 	<li>Ödeme sayfalarında, ki bunlar genelli alışveriş sitelerinde bulunur, kullanıcılar <strong>https </strong>protokolünü arıyorlar. Bulunduları sayfada en azından <b>yeşil renkli </b>kilit simgesini görmeyi bekliyorlar.</li>
</ul>
Alışveriş sitenizi <strong>http </strong>ile gezen birisi ödeme sayfasında <strong>https</strong> görmelidir. Çünkü işin içine para giriyor.

Bunu yapmanın iki yolu var.
<ol>
 	<li>Fazladan çalışıp kendinizi yormak istiyorsanız bütün projenizde linkleri <strong>https </strong>olarak ayarlarsınız.</li>
 	<li>Ama zekice davranıp 3 satırcık kodla işinizi bitirebilirsiniz.</li>
</ol>
<strong>Güncelleme: 1 Ağustos 2017</strong>

Kod içeriğinde iyileştirme
<pre class="line-numbers"><code class="language-apacheconf">RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]</code></pre>
Yukarıdaki kodu <strong>.htaccess</strong> dosyanızın içine ekleyin. İhtiyacınız olan herşeyi bu kod yapıverdi. Aşağıda bu satırları açıklayalım, bakalım ne demeklermiş:

<strong>Satır 1: </strong><strong>RewriteEngine On
</strong>Bu satır Apache'ye rewrite motorunu çalıştırmaını belirtir. Böylelikle verilen kurallara göre rewrite işlemi yapılabilecektir URL'lerde.

<strong>Satır 2 : RewriteCond %{HTTPS} off
</strong>Bu satırda URL protokolümüzü kontrol ediyoruz. <strong>HTTPS off</strong>'dan kastımız URL protokolümüz <strong>http</strong>'yse anlamına geliyor. Eğer koşulumuz doğruysa true döner ve bir alt satırı işleme alır.

<a title="Apache Mod rewrite" href="http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html" target="_blank" rel="noopener">RewriteCond Direktifleri</a> için linke tıklayın.

<strong>Satır 3: </strong><strong>RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
</strong>Üstteki koşul true döndüğü taktirde çalışır. http ile başlayan URL'mizi https olarak günceller.

Bu ipucunu kullanmaya başlamadan önce apache ayar dosyanızdan mod_rewrite modülünü açtığınızdan emin olun. Genellikle başında <strong>"#"</strong> işareti vardır ve kapalıdır. Başındaki diyez işaretini kaldırmanız gerekmektedir.

Fakat sadece bazı sayfalarımızda https olmasını istersek ne yapacağız? Bu da bir sonraki yazımızın konusu olsun.