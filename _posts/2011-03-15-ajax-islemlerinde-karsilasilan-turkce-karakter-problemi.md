---
ID: 105
post_title: >
  AJAX İşlemlerinde Karşılaşılan
  Türkçe Karakter Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php/ajax-islemlerinde-karsilasilan-turkce-karakter-problemi-105.html
published: true
post_date: 2011-03-15 08:49:05
---
Merhaba arkadaşlar,

Başıma gelen bir problemi hemen sizlerle paylaşmak istedim. İki gün önce hayatıma jQuery'yi de sokmuş bulunmaktayım. Belki anlamışsınızdır. Neyse lafı fazla uzatmayalım.

Web sayfanıza jQuery ile herhangi bir sayfaya veri Post ederken; eğer post ettiğiniz veri de türkçe karakterler varsa ne yazık ki bu karakterler PHP sayfanıza anlaşılmaz karakterler olarak gönderiliyor. Türk alfabesinde yer alan "ı, ğ, Ğ, ü, Ü, ş, Ş, ç, Ç, ö, Ö" karakterleri bozuluyor. Bunun için verileri gönderdiğimiz PHP sayfasında değişkenimizi bir fonksiyon yardımıyla düzenliyoruz.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$degiskenAdi = $_POST["nameAlani"];</pre>
Şeklindeki değişkenimiz türkçe karakterler içeriyorsa bozuk bir şekilde ekrana basılır. Bunu düzeltmek için iconv() veya mb_convert_encoding() fonksiyonunu kullanacağız. Yukarıdaki değişkende değişiklik yapalım hemen:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$degiskenAdi = iconv("UTF-8", "ISO-8859-9", $_POST["nameAlani"]);</pre>
Bu sayede $_POST["nameAlani"] ile gelen türkçe karakterler düzeltildi. Artık $degiskenAdi'ni rahat rahat kullanabilirsiniz. Aynı zamanda:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$degiskenAdi = mb_convert_encoding($_POST["nameAlani"], "UTF-8", "ISO-8859-9");</pre>
fonksiyonuyla da aynı işlemi rahatlıkla gerçekleştirebilirsiniz.
Kolay gelsin,