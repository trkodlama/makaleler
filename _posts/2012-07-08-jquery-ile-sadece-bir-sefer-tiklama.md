---
ID: 952
post_title: jQuery ile Sadece Bir Sefer Tıklama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery/jquery-ile-sadece-bir-sefer-tiklama-952.html
published: true
post_date: 2012-07-08 21:10:17
---
Merhaba,

Bu makalede jQuery ile bir  elemente tıklandığında yapılan işlemin sadece bir kere yapılmasını nasıl sağlayacağınızı gösteriyorum. Açıklama biraz karışık olmuş olabilir. Örnekleyerek açıklayayım.

Bir butonunuz olsun. Bu butona ilk tıklandığı zaman alert() ile bir mesaj göstersin. İkinci ve sonraki tıklamalarda hiç bir işlem yapmasın.

jQuery'de bu işlemi yapmamızı sağlayan <strong>.one()</strong> fonksiyonu var. Bu fonksiyon hakkında daha fazla bilgi edinmek istiyorsanız <a href="http://api.jquery.com/one/" target="_blank"><strong>jQuery .one()</strong></a> sayfasına göz atın.

Bu işlemi iki farklı yöntemle gerçekleştirebiliriz. <strong>#bana_tikla </strong>id'li bir butonumuz olsun ve bu butona tıklayınca "Sadece bir kere bu yazıyı göreceksiniz" şeklinde bir alert versin.
<h3>Yöntem 1</h3>
<pre class="prettyprint lang-java" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$("#bana_tikla").one("click", function() {
      alert("Sadece bir kere bu yazıyı göreceksiniz.");
});</pre>
<h3>Yöntem 2</h3>
<pre class="prettyprint lang-java" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$("#bana_tikla").bind("click", function( event ) {
    alert("Sadece bir kere bu yazıyı göreceksiniz.");
    $(this).unbind(event);
});</pre>
Umarım açıklayıcı olmuştur ve istediğinizi verebilmişimdir. Basit bir işlem fakat bu fonksiyonu bilmeyebilirsiniz. Tıklamaları tek tek sayıp sadece ilkse şeklinde if'li işlemlerle eskiden kontrol ederdim. Bu nedenle bu makalenin faydalı olabileceğini düşünüp paylaştım.