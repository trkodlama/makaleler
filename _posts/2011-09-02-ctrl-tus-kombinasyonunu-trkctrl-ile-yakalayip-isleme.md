---
ID: 238
post_title: >
  CTRL + Tuş Kombinasyonunu trkCtrl İle
  Yakalayıp İşleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/ctrl-tus-kombinasyonunu-trkctrl-ile-yakalayip-isleme-238.html
published: true
post_date: 2011-09-02 00:44:53
---
Merhaba arkadaşlar,

Bir projem için jQuery ile ctrl ile "V" tuşuna basıldığında bir işlem yapması için uğraşıyordum... Uğraşlarım doğrultusunda bir sonuca vardım ve bir jQuery fonksiyonu ayarladım. Bu fonksiyon ile ctrl+tuş kombinasyonunu başarılı bir şekilde yakalıyorsunuz.

Aslında bu işlem için jshotkeys isimli bir jQuery eklentisi var. Fakat bu eklenti çok geniş bir kitleye hitap ediyor. Yani her tuşu kapsıyor. Biz sadece Ctrl+tuş işlemi için fonksiyon paylaşacağız. Fonksiyonumuzun adı trkCtrl'dir.

Kullanımı şu şekildedir:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(document).ready(function(){
    $.trkCtrl("C", function(){
        alert("Kopyala Yapıştır tabii ki yapacaksın ama en azından kaynak belirt!");
    });
});</pre>
Bu fonksiyon ile ilgili yaşadığınız problemleri lütfen yorum olarak yazmayı ihmal etmeyin. Sizlerin geri dönüşleriyle bu fonksiyon geliştirilecektir.
<p style="text-align: left;"><a href="http://www.trkodlama.com/demo/trk_ctrl/index.htm" target="_blank">DEMO
</a>[wpdm_file id=4]</p>