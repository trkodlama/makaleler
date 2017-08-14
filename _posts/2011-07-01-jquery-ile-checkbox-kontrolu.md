---
ID: 207
post_title: jQuery ile Checkbox Kontrolü
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-checkbox-kontrolu-207.html
published: true
post_date: 2011-07-01 22:47:06
---
Merhaba arkadaşlar,

Bu makalemde yine jQuery ile bir kontrol işlemi gerçekleştiriyoruz. jQuery ile bir checkbox'ın(seçim kutusunun) seçili olup olmadığını nasıl kontrol edebileceğimizi anlatıyorum. Bunun için checked attribute'una bakacağız(kusura bakmayın attribute kelimesinin türkçe karşılığı nedir bilmiyorum). Önce bir adet input oluşturalım:
<pre class="line-numbers"><code class="language-html">&lt;input id="sec" type="checkbox" value="1" /&gt; Seçersen alert verir</code></pre>
Şimdi bu input seçildiğinde alert ile ekrana seçim kutusunun işaretlendiğini belirtelim:
<pre class="line-numbers"><code class="language-javascript">$(document).ready(function(){
    $("#sec").click(function(){
        if( $("#sec").attr("checked")=="checked" ) {
            alert("Seçim kutusu işaretlendi..");
        }
        else {
            alert("Seçim kutusu işareti kaldırıldı");
        }
    });
});</code></pre>
<strong>GÜNCELLEME (26 Kasım 2016)</strong>

Chrome'un artık <code>checked</code> özelliği ile işaretlemediğini farkettim checkbox'ları. O nedenle ekstra bir yöntem paylaşmak istedim:
<pre class="line-numbers"><code class="language-javascript">$(document).ready(function(){
    $("#sec").click(function(){
        if( $("#sec").is(':checked') ) {
            alert("Seçim kutusu işaretlendi..");
        }
        else {
            alert("Seçim kutusu işareti kaldırıldı");
        }
    });
});</code></pre>
Yukarıdaki javascript kodunun neler yaptığını anlatalım.. Öncelikle <code>id="sec"</code> olan elementine tıklandığında <code>if</code>...<code>else</code> ile <code>id="sec"</code> elementinin <code>checked</code> niteliğine bakıyoruz. eğer <code>checked="checked"</code> şeklinde ise işaretlendiğini belirtiyor ve seçim kutusu işaretlendi alerti veriyor. Eğer tekrar tıklanıp işaret kaldırılırsa yine aynı kontroller yapılıyor fakat bu sefer <code>checked="checked"</code> olmadığı için seçim kutusu işareti kaldırıldı alerti veriliyor.

Umarım anlatabilmişimdir arkadaşlar, basit bir işlem zaten. Kolay gelsin,