---
ID: 110
post_title: jQuery ile Bir Formu Temizleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-bir-formu-temizleme-110.html
published: true
post_date: 2011-03-15 08:58:24
---
Merhaba,

Oluşturduğunuz formun sonuna Gönder ve Sıfırla şeklinde iki buton koydunuz. Sıfırla butonuna bastığınızda ise bazı form alanlarınızın içeriğinin değişmesini istemiyor olabilirsiniz. Bunun için aşağıdaki koddan faydalanabilirsiniz. Satır satır ne yaptığımızı açıkladım. Anlaşılır olduğunu düşünüyorum. Buyrun:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$(':input','#formid')  
    .not(':hidden') // Burada temizlenmesini istemediğiniz alanları belirtiyorsunuz. Ben hidden yaptım  
    .val('') // Burada alanlarınızın value=&amp;quot;&amp;quot; kısmını boşaltıyoruz. İsterseniz değiştirebilirsiniz.  
    .removeAttr('checked') // Checkbox'ları temizliyoruz  
    .removeAttr('selected'); // select ile seçtiğimiz option'ı sıfırladık</pre>
İşte bitti.. Bu kadar basitmiş jQuery ile form alanlarını temizlemek. Hemde ekstra bir kaç özellik ile beraber.

Kolay gelsin,