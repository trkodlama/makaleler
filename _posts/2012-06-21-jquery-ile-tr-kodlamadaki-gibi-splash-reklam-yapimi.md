---
ID: 796
post_title: jQuery ile Splash Reklam Yapımı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ipuclari/jquery-ile-tr-kodlamadaki-gibi-splash-reklam-yapimi-796.html
published: true
post_date: 2012-06-21 06:01:45
---
TR Kodlama'ya ilk girdiğinizde ve her beş sayfa gezdiğinizde sizden bizi desteklemeniz için tıklamanızı istediğimiz bir reklam görüyorsunuz. Bu makale de bunun nasıl yapılacağını anlatıyorum.

TR Kodlama'daki reklam şu şekilde çalışır. Sayfa yüklenir. Siteyi tamamen kaplayacak koyu arkaplan renkli bir div oluşturulur. Bunun hemen önüne reklam konulur. Bu sistemin çalışma mantığı budur.

Şimdi öncelikle işin HTML kısmını yazıyorum:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;div class="kaplayici"&gt;&lt;!-- Genel arkaplan --&gt;
 &lt;!-- Reklam Alanımız --&gt;
 &lt;div class="reklam_popup"&gt;
  &lt;img src="birseyler.png" width="800" height="600" /&gt;&lt;!-- Reklamımız --&gt;
 &lt;/div&gt;
 &lt;!-- Reklam Alanı Bitişi --&gt;
 &lt;!-- Bu alanda geri sayım işlemimiz yer alıyor. Ve bir de metnimiz var --&gt;
 &lt;div class="yazi"&gt;
 &lt;span id="sayac"&gt;15&lt;/span&gt; sn. sonra kalkacak.. &lt;b&gt;Yazılar yazılar yazılar..&lt;/b&gt;
 &lt;/div&gt;

 &lt;!-- Bu da 15 sn. beklemek istemeyen kullanıcılar için Reklamı kapat seçeneğimiz..
 &lt;span class="kapat" onclick="kapat()"&gt;Kapat&lt;/span&gt;
&lt;/div&gt;</pre>
Şimdi birde bunun CSS'ini paylaşalım hemen:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">.kaplayici{
 background-color: #DDD;
 position: fixed;
 height: 100%;
 width: 100%;
 top: 0px;
 left: 0px;
 z-index: 10000000;
}
.reklam_popup{
 position: fixed;
 z-index: 9999;
 height: 300px;
 width: 336px;
 left: 10px;
 top: 30px;

}
div.yazi{
 position: fixed;
 z-index: 9999;
 width: 100%;
 left: 10px;
 top: 3px;
 line-height: 15px;
 color: white;
}
div#sayac{
 font-weight: bold;
 font-size: 16px;
}
span.kapat{
 position: fixed;
 top: 15px;
 left: 770px;
 font-weight: bold;
 font-size: 14px;
 z-index: 9999;
 cursor: pointer;
}</pre>
Yetmedi! Birde en önemli silahımız olan jQuery var. Bu kodların çalışması için jQuery kütüphanesini sayfaya çağırmanız gerektiğini unutmayın:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// Bu fonksiyon Kapat yazısına tıklatığımız zaman bütün o html etiketlerini sayfadan kaldırır.
function kapat(){
 $(".kaplayici").remove();
}

// Geri sayım fonksiyonudur. 15 saniyeden geriye sayar.
var enaz=0;
function geriSayim(){
 var deger=parseInt($('#sayac').html());
 $('#sayac').text(deger-1);
 if(deger-1!=enaz){ setTimeout('geriSayim()',1000); }
 else{ kapat(); }
}

// Ve geri sayım fonksiyonunu çalıştırdık
geriSayim();</pre>
Şimdi birde PHP'de SESSION'larla bu kullanıcının giriş çıkışlarını kontrol edelim. Kişi ilk defa giriyorsa ekrana bu reklamı bastıralım. Daha sonra da her 5 sayfa görüntülemesinden sonra ekrana bu reklamı bastırmaya devam edelim.

