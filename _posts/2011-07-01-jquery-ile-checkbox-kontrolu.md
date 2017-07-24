---
ID: 207
post_title: jQuery ile Checkbox Kontrolü
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery/jquery-ile-checkbox-kontrolu-207.html
published: true
post_date: 2011-07-01 22:47:06
---
Merhaba arkadaşlar,

Bu makalemde yine jQuery ile bir kontrol işlemi gerçekleştiriyoruz. jQuery ile bir checkbox'ın(seçim kutusunun) seçili olup olmadığını nasıl kontrol edebileceğimizi anlatıyorum. Bunun için checked attribute'una bakacağız(kusura bakmayın attribute kelimesinin türkçe karşılığı nedir bilmiyorum). Önce bir adet input oluşturalım:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input id="sec" type="checkbox" value="1" /&gt; Seçersen alert verir</pre>
Şimdi bu input seçildiğinde alert ile ekrana seçim kutusunun işaretlendiğini belirtelim:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(document).ready(function(){
    $("#sec").click(function(){
        if( $("#sec").attr("checked")=="checked" ) {
            alert("Seçim kutusu işaretlendi..");
        }
        else {
            alert("Seçim kutusu işareti kaldırıldı");
        }
    });
});</pre>
<strong>GÜNCELLEME (26 Kasım 2016)</strong>

Chrome'un artık checked özelliği ile işaretlemediğini farkettim checkbox'ları. O nedenle ekstra bir yöntem paylaşmak istedim:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(document).ready(function(){
    $("#sec").click(function(){
        if( $("#sec").is(':checked') ) {
            alert("Seçim kutusu işaretlendi..");
        }
        else {
            alert("Seçim kutusu işareti kaldırıldı");
        }
    });
});</pre>
Yukarıdaki javascript kodunun neler yaptığını anlatalım.. Öncelikle id="sec" olan elementine tıklandığında if...else ile id="sec" elementinin checked niteliğine bakıyoruz. eğer checked="checked" şeklinde ise işaretlendiğini belirtiyor ve seçim kutusu işaretlendi alerti veriyor. Eğer tekrar tıklanıp işaret kaldırılırsa yine aynı kontroller yapılıyor fakat bu sefer checked="checked" olmadığı için seçim kutusu işareti kaldırıldı alerti veriliyor.
Umarım anlatabilmişimdir arkadaşlar, basit bir işlem zaten.
Kolay gelsin,