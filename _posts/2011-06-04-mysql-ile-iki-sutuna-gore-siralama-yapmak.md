---
ID: 184
post_title: >
  MySQL ile İki Sütuna Göre Sıralama
  Yapmak
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mysql-ile-iki-sutuna-gore-siralama-yapmak-184.html
published: true
post_date: 2011-06-04 19:09:23
---
Merhaba arkadaşlar,
Uzun bir süredir yazı yazamıyordum. İşlerimin ve okulumun yoğunluğu artık uç noktada. Bu nedenle vakit bulamıyordum.
Bugün sizlere MySQL veritabanınızda sıralama işlemleri yaparken iki sütunu baza alırken nasıl sıralama yapacağınızı anlatıyorum.
Öncelikle normal bir sıralama işlemi yapalım:

<pre class="lang:php decode:1 " >&amp;lt;?php
$query=mysql_fetch_array(mysql_query(&amp;quot;SELECT sutun_adi FROM tablo_adi ORDER BY sutun_adi_1 ASC&amp;quot;));
?&amp;gt;</pre>

Bu şekilde çalıştırdığımızda PHP şu işlemi yapacaktır. tablo_adi tablosundan sutun_adi_1 sütunlarını küçükden büyüğe sıralayacaktır. Şimdi biz hem sütun_adi_1'e göre hem de sütun_adi_2'e göre bir sıralama yaptıralım:

<pre class="lang:php decode:1 " >&amp;lt;?php
$query=mysql_fetch_array(mysql_query(&amp;quot;SELECT sutun_adi FROM tablo_adi ORDER BY sutun_adi_1, sutun_adi_2&amp;quot;));
?&amp;gt;</pre>

Şu anda önce sütun_adi_1'e göre sonra ise sutun_adi_2'ye göre sıralayıp size verecektir. Tabii ki sutun_adi_1 sıralamasının yerini değiştirmeden. Yani sutun_adi_1'de elde ettiğiniz grupları kendi içinde sutun_adi_2'ye göre sıralayacaktır. Şimdi biraz daha abartalım ve sutun_adi_1'i ASC olarak ve sutun_adi_2'yi DESC olarak sıralayalım:

<pre class="lang:php decode:1 " >&amp;lt;?php
$query=mysql_fetch_array(mysql_query(&amp;quot;SELECT sutun_adi FROM tablo_adi ORDER BY sutun_adi_1 ASC, sutun_adi_2 DESC&amp;quot;));
?&amp;gt; </pre>

Umarım faydalı olmuştur, herkese kolay gelsin,