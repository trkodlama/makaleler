---
ID: 296
post_title: >
  JavaScript Fonksiyonunu Belirli Sürede
  Bir Çalıştırma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/javascript-fonksiyonunu-belirli-surede-bir-calistirma-296.html
published: true
post_date: 2012-01-15 02:57:16
---
Merhaba arkadaşlar,

Bu makalede setInterval ile nasıl belirli periyotlarda bir fonksiyon çalıştıracağımızı göstereceğim. Şimdi sayfada her 5 saniyede bir çalıştırılacak fonksiyonun kodunu yazalım:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">window.setInterval(function(){
 // Burada fonksiyonlarınızı çağırın
}, 5000);</pre>
Şimdi de bir örnek yapalım. Öcelikle bir fonksiyon oluşturalım. Bu fonksiyon kullanıcıya "TR Kodlama'ya gitmek ister misiniz?" sorusunu sorsun. Daha sonra bu soruyu her 60 saniyede bir tekrarlatalım. Kodlar aşağıdaki gibidir:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">function trkodlama(){
    var onay = confirm("TR Kodlama'ya gitmek ister misiniz?");
    if(onay==TRUE){
        location.href = "http://www.trkodlama.com";
    }
    else{
        alert("Siz bilirsiniz :)");
    }
}
window.setInterval(function(){
    trkodlama();
}, 60000);</pre>
Umarım faydalı olur arkadaşlar, kolay gelsin.