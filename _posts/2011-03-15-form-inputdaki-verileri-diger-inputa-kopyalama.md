---
ID: 97
post_title: >
  Form Inputdaki Verileri Diğer Inputa
  Kopyalama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery/form-inputdaki-verileri-diger-inputa-kopyalama-97.html
published: true
post_date: 2011-03-15 08:38:58
---
Merhaba arkadaşlar,

Bu örnek bir bölümdeki form input verilerini diğer form inputlara kopyalamak için son derece basit bir örnektir. Bir alandaki bilgiler diğer alanlara da girilebiliyorsa çok kullanışlı olur.

E-ticaret sitelerinde sık sık karşılaştığınız iletişim adresim aynı zamanda fatura adresim olsun seçeneğiyle aynıdır.

Hemen kodları sizinle paylaşmak istiyorum.. jQuery Kodlarımız:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(document).ready(function(){
    $("input#ayni").click(function(){
        if ($("input#ayni").is(':checked')){
            // Seçim yapildiginda kopyala
            $("input#iletisim-email").val($("input#email").val());
            $("input#iletisim-ad").val($("input#ad").val());
            $("input#iletisim-tel").val($("input#tel").val());
        }else{
            // Seçim kaldirildiginda iletisim kismini temizle
            $("input#iletisim-email").val("");
            $("input#iletisim-ad").val("");
            $("input#iletisim-tel").val("");
        }
    });
});</pre>
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;form&gt;
    &lt;p style="font-weight: bold;"&gt;Fatura&lt;/p&gt;
    Email: &lt;input type="text" name="email" id="email" value="test@trkodlama.com" /&gt;
    &lt;br /&gt;Ad: &lt;input type="text" name="ad" id="ad" value="TR Kodlama" /&gt;
    &lt;br /&gt;Telefon: &lt;input type="text" name="tel" id="tel" value="0555 555 55 55" /&gt;

    &lt;p style="padding-top: 15px; font-weight: bold;"&gt;Iletisim&lt;/p&gt;

    İletişim adresim fatura adresimle ayni olsun?: &lt;input type="checkbox" name="ayni" id="ayni" /&gt;
    &lt;br /&gt;Email: &lt;input type="text" name="email" id="iletisim-email" /&gt;
    &lt;br /&gt;Name: &lt;input type="text" name="ad" id="iletisim-ad" /&gt;
    &lt;br /&gt;Tel: &lt;input type="text" name="tel" id="iletisim-tel" /&gt;
&lt;/form&gt;</pre>
&nbsp;