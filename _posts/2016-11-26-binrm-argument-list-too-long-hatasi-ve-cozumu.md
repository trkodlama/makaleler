---
ID: 5913
post_title: '/bin/rm: Argument list too long Hatası ve Çözümü'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/binrm-argument-list-too-long-hatasi-ve-cozumu-5913.html
published: true
post_date: 2016-11-26 04:33:36
---
Merhaba arkadaşlar,

Bugün cPanel'den hesapları kurcalarken bir web sayfamın default mail adresinin boyutunun çok büyük olduğunu farkettim. Sebebini merak edip gelen maillere baktığımda yıllardır 10 dakikada bir çalışan CronJobs her çalıştığında varsayılan mail adresine e-posta gönderdiğini gördüm. Tarayıcı aracılığıyla Horde arayüzünü kullanarak silmeye çalıştım fakat bir kaç yüz binlik mailleri silmeye çalışmak sadece tarayıcımın kitlenip çökmesine sebep olurken hiç bir işlem yapmamasıyla son buluyordu.

Daha sonra SSH ile /<strong>home/kullanici_adi/mail/cur/</strong> klasörüne girerek klasörün içini şu şekilde temizlemeye kalktım:

<pre class="lang:bash decode:1 " >rm -fv *</pre>

<strong>DİKKAT! Bu komutu kullanırken içinde bulunduğum klasördeki bütün dosyaları siliyorum. Tam olarak ne olduğunu bilmiyorsanız lütfen denemeyin!.</strong>

Fakat o kadar çok e-posta vardı ki silemedi ve şu hatayı verdi:

<blockquote>/bin/rm: Argument list too long</blockquote>

Madem <strong>rm</strong> ile bütün dosyaları silemiyorum o zaman neden tek tek silmeyelim, değil mi? Tek tek silmek için şu komutu kullanabilirsiniz:

<pre class="lang:bash decode:1 " >find . -name &amp;quot;*&amp;quot; -print | xargs rm</pre>

<strong>Dikkat! Bu komut içinde bulunduğunuz klasördeki bütün dosyaları siler. Tam olarak ne yaptığınızdan emin değilseniz lütfen denemeyin.</strong>

Bu sayede bütün dosyaları tek kalemde silebileceksiniz.

Sağlıcakla kalın,