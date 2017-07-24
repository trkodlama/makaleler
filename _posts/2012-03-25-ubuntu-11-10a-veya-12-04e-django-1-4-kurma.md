---
ID: 413
post_title: 'Ubuntu 11.10&#8217;a veya 12.04&#8217;e Django 1.4 Kurma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ubuntu-11-10a-veya-12-04e-django-1-4-kurma-413.html
published: true
post_date: 2012-03-25 04:47:50
---
Python programlamacılar için Django web uygulamaları geliştirilebilinecek en iyi framework kuşkusuz. Bu framework tamamen ücretsiz ve açık kaynak kodludur.

Denk geldim ve paylaşmak istedim. Django 1.4 sürümü çıktı. Fakat Ubuntu 12.04 ve 11.10 veya daha eski versiyonlar için 1.4 sürümünü resmi repo'sundan indirmeniz mümkün olmuyor. Bu nedenle kurulumu manuel yapmanız gerekiyor. Bunun için yapacağımız aşamalar şu şekilde:
<ol>
	<li>Django 1.4'ü indiriyoruz.</li>
	<li>Daha sonra içindekileri çıkarıyoruz.</li>
	<li>Django-1.4 klasörünün içine geçiyoruz ve</li>
	<li>Kurulumu gerçekleştiriyoruz.</li>
</ol>
Bu kurulumu yapabilmek için aşağıdaki komutları terminalde sırayla yazmanız yeterli olacaktır.

[text]wget &amp;quot;http://www.djangoproject.com/download/1.4/tarball/&amp;quot;
tar xzvf Django-1.4.tar.gz
cd Django-1.4
sudo python setup.py install[/text]

Umarım faydalı olur, kolay gelsin.