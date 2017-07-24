---
ID: 2600
post_title: 'Magento&#8217;da Para Birimi Kodunu Alma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magentoda-para-birimi-kodunu-alma-2600.html
published: true
post_date: 2013-10-12 22:07:01
---
Merhaba arkadaşlar,

Magento'da para birimi kodunu almak için aşağıdaki paylaştığım koda ihtiyaç duyacaksınız:

<pre class="lang:php decode:1 " >&amp;lt;?php
$paraBirimi= Mage::app()-&amp;gt;getStore()-&amp;gt;getCurrentCurrencyCode();
echo $paraBirimi;
?&amp;gt;</pre>

Yukarıdaki kodun çıktısı <strong>USD</strong>, <strong>TRY</strong>, <strong>EUR</strong> vs. olacaktır.

Kolay gelsin,