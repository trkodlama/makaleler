---
ID: 447
post_title: 'Smarty&#8217;de .tpl Dosyasının İçine Eklenen Dosyanın Önbelleğe Alınmaması'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/smartyde-tpl-dosyasinin-icine-eklenen-dosyanin-onbellege-alinmamasi-447.html
published: true
post_date: 2012-04-16 16:28:15
---
Merhaba arkadaşlar,

Uzun bir zamandır yeni bir yazı ekleyemiyordum. Bugünse Smarty Template Engine hakkında merak edilen bir sorunun çözümünü paylaşıyorum. Çözümü aslında oldukça basit fakat nasıl arama yapacağımı bilmediğim için çözümü bulmak benim içinde zor oldu. Öncelikle "Smarty template engine ismi verilen bu motor ne işe yarıyor?" ondan bahsetmek istiyorum.
<h3>Smarty Nedir?</h3>
Bu konu hakkında uzun bir açıklama yapmayacağım. Smarty bir template motorudur. Daha güzel bir açıklama isterseniz kullanıcı taraflı kodlamayı ve arka plan kodlamasını birbirinden ayırmanızı sağlayacak muazzam güzellikte bir sınıftır. Güven ATBAKAN daha önce bu konuya bloğunda değinmiştir. Daha detaylı bir açıklama isterseniz <a href="http://www.guvenatbakan.net/2010/09/21/smarty-ile-calismak/" target="_blank">buraya</a> tıklayınız.
<h3>Tekrar Sorunumuza Dönelim</h3>
Öncelikle iki tane tpl dosyası oluşturalım. bunlar index.tpl ve random.tpl dosyaları olsun. random.tpl dosyasını index.tpl dosyasına include edeceğiz. Ve random.tpl dosyasına her zaman rastgele rakamsal değerler gelecek. Bunu nasıl yapacağız görelim..

index.tpl:

<pre class="lang:html decode:1 " >&amp;lt;p&amp;gt;Bu index.tpl dosyası random.tpl dosyasını i&ccedil;erir. İşte rastgele sayımız aşağıdaki gibidir:&amp;lt;/p&amp;gt;
&amp;lt;p&amp;gt;{include file=&amp;quot;template/random.php&amp;quot;}&amp;lt;/p&amp;gt;</pre>

Şimdi random.tpl dosyasının içeriğini yazalım.. random.tpl:

<pre class="lang:html decode:1 " >{$RANDOM}</pre>

Şimdi de bunların işleneceği index.php dosyamızı oluşturalım. index.php:

<pre class="lang:php decode:1 " >&amp;lt;?php
include &amp;quot;smarty.php&amp;quot;; // Smarty k&uuml;t&uuml;phanesini ekleyelim
# Smarty'yi başlatalım
$smarty = new Smarty;
# &Ouml;nbelleklemeyi başlatalım
$smarty-&amp;gt;caching = true;
$smarty-&amp;gt;cache_lifetime = 3600;

# Şimdi random bir sayı se&ccedil;elim
$rastgele = rand(0,99999);
# Bu random sayıyı smartye tanıtalım :)
$smarty-&amp;gt;assign(&amp;quot;RANDOM&amp;quot;, $rastgele); // Artık tpl dosyasında RANDOM g&ouml;rd&uuml;ğ&uuml; yere rastgele değişkenini basacak

# Template dosyasını se&ccedil;ip &ccedil;alıştıralım
$smarty-&amp;gt;display('template/index.tpl');
?&amp;gt;</pre>

Şimdi burada problem şu: biz önbellekleme açık olsun istiyoruz. Her seferinde index.tpl yeniden oluşturulmasın istiyoruz fakat random.tpl her seferinde yeniden oluşturulmasını istiyoruz. İşte bunu nasıl yapacağımızı aşağıda gösteriyorum.
<h3>{nocache}...{/nocache} kurtarıcı etiketleri</h3>
index.tpl dosyasında hatırladığınız gibi include file komutu ile random.tpl'i çekmiştik. Şimdi index.tpl dosyasındaki o komutu nocache etiketleri arasında yazıyoruz:

<pre class="lang:html decode:1 " >&amp;lt;p&amp;gt;Bu index.tpl dosyası random.tpl dosyasını i&ccedil;erir. İşte rastgele sayımız aşağıdaki gibidir:&amp;lt;/p&amp;gt;
&amp;lt;p&amp;gt;{nocache}{include file=&amp;quot;template/random.tpl&amp;quot;}{/nocache}&amp;lt;/p&amp;gt;</pre>

İşte bu şekilde nocache etiketleri arasına yazdığınız zaman bu kısım önbelleğe alınmayacaktır. Bu bütün her şey için geçerlidir. Değişkenleri nocache arasına yazabilirsiniz. Yani tpl dosyasında değişebilecek herşeyi nocache arasına yazabilirsiniz.

Sorularınızı yorum olarak veya <a href="http://forum.trkodlama.com" target="_blank">forumdan</a> sorabilirsiniz.

[wpdm_file id=3]