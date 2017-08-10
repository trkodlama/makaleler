---
ID: 223
post_title: HTML Kaynaktaki Bütün Resimleri Çekme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/html-kaynaktaki-butun-resimleri-cekme-223.html
published: true
post_date: 2011-08-02 00:11:28
---
Merhaba arkadaşlar,

Facebook'da bir web sayfası paylaştığınızda facebook size sitede bulunan resimleri sunuyordu. Sizde bu resimlerden seçip paylaşıyordunuz. Peki Facebook bir web sayfasındaki bütün resimleri çekebiliyorda siz neden çekemeyesiniz.

İşte bugün size bir web sayfasındaki bütün resimleri cURL ile bağlanıp regexp yardımıyla nasıl ayaklayacağımızı anlatıyorum. Hatta anlatmıyorum direkt olarak kodu paylaşıyorum:
<pre class="line-numbers"><code class="language-php">&lt;?php

$curl = curl_init("https://www.trkodlama.com");
$agent = "Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.7.12) Gecko/20050915 Firefox/1.0.7";
$curl = curl_init($url);
curl_setopt($curl, CURLOPT_USERAGENT, $agent); // Mozilla gibi göründük
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1); // Burayı 0 yaparsanız sitenin çıktısını da ekrana basar. Bunu istemeyiz..
$data = curl_exec($curl);
curl_close($curl);

$images = array();
preg_match_all('/(img|src)=("|\')[^"\'&gt;]+/i', $data, $media);

unset($data);

$data=preg_replace('/(img|src)("|\'|="|=\')(.*)/i',"$3",$media[0]);
foreach($data as $url)
{
	$info = pathinfo($url);
	if (isset($info['extension']))
	{
		if (($info['extension'] == 'jpg') ||
		    ($info['extension'] == 'jpeg') ||
		    ($info['extension'] == 'gif') ||
		    ($info['extension'] == 'png'))
			array_push($images, $url);
	}
}

// www.trkodlama.com adresindeki bütün resimleri $images dizisine aktardık. Bunun içeriğine de
// şöyle bakalım
echo "&lt;pre&gt;";
print_r($images);
echo "&lt;/pre&gt;";

?&gt;</code></pre>
Kolay gelsin arkadaşlar,
<div></div>