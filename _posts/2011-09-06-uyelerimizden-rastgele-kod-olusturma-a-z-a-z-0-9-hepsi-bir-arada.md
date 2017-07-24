---
ID: 246
post_title: >
  Rastgele Kod Oluşturma (a-z, A-Z, 0-9
  hepsi bir arada)
author: damatmedya
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/uyelerimizden-rastgele-kod-olusturma-a-z-a-z-0-9-hepsi-bir-arada-246.html
published: true
post_date: 2011-09-06 01:19:57
---
Merhaba arkadaşlar,
Bugünkü makalede sizlere istediğiniz uzunlukta a'dan z'ye, A'dan Z'ye ve 0'dan 9'a rastgele kod oluşturmanızı sağlayacak bir PHP fonksiyonu veriyorum.

<pre class="lang:php decode:1 " >&amp;lt;?php
function kod($uzunluk){
	$karakterler = array(); // boş bir dizi oluşturuyoruz
	$karakterler = array_merge(range(0,9),range('a','z'),range('A','Z')); // range = belirtilen aralık arasında dizi oluşturur
	// array_merge = dizileri arka arkaya ekler
	srand((float)microtime()*100000); // belirli bir d&uuml;zen i&ccedil;erisinde rastgele sayı &uuml;retir
	shuffle($karakterler); // dizideki elemanları rasgele sıralar
	$sonuc = ''; // boş bir sonuc değişkeni oluşturuyoruz
	for($i=0; $i&amp;lt;$uzunluk; $i++){
		$sonuc .= $karakterler[$i]; // karakterleri birleştirir&nbsp;
	}
	unset($karakterler); // tanımlanmamış hale getirir
	echo $sonuc; // &ccedil;ıkan sonucu ekrana yazdırır
}
// kullanımı
kod(5); // 5 haneli rastgele kod &uuml;retir isteğe g&ouml;re ayarlanabilir
?&amp;gt;</pre>

Umarım faydalı olur arkadaşlar, kolay gelsin,