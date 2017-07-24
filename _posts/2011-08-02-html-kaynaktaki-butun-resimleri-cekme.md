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

<pre class="lang:php decode:1 " >$curl = curl_init(&amp;quot;http://www.trkodlama.com&amp;quot;);
$agent = &amp;quot;Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.7.12) Gecko/20050915 Firefox/1.0.7&amp;quot;;
$curl = curl_init($url);
curl_setopt($curl, CURLOPT_USERAGENT, $agent); // Mozilla gibi g&ouml;r&uuml;nd&uuml;k
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1); // Burayı 0 yaparsanız sitenin &ccedil;ıktısını da ekrana basar. Bunu istemeyiz..
$data = curl_exec($curl);
curl_close($curl);

$images = array();
preg_match_all('/(img|src)=(&amp;quot;|')[^&amp;quot;'&amp;gt;]+/i', $data, $media);
unset($data);
$data=preg_replace('/(img|src)(&amp;quot;|'|=&amp;quot;|=')(.*)/i',&amp;quot;$3&amp;quot;,$media[0]);
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

// www.trkodlama.com adresindeki b&uuml;t&uuml;n resimleri $images dizisine aktardık. Bunun i&ccedil;eriğine de
// ş&ouml;yle bakalım
echo &amp;quot;&amp;lt;pre&amp;gt;&amp;quot;;
print_r($images);
echo &amp;quot;&amp;lt;/pre&amp;gt;&amp;quot;;</pre>

Kolay gelsin arkadaşlar,
<div></div>