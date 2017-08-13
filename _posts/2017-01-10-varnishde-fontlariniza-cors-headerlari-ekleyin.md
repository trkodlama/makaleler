---
ID: 6059
post_title: 'Varnish&#8217;de Font&#8217;larınıza CORS Header&#8217;ları Ekleyin'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/varnishde-fontlariniza-cors-headerlari-ekleyin-6059.html
published: true
post_date: 2017-01-10 00:10:30
---
Merhaba arkadaşlar,

Sunucunuzda Varnish kuruluysa .htaccess dosyanıza
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Header set Access-Control-Allow-Origin "*"</pre>
ekleseniz bile farklı bir alan adından veya alt alan adından font vs. çekmeye çalışırsanız geliştirici seçeneklerinde konsol da CORS hataları alırsınız. Bunun sebebi Varnish dosyaları yollarken bu header'ları dosyalarınızdan silecektir. Şöyle basit bir hamle ile <strong>fonts </strong>klasöründe bulunan dosyalar için CORS'a izin verebiliriz:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">if (req.url ~ "/fonts/") {
    set resp.http.Access-Control-Allow-Origin = "*";
    set resp.http.Access-Control-Allow-Methods = "GET, OPTIONS";
    set resp.http.Access-Control-Allow-Headers = "Origin, Accept, Content-Type, X-Requested-With, X-CSRF-Token";
}</pre>
Bu sayede rahatlıkla erişim sağlayabilirsiniz.