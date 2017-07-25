---
ID: 9280
post_title: 'DataTables&#8217;de Boş JSON Göndermek'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/datatablesde-bos-json-gondermek-9280.html
published: true
post_date: 2017-07-07 13:55:40
---
Merhaba arkadaşlar,

Bir kaç zamandır projelerimde DataTable kullanıyordum. Dün geceye kadar DataTables için hazırlanmış olan SSP sınıfını kullanıyordum. Fakat bir haftadır üzerinde çalıştığım sipariş sisteminin akışını komple değiştirdim. Bu sefer siparişleri listelerken kullanmış olduğum sorguda <strong>LEFT JOIN</strong> kullanma ihtiyacı hissettim. Sonuç itibari ile de kullandım. Kendi DataTables kaynağımı kendim oluşturmak için kolları sıvadım ve hayatımın SQL sorgusunu yazdım.
<blockquote>SSP sınıfını inceleyip indirmek için <a href="https://github.com/DataTables/DataTables/blob/master/examples/server_side/scripts/ssp.class.php" target="_blank" rel="noopener">buraya</a> tıklayınız.</blockquote>
Neyse buraları uzatmanın anlamı yok. DataTables ile verileri güzelce çekiyorum. Eğer veri varsa problem yaşamıyorum. Fakat boş JSON nasıl yollayabilirim? Aşağıdaki şekilde denedim fakat hata aldım.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="6" data-caption="Hatalı Gönderim">&lt;?php
$result['draw'] = (int)$_POST['draw'];
$result['recordsTotal'] = 0;
$result['recordsFiltered'] = 0;

$result['data'][] = [];

echo json_encode($result);
?&gt;</pre>
Fakat DataTables'a göndermemiz gereken JSON aşağıdaki formatta olmalıymış:
<pre class="prettyprint lang-json" data-start-line="1" data-visibility="visible" data-highlight="5" data-caption="">{
    "draw": 1,
    "recordsFiltered": 0,
    "recordsTotal": 0,
    "data": []
}</pre>
Bunun üzerinde <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >$result['data'][] = [];</pre> değişkenim dikkatimi çekti. Onu <pre class="class:prettyprint lang-php data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >$result['data'] = [];</pre> şeklinde değiştirdiğimizde problem çözülmüş oldu. Tam hali aşağıdadır:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="6" data-caption="">&lt;?php
$result['draw'] = (int)$_POST['draw'];
$result['recordsTotal'] = 0;
$result['recordsFiltered'] = 0;

$result['data']= [];

echo json_encode($result);
?&gt;</pre>
Kaynak: <a href="https://stackoverflow.com/questions/41431205/why-does-datatable-doesnt-show-empty-data-message" target="_blank" rel="noopener">stackoverflow.com/questions/41431205/why-does-datatable-doesnt-show-empty-data-message</a>