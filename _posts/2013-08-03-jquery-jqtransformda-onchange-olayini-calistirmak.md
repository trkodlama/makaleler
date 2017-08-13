---
ID: 1287
post_title: 'jQuery jqTransform&#8217;da onChange Olayını Çalıştırmak'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-jqtransformda-onchange-olayini-calistirmak-1287.html
published: true
post_date: 2013-08-03 18:51:20
---
Merhaba arkadaşlar,

jQuery jqTransform kütüphanesinde bilinen bir onChange açığı vardı. jqTransform ile <strong>select kutuları</strong> yeni görünümlerine kavuştuktan sonra <strong>onChange event</strong>'i çalışmayı durduruyor. Bu problemin çözmek için jquery.jqtransform.js dosyasını açın ve aşağıdaki satırı bulun:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">if ($select[0].selectedIndex != $(this).attr('index') &amp;&amp; $select[0].onchange) { $select[0].selectedIndex = $(this).attr('index'); $select[0].onchange(); }</pre>
Bu satırı aşağıdaki satırla değiştirin:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">if ($select[0].selectedIndex != $(this).attr('index')) { $select[0].selectedIndex = $(this).attr('index'); $select.change(); }</pre>
Umarım faydalı olur, kolay gelsin