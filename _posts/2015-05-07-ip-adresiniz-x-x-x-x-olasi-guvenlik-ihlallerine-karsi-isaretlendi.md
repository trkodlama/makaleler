---
ID: 5726
post_title: >
  IP Adresiniz (X.X.X.X) Olası Güvenlik
  İhlallerine Karşı İşaretlendi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress/ip-adresiniz-x-x-x-x-olasi-guvenlik-ihlallerine-karsi-isaretlendi-5726.html
published: true
post_date: 2015-05-07 12:13:48
---
Merhaba arkadaşlar,

<strong>Wordpress</strong> sitelerimden birinde Jetpack uygulamasına bağlamaya çalışırken farkettim ki Proxy ayarlarımdan dolayı www.wordpress.com'a erişimim yoktu. Tor browser'ı indirdim, farklı bir proxy ayarlarıyla WordPress'ime giriş yapmaya çalıştığımda bu hatayı aldım:
<blockquote>Ip adresiniz (X.X.X.X) olası güvenlik ihlallerine karşı işaretlendi. <span style="color: #3366ff;">Daha fazla bilgi...</span></blockquote>
Jetpack ile wordpress'i yetkilendiremedim ama Jetpack maşallah hemen engellemiş beni :) Çözümü oldukç basit arkadaşlar. <strong>wp-config.php</strong> dosyamıza X.X.X.X'de yazan IP'mize izin verilmesini bildiriyoruz Jetpack'e. wp-config.php dosyasına aşağıdaki satırı ekleyelim:
<pre class="lang:php decode:1 ">define('JETPACK_IP_ADDRESS_OK', 'X.X.X.X');</pre>
Bu satır sayesinde şimdi giriş yapabileceksiniz. Umarım faydalı olur, kolay gelsin.