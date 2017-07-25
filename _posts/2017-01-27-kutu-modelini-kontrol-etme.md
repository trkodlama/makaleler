---
ID: 6446
post_title: Kutu Modelini Kontrol Etme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/kutu-modelini-kontrol-etme-6446.html
published: true
post_date: 2017-01-27 21:22:17
---
<a href="http://www.w3.org/TR/CSS2/box.html" target="_blank">Bir belgede her eleman dikdörtgen kutu özelliğine sahiptir</a>. CSS kutu modeli, bu kutuları ve bileşenlerini anlatır.
<h2>Kutu Modeli Temelleri</h2>
HTML belgesindeki her diktörgen kutu içerik alanı, dolgu alanı, kenarlık alanı ve kenar boşluğu alanı olmak üzere 4 alandan oluşur. Bu alanların her birinin çevresi de "kenar" olarak adlandırılır.

Şu örneği düşünün:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;div class="kutu"&gt;  
  &lt;!-- içerik başlangıcı --&gt;
  Lorem ipsum dolor sit amet.
  &lt;!-- içerik bitişi --&gt;
&lt;/div&gt;</pre>
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">.box {
  width: 300px;
  height: 300px;

  padding: 50px; /* dolgu */
  margin: 50px; /* kenar boşluğu */
  border: 50px solid grey; /* kenar */
}</pre>
<h3>İçerik(content) Alanı</h3>
İçerik alanı, öğenin gerçek içeriği tarafından alınan alandır. Bu metin, resim veya başka ortam olabilir. Kenara "içerik kenarı" veya "iç kenar" denir.

<img class="aligncenter size-full wp-image-6447" src="http://www.trkodlama.com/wp-content/uploads/2017/01/1-content.jpg" alt="" width="499" height="499" />
<h3>Dolgu(padding) Alanı</h3>
Dolgu alanı, içerik alanı ile kenar arasında boşluğu ifade eder. Bu alanı bir kenar olarak düşünürsek bu kenara "dolgu kenarı" denir.

<img class="aligncenter size-full wp-image-6448" src="http://www.trkodlama.com/wp-content/uploads/2017/01/1-padding.jpg" alt="" width="500" height="499" />
<h3>Sınır(border) Alanı</h3>
Sınır alanı, sınır kalınlığına göre kaplanan alandır. Kenarı "sınır kenarı" olarak adlandırılır.

<img class="aligncenter size-full wp-image-6449" src="http://www.trkodlama.com/wp-content/uploads/2017/01/1-border.jpg" alt="" width="508" height="506" />
<h3>Kenar Boşluğu(margin) Alanı</h3>
Kenar boşluğu alanı kenarın(border) dışındaki alan. Kutunun bir parçası olmamasına rağmen sayfada kutunun kapladığı alanı düşünürsek kutunun bir parçasıymış gibi kabul edebiliriz. Kenar boşluğuna "kenar boşluğu kenarı" veya "dış kenar" denir.

<img class="aligncenter size-full wp-image-6450" src="http://www.trkodlama.com/wp-content/uploads/2017/01/1-margin.jpg" alt="" width="609" height="621" />

Kutuların yüksekliğini ve genişliğini <em>height</em> ve <em>width</em> css özellikleriyle tanımlayabiliriz. Bununla birlikte her kutunun sahip olacağı dört alan olduğunu biliyoruz. İçerik alanı, dolgu alanı, kenar ve kenar boşluğu alanlarını kullanıyorsak eğer yükseklik ve genişlikten neyi kastettiğimizi belirtmek zorundayız. Burada da yardımımıza <strong><em>box-sizing</em></strong> özelliği yetişiyor.
<h2>box-sizing Özelliği</h2>
<pre class="decode:1 " >box-sizing</pre> özelliği ile kutumuzun yüksekliğini ve genişliğini hangi kenara göre girdiğimizi belirtebiliyoruz. Yani kenar boşluğu dışında diğer üç özelliği dahil ve hariç tutacak şekilde genişlik ve yükseklik girebiliyoruz. <em><strong>box-sizing </strong></em>dört değer kabul eder. Bunlar <strong>content-box, padding-box, border-box</strong> ve <strong>inherit</strong> dir.
<h3>conten-box</h3>
<blockquote><em>genişlik = içerik alanı</em></blockquote>
Bu değer box-sizing özelliği için varsayılan değerdir. Kutunun genişliği, ki bizim örneğimizde kutunun genişliği 300px, içerik alanı genişliği eşit olur. Dolgu alanı ve kenar kalınlığı bu kutunun genişliğini 300px den daha büyük bir değer olmasına sebep olur. Sayfanın üstünde verdiğimiz örneğe göre bu değere sahip kutunun sayfada kapladığı genişliği düşünelim. İçerik alanı 300px, dolgu alanı 50+50=100px, kenar kalınlığı 50+50=100px olmak üzere kutunun boyutu 500px'dir. Kenar boşluğunu da 50+50=100px olarak hesaba katarsak kutunun sayfada kapladığı genişlik 600px olacaktır.

<img class="aligncenter size-full wp-image-6451" src="http://www.trkodlama.com/wp-content/uploads/2017/01/2-content.jpg" alt="" width="630" height="601" />
<h3>padding-box</h3>
<blockquote><em>genişlik = içerik alanı + dolgu alanı</em></blockquote>
Formülden de anlaşıldığı gibi genişliğimiz 300px ise ve dolgu alanımız 100 px ise içerik alanımızın genişliği 200px olacaktır otomatik olarak.

<img class="aligncenter size-full wp-image-6452" src="http://www.trkodlama.com/wp-content/uploads/2017/01/2-padding.jpg" alt="" width="529" height="514" />

<strong>Önemli Not: </strong>Bu değer sadece <em>Mozilla<strong> </strong></em>tarayıcısında destekleniyor ne yazık ki. Diğer tarayıcılar bu değeri ayarlamış olsanız bile <em>content-box</em> ayarlanmış gibi davranacaklar varsayılan olduğundan dolayı.
<h3>border-box</h3>
<blockquote><em>genişlik = içerik alanı + dolgu alanı + kenar kalınlığı</em></blockquote>
Bu değer ile de içerik alanımız 100px'e düşüyor gerekli hesaplamaları yaptığınızda.

<img class="aligncenter size-full wp-image-6453" src="http://www.trkodlama.com/wp-content/uploads/2017/01/2-border.jpg" alt="" width="406" height="419" />
<h3>inherit</h3>
Bu değer kutunun <em>box-sizing</em> değerini üst elemanın <em>box-sizing</em> değeri ile aynı yapar.
<h2>Kutu Modelini Kontrol Etme</h2>
Ben kendi adıma yorum yapmam gerekirse <strong><em>border-box</em></strong> değerini kullanmayı tercih ediyorum. Çünkü kutunun boyutunu belirledikten sonra dolgu alanı ve kenar kalınlıklarını görsel zevkime göre ayarlamak daha rahat geliyor. Diğer türlü onu hesapla, onu al oraya koy derken daha fazla zaman kaybı yaşıyorum.

Aşağıdaki kodu reset.css dosyanıza eklerseniz bütün elemanlarınızın box-sizing özelliği otomatik olarak border-box değerine sahip olacaktır.
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">html {  
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}</pre>
&nbsp;