Sonuç olarak karşımıza şu şekilde bir ürün çıkıyor. Aşağıdaki kod başarılı bir şekilde çalışıyor. Şimdi index.php adında bir dosya oluşturun ve içine aşağıdaki kodları yazın:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
# "kacinci" isimli oturum kullanıcının o oturumda siteye kaçıncı girişi olduğunu kontrol ediyor.
# her sayfa yenilediğinde $_SESSION["kacinci"] bir artıyor
# ilk sayfa görüntülediğinde ve her 5 sayfa görüntülediğinde $bastir = 1 oluyor
# $bastir = 1 olduğu durumlarda &lt;body&gt; etiketleri arasındaki reklam çalışır hale geliyor
if(!isset($_SESSION["kacinci"])){
    $_SESSION["kacinci"] = 0;
    $bastir = 1;
}
else{
    $_SESSION["kacinci"] = $_SESSION["kacinci"] + 1;
    if(($_SESSION["kacinci"]%5)==0) $bastir = 1;
    else $bastir = 0;
}
?&gt;

&lt;html&gt;
    &lt;head&gt;
        &lt;title&gt;jQuery Reklam&lt;/title&gt;
        &lt;script type="text/javascript" src="jQuery.js"&gt;&lt;/script&gt;
        &lt;style&gt;
        .kaplayici{
            background-color: #DDD;
            position: fixed;
            height: 100%;
            width: 100%;
            top: 0px;
            left: 0px;
            z-index: 10000000;
        }
        .reklam_popup{
            position: fixed;
            z-index: 9999;
            height: 300px;
            width: 336px;
            left: 10px;
            top: 30px;

        }
        div.yazi{
            position: fixed;
            z-index: 9999;
            width: 100%;
            left: 10px;
            top: 3px;
            line-height: 15px;
            color: white;
        }
        div#sayac{
            font-weight: bold;
            font-size: 16px;
        }
        span.kapat{
            position: fixed;
            top: 15px;
            left: 770px;
            font-weight: bold;
            font-size: 14px;
            z-index: 9999;
            cursor: pointer;
        }
        &lt;/style&gt;
    &lt;/head&gt;
    &lt;body&gt;
    &lt;?php if($bastir == 1){ ?&gt;
        &lt;div class="kaplayici"&gt;
            &lt;div class="reklam_popup"&gt;
                &lt;img src="reklam.png" width="800" height="600" /&gt;
            &lt;/div&gt;
            &lt;div class="yazi"&gt;
                &lt;span id="sayac"&gt;15&lt;/span&gt; sn. sonra kalkacak.. &lt;b&gt;Reklama tıklayarak bize destek olabileceğinizi unutmayın...&lt;/b&gt;
            &lt;/div&gt;
            &lt;span class="kapat" onclick="kapat()"&gt;Kapat&lt;/span&gt;
        &lt;/div&gt;
        &lt;script&gt;
        // Bu fonksiyon Kapat yazısına tıklatığımız zaman bütün o html etiketlerini sayfadan kaldırır.
        function kapat(){
                $(".kaplayici").remove();
        }
 
        // Geri sayım fonksiyonudur. 15 saniyeden geriye sayar.
        var enaz=0;
        function geriSayim(){
                var deger=parseInt($('#sayac').html());
                $('#sayac').text(deger-1);
                if(deger-1!=enaz){ setTimeout('geriSayim()',1000); }
                else{ kapat(); }
        }
 
        // Ve geri sayım fonksiyonunu çalıştırdık
        geriSayim();
        &lt;/script&gt;
    &lt;?php } ?&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>
