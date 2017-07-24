---
ID: 6323
post_title: >
  Google reCaptcha Responsive(Uyumlu)
  Tasarım Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/uyumlu-web-tasarim/google-recaptcha-responsiveuyumlu-tasarim-problemi-6323.html
published: true
post_date: 2017-01-23 02:31:12
---
Google reCaptcha aldınız sitenize koydunuz. Tarayıcı ile görüntülediğiniz de hiç bir problem görmediniz. Temanız uyumlu, birde değişikliklere mobil cihazınızdan baktınız ve o da ne?! Google reCaptcha kutunun dışına taşıyor. Şu anda fixlemek üzere olduğum bir durum aynı zamanda.

<img class="aligncenter size-full wp-image-6325" src="http://www.trkodlama.com/wp-content/uploads/2017/01/recaptcha-tasma.png" alt="" width="244" height="236" />

İlk olarak aşağıdaki CSS kodu'nu CSS dosyanıza ekleyin:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">.g-recaptcha {
  transform-origin: left top;
  -webkit-transform-origin: left top;
}</pre>
Daha sonra JavaScript dosyanıza aşağıdaki kodu ekleyin:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// Google reCaptcha Uyumluluk Çözümü

function uyumluReCaptcha() {
    // reCaptcha'nın genişliği
    var reCaptchaGen = 304;
    // reCaptcha'nın içinde olduğu kutunun genişliği
    var kapsulGen = $('.g-recaptcha').parent().width();
  
    if(reCaptchaGen &gt; kapsulGen) {
        // Oranlarını hesaplayalım
        var oran = kapsulGen / reCaptchaGen;
        // Elde ettiğimiz orana göre yeniden ölçekleyelim
        $('.g-recaptcha').css({
            'transform':'scale('+oran+')'
        });
    }
}

$(function() { 
 
    // Ölçekleme işlemini yapalım
    uyumluReCaptcha();
  
    /**
     * Pencere boyutu değiştiği anda tekrar ölçekleyelim
     * throttle kütüphanesi
     * https://cdnjs.cloudflare.com/ajax/libs/jquery-throttle-debounce/1.1/jquery.ba-throttle-debounce.min.js
     */
    $(window).resize( $.throttle( 100, uyumluReCaptcha ) );
  
});</pre>
Çalışan demo için <a href="https://codepen.io/oralunal/pen/GrmYOR" target="_blank">buraya</a> tıklayınız. Kolay gelsin,