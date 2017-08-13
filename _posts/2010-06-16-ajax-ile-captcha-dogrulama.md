---
ID: 52
post_title: AJAX ile CAPTCHA Doğrulama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ajax-ile-captcha-dogrulama-52.html
published: true
post_date: 2010-06-16 07:30:22
---
Bir kaç dosyada oluşan bu güvenlik tedbiri ile sitenize yapılan bot saldırılarını engelleyebilirsiniz. Yalnız bu güvenlik tedbirini sisteminize entegre etmeden önce lütfen sisteminizin bir yedeğini alın.

Öncelikle dosyalarımızı <a href="http://www.phpclasses.org/browse/package/5126/download/zip.html" target="_blank">bu adresten</a> indiriyoruz.

İndirdiğimiz dosyaların arasında jQuery'de bulunmaktadır. Dilerseniz
<ol>
 	<li>jquery.js</li>
 	<li>jquery.fom.js</li>
 	<li>jquery.validate.js</li>
</ol>
Dosyalarını yeni sürümleriyle değiştirebilirsiniz.

Dosyaları sitenizin ana dizinine atın. Daha sonra class/config.php dosyasını açın ve içindeki parametreleri kendi isteğinize göre düzenleyin.

En son olarak da ana dizininize <strong>captcha</strong> adlı bir klasör oluşturun. İşleminiz tamamlanmıştır.

Son olarak da captcha'yı nasıl entegre edeceğinizi anlatayım. Formunuzun bulunduğu sayfayı açın ve içine
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;script src="scripts/jquery.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script src="scripts/jquery.form.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script src="scripts/jquery.validate.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script src="scripts/check.js" type="text/javascript"&gt;&lt;/script&gt;</pre>

&lt;head&gt;...&lt;/head&gt; tagları arasına yukarıdaki kodları ekleyin. Sayfanın en üstüne de

<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php require(&#39;./config.php&#39;); ?&gt;</pre>

kodunu ekleyin. Resmi çağırmanız için gereken kod:

<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php echo $capimage; ?&gt;</pre>

Ve resimdeki yazıları girmeniz gereken inputun biçimide şöyle olacak:

<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input type=&quot;text&quot; name=&quot;captcha&quot; id =&quot;captcha&quot; class=&quot;captcha&quot;/&gt;</pre>

Artık form sayfası bitti. Şimdi de kontrolü yapacağımız sayfaya geliyoruz. Kontrolünü de aynen şöyle yapıyoruz:

<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
session_start();

if(($_REQUEST[&#39;captcha&#39;]) == $_SESSION[&#39;key&#39;]){
    echo &quot;true&quot;;
}
else {
    echo &quot;false&quot;;
}
?&gt;</pre>

Umarım anlaşılır olmuştuk. Bir yıldır makale yazmadığım için kelimeleri zor topladım biraz.

Herkese iyi çalışmalar,