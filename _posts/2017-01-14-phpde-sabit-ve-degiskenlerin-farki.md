---
ID: 6178
post_title: 'PHP&#8217;de Sabit ve Değişkenlerin Farkı'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/phpde-sabit-ve-degiskenlerin-farki-6178.html
published: true
post_date: 2017-01-14 06:17:15
---
Değişkenlere herhangi tip bilgi atanabilir: yazı (<strong>string</strong>), rakamlar (<strong>integer</strong>), dizi, doğru yanlış değerleri (<strong>true/false</strong>), <strong>null</strong> vb. Bir değişken tanımlanırken bu veri tiplerinden biri kullanılır.
<pre class="lang:php decode:true">$degisken_adi = 'değeri';</pre>
Ayrıca PHP değişkenlere atadığınız veri tiplerini değiştirmenize izin veriyor. Yani <strong>string</strong> bir ifade atadığınız değişkene <strong>integer</strong> bir ifade atayarak tipini <strong>integer</strong> olarak güncelleyebilirsiniz.
<pre class="lang:php decode:true">&lt;?php 
$degiskenim = "string değer"; 
$degiskenim = 30; 
$degiskenim = array('bu','bir','dizi'); 
$degiskenim = true; 
?&gt;</pre>
Bu kodda görünüyor ki <span class="lang:php decode:true crayon-inline ">$degiskenim</span> değişkenine en son <strong>true</strong> değeri atanıyor. Önceki atanan ifadeler ise kaybolup gider.

<strong>Sabit</strong> ise, adından da anlaşılacağı gibi, scriptin çalışması boyunca değeri asla değiştirilemez. Sabitler genellikle büyük harflerle tanımlanırlar. Sabitleri tanımlarken <strong>$</strong> kullanılmaz onun yerine <strong>define()</strong> fonksiyonu kullanılır.
<pre class="lang:php decode:true">define('_SABIT', 'değer');</pre>
Örnek kullanımı şöyledir:
<pre class="lang:php decode:true">&lt;?php define('SLM', 'Selam Naber?'); ?&gt;
&lt;html&gt;
	&lt;head&gt;
		&lt;title&gt;&lt;?php echo SLM; ?&gt;&lt;/title&gt;
	&lt;/head&gt;
	&lt;body&gt;
		&lt;p&gt;&lt;?php echo SLM; ?&gt;&lt;/p&gt;
	&lt;/body&gt;
&lt;/html&gt;</pre>
Yukarıdaki kodun çıktısı p etiketleri arasında <strong>Selam Naber?</strong> olacaktır.

define() ile sabit tanımlamak değişken oluşturmaktan daha yavaş olduğundan değişken kullanımı tavsiye edilir. Lakin değişkenlerin üzerine yazılabilir bu nedenle çok önemli olan ayar verilerinizi genellikle sabitlerle saklamayı tercih etmelisiniz projelerinizde. Bu sayede SITE_TITLE sabitinize atadığınız değeri kaza ile değiştiremezsiniz fakat $site_title değişkeninizi kodlama içerisinde farkında olmadan değiştirebilirsiniz. Bu tip ufak problemlerle karşılaşmamak için evrensel veya projenin tamamında aynı şekilde kullanılan önemli değerleri sabitlerle kullanmak daha mantıklıdır.

Keyifli kodlamalar,