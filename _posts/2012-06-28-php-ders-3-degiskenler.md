---
ID: 915
post_title: 'PHP Ders 3: Değişkenler'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ders-3-degiskenler-915.html
published: true
post_date: 2012-06-28 15:56:24
---
Değişkenler bir takım değerleri, yazıları, rakamları ve fonksiyon çıktılarını saklamak için kullanılır, bu nedenle kodlama sırasında çok kullanılırlar.

<hr />

<h3>PHP'de Değişkenler</h3>
<ol>
	<li>Değişkenler yazı, rakam ve dizi gibi değerleri saklamak için kullanılır.</li>
	<li>Bir scriptte ayarlanan bir değişken tekrar ve tekrar kullanılabilir.</li>
	<li>PHP'de bütün değişkenler $ sembolü ile başlar.</li>
</ol>
PHP'de doğru bir değişken yapısı:

<pre class="lang:php decode:1 " >$degisken_adi = deger;</pre>

PHP'ye yeni başlayan programcılar genelde $ işaretini koymayı unuturlar. Bu nedenle kodları çalışmaz.

Hadi bir yazının ve bir rakamın değişkene nasıl atandığını görelim:

<pre class="lang:php decode:1 " >&amp;lt;?php
$yazi = &amp;quot;Merhaba D&uuml;nya!&amp;quot;;
$number = 1992;
?&amp;gt;</pre>

<hr />

<h3>PHP Kodlaması Rahat Olan Bir Dildir</h3>
PHP değişkenlerinde değişkenin türünü belirlemene gerek yoktur. Yukarıdaki örnekte gördüğünüz gibi PHP'ye değer atadık ama değişkenler için önceden değerleri hakkında bilgi vermedi. PHP değişkenlerinin türü otomatik olarak doğru veri türüne çevirir. Bir çok popüler programlama dillerinde değişkenlere atayacağınız değerlerin türünü kullanmadan önce belirlemeniz gerekmektedir. PHP'de değişkenlerin türü otomatik olarak kullandığınız zaman belirlenir.

<hr />

<h3>Değişkenleri İsimlendirme Kuralları</h3>
<ul>
	<li>Bir değişken harfle, rakamla veya alt çizgi(_) ile başlamalıdır.</li>
	<li>Bir değişken sadece harf, rakam ve alt çizgi içerebilir(a-z, A-Z, 0-9, ve _ )</li>
	<li>Bir değişken boşluk içeremez. Eğer bir değişken birden çok isim içeriyorsa bunları ayırmak için alt çizgi kullanılabilir($degisken_adi) veya büyük harf ile başlayabilir($DegiskenAdi).</li>
</ul>