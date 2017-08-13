---
ID: 5722
post_title: Sunucu Tarih ve Saatini Ayarlama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/sunucu-tarih-ve-saatini-ayarlama-5722.html
published: true
post_date: 2015-04-29 09:21:52
---
Merhaba arkadaşlar,

Bir web sitesi yaptık, canavar gibi çalışıyor. Her şeyin güzel olduğunu test ettik. Tam mutluluktan havaya uçacaksınız ki birde ne göresiniz. Saatler yanlış. Ya bir veya bir kaç saat ileri ya da geri. Canınız sıkıldı ve hemen <strong><a href="http://php.net/manual/tr/function.date-default-timezone-set.php" target="_blank">date_default_timezone_set</a></strong> kullanarak <strong>Europe/Istanbul</strong> olarak ayarladınız zaman diliminizi ve problemin geçtiğinden emin bir şekilde kaydedip sayfayı yenilediniz. Birde bakmışsınız sıkıntınız hala devam ediyor. (PHP'nin desteklediği zaman dilimleri için <a href="http://php.net/manual/tr/timezones.php" target="_blank">buraya</a> tıklayınız.)

İşin aslı sunucunuz zaten Europe/Istanbul olarak ayarlıydı fakat sunucunuzun saati yanlıştı. Bu sefer kendine zaman dilimi olarak bizden iki saat geri olan bir bölge seçebilirsiniz ama bu da sağlıklı bir çözüm değil. Sonuçta hata var ortada, hatayı gidermek yerine üstüne örtmeye çalışmak hiç doğru değil. O zaman gelelim ve sunucu saatimizi kontrol edelim.
<h3>Sunucu Saatini Nasıl Öğrenirim?</h3>
Sunucu saatini öğrenmek için <strong><em>date </em></strong>komutunu kullanırız.
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">date</pre>
Bize tarih, saat ve zaman dilimini bildirir.
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">[root@trkodlama ~]# date
Wed Apr 29 11:46:42 EEST 2015</pre>
EEST(East European Summer Time) doğu avrupa yaz saati anlamına geliyor. Yazın EEST zaman dilimindeyizdir aynı zamanda UTC+3 olarak da görebilirsiniz. Kışın ise EET(East European Time) yani doğu avrupa saati anlamına gelen dilimi kullanmaktayız. Bunu da UTC+2 olarak görebilirsiniz.
<h3>Sunucum Hangi Zaman Dilimlerini Destekliyor?</h3>
Bu sorunun cevabı için sunucunuza bakmak gerekir. Sunucunuzun desteklediği zaman dilimlerini <b><i>/usr/share/zoneinfo </i></b>klasöründe bulabilirsiniz. Burada dosyalar ve klasörler bulunur. Mesela Istanbul dosyası Europe klasörü altındadır.
<h3>Sunucumun Zaman Dilimini Nasıl Değiştirebilirim?</h3>
Önceki başlıkta Istanbul'un nerede olduğunu söyledim. <em><strong>/usr/share/zoneinfo/Europe/Istanbul </strong></em>da bulunur. Peki sunucumuzun zaman dilimini nasıl böyle ayarlayabiliriz?
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">export TZ=Europe/Istanbul</pre>
Bu komut ile zaman diliminizi ayarlayabilirsiniz.
<h3>Sunucumun Tarih ve Saatini Nasıl Değiştirebilirim?</h3>
Artık son noktaya geldik. Zaman dilimini ayarladık fakat gördükki sunucu saatimizde yanlış. O zaman yine date komutunu kullanarak tarih ve saatimizi ayarlayalım:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">date -s "29 APR 2015 09:10:00";</pre>
İşte bu kadar! Şu anda tarih ve saatimiz ayarlandı. Artık hiç bir problem yaşamayacaksınız :) Umarım işinize yarar ;)