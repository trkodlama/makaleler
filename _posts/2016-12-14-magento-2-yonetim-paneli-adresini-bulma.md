---
ID: 5939
post_title: Magento 2 Yönetim Paneli Adresini Bulma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento/magento-2-yonetim-paneli-adresini-bulma-5939.html
published: true
post_date: 2016-12-14 22:54:21
---
Merhaba arkadaşlar,

Magento 2 e-ticaret sisteminde yönetici panelinin adresini kurulum sonrasında not etmediyseniz bulmanız biraz zor olabiliyor. Fakat bunu nasıl öğreneceğinizi sizinle paylaşıyorum.

Magento 2 Admin panel adresini şu dosyada bulabilirsiniz:
<blockquote>/app/etc/env.php</blockquote>
Bu dosyanın içinde şu şekilde paylaşılmıştır, ilk satırlarda:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
return array (
  'backend' =&gt;
  array (
    'frontName' =&gt; 'admin_uu2osg',
  )
 );</pre>
İşinize yararsa ne mutlu :)