Arkaplan gri ama transparan olsun isterseniz aşağıdaki kodu kullanmalısınız. Aşağıdaki kodda .kaplayici class'ına opacity değerleri verdik. Ve bu class'ın bağlı bulunduğu divin için boş bıraktık. Farklı opacity değerleri kullanmak için TR Kodlama'nın <a href="http://www.trkodlama.com/demo/css_opacity_olusturucu/" target="_blank">CSS Opacity Oluşturucusu</a>'nu kullanabilirsiniz.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
# "kacinci" isimli oturum kullanıcının o oturumda siteye kaçıncı girişi olduğunu kontrol ediyor.
# her sayfa yenilediğinde $_SESSION["kacinci"] bir artıyor
# ilk sayfa görüntülediğinde ve her 5 sayfa görüntülediğinde $bastir = 1 oluyor
# $bastir = 1 olduğu durumlarda &lt;body&gt; etiketleri arasındaki reklam çalışır hale geliyor
if(!isset($_SESSION["kacinci"])){
    $_SESSION["kacinci"] = 0;
    $bastir = 1;
}
else{
    $_SESSION["kacinci"] = $_SESSION["kacinci"] + 1;
    if(($_SESSION["kacinci"]%5)==0) $bastir = 1;
    else $bastir = 0;
}
?&gt;

&lt;html&gt;
    &lt;head&gt;
        &lt;title&gt;jQuery Reklam&lt;/title&gt;
        &lt;script type="text/javascript" src="jQuery.js"&gt;&lt;/script&gt;
        &lt;style&gt;
        .kaplayici{
            background-color: #DDD;
            position: fixed;
            height: 100%;
            width: 100%;
            top: 0px;
            left: 0px;
            z-index: 9990;
            -moz-opacity: 0.70;
            -khtml-opacity: 0.70;
            opacity: 0.70;
            -ms-filter:"progid:DXImageTransform.Microsoft.Alpha"(Opacity=70);
            filter: progid:DXImageTransform.Microsoft.Alpha(opacity=70);
            filter:alpha(opacity=70);
        }
        .reklam_popup{
            position: fixed;
            z-index: 9999;
            height: 300px;
            width: 336px;
            left: 10px;
            top: 30px;

        }
        div.yazi{
            position: fixed;
            z-index: 9999;
            width: 100%;
            left: 10px;
            top: 3px;
            line-height: 15px;
            color: white;
        }
        div#sayac{
            font-weight: bold;
            font-size: 16px;
        }
        span.kapat{
            position: fixed;
            top: 15px;
            left: 770px;
            font-weight: bold;
            font-size: 14px;
            z-index: 9999;
            cursor: pointer;
        }
        &lt;/style&gt;
    &lt;/head&gt;
    &lt;body&gt;
    &lt;?php if($bastir == 1){ ?&gt;
        &lt;div class="kaplayici"&gt;&lt;/div&gt;
        &lt;div class="reklam_popup"&gt;
            &lt;img src="reklam.png" width="800" height="600" /&gt;
        &lt;/div&gt;
        &lt;div class="yazi"&gt;
            &lt;span id="sayac"&gt;15&lt;/span&gt; sn. sonra kalkacak.. &lt;b&gt;Reklama tıklayarak bize destek olabileceğinizi unutmayın...&lt;/b&gt;
        &lt;/div&gt;
        &lt;span class="kapat" onclick="kapat()"&gt;Kapat&lt;/span&gt;

        &lt;script&gt;
        // Bu fonksiyon Kapat yazısına tıklatığımız zaman bütün o html etiketlerini sayfadan kaldırır.
        function kapat(){
                $(".kaplayici").remove();
        }
 
        // Geri sayım fonksiyonudur. 15 saniyeden geriye sayar.
        var enaz=0;
        function geriSayim(){
                var deger=parseInt($('#sayac').html());
                $('#sayac').text(deger-1);
                if(deger-1!=enaz){ setTimeout('geriSayim()',1000); }
                else{ kapat(); }
        }
 
        // Ve geri sayım fonksiyonunu çalıştırdık
        geriSayim();
        &lt;/script&gt;
    &lt;?php } ?&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>
jQuery geri sayımı ile ilgili fonksiyonu daha önce paylaşmıştık. <a title="jQuery ile Rakam Sayımı Yapmak" href="http://www.trkodlama.com/makaleler/javascript/jquery/jquery-ile-rakam-sayimi-yapmak-66.html" target="_blank">Bu sayfadan</a> onunla ilgili bilgi alabilirsiniz. Umarım faydalı olmuştur.

Kolay gelsin,