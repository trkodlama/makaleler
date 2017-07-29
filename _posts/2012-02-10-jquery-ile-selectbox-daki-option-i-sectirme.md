---
ID: 289
post_title: >
  jQuery ile Select Form Elemanını
  Değerine Göre Selected Yaptırma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/jquery-web-tasarim-2/jquery-ile-selectbox-daki-option-i-sectirme-289.html
published: true
post_date: 2012-02-10 02:47:31
---
Merhaba arkadaşlar,

Bir <code>&lt;select&gt;</code> form elemanınızın olduğunu düşünün ve bu elemandaki bir değeri linke vb. tıkladığınız zaman seçili hale getirmek istiyorsunuz. Bunu jquery ile basit bir şekilde yapabildiğimizi gördüm. Üzerinde uğraştığım bir projede ihtiyaç duydum, araştırdım ve buldum. Öncelikle olmazsa olmazımız olan jQuery kütüphanesinin sayfanızda yüklenmiş olması gerekiyor. jQuery'yi buraya tıklayarak edinebilirsiniz. Şimdi bir örnek select form oluşturalım:
<pre class="line-numbers"><code class="language-markup">&lt;select name="sec"&gt;
    &lt;option selected="selected" value="varsayilan"&gt;Lütfen seçim yapın&lt;/option&gt;
    &lt;option value="a"&gt;A&lt;/option&gt;
    &lt;option value="b"&gt;B&lt;/option&gt;
&lt;/select&gt;

&lt;!-- Şimdi A linkine tıklayınca value="a" olanı seçtirmek için gerekli linkleri hazırlayalım --&gt;
&lt;a onclick="sectir('a')" href="#"&gt;A&lt;/a&gt;
&lt;a onclick="sectir('b')" href="#"&gt;B&lt;/a</code></pre>
Şimdi burada kullandığımız sectir() fonksiyonunu hazırlayalım. Bu fonksiyonda yaptığımız iş çok basit. Öncelikle selected="selected" parametrelerini bulup siliyoruz. Daha value değerini girdiğimiz option'a selected="selected" parametresini ekliyoruz. Aşağıda fonksiyonumuz:
<pre class="line-numbers"><code class="language-javascript">function sectir(value){
    $("select[name='sec'] option:selected").removeAttr("selected");
    $("select[name='sec'] option[value='"+value+"']").attr("selected", "selected");
}</code></pre>
Kullanımı hakkında bilgi sahibi olmuşsunuzdur. Faydalı olmuştur umarım,Kolay gelsin,