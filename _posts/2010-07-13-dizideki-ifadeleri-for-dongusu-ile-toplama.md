---
ID: 58
post_title: >
  Dizideki İfadeleri For Döngüsü ile
  Toplama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/dizideki-ifadeleri-for-dongusu-ile-toplama-58.html
published: true
post_date: 2010-07-13 07:41:32
---
Merhaba,

Bu yazımda bir dizi içindeki bütün değerleri for döngüsü ile nasıl toplayacağımızı anlatacağım.. Basit bir örnekle açıklıyorum
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$dizi=array(10, 25, 36, 65, 9, 25); // Basit bir dizi oluşturduk..
$dizi_boyutu=count($dizi); // Dizinin kaç terimden oluştuğunu saydık..
// Şimdi for döngüsü ile bu ifadeleri toplayalım
$toplam=0;
for($i=0; $i&lt;=$dizi_boyutu; $i++){
    $toplam+=$dizi[$i];
}
echo $toplam; // Dizinin içindeki ifadelerin toplamını gösterir...
?&gt;</pre>
Umarım faydalı olur. Bu makalede bizim işimizi "+=" operatörü görmüş oldu..

<hr />

<h2>Güncelleme 20.01.2017</h2>
Geçmişe dönük yazılarımı kontrol ederken bu gönderiyi farkettim. Dizi elemanlarını toplamak için bu kadar işleme hiç bir şekilde gerek yok :) 7 yıl önce bu şekilde topluyormuşum ama. Halbuki <strong>array_sum</strong> fonksiyonu ile dizi elemanlarını toplamak oldukça kolay:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$dizi=array(10, 25, 36, 65, 9, 25); // Basit bir dizi oluşturduk..
$toplam = array_sum($dizi);
echo $toplam; // Dizinin içindeki ifadelerin toplamını gösterir...
?&gt;</pre>
Eğer dizinizin içerisinde <em>string </em>türünde terimler yer alıyorsa bunlarda <em>integer</em> türüne çevrilerek toplanır. Yani içinizi ferah tutun. Bu güncellemeyi yapmak zorunda hissettim kendimi.

Tekrar görüşmek üzere...