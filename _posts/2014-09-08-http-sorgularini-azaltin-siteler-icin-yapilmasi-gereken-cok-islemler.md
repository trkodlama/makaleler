---
ID: 5438
post_title: 'HTTP Sorgularını Azaltın &#8211; Websitenizi Hızlandırmanın En İyi Yolu'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/http-sorgularini-azaltin-siteler-icin-yapilmasi-gereken-cok-islemler-5438.html
published: true
post_date: 2014-09-08 15:40:36
---
Bir çok web kullanıcısına site ziyaretlerinde resimleri, scriptleri, Flash'ları vb. dosyaların yüklenmesine çok vakit ayırıyor. Zengin arayüzlü web sayfalarında büyük problem olabiliyor bu. O zaman bu problem en güzel sorgu sayısını azaltarak başaçıkabiliriz.

Değerlendirmeniz gereken bazı yöntemler:
<ul>
	<li style="font-weight: inherit; font-style: inherit;"><strong>CSS ve JS dosyalarınızı birleştirin.</strong> Dosyaları birleştirmek HTTP azaltmanın yoludur. Bu işlemi CSS dosyalarınız için şöyle yapabilirsiniz. Bir tane boş CSS dosyası oluşturursunuz ve diğer CSS dosyalarınızın içeriğini sırasıyla eklersiniz. Aynı işlemi JS dosyaları içinde yapabilirsiniz. Böylelik siteniz 7 JS dosyası çağıracağını bir tane çağırır.</li>
</ul>
<ul>
	<li style="font-weight: inherit; font-style: inherit;"><strong style="font-style: inherit;"><a style="font-weight: inherit; font-style: inherit; color: #8dc03c;" title="CSS Sprites" href="http://alistapart.com/articles/sprites" target="_blank">CSS Sprites</a>. </strong>CSS Sprites arka plan resimleri sorguları azaltmak için bir yöntemdir. Tek yapmanız gereken bütün arka plan resimlerini bir resimde toplamak. Daha sonra <a style="font-weight: inherit; font-style: inherit; color: #8dc03c;" title="Background Image" href="http://www.w3schools.com/css/pr_background-image.asp" target="_blank"><strong style="font-style: inherit;">background- image</strong></a> ve <strong style="font-style: inherit;"><a style="font-weight: inherit; font-style: inherit; color: #8dc03c;" title="Background Posotion" href="http://www.w3schools.com/css/pr_background-position.asp" target="_blank">background-position</a> </strong>kullanarak bu arkaplan resimlerini ayarlamak.</li>
</ul>
<ul>
	<li style="font-weight: inherit; font-style: inherit;"><span style="font-weight: inherit; font-style: inherit; color: #888888;"><a style="font-weight: inherit; font-style: inherit; color: #8dc03c;" title="Image Maps" href="http://www.w3.org/TR/html401/struct/objects.html#h-13.6" target="_blank"><strong style="font-style: inherit;">Image maps</strong></a></span> bir kaç tane resmi tek resim olarak birleştirir. Genel olarak dosya boyutu aynıdır fakat HTTP sorgularını düşürmesinden ötürü sitenizi hızlandıracaktır.</li>
</ul>
Optimizasyonun anahtar hamlesi HTTP sorgularını azaltmaktır. Önbellekleme çalışmalarından ziyade bu işlem daha faydalı olacaktır. Ziyaretçilerinizin çoğunun boş bir önbellekle sizi ziyaret ettiğini unutmayın. HTTP sorgularını azaltma sayfa açılış hızını düşürecektir.