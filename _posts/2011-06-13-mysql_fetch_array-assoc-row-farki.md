---
ID: 190
post_title: >
  mysql_fetch_array / mysql_fetch_assoc /
  mysql_fetch_row Farkı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mysql_fetch_array-assoc-row-farki-190.html
published: true
post_date: 2011-06-13 19:39:20
---
Merhaba arkadaşlar,
Bugünkü makalemde basit, kısa ama çok merak edilen bir makale. Bugün sizlere mysql_fetch_array, mysql_fetch_assoc ve mysql_fetch_row fonksiyonlarının arasındaki farkı açıklıyorum.

Farkları değişkenleri dizide tutuş yöntemleridir, şöyleki mysql_fetch_array fonksiyonunun kullanımı ve sonucu:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$sorgu=mysql_fetch_array(mysql_query("SELECT * FROM something"));

$sorgu[0]=$sorgu["ilksutun"];
$sorgu[1]=$sorgu["ikincisutun"];
$sorgu[n]=$sorgu["nincisutun"];</pre>
Yani diziye hem normal rakamsal değer veriyor hemde sütun adını veriyor.
mysql_fetch_rows fonksiyonunda sadece rakamsal değerleri verir. Yani $sorgu[0] fonksiyonu cevap verir fakat $sorgu["ilksutun"] boş gelirdi..
mysql_fetch_assoc fonksiyonunda ise değerleri sadece sütun adını kullanarak çekebilirsiniz. Yani $sorgu["ikincisutun"] değişkeni dolu gelir fakat $sorgu[1] tanımlanmamıştır bu nedenle boş gelecektir.
Farkı anlaşılır anlatabilmişimdir umarım arkadaşlar, herkese kolay gelsin,