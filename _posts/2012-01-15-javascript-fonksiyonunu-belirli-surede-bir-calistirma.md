---
ID: 296
post_title: >
  JavaScript Fonksiyonunu Belirli Sürede
  Bir Çalıştırma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/javascript-fonksiyonunu-belirli-surede-bir-calistirma-296.html
published: true
post_date: 2012-01-15 02:57:16
---
Bu makalede setInterval ile belirli periyotlarda bir fonksiyonu nasıl çalıştıracağımızı göstereceğim. Şimdi sayfada her 5 saniyede bir çalıştırılacak fonksiyonun kodunu yazalım:
<pre class="line-numbers"><code class="language-javascript">window.setInterval(function(){
      // Burada fonksiyonlarınızı çağırın
}, 5000);</code></pre>
Şimdi de bir örnek yapalım. Öcelikle bir fonksiyon oluşturalım. Bu fonksiyon kullanıcıya "TR Kodlama'ya gitmek ister misiniz?" sorusunu sorsun. Daha sonra bu soruyu her 60 saniyede bir tekrarlatalım. Kodlar aşağıdaki gibidir:
<pre class="line-numbers" data-line="12"><code class="language-javascript">function trkodlama(){
    var onay = confirm("TR Kodlama'ya gitmek ister misiniz?");
    if(onay == TRUE){
        location.href = "https://www.trkodlama.com";
    }
    else{
        alert("Siz bilirsiniz :)");
    }
}
window.setInterval(function(){
    trkodlama();
}, 60000);</code></pre>
Umarım faydalı olur arkadaşlar, kolay gelsin.