---
ID: 9316
post_title: 'PHP&#8217;de explode() Fonksiyonu ve Kullanımı'
author: Oral ÜNAL
post_excerpt: '<code>explode()</code> - Bir dizgeyi istediğiniz bir ifade ile parçalara ayırarak dizi oluşturur.'
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/phpde-explode-fonksiyonu-kullanimi-9316.html
published: true
post_date: 2011-07-19 04:26:37
---
Aslında bu bir fonksiyon tanıtımı ve çok saçma olduğunu biliyorum. Fakat belli başlı temel fonksiyonların bu şekilde yazılarını paylaşmayı düşünüyorum. Bunun sebebi diğer yazılarımı hazırlarken explode kullanımı ile ilgili okuyucuyu php.net'e yönlendirmek istemiyorum. TR Kodlama içerisinde tutmak için bu şekilde belki çöp denilebilecek içerikler hazırlayacağım. Ayrıca bu yazıların tarihlerini 2011 olarak ayarlayacağım :) Güncel içerik gibi görünmelerini istemiyorum.
<h2>explode() Tanımı</h2>
explode - Bir dizgeyi istediğiniz bir ifade ile parçalara ayırarak dizi oluşturur.
<h3>Desteklenen PHP Sürümleri</h3>
<ol>
 	<li>PHP 4</li>
 	<li>PHP 5</li>
 	<li>PHP 7</li>
</ol>
<h2>explode() Kullanımı</h2>
<pre class="line-numbers"><code class="language-php">array explode ( string $ayraç , string $dizge [, int $sınır ] );</code></pre>
<h3>- $ayrac</h3>
İfadeyi parçalamak için kullanılacak olan ifade
<h3>- $dizge</h3>
Parçalanacak ifade
<h3>- $sınır</h3>
Oluşacak dizinin boyutunu tanımlar. İsteğe bağlıdır kullanılması zorunlu değildir. Pozitifse dizi en çok <code>$sınır</code> sayıda eleman içerir ve ifadenin kalanı son elemana yerleştirilir. Negatifse, son <code>$sınır</code> eleman hariç tüm elemanlar döndürülür. Eğer sıfırsa, 1 olarak ele alınır.
<h2>Dönen Değerler</h2>
Eğer <code>$ayrac</code> için boş bir ifade ("") kullanıldıysa <code>FALSE</code> döner. Diğer durumlar bir dizi döner.
<h2>explode() Örnekler 1</h2>
<pre class="line-numbers"><code class="language-php">&lt;?php
// 1. örnek
$pizza  = "dilim1 dilim2 dilim3 dilim4 dilim5 dilim6";
$dilimler = explode(" ", $pizza);
echo $dilimler[0]; // dilim1
echo $dilimler[1]; // dilim2

// 2. örnek
$data = "foo:*:1023:1000::/home/foo:/bin/sh";
list($user, $pass, $uid, $gid, $gecos, $home, $shell) = explode(":", $data);
echo $user; // foo
echo $pass; // *

?&gt;</code></pre>
<h2>explode() Örnekler 2 - sınır parametresi tanımlı</h2>
<pre class="line-numbers"><code class="language-php">&lt;?php
$str = 'one|two|three|four';

// positif sınır
print_r(explode('|', $str, 2));

// negatif sınır (PHP 5.1 ve sonrası)
print_r(explode('|', $str, -1));
?&gt;</code></pre>
Bu örneğin çıktısı aşağıdaki gibi olacaktır:
<pre class="line-numbers"><code class="language-markup">Array
(
    [0] =&gt; one
    [1] =&gt; two|three|four
)
Array
(
    [0] =&gt; one
    [1] =&gt; two
    [2] =&gt; three
)</code></pre>
<h3>Ayrıca Bakmanızda Fayda Var</h3>
<code>preg_split()</code> - Dizgeyi düzenli ifadeye göre böler
<code>str_split()</code> - Bir dizgeyi bir diziye dönüştürür
<code>str_word_count()</code> - Bir dizgedeki sözcükler hakkında bilgi verir
<code>strtok()</code> - Dizgeyi bir dizgeciğe göre böler
<code>implode()</code> - Dizi elemanlarını birleştirip bir dizge elde eder