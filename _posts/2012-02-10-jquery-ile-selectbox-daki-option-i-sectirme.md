---
ID: 289
post_title: 'jQuery ile Selectbox&#8217;daki Option&#8217;ı Seçtirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-selectbox-daki-option-i-sectirme-289.html
published: true
post_date: 2012-02-10 02:47:31
---
Merhaba arkadaşlar,

Bir &lt;select&gt; form elemanınızın olduğunu düşünün ve bu elemandaki bir değeri linke vb. tıkladığınız zaman seçili hale getirmek istiyorsunuz. Bunu jquery ile basit bir şekilde yapabildiğimizi gördüm. Üzerinde uğraştığım bir projede ihtiyaç duydum, araştırdım ve buldum. Öncelikle olmazsa olmazımız olan jQuery kütüphanesinin sayfanızda yüklenmiş olması gerekiyor. jQuery'yi buraya tıklayarak edinebilirsiniz. Şimdi bir örnek select form oluşturalım:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;select name="sec"&gt; &lt;option selected="selected" value="varsayilan"&gt;Lütfen seçim yapın&lt;/option&gt;&lt;/select&gt;
&lt;select name="sec"&gt; &lt;option value="a"&gt;A&lt;/option&gt;&lt;/select&gt;
&lt;select name="sec"&gt; &lt;option value="b"&gt;B&lt;/option&gt;&lt;/select&gt;

&lt;!-- Şimdi A linkine tıklayınca value="a" olanı seçtirmek için gerekli linkleri hazırlayalım --&gt;
&lt;a onclick="sectir('a')" href="#"&gt;A&lt;/a&gt;
&lt;a onclick="sectir('b')" href="#"&gt;B&lt;/a</pre>
Şimdi burada kullandığımız sectir() fonksiyonunu hazırlayalım. Bu fonksiyonda yaptığımız iş çok basit. Öncelikle selected="selected" parametrelerini bulup siliyoruz. Daha value değerini girdiğimiz option'a selected="selected" parametresini ekliyoruz. Aşağıda fonksiyonumuz:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">function sectir(value){
    $("select#sec option[selected]").removeAttr("selected");
    $("select#sec option[value='"+value+"']").attr("selected", "selected");
}</pre>
Kullanımı hakkında bilgi sahibi olmuşsunuzdur. Faydalı olmuştur umarım,Kolay gelsin,